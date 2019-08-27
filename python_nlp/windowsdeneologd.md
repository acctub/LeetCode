---
description: 'https://github.com/neologd/mecab-ipadic-neologd/blob/master/README.ja.md'
---

# WindowsでNEologd辞書

**１. Windows Subsystem for Linuxを有効にする**

```text
管理者権限でPowerShellを開いて
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
再起動
```

 **２. Ubuntuをインストール**

```text
Microsoft StoreからUbuntuをインストール
//リポジトリを日本のサーバーに切り替える
sudo sed -i -e 's%http://.*.ubuntu.com%http://ftp.jaist.ac.jp/pub/Linux%g' /etc/apt/sources.list

sudo apt update
sudo apt upgrade//めっちゃ時間かかる

//アンインストール
lxrun /uninstall /full
lxrun /install

```

 **３. NEologdをインストール**

```text
//ビルドに必要なもの
sudo apt install mecab
sudo apt install libmecab-dev
sudo apt install make

//NEologd
git clone https://github.com/neologd/mecab-ipadic-neologd.git
cd mecab-ipadic-neologd
sudo bin/install-mecab-ipadic-neologd

//copyする
cd ..
sudo cp -R /usr/lib/x86_64-linux-gnu/mecab/dic/mecab-ipadic-neologd/  /mnt/c/

```

**４. Pythonで実行**

```text
import MeCab

mecab = MeCab.Tagger("-Ochasen -d C:\mecab-ipadic-neologd")
print(mecab.parse("進撃の巨人の発売日だ"))
```

