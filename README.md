创建两个频率不同的周期函数， 现实生活中一个声音可能是有多种声音叠加的，比如音乐

```
import numpy as np
import matplotlib.pyplot as plt
# 定义域
x = np.linspace(0, 12 * np.pi, 500)
# 函数1
y1 = 2 * np.sin(x)
# 函数2
y2 = np.cos(2 * x)
```

画出两个函数在0到12 $\pi$ 之间的变化情况

```
# 创建图形
plt.figure(figsize=(10, 6))

# 上图 2sin(x)
plt.subplot(2, 1, 1) # 两行一列，其中第一张图
plt.plot(x, y1, label='2sin(x)')
plt.title('2sin(x)')
plt.xlabel('x')
plt.ylabel('y')
plt.grid()
plt.legend()

# 下图 cos(2x)
plt.subplot(2, 1, 2)
plt.plot(x, y2, label='cos(2x)', color='orange')
plt.title('cos(2x)')
plt.xlabel('x')
plt.ylabel('y')
plt.grid()
plt
```

