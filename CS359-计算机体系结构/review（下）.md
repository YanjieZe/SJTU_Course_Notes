# CS359: Computer Architecture

Yanjie Ze, June 2021

This file contains Chapter 7, 8.

# 7 Memory

## Memory Hierarchy

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210620195511095.png" alt="image-20210620195511095" style="zoom:50%;" />

## DRAM and SRAM

- SRAM is faster.
- SRAM is high power and expensive.
- SRAM not need to refresh

## Terminology

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210620200039165.png" alt="image-20210620200039165" style="zoom:50%;" />

## Data management

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210620200304981.png" alt="image-20210620200304981" style="zoom:50%;" />

## Four Memory Heirarchy Question

• **Block Placement**: n-way associative (*n* from 1 to the block number of cache).

• **Block Identifification**: Match(Block address and address tag)

• **Block Replacement**: Block Replacement algorithm just like page (benchmark:Greedy-OPT,LRU,FIFO,LFU,MFU...)

• **Write Strategy**: Write through , Write back (Modify(dirty) bit)

## Block Replacement

- Fully associative
- Direct mapped
- Set associative

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210620200824892.png" alt="image-20210620200824892" style="zoom:50%;" />

## Block Identification

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210620200809857.png" alt="image-20210620200809857" style="zoom:50%;" />

## **Measuring Memory Hierarchy Performance** 

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210620202543806.png" alt="image-20210620202543806" style="zoom:50%;" />

## Virtual Address Translation

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210620201605213.png" alt="image-20210620201605213" style="zoom:50%;" />

## Page Table

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210620201709497.png" alt="image-20210620201709497" style="zoom:50%;" />

## TLB

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210620202238177.png" alt="image-20210620202238177" style="zoom:50%;" />

## Six Basic Cache Optimizations

三种miss：

- compulsory
- capacity(account for the largest proportion. )
- conflict: In set associative and direct mapped, conflict misses occur

六种优化方式：

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210620204923203.png" alt="image-20210620204923203" style="zoom:50%;" />

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210620203008946.png" alt="image-20210620203008946" style="zoom:50%;" />

1. Larger block size：blok数量更少，更容易发生冲突，conflict miss增加，但是更加利用了局部性，compulsory miss减少了

2. Larger cache capacity: hit time增加了，但是miss rate减少

3. Higher associativity: 
   1. 8-way is good
   2. 2:1 cache rule of thumb: 一个direct mapper的size N cache和一个two-way set associative cache of size N/2有一样的miss rate。
   
4. Higher number of cache levels: <img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210620210306359.png" alt="image-20210620210306359" style="zoom:50%;" />
   5. global miss rate
   2. Local miss rate

5. Giving priority to read misses over writes:可能会有RAW冒险。解决方法有两种：<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210620210937509.png" alt="image-20210620210937509" style="zoom:50%;" />

6. Avoiding address translation in cache indexing: 就是cache也用虚拟地址，少一次虚拟地址到物理地址的转化。但是有三个问题：

   1. Protection
   2. process switching: Each time a process is switched, the cache should be flushed!因为每个process对应的虚拟地址不一样。
   3. Synonyms or Aliases

   - ☆解决办法：block offset+index<=page offset 

## Ten Advanced Cache Optimizations

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210620213555368.png" alt="image-20210620213555368" style="zoom:50%;" />

## Summary

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210620211405862.png" alt="image-20210620211405862" style="zoom:50%;" />

<img src="https://shuiyuan.sjtu.edu.cn/uploads/default/original/3X/3/a/3aa0aaec941746b8c44503bd37ecdd047aa3ded7.png" style="zoom:50%;" />

# 8 DLP

