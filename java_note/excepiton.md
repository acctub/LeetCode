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

//catch (Exception e)で上記の例外処理をまとめて対応できる（コンパイルエラー以外の）
```

catch\(ここでは、例外を発生させる可能性のある**クラス**名を書く\)

ここでの**クラス**は、システムの例外クラスのことです。

 またcatchブロックが複数記述されている場合、例外発生時はcatchブロックを順番に確認します。もし最初に「catch\(Exception e\)」というcatchブロックがあると、全ての例外を捕捉してしまうため、それ以降のcatchブロックはチェックされません（**この場合はコンパイルエラーが発生します**）。したがって、複数のcatchブロックを記述する場合は、サブクラスの例外から先に記述して、最後にExceptionクラスのcatchブロックを記述するようにします。

1. java.lang.Exceptionクラス：一般的な「例外」を表現するクラス
2. java.lang.RuntimeExceptionクラス：「実行時例外」を表現するクラス
3. java.lang.Errorクラス：致命的なエラーを表現するクラス

**Throwsによる例外処理**

 throwsキーワードを使用すると、発生した例外をそのメソッドでは処理せず、**メソッドの呼び出し元に発生した例外を渡してその処理を任せることができます。**

```java
class Main {
    public static void main(String[] args) {
      try{
				int sum = average(args);
        System.out.println(sum);
      } catch (NumberFormatException e){
        System.out.println("入力する値は数値でなければいけません。");
      } catch (ArithmeticException e){
        System.out.println("0以外の数値を入力して下さい。");
      } 
    }
  	public static int average(String[] args)throws
      NumberFormatException, ArithmeticException{
        int sum = 0;
      	for (int i = 0; i < args.length; i++){
        	sum += Integer.parseInt(args[i]);
        }
        sum /= args.length;
        System.out.printf("平均は%dです。\n",sum);
    	 return sum;  
    }
}
```

```java
      //例外を創出する
      try{
        throw new Exception("明示的に例外を発生させています");
      } catch (Exception e){
        e.printStackTrace();
      }
      
     //Exceptionはクラスだよ、つまり変数を作ることができる
      try{
        Exception ex = new Exception ("明示的に例外を発生させています");
        throw ex;
      } catch (Exception e){
        e.printStackTrace();
      }
```

