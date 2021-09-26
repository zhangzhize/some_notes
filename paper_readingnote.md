# 查阅论文，随意记录

## 第一篇
**title**:[Stability and Control of a Pacing Quadruped Using Stabilizing Switching Design](https://ieeexplore.ieee.org/document/9528029)

**摘要**：使用**状态反馈切换**来控制和稳定行走的四足机器人。四足动物通适当的方式切换位姿来实现**动态稳定性**。这篇文章提出一种基于他们系统的每组方程的线性化模型的**状态反馈切换定律**，使得在roll方向上稳定机器人。

## 第二篇
**title**:[MPC-based control strategy of a neuro-inspired quadruped robot](https://ieeexplore.ieee.org/document/9533394)

**摘要**：将模型预测控制（MPC）策略应用于具有中央模式生成器（CPG）神经元运动架构的四足机器人的运动。

## 第四篇
**title**:[Online Learning of Unknown Dynamics for Model-Based Controllers in Legged Locomotion](https://ieeexplore.ieee.org/document/9525285)

**摘要**：由于模型如果不准确地代表真实的动力学时，基于模型的控制器的性能会受到严重影响。因此这篇文章，通过沿着机器人当前的轨迹**学习**一个随时间变化的**局部线性残差模型**，以补偿控制器模型的预测误差。

![方法框图](/home/z/图片/ss.png)
> 基于模型的控制器运行时，将数据收集道到滑动窗口数据集中，并进行监督学习以估计残差参数a～、b～，然后它们被用来改进控制器背后的模型。
