---
description: //return >> 略--> >>
---

# Java\_method

### String.method

String.charAt\(i\)

```text
eg. str0 = "apple" , i = 3
    str0.charAt(i) >> 'l'
```

String.indexOf\(str\) 

```text
str0.indexOf(str1)>>
    if str0 包含 str1 : return （str1最初出现在str0的idx）
        eg. str0 = "leapp",str1 = "app", str0.indexOf(str1) >> 2
    elif str0 等于 str1 : return 0
        eg. str0 = "app",str1 = "app", str0.indexOf(str1) >> 0
    else : return -1
        eg. str0 = "app",str1 = "bqp", str0.indexOf(str1) >> -1
```

String.substring\(start\_idx,end\_idx\)

```text
eg. str0 = "apple",str0.length = 5
    str0.substring(0,str0.length-2) >> "app"
```

.length

```text
获取长度
String.length()
int[].length
```

StringBulder

```text
在程序开发过程中，我们常常碰到字符串连接的情况，
方便和直接的方式是通过"+"符号来实现，但是这种方式达到目的的效率比较低，
且每执行一次都会创建一个String对象，即耗时，又浪费空间。
使用StringBuilder类就可以避免这种问题的发生。

StringBuilder strB = new StringBuilder();
System.out.println(strB.append("ch").append("111").append('c'));
//return "ch111c"

https://www.cnblogs.com/songsongblue/p/9798651.html
```

int  &gt; String

```java
int n = 5;
String str = "";
//way1
str = n + "";//产生2个str对象
//way2
str = String.valueOf(n);//只产生一个对象
//way3
str = Integer.toString(n);//
```

String &gt; int

```java
String str = "5";
int i;
//way1
i = Integer.parseInt(str);//静态方法，不会产生多余的对象
//!!如果str为空or""会报错!!
//way2
i = Integer.valueOf(str).intValue();//多产生一个对象

Integer.valueOf("374");//是将字符串解析成Intger对象类型,返回的是Integer   
Integer.parseInt("374");//是将字符串解析成int基本类型,返回的是int
//整数值在 -128到127之间，解析的Integer是同一个对象，不再-128~127之间，数值相同，但地址不同。
```

### Arrays.method

```text
Arrays.copyOf(array,end);
Arrays.sort(array);//quick sort
```

HashSet\_travel

```java
HashSet<Character> set = new HashSet<>();
set.add('1');set.add('2');
set.add('3');set.add('4');
set.add('4');set.add('');
set.add(null);

//Method 1 using Iterator
Iterator<Charactor> iter = set.iterator();
while(iter.hasNext()){
    System.out.print(iter.next()+ " ");
}
//Method 2 using foreach
for(Object obj : set){
    System.out.print(obj + " ");
}
// output null  1 3 4 2
//結果から、HashSetは重複する要素を格納せず
//‘’とnullも格納可能とのことがわかる
//データ保存の順序はないらしい（要確認）
```

Hashmap\_contains

```java
//containsKey
boolean containsKey(Object key)
/*如果此映射包含指定键的映射关系，则返回 true。
更确切地讲，当且仅当此映射包含针对满足
 (key==null ? k==null : key.equals(k)) 的键 k 的映射关系时，
 返回 true。（最多只能有一个这样的映射关系）。 
*/



//containsValue
boolean containsValue(Object value)
/*如果此映射将一个或多个键映射到指定值，则返回 true。
更确切地讲，当且仅当此映射至少包含一个对满足 
(value==null ? v==null : value.equals(v)) 的值 v 的映射关系时，
返回 true。对于大多数 Map 接口的实现而言，
此操作需要的时间可能与映射大小呈线性关系。 
*/
```





