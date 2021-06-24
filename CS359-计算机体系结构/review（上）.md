# CS359 Computer Architecture(上)

Yanjie Ze, June 2021

This file includes Chapter 2,3,4,5,6, noted by Yanjie Ze.

# 1 Introduction

## Dependability依赖性

MTTF：Mean time to failure

MTTR: Mean time to repair

MTBF: Mean time between failures=MTTF+MTTR

Availability: MTTF / MTBF

**MTTF of the whole system:**
$$
MTTF_{system}=\frac{1}{\frac{1}{MTTF_1}+\frac{1}{MTTF_2}+\frac{1}{MTTF_3}}
$$


一个练习：

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210622001545559.png" alt="image-20210622001545559" style="zoom:50%;" />

## Principles for computer design

- take advantage of parallelism
- Principle of locality
- Focus on common case

## Amdahl's Law

$$
speedup_{overall}=\frac{1}{1-fraction_{enhanced}+\frac{fraction_{enhanced}}{speedup_{enhanced}}}
$$

## Processor Performance

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210622002811354.png" alt="image-20210622002811354" style="zoom:50%;" />



# 2 MIPS ISA

## MIPS-32

R型：6+5+5+5+5+6

I型：6+5+5+16

J型：6+26

## MIPS register

## byte addressing

一个地址对应一个byte。

## ☆Big endian and Little Endian

记住：小字节序：低位对低地址

![image-20210623201631132](/Users/yanjieze/Library/Application Support/typora-user-images/image-20210623201631132.png)

## ☆Load Byte and Save Byte

lb和sb指令对于byte进行操作。

## Branch Instructions

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210620085312015.png" alt="image-20210620085312015" style="zoom:50%;" />

 ## Branch Destination

Branch指令的目标地址计算公式： 
$$
PC = PC+4+signext(offset<<2)
$$
为什么用sign extension而不是zero extension？：

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210620085924963.png" alt="image-20210620085924963" style="zoom:50%;" />

## Jump

jump指令的更新公式：
$$
PC=PC[31:28]:(offset<<2)
$$


<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210623202526301.png" alt="image-20210623202526301" style="zoom:50%;" />

##  ☆Problem of Branching Far Away

有可能branch指令的offset不够用，无法到达更远的指令。

因为offset只有16位。

因此可以用jump指令。

具体来说：

当beq的offset太大了的时候，**编译器**会自动转化成bne+j的两个指令的组合，代码如下图所示。

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210620090736531.png" alt="image-20210620090736531" style="zoom:50%;" />

# 3 Single Cycle Processor

## 三种类型的指令

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210623203035065.png" alt="image-20210623203035065" style="zoom:50%;" />

这一部分，只讲如下几个指令的实现。

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210620092643264.png" alt="image-20210620092643264" style="zoom:50%;" />

## RTL

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210623203216234.png" alt="image-20210623203216234" style="zoom:50%;" />

## Combinaitional Elements

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210620093216866.png" alt="image-20210620093216866" style="zoom:50%;" />

## Storage Elements (State Elements)

register file:<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210620093402663.png" alt="image-20210620093402663" style="zoom:50%;" />

idealized memory: <img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210620093417360.png" alt="image-20210620093417360" style="zoom:50%;" />

## Clocking Methodology

**register file的CLK信号只有在write operation的时候才进行判断。**

**在read的时候，先判断地址是否有效，再在access time的时候读入（即时钟上升沿）。**

只在时钟上升沿的时候更新。

一个时钟周期：
$$
CycleTime =hold+LongestDelayPath+SetUp+ClockSkew
$$

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210623203620082.png" alt="image-20210623203620082" style="zoom:50%;" />

## Data Path

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210620093843173.png" alt="image-20210620093843173" style="zoom:50%;" />

1. Fetch: read `M[PC]`, then `PC<-PC+4`
2. Decode
3. Execute:
   - R type: `R[rd]<-R[rs] op R[rt]`
4. Memory
5. Write

## Fetch instructions

PC更新不需要一个write信号，只要时钟信号就行。

读instruction也不需要特意的read信号。

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210623204125360.png" alt="image-20210623204125360" style="zoom:50%;" />

## Load

