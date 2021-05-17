# JDBC

MAIN　ファイル

```java
import java.sql.Connection;
import java.sql.SQLException;
import java.util.List;

import dao.ConnectionUtil;
import dao.ContactDAO;
import dto.ContactDTO;

public class ContactDAOUse2 {

	private static void print(ContactDTO dto, boolean signal) {
		if (dto == null) {
			System.out.println("nullです。");
		} else {
			if (signal == true)
				System.out.printf(" Id:%d ,Extension:%d, Mobile:%s \n\n", dto.getId(), dto.getExtension(),
						dto.getMobile());
			else
				System.out.printf(" Id:%d ,Extension:%d, Mobile:%s \n", dto.getId(), dto.getExtension(),
						dto.getMobile());
		}
	}

	public static void main(String[] args) throws SQLException {
		Connection conn = null;
		ContactDTO dto = new ContactDTO();

		try {
			//接続し、自動コミットをオフにする
			conn = ConnectionUtil.getConnection();
			ContactDAO dao = new ContactDAO(conn);
			conn.setAutoCommit(false);

			//削除と確認
			dto = setDTOValue(102, 9999, "090-444-4444");
			dao.delete(dto);
			print(dto, true);
			//二度の削除-->エラー
			dao.delete(dto);
			print(dto, true);

			//挿入と確認
			dao.insert(dto);
			print(dao.getByPrimaryKey(102), true);

			//挿入と確認2
			//			dto = setDTOValue(104, 4004, "090-3233-6666");
			//			dao.insert(dto);
			//			print(dao.getByPrimaryKey(104), true);

			//変更と確認１
			dto = setDTOValue(102, 4002, "090-3333-6666");
			dao.update(dto);
			print(dao.getByPrimaryKey(102), true);

			//変更と確認2
			dto = setDTOValue(101, 4001, "090-1111-2222");
			dao.update(dto);
			print(dao.getByPrimaryKey(101), true);

			//全体を確認
			printList(dao);
			conn.commit();

		} catch (SQLException e) {
			e.printStackTrace();
		} finally {
			if (conn != null) {
				try {
					conn.close();
				} catch (SQLException e) {
					conn.rollback();
					e.printStackTrace();
				}
			}
		}
	}

	static ContactDTO setDTOValue(int id, int extension, String mobile) {
		ContactDTO dto = new ContactDTO();
		dto.setId(id);
		dto.setExtension(extension);
		dto.setMobile(mobile);
		return dto;
	}

	static void printList(ContactDAO dao) throws SQLException {
		System.out.println("Talbe------<contact>");
		List<ContactDTO> list = dao.getAll();
		for (ContactDTO dto : list) {
			print(dto, false);
		}
	}
}
```

DAOクラス

```java
package dao;

import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.util.ArrayList;
import java.util.List;

import dto.ContactDTO;

public class ContactDAO {
	private Connection conn = null;

	public ContactDAO(Connection conn) {
		this.conn = conn;
	}

	//GET 1 RECORD
	public ContactDTO getByPrimaryKey(int id) throws SQLException {
		ContactDTO dto = null;
		PreparedStatement pstmt = this.conn.prepareStatement(
				"SELECT * FROM contact WHERE id = ?");
		pstmt.setInt(1, id);
		ResultSet rs = pstmt.executeQuery();
		if (rs.next()) {
			dto = new ContactDTO();
			dto.setId(rs.getInt(1));
			dto.setExtension(rs.getInt(2));
			dto.setMobile(rs.getString(3));
		}
		return dto;
	}

	//GET ALL RECORD
	public List<ContactDTO> getAll() throws SQLException {
		List<ContactDTO> dtos = new ArrayList<ContactDTO>();

		PreparedStatement pstmt = this.conn.prepareStatement(
				"SELECT * FROM contact");
		ResultSet rs = pstmt.executeQuery();
		while (rs.next()) {
			ContactDTO dto = new ContactDTO();
			dto.setId(rs.getInt(1));
			dto.setExtension(rs.getInt(2));
			dto.setMobile(rs.getString(3));
			dtos.add(dto);
		}

		return dtos;
	}

	//INSERT-----------------------------
	public void insert(ContactDTO dto) throws SQLException {
		PreparedStatement pstmt = this.conn.prepareStatement(
				"INSERT INTO contact VALUES(?,?,?)");
		pstmt.setInt(1, dto.getId());
		pstmt.setInt(2, dto.getExtension());
		pstmt.setString(3, dto.getMobile());
		int rs = pstmt.executeUpdate();
		System.out.printf("Table <contact>: %d Data Inserted! >>", rs);
	}

	//UPDATE-----------------------------
	public int update(ContactDTO dto) throws SQLException {
		PreparedStatement pstmt = this.conn.prepareStatement(
				"UPDATE contact SET extension=?, mobile=? WHERE id = ?");
		pstmt.setInt(3, dto.getId());
		pstmt.setInt(1, dto.getExtension());
		pstmt.setString(2, dto.getMobile());
		int count = pstmt.executeUpdate();
		if (count != 1) {
			//System.out.print("Update Failed! >指定されるIDが存在しません。>");
			throw new RuntimeException(String.format("Update Failed! >ID<%d>が存在しません。", dto.getId()));
		} else {
			System.out.print("Table <contact>: Data Updated! >>");
		}
		return count;
	}

	//DELETE-----------------------------
	public int delete(ContactDTO dto) throws SQLException {
		PreparedStatement pstmt = this.conn.prepareStatement(
				"DELETE FROM contact WHERE id = ?");
		pstmt.setInt(1, dto.getId());
		int count = pstmt.executeUpdate();
		if (count != 1) {
			//System.out.print("Update Failed! >指定されるIDが存在しません。>");
			throw new RuntimeException(String.format("Update Failed! >ID<%d>が存在しません。", dto.getId()));
		} else {
			System.out.print("Table <contact>: Data Updated! >>");
		}

		return count;
	}

}

```

DIOクラス

```java
package dto;

public class ContactDTO {
	int id;
	int extension;
	String mobile;

	public int getId() {
		return id;
	}

	public int getExtension() {
		return extension;
	}

	public String getMobile() {
		return this.mobile;
	}

	public void setId(int id) {
		this.id = id;
	}

	public void setExtension(int extension) {
		this.extension = extension;
	}

	public void setMobile(String mobile) {
		this.mobile = mobile;
	}
}

```

Connectionクラス

```java
package dao;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;

public class ConnectionUtil {
	private static final String DRIVER_NAME = "org.postgresql.Driver";
	private static final String DB_URL = "jdbc:postgresql://localhost:5432/univ";
	private static final String DB_USER = "postgres";
	private static final String DB_PASSWORD = "postgres";

	public static Connection getConnection() throws SQLException {
		try {
			Class.forName(DRIVER_NAME);
			return DriverManager.getConnection(DB_URL, DB_USER, DB_PASSWORD);
		} catch (ClassNotFoundException e) {
			System.out.println("Conn ER");
			throw new RuntimeException(e);
		}
	}
}

```

