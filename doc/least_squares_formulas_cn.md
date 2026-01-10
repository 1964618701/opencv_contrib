## 最小二乘法核心公式详解

最小二乘法的核心目标是寻找参数向量 \(x\)，使得模型预测 \(Ax\) 与观测值 \(b\) 的平方误差最小：
\[
\min_x \; \|Ax-b\|_2^2.
\]
这里 \(A\) 为观测矩阵（或雅可比矩阵），\(b\) 为观测向量。

### 1. 线性最小二乘（无权）

目标函数的梯度设为零得到一阶最优条件（正规方程）：
\[
A^\top A\,x = A^\top b.
\]
当 \(A\) 满列秩时，闭式解为
\[
x^\* = (A^\top A)^{-1}A^\top b = A^{+} b,
\]
其中 \(A^{+}\) 是 Moore–Penrose 伪逆。如果 \(A\) 秩亏，可通过 SVD \(A = U\Sigma V^\top\) 得到 \(A^{+} = V\Sigma^{+}U^\top\)。

### 2. 加权最小二乘

当观测具有不同置信度（权重矩阵 \(W\succ 0\)）时：
\[
\min_x (Ax-b)^\top W (Ax-b).
\]
对应的正规方程为
\[
(A^\top W A)\,x = A^\top W b,\quad
x^\* = (A^\top W A)^{-1}A^\top W b.
\]

### 3. 正则化 / 岭回归 / Tikhonov

为抑制病态或过拟合，常加入正则项（最常见是 \(L=I\)）：
\[
\min_x \|Ax-b\|_2^2 + \lambda \|Lx\|_2^2.
\]
解满足
\[
(A^\top A + \lambda L^\top L)\,x = A^\top b,\quad
x^\* = (A^\top A + \lambda L^\top L)^{-1}A^\top b.
\]
当 \(L=I\) 时即岭回归公式 \((A^\top A + \lambda I)^{-1}A^\top b\)。

### 4. 非线性最小二乘（高斯–牛顿、LM）

对于残差 \(r_i(\theta)\) 的非线性问题
\[
\min_\theta \sum_i r_i(\theta)^2,
\]
在当前估计 \(\theta_k\) 处线性化得到雅可比 \(J\) 与残差向量 \(r\)，增量 \(\Delta\theta\) 由
\[
J^\top J\,\Delta\theta = -J^\top r
\]
（高斯–牛顿）求得。Levenberg–Marquardt 则加入阻尼
\[
(J^\top J + \lambda I)\,\Delta\theta = -J^\top r,
\]
权重可同理并入 \(J^\top W J\)。

### 5. 残差与协方差

拟合后残差 \(e = Ax^\* - b\)，其均方误差 \(\sigma^2 \approx \|e\|_2^2/(m-n)\)。若噪声独立同分布，参数协方差可近似为
\[
\mathrm{Cov}(x^\*) \approx \sigma^2 (A^\top A)^{-1}
\]
（或加权、正则化情形的对应矩阵逆）。

以上公式覆盖了最常见的最小二乘场景：无权、加权、正则化、非线性迭代与不确定性估计。
