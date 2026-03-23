# Y轴方向最小距离搜索

## 开始做实体实验

![](/images/优化算法与生成设计/使用目标函数求最小距离/到两个点距离和最短的坐标/Y轴方向最小距离搜索/1a1.jpg)

#### y 轴方向以步长 1 变化时的距离和计算

```python
import matplotlib.pyplot as plt
import numpy as np
import random
import math

# ---------------- 输入数据 ----------------
x = float(input('input any number between 0 and 20: \n'))  # x = random.uniform(0,20)
y = float(input('input any number between 0 and 15: \n'))  # y = random.uniform(0,15)

# ---------------- 固定点定义 ----------------
p1 = [2, 3]     # the 2D coordinates of existing point A
p2 = [14, 12]   # the 2D coordinates of existing point B
p3 = [x, y]     # the 2D coordinates of desired point C

# ---------------- 距离函数 ----------------
def sum_of_distances(p1, p2, p3):
    total = (
        math.sqrt((p3[0] - p1[0])**2 + (p3[1] - p1[1])**2) +
        math.sqrt((p3[0] - p2[0])**2 + (p3[1] - p2[1])**2)
    )
    return total

# ---------------- 初始距离 ----------------
init_distances = sum_of_distances(p1, p2, p3)
print(init_distances)

# ---------------- 搜索过程 ----------------
for i in range(1, 20):

    # move only in Y direction
    p3[1] = p3[1] + 1

    if sum_of_distances(p1, p2, p3) < init_distances:
        print(p3)
        print(sum_of_distances(p1, p2, p3))

        # ---------------- 绘制方法 ----------------
        plt.scatter([p3[0]], [p3[1]])

# ---------------- 绘制固定点 ----------------
plt.scatter([p1[0], p2[0]], [p1[1], p2[1]])

plt.show()
```

#### y轴方向以可变步长变化时距离和递减点的筛选与输出

```python
import matplotlib.pyplot as plt
import numpy as np
import random
import math

# ---------------- 输入数据 ----------------
x = float(input('input any number between 0 and 20: \n'))  # x = random.uniform(0,20)
y = float(input('input any number between 0 and 15: \n'))  # y = random.uniform(0,15)
stepsize = float(input('input stepsize between 0 and 1: \n'))  # x = random.uniform(0,1)

# ---------------- 固定点定义 ----------------
p1 = [2, 3]     # the 2D coordinates of existing point A
p2 = [14, 12]   # the 2D coordinates of existing point B
p3 = [x, y]     # the 2D coordinates of desired point C

# ---------------- 距离函数 ----------------
def sum_of_distances(p1, p2, p3):
    total = (
        math.sqrt((p3[0] - p1[0])**2 + (p3[1] - p1[1])**2) +
        math.sqrt((p3[0] - p2[0])**2 + (p3[1] - p2[1])**2)
    )
    return total

# ---------------- 初始状态 ----------------
init_distances = sum_of_distances(p1, p2, p3)
print(init_distances)

# ---------------- 搜索过程 ----------------
for i in range(1, 20):

    previous_distances = sum_of_distances(p1, p2, p3)

    # move in Y direction using step size
    p3[1] = p3[1] + stepsize

    moved_distances = sum_of_distances(p1, p2, p3)

    if moved_distances < previous_distances:
        print('At point', p3, ', the total distances is', moved_distances)

        # ---------------- 绘制方法 ----------------
        plt.scatter([p3[0]], [p3[1]])

# ---------------- 绘制固定点 ----------------
plt.scatter([p1[0], p2[0]], [p1[1], p2[1]])

plt.show()
```

```python
import matplotlib.pyplot as plt
import numpy as np
import random
import math

# ---------------- 输入数据 ----------------
x = float(input('input any number between 0 and 20: \n'))  # x = random.uniform(0,20)
y = float(input('input any number between 0 and 15: \n'))  # y = random.uniform(0,15)
stepsize = float(input('input stepsize between 0 and 1: \n'))  # x = random.uniform(0,1)

# ---------------- 固定点定义 ----------------
p1 = [2, 3]     # the 2D coordinates of existing point A
p2 = [14, 12]   # the 2D coordinates of existing point B
p3 = [x, y]     # the 2D coordinates of desired point C

# ---------------- 距离函数 ----------------
def sum_of_distances(p1, p2, p3):
    total = (
        math.sqrt((p3[0] - p1[0])**2 + (p3[1] - p1[1])**2) +
        math.sqrt((p3[0] - p2[0])**2 + (p3[1] - p2[1])**2)
    )
    return total

# ---------------- 初始状态 ----------------
init_distances = sum_of_distances(p1, p2, p3)
print(init_distances)

# ---------------- 粗粒度搜索（stepsize） ----------------
for i in range(1, 20):

    previous_distances = sum_of_distances(p1, p2, p3)

    p3[1] = p3[1] + stepsize

    moved_distances = sum_of_distances(p1, p2, p3)

    if moved_distances < previous_distances:
        print('At point', p3, ', the total distances is', moved_distances)

        # ---------------- 绘制方法 ----------------
        plt.scatter([p3[0]], [p3[1]])

# ---------------- 细粒度搜索（stepsize/10） ----------------
for i in range(1, 20):

    previous_distances = sum_of_distances(p1, p2, p3)

    p3[1] = p3[1] + stepsize / 10

    moved_distances = sum_of_distances(p1, p2, p3)

    if moved_distances < previous_distances:
        print('At point', p3, ', the total distances is', moved_distances)

        # ---------------- 绘制方法 ----------------
        plt.scatter([p3[0]], [p3[1]])

# ---------------- 绘制固定点 ----------------
plt.scatter([p1[0], p2[0]], [p1[1], p2[1]])

plt.show()
```

## 参考文献及资料

1. 维基百科
	- [Matplotlib](https://en.wikipedia.org/wiki/Matplotlib) | [Matplotlib库](https://en.wikipedia.org/wiki/Matplotlib)
	- [John D. Hunter](https://en.wikipedia.org/wiki/John_D._Hunter#Matplotlib)
	- [**matplotlib.pyplot.plot**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.plot.html)

