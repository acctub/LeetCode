# ArrayList

```java
import java.util.ArrayList;

//Data Transfer Object読み取り専用アクセッサ
class DTO{
  private String name;
  private int age;
  //コンストラクタ
  public DTO(String name, int age){
    this.name = name;
    this.age = age;
  }
  public String getName(){
    return name;
  }
  public int getAge(){
    return age;
  }  
}

class Main {
    public static void main(String[] args) {
      //ジェネリスクの定義
			ArrayList<DTO> list = new ArrayList<DTO>();
      DTO dto1 = new DTO("太郎", 23);
      DTO dto2 = new DTO("花子", 22);
      list.add(dto1);
      list.add(dto2);
      list.add(new DTO("巨朗", 33));
      //アレーリストのアウトプット
      //これはただのアドレス
      System.out.println(list);
      //内容を取り出すには
      for (int i = 0; i < list.size(); i++){
        System.out.println(list.get(i).getName()+","+list.get(i).getAge());
      }
    }
}

```

Listのインスタンスを使う場合

```java
import java.util.ArrayList;
import java.util.LinkedList;
import java.util.List;

public class Main {
 
    public static void main(String[] args) {    
        List<Integer> list1 = new ArrayList<Integer>();
        list1.add(10);
        list1.add(20);
        list1.add(30); 
        // ArrayListからLinkedListへの変換
        LinkedList<Integer> list2 = new LinkedList<Integer>(list1);
        for(Integer i : list2) {
            System.out.println(i);
        }
    }
}
```



