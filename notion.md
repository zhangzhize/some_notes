<font face="宋体">  

# 最优控制理论与系统  
## 最优控制问题的基本组成
* 系统数学模型  <center>$\dot{x}(t)=f[x(t),u(t),t],t\in[t_0,t_f]$</center>
* 边界条件与目标集  <center>$\Psi[x(t_f),t_f]=0$</center>  
* 容许控制
* 性能指标

## 最优控制问题的提法  
* 系统状态方程及其初始条件：<center>$\dot{x}(t)=f[x(t),u(t),t],x(t_0)=x_0$</center>  
* 性能指标：<center>$J=\varphi[x(t_f),t_f]+\int_{t_0}^{t_f}{L[x(t),u(t),t]}dt$</center>
* 控制不等式约束：<center>$g[x(t),u(t),t]\geqslant0$</center>
* 目标集等式约束：<center>$\Psi[x(t_f),t_f]=0$</center>  

## 性能指标类型
* 积分型:<center>$J=\int_{t_0}^{t_f}{L[x(t),u(t),t]}dt$</center>  
* 末值型:<center>$J=\varphi[x(t_f),t_f]$</center>
* 复合型:<center>$J=\varphi[x(t_f),t_f]+\int_{t_0}^{t_f}{L[x(t),u(t),t]}dt$</center>

## 线性赋范空间  
了解即可

## 泛函及其定义域
**定义2-10** 设$R^n$为$n$维线性赋范空间，$R$为实数集，若存在一一对应关系<center>$y=J(x),\forall{x}\in{R^n},y\in{R}$</center>  
则$J(x)$称为$R^n$到$R$的泛函算子。若<center>$J(x_1+x_2)=J(x_1)+J(x_2),\forall{x_1,x_2}\in{R^n}$</center>  <center>$J(ax)=aJ(x),\forall{x}\in{R^n}$</center>  
则称$J(x)$为线性泛函算子

**定义2-11** 在线性赋范空间$R^n$上，使泛函算子$J$作用有意义的元的全体，称为$J$的定义域，记作$D(J)$;$D(J)$在$J$作用下的几何，称为$J$的值域，记作:<center>$Z(J)={y|y=J(x),x\in{D(J)}}$</center>  
如果在线性赋范空间$R^n$中,当$x_n\rightarrow{x_0}时，x_n\in{R^n},x_0\in{R^n},对应有J(x_n)\rightarrow{J(x_0)}(n\rightarrow{\infty})$,则这样的泛函算子是连续的。

## 泛函的变分
**综量的变分**：$\delta{x}=x(t)-x_0(t),x(t),x_0(t)\in{R^n}$,表示$R^n$中点$x(t)与x_0(t)$之间的差
**定义2-13** 设$J(x)$是线性赋范空间$R^n$上的连续泛函，若其增量可以表示为:<center>$\delta{J(x)}=J(x+\delta{x})-J(x)=L[x,\delta{x}]+r(x,\delta{x})$</center>  
式中，$L(x,\delta{x})$是关于$\delta{x}$的线性连续泛函，$r(x,\delta{x})$是关于$\delta{x}$的高阶无穷小，则$\delta{J}=L[x,\delta{x}]$称为泛函$J$的变分

## 求泛函的变分  
**定理2-1** 设$J(x)$是线性赋范空间$R^n$上的连续泛函，若$x=x_0处J(x)是可微的，x,x_0\in{R^n}$则其变分为<center>$\delta{J(x_0,\delta{x})=}=\frac{\partial}{\partial{\varepsilon}}J(x_0,\varepsilon{\delta{x}})|_{\varepsilon=0},0\leqslant \varepsilon \leqslant 1$</center>  
**定理2-2** 泛函的二次变分<center>$\delta^2J(x_0,\delta{x})=\frac{\partial^2}{\partial{\varepsilon^2}}J(x_0,\varepsilon{\delta{x}})|_{\varepsilon=0},0\leqslant \varepsilon \leqslant 1$</center>  

## 泛函极值与变分引理
(1)泛函极值的定义  
**类似函数的极值**  
(2)泛函极值的必要条件与一次变分  
**定理2-3** 设$J(x)$是在线性赋范空间$R^n$中某个开子集D上定义的可微泛函，且在$x=x_0$处达到极值，其中$x\in{R^n},则泛函J(x)在x=x_0处必有$ <center>$\delta{J(x_0,\delta{x})}=0$</center>  
(3)泛函极小值的充要条件与二次变分:<center>$\delta{J(x,\delta{x})}=0,\delta^2{J(x_0,\delta{x})}>0$</center>  
(4)变分引理  
**定理2-5** 设$\xi(t)$是时间区间$[t_0,t_f]$上的$n$维连续向量函数，若对于n维任意的连续向量函数$\eta(t)$,其边界条件为：$\eta(t_0)=\eta(t_1)=0$均有$\int_{t_0}^{t_1}{\xi^T(t)\eta(t)}dt=0$，则 <center>$\xi(t)=0,\forall{t}\in[t_0,t_1]$</center>  

