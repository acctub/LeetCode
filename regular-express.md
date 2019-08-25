# Regular express

```text
.                 任意の一文字にマッチする。
[...]             括弧内に含まれる一文字にマッチする。
[^...]            括弧内に含まれない一文字にマッチする。
^                 行の最初にマッチする。
&                 行の最後にマッチする。
ne*ko             nko,neko,neeeeko
(neko)*ano        ano,nekonekoano,nekoano,//繰り返す表現
(https|https)://(\S+?)/    ???????????????????
(a)+(\S+?)s        aからsまでのも全部（一行以内）
(str1)+([\s\S]+?)str2    str1からstr2までのも全部（改行も含む）
```



