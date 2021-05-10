# Excepiton

今回はInteger.parseInt\(\)メソッドが例外クラスNumberFormatExceptionを発生させる可能性があるので、この例外のための処理をcatchブロック内に記述します。

```java
class Main {
    public static void main(String[] args) {      
      System.out.println(args[0]);    
      if (args.length == 1){
        try{
          int number = Integer.parseInt(args[0]);
          System.out.println(number);
        } catch (NumberFormatException e){
          System.out.println("入力は数値ではない！");
        }
      }else{
        System.out.println("１つの数値を入力ください１");
      }   
    }
}
```

catch\(ここでは、例外を発生させる可能性のある**クラス**名を書く\)

ここでの**クラス**は、システムの例外クラスのことです。

