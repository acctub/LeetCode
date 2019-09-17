---
description: 找出最长的镜像部分字符串
---

# 04. Longest Palindromic Substring

```text
tips
一个长为n的字符串中包含
sigma[i=1;i<=n;i++]个部分字符串
比如abcde包含5个1字符，4个2字符，3个3字符，2个4字符
总共15个部分字符串
除去1字符包含10个也就是
nC2 > n/2(n-1)个部分字符串
(注意，nC2是n个里面不重复的选出2个的意思，
计算的结果和n个字符串里除去1字符的所有
部分字符串的个数相同)
```

### Myfirst Solution\(Time Limit Exceeded\)

```java
class Solution {
    public String longestPalindrome(String s) {
        
        if(s.length() == 0) return "";
        else if(s.length() == 1) return s;
        String rev = reverse(s),ans = s.charAt(0)+"";
        if(rev.equals(s)) return s;
        int len = -1,n = s.length();
        
        for(int i = 0;i < n;i++){
            for(int j = i+2; j <= n; j++){
                int tmp = s.indexOf(rev.substring(i,j));
                int rev_len = rev.substring(i,j).length();
                String r_sub = rev.substring(i,j);
                String o_sub = original_sub(s,i,j);
                
                //部分文字列のインデックスが反転部分文字列の元のインデックスと同じなら
                if(tmp >= 0 && r_sub.equals(o_sub)&& rev_len>len){
                    len = rev_len;
                    ans = r_sub;
                }
            }
        }
        return ans;
    }

    public String reverse(String s){
        StringBuilder str = new StringBuilder(s);
        return str.reverse().toString();
    }
    public String original_sub(String s,int i,int j){
        int start = s.length()-j;
        int end = s.length()-i;
        return s.substring(start,end);
    }
}
```

Solution-1 Expand Around Center O\(n^2\)

```java
class Solution {
    public String longestPalindrome(String s) {
        int n = s.length();
        int start = 0,end = 0;
        StringBuilder rev = new StringBuilder(s);
        rev.reverse();
        
        if(s.length() == 0) return "";
        else if(s.equals(rev))  return s;
        
        for(int i = 0; i < n; i++){
            int odd = get_sub_len(s,i,i);//奇数
            int even = get_sub_len(s,i,i+1);//偶数
            int len = Math.max(odd,even);//subStringの本当の長さ
            
            if(len > (end-start)){//長さを更新する必要がある
                start = i -(len-1)/2;
                end = i + len/2;
            }
        }
        return s.substring(start,end+1);
    }
    public Integer get_sub_len(String s,int L,int R){
        
        while(L >= 0 && R < s.length() && s.charAt(L) == s.charAt(R)){
                L--;R++;
        }
        return R-L-1;
    }
}
/*思路
所有回文都存在一个中心，aba的中心是b，abba的中心是两个b之间。
那么只需要把从头遍历一次字符串，看看以哪个字符或字符间为中心时回文最长就行
因为不知道是奇数回文还是偶数回文，所以每次判断都需要假定奇数和偶数的情况
用函数getsublen来判断以x为中心是否存在回文，回文长度多少。
直到了长度就可以计算回文的开始和结束的index
通过不断更新回文长度和计算index我们就可以找到最长回文。
时间复杂度：
    一个大循环O(n)，每次找回文2*O(n),
    总共O(n^2)
*/
```

Using char List（MostFast）

```java
public class Solution {
    public String longestPalindrome(String s) {
        if (s.length() < 2) {
            return s;
        }
        char[] chars = s.toCharArray();
        int charlen = chars.length;
        int max = 0 , start = 0;
        for(int i = 0 ; i < charlen - max / 2; i ++) {
            int k = i;
            int j = i;
            while(k < charlen - 1 && chars[k] == chars[k + 1]) {
                k ++;
            }
            // After we have scanned duplicate charactor, we don't need to rescan this charactors
            // if you commit this line, it will use `10ms`
            // but now, it use `2ms` :)
            i = k;
            while(j > 0  && k < charlen - 1 && chars[j - 1] == chars[k + 1]) {
                j --;
                k ++;
            }
            int len = k - j + 1;
            if (max <= len){
                start = j;
                max = len;
            }
        }
        return s.substring(start, start + max);
    }
}
```





