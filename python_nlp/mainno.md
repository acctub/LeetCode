# \_\_main\_\_変数の意味

```python
#每个python文件都包含一个内置变量__name__，
#当文件a作为主函数（主要流程？主要脚本？）执行时，文件a的__name__变量等于"__main__"，
#当文件a被当作模块import进文件b后再被执行时，文件a的变量__name__等于模块名（文件名）
#列如：

import numpy as np 

print(__name__)#当前正在执行的主文件。
#__main__
print(np.__name__)#numpy库也可以理解为一个外来的模块
#numpy


#结合上面所说的，下面这个if语句的含义就是，判断某文件a是否是正在执行的主文件
if __name__=="__main__":
    print("this is main function!!")
    
if np.__name__=="__main__":
    print("os is main function")
else:
    print(np.__name__ + " is not main function")
```

