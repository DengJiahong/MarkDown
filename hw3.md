<style>
.title-box {
    border-style: solid;
    border-width: 1px;
    padding: 16px;
    padding-bottom: 32px;
}
</style>

<div class="title-box">
    <div>
        <b style="float: left;">Optimization Methods</b>
        <b style="float: right;">Fall 2021</b>
    </div>
    <h1 style="text-align: center;">Homework 3</h1>
    <div>
        <span style="float: left;"><i>Instructor:</i> Lijun Zhang</span>
        <span style="float: right;"><i>Name:</i> 张朝植, <i>StudentId:</i> 201300067</span>
    </div>
</div>

## Problem 1: One inequality constraint

$$
\begin{aligned}
g(\lambda) &= \displaystyle \inf_{\boldsymbol{x}} L(\boldsymbol{x}, \lambda) 
\\&= \inf_{\boldsymbol{x}} \{\boldsymbol{c}^\top \boldsymbol{x} + \lambda f(\boldsymbol{x})\} 
\end{aligned}
$$

如果 $\lambda > 0$，则

$$
\begin{aligned}
g(\lambda) &= -\lambda \sup_{\boldsymbol{x}} \{-(\frac{\boldsymbol{c}}{\lambda})^\top \boldsymbol{x} - f(\boldsymbol{x})\}
\\&= -\lambda f^*(-\frac{\boldsymbol{c}}{\lambda})
\end{aligned}
$$

如果 $\lambda = 0$，则 $g(\lambda) = \displaystyle \inf_{\boldsymbol{x}} \boldsymbol{c}^\top \boldsymbol{x}$，由 $\boldsymbol{c}^\top \boldsymbol{x}$ 是线性函数而 $\boldsymbol{c} \neq \boldsymbol{0}$，因此 $\boldsymbol{c}^\top \boldsymbol{x}$ 无下界，$g(\lambda) = -\infty$。

因此对偶问题为

$$
\begin{aligned}
&\text{maximize} &&-\lambda f^*(-\frac{\boldsymbol{c}}{\lambda})
\\&\text{s.t.} &&\lambda > 0
\end{aligned}
$$

## Problem 2: KKT Conditions

### (1)

标准形式的优化问题是

$$
\begin{aligned}
&\min_{\boldsymbol{x}\in \mathbb{R}^2} && f_0(\boldsymbol{x})
\\&\text{s.t.} && f_i(\boldsymbol{x})\leqslant 0, &i = 1, 2
\end{aligned}
$$

其中 $f_0(\boldsymbol{x}) = x_1^2 + x_2^2,\ f_1(\boldsymbol{x}) = (x_1 - 1)^2 + (x_2 - 1)^2 - 2,\ f_2(\boldsymbol{x}) = (x_1 - 1)^2 + (x_2 + 1)^2 - 2$。

因此

$$
\begin{aligned}
L(\boldsymbol{x}, \boldsymbol{\lambda}) &= x_1^2 + x_2^2 + \boldsymbol{\lambda}^\top f(x)
\end{aligned}
$$

其中 $\boldsymbol{\lambda} = \begin{bmatrix}\lambda_1 & \lambda_2\end{bmatrix}^\top, f(\boldsymbol{x}) = \begin{bmatrix}f_1(\boldsymbol{x}) & f_2(\boldsymbol{x})\end{bmatrix}^\top$

### (2)

强对偶性成立。

取 $\boldsymbol{x} = \begin{bmatrix}
    1\\
    0
\end{bmatrix}\in \mathbf{relint}\ \mathbb{R}^2
$

可以使得 $f_i(\boldsymbol{x}) = -1 < 0$，$(i = 1, 2)$

此处 $f_0, f_1, f_2$ 均为凸函数，且 $\textbf{dom}\ f_0 = \mathbb{R}^2$，因此原问题是一个凸问题。根据 `Slater` 约束准则，强对偶性成立。 

### (3)

该问题的 `KKT` 约束条件是

$$
\begin{aligned}
f_i(\boldsymbol{x}^*) \leqslant 0, &&i = 1, 2
\\\lambda_i^* \geqslant 0, &&i = 1,2
\\\lambda_i^*f_i(\boldsymbol{x}^*) = 0, &&i = 1, 2
\\\nabla f_0(\boldsymbol{x}^*) + \boldsymbol{\lambda}^\top \nabla f(\boldsymbol{x}^*) = \boldsymbol{0}
\end{aligned}
$$

代入得

