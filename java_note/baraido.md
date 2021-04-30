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

