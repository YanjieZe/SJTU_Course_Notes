# 基本图算法

<center>
  Yanjie Ze, May 2021
</center>

## DFS

每个顶点只explore一次。每条边check两次：
$$
T=O(|V|+|E|)
$$


## BFS

用link list队列实现的话O(1)，每个点入队出队一次，每条边检查两次：
$$
T=O(|V|+|E|)
$$


# 单源最短路

## Dijkstra（无负权）

把点插入堆V次，提出堆V次，2E次再插入点。

如果用二叉堆：
$$
T=O((|V|+|E|)log|V|)
$$

## Bellman-Ford（有负权）

<img src="/Users/yanjieze/Downloads/IMG_1671(20210525-001011).PNG" style="zoom30%;" />

$$
Running Time: T=O(|V|\times|E|)
$$





# 多源最短路

## Floyd-Warshall

![IMG_1670(20210525-000308)](/Users/yanjieze/Downloads/IMG_1670(20210525-000308).PNG)
$$
Running\ Time: O(|V|^3)
$$



## Johnson

首先用bellman-ford进行reweight： 
$$
T_1=O(|V|\times|E|)
$$
再对每个点用Dijkstra：
$$
T_2=O(|V|\times(|V|+|E|)log|V|)=O((|V|^2+|V|\times|E|)log|V|)
$$
再reweight回去，并获得最短路：
$$
T_3=O(|V|^2)
$$
总共为：
$$
T=O((|V|^2+|V|\times|E|)log|V|)
$$




# 网络流

## Ford-Fulkerson

<img src="/Users/yanjieze/Downloads/IMG_1673(20210525-004747).PNG" alt="IMG_1673(20210525-004747)" style="zoom:50%;" />



<img src="/Users/yanjieze/Downloads/IMG_1672(20210525-004351).PNG" style="zoom:50%;" />



## Improved Ford-Fulkerson

<img src="/Users/yanjieze/Downloads/IMG_1674(20210525-005549).PNG" alt="IMG_1674(20210525-005549)" style="zoom:50%;" />

Find a max flow in $O(mlogC)$ augmentations.

Thus,
$$
Running\ Time:O(m^2logC)
$$
