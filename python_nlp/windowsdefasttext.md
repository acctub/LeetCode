# WindowsでfastText

STEP１各種ライブラリをインストール

```bash
$ wget https://github.com/facebookresearch/fastText/archive/v0.1.0.zip
$ unzip v0.1.0.zip
$ cd fastText-0.1.0
$ make
```

makeでエラーになったら

```bash
c++ -pthread -std=c++0x -march=native -O3 -funroll-loops -c src/args.cc
make: c++: Command not found
Makefile:22: recipe for target 'args.o' failed
make: *** [args.o] Error 127
#g++をインストールしろう
sudo apt-get install g++
```

fasttextのpython用のライブラリのインストール

```bash
$ git clone https://github.com/facebookresearch/fastText.git
$ cd fastText
$ pip install .
```

分散表現辞書を作る

```bash
$ cd fastText-0.1.0
./fasttext skipgram -input(分かち書きしたファイル) -output() -dim 次元数() -lr 学習率
-epoch エポック数
次元数について、
文書のサイズに比例して、100,200,300まで(?)設定可能
```

