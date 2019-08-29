# 09. Palindrome Number

### Mycode

```java
class Solution {
    public boolean isPalindrome(int x) {  
    
         String str = String.valueOf(x);
         int left = 0,right = str.length()-1;
        
         while(left < str.length()/2){           
             if(str.charAt(left) ==  str.charAt(right)){
                 left += 1;
                 right -= 1;
             }
             else return false;
         }  
        return true; 
    }
}

```

### Soluton-1

Time complexity :O\(log 10 ​\(n\)\)  Space complexity :O\(1\).

```java
class Solution {

    public boolean isPalindrome(int x) {  
    
        int vec = 0;
        if(x < 0 || x%10 == 0 && x != 0) return false;

        while(x > vec){
            vec = vec*10 + x%10;
            x = x/10;
        }
        return (x == vec)||(x == vec/10);  
    }
}
```

### MyCode2

```java
class Solution {
    public boolean isPalindrome(int x) {

        int rev = 0;
        if( (x != 0 && x%10 == 0) || x < 0) return false;
        
        while(rev <= x){
            rev = rev*10 + x%10;
            if( rev == x || rev == x/10) return true;
            x = x/10;
        }
        return false;
    }
}
```

