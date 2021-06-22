# Hard Problems in CS499

Yanjie Ze, June 2021

# Set theory

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210620222251085.png" alt="image-20210620222251085" style="zoom:50%;" />

# Tall or Width

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210620235731576.png" alt="image-20210620235731576" style="zoom:50%;" />

# Counting

![image-20210621101022182](/Users/yanjieze/Library/Application Support/typora-user-images/image-20210621101022182.png)

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210621102035780.png" alt="image-20210621102035780" style="zoom:50%;" />

Problem5可以想像成求非负整数解个数的那个问题。

# 容斥原理

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210621103635818.png" style="zoom:50%;" />

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210621104305069.png" alt="image-20210621104305069" style="zoom:50%;" />

# Generating Function

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210621140333214.png" alt="image-20210621140333214" style="zoom:50%;" />

# Recurrence Function

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210621140926418.png" alt="image-20210621140926418" style="zoom:50%;" />

# 函数的渐进式比较

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210621142312332.png" alt="image-20210621142312332" style="zoom:50%;" />

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210621144114254.png" alt="image-20210621144114254" style="zoom:50%;" />

这一题很难想啊。第一小问的答案就不放了，看到了自己想想，第二小问的解答：

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210621145809415.png" alt="image-20210621145809415" style="zoom:50%;" />

# 图同构

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210621164704081.png" alt="image-20210621164704081" style="zoom:50%;" />

思路：

- 先2n选2，再2n-2选2，再...
- 最后要除以n!，因为之前的选法其实做了一个组合。

# 树

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210621170258422.png" alt="image-20210621170258422" style="zoom:50%;" />

1到2很简单，2到1需要用一下归纳法。**注意**： 归纳法从n+1去掉一个叶节点构造出n的树，而不是从n加一个点变成n+1的树。后者没有证明到generality。

具体过程如下。

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210621171623476.png" alt="image-20210621171623476" style="zoom:50%;" />



# 树的同构

TODO：再把这一题看一下

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210621174915453.png" alt="image-20210621174915453" style="zoom:50%;" />

# 概率论

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210621194216389.png" alt="image-20210621194216389" style="zoom:50%;" />

# 概率方法

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210621195832291.png" alt="image-20210621195832291" style="zoom:50%;" />

思路：

- 第一问用概率方法做
- 第二问类似于las vegas 算法。
- 第二问的解答：<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210621195916352.png" alt="image-20210621195916352" style="zoom:50%;" />

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210621200409364.png" alt="image-20210621200409364" style="zoom:50%;" />

这一题套一下lovasz local lemma就行，关键在于怎么设计p和d。



# 随机图

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210621200928556.png" alt="image-20210621200928556" style="zoom:50%;" />

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210621201511830.png" alt="image-20210621201511830" style="zoom:50%;" />

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210621203411410.png" alt="image-20210621203411410" style="zoom:50%;" />

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210621204601054.png" alt="image-20210621204601054" style="zoom:50%;" />

这一题求期望的时候要分类讨论一下。
