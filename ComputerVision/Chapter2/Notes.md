1. @[toc]
   ## 第2章 概率概述
   ### 2.1 随机变量
   1. 随机变量 $x$ 表示一个不确定的数量，可以是连续或者离散的
   2. 概率分布 $Pr(x)$
   3. 离散变量的概率分布可以用**直方图**或**Hinton图**表示，每个结果有一个正概率，概率之和为1
   4. 连续变量的概率分布可以用**概率密度函数**（PDF）来表示，概率密度表示随机变量的取该值的相对可能性，可以取任意正值，然而，PDF的积分总是1

   ### 2.2 联合概率
   1. $x$ 和 $y$ 的联合概率分布表示记作 $Pr(x,y)$，逗号可以理解为“和”，所有结果的概率之和总是1

   ### 2.3 边缘化
   1.如果 $x$ 和 $y$ 连续，并且已知 $Pr(x,y)$，那么
   $$Pr(x)=\int Pr(x,y)\text{d}y$$ 
   $$Pr(y)=\int Pr(x,y)\text{d}x$$ 
   2. 已知 $Pr(x,y)$，求 $Pr(x)$ 和 $Pr(y)$ 称为**边缘分布**，其他变量的积分/求和过程称为**边缘化**
   3. 计算概率分布 $Pr(x)$ 的过程可以解释为计算 $x$ 的概率分布且忽略（或不考虑） $y$ 的值

   ### 2.4 条件概率
   1. 给定 $y$ 取 $y^*$ 时 $x$ 的条件概率记作 $Pr(x|y=y^*)$，“|”可以理解为“给定”
   2. 条件概率 $Pr(x|y=y^*)$ 可以由联合分布中的切片 $Pr(x,y=y^*)$ 计算出来，切片值表示当 $y=y^*$ 时 $x$ 取不同值的相对概率。因为它们仅构成联合分布的一部分，总和不为1，所以计算条件概率分布，需要规范化切片中的总概率
   $$Pr(x|y=y^*)=\frac{Pr(x,y=y^*)}{\int{Pr(x,y=y^*)}}=\frac{Pr(x,y=y^*)}{Pr(y=y^*)}$$
   3. 上式简化缩写为 $$Pr(x|y)=\frac{Pr(x,y)}{Pr(y)}$$重新整理得：
   $$Pr(x,y)=Pr(x|y)Pr(y)$$ 
   4. 多变量时，可以不断应用条件概率分布将联合概率分布分解为乘积形式：
   $$Pr(w,x,y,z)=Pr(w,x,y|z)Pr(z)$$
   $$=Pr(w,x|y,z)Pr(y|z)Pr(z)$$
   $$=Pr(w|x,y,z)Pr(x|y,z)Pr(y|z)Pr(z)$$
   $Pr(w|x,y,z)$表示在给定 $x,y,z$ 的情况下 $w$ 的概率

   ### 2.5 贝叶斯公式
   1. 贝叶斯公式：
   $$Pr(y|x)=\frac{Pr(x|y)Pr(y)}{Pr(x)}$$
   $$=\frac{Pr(x|y)Pr(y)}{\int Pr(x,y)\text{d}y}$$
   $$=\frac{Pr(x|y)Pr(y)}{\int Pr(x|y)Pr(y)\text{d}y}$$
   2. **后验概率：**$Pr(y|x)$，代表给定 $x$ 下 $y$ 的概率
   **先验概率：**$Pr(y)$，代表在考虑 $x$ 之前 $y$ 的概率
   **似然性：**$Pr(x|y)$
   **证据：**$Pr(x)$
   3. 在计算机视觉中，常用条件概率 $Pr(x|y)$ 表示变量 $x$ 和 $y$ 的关系，然而我们主要感兴趣的是变量 $y$，因此，概率 $Pr(y|x)$ 就用贝叶斯公式来计算

   ### 2.6 独立性
   1. 如果从变量 $x$ 不能得到变量 $y$ 的任何信息（反之亦然），就称 $x$ 和 $y$ 是独立的，可以表示为：
   $$Pr(x|y)=Pr(x)$$
   $$Pr(y|x)=Pr(y)$$
   代入条件概率公式中可得：
   $$Pr(x,y)=Pr(x|y)Pr(y)=Pr(x)Pr(y)$$

   ### 2.7 期望
   1. 如果从概率分布中抽取大量样本，计算每个样本的函数，并求这些值的平均值，其结果就是期望。在离散及连续情况下，一个随机变量 $x$ 的函数 $f[\cdot]$ 的期望值分别定义为
   $$E[f[x]]=\sum_x f[x]Pr(x)$$ 
   $$E[f[x]]=\int f[x]Pr(x)\text{d}x$$
   2. 特殊函数的期望
   3. 期望的四条性质
   $$E[k]=k$$
   $$E[kf[x]]=kE[f[x]]$$
   $$E[f[x]+g[x]]=E[f[x]]+E[g[x]]$$
   $$E[f[x]g[y]]=E[f[x]]E[g[y]]（若x和y独立）$$