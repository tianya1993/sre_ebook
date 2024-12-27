grep sed awk cut 组合使用☆

http 错误码和原因

长连接、短连接、WebSocket 区别和使用场景

nginx 性能优化有哪些方式☆

lvs、nginx、haproxy 区别和使用场景☆

僵尸进程是什么

进程、线程、协程区别☆

什么是 nginx 的异步非阻塞

linux 网络丢包怎么排查☆

常用的性能分析诊断命令☆

什么是进程中断

什么是软中断、硬中断

什么是不可中断进程

什么是栈内存和堆内存

top 命令里面可以看到进程哪些状态☆

Linux 系统中 /proc 是做什么的

load 和 cpu 使用率区别

MAC 地址 IP 地址如何转换

常见的 raid 有哪些，使用场景是什么

lvm 怎么划分

jvm 内存如何查看

如何管理和优化内核参数

什么是进程最大数、最大线程数、进程打开的文件数，怎么调整☆

du 和 df 统计不一致原因☆

buffers 与 cached 的区别☆

lsof 命令使用场景

Linux 中的进程间通信的方式及其使用场景

Linux 中的进程优先级与设置方法

什么是内存分页和分段

如何创建和管理自定义 systemd 服务

Linux 内核模块的加载与卸载过程

ansible roles 使用场景，现在有多台机器需要批量加入 k8s 集群，怎么实现☆

## **Kubernetes**

---

谈谈你对 k8s 的理解☆

k8s 集群架构是什么☆

简述 Pod 创建过程☆

简述删除一个 Pod 流程

不同 node 上的 Pod 之间的通信过程☆

pod 创建 Pending 状态的原因☆

deployment 和 statefulset 区别☆

kube-proxy 有什么作用☆

kube-proxy 怎么修改 ipvs 规则

ipvs 为什么比 iptables 效率高

pod 之间访问不通怎么排查☆

k8s 中 Network Policy 的实现原理

探针有哪些？探测方法有哪些？

pod 健康检查失败可能的原因和排查思路

k8s 的 Service 是什么☆

metrics-server 采集指标数据链路

k8s 服务发现有哪些方式？

pod 几种常用状态

Pod 生命周期的钩子函数

Calico 和 flannel 区别☆

calico 网络原理、组网方式

Network Policy 使用场景

kubectl exec 实现的原理

cgroup 中限制 CPU 的方式有哪些

kubeconfig 存放内容

pod DNS 解析流程☆

traefik 对比 nginx ingress 优点

Harbor 有哪些组件

Harbor 高可用怎么实现

ETCD 调优

假设 k8s 集群规模上千，需要注意的问题有哪些？

节点 NotReady 可能的原因？会导致哪些问题？☆

service 和 endpoints 是如何关联的？

ReplicaSet、Deployment 功能是怎么实现的？

scheduler 调度流程

HPA 怎么实现的☆

request limit 底层是怎么限制的☆

helm 工作原理是什么？

helm chart rollback 实现过程是什么？

velero 备份与恢复流程是什么

docker 网络模式

docker 和 container 区别☆

如何减⼩dockerfile⽣成镜像体积？

k8s 日志采集方案

Pause 容器的用途☆

k8s 证书过期怎么更新

K8S QoS 等级☆

k8s 节点维护注意事项

Headless Service 和 ClusterIP 区别☆

Linux 容器技术的基础原理

Kubernetes Pod 的常见调度方式

kubernetes Ingress 原理☆

Kubernetes 各模块如何与 API Server 通信

kubelet 监控 worker 节点如何实现

容器时区不一致如何解决？

## **Prometheus**

---

Prometheus 的工作流程

Metric 的几种类型？分别是什么？☆

Prometheus 有哪几种服务发现☆

Prometheus 常用函数

thanos 架构☆

thanos 与 VictoriaMetrics 对比

thanos sidecar 和 receive 区别☆

thanos rule 组件和 prometheus 区别

Prometheus 告警从触发到收到通知延迟在哪

告警抑制怎么做☆

告警架构高可用怎么做☆

Pod 指标 WSS 和 RSS 区别☆

监控四个黄金指标

在大规模环境下，如何优化 Prometheus 性能

如何实现告警的自动化响应☆

Prometheus 数据压缩和持久化实现原理

kubectl top 输出与 Linux free 命令不一致原因☆

用到了哪些 exporter，功能是什么

是否自己开发过 exporter☆

target down 的情况如何进行故障排除？

Exporter 停止工作，如何监控？

Prometheus 的拉取模式与 zabbix 推送模式有何区别？各有什么优缺点？

Prometheus operator 怎么添加 targets 和告警规则

k8s 集群外 exporter 怎么使用 Prometheus 监控

## **ELK**

---

ES 写入索引原理

ES 存储原理☆

搜索文档（单个文档）流程

ES 全文搜索流程

ES 写入性能优化☆

ES 查询性能优化☆

ES JVM 使用过高如何排查

ES 的 Fleet server 架构☆

