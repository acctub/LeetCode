# How to make a class

```java
public class Dog{
    //クラスの属性
    String name;
    int age;
    //クラスの初期化
    public Dog(String name_){
        name = name_;
        System.out.print("name is :" + name);
    }
    //クラスのメソッド
    public setage(int age_){
        age = age_;
    }
    public getage(){
        return age;
    }
    
    //マイン関数
    public static void main(String[] args){
        Dog mydog = new Dos("satosi");
        
        mydog.setage(3);
        age = mydog.getage();
        System.out.println("age is " + age);
    }
}
//output
//name is : satosi
//age is 3
```

