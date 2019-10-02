# pythonでの操作

テーブルをつくる

```python
import sqlite3
from contextlib import closing

dbpath = path
with closing(sqlite3.connect(dbpath)) as Conn:
    c = Conn.cursor()
    SQL_code = 'create <table> (<date> date,<name> text,<len> integer)'
    #実際にコード書くとき<>はいらない、わかりやすくするため書いたの
    c.execute(SQL_code)
```

テーブルにデータをインサートする

```python
data = ('1991-01-01','jack',20)
with closing(sqlite3.connect(dbpath)) as Conn:
    c = Conn.cursor()
    insert_sql = f'insert into <table>　(<date>,<name>,<len>) values (?,?,?)'
    c.executemany(insert_sql,data)#複数のデータをDBのuserテーブルに渡す
```

条件付きでテーブルからデータを抽出する

```python
with closing(sqlite3.connect(dbpath)) as Conn:
    c = Conn.cursor()
    SQL_code = 'select * from <table> where date < ? and name = ? and len < 15'
    #条件に文字列を含む場合は、?で条件文を表し、後で条件を書く
    condition = ('1991-01-02','jack',)
    c.execute(SQL_code,condition)
    for row in c:
        print(row)
    
    # 全行をlistで返す
    cur.execute( "select * from <table>" )
    list = cur.fetchall()
    
#>('1991-01-01', 'jack','静粛に願います。\n', 9)
#>('1991-01-01', 'jack','これより会議を開きます。\n', 7)
#>...
```

