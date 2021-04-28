---
description: コンストラクタ
---

# Constructor

 コンストラクタはクラス名と同じ名前を持ち、**インスタンスの生成に伴って、前もって行う必要のある処理を記述しておくためのものです。**

 実は**コンストラクタの記述を省略した場合には、コンパイラ**はコンパイル時に**何もしないコンストラクタ**を**自動的に追加**しています**。この自動的に追加されるコンストラクタ**のことを**デフォルトコンストラクタ**と言います**。**

コンストラクタはインスタンス化の際のみ使用されるため、インスタンス生成後は不要であることから、生成されたインスタンス自体にコンストラクタは含まれません。

**特徴**　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　 　- クラス名と同じ名前である  
- 戻り値の型を持たない

```java

class ListNode {
    int val;
    ListNode next;
  	//初期化の方法---コンストラクタ
    //1)値指定せず---自動初期化される
    ListNode() {}
    //2)宣言時に値を１つ指定
    ListNode(int val){ this.val = val; }
    //3)宣言時に値を全部指定
    ListNode(int val, ListNode next) {
      this.val = val; 
      this.next = next; 
    }
}

class Main {
    public static void main(String[] args) {
      ListNode head = makeIntList(1,2,7,4,9,8,3,6,0);
      show(head);
      show(reverse(head));
    }
  	//逆転メソッド
    static ListNode reverse(ListNode head){
      ListNode pre = null, 
              cur = null, 
              tmp = head;
              
      while(tmp != null){
        pre = cur; 
        cur = tmp; 
        tmp = tmp.next;
        cur.next = pre;
      }
      return cur;
    }
  	//リストを生成するメソッド
    static ListNode makeIntList(int...nums){
      ListNode head = new ListNode(0);
      ListNode dummy = head;
      for(int i = 0; i < nums.length; i++){
        dummy.next = new ListNode(nums[i]);
        dummy = dummy.next;
      }
      return head.next;
    }
  　//リストを表示するメソッド
  	static void show(ListNode head){
      System.out.print("[");
      while(head != null){
        if(head.next == null){
          System.out.print(head.val+"]");
          break;
        }else{
          System.out.print(head.val+",");
        }
        head = head.next;
      }
    }
}
```

