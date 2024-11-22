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

```
y3 = y1 + y2
# 对 y3 进行快速傅里叶变换
F = np.fft.fft(y3)  # 傅里叶变换结果
freqs = np.fft.fftfreq(len(t), d=(t[1] - t[0]))  # 对应频率
```

```
# 仅取正频率部分
positive_freqs = freqs[freqs >= 0]
positive_F = np.abs(F[freqs >= 0])  # 幅值谱

# 绘制频谱
threshold = 0.1 * np.max(positive_F)  # 设置一个阈值，过滤噪声
print("Significant Frequencies:")
for freq, amp in zip(positive_freqs, positive_F):
    if amp > threshold:
        print(f"Frequency: {freq:.2f} Hz, Amplitude: {amp:.2f}")
```

结果显示有两段显著的频率，分别为2hz和3hz

Significant Frequencies:

Frequency: 2.00 Hz, Amplitude: 1000.00

Frequency: 3.00 Hz, Amplitude: 1000.00

```
plt.figure(figsize=(12, 4))
plt.plot(positive_freqs, positive_F, label="Amplitude Spectrum")
plt.title("Frequency Spectrum of y3")
plt.xlabel("Frequency (Hz)")
plt.ylabel("Amplitude")
plt.xlim(0,10)
plt.grid()
plt.legend()
plt.show()
```