$$
\begin{aligned}
(x_1^* - 1)^2 + (x_2^* - 1)^2 - 2 \leqslant 0
\\(x_1^* - 1)^2 + (x_2^* + 1)^2 - 2 \leqslant 0
\\\lambda_i^* \geqslant 0, &&i = 1, 2
\\\lambda_1^* [(x_1^* - 1)^2 + (x_2^* - 1)^2 - 2] = 0
\\\lambda_2^* [(x_1^* - 1)^2 + (x_2^* + 1)^2 - 2] = 0
\\ 2x_1^* + 2\lambda_1(x_1^* - 1) + 2\lambda_2 (x_1^* - 1) = 0
\\ 2x_2^* + 2\lambda_1(x_2^* - 1) + 2\lambda_2 (x_2^* + 1) = 0
\end{aligned}
$$

## Problem 3: Equality Constrained Least-squares

### (1)

$$
\begin{aligned}
L(\boldsymbol{x}, \boldsymbol{v}) &= \frac{1}{2}\|A\boldsymbol{x} - \boldsymbol{b}\|_2^2 + \boldsymbol{v}^\top (Gx - h)
\\&= \frac{1}{2} \boldsymbol{x}^\top A^\top A\boldsymbol{x} + (\boldsymbol{v}^T G- \boldsymbol{b}^\top A)\boldsymbol{x} + \frac{1}{2} \boldsymbol{b}^\top \boldsymbol{b} - \boldsymbol{v}^\top h
\end{aligned}
$$

对 $\boldsymbol{x}$ 求偏导有 $\nabla_{\boldsymbol{x}} L(\boldsymbol{x}, \lambda) = A^\top A\boldsymbol{x} + (G^\top \boldsymbol{v}- A^\top \boldsymbol{b}) $

由 ${\bf rank}\ A = n$，则 ${\bf rank}\ A^\top A = n$，因此 $\displaystyle \nabla_{\boldsymbol{x}} L(\boldsymbol{x}, \lambda) = 0$ 有唯一解 $\boldsymbol{x} = (A^\top A)^{-1} (A^\top \boldsymbol{b} - G^\top \boldsymbol{v})$。

$$
\begin{aligned}
g(\boldsymbol{v}) &= \inf_x L(\boldsymbol{x}, \boldsymbol{v})
\\&= L((A^\top A)^{-1} (A^\top \boldsymbol{b} - G^\top \boldsymbol{v}), \boldsymbol{v})
\\&= -\frac{1}{2} (A^\top \boldsymbol{b} - G^\top \boldsymbol{v})^\top (A^\top A)^{-1} (A^\top \boldsymbol{b} - G^\top \boldsymbol{v}) + \frac{1}{2} \boldsymbol{b}^\top \boldsymbol{b} - \boldsymbol{v}^\top h
\end{aligned}
$$

则 `Lagrange` 对偶问题为无约束的优化问题

$$
\begin{aligned}
\text{maximize} &&g(\boldsymbol{v})
\end{aligned}
$$

### (2)

由 (1)，`KKT` 条件有：

$$
\boldsymbol{x}^* = (A^\top A)^{-1} (A^\top \boldsymbol{b} - G^\top \boldsymbol{v}^*)
$$

根据约束条件有：

$$
G\boldsymbol{x}^*=\boldsymbol{h}
$$

消去 $\boldsymbol{x}^*$ 有 $G(A^\top A)^{-1} (A^\top \boldsymbol{b} - G^\top \boldsymbol{v}^*) = \boldsymbol{h}$

$G(A^\top A)^{-1} G^\top \boldsymbol{v}^* = G(A^\top A)^{-1}A^\top \boldsymbol{b} - \boldsymbol{h}$

根据 $\textbf{rank}\ G = p, \textbf{rank}\ A^\top A = n$ 得 $\textbf{rank}\ G(A^\top A)^{-1}G^{\top} = p$ 则 $\boldsymbol{v}^*$ 由唯一解

$$
\boldsymbol{v}^* = (G(A^\top A)^{-1} G^\top)^{-1}[G(A^\top A)^{-1}A^\top \boldsymbol{b} - \boldsymbol{h}]
$$

将该 $\boldsymbol{v}^*$ 代回 $\boldsymbol{x}^*$ 可以求出

$$
\begin{aligned}
\boldsymbol{x}^* &= (A^\top A)^{-1} (A^\top \boldsymbol{b} - G^\top (G(A^\top A)^{-1} G^\top)^{-1}(G(A^\top A)^{-1}A^\top \boldsymbol{b} - \boldsymbol{h}))
\end{aligned}
$$

## Problem 4: Negative-entropy Regularization

当 $c > 0$ 时：

先求

