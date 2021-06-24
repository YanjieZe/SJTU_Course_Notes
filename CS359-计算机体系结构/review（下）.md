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

## Handle Miss

write miss(single word block):

- write allocate
- No-write allocate

Read miss(multi word):

- early restart：先执行下一个，等全部data拿到再执行
- Requested word first
- Non-blocking cache

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

## ☆Summary

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210624095206448.png" alt="image-20210624095206448" style="zoom:50%;" />

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210620211405862.png" alt="image-20210620211405862" style="zoom:50%;" />

<img src="https://shuiyuan.sjtu.edu.cn/uploads/default/original/3X/3/a/3aa0aaec941746b8c44503bd37ecdd047aa3ded7.png" style="zoom:50%;" />

# 8 DLP

## Vector Architecture

### Vector Programming Model

**VLR是向量长度寄存器。**

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210623151556902.png" alt="image-20210623151556902" style="zoom:50%;" />

### Vector Instructions

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210623151648915.png" alt="image-20210623151648915" style="zoom:50%;" />

### Vector Instruction Set Advantages

- Compact: 一条指令代表N条指令
- Expressive: 
  - 表示n条指令是独立的
  - 用相同的functional unit
- Scalabel: 可以在有更多流水线的机器上运行

### Example: DAXPY

DAXPY是Double Precision a\*x plus Y的缩写。
$$
Y=a\times X+Y
$$
VMIPS code:

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210623153209154.png" alt="image-20210623153209154" style="zoom:50%;" />

### Vector Arithmetic Execution

- deep pipeline
- Elements are independent => simplify the control logic

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210623154039387.png" alt="image-20210623154039387" style="zoom:50%;" />

### vector execution time

- Length of operand vectors
- 结构冒险
- 数据相关

### Vector chaining

和forwarding类似，用来解决**数据冒险**。

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210623154513054.png" alt="image-20210623154513054" style="zoom:50%;" />

需要多个read port/write port来进行操作。

优点：减少指令的执行时间

### ☆优化

- 怎么快于one element per clock cycle？答：多个pipeline lines，一次算出多个<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210623154744394.png" alt="image-20210623154744394" style="zoom:50%;" />
- 怎么编程一个vector computer？<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210623160651953.png" alt="image-20210623160651953" style="zoom:50%;" />
- 怎么处理vector length不知道的情况？答：**用Vector Length Register**来控制vector操作的长度。<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210623161340860.png" alt="image-20210623161340860" style="zoom:50%;" />
- 如果代码里有一个if操作，怎么向量化？答：用vector mask register和maskable vector instruction。
  - vector mask register<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210623162523831.png" alt="image-20210623162523831" style="zoom:50%;" />
  - maskable vector instruction<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210623162613855.png" alt="image-20210623162613855" style="zoom:50%;" />
- Vector processor需要memory system的什么？答：带宽
  - Vector Memory-Memory Machine：所有指令在memory里完成
  - Vector Register Machines：先load到寄存器完成，再store回memory
  - 所以Vector Memory-memory Architecture需要更大的main memory bandwidth
  - **memory banks**可以提升bandwidth。<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210623163902820.png" alt="image-20210623163902820" style="zoom:50%;" />
- vector processor怎么处理multi-dimensional matrices？答：stride<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210623165247486.png" alt="image-20210623165247486" style="zoom:50%;" />
- 怎么处理sparse matrices？答：scatter-gather，用index vector表明非0向量。<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210623165937250.png" alt="image-20210623165937250" style="zoom:50%;" />

## SIMD Instruction Set Extensions

Goal: 把64-bit register分成$2\times 32b, 4\times 16b, 8\times 8b$。

例子：<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210623170955979.png" alt="image-20210623170955979" style="zoom:50%;" />

优点：

1. cost little
2. require little extra state
   1. save memory bandwidth
   2. avoid page fault in the middle of the vector

缺点：

1. Limited instruction set: 
   1. Fixed number of data operands in opcode; 
   2. Fixed vector length; 
   3. No strided load/store or scatter/gather; 

2. Limited vector register length; 

3. Limited mask registers. 	

## GPU

**Texture Processing Cluster** (TPC)

TPC consists of **Streaming Multiprocessors**(SM)

SM consists of Stream Processor

Each SM supports up to 1024 threads



## GPU Memory Hierarchy

shared memory 是同一个block里不同thread共享的。

device memory是不同block可以共享的。

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210623185540029.png" alt="image-20210623185540029" style="zoom:50%;" />

## Overview of CUDA Programming

A kernel is executed as a Grid of thread Blocks.

一个kernel运行一个gird，一个grid包含很多个thread block。所以这些block执行的是同一个kernel，但是data不同。

一个例子：<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210623184410953.png" alt="image-20210623184410953" style="zoom:50%;" />

☆一个计算题：

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210623184614379.png" alt="image-20210623184614379" style="zoom:50%;" />

一个grid由多个thread block组成（512个），一个SIMD指令操作32个元素，所以一个grid可以执行512/32个SIMD指令。



a warp: threads execute the same instructions at same time

a SP runs on CUDA thread

**global block scheduler** manages and allocates blocks of threads to SM



**life cycle of thread**:

- Grid is started on GPU
- a block of threads allocated to a SM
- SM organizes threads of a given block into **warps**
- Warps are scheduled on SM

GPU线程的生命周期：

- gird在GPU上启动
- thread 分配到Stream Multi processor
- SM组织这些thread成warp（执行同一个指令）
- warps在SM上执行
