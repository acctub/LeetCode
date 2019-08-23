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



