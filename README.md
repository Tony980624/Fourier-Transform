创建两个频率不同的周期函数， 现实生活中一个声音可能是有多种声音叠加的，比如音乐

```
import numpy as np
import matplotlib.pyplot as plt
# 时间
t = np.arange(0,2,0.001)
# 频率为3HZ的cos函数
f1 = 3
y1 = np.cos(2*np.pi*f1*t)
# 频率为4hz的sin函数
f2 = 4
y2 = np.sin(np.pi*f2*t)
```

画出两个函数,以及它们的叠加（和）在0到12 $\pi$ 之间的变化情况

```
# 创建图形
plt.figure(figsize=(10, 6))

# 上图 2sin(x)
plt.subplot(3, 1, 1)
plt.plot(t, y1, label='sin_wave')
plt.xlabel('x')
plt.ylabel('y')
plt.grid()
plt.legend()

# 下图 cos(2x)
plt.subplot(3, 1, 2)
plt.plot(t, y2, label='cos_wave', color='orange')
plt.legend()
plt.ylabel('y')
plt.grid()
plt

# 下图 cos(2x)
plt.subplot(3, 1, 3)
plt.plot(t, y2+y1, label='wave', color='gray')
plt.legend()
plt.ylabel('y')
plt.grid()
plt
```

![a00](https://github.com/Tony980624/Fourier-Transform/blob/main/images/output.png)


