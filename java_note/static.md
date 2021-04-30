# Static

 クラスの**メンバ変数やメソッドにstaticキーワードを付けると、そのメンバはstaticメンバのためのオブジェクト要素として定義されたことになります。**staticメンバのオブジェクトは、**1つのクラスに対して1つしか存在しない単独のオブジェクトです。**staticの付いているメンバはインスタンスを生成する必要もなく、メンバにアクセスすることができます。

メンバーの前にstaticをつけるとインスタンスを作らなくてもアクセスできる。それは、staticメソッドはインスタンスと別のメモリ領域で管理されることに理由があります。

mainメソッドのmainはただ、最初にこのメソッドを実行するよという意味であり、別にmainメソッドにstaticを付けると、当クラスの他のメソッドも、自動にメモリ上にロードされ、インスタンスなしで使えるわけではない。でも一般的に、mainメソッドのクラスのすべてのメソッドに対して、staticをつけます。

```java
class Main {
    public static void main(String[] args) {
  			//staticメンバーはプログラム実行したとき初期化される（どのクラスのものでも）
      	Obj.num0 = 4;
        Obj.add(2);//OK
        //Cash.add2(2,3);//エラー
      	
      	Obj obj = new Obj();
      	//メモリ： objの場所をnewして、データ領域でnum1を初期化
      　//（staticメンバーはnewの時初期化されない）
      	System.out.println(obj.num1);
      	//メモリ： num0はプログラム実行時にすでに「テキスト領域」で初期化されたので、
      	//インスタンスを「データ領域」で生成する際はもうstatic変数の初期化をしない
      	//だから、インスタンスからクラスのstatic変数をアクセスするときは、
      　//インスタンスのクラスを探して、
      	//そして「テキスト領域」にあるクラスのstatic変数のところから、
        //num0を参照することになる。
      	System.out.println(obj.num0);
    }
}

class Obj{
  static int num0 = 2;
  int num1 = 2;
  //これインスタンスなしでも使える
  static void add (int num2){
    System.out.println(num0 + num2);
    //System.out.println(num + num1);//エラー
  }
  //これはインスタンスしないと使えない
  void add2 (int num1){
    System.out.println(num0 + num1);
  }
}
```

```java
class Main {
    public static void main(String[] args) {
      Obj.num_s = 10;
      Obj obj = new Obj();
      obj.num = 20;
      //new領域にあるインスタンスの状態で、元のクラスにあるstatic変数の値を帰ると
      //テキスト領域にあるstatic変数は変えられて、
      //仮に、new領域にあるインスタンスが消されても、そのstatic変数は変えられたままです。
      obj.num_s = 100;
    
      System.out.print(Obj.num_s+","+obj.num);
    }
}

class Obj{
  //finalがついてるデータは変えられない。
  static final String MESSAGE = "HELLO";
  static int num_s = 1;
  int num = 2;
}
```

