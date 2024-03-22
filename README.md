***
## 参数选取
$L=1mH$, $C=1000\mu F$, $R_{res}=150k\Omega$, $f=20kHz$
***
## 训练工况
输入 $E=120V$

输出 $V_{out}=60V$

功率变化 $200W \stackrel{0.14s}{\longrightarrow} 800W \stackrel{0.2s}{\longrightarrow} 200W$ 

action选取范围 $[0.46,0.47,0.48,0.49,0.50,0.51,0.52,0.53,0.54,0.55,0.56,0.57]$
***
## 训练结果
![](https://github.com/Flow0312/20211229/blob/main/train.png?raw=true)
### 工况 200-800-200W
+ 静差$0.03V$左右
+ 下超调接近$6V$，上超调不到$4V$
+ 恢复时间$5ms$
***
## 重构网络仿真结果
![](https://github.com/Flow0312/20211229/blob/main/net.png?raw=true)
### 工况同样为 200-800-200W
+ 静差$0.6V$左右
+ 上下超调与训练结果几乎一致，下超调接近$6V$，上超调不到$4V$
+ 恢复时间$5ms$
+ **区别为$800W$工况下抖动减小**
***
## 实验结果（对比PI）（无迁移）
左一为输出电压变化，中间为电流变化，右一为占空比变化
### PI实验结果Controldesk截图
![](https://github.com/Flow0312/20211229/blob/main/pi.png?raw=true)
### DRL实验结果Controldesk截图
![](https://github.com/Flow0312/20211229/blob/main/drl.png?raw=true)
### 某一时刻控制器由DRL切换至PI后Controldesk截图
![](https://github.com/Flow0312/20211229/blob/main/DRL-pi.png?raw=true)
#### 说明
+ 无论是PI控制器产生的占空比以及未截出的开环占空比波动均明显小于drl控制器产生
+ DRL的电压波动为上下$1V$,pi为上下$0.4V$
+ 瞬态方面DRL控制器明显优于PI控制器，但超调量与仿真不符，原本$5V$左右的仿真超调在实验中体现为$0.4V$左右的静差
+ 稳态静差始终存在
***
## 示波器结果
采样倍率0.1，偏置5V
### PI控制器对应输出电压
![](https://github.com/Flow0312/20211229/blob/main/ocpi.png?raw=true)
### DRL控制器对应输出电压
![](https://github.com/Flow0312/20211229/blob/main/ocdrl.png?raw=true)
