---
description: 'https://web.plus-idea.net/2017/02/python2-3-venv-virtualenv/'
---

# 複数のpythonバージョンを扱うとき

まず3系をインストールするとき「Add Python to environment variables」はチェックを外しておき、環境変数のPATHにこのバージョンのpython.exeが追加されないようにしておきます。2系をインストールするとき、「Register Extentions」を外すことが重要！

指定するpythonを実行する

```bash
py -3#(3系最新版がデフォルトで実行される)
py -3.6
py -3.7
py -2#(2系最新版がデフォルトで実行される)
```

各バージョンのライブラリの場所を確認

```bash
py -3 -m pip -V
#pip 9.0.3 from C:\Program Files\Python36\lib\site-packages (python 3.6)
```

指定するpythonにライブラリをインストール

```bash
#方法１
cd C:\Python27\Scripts
pip2.7 install virtualenv -user
#方法2
py -2 -m pip install virtualenv -user
#指定するバージョンのScriptsフォルダに入り、pip -freezeでライブライの状況を確認できる
```

ヴァーチャル環境の構築

```bash
py -3.6 -m virtualenv <filename>
```

指定するバージョンをデフォルトで実行したい場合

```bash
set PY_PYTHON=3.6.5
py -3
```



