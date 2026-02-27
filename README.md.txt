# 高可用 Kubernetes 集群部署（Rocky Linux 9.7 + Containerd + Calico + Prometheus + Loki）

本项目详细记录了在 VMware 虚拟机环境下，使用三台 Master、一台 Worker 搭建高可用 Kubernetes 集群的全过程。集群采用 Keepalived + HAProxy 实现 API Server 负载均衡，Containerd 作为容器运行时，并集成了 Prometheus 监控和 Loki 日志系统。

## 环境信息
- 操作系统：Rocky Linux 9.7
- Kubernetes 版本：v1.35
- Containerd 版本：v2.2.1
- 网络插件：Calico v3.26
- 负载均衡：HAProxy + Keepalived
- 虚拟 IP（VIP）：192.168.10.100
- 节点规划：
  - master1: 192.168.10.11
  - master2: 192.168.10.12
  - master3: 192.168.10.13
  - worker1: 192.168.10.14
- 网关：192.168.10.2

## 快速开始
1. 阅读 [环境准备](docs/environment.md) 文档，完成所有节点的基础配置。
2. 按照 [安装 Containerd](docs/installation.md#二安装containerd) 部分安装容器运行时。
3. 根据 [安装 Kubernetes 组件](docs/installation.md#三安装kubernetes组件) 安装 kubeadm/kubelet/kubectl。
4. 配置 [HAProxy 和 Keepalived](docs/installation.md#四配置高可用组件master节点)。
5. 在 master1 上执行 [初始化集群](docs/installation.md#五初始化kubernetes集群仅在master1执行)。
6. 参考 [添加其他节点](docs/add-nodes.md) 将 master2、master3 和 worker1 加入集群。
7. 部署 [Prometheus 监控](docs/monitoring.md) 和 [Loki 日志系统](docs/logging.md)。

## 目录说明
- `docs/`：详细部署文档
- `configs/`：所有组件的配置文件
- `scripts/`：自动化部署脚本（按编号顺序执行）
- `history/`：操作命令历史记录

## 许可证
MIT