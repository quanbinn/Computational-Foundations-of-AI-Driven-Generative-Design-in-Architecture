# 矩形中心点在X轴方向投影距离

```python
import matplotlib.pyplot as plt

# 设置绘图比例相等
plt.axis('equal')


class Rectangle_center:
    """以中心点坐标创建的矩形类"""
    def __init__(self, xOfCenter, yOfCenter, length, width):
        self.xOfCenter = xOfCenter
        self.yOfCenter = yOfCenter

        # 根据中心点计算矩形四个角
        self.x1 = xOfCenter - length / 2
        self.y1 = yOfCenter - width / 2
        self.x2 = xOfCenter + length / 2
        self.y2 = yOfCenter + width / 2

        self.length = length
        self.width = width        

    # 获取属性方法
    def getlength(self): return self.length
    def getwidth(self): return self.width

    # 获取中心点
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


# ==========================================================
# X轴方向：中心点投影距离（修改核心）
# ==========================================================
def distance_of_centers_in_xaxis(rect1, rect2):
    """
    两个矩形中心点在 X 轴方向的投影距离
    本质：只比较 x 坐标差值
    """
    x1 = rect1.centralCoordinates()[0]
    x2 = rect2.centralCoordinates()[0]

    return abs(x2 - x1)


# ==========================================================
# 创建矩形并绘制
# ==========================================================
rect1 = Rectangle_center(0, 0, 10, 10)
rect1.render()

rect2 = Rectangle_center(3, 15, 5, 5)
rect2.render()


# ==========================================================
# 计算中心点 X 轴投影距离
# ==========================================================
dist_x = distance_of_centers_in_xaxis(rect1, rect2)

print('两个矩形中心点在X轴方向的投影距离是：', dist_x)

plt.show()
```