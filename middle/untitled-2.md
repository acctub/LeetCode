---
description: 将字符串转化为Z形字符串
---

# 06. ZigZag Conversion

```text
eg:"PAYPALISHIRING"
P   A   H   N
A P L S I I G
Y   I   R
```

### MyCode 15ms

```java
class Solution {
    public String convert(String s, int numRows) {
        //s ="PAYPALISHIRING"; numRows = 3;
        
        if(s.length() < 2 || numRows >= s.length()) return s;
        
        List<List<Character>> Matrix = new ArrayList<>();//char的2d列表
        int n = s.length(),mid = numRows-2;
        if( n <=2 || numRows == 1)
            mid = 0;//中间层的长度
        
        int looptime = n/(numRows+mid);
        int extra = n%(numRows+mid);int i = 0;
        
        if((numRows+mid) > n) {
            looptime = 1;
            extra = 0;
        }
        
        for(int j = 0; j < looptime; j++){
            add2List(Matrix,s,i,numRows,0);i += numRows;
            add2List(Matrix,s,i,mid,1);i += mid;
        }
        while(extra >= numRows){
            add2List(Matrix,s,i,numRows,0);
            extra -= numRows;
            i += numRows;
            if(extra > 0){
                add2List(Matrix,s,i,extra,1);
                i += extra;
            }
        }
        if(extra > 0){
            add2List(Matrix,s,i,extra,2);
            i += extra;
        }
        return conversion(Matrix);
    }
    public void add2List(List<List<Character>> Matrix,String s,int i, int row,int flag){
        String sub = new String();//字符串[文字列]
        if((i+row)>s.length())
            sub = s.substring(i,s.length());
        else
            sub = s.substring(i,i+row);
        
        if(flag == 1){
            StringBuilder tmp = new StringBuilder(sub);
            tmp.reverse();
            sub = tmp.toString();
            sub = "#"+sub+"#";
        }
        else if(flag == 2){
            List<Character> tmp = Matrix.get(0);
            while(sub.length() < tmp.size())
                sub = sub+"#";            
        }
        char[] ch = sub.toCharArray();//数组[配列]
        List<Character> lst = new ArrayList<>();//列表[リスト]
        //List<Character> lst = Arrays.asList(ch);错误！
        //不能直接把基本数据类型的数组转化为列表
        for(int q = 0;q < ch.length;q++)
            lst.add(ch[q]);
        Matrix.add(lst);
    }
    public String conversion(List<List<Character>> Matrix){
        int n = Matrix.size();       
        List<Character> m0 = Matrix.get(0);
        int m = m0.size();
        StringBuilder ans = new StringBuilder();
        
        for(int i = 0; i < m; i++){//循环n次,取Matrix的第i列元素
            for(int j = 0; j < n;j++){
                List<Character> tmp = Matrix.get(j);
                while(tmp.size() < m){
                    tmp.add(0,'#');     
                }   
                if( i < tmp.size() && tmp.get(i) != '#')
                    ans.append(tmp.get(i));
            }
        }
        return ans.toString();
    }
}
```

### Solution-1 O\(n\) n == len\(s\)---6ms

```java
class Solution {
    public String convert(String s, int numRows) {
        
        if (numRows <= 1) return s;
        
        List<StringBuilder> rows = new ArrayList<StringBuilder>();
        StringBuilder ans = new StringBuilder();
        
        //因为要将Z字形字符串逐行读取，故此处初始化行数。
        //一般而言行数等于Z字的横长，但对于s.length()<numRows的情况
        //行数等于len，因为字符串长度还不够一个Z字的横长。
        for(int i = 0; i < Math.min(numRows,s.length());i++){
            rows.add(new StringBuilder());//List->add
        }

        //设一个布尔量，用于控制写Z字的方向
        int i = 0;boolean flag = false;//true++ false--
        
        //如果写道Z字转角就反向，正向的话i++反向i--
        for(char c: s.toCharArray()){
            StringBuilder tmp = rows.get(i);
            tmp.append(c);
            if( i == 0 || i == numRows-1) flag = !flag;//boolean reverse
            i += flag? 1:-1;
        }
        
        for(StringBuilder row : rows){
            ans.append(row);//StringBuilder->append
        }
        return ans.toString();
    }
}

```

### Solution-2 O\(n\)n == len\(s\)---3ms

```java
class Solution {
    public String convert(String s, int numRows) {

        if (numRows <= 1) return s;

        StringBuilder ret = new StringBuilder();
        int n = s.length();
        int cycleLen = 2 * numRows - 2;

        for (int i = 0; i < numRows; i++) {
            for (int j = 0; j + i < n; j += cycleLen) {
                ret.append(s.charAt(j + i));
                //System.out.print(s.charAt(j + i));
                if (i != 0 && i != numRows - 1 && j + cycleLen - i < n){
                    ret.append(s.charAt(j + cycleLen - i));
                    //System.out.print("["+s.charAt(j + cycleLen - i)+"]");
                }       
            }
            //System.out.println();
        }
        return ret.toString();
    }
}
//根据计算z形字符串所构成的z字最小周期来推演
```

