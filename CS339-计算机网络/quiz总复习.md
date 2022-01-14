# 计算机网络 小测(quiz)复习

整理者：Yanjie Ze

开始日期：2022.1.12

考试日期：2022.1.14



# Chapter 1 Introduction

1. Lower layers can change implementation without affecting upper layers as long as the interface between layers remains the same. (T)

2. **Computer Network is collection of autonomous computers interconnected by a single technology where single technology means protocol layering. (F)**

3. LAN and WAN only differs in the network scale. (F)

   解释：LAN一般连接在同一个地方、同一个建筑里的设备，WAN可以跨地区。

4. The end-to-end delay of 10 pipelining packets equals sum of the end-to-end delay of each packet. (F)

5. TDM is suitable for Circuit switching, whereas ATDM is for packet switching (with packet scheduling in router input/output port queuing) (T)

6. Protocol layering gains a lot and loses nothing. (F)

7. Given a 3kHz telephone line with signal-to-noise ratio of 30 dB, the maximum capacity is approximately 30kbps. (T)

   

8. **Layers four and five of the Internet protocol stack are implemented in the end systems but not in the routers in the network core. (T)**

   解释：第四层和第五层是transport layer和application layer，都只在end host里实现。

9. The capacity of a channel is only constrained by its physical bandwidth. (F)

10. A protocol is always implemented in software. (F)



# Chapter 2 Application Layer

1. Consider an HTTP Web server using persistent connections. Suppose the server spawns a separate process for each client that connects to the server. Then each of these spawned processes will have different server port numbers. (F)

2.  Applications using UDP service are always unreliable. (F)

   不一定，如果上层是reliable的应该就可以吧

3. Since HTTP is stateless, it cannot offer personalized services for different users. (F)

   不对，可以用cookie。

4. FTP is out of band, as it uses separate channels to send control and data messages. (T)

5. Email uses push protocols. (F)

   不对，both push and pull。

6. Unlike UDP, TCP can provide a throughput guarantee. (F)

   不能保证吧，因为reliable data transfer，flow control，congestion control。

7. DNS can offer load balancing service. (T)

   因为DNS server收到很多请求的时候，会把请求转给其他server。

8. HTTP always runs on top of TCP. (F)

   也可以用UDP？

9. In the client-server model, if a server fails, its clients should always be notified. (F)

   也可以不notify咯

10. On the same server, two sockets can bind to the same port. (F)

    不能，但是可以在accept的时候同时生成两个socket对应一个port



甚至还有问答题：

1. What is UDP hole punching?

   用来穿过NAT的。

2. What happens when you ping some IP?

3. What is ARP storm?

   ARP，address resolution protocol，请求IP地址的对应mac地址，所以需要broadcast

4. **How to emulate a router in Mininet?**

5. **Can Mininet emulate a high-speed network?**

6. **How does Mininet emulate a host?**

7. **How does Mininet emulate link delay/bandwidth/packet loss?**



# Chapter 3 Application Layer

1. Suppose that the last SampleRTT in a TCP connection is equal to 1 sec. Then timeout for the connection will necessarily be set to a value >= 1 sec. (T)

   对的，因为time out的时间要至少大于等于RTT的时间，实际上time out value = RTT + 4D。

2. Except for packet loss, network congestion can also cause the timer time-out. (T)

3. The timer is used to detect packet loss. Duplicate acks can be caused by setting the timer too long. (T)

   是的，receiver可能在time out之前发多个ack，但是sender还在等待。

4. Sequence number space is the bigger the better. (F)

   不能，seq#更大会让header更大的。

5. Suppose that host A wants to send data over TCP to host B, and host B wants to send data to host A over TCP. Two separate TCP connections - one for each direction - are needed. (F)

   不需要吧，好像是双向的

6. TCP will crowd out UDP when congestion occurs. (F)

   UDP是有包就发，所以会crowd out TCP

7. Fair sharing network bandwidth reduces average TCP flow completion time. (F)

   增加？

8. Using sequence numbers can help handle duplicated acks in rdt2.1. (T)

   对的，这就是rdt2.2啊

9. Rdt2.1 cannot be used in practical network systems, as it cannot handle packet loss. In this sense, Rdt3.0 is always better. (F)

   不是always

10. Error correction code is always prefered to error detection code. (F)

    不是always。

    Detection VS Correction：

    - detection+重传在error not expected的时候用，在有burst error的时候用，在重传的损耗不是很大的时候用
    - correction相反。



# Chapter 4 Network Layer

1. **CIDR could be used for any contiguous IP network to aggregate route entries. (F)**

   不对，需要前缀的后缀能合并

