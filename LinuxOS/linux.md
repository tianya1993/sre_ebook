# Linux 

## Namespace
- UTS   主机名 域名
- Mount  文件系统
- Network 网络协议栈
- User 用户隔离
- PID 进程号
- IPC 进程通信

## Cgroup
 有V1和V2版本的区别，主要是层级结构的变化

 CPU
    cpuset   绑定核心
    cpu.shares  1024 根据比例分配CPU
    cpu.cfs_period_us 100000us 100ms
    cpu.cfs_quota_us 

 Memory 
   max limit 

 IO  


## CPU的四种进程调度




## Linux的进程调度
-  CFS（Completely Fair Scheduler）
 是 Linux 内核中的默认进程调度器。它主要用于公平地分配 CPU 时间给各个进程，确保所有进程在 CPU 时间的使用上尽可能公平。

CFS 的主要特点
- 公平性：
CFS 的设计目标是确保所有进程都能公平地获得 CPU 时间。每个进程根据其优先级和 CPU 使用情况被分配时间片。
- 时间片：
CFS 不使用固定的时间片，而是根据进程的权重（优先级）动态计算每个进程应该获得的 CPU 时间。高优先级的进程会获得更多的 CPU 时间。
- 红黑树：
CFS 使用红黑树数据结构来管理可运行的进程。每个进程在树中的位置根据其“虚拟运行时间”（vruntime）来决定。vruntime 是进程实际运行时间与其权重的比值，权重越高，vruntime 增加得越慢。
- 上下文切换：
CFS 尽量减少上下文切换的成本，通过选择 vruntime 最小的进程来进行调度，从而实现低延迟和高吞吐量。
- 优先级：
CFS 支持动态优先级调整。进程在 CPU 上运行的时间越长，其优先级（nice 值）就会逐渐降低，反之亦然，这样可以避免某些进程长期占用 CPU。
配置 CFS 调度器
1. 查看当前调度策略
您可以使用 ps 命令查看当前进程的调度策略：
```bash
ps -eo pid,comm,cls,nice
其中，cls 列显示调度策略，CFS 使用的调度策略是 SCHED_OTHER。
```


1. 修改进程的优先级
您可以使用 nice 和 renice 命令来调整进程的优先级：

使用 nice 创建新进程时设置优先级：
```dotnetcli
nice -n 10 ./your_program
```
使用 renice 修改运行中进程的优先级：
```dotnetcli
renice -n 10 -p <pid>

```
### CFS 的调度过程
进程进入就绪队列：
当进程准备好运行时，它会进入就绪队列，并根据其 vruntime 进行排序。
选择进程：
CFS 从就绪队列中选择 vruntime 最小的进程进行调度。
时间片管理：
被调度的进程会运行，直到它的时间片用完、被更高优先级的进程抢占，或自愿放弃 CPU。
上下文切换：
当需要调度其他进程时，CFS 会进行上下文切换，将当前进程的状态保存到内存，并加载下一个进程的状态。
总结
CFS 通过使用 vruntime 和红黑树数据结构实现了公平、高效的 CPU 调度。它支持动态优先级调整，可确保所有进程都能获得合理的 CPU 时间。了解 CFS 的工作原理和配置方法可以帮助您更好地管理系统性能和资源使用

