# Linux 内核网络协议栈

## 1.1 数据报文信息的封装

![1733556736520](image/Linux_network_stack/1733556736520.png)
![1733557418366](image/Linux_network_stack/1733557418366.png)

## 1.2 内核协议栈分层架构

![1733556035065](image/Linux_network_stack/1733556035065.png)
![1733557469278](image/Linux_network_stack/1733557469278.png)

## 1.3 协议栈初始化过程

## 1.4 协议栈接收 / 发送包的流程

![1733557553671](image/Linux_network_stack/1733557553671.png)

**内核收包的路径**

1. 数据帧从外包网络到达网卡
2. 网卡把帧 DMA （Direct Memory Access 直接内存访问） 到内存 （不需要 CPU 的参与）
3. 硬中断通知 CPU
4. CPU 响应硬中断，简单处理后发起软中断（Linux 中断处理函数的上半部分和下半部分）简单处理快速释放 CPU 避免影响 CPU 响应其他设备
5. ksoftirqd 线程处理软中断 调用网卡驱动注册的 epoll 函数处理数据包
6. 帧被从 RingBuffer 上摘下来保存为 1 个 skb
7. 协议层开始处理网络帧，处理完后的数据 data 放到 socket 的接收队列中
8. 内核唤醒用户进程处理

```dotnetcli

# 查看当前值
sysctl net.ipv4.tcp_tw_reuse

# 设置为 1 以启用重用
sudo sysctl -w net.ipv4.tcp_tw_reuse=1

```

tcp_tw_recycle 是一个已被废弃的参数，因其在 NAT 环境中的不兼容性问题而不再推荐使用。
tcp_tw_reuse 仍然有效，并允许在某些条件下重用 TIME_WAIT 状态的连接，以提高连接效率。

定义：tcp_tw_recycle 是一个已被废弃的参数，旨在允许快速回收处于 TIME_WAIT 状态的 TCP 连接。启用后，内核会在收到新的 SYN 请求时，快速重用处于 TIME_WAIT 状态的连接。
影响：
此功能可以减少 TIME_WAIT 状态连接的数量，从而提高服务器的并发连接能力。
但是，tcp_tw_recycle 存在一些问题，特别是在 NAT 环境中。它会导致连接不稳定，因为该功能依赖于时间戳来识别连接。
废弃：由于其潜在的兼容性问题和引发的错误，tcp_tw_recycle 在 Linux 4.12 版本中被废弃。 因其在 NAT 环境中的不兼容性问题而不再推荐使用。