2. NAT uses port number to multiplex IP address, therefore violates the independence layering principle. (T)

   对的

3. LSR advertise smaller LS messages, so it is better than DVR for large network. (F)

   DVR是局部的，对于大网络来说应该更好

4. For an IP address, routers in different level can have different masks for it. E.g., the IP prefix 59.78.0.0/16 is divided into 8 subnets, and then the subnet 59.78.32.0/19 is further divided into 4 subnets. The entries of hierarchical routing table for the IP address 59.78.46.80 are: 59.78.0.0/16, 59.78.32.0/19, 59.78.40.0/21. (T)

5. IPv6 is more efficient than IPv4 because IPv6 header is smaller than IPv4 header. (F)

   错的，IPv4: **20+ Byte**header         IPv6: **40 byte**header

6. Within block of IP addresses 202.120.50.0~202.120.63.255, 202.120.50.0~202.120.53.0 could be assigned to a company in need of 1020 IP addresses. (F)

7. Intra-AS and inter-AS routing algorithms have different routing policies. (T)

8. OSPF uses LSR and Hierarchical Routing to find the least-cost path, whereas BGP uses DVR, together with local policies, to find a good path instead of best path, with explicit AS path to avoid count-to-infinity problem. (T)

9. LSR collects global topology information whereas DVR only collects local information, so LSR has no convergence problem. (F)

   不对，有震荡。

10. Internet uses packet switching for the routers to store and forward the packets. The router's buffer is usually designed big enough to store the incoming packets, but when network congestion happens, the buffer can be full and the packets can be dropped and lost. (T)

    蛮对的

11. Internet uses Hierarchical Routing to save routing table size and reduce update traffic. (T)

    蛮对的

12. Tracert uses ICMP to get "TTL expired" error-reporting message from each hop to extract their IP addresses and evaluate the RTT. (T)

    蛮对的

13. IP service is simple and unreliable, complicated features are implemented in the end hosts. This conforms to the End-to-End Principle. (T)

    蛮对的

14. CIDR is designed to deal with the shortage of IPv4 addresses, whereas VLSM is designed to solve the problem of routing table explosion. (F)

    好像反了

15. Most routers in Internet support broadcast/multicast routing. (F)

    Router不应该支持broadcast，这应该是在子网里做的。



# Chapter 5 Link Layer

1. If we can guarantee reliable data transfer at the link layer, then the end-to-end reliability can be also guaranteed. (F)

   上面的层也有可能不可靠

2. Suppose the following bit string is received by the data link layer from the network layer: 01110111101111101111110. Then the resulting string after bit stuffing is 0111011110111110011111010. (T)

   遇到5个1就加0

3. Since CSMA performs carrier sensing before data transfer, the possibility of packet collision becomes smaller. That is why CSMA attains higher throughout than ALOHA. (T)

4. A full-duplex point-to-point ethernet link does not require CSMA/CD. (T)

   没有碰撞了都

5. Given two hosts A and B. A's IP is 111.111.111.111/24, and B's IP is 222.222.222.222/24. Suppose that A's ARP table is empty at the beginning. If A wants to talk to B, A needs to generate an ARP request first to acquire B's MAC address. (F)

6. Compared with a hub, a switch can reduce a LAN's collision region. (T)

   是的，link layer层面

7. If we divide a switch into two VLANs, then the two VLANs need to connect to a router in order to communicate. (T)

   是的

8. L2 switches are plug and play, using self-learning to construct switch tables. In contrast, L3 switches require manual configuration. (T)

   是的

9. We should avoid building network topologies with cycles, because of the ARP storm. (F)

   不会的，可以RPF来阻止ARP Storm。

10. The MAC layer is always implemented in NIC, while the transport layer is always implemented in software. (F)

    always是不对的，但是有反例吗？

# Chapter 6 WIFI

1. The mac and physical layer characteristics of a wireless network should not affect the design of transport layer and application layer protocols. (F)

2. Different modulation schemes give different throughput. For example, the throughput of QAM16 is 4 times the throughput of BPSK. Hence, we should always prefer QAM16 to BPSK in wireless communication. (F)

   这两个啥玩意？好像没讲

3. The exposed terminal problem could reduce the wireless network throughput. (T)

4. The RTS-CTS scheme allows senders to reserve channels and avoid collisions of data frames. Hence, enabling RTS-CTS will improve network throughput. (F)

   不一定improve，如果packet比较小的话overhead也比较大

5. When a mobile node moves to a foreign network, one addressing approach is to let the foreign network advertise to all other networks that the mobile node is resident in its network. Compared to this approach, the IP-in-IP tunneling approach is easier to support millions of mobile nodes. (T)

   
