# Excepiton

今回はInteger.parseInt\(\)メソッドが例外クラスNumberFormatExceptionを発生させる可能性があるので、この例外のための処理をcatchブロック内に記述します。

```java
class Main {
    public static void main(String[] args) {
      System.out.println(args[0]);    
     	try{
          int number = Integer.parseInt(args[0]);
          System.out.println(number);
        } catch (NumberFormatException e){
          e.printStackTrace();
          System.out.println("入力は数値ではない！");
        } catch (ArrayIndexOutOfBoundsException e) {
            System.out.println("1つの数値を入力して下さい。");
        } finally{
        	System.out.println("プログラムは終了しました");
      	}
      System.out.println(222);
    }
}

```

catch\(ここでは、例外を発生させる可能性のある**クラス**名を書く\)

ここでの**クラス**は、システムの例外クラスのことです。

