# HashMap

 **HashMapには、&lt;&gt;内で指定した識別子（String型のインスタンス）で格納するデータ（DTOSample型のインスタンス）を追加することしかできません。**また**&lt;&gt;内に指定可能なものは参照型**に限られ、基本データ型は指定できません。

```java
import java.util.HashMap;
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
    	DTO dto1 = new DTO("太郎",24);
      DTO dto2 = new DTO("花子",19);
      DTO dto3 = new DTO("二郎",22);
      //key value;どっちも必ず参照型!!!!!!!!!!!!!!!!!!
      HashMap<String, DTO> map = new HashMap<String, DTO>();
      map.put("1",dto1);
      map.put("2",dto2);
      map.put("3",dto3);
      String[] keyList = {"1","2","3"};
      //
      printMap(keyList, map);
    }
  	static void printMap(String[] keyList, HashMap<String, DTO> map){
      for(int i = 0; i < keyList.length; i++){
        DTO tmp = map.get(keyList[i]);
        System.out.println(tmp.getName()+","+tmp.getAge());
      }    
    }
}
```