$$
\begin{aligned}
&\text{minimize} && \boldsymbol{b}^\top \boldsymbol{x} + c\sum_{i=1}^{n} x_i \ln x_i
\\&\text{s.t.} &&\displaystyle \sum_{i=1}^{n} x_i - 1 = 0
\end{aligned}
$$

其中定义域 $\Delta'= \mathbb{R}_{++}^n$。由于没有不等式约束，且极小化的函数以及等式约束都是凸函数，根据 `slater` 约束性准则，强对偶性成立。

由 $L(\boldsymbol{x}, \nu) = \boldsymbol{b}^\top \boldsymbol{x} + c\displaystyle \sum_{i=1}^{n} x_i \ln x_i + \nu (\sum_{i=1}^{n} x_i - 1)$

有

$$
\begin{aligned}
 \frac{\partial L(\boldsymbol{x}, \nu)}{\partial x_i} =b_i + c(\ln x_i + 1) + \nu
\end{aligned}
$$

$L(\boldsymbol{x}, \nu)$ 是对 $\boldsymbol{x}$ 是凸函数，则取 $\nabla_x L(\boldsymbol{x}, \nu) = 0$ 得 $x_i = \displaystyle \operatorname{exp}({-\frac{b_i + \nu}{c} -1})$

$$
\begin{aligned}
g(\nu) &= \inf_{\boldsymbol{x}\in \Delta'} L(\boldsymbol{x}, \nu)
\\&= \displaystyle \sum_{i=1}^{n} (b_i + \nu)\operatorname{exp}(-\frac{b_i + \nu}{c} - 1) + c\displaystyle \sum_{i=1}^{n} ({-\frac{b_i + \nu}{c} -1})\operatorname{exp}({-\frac{b_i + \nu}{c} -1}) - \nu
\\&= -c \displaystyle \sum_{i=1}^{n} \operatorname{exp}({-\frac{b_i + \nu}{c} -1}) - \nu
\end{aligned}
$$

求解对偶问题

$$
\begin{aligned}
&\text{maximize}&& g(\nu)
\end{aligned}
$$

仿射函数和凸函数的复合 $\displaystyle \operatorname{exp}({-\frac{b_i + \nu}{c} -1})$ 仍是凸函数，因此 $\displaystyle \sum_{i=1}^{n} \operatorname{exp}({-\frac{b_i + \nu}{c} -1})$ 也是凸函数，$-c \displaystyle \sum_{i=1}^{n} \operatorname{exp}({-\frac{b_i + \nu}{c} -1}) - \nu$ 是凹函数。

要极大化 $g(\nu)$ 只需 $g'(v) = \displaystyle \sum_{i=1}^{n} \operatorname{exp}({-\frac{b_i + \nu}{c} -1}) - 1 = 0$

即 $\nu^* = \displaystyle c \ln (\displaystyle \sum_{i=1}^{n} \operatorname{exp}(-\frac{b_i}{c})) - c$

根据 `KKT` 条件有：$b_i + c(\ln x_i^* + 1) + \nu^* = 0,\quad i = 1, ..., n$

则

$$
x_i^* = \frac{\displaystyle \operatorname{exp}(-\frac{b_i}{c})}{\displaystyle \displaystyle \sum_{i=1}^{n} \operatorname{exp}(-\frac{b_i}{c})}
$$

因此对原问题

$$
\begin{aligned}
&\argmin_{\boldsymbol{x}\in \Delta^n} && \boldsymbol{b}^\top \boldsymbol{x} + c\sum_{i=1}^{n} x_i \ln x_i
\end{aligned}
$$

其最优解即对应 $\boldsymbol{x}^* = \begin{bmatrix}x_1^* & ... & x_n^*\end{bmatrix}^\top$。

当 $c = 0$ 时：

先求

$$
\begin{aligned}
&\text{minimize} && \boldsymbol{b}^\top \boldsymbol{x}
\\&\text{s.t.} &&-\boldsymbol{x}\preccurlyeq 0
\\&&&\displaystyle \sum_{i=1}^{n} x_i - 1 = 0
\end{aligned}
\qquad\qquad(^*)
$$


显然 $f_0$ 以及约束条件都是凸函数，并且可以取 $x_i = \displaystyle \frac{1}{n}$，使得 $\boldsymbol{x} \prec 0, \displaystyle \sum_{i=1}^{n} x_i  - 1 = 0$，因此根据 `Slater` 约束准则，原问题满足强对偶性。

而

$$
\begin{aligned}
g(\lambda, \nu) &= \inf_{\boldsymbol{x}} L(\boldsymbol{x}, \lambda, \nu)
\\&= \inf_{\boldsymbol{x}} \{\boldsymbol{b}^\top \boldsymbol{x} - \lambda^\top \boldsymbol{x} + \nu \displaystyle \sum_{i=1}^{n} x_i - \nu\}
\\&=\begin{cases}
-\nu, &b_i - \lambda_i + \nu = 0,
\\-\infty, & \text{otherwise}
\end{cases}
\end{aligned}
$$

对偶问题为

$$
\begin{aligned}
&\text{maximize}&& -\nu
\\&\text{s.t.}&& \lambda \succcurlyeq 0
\\&&&b_i - \lambda_i + \nu = 0
\end{aligned}
$$

根据对偶问题的约束条件可以得到 $\lambda_i = b_i + \nu \geqslant 0,\quad i = 1, ... , n$

即有 $-\nu \leqslant b_i,\quad i = 1, ... , n$

因此对偶最优解

$$
\nu^* = - \min_{i} b_i
\\\lambda^* = b_i - \min_{i} b_i
$$

根据互补松弛性有

$$
\begin{aligned}
\lambda_i^* = b_i - \min_{i} b_i > 0 \implies x_i^* = 0
\end{aligned}
$$

因此原约束条件再加上该条件规定了原问题的最优解集。

当 $c < 0$ 时，

先考虑问题 (*)：

记 $\alpha = \displaystyle \argmin b_i$，观察到满足 $\tilde{x_i} = \begin{cases}1, &i = \alpha\\0, &\text{otherwise}\end{cases}$ 的解 $\tilde{\boldsymbol{x}}$ 能满足上述约束条件，因此 $\tilde{\boldsymbol{x}}$ 在问题 (*) 的最优解集中。

<!-- $$
\begin{aligned}
&\argmin_{\boldsymbol{x}\in \Delta^n}&& \boldsymbol{b}^\top \boldsymbol{x} + c\sum_{i=1}^{n} x_i \ln x_i
\end{aligned}
$$ -->

而对问题

$$
\begin{aligned}
&\text{minimize}&& c\sum_{i=1}^{n} x_i \ln x_i
% \\&\text{s.t.} &&\displaystyle \sum_{i=1}^{n} x_i - 1 = 0
\end{aligned}
$$

对定义域 $\boldsymbol{x}\in \Delta^n$，由 $\boldsymbol{x}\succcurlyeq 0$ 且 $\boldsymbol{1}^\top \boldsymbol{x} = 1$ 可知 $0\leqslant x_i \leqslant 1$，对 $i= 1, 2, ..., n$，则在约束条件下 $\displaystyle c\sum_{i=1}^{n} x_i \ln x_i \geqslant 0$，而代入 $\tilde{\boldsymbol{x}}$ 时恰能取到 $0$，因此 $\tilde{\boldsymbol{x}}$ 也是该问题的最优解。

根据上述分析，$\tilde{\boldsymbol{x}}$ 也是原问题的最优解。

## Problem 5: Support Vector Machines

### (1)

使用变量 $u_i = y_i(\boldsymbol{w}^\top \boldsymbol{x}_i + \boldsymbol{b}),\quad i = 1, ..., d$，得到等价的

$$
\begin{aligned}
&\text{minimize}&&\displaystyle \sum_{i=1}^{n} \max \{0, 1 - u_i\} + \frac{\lambda}{2} \|\boldsymbol{w}\|_2^2
\\&\text{s.t.}&&y_i(\boldsymbol{w}^\top \boldsymbol{x}_i + \boldsymbol{b}) - u_i = 0, &i = 1, ... , n
\end{aligned}
$$

### (2)

$$
\begin{aligned}
L(\boldsymbol{w}, \boldsymbol{b}, u, \nu) &= \sum_{i=1}^{n} \max \{0, 1 - u_i\} + \frac{\lambda}{2} \|\boldsymbol{w}\|_2^2 + \displaystyle \sum_{i=1}^{n} \nu_i(y_i(\boldsymbol{w}^\top \boldsymbol{x}_i + \boldsymbol{b}) - u_i)
\\&= \displaystyle \sum_{i=1}^{n} [l(u_i) - \nu_i u_i] + \displaystyle \sum_{i=1}^{n} \nu_i y_i \boldsymbol{b} + \sum_{i=1}^{n}\nu_i y_i \boldsymbol{w}^\top \boldsymbol{x}_i + \frac{\lambda}{2} \|\boldsymbol{w}\|_2^2
\end{aligned}
$$

$$
\begin{aligned}
g(\nu) &= \inf_{(\boldsymbol{w}, \boldsymbol{b}, u)} \{\sum_{i=1}^{n} [l(u_i) - \nu_i u_i] + \displaystyle \sum_{i=1}^{n} \nu_i y_i \boldsymbol{b} + \sum_{i=1}^{n}\nu_i y_i \boldsymbol{w}^\top \boldsymbol{x}_i + \frac{\lambda}{2} \|\boldsymbol{w}\|_2^2\}
\\&= \inf_{u} \{\sum_{i=1}^{n} [l(u_i) - \nu_i u_i]\} + \inf_{\boldsymbol{b}}\{\sum_{i=1}^{n} \nu_i y_i \boldsymbol{b}\}  + \inf_{\boldsymbol{w}} \{\sum_{i=1}^{n}\nu_i y_i \boldsymbol{w}^\top \boldsymbol{x}_i + \frac{\lambda}{2} \|\boldsymbol{w}\|_2^2\}\}
\\&= -\sup_{u} \{\sum_{i=1}^{n} [\nu_i u_i - l(u_i)]\} + \inf_{\boldsymbol{b}}\{\sum_{i=1}^{n} \nu_i y_i \boldsymbol{b}\}  + \inf_{\boldsymbol{w}} \{\sum_{i=1}^{n}\nu_i y_i \boldsymbol{w}^\top \boldsymbol{x}_i + \frac{\lambda}{2} \|\boldsymbol{w}\|_2^2\}\}
\\&= - \sum_{i=1}^{n}\sup_{u} \{\nu_i u_i - l(u_i)\} + \inf_{\boldsymbol{b}}\{\sum_{i=1}^{n} \nu_i y_i \boldsymbol{b}\}  + \inf_{\boldsymbol{w}} \{\sum_{i=1}^{n}\nu_i y_i \boldsymbol{w}^\top \boldsymbol{x}_i + \frac{\lambda}{2} \|\boldsymbol{w}\|_2^2\}\}
\\&=\begin{cases}
-\displaystyle \sum_{i=1}^{n} \nu_i - \frac{1}{2\lambda} \|\displaystyle \sum_{i = 1}^{n} \nu_i y_i \boldsymbol{x}_i\|_2^2, & -1 \leqslant y\leqslant 0,\ \displaystyle \sum_{i=1}^{n} \nu_iy_i = 0\\
-\infty, &\text{otherwise}
\end{cases}
\end{aligned}
$$

