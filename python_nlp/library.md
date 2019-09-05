# Library

### pprint

```python
#リストや辞書の要素が改行して出力するモジュール
import pprint
import sys

l = [{'Name': 'Alice XXX', 'Age': 40, 'Points': [80, 20]}, 
     {'Name': 'Bob YYY', 'Age': 20, 'Points': [90, 10]},
     {'Name': 'Charlie ZZZ', 'Age': 30, 'Points': [70, 30]}]
     
print(l)
#略
pprint(l)
# [{'Age': 40, 'Name': 'Alice XXX', 'Points': [80, 20]},
#  {'Age': 20, 'Name': 'Bob YYY', 'Points': [90, 10]},
#  {'Age': 30, 'Name': 'Charlie ZZZ', 'Points': [70, 30]}]]
pprint.pprint(l, width=40)
# [{'Age': 40,
#   'Name': 'Alice XXX',
#   'Points': [80, 20]},
#  {'Age': 20,
#   'Name': 'Bob YYY',
#   'Points': [90, 10]},
#  {'Age': 30,
#   'Name': 'Charlie ZZZ',
#   'Points': [70, 30]}]
pprint.pprint(l, depth=1)
# [{...}, {...}, {...}]
pprint.pprint(l, depth=2)
# [{'Age': 40, 'Name': 'Alice XXX', 'Points': [...]},
#  {'Age': 20, 'Name': 'Bob YYY', 'Points': [...]},
#  {'Age': 30, 'Name': 'Charlie ZZZ', 'Points': [...]}]


#Pythonでimportの対象ディレクトリのパスの確認・追加
#確認
pprint.pprint(sys.path)
#追加
sys.path.append(os.path.join(os.path.dirname(__file__), '..'))
```

### もしpip install してもimportできない場合は

```text
pip install のパスを確認
pip uninstall <packages>

pprint.pprint(sys.path)
両方が一致するかどうかチェック
```

### xml\_method

```python
#ファイルからxmlを読み込み
import xml.etree.ElementTree as ET
tree = ET.parse('country_data.xml')
root = tree.getroot()

#文字列から直接インポート
root = ET.fromstring(country_data_as_string)
```

### urllib\_method

```python
from urllib.parse import quote
#quote 文字列のURLエンコード（パーセントエンコーディング）するツール

tmp = '日本'

url = 'http://kokkai.ndl.go.jp/api/1.0/speech?' + quote(tmp)
#'http://kokkai.ndl.go.jp/api/1.0/speech?%E6%97%A5%E6%9C%AC'
url_moji = 'http://kokkai.ndl.go.jp/api/1.0/speech?' + tmp
#'http://kokkai.ndl.go.jp/api/1.0/speech?日本'

url_mojiをそもまま使えないのでエンコードが必要

```

### re\_method

```python
#正規表現でいらない部分を置換する
import re
string = "1955年（昭和30年）2月27日"
pattern = "（.+）"
#正規表現テストサイトhttps://www.regexpal.com/
text = re.sub(re.compile(pattern, '', string)
#1955年2月27日

#普通の置換
string.replace("昭和30年",'')
#1955年（）2月27日
```

### テキストファイルの読み込みと書き込み

```python
path = ""
#読み込み
with open(path,mode = 'r',encoding = 'UTF-8') as f:
    text = f.read()
    print(text)
#書き出し
with open(path,mode = 'w',encoding = 'UTF-8') as f:
    f.write('\n')
    f.write("hallo")
#vscode　変量の名前を一斉に変える方法:ctrl+shift+L
```





