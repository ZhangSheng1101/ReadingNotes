@[toc]
## 习题解答
$\color{red}{答案仅供参考}$
#### 2.1 
$统计一周的下雨量，x\ 的值为周一到周日，y\ 的值为降雨量$
#### 2.2
$仅考虑变量\ w\ 和\ y$
$$
\begin{aligned}
Pr(v,w,x,y,z)
& =Pr(v,x,z,w|y)Pr(y) \\
& = Pr(v,x,z|w,y)Pr(w|y)Pr(y) \\
& =Pr(v,x,z|w,y)Pr(w,y) \\
\end{aligned}
$$
$整理得到$
$$
Pr(w,y)=\frac{Pr(v,w,x,y,z)}{Pr(v,x,z|w,y)}
$$
$同理可得$
$$
Pr(v)=\frac{Pr(v,w,x,y,z)}{Pr(w,x,y,z|v)}
$$
#### 2.3
$$
\begin{aligned}
Pr(w,x,y,z)
& =Pr(z|w,x,y) Pr(w,x,y) \\
& =Pr(z|w,x,y)Pr(w|x,y)Pr(x,y)
\end{aligned}
$$
$得证$
#### 2.4
$$
\begin{aligned}
Pr(c=2|h=1)
& =\frac{Pr(h=1,c=2)}{Pr(h=1)} \\
& =\frac{Pr(h=1,c=2)}{Pr(h=1,c=1)+Pr(h=1,c=2)} \\
& =\frac{Pr(h=1|c=2)Pr(c=2)}{Pr(h=1,c=1)Pr(c=1)+Pr(h=1|c=2)Pr(c=2)} \\
& =\frac{0.5\times0.8}{0.5\times0.5+0.5\times0.8} \\
& =\frac{8}{13}
\end{aligned}
$$
#### 2.5
$y\ 和\ z\ 不相互独立。考虑任意一个概率分布Pr(y,z)并且\ y\ 和\ z\ 不独立，\\那么我们可以找到一个概率分布Pr(x)，它并没有提供关于\ y\ 和\ z\ 的任何信息\\
即\ x\ 和\ y\ 相互独立且\ x\ 和\ z\ 相互独立$
#### 2.6
$$
\begin{aligned}
Pr(x|y=y^*)
& =\frac{Pr(x,y=y^*)}{Pr(y=y^*)} \\
& =\frac{Pr(x)Pr(y=y^*)}{Pr(y=y^*)}  (因为x和y相互独立)\\
& =Pr(x)
\end{aligned}
$$
得证
#### 2.7
$（这道题不太懂，给定的条件不是已经证明了独立性了吗？）$
$$
\begin{aligned}
Pr(w,x,y,z)
& =Pr(w)Pr(z|y)Pr(y|x,w)Pr(x) \\
& =Pr(z|y)Pr(y|x,w)Pr(x,w)（代入Pr(x,w)=Pr(x)Pr(w)）\\
& =Pr(z|y)Pr(x,y,w) \\
又有\;Pr(w,x,y,z) &=Pr(z|x,y,w)Pr(x,y,w)
\end{aligned}
$$
$所以，Pr(z|y)=Pr(z|x,y,w)，又$
$$
\begin{aligned}
Pr(w,x,y,z)
& =Pr(z|x,y,w)Pr(y|x,w)Pr(x|w)Pr(w) \\
& =Pr(z|y)Pr(y|x,w)Pr(x|w)Pr(w) \\
& \; \\
Pr(w,x,y,z)& =Pr(w)Pr(z|y)Pr(y|x,w)Pr(x)
\end{aligned}
$$
$对比两式，可以得到Pr(x|w)=Pr(x)，同理可得Pr(w|x)=Pr(w)$

$所以，x和w相互独立$

#### 2.8
$（为啥概率总和不为1）$

$设第一次骰子朝上的值为\bm X，第二次为\bm Y$
$$
\begin{aligned}
E[\bm X]
 =&1\times 1/12+2\times 1/12+3\times 1/12 \\
 &+4\times 1/12+5\times 1/6+6\times 1/12 \\
 =&13/6
\end{aligned}
$$
$计算两次投掷可以列表计算$
$$
\begin{aligned}
E[\bm X+\bm Y]
=& 2\times 1/144+3\times 2/144+4\times 3/144 \\
&+5\times 4/144+6\times 7/144+7\times 8/144 \\
& +8\times 7/144+9\times 6/144+10\times 6/144 \\
& +11\times 4/144+12\times 1/144\\
=&91/36
\end{aligned}
$$
#### 2.9
$首先我们假定随机变量x为连续值$
$$
\begin{aligned}
E[k]
& =\int kPr(x)\text dx \\
& =k\int Pr(x)\text dx \\
& =k
\end{aligned}
$$
$性质1得证$
$$
\begin{aligned}
E[kf[x]]
& =\int kf[x]Pr(x)\text dx \\
& =k\int f[x]Pr(x)\text dx \\
& =kE[f[x]]
\end{aligned}
$$
$性质2得证$
$$
\begin{aligned}
E[f[x]+g[x]]
& =\int (f[x]+g[x])Pr(x)\text dx \\
& =\int f[x]Pr(x)\text dx +\int g[x]Pr(x)\text dx \\
& =E[f[x]]+E[g[x]]
\end{aligned}
$$
$性质3得证$
$$
\begin{aligned}
E[f[x]g[y]]
& =\iint f[x]g[y]Pr(x,y)\text dx\text dy\\
& =\iint f[x]g[y]Pr(x)Pr(y)\text dx\text dy \\
& =\iint f[x]Pr(x)\text dx \cdot g[y]Pr(y)\text dy\\
& =\int f[x]Pr(x)\text dx \int g[y]Pr(y)\text dy \\
& =E[f[x]]E[g[y]]
\end{aligned}
$$
$性质4得证$

#### 2.10
$$
\begin{aligned}
E[(x-\mu)^2]
& =E[x^2-2\mu x+\mu^2]\\
& =E[x^2]+E[-2\mu x]+E[\mu^2]\\
& =E[x^2]-2\mu E[x]+\mu^2\\
& =E[x^2]-2E[x]E[x]+E[x]E[x]\\
& =E[x^2]-E[x]E[x]
\end{aligned}
$$