注意，这里用的是sign extension。

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210623204929756.png" alt="image-20210623204929756" style="zoom:50%;" />



## Control Signal Logic

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210620110530158.png" alt="image-20210620110530158" style="zoom:50%;" />

## Two-level Decoding

- 指令中的op经过main control获得ALUop和其他控制信号
- ALUop结合func，经过ALU Control获得ALUctr控制信号

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210620110816895.png" alt="image-20210620110816895" style="zoom:50%;" />

## Generating ALUctr

ALUop要3个bit，是因为有R，or，add，sub等超过了2个bit可以表示的范围。

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210623210203359.png" alt="image-20210623210203359" style="zoom:50%;" />

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210620111820456.png" alt="image-20210620111820456" style="zoom:50%;" />

## Features of Single Cycle Processor

1. Mutually Exclusive Datapath Resources
2. Multiplexers
3. Write signals
4. Cycle Time Determined by Longest Path

## Disadvantages of Single Cycle Processor

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210620112859818.png" alt="image-20210620112859818" style="zoom:50%;" />

# 4 Multi Cycle Processor

## Register

五个新的register：

- MDR
- IR
- A
- B
- ALUout

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210623211720051.png" alt="image-20210623211720051" style="zoom:50%;" />

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210623211549387.png" alt="image-20210623211549387" style="zoom:50%;" />

 

## 概括

记得在decode的时候把ALUOut先用immediate给算出来。

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210620143044069.png" alt="image-20210620143044069" style="zoom:50%;" />

## 一个题目

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210623212909503.png" alt="image-20210623212909503" style="zoom:50%;" />

# 5 Pipelining

## Pipelining Speedup

理想情况是：
$$
Time\ to execute\ an\ instruction_{pipelining}=\frac{Time\ to\ execute\ an\ instruction_{sequential}}{num_{stages}}
$$
 实际是要小一点的。

## Difference between Pipelining and Multi-cycle

- 一个时钟周期内，多周期处理器只有一条指令在执行，但是pipeline有多条。
- pipeline中的指令都要经过五个stage，多周期处理器的指令只经过它所需要的stage。

## Pipeline Control

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210623224006522.png" alt="image-20210623224006522" style="zoom:50%;" />

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210623224350453.png" alt="image-20210623224350453" style="zoom:50%;" />



## Five stages

IF, ID, EX, MEM, WB

![image-20210620150819602](/Users/yanjieze/Library/Application Support/typora-user-images/image-20210620150819602.png)

右半边黑色表明在读；左半边黑色表明在写。

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210620151029967.png" alt="image-20210620151029967" style="zoom:50%;" />

## Data Path with Control

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210623224821344.png" alt="image-20210623224821344" style="zoom:50%;" />

## 一个例子：lw

1. IF：instruction存入IF/ID。PC+4也要存入IF/ID。
2. ID：把rs，rt，rd存入ID/EX。还有sign extension后的immediate存入ID/EX。PC+4也要存入ID/EX。
3. EX：把rs寄存器和immediate用ALU加起来，再存入EX/MEM。
4. MEM：读取数据，存入MEM/WB。
5. WB：写入register file。由于这一步需要用到rt，rt要一直保存在流水线寄存器中。

## Control Signals

把instruction从IF/ID取出来，在ID阶段获得main control。

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210620153354849.png" alt="image-20210620153354849" style="zoom:50%;" />

## Structure Hazarads

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210620153649570.png" alt="image-20210620153649570" style="zoom:50%;" />

两个指令用到同一个硬件。

处理方法：

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210620153753879.png" alt="image-20210620153753879" style="zoom:50%;" />

## Data Hazards

三种：

- RAR
- WAR
- WAW

三种解决方法：

- stalling
- forwarding
- code scheduling

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210620154652431.png" alt="image-20210620154652431" style="zoom:50%;" />

有时候stalling是不可避免的，因为lw只有在mem阶段才有结果。

## Load-Use Case



## Hazard Detection Unit

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210623231357195.png" alt="image-20210623231357195" style="zoom:50%;" />

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210620162313793.png" alt="image-20210620162313793" style="zoom:50%;" />

## Control Hazard

解决方法：

