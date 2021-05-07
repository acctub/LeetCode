# アクセス制限

```java
class Main {

    public static void main(String[] args) {
      Obj obj = new Obj();
      obj.print1();obj.print2();obj.print4();
      //obj.print3();
      
    }
}

class Obj{
  protected void print1(){
    System.out.println("Protected");
  }
  public void print2(){
    print3();
    System.out.println("Public");
  }
  private void print3(){
    System.out.println("Private");
  }
  void print4(){
    System.out.println("No修飾");
  }
}
```

アクセッサ

アクセッサメソッド Javaの話じゃない、 通常、Javaではすべてのメンバ変数をprivateに設定します。 変数の値はクラスの外部から不用意に変更されると危険であるためです。 しかし、場合によってはメンバ変数の値を調べたり、外部から値を変えることが一切できなくなってしまいます。 そこで、そのようなアクセスを許可する時だけ、 アクセッサメソッドと呼ばれるものを用意し、他のクラスからのアクセスはアクセッサメソッドを介して行うようにします。

```java
class Obj{
  void print(){
    System.out.println("huhuhu~!");
  }
}

class Accessor {
    private Obj obj = null;

    public Obj getObject() {
        return obj;
    }
    public void setObject(Obj obj) {
        this.obj = obj;
    }
}
class Main {
    public static void main(String[] args) {
      	//アクセッサのインスタンスをつっくる
        Accessor acs = new Accessor();
      	//普通のインスタンスを作る
        Obj obj1 = new Obj();
      	//先つくたったインスタンスのobj1をアクセッサに渡して、
        acs.setObject(obj1);
      	//アクセッサが受け取ったobj1をいったん保有して、そのあとobj2はgetメソッドで、アクセッサあらobj1を取得する
        Obj obj2 = acs.getObject();
      	//今obj2はobj1の内容と一緒で、アドレスも一緒
        obj2.print();
      	System.out.println(obj1);
        System.out.print(obj2);
        //だから、アクセッサが仲介として参照型変数を渡した場合、渡したのは
        //参照型変数の「ア・ド・レ・ス」だけです！
    }
}
```

一切のアクセスを許さない変数や参照だけはできる変数、参照も変更もできる変数というように、 メンバ変数に柔軟なアクセス制御を与えることができます。

