# Untitled

```java
class Solution {
    public String convert(String s, int numRows) {
        s = "PAYPALISHIR"; numRows = 4;
        List<List<Character>> Matrix = new ArrayList<>();//char的2d列表
        int n = s.length(), mid = numRows-2;//中间层的长度
        
        for(int i = 0; i < n; i++){
            if(i < (n-numRows-mid)){
                add2List(Matrix,s,i,numRows);i += numRows;
                //此时i跳到中间层的第一个字母位置
                add2List(Matrix,s,i,mid);i += mid-1;
            }else if(i < n){
                add2List(Matrix,s,i,n-i);i = n;
            }
        }
        return s;
    }
    public void add2List(List<List<Character>> Matrix,String s,int i, int row){
        //System.out.print("i="+i+"row="+row);
        String sub = s.substring(i,i+row);//字符串[文字列]
        char[] ch = sub.toCharArray();//数组[配列]
        List<Character> lst = new ArrayList<>();//列表[リスト]
        //List<Character> lst = Arrays.asList(ch);错误！
        //不能直接把基本数据类型的数组转化为列表
        for(int q = 0;q < ch.length;q++){
            lst.add(ch[q]);
        }
        System.out.println(lst);//java可以直接打印列表
        Matrix.add(lst);
    }
}
```

