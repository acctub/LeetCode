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
        eg. str0 = "app",str1 = "app", str0.indexOf(str1) >> -1
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



