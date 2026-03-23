# Code：绘出距离函数的图像

## 开始做实体实验

![](/images/优化算法与生成设计/使用目标函数求最小距离/到两个点距离和最短的坐标/Code：绘出距离函数的图像/1a1.png)


```python
import matplotlib.pyplot as plt
from matplotlib import cm
import numpy as np

# ---------------- 坐标系初始化 ----------------
fig = plt.figure()
ax = fig.add_subplot(111, projection='3d')

# ---------------- 坐标网格生成 ----------------
X = np.arange(0, 20, 0.25)   # x coordinate of point C
Y = np.arange(0, 15, 0.25)   # y coordinate of point C
X, Y = np.meshgrid(X, Y)     # 2D grid [x, y]

# ---------------- 距离场计算 ----------------
# fixed point A: [2, 3]
d1 = np.sqrt((X - 2)**2 + (Y - 3)**2)

# fixed point B: [14, 12]
d2 = np.sqrt((X - 14)**2 + (Y - 12)**2)

# total distance field
Z = d1 + d2

# ---------------- 绘制方法 ----------------
ax.plot_surface(
    X, Y, Z,
    rstride=1,
    cstride=1,
    cmap=cm.coolwarm,
    linewidth=0,
    antialiased=False
)

plt.show()
```

## 参考文献及资料

1. 维基百科
	- [Matplotlib](https://en.wikipedia.org/wiki/Matplotlib) | [Matplotlib库](https://en.wikipedia.org/wiki/Matplotlib)
	- [John D. Hunter](https://en.wikipedia.org/wiki/John_D._Hunter#Matplotlib)
	- [**matplotlib.pyplot.plot**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.plot.html)

