---
description: 整型反转
---

# 07Reverse Interger

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

