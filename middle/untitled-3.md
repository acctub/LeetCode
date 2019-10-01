# Untitled

```text
class Solution {
    public List<String> letterCombinations(String digits) {
        
        if(digits.equals("")) return new ArrayList<>();//空であれば空リストを返す
        
        if(digits.length() == 1){
            
            List<String> str = new ArrayList<>();//sbのリストを作る
            int i = (int)digits.charAt(0)-'0';//一番小さいのは２
            boolean sig = (i==7||i==9);
            boolean sig2 =(i==8||i==9);
            if(i == 8){
                str.add("t");str.add("u");
                str.add("v");
                return str;
            }
            i -= 2;
            i = i*3 + (sig2?1:0);
            //System.out.println("i:"+i);
            if(i < 0 || i > 24) return str;
            for(int j = sig?(i+4):(i+3);i < j;i++){
                str.add(""+(char)(97+i));
            }
            System.out.println(str);
            return str;
        }     
        Character c = digits.charAt(digits.length()-1);
        //debug
        //System.out.print("s:"+digits.substring(0,digits.length()-1)); 
        //System.out.println(" c:"+c);
        //debug
        List<String> str = letterCombinations(digits.substring(0,digits.length()-1));
        
        List<Character> ch = itoa(c);//'数字'を入力し、‘char’のリストが返す
        List<String> s = new ArrayList<>();
        for(int i = 0; i < str.size(); i++){
            for(int j = 0; j < 3; j++){
                s.add(str.get(i)+(""+ch.get(j)));
            }
        }
        
        return s;
    }
    public List<Character> itoa(Character c){
        List<Character> ch = new ArrayList<>();
        int i = (int)c-'0'-2;
        System.out.println(i);
        i = 
        boolean sig = (i==7||i==9);
        for(int j = sig?(i+4):(i+3);i < j;i++){
            ch.add((char)(97+i));
        }
        System.out.println(ch);
        return ch;
    }
}
```

