# インターフェース

**インタフェースは具象メソッドを持つことができず、抽象メソッドのみ定義できる**  
**インタフェースに定義可能なメンバ変数は定数のみ**

```java
interface Inter{
  int num = 5;
  void print();
}
class Sub implements Inter{
  public void print(){
    System.out.println("Sub!");
  }
}
class Main {
    public static void main(String[] args) {
        Inter obj = new Sub();
        obj.print();
      	System.out.println(obj.num);
    }
}
```

