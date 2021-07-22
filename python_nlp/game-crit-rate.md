# Game Crit Rate

```python
import random
import matplotlib.pyplot as plt

#面板爆率
DEFAULT_RATE=0.2

#修改爆率的函数
def balance(Crit_Count,Damage_Count,Crit_Rate, X=5):
    #根据当前暴击次数和击中次数计算当前的真实暴击率
    True_Rate = Crit_Count/(Crit_Count+Damage_Count)
    #真实暴击率低于面板爆率
    if True_Rate < DEFAULT_RATE:
        #面板爆率乘以x倍（最大不超过1）
        Crit_Rate *= X
        Crit_Rate = 1 if Crit_Rate >= 1 else Crit_Rate
    #真实爆率高于面板爆率
    elif True_Rate >= DEFAULT_RATE:
        #面板爆率除以x倍
        Crit_Rate /= 2*X
    #真实爆率等于面板爆率（几乎不可能发生）
    else:
        #什么也不做
        pass
    #返回平衡后的爆率
    return Crit_Rate

#计算并打印统计结果的函数
def show_result(G:int, Rate_List:list):
    print("Group{}--------------------Result".format(G))
    count_1,count_2,count_3 = 0,0,0
    for rate in Rate_List:
        if rate < 0.12 and rate > 0.08:
            count_1 += 1
        elif rate <= 0.05:
            count_2 += 1
        elif rate >= 0.5:
            count_3 += 1
        else:
            pass
    plt.hist(Rate_List, bins=10, alpha=0.5)
    #真实爆率分布在【8%-10%】的概率
    print("Real Cril Rate - [8%-12%]:", count_1/len(Rate_List))
    #真实爆率分布在【0%-5%】的概率
    print("Real Cril Rate - [0%-5%]:", count_2/len(Rate_List))
    #真实爆率分布在【50%-100%】的概率
    print("Real Cril Rate - [50%-100%]:", count_3/len(Rate_List))
    print()

#模拟运行N次攻击实验
def Run_Simulartion(times=50000,bal=False):
    '''times:实验数, bal:是否修正面板爆率'''
    Rate_Lst = []
    for j in range(times):
        Crit_Rate = DEFAULT_RATE
        Damage_Count = 0
        Crit_Count = 0
        #测试条件为打30次怪物
        #测试数量过大的话因为大数定理不用修正爆率最终都会接近面板爆率，这毫无意义
        #因为你打竞技场可能就是几十次攻击就决定胜负了，这就是不公平的所在
        for i in range(30):
            tmp = random.random()
            if tmp <= Crit_Rate:
                Crit_Count += 1
            else:
                Damage_Count += 1
            if bal==True:
                Crit_Rate = balance(Crit_Count, Damage_Count, Crit_Rate)
        #计算30次攻击后得到的真实爆率
        True_Crit_Rate = Crit_Count/(Crit_Count+Damage_Count)
        Rate_Lst.append(True_Crit_Rate)
        
    return Rate_Lst

#看看结果，不修改爆率情况下，在攻击次只有30的情况下分布有多不平衡，啧啧啧啧
show_result(1,Run_Simulartion())
#看看改了以后平衡性改善多少？而且并没有失去随机性哦
show_result(2,Run_Simulartion(bal=True))


#以下是为了分析具体攻击过程中的爆率变化和观察是否暴击的实验
#并最终打印面板爆率和真是爆率的变化图
#真实爆率list
R_Rate_List =[]
#面板爆率list
Crit_Rate_List = []
#面板爆率
Crit_Rate= DEFAULT_RATE
#暴击数，击中数
Crit_Count,Damage_Count = 0,0

for i in range(100):
    tmp = random.random()
    if tmp <= Crit_Rate:
        Crit_Count += 1
    else:
        Damage_Count += 1
    Crit_Rate = balance(Crit_Count, Damage_Count, Crit_Rate)
    Real_Rate = Crit_Count/(Damage_Count+Crit_Count)
    R_Rate_List.append(Real_Rate)
    Crit_Rate_List.append(Crit_Rate)
    #这个取消掉注释就可以观察每次攻击时的爆率是如何变化的
    #print("CD:{}   D:{}   C_Rate:{:.3g}   R_Rate:{:.2g}".format(Crit_Count,Damage_Count,Crit_Rate, Real_Rate))
plt.plot(R_Rate_List)
plt.plot(Crit_Rate_List)
#看好了奥！
```

