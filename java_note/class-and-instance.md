# Class and Instance

```java
class Main {
    public static void main(String[] args) {
      ObjSample obj = new ObjSample();
      //インスタンスメンバーにアクセスする方法
      int sum = obj.sum(4,5,6,7,8);
      
      System.out.print(obj.original);
      System.out.print(sum);
    }
}


class ObjSample{
  //メンバー変数
  static int original = 1;
  //メンバーメソッド
  public static int sum(int...nums){
    int sum = 0;
    System.out.print("The Sum of [");
    for(int i = 0; i < nums.length; i++){
      	if(i != nums.length-1)
					System.out.printf("%d,",nums[i]);
      	else
          System.out.printf("%d] is : ",nums[i]);
      	sum += nums[i];      
    }
    return sum;
  }
}
```