## 接下来开始是重点：欧拉方程(必要条件)和勒让德条件(充分条件)

## 无约束泛函极值的必要条件
**问题2-1** 无约束泛函极值问题为 <center>$\underset{x}{min}J(x)=\int_{t_0}^{t_f}{L(x,\dot{x},t)}dt$</center>
式中，$L[x,\dot{x},t]及x(t)在[t_0,t_f]上连续可微，t_0及t_f固定。已知x(t_0)=x_0,x(t_f)=x_f,x(t)\in{R^n},求极值轨线x^*(t)$  
**定理2-6** 对于问题2-1，使性能泛函$J(x)$取极值的**必要条件**是轨线$x(t)$满足下列欧拉方程 <center>$\frac{\partial{L}}{\partial{x}}-\frac{d}{dt}\frac{\partial{L}}{\partial{\dot{x}}}=0$</center>  
## 有等式约束的泛函极值的必要条件
**问题2-2** 有等式约束的泛函极值问题为 <center>$\underset{x}{min}J(x)=\int_{t_0}^{t_f}{g(x,\dot{x},t)}dt$</center>  <center>$s.t. f(x,\dot{x},t)=0$</center>  
式中$g(x,\dot{x},t)及x(t)在[t_0,t_f]$上连续可微，$t_0$和$t_f$固定。已知$x(t_0)=x_0,x(t_f)=x_f,x\in{R^n},f(\cdot)\in{R^n},求x^*(t)$  
**定理2-7** 对于问题2-2，在约束条件下，使泛函取极值的必要条件是$x(t)$满足下列欧拉方程 <center>$\frac{\partial{L}}{\partial{x}}-\frac{d}{dt}\frac{\partial{L}}{\partial{\dot{x}}}=0$</center>  
式中，$L(x,\dot{x},\lambda,t)=g(x,\dot{x},t)+\lambda^T(t)f(x,\dot{x},t)$,(**注意**:以上讨论两端固定的情况，横截条件自然满足)

## 泛函极小值的充分条件
(1)无约束情况  
**定理2-8** 对于问题2-1,使性能泛函成立的充分条件是，除欧拉方程成立外，下列等价勒让德条件之一成立：

1)
$$\left[ \begin{matrix}{l}
	\frac{\partial ^2L}{\partial x}&		\frac{\partial ^2L}{\partial x\partial \dot{x}}\\
	\left( \frac{\partial ^2L}{\partial x\partial \dot{x}} \right) ^T&		\frac{\partial ^2L}{\partial \dot{x}^2}\\
\end{matrix} \right] >0$$

2)
$$
\frac{\partial ^2L}{\partial x^2}-\frac{d}{dt}\frac{\partial ^2L}{\partial x\partial \dot{x}}\geqslant 0,\frac{\partial ^2L}{\partial \dot{x}^2}>0
$$

3)
$$
\frac{\partial ^2L}{\partial x^2}-\frac{d}{dt}\frac{\partial ^2L}{\partial x\partial \dot{x}}>0,\frac{\partial ^2L}{\partial \dot{x}^2}\geqslant 0
$$   

## 有约束情况
**定理2-9** 对于问题2-2,充分条件同定理2-8,只是在式中$L=L(x,\dot{x},\lambda,t),\lambda$为$n$维拉格朗日乘子向量   

