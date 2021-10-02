# 查阅论文，随意记录

## 第一篇
**title**:[Stability and Control of a Pacing Quadruped Using Stabilizing Switching Design](https://ieeexplore.ieee.org/document/9528029)

**摘要**：使用**状态反馈切换**来控制和稳定行走的四足机器人。四足动物通适当的方式切换位姿来实现**动态稳定性**。这篇文章提出一种基于他们系统的每组方程的线性化模型的**状态反馈切换定律**，使得在roll方向上稳定机器人。

## 第二篇
**title**:[MPC-based control strategy of a neuro-inspired quadruped robot](https://ieeexplore.ieee.org/document/9533394)

**摘要**：将模型预测控制（MPC）策略应用于具有中央模式生成器（CPG）神经元运动架构的四足机器人的运动。

## 第三篇
**title**:[Online Learning of Unknown Dynamics for Model-Based Controllers in Legged Locomotion](https://ieeexplore.ieee.org/document/9525285)

**摘要**：由于模型如果不准确地代表真实的动力学时，基于模型的控制器的性能会受到严重影响。因此这篇文章，通过沿着机器人当前的轨迹**学习**一个随时间变化的**局部线性残差模型**，以补偿控制器模型的预测误差。

**论文图2**：方法框图
> 基于模型的控制器运行时，将数据收集道到滑动窗口数据集中，并进行监督学习以估计残差参数a～、b～，然后它们被用来改进控制器背后的模型。


## 第四篇
**title**:[A dynamic locomotion strategy for stair walking of a quadruped robot](https://ieeexplore.ieee.org/document/9494678)

**摘要**：在非结构化环境中，盲目行走容易使机器人因与地面接触不稳定而失去平衡或倒塌。解决这个问题的一种方法时调整步态周期和步态模式。**步态周期调节步态速度，以减轻足部接触地面时的冲击量；步态模式起到稳定机器人底座平衡的作用，使其免受外界干扰或地面冲击**。这篇文章使用**具有可调步态周期和步态模式的凸模型预测为控制（MPC）的步态控制器。**


## 收集
**title**:[Efficient Multicontact Pattern Generation With Sequential Convex Approximations of the Centroidal Dynamics](https://ieeexplore.ieee.org/document/9350175)  
**title**:[Representation-Free Model Predictive Control for Dynamic Motions in Quadrupeds](https://ieeexplore.ieee.org/document/9321699)  
**title**:[Proprioceptive Sensor Fusion for Quadruped Robot State Estimation](https://ieeexplore.ieee.org/document/9341521)  
**title**:[Risk-Averse MPC via Visual-Inertial Input and Recurrent Networks for Online Collision Avoidance](https://ieeexplore.ieee.org/document/9341070)  
**title**:[Robust Autonomous Navigation of a Small-Scale Quadruped Robot in Real-World Environments](https://ieeexplore.ieee.org/document/9340701)  
**title**:[Line Walking and Balancing for Legged Robots with Point Feet](https://ieeexplore.ieee.org/document/9341743)  
## Founded in ICRA2020
**title**:[An Open Torque-Controlled Modular Robot Architecture for Legged Locomotion Research]  
**title**:[Mechanical Shock Propagation Reduction in Robot Legs]  
**title**:[Guided Constrained Policy Optimization for Dynamic Quadrupedal Robot Locomotion]  
**title**:[MPC-Based Controller with Terrain Insight for Dynamic Legged Locomotion]  
**title**:[Joint Space Position/Torque Hybrid Control of the Quadruped Robot for Locomotion and Push Reaction]  
**title**:[Vision Aided Dynamic Exploration of Unstructured Terrain with a Small-Scale Quadruped Robot]  
**title**:[Reliable Trajectories for Dynamic Quadrupeds Using Analytical Costs and Learned Initializations]  
**title**:[On the Hardware Feasibility of Nonlinear Trajectory Optimization for Legged Locomotion Based on a Simplified Dynamics]  
**title**:[Planning for the Unexpected: Explicitly Optimizing Motions for Ground Uncertainty in Running]  
**title**:[Preintegrated Velocity Bias Estimation to Overcome Contact Nonlinearities in Legged Robot Odometry]  
**title**:[Optimized Foothold Planning and Posture Searching for Energy-Efficient Quadruped Locomotion Over Challenging Terrains]  
**title**:[Precision Robotic Leaping and Landing Using Stance-Phase Balance]  
**title**:[STANCE: Locomotion Adaptation Over Soft Terrain (I)]  
**title**:[Optimal Landing Strategy for Two-Mass Hopping Leg with Natural Dynamics]  
**title**:[From Bipedal Walking to Quadrupedal Locomotion: Full-Body Dynamics Decomposition for Rapid Gait Generation]  
**title**:[DeepGait: Planning and Control of Quadrupedal Gaits Using Deep Reinforcement Learning]  
**title**:[The Soft-Landing Problem: Minimizing Energy Loss by a Legged Robot Impacting Yielding Terrain]  
**title**:[LiStereo: Generate Dense Depth Maps from LIDAR and Stereo Imagery]  

**title**:[LiStereo: Generate Dense Depth Maps from LIDAR and Stereo Imagery]  
**title**:[Automatic Snake Gait Generation Using Model Predictive Control]  
**title**:[Safe and Fast Tracking on a Robot Manipulator: Robust MPC and Neural Network Control]  
**title**:[Real-Time Nonlinear Model Predictive Control of Robots Using a Graphics Processing Unit]  
**title**:[An NMPC Approach Using Convex Inner Approximations for Online Motion Planning with Guaranteed Collision Avoidance]  
**title**:[Virtual Point Control Strategy with Power Optimization for Trajectory Planning of Autonomous Mobile Robots]  
**title**:[Bi-Convex Approximation of Non-Holonomic Trajectory Optimization]  
**title**:[Robust and Efficient Estimation of Absolute Camera Pose for Monocular Visual Odometry]  
**title**:[Collision-Free Navigation of Human-Centered Robots Via Markov Games]  
**title**:[DenseCAvoid: Real-Time Navigation in Dense Crowds Using Anticipatory Behaviors]  
**title**:[Observer-Extended Direct Method for Collision Monitoring in Robot Manipulators Using Proprioception and IMU Sensing]  
**title**:[Forward Kinematics Kernel for Improved Proxy Collision Checking]  
**title**:[Predicting Obstacle Footprints from 2D Occupancy Maps by Learning from Physical Interactions]  
**title**:[Path Planning in Dynamic Environments Using Generative RNNs and Monte Carlo Tree Search]


## founded in ICRA2019(keywords:quadrup)
**title**:[Mini Cheetah - A Platform for Pushing the Limits of Dynamic Quadruped Control]  
**title**:[Single-Shot Foothold Selection and Constraint Evaluation for Quadruped Locomotion]  
**title**:[Stanford Doggo - An Open-Source Quasi-Direct-Drive Quadruped]  
**title**:[Real-Time Model Predictive Control for Versatile Dynamic Motions in Quadrupedal Robots]  





