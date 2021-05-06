# オーバライド

スーパクラスとサブクラスに、「戻り値の方、メソッド名、引数リスト」がすべて存在する場合、発動します。スーパクラスのメソッドはサブクラスのメソッドに隠されてしまう。（サブのヤツにアクセルすることになる）。

```java
class Main{
  public static void main(String[] args) {
    Bot obj = new Bot();
    obj.print();
    //obj.print2();//使えない
  }
}

class Top extends Object{
  int num1;
  void print(){ System.out.println("Top:"+num1); }
}
class Mid extends Top{
  int num2;
  //super.print()で親クラスTopのprint()を使う。
  private void print2(){ System.out.println("使ってあげない！"); }
  void print(){ System.out.println("Mid:"+num2); super.print();}
}
class Bot extends Mid{
  int num3;
  //super.print()で親クラスMidのprint()を使う。
  void print(){ 
    System.out.println("Bot:"+num3); 
    super.print(); 
    //super.print2();//使えない
  }
}


// java Main
// Bot:0
// Mid:0
//Top:0
```

 **サブクラスのインスタンスはスーパークラスの型の変数に代入する**ことができます。その場合、スーパークラス型の変数に対しては、**スーパークラスのメンバに限ってアクセス**可能です。

Super obj = new Sub\(\)の場合

```java
class Main {

    public static void main(String[] args) {
      Super obj = new Sub();
      obj.method();
      obj.func1();
      //obj.func2();//エラーになる
    }
}

class Super{
  void method(){
    System.out.println("Super");
  }
  void func1(){
    System.out.println("Func1");
  }
}

class Sub extends Super{
  void method(){
    System.out.println("Sub");
  }
  void func2(){
    System.out.println("Func2");
  }
}
```
