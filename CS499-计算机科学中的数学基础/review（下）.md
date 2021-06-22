# CS499: Mathematical Foundations of Computer Science（下）

Yanjie Ze, June 2021

*This note contains some hard proofs or points worth noting, based on Associate Professor [Huan Long](http://basics.sjtu.edu.cn/~longhuan/)'s slides, collected by [Yanjie Ze](http://yanjieze.xyz/website).*

# 11 图论引导

## 导出子图

在图论中，一个图的*导出子图*(induced subgraph)是指，由该图顶点的一个子集和该图中两端均在该子集的所有边的集合组成的图。

## 生成子图

*生成子图*,亦称支撑子图,图论中一类图的统称。由一个图的全部顶点及连结这些顶点的部分边构成的图称为原图的支撑子图。

## 特殊图

- cycle
- path
- Bipartite graph二分图
- Complete graph完全图
- Complete bipartite graph完全二分图
- r-正则图：点的度数都为r

## 简单图

没有自环和重边的图

## 极大连通子图

## 握手定理

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210618112907277.png" alt="image-20210618112907277" style="zoom:50%;" />

# 12 Graph: Isomorphism and Score

## 图同构

- 点的双射函数
- 边的对应存在关系

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210621162127012.png" alt="image-20210621162127012" style="zoom:50%;" />

## 非同构图的计数

先粗略放缩，再估值。

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210618200445808.png" alt="image-20210618200445808" style="zoom:50%;" />

## Graph Score

degree sequence

两个图同构一定score一样，反之不一定。

不是所有sequence都是一个score。



## Score Theorem

- 先求n-dn。
- 序号小于n-dn的不变
- 序号大于等于n-dn的减1。
- 并且序列不包含dn。（意味着去掉这个点）

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210618200843083.png" alt="image-20210618200843083" style="zoom:50%;" />



## 证明score theorem

TODO：再看看这个吧，大概思路懂了但是没完全懂最后一页。



# 13 Applications of Handshake lemma

## Sperner 引理

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210618114021165.png" alt="image-20210618114021165" style="zoom:50%;" />

## Sperner引理的证明

证明思路：

- 在外面加一个点v，构造图
- 把一个三角形看作一个vertex，把有红蓝边的相邻点连起来。
- 由于v的度数一定是 **奇数**， 所以一定存在一个三色的小三角。（握手定理推论）

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210618114324311.png" alt="image-20210618114324311" style="zoom:50%;" />

## Sperner引理的一般形式

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210618114958074.png" alt="image-20210618114958074" style="zoom:50%;" />

## 应用一：不动点

TODO：这里可以再好好想一想是怎么构造的。

证明思路：

- 构造颜色
- 着色
- 无限分割

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210618115536636.png" style="zoom:50%;" />

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210618115549086.png" alt="image-20210618115549086" style="zoom:50%;" />

## 应用二：hex game

一定有一个winner。

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210618115915413.png" alt="image-20210618115915413" style="zoom:50%;" />



## 握手定理与哈密尔顿图

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210618202634529.png" alt="image-20210618202634529" style="zoom:50%;" />

TODO：这个的证明也好好看一下。



# 14 The number of spanning trees

## 树的等价刻画

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210618234948459.png" alt="image-20210618234948459" style="zoom:50%;" />



## 树的计数：Caley定理

Caley 定理(Caley’s formula)： 

n个顶点能构成的不同树一共有$n^{n-2}$种。



## A proof via score

用score证明，首先需要证明一个性质：一个和为2n-2的degree sequence的生成树有如下这么多种。

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210621172232009.png" alt="image-20210621172232009" style="zoom:50%;" />

证明思路：

## A proof with Vertebrates

TODO：看懂

## Proof working with determinants

TODO：看懂



# 15 Tree Isomorphism

## 有根树同构

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210619090331518.png" alt="image-20210619090331518" style="zoom:50%;" />

## 有根树同构判定算法

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210619090717666.png" alt="image-20210619090717666" style="zoom:50%;" />

## 有根树同构判定算法的证明

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210619091128110.png" alt="image-20210619091128110" style="zoom:50%;" />

## 从编码恢复到树结构

0就往上走，1就往下走

（或者0往下走，1往上走，一样的）

## 为一般树找根

- 距离：两点之间的最短路径的长度
- 偏心率：和距离最远的点的距离
- 中心：偏心率最小的点的集合

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210619091949544.png" alt="image-20210619091949544" style="zoom:50%;" />

若是出现有两个根的情况：

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210619092115552.png" alt="image-20210619092115552" style="zoom:50%;" />

# 16 A quick review of probability theory

## Application1: Identify polynomials

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210619003002576.png" alt="image-20210619003002576" style="zoom:50%;" />



TODO：QUESTON：为什么是d/100d？值的个数和值的范围有关系吗？？

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210619002811301.png" alt="image-20210619002811301" style="zoom:50%;" />



## Application 2: Monty Hall problem

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210619003245321.png" alt="image-20210619003245321" style="zoom:50%;" />



## Tuesday boy problem

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210619004021166.png" alt="image-20210619004021166" style="zoom:50%;" />

## Bayes公式

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210619082218549.png" alt="image-20210619082218549" style="zoom:50%;" />

## 期望、方差

## 二项分布、几何分布

## 几何分布的memoryless

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210619083940654.png" alt="image-20210619083940654" style="zoom:50%;" />

## 几何分布的期望

$$
E(x)=\frac 1p
$$

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210619084224619.png" alt="image-20210619084224619" style="zoom:50%;" />

## Markov不等式

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210619085216376.png" alt="image-20210619085216376" style="zoom:50%;" />



## Application: Coupon Collector’s Problem

![image-20210619085637738](/Users/yanjieze/Library/Application Support/typora-user-images/image-20210619085637738.png)

## Chebyshev不等式

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210619085439307.png" alt="image-20210619085439307" style="zoom:50%;" />



# 17 The Probabilistic Method
## Basic Counting Argument
### 1. Cards Shuffling

### 2. Difficult Boolean Functions

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210619095134058.png" alt="image-20210619095134058" style="zoom:50%;" />

### 3. Edge Coloring

R(3,3)=6

在一个K6的完全图里，每一个点（wiki上是错的，是点，不是边）涂上红色，或者蓝色，一定有一个红色的，或者蓝色的三角形。

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210619100846842.png" alt="image-20210619100846842" style="zoom:50%;" />

最后一步的放缩其实应该用到了Union Bound。

### 4.  Coloring set systems by two colors

一个由集合构成的集合，他的每个元素（某个集合）都可以二着色，则为2-colorable。

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210619102015528.png" alt="image-20210619102015528" style="zoom:50%;" />



定义s(k)，k为M中集合的大小，s(k)表示集合的数量。

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210619103203698.png" alt="image-20210619103203698" style="zoom:50%;" />

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210619102604792.png" alt="image-20210619102604792" style="zoom:50%;" />

这个上界放的比较宽，然后让存在single color的概率一定小于1，就可以证明存在2-coloring。

直观理解：单个集合的元素远少于总的元素数量，二着色绰绰有余。



## The Expectation Argument

### 1. *Dense* Partition

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210619104210608.png" alt="image-20210619104210608" style="zoom:50%;" />

对中间这行的解释：

分母2n选n，做A（或B）

分子固定u和v再选n-1做A（或B），由于不知道u和v哪个在A里面，要乘2。

### Las Vegas算法

思路：求出cross edge大于等于m/2的概率，然后这是几何概率，期望是1/p，因此要想sample出来的次数就是期望。

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210619104723916.png" alt="image-20210619104723916" style="zoom:50%;" />

### 2. Independent set

先证明一个引理：

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210621153105406.png" alt="image-20210621153105406" style="zoom:50%;" />

思路：好像是求每个点在独立集中的概率，然后求期望之和，就是一个最大独立集的下限。

然后利用这个引理，并且代入度数最大的时候的情况，就是turan定理。

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210621153641335.png" alt="image-20210621153641335" style="zoom:50%;" />

### 3 Maximum Satisfaction

m个从句，第i个从句有ki个文字，要想可满足，至少需要：

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210621153933318.png" alt="image-20210621153933318" style="zoom:50%;" />

证明思路：

- 求第i个从句可满足的概率：1-不可满足的概率
- 求所有从句可满足的期望（求个和），然后做个放缩就行

## Lovasz Local Lemma

Dependency graph: 两个事件相互独立，则他们之间没有边。

Lovasz Local Lemma:

- 假设有一堆事件（暂且称呼他们为坏事件，方便直观理解），发生的概率都小于等于p
- 他们的dependency graph中每个事件的度数小于等于d
- 并且d和p有这样的关系：$4dp\leq 1$
- 那么，所有坏事件都不发生的概率大于0。

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210621155433197.png" alt="image-20210621155433197" style="zoom:50%;" />

## Application 1: Edge-disjoint path

## Application 2: Satisfiability

基本思路：

- 设定坏事件
- 求p和d
- 根据$4pd\leq 1$得出结论

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210621160325670.png" alt="image-20210621160325670" style="zoom:50%;" />

# 18 Introduction to Random Graphs

这一章的内容记录在手写的note上也有。

## Central Limit Theorem

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210619110502255.png" alt="image-20210619110502255" style="zoom:50%;" />

## Pij

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210621202012877.png" alt="image-20210621202012877" style="zoom:50%;" />

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210621202002377.png" alt="image-20210621202002377" style="zoom:50%;" />

## First Moment Method

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210621203722645.png" alt="image-20210621203722645" style="zoom:50%;" />

## Second Moment Method

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210621203809027.png" alt="image-20210621203809027" style="zoom:50%;" />

## ☆Diameter 2

TODO：最后一个划分a=4，a=3, a=2的是什么怎么来的？



# 19 Random Graphs

## Phase Transition

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210619161047981.png" alt="image-20210619161047981" style="zoom:50%;" />

## Increasing Property

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210619155638598.png" alt="image-20210619155638598" style="zoom:50%;" />

## ☆Replication

这里有一个不等式。

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210619161506291.png" alt="image-20210619161506291" style="zoom:50%;" />

## Theorem

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210619162651585.png" alt="image-20210619162651585" style="zoom:50%;" />

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210619162636773.png" alt="image-20210619162636773" style="zoom:50%;" />

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210619162707737.png" alt="image-20210619162707737" style="zoom:50%;" />

TODO：TODO：把最后一半证明完。

