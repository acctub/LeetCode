---
description: 数字键盘输入英文
---

# 17. Letter Combinations of a Phone Number

### MyCode  Using recursion\_\_\_O\(n^m\) m=len,1ms

```java
class Solution {
    public List<String> letterCombinations(String digits) {
        
        if(digits.equals("")) return new ArrayList<>();//空であれば空リストを返す
        if(digits.length() == 1)
            return itoa(digits.charAt(0));
        
        Character c = digits.charAt(digits.length()-1);
        List<String> str = letterCombinations(digits.substring(0,digits.length()-1));
        List<String> ch = itoa(c);//'数字'を入力し、‘char’のリストが返す
        List<String> ans = new ArrayList<>();
        
        for(int i = 0; i < str.size(); i++)
            for(int j = 0; j < ch.size(); j++)
                ans.add(str.get(i)+ch.get(j));//str+str
        return ans;
    }
    public List<String> itoa(Character c){
        
        List<String> str = new ArrayList<>();//新しい文字列リストを作成する
        int i = (int)c-'0';//strの数字をintに置換
        
        boolean sig = (i==7||i==9);//7と9のキーはアルファベット4つあるからマークする
        boolean sig2 =(i==8||i==9);//8と9のキーはアルファベットのインデックスが一つ偏移(*)するからマーク
        //数字と文字の等差数列(*)を作るためiの値を0からとする
        i -= 2;i = i*3 + (sig2?1:0);//8,9なら+1
        
        if(i < 0 || i > 22) return str;
        for(int j = sig?(i+4):(i+3);i < j;i++)//7,9なら4つ取り出す
            str.add(""+(char)(97+i));
        return str;
    }
}
```

