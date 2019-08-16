---
description: '给定一个只包含字符''（''，''）''，''{''，''}''，''[''，'']''的字符串，确定输入字符串是否合法。'
---

# 20. Valid Parentheses

### Mycode

```java
class Solution {
    public boolean isValid(String s) {
        
        //s = "([)]";
        
        if (s.length() == 0) return true;
        
        Stack<Integer> st = new Stack<Integer>();
        System.out.println("stack: " + st + "---------------");
        
        for(int i = 0; i < s.length() ; i++){
            
            if(st.isEmpty()){
                Push(st,(int)s.charAt(i));
            }
            else{
                int tmp = st.peek();
                //System.out.println("tmp ->" + tmp);
                switch (tmp){
                    case 40:
                        if(s.charAt(i) == ')') Pop(st);
                        else Push(st,(int)s.charAt(i));
                        break;
                    case 91:
                        if(s.charAt(i) == ']') Pop(st);
                        else Push(st,(int)s.charAt(i));
                        break;
                    case 123:
                        if(s.charAt(i) == '}') Pop(st);
                        else Push(st,(int)s.charAt(i));
                        break;
                    default:
                        System.out.println("input error!");
                        break;
                }
            }
            
        }
        
        if(st.isEmpty()) return true;
        else return false;
    }
    
    static void Push(Stack<Integer> st, int el){
        st.push(el);
        System.out.println("push(" + el + ")");
        System.out.println("stack: " + st);
    }
    static void Pop(Stack<Integer> st){

        if(st.isEmpty() == true) 
            System.out.println("stack is empty!");
        else{
            int el = (int)st.pop();
            System.out.println("pop<" + el + ">");
            System.out.println("stack: " + st);
        }
    }
}
```

