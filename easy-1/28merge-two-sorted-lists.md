---
description: 结合两个链表
---

# 21. Merge Two Sorted Lists

### Solution

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
        
        ListNode rev = new ListNode(0);
        ListNode dummy = rev;

        if(l1 == null) return l2;
        if(l2 == null) return l1;
        
        while( l1 != null && l2 != null){
           if( l1.val <= l2.val){
                rev.next = l1;System.out.println(rev.next.val);
                rev = rev.next;
                l1 = l1.next;
           }else{
                rev.next = l2;System.out.println(rev.next.val);
                rev = rev.next;
                l2 = l2.next;
           }
        }         
        if(l1 != null) rev.next = l1;
        if(l2 != null) rev.next = l2;
 
        return dummy.next;
    }
}
```



