# 两个长方体的底面中心点在Y轴方向投影距离

```python
import matplotlib.pyplot as plt

# ==========================================================
# 创建3D坐标系
# ==========================================================
fig = plt.figure()
ax = fig.add_subplot(111, projection='3d')

ax.set_xlim((0, 50))
ax.set_ylim((0, 50))
ax.set_zlim((0, 50))


# ==========================================================
# Cuboid（长方体类）
# ==========================================================
class Cuboid:
    """
    教学版长方体：
    用中心点 + 尺寸定义一个3D盒子
    """

    def __init__(self, xOfCenter, yOfCenter, zOfCenter, width, height, depth):

        # =========================
        # 中心点坐标
        # =========================
        self.xOfCenter = xOfCenter
        self.yOfCenter = yOfCenter
        self.zOfCenter = zOfCenter

        # 尺寸
        self.width = width    # X方向
        self.height = height  # Y方向
        self.depth = depth    # Z方向

    # ==========================================================
    # 获取中心点
    # ==========================================================
    def base_center(self):
        """
        返回中心点坐标 (x, y, z)
        """
        return [self.xOfCenter, self.yOfCenter, self.zOfCenter]

    # ==========================================================
    # 3D绘制
    # ==========================================================
    def render(self):
        """
        绘制长方体
        """

        # bar3d需要左下角坐标，所以要做转换
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


# ==========================================================
# Y轴投影距离（核心函数）
# ==========================================================
def distance_y_projection(cuboid1, cuboid2):
    """
    计算两个长方体中心点在 Y 轴方向的投影距离
    """

    _, y1, _ = cuboid1.base_center()
    _, y2, _ = cuboid2.base_center()

    return abs(y2 - y1)


# ==========================================================
# 示例数据
# ==========================================================
cuboid1 = Cuboid(10, 20, 8, 16, 8, 16)
cuboid2 = Cuboid(15, 20, 4, 16, 16, 24)

# ==========================================================
# 绘制
# ==========================================================
cuboid1.render()
cuboid2.render()

# ==========================================================
# 计算Y轴投影距离
# ==========================================================
print("Y轴投影距离：", distance_y_projection(cuboid1, cuboid2))

# ==========================================================
# 显示
# ==========================================================
plt.show()
```