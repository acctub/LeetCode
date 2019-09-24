# SQLite操作

SQLiteファイルの作成

```text
$sqlite3 sample.sqlite3
$sqlite>.show
```

テーブルの作成とデータの入れ込み

```sql
$sqlite>create table user(name text,age integer,addr text);
>insert into user values('Suzuki', 24, 'Osaka');
>insert into user values('Honda', 18, 'Tokyo');
>insert into user values('Yamada', 32, 'Osaka');
```

条件付きでデータを抽出

```sql
>select * from user where addr = 'Osaka';//値で
# Suzuki|24|Osaka
# Yamada|32|Osaka
>select * from user where age <= 20;//比較演算子
# Honda|18|Tokyo
>select * from user where addr <>'Osaka';//そうでないデータ
# Honda|18|Tokyo

//複数の条件式の場合
where 条件式1 and 条件式2
where 条件式1 or 条件式2
where not 条件式
select * from user where　age > 30 and address = 'Osaka';
# Yamada|32|Osaka

```

