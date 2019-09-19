# Vector Class

```
//Vectorクラスの可変長配列は通常の配列と違い、要素を追加したり、削除することが簡単にできます。
```

```java
public class Main {
    public static void main(String[] args) {
        Vector<String> vec = new Vector<>();
        //要素の追加
        vec.add("さ");vec.add("む");
        vec.add("ら");vec.add("い");
        System.out.println(vec);
        //要素の削除
        vec.remove(1);//indexを指定して削除する
        System.out.println(vec);
        //サイズの取得
        System.out.println(vec.size());
    }
}
//[さ, む, ら, い]
//[さ, ら, い]
//3

```



\*\*\*\*

\*\*\*\*