Fleet server 架构和 elk 架构使用场景☆

ClickHouse、loki、ES 的优劣对比

ES 架构☆

业务类 ES 和日志类 ES 架构设计区别

ES Full Gc 怎么排查处理

全文检索和精确搜索区别☆

集群变黄状态时，你会如何进行故障排除☆

如何在集群中添加或移除节点

ES Young GC 和 old GC 有什么区别

怎么提高查询结果评分

ES 的 version 是解决什么问题的

查询数据慢如何排查优化☆

是否对 ES JVM 做过调优

ES 是否数据越多需要内存越大

ES 集群数据备份如何实现☆

ES 聚合有哪些方式

Filebeat 如何保证连续发送日志

Logstash 如何提升性能☆

如何提高 Filebeat 性能

Filebeat 如何收集容器日志

## **Devops**

---

gitlab runner 做了哪些优化

怎么实现多集群逐个发布

蓝绿部署、灰度发布、金丝雀发布区别☆

什么是测试左移？（Shift-Left testing）

什么是 GitOps

GitOps 和 DevOps 区别☆

gitlab 仓库代码如何备份

Jenkins 构建失败时，你如何排查问题☆

Jenkins 用户权限管理怎么做的

Jenkins pipeline 有几种模式，区别是什么？

如何配置 Jenkins 实现高可用性

Jenkins Master 和 Slave 是如何协同工作的

如何设计和实现一个 Jenkins Pipeline，以支持多阶段构建、测试和部署流程

Argo Rollouts 蓝绿部署和金丝雀发布原理☆

Argo CD 中的 Application CRD 是什么

Argo CD 中自动同步（Auto-sync）和手动同步的区别与应用场景

Argo CD 检测到应用状态异常，你会如何进行故障排除

Argo CD 如何配置自定义的健康检查规则

Argo CD 检测到配置与实际状态不一致时如何处理这些差异

CICD 流程如何监控？

平时开发项目时 git 开发功能分支标准流程是什么？

git 分支冲突怎么解决？

## **Python VUE**

---

Python 中的 GIL 是什么？它如何影响多线程？☆

python 装饰器☆

is 和 == 的区别☆

Python 中的生成器和迭代器有什么区别

Python 的垃圾回收机制是如何工作的

Python 上下文管理器的概念及其用途。

dict 的内部实现原理

python 浅拷贝和深拷贝☆

lambda 匿名函数使用场景举例

常见设计模式

python 单例模式

面向对象中__new__和__init__区别☆

Python 中的列表和字典是如何实现的？它们在时间复杂度上有何差异？

Python 中的多线程模块的区别☆

asyncio 编写异步代码

django 请求的生命周期☆

JWT 认证

什么是 wsgi，uwsgi

Django 安全防护

drf 继承过哪些视图类，他们之间的区别☆

谈谈 django flask fastapi 各自的优劣和适用场景。

python 定时任务解决方案☆

在 Celery 中，如何确保任务的可靠性和持久性

如何监控 Celery 任务的执行情况

当 Celery 任务出现阻塞或延迟时，你如何进行故障排除？

VUE 双向数据绑定

VUE 实例的生命周期钩子函数有哪些☆

v-if 与 v-show 区别☆

cookie 和 seesion 区别☆

VUE 父子组件如何通信

nextTick 使用场景

ref 和 reactive 区别

你有写过 VUE 自定义指令吗？

排序算法☆

查找算法☆

SSO 单点登录实现原理☆

## **开放性问题**

---

谈谈你对 SRE 理念的理解☆

什么是可观测性

你们当前的业务规模☆

运维过程中遇到的最大的故障是什么？怎么解决的？☆

有没有人为误操作导致故障，如何处理的？☆

平时怎么去学习新的技术☆

最近工作中做过最有意义的事☆

最近研究的技术方向是什么

运维上线流程规范

运维体系建设包含哪些方面☆

故障事件管控怎么设计

告警覆盖率和准确率怎么衡量☆

如何建设运维保障体系

运维给公司带来的价值是什么

运维和其他团队的职能边界和合作模式是什么

运维的发展方向是什么☆

运维的工作重点是什么

运维的工作效率如何提升

是否做过故障总结，包含哪些内容

如何看待自动化操作高效性和人工操作确认安全性的问题

如何看待运维维稳和开发求新的问题☆

如何看待追求更多的可靠性和成本的平衡问题

如何看待追求稳定性和新技术方案实践的问题

如何看待运维工作中的重复性、没有持续价值的工作☆

如何避免告警通知频繁导致成为告警噪声☆

是否关注过资源使用率，考虑降低成本☆

CMDB 数据库怎么设计

SLO 是多少，运维自动化率多少

与上级意见不一致怎么办

你的优点和缺点分别是什么？

与其他候选人相比，你的核心竞争力是什么？

部分用户访问服务首页白屏超时，分析服务请求过程和可能的原因

线上一个服务响应很慢，你如何排查，排查流程是什么？

你们的告警监控体系怎么设计的？
