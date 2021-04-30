# 継承

もしコンパイル時にサブクラスのファイルの中にスーパークラスのコードを結合してしまうと、後でスーパークラスを修正するたびにサブクラスも再コンパイルする必要が出てきます。しかし継承はプログラムの実行時に動的に行われるものなので、スーパークラスを再コンパイルするだけで、その結果がサブクラスにもすぐ反映されます。

多重継承ダメ、リンク継承はOK

![](https://track-contents-prod.s3.ap-northeast-1.amazonaws.com/books/86d0cb93-d538-4cf2-9f5c-05efb2642f82/79e90883-53d6-4bc2-84de-71fdcd982e24/img/slides/2-4.jpg)

![](https://track-contents-prod.s3.ap-northeast-1.amazonaws.com/books/86d0cb93-d538-4cf2-9f5c-05efb2642f82/79e90883-53d6-4bc2-84de-71fdcd982e24/img/items/Picture3a.png)

```java
class Main {
    public static void main(String[] args) {
      Child obj = new Child();
      System.out.println(obj.c_num);
      obj.parent_print();
      obj.child_print();
    }
}

class Parent{
  int p_num = 2;
  void parent_print(){
    System.out.println("これはスーパクラスのメソッドだよ！");
  }
}
class Child extends Parent{
  int c_num = 3;
  void child_print(){
    System.out.println("これはサブクラスのメソッドだよ！");
  }
}
```

 サブクラスをインスタンス化した場合、その**コンストラクタに引数を与えても、スーパークラス部分をインスタンス化するコンストラクタにはその引数は渡されません**（サブクラス部分のインスタンス化にはその引数は渡されます）。つまり、継承クラスのインスタンス化では、スーパークラス部分については常に引数なしのコンストラクタが選択されます。**これを変更するには、サブクラスのコンストラクタ内でsuper\(\)という命令を使用します。**super\(\)はthis\(\)と同じようにコンストラクタの中でしか使えず、またコンストラクタ内の最初の行でしか使うことができません。

**多層継承におけるコンストラクタの初期化**

```java

class Main{
  public static void main(String[] args) {
    Bot obj = new Bot(1,2,3);
    //コンストラクタを全く書かないのか、全部書くか、のどっちにしなきゃならない。
    //中途半端に書くとエラー
    obj.Top_print();
    obj.Mid_print();
    obj.Bot_print();
  }
}

class Top extends Object{
  int num1;
  Top(int num){ num1 = num; }
  void Top_print(){
    System.out.println("Top:"+num1);
  }
}
class Mid extends Top{
  int num2;
  Mid(int input1, int input2){ 
    super(input1);
    this.num2 = input2; 
  }
  void Mid_print(){
    System.out.println("Mid:"+num2);
  }
}
class Bot extends Mid{
  int num3;
  Bot(int input1, int input2, int input3){ 
    //this と super で子クラスの変数と、親クラスの変数を初期化できる
    //多層クラスまで初期化する必要がある場合、一個一個のsuperで上まで初期化する
    super(input1, input2);
    this.num3 = input3; 
  }
  void Bot_print(){
    System.out.println("Bot:"+num3);
  }
}
```

