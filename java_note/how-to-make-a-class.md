# How to make a class

```java
public class Dog{
    //メンバ変数はメソッドの変数と異なり、宣言時に決められた値で自動的に初期化されます。
  	//byte-short-int -> 0; long -> 0l,float-double -> 0.0f
  	//char -> '\u0000', boolean -> false
  
    String name;
    int age;
    //クラスの初期化
    public Dog(String name_){
        name = name_;
        System.out.print("name is :" + name);
    }
    //クラスのメソッド（メンバーメソッド）
    public setage(int age_){
        age = age_;
    }
    public getage(){
        return age;
    }
    
    //マイン関数
    public static void main(String[] args){
        //インスタンスはオブジェクトの一種、インスタンスオブジェクトとも呼ぶ。
        //クラスファイルをひな形として、生成され、それぞれ独立するものをインスタントと呼ぶ。
        //それは、クラスから別のクラスを利用するために必要なものですそれは、
        //mydogはDogのインスタンス
        Dog mydog = new Dos("satosi");
        //mydogは参照型変数
        
        mydog.setage(3);
        age = mydog.getage();
        System.out.println("age is " + age);
    }
}
//output
//name is : satosi
//age is 3


```

