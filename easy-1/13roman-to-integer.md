---
description: 将数字转化为罗马数字表示（不要求检错）
---

# 13Roman to Integer



### Mycode

```java
class Solution {
        public int romanToInt(String s) {
        //s = "DCCCXLV";
        int sum = 0;
        
        for(int i = s.length()-1 ; i > -1; i -= 2){
            int I = func(s.charAt(i));
            
            if(i-1 != -1 && i-2 != -1){
                int J = func(s.charAt(i-1));
                int K = func(s.charAt(i-2));
                if(J > I && J >K) {
                    sum += J+I-K;
                    i -= 1;
                }
                else if( J >= I) sum +=J+I;
                else sum += I-J;
            }
            else if(i-1 != -1){
                int J = func(s.charAt(i-1));   
                if(J >= I) sum += J+I;  
                else sum += I-J;
            }
            else sum += I; 
            System.out.println(sum);
        }
        return sum;  
    }
    public int func(char c){
        
        switch (c) {
            case 'I':
                return 1;
            case 'V':
                return 5;
            case 'X':
                return 10;
            case 'L':
                return 50;
            case 'C':
                return 100;
            case 'D':
                return 500;
            case 'M':
                return 1000;
            default:
                System.out.println("エラー");
                break;
        }
        return -1;
    }
}
```

### Solution-1

```java
class Solution {
    public int romanToInt(String s) {
        
        //s = "IIV";
        
        int sum = 0;
        for(int i=0; i<s.length(); i++){
            switch(s.charAt(i)){
                case 'I':
                    if(i < s.length()-1 && (s.charAt(i+1) == 'V' || s.charAt(i+1) == 'X')){
                        if(i < s.length()-2){
                            System.out.println("Illegal input(1)!");return -1;
                        }
                        else   
                        sum -= 1;
                    }
                    else if(i < s.length()-3 && (s.charAt(i+3) == 'I')&& (s.charAt(i+2) == 'I')&& (s.charAt(i+1) == 'I')){
                        System.out.println("Illegal input(20)!");return -1;}
                    else
                        sum += 1;
                    break;
                case 'V':
                    sum += 5;
                    break;
                case 'X':
                    if(i < s.length()-1 && (s.charAt(i+1) == 'L' || s.charAt(i+1) == 'C'))
                        sum -= 10;
                    else if(i < s.length()-3 && (s.charAt(i+3) == 'X')&& (s.charAt(i+2) == 'X')&& (s.charAt(i+1) == 'X')){
                        System.out.println("Illegal input(21)!");return -1;}
                    else
                        sum += 10;
                    break;
                case 'C':
                    if(i < s.length()-1 && (s.charAt(i+1) == 'D' || s.charAt(i+1) == 'M'))
                        sum -= 100;
                    else if(i < s.length()-3 &&(s.charAt(i+3) == 'C')&&(s.charAt(i+2) == 'C')&&(s.charAt(i+1) == 'C')){
                        System.out.println("Illegal input(22)!");return -1;}
                    else
                        sum += 100;
                    break;
                case 'L':
                    if(i < s.length()-1 && (s.charAt(i+1) == 'L')){
                        System.out.println("Illegal input(23)!");return -1;}
                    else    sum += 50;
                    break;
                case 'D':
                    if(i < s.length()-1 && (s.charAt(i+1) == 'D')){
                        System.out.println("Illegal input(24)!");return -1;}
                    else    sum += 500;
                    break;
                case 'M':
                    sum += 1000;
                    break;   
                default:
                    break;
            }
        }
        return sum;     
    }
}
```

