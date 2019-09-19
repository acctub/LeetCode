---
description: 図を描くライブラリ
---

# matplotlib.pyplot

```python
x = list(range(0,10))
y = list(range(10,0))

#リストデータで図を描く
p = plt.plot(x,y,zorder=1)#表示の順番
p = plt.xlabel('X')
p = plt.ylabel('Y')

#直線を描く
p = plt.hlines(mean(count), xmin = 0,xmax = 10, colors="red",zorder=2) 
p = plt.hlines(y=[0,5,10], xmin=0, xmax=10, colors='b', linestyles='dashed', linewidths=1,zorder=3)
plt.show(p)

```