因此上述等价问题的 `Lagrange` 对偶问题为

$$
\begin{aligned}
&\text{maximize}&& \displaystyle \sum_{i=1}^{n} \nu_i - \frac{1}{2\lambda} \|\displaystyle \sum_{i = 1}^{n} \nu_i y_i \boldsymbol{x}_i\|_2^2\\
&\text{s.t.}&&-1 \leqslant y\leqslant 0,\\
&&&\lambda\geqslant 0\\
&&&\displaystyle \sum_{i=1}^{n} \nu_iy_i = 0
\end{aligned}
$$

### (3)

由 $\displaystyle \sum_{i=1}^{n} [l(u_i) - \nu_i u_i] + \displaystyle \sum_{i=1}^{n} \nu_i y_i \boldsymbol{b} + \sum_{i=1}^{n}\nu_i y_i \boldsymbol{w}^\top \boldsymbol{x}_i + \frac{\lambda}{2} \|\boldsymbol{w}\|_2^2$

由

$$
\begin{aligned}
\nabla_{\boldsymbol{w}} L(\boldsymbol{w}, \boldsymbol{b}, u, \nu) &= \frac{\lambda}{2} \boldsymbol{w} + \displaystyle \sum_{i=1}^{n} \nu_i y_i \boldsymbol{x}_i\\
\nabla_{\boldsymbol{b}} L(\boldsymbol{w}, \boldsymbol{b}, u, \nu) &= \sum_{i=1}^{n} \nu_i y_i
\end{aligned}
$$

注意 $L(\boldsymbol{w}, \boldsymbol{b}, u, \nu)$ 关于 $u$ 在定义域上存在不可微的点。

`KKT` 条件为

$$
\begin{aligned}
y_i(\boldsymbol{w}^\top \boldsymbol{x}_i + \boldsymbol{b}) - u_i = 0, && i = 1, ... , n\\
\frac{\lambda}{2} \boldsymbol{w} + \displaystyle \sum_{i=1}^{n} \nu_i y_i \boldsymbol{x}_i = 0\\
\sum_{i=1}^{n} \nu_i y_i = 0
\end{aligned}
$$


