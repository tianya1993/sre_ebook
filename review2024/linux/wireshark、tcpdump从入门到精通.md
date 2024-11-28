wireshark、tcpdump从入门到精通

详解来自 Google 的协议栈测试神器一packetdrill

剖析支撑TCP协议的基石一首部字段

数据包大小对网络的影响-MTU 与MSS的奥秘

深度聊聊端口号


三次握手、四次挥手背后的细节一半连接队列、全连接队列

冷知识一什么是TCP的自连接

实战模拟-TCP的 11种状态变迁

实战模拟-SYNFlood攻击原理



三次握手太慢一来看看快速打开



一台主机上两个进程可以同时监听同一个端口吗一聊聊惊群效应

当多个进程监听同一个端口时，如果有一个新的连接请求到来，所有监听的进程都会被唤醒，但只有一个进程能够成功处理这个连接请求，其他进程则会重新进入休眠状态。这种现象称为“惊群效应”，会导致CPU资源的浪费和锁竞争的开销‌12。



可以 例如nginx的 work 进程



优雅关闭连接-SO LINGER

不得不聊的TIME_WAIT

2MLS  



- 客户端特有的状态：SYN_SENT、FIN_WAIT_1、FIN_WAIT_2、CLOSING、TIME_WAIT 。
- 服务端特有的状态：LISTEN、SYN_RCVD、CLOSE_WAIT、LAST_ACK 。
- 共有的状态：CLOSED、ESTABLISHED 



![img](https://images2015.cnblogs.com/blog/593627/201509/593627-20150929184604886-1163609285.png)



Timiestate  

RST 包出现的原因与分析、RST 攻击

TCP与重传

深度剖析 TCP 滑动窗口

深度剖析TCP拥塞控制算法

详聊网络编程中Keep-Alive机制

UDP 协议入门

HTTP协议入门到精通

HTTP2.0协议详解

HTTP3.0协议详解

详解 websocket 协议

容器网络原理-veth机制、bridge机制、NAT与iptables

剖析DNS协议

流媒体技术:直播用到的协议一览

select/epoll 的底层原理

真正搞懂网络I/O模型

HTTP、TLS/SSL协议

