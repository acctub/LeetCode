---
description: 整型反转
---

# 07. Reverse Interger

### Solution

```java
class Solution {
    public int reverse(int x) {
        
        int rev = 0;
        //x = 1534236469;
        
        while(x != 0){
            int tail = x%10;
            x = x/10;
            if(rev > Integer.MAX_VALUE/10 || (x == Integer.MAX_VALUE)) return 0;
            if(rev < Integer.MIN_VALUE/10 || (x == Integer.MIN_VALUE)) return 0;
            rev = rev*10 + tail; 
            System.out.println(rev);
        }
        return rev;
        
    }
}
```

### Runtime: 1 ms

```java
//use long
class Solution {
  public int reverse(int x) {
      long rev = 0;

      while(x != 0){
          rev = rev*10 + x%10;
          x = x/10;
          if(rev > Integer.MAX_VALUE || rev < Integer.MIN_VALUE)
              return 0;
      }
      return (int)rev;
  }
}
```

```java
//use int only
class Solution {
  public int reverse(int x) {
      int rev = 0;preRev = 0;
      
      while(x != 0){
          rev = rev*10 + x%10;
          x = x/10;
          if(rev/10 != preRev) return 0;
          preRev = rev;
      }
      return rev;
  }
}
```

