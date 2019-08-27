@[toc]
## 第3章 常用概率分布
当拟合数据的概率模型时，需要知道拟合的不确定性。该不确定性用拟合模型参数的概率分布来表示。因此对用于建模的每种分布，另有一个与参数联系的概率分布，后者用来建模前者分布的参数，后者的参数为**超参数**。

超参数决定原分布的参数的概率分布的形状。
### 3.1 伯努利分布
伯努利分布有一个单参数 $\lambda \in[0,1]$，它定义成功一次（$x=1$）的概率。
可以表示为：
$$
\begin{aligned}
Pr(x=0) & =1-\lambda \\
Pr(x=1) & =\lambda
\end{aligned}
$$
或者表示为：
$$Pr(x)=\lambda^x(1-\lambda)^{1-x}$$
或者等价的表示方法：
$$Pr(x)=Bern_x[\lambda]$$

### 3.2 贝塔分布
贝塔分布是由单变量 $\lambda$ 定义的连续分布，这里 $\lambda=[0,1]$。因此，它适合表示伯努利分布中参数 $\lambda$ 的不确定性。
贝塔分布有两个参数（即上文所说的超参数）$(\alpha,\beta)\in[0,\infty]$，两个参数均取正值并且都影响曲线的形状。
参数决定预期值，如下：
$$E[\lambda]=\frac{\alpha}{\alpha+\beta}$$

### 3.3 分类分布
分类分布是离散分布，观察 $k$ 个可能结果的概率。当仅有两种结果时，伯努利分布是一种特殊的分类分布。
观察 $K$ 种可能结果的概率存储在 $K*1$ 的参数向量 $\bm\lambda=[\lambda_1,\lambda_2,\cdots,\lambda_k]$，其中 $\lambda_k\in[0,1]$，$\sum_{k=1}^K=1$。
分类分布可写成如下形式：
$$Pr(x=k)=\lambda_k$$
记号法为：
$$Pr(x)=Cat_x[\bm\lambda]$$

### 3.4 狄利克雷分布
狄利克雷分布定义在 $K$ 个连续值 $\lambda_1,\cdots,\lambda_k$ 上，其中    $\lambda_k\in[0,1]$，$\sum_{k=1}^K=1$。因此狄利克雷分布用来定义分类分布中参数的分布。
在 $K$ 维空间中，狄利克雷分布有 $K$ 个参数 $\alpha_1,\cdots,\alpha_K$，每个参数都取正值。可以写成：
$$Pr(\lambda_{1\cdots K})=Dir_{\lambda_1\cdots K}[\alpha_{1\cdots K}]$$
贝塔分布是一个二维的特殊狄利克雷分布。

### 3.5 一元正态分布
一元正态分布（高斯分布）由一个连续值 $x\in[-\infty,\infty]$ 定义。
一元正态分布有两个参数，均值 $\mu$ 和方差 $\sigma^2$。$\mu$ 可以取任意实数，它决定峰值的位置。$\sigma^2$ 大于零，它决定分布的宽度。正态分布定义为：
$$Pr(x)=\frac{1}{\sqrt{2\pi\sigma^2}}\text{exp}\left[-0.5\frac{(x-\mu)^2}{\sigma^2}\right]$$
将其简写为
$$Pr(x)=Norm_x[\mu,\sigma^2]$$

### 3.6 正态逆伽马分布
正态逆伽马分布由 $\mu$ 和 $\sigma^2$ 两个参数定义，其中，前者可取任意值，后者仅取大于零的值。因此该分布可以用来定义正态分布中参数方差和均值的分布。
正态逆伽马分布有4个参数 $\alpha,\beta,\gamma,\delta$，其中，前三个参数为正实数，最后一个参数可取任意值，可以简写为：
$$Pr(\mu,\sigma^2)=NormInvGam_{\mu,\sigma^2}[\alpha,\beta,\gamma,\delta]$$

### 3.7 多元正态分布
多元正态分布（多元高斯分布）是一个由 $D$ 维变量 $\bm x$ 的每个元素 $x_1,\cdots,x_D$ 都是连续的且为任意实数。
多元正态分布有两个参数，均值 $\bm\mu$，协方差 $\bm\Sigma$。$\bm\mu$ 是 $D\times1$ 维向量，它描述分布的均值。协方差 $\bm\Sigma$ 是对称的 $D\times D$ 维正定矩阵，这样使任意的实向量 $\bm z$ 满足 $\bm z^T\bm{\Sigma z}$ 恒为正。可以简写为：
$$Pr(\bm x)=Norm_{\bm x}[\bm\mu,\bm\Sigma]$$

### 3.8 正态逆维希特分布
正态逆维希特分布由一个 $D\times 1$ 维向量 $\bm\mu$ 和 $D\times D$ 维正定矩阵  $\bm\Sigma$ 定义。它用来描述多元正态分布中参数的概率分布。
正态逆维希特分布有四个参数 $\alpha,\bm\Psi,\gamma,\bm\delta$，可以简写为：
$$Pr(\bm\mu,\bm\Sigma)=NorIWis_{\bm{\mu,\Sigma}}[\alpha,\bm\Psi,\gamma,\bm\delta]$$

### 3.9 共轭性
贝塔分布可以表征伯努利分布中参数的概率，其他类似。
前一个分布是后一个的共轭：贝塔分布与伯努利分布共轭。当把一个分布与其共轭分布相乘时，结果正比于一个新的分布，它与共轭形式相同，例如：
$$Bern_x[\lambda]\cdot Beta_\lambda[\alpha,\beta]=k(x,\alpha,\beta)\cdot Beta_\lambda[\widetilde{\alpha},\widetilde{\beta}]$$

### 总结
使用概率分布可以描述全局状态和图像数据。为此已经给出了四个分布（伯努利分布、分类分布、一元正态分布、多元正态分布）。还给出了四个分布（贝塔分布、狄利克雷分布、正态逆伽马分布、正态逆维希特分布），可以用来描述上一组分布的参数的概率的分布，因此它们可以描述拟合模型的不确定性。第二组的每个分布是对应第一组的共轭。

### 备注
- Bishops（2006）第2章
- Gelman（2004）