# X轴方向最小距离搜索

## 开始做实体实验

![](/images/优化算法与生成设计/使用目标函数求最小距离/到两个点距离和最短的坐标/X轴方向最小距离搜索/1a1.jpg)

#### x 轴方向以步长 1 变化时的距离之和

```python
import matplotlib.pyplot as plt
import numpy as np
import random
import math

x = float(input('input any number between 0 and 20: \n'))	  # x = random.uniform(0,20)
y = float(input('input any number between 0 and 15: \n'))	  # y = random.uniform(0,15)

p1 = [2,3]		# the 2D coordinates of existing point A
p2 = [14,12]	# the 2D coordinates of existing point B
p3 = [x,y]		# the 2D coordinates of desired point C

def sum_of_distances(p1,p2,p3):
	sum = math.sqrt((p3[0]-p1[0])**2 + (p3[1]-p1[1])**2) + math.sqrt((p3[0]-p2[0])**2 + (p3[1]-p2[1])**2)
	return sum

init_distances = sum_of_distances(p1, p2, p3)
print(init_distances)

for i in range(1,20):
    p3[0] = p3[0] - 1
    if sum_of_distances(p1, p2, p3) < init_distances:
        print(p3)
        print(sum_of_distances(p1, p2, p3))
        plt.scatter([p3[0]],[p3[1]])

plt.scatter([p1[0],p2[0]],[p1[1],p2[1]])
plt.show()
```

#### x 轴方向以步长 1 变化时距离和减小点的筛选与输出

```python
import matplotlib.pyplot as plt
import numpy as np
import random
import math

x = float(input('input any number between 0 and 20: \n'))	  # x = random.uniform(0,20)
y = float(input('input any number between 0 and 15: \n'))	  # y = random.uniform(0,15)

p1 = [2,3]		# the 2D coordinates of existing point A
p2 = [14,12]	# the 2D coordinates of existing point B
p3 = [x,y]		# the 2D coordinates of desired point C

def sum_of_distances(p1,p2,p3):
	sum = math.sqrt((p3[0]-p1[0])**2 + (p3[1]-p1[1])**2) + math.sqrt((p3[0]-p2[0])**2 + (p3[1]-p2[1])**2)
	return sum

init_distances = sum_of_distances(p1, p2, p3)
print(init_distances)

for i in range(1,20):
	previous_distances = sum_of_distances(p1, p2, p3)
	p3[0] = p3[0] - 1
	moved_distances = sum_of_distances(p1, p2, p3)
	if moved_distances < previous_distances:
		print('At point ',p3,', the total distances is ',moved_distances)
		plt.scatter([p3[0]],[p3[1]])

plt.scatter([p1[0],p2[0]],[p1[1],p2[1]])
plt.show()
```

####  **x 轴方向以可变步长变化时距离和减小点的筛选与输出**

```python
import matplotlib.pyplot as plt
import numpy as np
import random
import math

x = float(input('input any number between 0 and 20: \n'))	  # x = random.uniform(0,20)
y = float(input('input any number between 0 and 15: \n'))	  # y = random.uniform(0,15)
stepsize = float(input('input stepsize between 0 and 1: \n'))	  # x = random.uniform(0,1)

p1 = [2,3]		# the 2D coordinates of existing point A
p2 = [14,12]	# the 2D coordinates of existing point B
p3 = [x,y]		# the 2D coordinates of desired point C

def sum_of_distances(p1,p2,p3):
	sum = math.sqrt((p3[0]-p1[0])**2 + (p3[1]-p1[1])**2) + math.sqrt((p3[0]-p2[0])**2 + (p3[1]-p2[1])**2)
	return sum

init_distances = sum_of_distances(p1, p2, p3)
print(init_distances)

for i in range(1,20):
	previous_distances = sum_of_distances(p1, p2, p3)
	p3[0] = p3[0] - stepsize
	moved_distances = sum_of_distances(p1, p2, p3)
	if moved_distances < previous_distances:
		print('At point ',p3,', the total distances is ',moved_distances)
		plt.scatter([p3[0]],[p3[1]])

plt.scatter([p1[0],p2[0]],[p1[1],p2[1]])
plt.show()
```

```python
import matplotlib.pyplot as plt
import numpy as np
import random
import math

x = float(input('input any number between 0 and 20: \n'))	  # x = random.uniform(0,20)
y = float(input('input any number between 0 and 15: \n'))	  # y = random.uniform(0,15)
stepsize = float(input('input stepsize between 0 and 1: \n'))	  # x = random.uniform(0,1)

p1 = [2,3]		# the 2D coordinates of existing point A
p2 = [14,12]	# the 2D coordinates of existing point B
p3 = [x,y]		# the 2D coordinates of desired point C

def sum_of_distances(p1,p2,p3):
	sum = math.sqrt((p3[0]-p1[0])**2 + (p3[1]-p1[1])**2) + math.sqrt((p3[0]-p2[0])**2 + (p3[1]-p2[1])**2)
	return sum

init_distances = sum_of_distances(p1, p2, p3)
print(init_distances)

for i in range(1,20):
	previous_distances = sum_of_distances(p1, p2, p3)
	p3[0] = p3[0] - stepsize
	moved_distances = sum_of_distances(p1, p2, p3)
	if moved_distances < previous_distances:
		print('At point ',p3,', the total distances is ',moved_distances)
		plt.scatter([p3[0]],[p3[1]])

for i in range(1,20):
	previous_distances = sum_of_distances(p1, p2, p3)
	p3[0] = p3[0] - stepsize/4
	moved_distances = sum_of_distances(p1, p2, p3)
	if moved_distances < previous_distances:
		print('At point ',p3,', the total distances is ',moved_distances)
		plt.scatter([p3[0]],[p3[1]])

plt.scatter([p1[0],p2[0]],[p1[1],p2[1]])
plt.show()
```

## 参考文献及资料

1. 维基百科
	- [Matplotlib](https://en.wikipedia.org/wiki/Matplotlib) | [Matplotlib库](https://en.wikipedia.org/wiki/Matplotlib)
	- [John D. Hunter](https://en.wikipedia.org/wiki/John_D._Hunter#Matplotlib)
	- [**matplotlib.pyplot.plot**](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.plot.html)