1. stall两次
2. 在ID就进行比较，再stall一次
3. branch指令下一条指令从Delayed Slot里面取，这样就不用stall了。
4. Predict-not-taken(predict失败要添加flush)

## Most Difficult Exceptions

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210623232247943.png" alt="image-20210623232247943" style="zoom:50%;" />

## Steps to save pipeline state

- Force a trap instruction
- Turn off all writes for the faulting instruction and the following instructions
- After OS receive control of the exception-handling rountine, it immediately saves the PC of the fault instruction.

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210623232424768.png" alt="image-20210623232424768" style="zoom:50%;" />

## Precise vs Imprecise Exceptions

如果pipeline能完成错误指令前的指令并且可以从错误指令重新开始执行，则是precise的。

## Exceptions in MIPS Pipeline

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210620165009192.png" alt="image-20210620165009192" style="zoom:50%;" />

## Handling Multicycle Operations

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210620165748213.png" alt="image-20210620165748213" style="zoom:50%;" />

## Improving Scalar Pipeline

- superscalar pipeline
- superpipeline<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210623233226133.png" alt="image-20210623233226133" style="zoom:50%;" />

# 6 ILP

## Pipeline CPI

Pipeline CPI = Ideal pipeline CPI + Structural Stalls + Data hazard stalls + Control Stalls

Ideal pipeline CPI is the max performance a pipeline can reach.

## Dependency

- Data dependency. 

  1. the results of instruction *i* may be used in instruction *j* 
	2. instruction *j* has data dependence on instruction *k* and *k* has data dependence on *i*

- Name dependency. Two instructions use the same register or memory location but no flow of information

- Control dependency. 

	1. if an instruction depends on a branch then this instruction can not be moved before the  branch so that its execution is no longer controlled by the branch.

  2. if an instruction does not depend on a branch then it can not be moved after the branch so that it is controlled by the branch.

## Data Dependency

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210623234553874.png" alt="image-20210623234553874" style="zoom:50%;" />

## Name Dependency

- Anti dependence: 和数据相关不太一样，两个指令没有数据依赖，但是有顺序的限制。i先写，j再读。
- Output dependence: i先写，j再写。也要保持顺序。

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210623234639402.png" alt="image-20210623234639402" style="zoom:50%;" />

## Control Dependence

被一个branch控制的指令不能移到前面；没有被一个branch控制的指令不能被控制。

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210623235204623.png" alt="image-20210623235204623" style="zoom:50%;" />

## Data Hazard

- RAW:读在写后，要保持指令顺序
- WAW：写后写，要保持指令顺序
- WAR：写在读后，

## Latency of FP operation

FPALUop then FPALUop: 3

FPALUop then store double : 2

Load double then FPALUop: 1

Load double then store double: 0

记忆：load， 1， aluop，3，aluop， 2， store 

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210624003102128.png" alt="image-20210624003102128" style="zoom:50%;" />

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210624003447228.png" alt="image-20210624003447228" style="zoom:50%;" />

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210624003516045.png" alt="image-20210624003516045" style="zoom:50%;" />

## Basic Complier Techniques

- reorder
- loop unrolling

## Reducing Branch Costs with Advanced Branch Prediction

- Static branch prediction
- Dynamic branch prediciton

## Dynamic branch prediction

用一个hash table记录是否跳转。

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210624004040559.png" alt="image-20210624004040559" style="zoom:50%;" />

然后这个table元素状态是否改变，由有限状态机决定。

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210624004138642.png" alt="image-20210624004138642" style="zoom:50%;" />

- 1-bit prediction<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210620174826612.png" alt="image-20210620174826612" style="zoom:50%;" />
- 2-bit prediction<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210620174904776.png" alt="image-20210620174904776" style="zoom:50%;" />

## Out-of-order Execution

Motivation

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210624004330896.png" alt="image-20210624004330896" style="zoom:50%;" />

具体执行：

IDstage的时候：

- 检查是否有结构冒险
- 等待数据冒险的消失



<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210624004358950.png" alt="image-20210624004358950" style="zoom:50%;" />

<img src="/Users/yanjieze/Library/Application Support/typora-user-images/image-20210624004730723.png" alt="image-20210624004730723" style="zoom:50%;" />

## Dynamic Scheduling

Scoreboard Algorithm
