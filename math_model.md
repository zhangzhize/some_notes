##智能算法30个案例分析笔记
### 工具箱篇
#### 谢菲尔德遗传算法工具箱gatbx
**查看版本**
```
v=ver('gatbx')
```

主要函数列表
**创建种群**
* crtbase创建基向量
* crtbp创建任意离散随机种群
* crtrp创建实值初始种群

**适应度计算** 
* ranking基于**排序**的适应度分配
* scaling比率适应度计算
  
**选择函数**
* reins一致随机和基于适应度的重插入
* select高级选择例程
* rws轮盘选择
* sus随机遍历采样

**交叉算子**
* recdis离散重组
* recint中间重组
* recline线性重组
* recmut具有变异特征的线性重组
* recombin高级重组算子
* xovdp两点交叉算子
* xovdprs减少代理的两点交叉
* xovmp通常多点交叉
* xovsh洗牌交叉
* xovshrs减少代理的洗牌交叉
* xovsp单点交叉
* xovsprs较少代理的单点交叉
  
**变异算子**
* mut离散变异
* mutate高级变异函数
* mutbga实值变异
  
**子种群的支持**
* migrate在自重群间交换个体
  
**实用函数**
* bs2rv二进制串到实值的转换
* rep矩阵的复制(matlab自带的repmat也可)