## 末端时刻固定时的横截条件
两端时间固定时的横截条件的一般表达式: <center>$\left( \frac{\partial L}{\partial x} \right) ^T|_{t_f}\delta x\left( t_f \right) -\left( \frac{\partial L}{\partial \dot{x}} \right) ^T|_{t_0}\delta x\left( t_0 \right) =0$</center>  
则因为：
$$
\left\{ \begin{array}{c}
	\text{起点固定时，}x\left( t_0 \right) =x_0,\delta x\left( t_0 \right) =0\\
	\text{起点自由时，}\delta x\left( t_0 \right) \ne 0\\
	\text{终点固定时，}x\left( t_f \right) =x_f,\delta x\left( t_f \right) =0\\
	\text{终点自由时，}\delta x\left( t_f \right) \ne 0\\
\end{array} \right. 
$$
得
$$
\left\{ \begin{array}{c}
	\text{固定起点终点，}x\left( t_0 \right) =x_0,x\left( t_f \right) =x_f\\
	\text{自由起点和终点，}\frac{\partial L}{\partial \dot{x}}|_{t_0}=0,\frac{\partial L}{\partial \dot{x}}|_{t_f}=0\\
	\text{自由起点和固定终点，}\frac{\partial L}{\partial \dot{x}}|_{t_0}=0,x\left( t_f \right) =x_f\\
	\text{固定起点和自由终点，}x\left( t_0 \right) =x_0,\frac{\partial L}{\partial \dot{x}}|_{t_f}=0\\
\end{array} \right. 
$$

## 末端时刻自由时得横截条件  
(1)起点固定，末端自由  
$$
\left\{ \begin{array}{c}
	x\left( t_0 \right) =x_0,\text{故}\delta x\left( t_0 \right) =0\\
	\delta x\left( t_f \right) \text{任意}\\
\end{array} \right. 
$$
及末端自由时横截条件得一般表达式  
$$
\left( L-\dot{x}^T\left( t \right) \frac{\partial L}{\partial \dot{x}} \right) |_{t_f}\delta t_f+\left( \frac{\partial L}{\partial \dot{x}} \right) ^T|_{t_f}\delta x_f=0
$$
故横截条件  
$$
\left\{ \begin{array}{c}
	\left( L-\dot{x}^T\frac{\partial L}{\partial \dot{x}} \right) |_{t_f}=0\\
	\left( \frac{\partial L}{\partial \dot{x}} \right) |_{tf}=0\\
	x\left( t_0 \right) =x_0\\
\end{array} \right. 
$$

(2)起点固定，末端受约束  
设末端约束方程为 
$$
x(t_f)=c(t_f),则\delta{x_f}=\dot{c}(t_f)\delta{t_f}
$$
及演化得到得横截条件的一般表达式
$$
\left[ L+\left( \dot{c}-\dot{x} \right) ^T\frac{\partial L}{\partial \dot{x}} \right] |_{t_f}\delta t_f=0
$$
故横截条件为
$$
\left\{ \begin{array}{c}
	\left[ L+\left( \dot{c}-\dot{x} \right) ^T\frac{\partial L}{\partial \dot{x}} \right] |_{t_f}=0\\
	x\left( t_f \right) =c\left( t_f \right)\\
	x\left( t_0 \right) =x_0\\
\end{array} \right. 
$$  

## 用变分法求解最优控制问题  
## 可用变分法求解的最优控制问题  
$$
\dot{x}(t)=f[x(t),u(t),t],x(t_0)=x_0
$$
$$
目标集:\Psi[x(t_f),t)f]=0
$$
$$
性能泛函：J=\varphi[x(t_f),t_f]+\int_{t_0}^{t_f}{L[x,u,t]}dt
$$
其中，$u$在区区间$[t_0,t_f]$上连续且不受约束；$t_f$可固定可自由；$x(t_f)$可固定可约束可自由；$\varphi(\cdot)和L(\cdot)$在$[t_0,t_f]$上连续且二次可微；向量函数$f(\cdot)$连续可微

## 末端时刻固定时的最优解的必要条件
### (1)末端受约束情况
**问题**
$$
\underset{u\left( t \right)}{\min}J=\varphi \left[ x\left( t_f \right) \right] +\int_{t_0}^{t_f}{L\left[ x,u,t \right]}dt,t_f\text{固定}
\\
s.t. \dot{x}\left( t \right) =f\left( x,u,t \right) ,x\left( t_0 \right) =x_0
\\
\Psi \left[ x\left( t_f \right) \right] =0
$$
**必要条件**  
**$x(t)和\lambda(t)$满足下列方程**
$$
\dot{x}(t)=\frac{\partial{H}}{\partial{\lambda}}
\\
\dot{\lambda}(t)=-\frac{H}{\partial{x}}
\\
式中H(x,u,\lambda,t)=L(x,u,t)+\lambda^T(t)f(x,u,t)
$$  
**边界条件**
$$
x(t_0)=x_0
\\
\lambda(t_f)=\frac{\partial{\varphi}}{\partial{x}(t_f)}+\frac{\Psi^T}{\partial{x}(t_f)}\gamma(t_f)
\\
\Psi[x(t_f)]=0
$$  
**极值条件**
$$
\frac{H}{\partial{u}}=0
$$

### (2)末端自由情况  
**问题**
$$
\underset{u(t)}{min}J=\varphi[x(t_f)]+\int_{t_0}^{t_f}{L[x,u,t]}dt,t_f固定
\\
s.t. \dot{x}(t)=f(x,u,t),x(t_0)=x_0
$$  
**必要条件**  
**$x(t)和\lambda(t)$满足下列正则方程**
$$
\dot{x}(t)=\frac{\partial{H}}{\partial{\lambda}}
\\
\dot{\lambda}(t)=-\frac{\partial{H}}{\partial{x}}
\\
式中H(x,u,\lambda,t)=L(x,u,t)+\lambda^T(t)f(x,u,t)
$$  
**边界条件**  
$$
x(t_0)=x_0
\\
\lambda(t_f)=\frac{\partial{\varphi}}{\partial{x}(t_f)}
$$  
**极值条件**
$$
\frac{\partial{H}}{\partial{u}}=0
$$  
### (3)末端固定情况  
**问题**
$$
\underset{u(t)}{min}J=\varphi[x(t_f)]+\int_{t_0}^{t_f}{L[x,u,t]}dt,t_f固定
\\
s.t. \dot{x}(t)=f(x,u,t),x(t_0)=x_0,x(t_f)=x_f
$$  
**必要条件**  
**$x(t)和\lambda(t)$满足下列正则方程**
$$
\dot{x}(t)=\frac{\partial{H}}{\partial{\lambda}}
\\
\dot{\lambda}(t)=-\frac{\partial{H}}{\partial{x}}
\\
式中H(x,u,\lambda,t)=L(x,u,t)+\lambda^T(t)f(x,u,t)
$$  
**边界条件**  
$$
x(t_0)=x_0
\\
x(t_f)=x_f
$$  
**极值条件**
$$
\frac{\partial{H}}{\partial{u}}=0
$$  
## 末端时刻固定时最优解的充分条件  
**定理2-13** 对于如下最优控制问题  
$$
\underset{u(t)}{min}J=\varphi[x(t_f)]+\int_{t_0}^{t_f}{L(x,u,t)}dt
\\
s.t. \dot{x}(t)=f(x,u,t),x(t_0)=x_0,\Psi[x(t_f)]=0
$$  
使性能泛函$J$取极小值的最优解的充分条件是下列勒让德条件之一成立  
$$
\left[ \begin{matrix}{l}
	\frac{\partial ^2H}{\partial x^2}&		\frac{\partial ^2H}{\partial u\partial x}\\
	\left( \frac{\partial ^2H}{\partial u\partial x} \right) ^T&		\frac{\partial ^2H}{\partial u^2}\\
\end{matrix} \right] >0,\frac{\partial \varTheta \left[ x\left( t_f \right) ,\gamma \right]}{\partial x^2\left( t_f \right)}\geqslant 0
$$ 
$$
\left[ \begin{matrix}{l}
	\frac{\partial ^2H}{\partial x^2}&		\frac{\partial ^2H}{\partial u\partial x}\\
	\left( \frac{\partial ^2H}{\partial u\partial x} \right) ^T&		\frac{\partial ^2H}{\partial u^2}\\
\end{matrix} \right] \geqslant0,\frac{\partial \varTheta \left[ x\left( t_f \right) ,\gamma \right]}{\partial x^2\left( t_f \right)}> 0
$$

## 末端时刻自由时的最优解  
### (1)末端受约束时最优解的必要条件
**问题**  
$$
\underset{u(t)}{min}J=\varphi[x(t_f),t_f]+\int_{t_0}^{t_f}{L(x,u,t)}dt
\\
s.t. \dot{x}(t)=f(x,u,t),x(t_0)=x_0,\Psi[x(t_f),t_f]=0
$$  
**必要条件**  
**$x(t)和\lambda(t)$满足下列正则方程**  
$$
\dot{x}(t)=\frac{\partial{H}}{\partial{\lambda}}
\\
\dot{\lambda}(t)=-\frac{\partial{H}}{\partial{x}}
$$  

**边界条件**  
$$
x(t_0)=x_0
\\
\lambda(t_f)=\frac{\partial{\varphi}}{\partial{x}(t_f)}+\frac{\partial{\Psi^T}}{\partial{x}(t_f)}\gamma(t_f)
$$  
**极值条件**
$$
\frac{\partial{H}}{\partial{u}}=0
$$  
**哈密顿函数在最优轨线末端满足**
$$
H(t_f)=-\frac{\partial{\varphi}}{\partial(t_f)}-\gamma^T(t_f)\frac{\partial{\varphi}}{\partial{t_f}}
$$  
### (2)末端自由时最优解的必要条件  
**同末端受约束时最优解的必要条件，只不过没有$\Psi$**  
### (3)末端固定时最优解的必要条件
**同末端受约束时最优解的必要条件,只有如下不同**
**边界条件**
$$
x(t_0)=x_0
\\
x(t_f)=x_f
$$
**极值调条件**
$$
H(t_f)=-\frac{\partial{\varphi}}{\partial{t_f}}
$$