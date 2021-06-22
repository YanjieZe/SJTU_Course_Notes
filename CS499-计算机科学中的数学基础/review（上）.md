# CS499: Mathematical Foundations of Computer Science（上）

Yanjie Ze, June 2021

*This note contains some hard proofs or points worth noting, based on Associate Professor [Huan Long](http://basics.sjtu.edu.cn/~longhuan/)'s slides, collected by [Yanjie Ze](http://yanjieze.xyz/website).*

# 03 序 ordering

## 线性扩充

用归纳法证明线性扩充。

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210617191339400.png" alt="image-20210617191339400" style="zoom:50%;" />



# 04 或者宽，或者高

## 最大独立集和最长链

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210617192255312.png" alt="image-20210617192255312" style="zoom:50%;" />

## 定理：最长链长度=最小反链划分数

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210617192413933.png" alt="image-20210617192413933" style="zoom:50%;" />

## 证明：最长链长度=最小反链划分数

**思路：两边夹逼，有一边要稍微绕一下**

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210617193645978.png" alt="image-20210617193645978" style="zoom:50%;" />

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210617193906478.png" alt="image-20210617193906478" style="zoom:50%;" />

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210617194356386.png" alt="image-20210617194356386" style="zoom:50%;" />



## 定理的推论：或者宽，或者高


$$
\alpha \cdot \omega \geq |S|
$$


<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210617194708672.png" alt="image-20210617194708672" style="zoom:50%;" />

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210617194806442.png" alt="image-20210617194806442" style="zoom:50%;" />

## Erdos-Szekeres定理

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210617194946123.png" alt="image-20210617194946123" style="zoom:50%;" />

## Mirsky定理和Dilworth定理

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210617195455900.png" alt="image-20210617195455900" style="zoom:50%;" />



# 05 Combinatorial Counting

## Count空表格

n个球放进m个盒子

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210617195723446.png" alt="image-20210617195723446" style="zoom:50%;" />



## 最简单的两种情况

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210617200143547.png" alt="image-20210617200143547" style="zoom:50%;" />



## n distinct balls into m distinct bins(unrestricted)

这个问题可以抽象成函数的映射，确定定义域和值域，有多少种函数？

答案是$m^n$。

可以用数学归纳法证明。

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210617200929196.png" alt="image-20210617200929196" style="zoom:50%;" />

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210617201137408.png" alt="image-20210617201137408" style="zoom:50%;" />



## n distinct balls into m distinct bins(<=1)

仍然可以抽象成，函数的映射。但是这个函数需要是单射(one to one)。

因此是：
$$
m(m-1)...(m-n+1)=(m)_n 
$$
<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210617201726393.png" alt="image-20210617201726393" style="zoom:50%;" />

## 应用1:求子集个数
## 应用2: counting the permutations

## 问题：一个集合的k大小的子集有多少个

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210617203008785.png" alt="image-20210617203008785" style="zoom:50%;" />



## ☆应用：counting non-negaive solutions

这里为什么是m+r-1？可以再好好想想。

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210617203345392.png" alt="image-20210617203345392" style="zoom:50%;" />



## 应用：counting positive solutions

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210617211812655.png" style="zoom:50%;" />



## 练习：一个等式

等式左边表明先n选i，再n选n-i，求和。

等式右边表明2n选n。

两边做的事情是一样的。

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210617212631323.png" alt="image-20210617212631323" style="zoom:50%;" />



## 范德蒙德等式

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210617212840378.png" alt="image-20210617212840378" style="zoom:50%;" />



## 根据count solutions的方法可更新表格

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210617213023910.png" alt="image-20210617213023910" style="zoom:50%;" />



## Multiset Coefficient

这个系数的意思是：给定一个有n个元素的集合，划分成k个子集，这样的划分的个数。（可以为空集）

TODO：这里的意思好像我的理解有点误差？再想想。

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210617213413261.png" alt="image-20210617213413261" style="zoom:50%;" />

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210617214256429.png" alt="image-20210617214256429" style="zoom:50%;" />



## ☆多项式定理

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210617214404514.png" alt="image-20210617214404514" style="zoom:50%;" />

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210617214450914.png" alt="image-20210617214450914" style="zoom:50%;" />



## 二项式定理的扩展

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210617214650404.png" alt="image-20210617214650404" style="zoom:50%;" />

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210617215740869.png" alt="image-20210617215740869" style="zoom:50%;" />



## 第二类Stirling number

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210617215946119.png" alt="image-20210617215946119" style="zoom:50%;" />

第二类斯特林数的性质：

等式左边表明n个元素分成k个集合

等式右边表明：

- 先取一个元素出来，再将剩下n-1个元素分成k个集合，再将该元素插入

- n-1个元素中划分k-1个集合，剩下单独一个元素做集合

  TODO：为什么取元素的时候不count？

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210617221151306.png" alt="image-20210617221151306" style="zoom:50%;" />



## 第一类Stirling number

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210617221413829.png" alt="image-20210617221413829" style="zoom:50%;" />

第一类斯特林数的性质：

![image-20210617221851835](/Users/yanjieze/Library/Application Support/typora-user-images/image-20210617221851835.png)



## 用斯特林数更新表格

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210617222131909.png" alt="image-20210617222131909" style="zoom:50%;" />



## Partition of a number

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210617222316626.png" alt="image-20210617222316626" style="zoom:50%;" />



## 用partition of a number 更新表格

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210617222513592.png" alt="image-20210617222513592" style="zoom:50%;" />



# 06 容斥原理

## 容斥原理

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210617223220304.png" alt="image-20210617223220304" style="zoom:50%;" />



## ☆应用一：错排公式

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210617224651789.png" alt="image-20210617224651789" style="zoom:50%;" />



## 应用二：欧拉函数

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210617224800284.png" alt="image-20210617224800284" style="zoom:50%;" />

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210617224851591.png" alt="image-20210617224851591" style="zoom:50%;" />



# 07 Generating Function

## Definition

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210618000755266.png" alt="image-20210618000755266" style="zoom:50%;" />

## ☆Generalized binomial theorem

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210618001019390.png" alt="image-20210618001019390" style="zoom:50%;" />

*：上面这个公式得记得。

## Operations

1. Addition：加
2. Constane linear expansion ：乘个常数
3. Shift right: 乘
4. Shift left: 减去前面几项再除
5. Subsititute
6. Differentiation
7. Integration
8. Multiplication/Convolution

## Application1：求多项式系数

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210618002212199.png" alt="image-20210618002212199" style="zoom:50%;" />



## Application2: 求斐波那契数

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210618002354791.png" alt="image-20210618002354791" style="zoom:50%;" />



## Application3: Catalan Number

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210618002535606.png" alt="image-20210618002535606" style="zoom:50%;" />

TODO：看懂这个。。有点难的。



# 08 Recurrence Relation

## 用特征多项式解决齐次线性递归式

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210618090957698.png" alt="image-20210618090957698" style="zoom:50%;" />



## 非齐次线性递归式

**先找齐次部分的通解，再找非齐次部分+齐次部分的特解。**

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210618091916328.png" alt="image-20210618091916328" style="zoom:50%;" />



# 09 函数的渐进式比较

## 常用符号

值得注意的是：
$$
f(n)=O(g(n))
$$
表示f的增长不比g快很多，即意味着：f可以比g稍微快一点，是常数级别的，f也可以比g慢。

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210618092241507.png" alt="image-20210618092241507" style="zoom:50%;" />



## 调和级数估值

**把调和级数拆分成多个部分，每个部分进行放缩。**

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210618093302002.png" alt="image-20210618093302002" style="zoom:50%;" />

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210618093533688.png" alt="image-20210618093533688" style="zoom:50%;" />

# 10 阶乘估值、二项式系数估值

## 阶乘估值的极值点估值

最简单的思路是用最大值n和最小值2进行放缩。

稍微进阶一点：

- 上界，放缩成两部分，取两个上界再乘。
- 下界，仍然分成两部分，但是把较小的前半部分去掉。

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210618094413356.png" alt="image-20210618094413356" style="zoom:50%;" />



## 阶乘估值的高斯估值

上界：

- 正过来和倒过来乘一下
- 基本不等式

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210618095049558.png" alt="image-20210618095049558" style="zoom:50%;" />

下界：主要用不等式：
$$
i(n+1-i)\geq n
$$
<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210618095421071.png" alt="image-20210618095421071" style="zoom:50%;" />



## 阶乘估值的进一步优化

进一步优化的时候，直接给了上界和下界，需要用到不等式：
$$
1+x\leq e^x
$$
上界证明比较简单，直接用一次不等式即可。

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210618100413928.png" alt="image-20210618100413928" style="zoom:50%;" />



下界证明，由于不等式$1+x\leq e^x$的方向，需要进行一些调整。

如何将$\leq$转化成$\geq$？提个-1出来。

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210618100751635.png" alt="image-20210618100751635" style="zoom:50%;" />

## Stirling公式

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210618101143812.png" alt="image-20210618101143812" style="zoom:50%;" />



## 二项式系数估值

初步估值：

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210618103300478.png" alt="image-20210618103300478" style="zoom:50%;" />

利用二项式定理估值：

基本思路是用二项式定理，求k个系数的和。

再代入$x=\frac{k}{n}$得到一个更加紧的上界。

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210618103123644.png" alt="image-20210618103123644" style="zoom:50%;" />

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210618103543406.png" alt="image-20210618103543406" style="zoom:50%;" />

