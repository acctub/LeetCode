# Excepiton

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

