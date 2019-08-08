---
description: '["flower","flow","flip"]编写一个函数来查找字符串数组中最长的公共前缀字符串。空则返回“”'
---

# 14Longest Common Prefix

### Mycode

```java
class Solution {
    public String longestCommonPrefix(String[] strs) {
        String rev = "";
        int len = minlen(strs);
        int Len = strs.length;
	 
	 if(Len == 0) return "";
  
        //System.out.println("len :" + len);
        //System.out.println("Len :" + Len);
        
        int flag = 0;
        for (int i = 0; i < len; i++){
            for(int j = 0; j < Len-1; j++){ 
                if(strs[j].charAt(i) != strs[j+1].charAt(i)) flag = 1;
                //System.out.println(strs[j].charAt(i) != strs[j+1].charAt(i));
                //System.out.println(flag);
            }
            if(flag == 0){
                //System.out.println(flag);
                rev = rev.concat(String.valueOf(strs[0].charAt(i)));
            }
        }
        return rev;
    }
    
    public int minlen(String[] strs){
        int len = Integer.MAX_VALUE;
        
        for (int i = strs.length-1;i > -1; i --){// 获取String[]类型的长度是，不用括号
               if( len > strs[i].length() ) len = strs[i].length() ;
        }
        return len;
    }
}

```

### Solution-1

Time complexity : **O\(S\)** Space complexity :  **O\(1\)**. We only used **constant** extra space.

```java
class Solution {
     public String longestCommonPrefix(String[] strs) {
         
         if (strs.length == 0) return "";
         String prefix = strs[0];
         
         //LCP(LCP(x1,x2),x3...)...
         for(int i = 1; i < strs.length; i++){
            while(strs[i].indexOf(prefix) != 0){
                prefix = prefix.substring(0,prefix.length()-1);//不同就缩短一位
                if(prefix.length() == 0) return "";
            }
         }
     
		// String Str = new String("hel");
		// System.out.println(Str.indexOf("hell"));//-1 hell不再hel中

         return prefix;
     }
}
```

