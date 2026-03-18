# Y轴方向投影距离

```python
import matplotlib.pyplot as plt

# 设置绘图比例相等
plt.axis('equal')

class Rectangle_center:
    """以中心点坐标创建的矩形类"""
    def __init__(self, xOfCenter, yOfCenter, length, width):
        self.xOfCenter = xOfCenter
        self.yOfCenter = yOfCenter
        # 根据中心点计算矩形左下角(x1, y1)和右上角(x2, y2)坐标
        self.x1 = xOfCenter - length / 2
        self.y1 = yOfCenter - width / 2
        self.x2 = xOfCenter + length / 2
        self.y2 = yOfCenter + width / 2
        self.length = length
        self.width = width        

    # 获取属性方法
    def getx1(self): return self.x1
    def gety1(self): return self.y1
    def getx2(self): return self.x2
    def gety2(self): return self.y2
    def getlength(self): return self.length
    def getwidth(self): return self.width
    def getCenter(self): return [self.xOfCenter, self.yOfCenter]

    # 计算面积
    def area(self):
        return self.length * self.width

    # 获取中心点坐标
    def centralCoordinates(self):
        return [self.xOfCenter, self.yOfCenter]

    # 绘制矩形
    def render(self):
        p1 = [self.x1, self.y1]
        p2 = [self.x2, self.y1]
        p3 = [self.x2, self.y2]
        p4 = [self.x1, self.y2]
        plt.plot([p1[0], p2[0]], [p1[1], p2[1]], color="green")
        plt.plot([p2[0], p3[0]], [p2[1], p3[1]], color="green")
        plt.plot([p3[0], p4[0]], [p3[1], p4[1]], color="green")
        plt.plot([p4[0], p1[0]], [p4[1], p1[1]], color="green")

# 计算两个矩形在Y轴方向上最近边缘的垂直距离
def distance_of_edges_in_yaxis(rect1, rect2):
    """
    计算两个矩形在Y轴方向上最近边缘的垂直距离
    输入：两个 Rectangle_center 实例
    输出：边缘距离（可能为负数，表示重叠）
    """
    # 获取中心点Y坐标
    y1_center = rect1.centralCoordinates()[1]
    y2_center = rect2.centralCoordinates()[1]
    # 中心点垂直距离
    distance_between_centers = abs(y2_center - y1_center)
    # 减去各矩形垂直半宽得到边缘间距离
    distance_between_edges = distance_between_centers - (rect1.getwidth()/2 + rect2.getwidth()/2)
    return distance_between_edges

# 创建矩形并绘制
rect1 = Rectangle_center(0, 0, 10, 10)
rect1.render()

rect2 = Rectangle_center(3, 3, 5, 5)
rect2.render()   

# 计算Y轴方向上边缘距离
dist_y = distance_of_edges_in_yaxis(rect1, rect2)
print('两个矩形在Y轴方向上最近边缘的垂直距离是：', dist_y)

plt.show()
```