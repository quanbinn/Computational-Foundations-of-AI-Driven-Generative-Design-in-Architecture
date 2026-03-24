# 两个长方体的底面中心点在X轴方向投影距离

```python
import matplotlib.pyplot as plt

# ---------------- 创建3D坐标系 ----------------
fig = plt.figure()
ax = fig.add_subplot(111, projection='3d')

ax.set_xlim((0, 50))
ax.set_ylim((0, 50))
ax.set_zlim((0, 50))

# ---------------- Cuboid（长方体类） ----------------
class Cuboid:
    """
    教学版长方体：
    用中心点 + 尺寸定义一个3D盒子
    """

    def __init__(self, xOfCenter, yOfCenter, zOfCenter, width, height, depth):

        # ---------------- 中心点坐标 ----------------
        self.xOfCenter = xOfCenter
        self.yOfCenter = yOfCenter
        self.zOfCenter = zOfCenter

        # 尺寸
        self.width = width
        self.height = height
        self.depth = depth

    # ---------------- 获取中心点 ----------------
    def base_center(self):
        """
        返回中心点坐标 (x, y, z)
        """
        return [self.xOfCenter, self.yOfCenter, self.zOfCenter]

    # ---------------- 绘制方法 ----------------
    def render(self):

        x = self.xOfCenter - self.width / 2
        y = self.yOfCenter - self.height / 2
        z = self.zOfCenter - self.depth / 2

        ax.bar3d(
            x, y, z,
            self.width,
            self.height,
            self.depth,
            color="green",
            alpha=0.5
        )

# ---------------- X轴投影距离函数 ----------------
def distance_x_projection(cuboid1, cuboid2):
    """
    计算两个长方体中心点在 X 轴方向的投影距离
    """

    x1, _, _ = cuboid1.base_center()
    x2, _, _ = cuboid2.base_center()

    return abs(x2 - x1)

# ---------------- 示例数据 ----------------
cuboid1 = Cuboid(10, 20, 8, 16, 8, 16)
cuboid2 = Cuboid(15, 20, 4, 16, 16, 24)

# ---------------- 绘制方法 ----------------
cuboid1.render()
cuboid2.render()

# ---------------- 计算X轴投影距离 ----------------
print("X轴投影距离：", distance_x_projection(cuboid1, cuboid2))

# ---------------- 显示结果 ----------------
plt.show()
```