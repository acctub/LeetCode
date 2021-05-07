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

