# 08. 虚拟化 (Virtualization)

## 虚拟化 (Virtualization)

### Ballooning / 气球技术
- **中文**：气球技术
- **定义**：动态调整虚拟机内存使用的技术
- **说明**：Hypervisor 在 Guest OS 内安装气球驱动（Balloon Driver），通过"充气"（分配内存）和"放气"（释放内存）调整 VM 内存；实现内存超配
- **相关**：Memory Overcommitment（内存超配）、Virtual Machine（虚拟机）

### Binary Translation / 二进制翻译
- **中文**：二进制翻译
- **定义**：在运行时将 Guest OS 的敏感指令翻译为安全指令的技术
- **说明**：二进制翻译是全虚拟化早期使用的技术（如 VMware）；有硬件辅助虚拟化后较少使用
- **相关**：Full Virtualization（全虚拟化）、Trap-and-Emulate（陷入模拟）

### Full Virtualization / 全虚拟化
- **中文**：全虚拟化
- **定义**：虚拟机完全模拟物理硬件，Guest OS 无需修改即可运行
- **说明**：全虚拟化使用二进制翻译（Binary Translation）或硬件辅助虚拟化处理特权指令；代表：VMware ESXi、VirtualBox、KVM
- **相关**：Paravirtualization（半虚拟化）、Hardware-Assisted Virtualization（硬件辅助虚拟化）

### Guest OS / 客户操作系统
- **中文**：客户操作系统
- **定义**：运行在虚拟机中的操作系统
- **说明**：Guest OS 不知道自己运行在虚拟机上；可以是 Windows、Linux 等任意操作系统
- **相关**：Host OS（宿主操作系统）、Virtual Machine（虚拟机）

### Hardware-Assisted Virtualization / 硬件辅助虚拟化
- **中文**：硬件辅助虚拟化
- **定义**：CPU 提供专门的虚拟化扩展指令，加速虚拟化操作
- **说明**：Intel VT-x（Virtualization Technology）和 AMD-V（AMD Virtualization）提供硬件虚拟化支持；包括 VMX root/non-root 模式、EPT（扩展页表）等
- **相关**：Intel VT-x、AMD-V、Virtualization（虚拟化）

### Host OS / 宿主操作系统
- **中文**：宿主操作系统
- **定义**：直接运行在物理硬件上的操作系统，管理虚拟机
- **说明**：在 Type 2 Hypervisor 中，Host OS 是普通操作系统（如 Windows、Linux），Hypervisor 作为应用程序运行
- **相关**：Guest OS（客户操作系统）、Hypervisor（虚拟机监控器）

### Hypercall / 超级调用
- **发音**：/ˈhaɪpərkɔːl/
- **中文**：超级调用
- **定义**：半虚拟化中 Guest OS 向 Hypervisor 请求服务的接口
- **说明**：Hypercall 类似系统调用，但调用对象是 Hypervisor 而非操作系统；比陷入模拟性能更好
- **相关**：Paravirtualization（半虚拟化）、System Call（系统调用）

### Hypervisor / 虚拟机监控器
- **音标**：/ˈhaɪpərvaɪzər/
- **中文**：虚拟机监控器（Hypervisor）
- **定义**：创建和管理虚拟机的软件或固件层
- **说明**：Hypervisor 分为 Type 1（裸机型，直接运行在硬件上，如 VMware ESXi、Xen、Hyper-V）和 Type 2（宿主型，运行在操作系统上，如 VMware Workstation、VirtualBox）
- **同义词**：Virtual Machine Monitor (VMM)
- **相关**：Virtual Machine（虚拟机）、Virtualization（虚拟化）

### Live Migration / 实时迁移
- **中文**：实时迁移
- **定义**：在不中断虚拟机运行的情况下，将虚拟机从一个物理主机迁移到另一个
- **说明**：实时迁移需要共享存储（或存储迁移配合）；先拷贝内存，最后同步差异并切换；用户几乎无感知
- **同义词**：vMotion（VMware 术语）
- **相关**：Virtual Machine（虚拟机）、Hypervisor（虚拟机监控器）

### Memory Overcommitment / 内存超配
- **中文**：内存超配
- **定义**：分配给虚拟机的内存总量超过物理内存总量的配置
- **说明**：内存超配基于假设：不是所有 VM 同时使用所有内存；通过气球技术和交换实现；如果所有 VM 同时使用分配的内存，会导致性能严重下降
- **相关**：Ballooning（气球技术）、Virtual Machine（虚拟机）

### Oversubscription / 超配
- **中文**：超配
- **定义**：分配的虚拟资源总量超过物理资源总量的配置
- **说明**：如物理机有 8 核 CPU，但分配给 VM 的 vCPU 总数为 16；超配提高资源利用率，但可能导致性能下降
- **相关**：Virtual Machine（虚拟机）、Resource Allocation（资源分配）

### Paravirtualization / 半虚拟化
- **音标**：/ˌpærəˌvɜːrtʃuələˈzeɪʃn/
- **中文**：半虚拟化
- **定义**：Guest OS 需要修改以调用 Hypervisor 提供的特殊接口（Hypercall）
- **说明**：半虚拟化性能高，因为避免了特权指令的模拟；但需要修改 Guest OS；代表：Xen（早期）、VMware ESXi（部分）
- **相关**：Full Virtualization（全虚拟化）、Hypercall（超级调用）

### Template / 模板
- **音标**：/ˈtempleɪt/
- **中文**：模板
- **定义**：预配置的虚拟机镜像，用于快速创建新虚拟机
- **说明**：模板包含操作系统、应用程序、配置；从模板创建 VM 比全新安装快得多；常用于虚拟桌面和云环境
- **相关**：Clone（克隆）、Virtual Machine（虚拟机）

### Thick Provisioning / 厚配置
- **中文**：厚配置
- **定义**：为虚拟机预先分配所有存储空间
- **说明**：厚配置的虚拟磁盘创建时就占用全部空间；性能略好，但存储利用率低；分为厚置备延迟清零（zeroedthick）和厚置备置零（eagerzeroedthick）
- **相关**：Thin Provisioning（精简配置）、Virtual Disk（虚拟磁盘）

### Thin Provisioning / 精简配置
- **中文**：精简配置
- **定义**：为虚拟机分配逻辑上大于实际物理存储的存储空间
- **说明**：精简配置的虚拟磁盘初始占用空间小，随数据写入增长；提高存储利用率；但需要注意物理存储不足的风险
- **相关**：Thick Provisioning（厚配置）、Virtual Disk（虚拟磁盘）

### Trap-and-Emulate / 陷入模拟
- **中文**：陷入模拟
- **定义**：Guest OS 执行特权指令时触发陷入，Hypervisor 模拟该指令的执行
- **说明**：Trap-and-Emulate 是全虚拟化的基本机制；硬件辅助虚拟化优化了陷入模拟的开销
- **相关**：Full Virtualization（全虚拟化）、Binary Translation（二进制翻译）

### Type 1 Hypervisor / 裸机型虚拟机监控器
- **中文**：裸机型虚拟机监控器
- **定义**：直接运行在物理硬件上的 Hypervisor
- **说明**：Type 1 性能高、开销小、安全性好；代表：VMware ESXi、Microsoft Hyper-V、Citrix XenServer、Linux KVM（严格说 KVM 是内核模块）
- **同义词**：Bare-Metal Hypervisor、Native Hypervisor
- **相关**：Type 2 Hypervisor、Virtual Machine（虚拟机）

### Type 2 Hypervisor / 宿主型虚拟机监控器
- **中文**：宿主型虚拟机监控器
- **定义**：运行在宿主操作系统上的 Hypervisor
- **说明**：Type 2 易于安装和使用，但性能较低；代表：VMware Workstation/Fusion、Oracle VirtualBox、Parallels Desktop
- **同义词**：Hosted Hypervisor
- **相关**：Type 1 Hypervisor、Host OS（宿主操作系统）

### Virtual CPU (vCPU) / 虚拟 CPU
- **中文**：虚拟 CPU
- **定义**：分配给虚拟机的逻辑 CPU
- **说明**：一个物理 CPU 核心可以支持多个 vCPU；vCPU 可以绑定到物理 CPU（CPU Pinning）或由 Hypervisor 动态调度
- **相关**：Virtual Machine（虚拟机）、CPU Pinning（CPU 绑定）

### Virtual Disk / 虚拟磁盘
- **中文**：虚拟磁盘
- **定义**：虚拟机使用的磁盘文件，模拟物理磁盘
- **说明**：虚拟磁盘格式包括 VMDK（VMware）、VHD/VHDX（Microsoft）、QCOW2（QEMU/KVM）、RAW 等；可以存储为文件或块设备
- **相关**：Virtual Machine（虚拟机）、Thin Provisioning（精简配置）

### Virtual Machine (VM) / 虚拟机
- **中文**：虚拟机
- **定义**：通过软件模拟的完整计算机系统，运行在物理主机上
- **说明**：虚拟机有自己的操作系统（Guest OS）、虚拟硬件（CPU、内存、磁盘、网卡）；多个 VM 可以在同一物理机上隔离运行
- **相关**：Guest OS（客户操作系统）、Host OS（宿主操作系统）、Hypervisor（虚拟机监控器）

### Virtualization / 虚拟化
- **音标**：/ˌvɜːrtʃuələˈzeɪʃn/
- **中文**：虚拟化
- **定义**：通过软件抽象，将物理资源（CPU、内存、存储、网络）虚拟为多个逻辑资源的技术
- **说明**：虚拟化提高资源利用率、隔离性、灵活性；类型包括服务器虚拟化、存储虚拟化、网络虚拟化、桌面虚拟化等
- **相关**：Virtual Machine（虚拟机）、Hypervisor（虚拟机监控器）、Container（容器）

---

## 容器技术 (Container Technology)

### Capability / 能力
- **音标**：/keɪˈpæbɪləti/
- **中文**：能力
- **定义**：Linux 中将 root 权限细分为多个独立权限的机制
- **说明**：Capability 允许进程拥有部分 root 权限（如 CAP_NET_ADMIN 管理网络、CAP_SYS_ADMIN 系统管理）而非全部；Docker 默认删除大部分 Capability
- **相关**：Seccomp、Container Security（容器安全）、root

### Cgroup (Control Group) / 控制组
- **发音**：/siː-ɡruːp/
- **中文**：控制组
- **定义**：Linux 内核提供的资源限制、统计和隔离机制
- **说明**：Cgroup 限制进程组的 CPU、内存、磁盘 I/O、网络等资源使用；Cgroup v1 和 v2 是两个版本
- **相关**：Namespace（命名空间）、Container（容器）、Resource Limit（资源限制）

### Container / 容器
- **音标**：/kənˈteɪnər/
- **中文**：容器
- **定义**：操作系统级虚拟化技术，共享宿主机内核，提供隔离的用户空间
- **说明**：容器比虚拟机轻量，启动快（秒级），资源开销小；但隔离性不如 VM；代表：Docker、containerd、CRI-O
- **相关**：Docker、Namespace（命名空间）、Cgroup（控制组）、Image（镜像）

### Container Orchestration / 容器编排
- **中文**：容器编排
- **定义**：自动化部署、管理、扩展容器化应用的过程
- **说明**：容器编排处理容器的调度、服务发现、负载均衡、滚动更新、回滚、自动扩缩容等；代表：Kubernetes、Docker Swarm、Apache Mesos
- **相关**：Kubernetes、Docker Swarm、Container（容器）

### Container Runtime / 容器运行时
- **中文**：容器运行时
- **定义**：负责运行容器的底层软件
- **说明**：容器运行时包括：Docker（完整平台）、containerd（轻量级运行时，Docker 底层）、CRI-O（Kubernetes 专用运行时）；通过 CRI（Container Runtime Interface）与 Kubernetes 交互
- **相关**：Container（容器）、Kubernetes、CRI

### CPU Quota / CPU 配额
- **中文**：CPU 配额
- **定义**：Cgroup 中绝对 CPU 使用限制
- **说明**：CPU quota 配合 period 使用；如 quota=100000, period=100000 表示最多使用 1 核 CPU；Docker 的 --cpus 使用 CPU quota
- **相关**：CPU Shares（CPU 份额）、Cgroup（控制组）

### CPU Shares / CPU 份额
- **中文**：CPU 份额
- **定义**：Cgroup 中相对 CPU 分配权重
- **说明**：CPU shares 是相对值（默认 1024）；CPU 紧张时，容器获得的 CPU 比例 = 容器 shares / 总 shares；不限制最大 CPU 使用
- **相关**：CPU Quota（CPU 配额）、Cgroup（控制组）

### Docker
- **发音**：/ˈdɒkər/
- **中文**：Docker
- **定义**：最流行的容器平台，提供容器的构建、分发和运行工具
- **说明**：Docker 使用 Linux Namespace 和 Cgroup 实现容器隔离；Docker Hub 是公共镜像仓库；Dockerfile 定义镜像构建步骤
- **相关**：Container（容器）、Image（镜像）、Dockerfile

### Dockerfile
- **发音**：/ˈdɒkər-faɪl/
- **中文**：Dockerfile
- **定义**：定义 Docker 镜像构建步骤的文本文件
- **说明**：Dockerfile 包含 FROM（基础镜像）、RUN（执行命令）、COPY（复制文件）、CMD（默认命令）等指令
- **相关**：Docker、Image（镜像）、Build（构建）

### Image / 镜像
- **音标**：/ˈɪmɪdʒ/
- **中文**：镜像
- **定义**：容器运行时的只读模板，包含应用程序和依赖
- **说明**：容器镜像分层存储（Layer），使用写时复制；镜像可以从 Dockerfile 构建或从仓库拉取
- **相关**：Container（容器）、Docker、Layer（层）

### Layer / 层
- **音标**：/ˈleɪər/
- **中文**：层
- **定义**：容器镜像的分层存储单元
- **说明**：每层对应 Dockerfile 的一条指令；层是只读的，容器运行时添加可写层；层可以共享和缓存
- **相关**：Image（镜像）、Docker、Union File System（联合文件系统）

### Memory Limit / 内存限制
- **中文**：内存限制
- **定义**：容器可以使用的最大内存量
- **说明**：超过内存限制时，容器中的进程可能被 OOM Killer 杀死；Docker 使用 --memory 设置
- **相关**：OOM Killer、Cgroup（控制组）、Container（容器）

### Namespace / 命名空间
- **音标**：/ˈneɪmspeɪs/
- **中文**：命名空间
- **定义**：Linux 内核提供的资源隔离机制
- **说明**：Namespace 将全局系统资源封装为抽象，使进程只能看到同一命名空间内的资源；类型包括：PID（进程）、Net（网络）、IPC（进程间通信）、Mnt（挂载点）、UTS（主机名）、User（用户）、Cgroup（控制组）、Time（时间）
- **相关**：Cgroup（控制组）、Container（容器）、Isolation（隔离）

### OCI (Open Container Initiative) / 开放容器倡议
- **发音**：/oʊ-siː-aɪ/
- **中文**：开放容器倡议
- **定义**：开放标准组织，定义容器和镜像的标准规范
- **说明**：OCI 规范包括：runtime-spec（运行时规范，如 runc）、image-spec（镜像规范）；确保容器生态的互操作性
- **相关**：runC、Container（容器）

### OverlayFS / 覆盖文件系统
- **中文**：覆盖文件系统
- **定义**：Linux 内核的联合文件系统实现
- **说明**：OverlayFS 将 lowerdir（只读层）和 upperdir（可写层）合并为 merged 目录；Docker 默认使用 OverlayFS
- **相关**：Union File System（联合文件系统）、Docker

### Resource Limit / 资源限制
- **中文**：资源限制
- **定义**：限制容器或进程可以使用的资源量
- **说明**：资源限制包括 CPU 限制（CPU shares、CPU quota）、内存限制（memory limit、swap limit）、磁盘 I/O 限制等
- **相关**：Cgroup（控制组）、Container（容器）

### Seccomp / 安全计算模式
- **发音**：/ˈsɛk-kɒmp/
- **中文**：安全计算模式
- **定义**：Linux 内核的安全机制，限制进程可以使用的系统调用
- **说明**：Seccomp 通过 BPF（Berkeley Packet Filter）过滤系统调用；Docker 默认使用 Seccomp 配置文件限制容器系统调用
- **相关**：Capability（能力）、Container Security（容器安全）

### Union File System / 联合文件系统
- **中文**：联合文件系统
- **定义**：将多个目录合并为单个视图的文件系统
- **说明**：联合文件系统用于容器镜像的分层存储；上层修改不影响下层；实现包括 AUFS、OverlayFS、Devicemapper、Btrfs、ZFS
- **相关**：Layer（层）、Container（容器）、OverlayFS

### User Namespace / 用户命名空间
- **中文**：用户命名空间
- **定义**：隔离用户和组 ID 的命名空间
- **说明**：User Namespace 允许容器内的 root 用户映射到宿主机上的普通用户；提高容器安全性；是容器安全的关键
- **相关**：Namespace（命名空间）、Container（容器）

---

## 容器编排与 Kubernetes (Orchestration & Kubernetes)

### ConfigMap / 配置映射
- **中文**：配置映射
- **定义**：Kubernetes 中存储配置数据的对象
- **说明**：ConfigMap 存储非敏感配置（如环境变量、配置文件），供 Pod 使用；将配置与镜像分离，便于管理
- **相关**：Kubernetes、Secret（密钥）、Pod

### Control Plane / 控制平面
- **中文**：控制平面
- **定义**：Kubernetes 的管理组件集合
- **说明**：控制平面包括：API Server（REST API 入口）、Scheduler（调度器）、Controller Manager（控制器管理器）、etcd（分布式键值存储）
- **相关**：Kubernetes、Master（主节点）、Data Plane（数据平面）

### Data Plane / 数据平面
- **中文**：数据平面
- **定义**：处理应用数据流量的组件集合
- **说明**：数据平面包括：Kubelet（节点代理）、Kube-proxy（网络代理）、Container Runtime（容器运行时）
- **相关**：Control Plane（控制平面）、Kubernetes

### Deployment / 部署
- **中文**：部署
- **定义**：Kubernetes 中管理无状态应用的控制器
- **说明**：Deployment 定义应用的期望状态（副本数、镜像、更新策略），自动创建/更新/删除 ReplicaSet 和 Pod；支持滚动更新和回滚
- **相关**：Kubernetes、Pod、ReplicaSet、Rolling Update（滚动更新）

### etcd
- **发音**：/ˈɛt-siː-diː/
- **中文**：etcd
- **定义**：分布式键值存储，Kubernetes 的后端存储
- **说明**：etcd 使用 Raft 共识算法保证一致性；存储 Kubernetes 的所有配置数据、状态和元数据
- **相关**：Kubernetes、Raft、Distributed Storage（分布式存储）

### Helm
- **发音**：/hɛlm/
- **中文**：Helm
- **定义**：Kubernetes 的包管理工具
- **说明**：Helm 使用 Chart（图表）定义、安装、升级 Kubernetes 应用；Chart 是预配置的 Kubernetes 资源包；Helm Hub 是 Chart 仓库
- **相关**：Kubernetes、Chart（图表）

### Ingress / 入口
- **音标**：/ˈɪnɡres/
- **中文**：入口
- **定义**：Kubernetes 中管理外部访问集群服务的 API 对象
- **说明**：Ingress 提供 HTTP/HTTPS 路由（基于主机名和路径），将外部流量转发到 Service；需要 Ingress Controller（如 Nginx、Traefik）实现
- **相关**：Kubernetes、Service（服务）、Load Balancing（负载均衡）

### Kubernetes (K8s) / Kubernetes
- **发音**：/kuːbərˈnetiːz/ 或 /kuː-bər-ne-tiːz/
- **中文**：Kubernetes（K8s）
- **定义**：最流行的开源容器编排平台
- **说明**：Kubernetes 由 Google 开发（基于 Borg），现由 CNCF 维护；提供 Pod、Service、Deployment、ConfigMap、Secret 等抽象；是云原生应用的事实标准
- **相关**：Pod、Node、Cluster、Container Orchestration（容器编排）

### Microservices / 微服务
- **音标**：/ˈmaɪkroʊsɜːrvɪsɪz/
- **中文**：微服务
- **定义**：将应用拆分为一组小型、独立、可独立部署的服务的架构风格
- **说明**：微服务通过轻量级通信（HTTP/REST、gRPC、消息队列）交互；每个服务独立开发、部署、扩展；容器和 Kubernetes 是微服务的理想运行平台
- **相关**：Monolith（单体）、Service Mesh（服务网格）、Container（容器）

### Node / 节点
- **发音**：/noʊd/
- **中文**：节点
- **定义**：Kubernetes 集群中的工作机器，可以是物理机或虚拟机
- **说明**：Node 上运行 Kubelet（节点代理）和容器运行时（如 Docker、containerd）；Master 节点运行控制平面组件
- **相关**：Kubernetes、Cluster（集群）、Kubelet

### PersistentVolume (PV) / 持久卷
- **中文**：持久卷
- **定义**：Kubernetes 中的存储资源，由管理员配置
- **说明**：PV 是集群中的存储资源（如 NFS、iSCSI、云存储）；独立于 Pod 生命周期；通过 PVC（PersistentVolumeClaim）申请使用
- **相关**：PersistentVolumeClaim（持久卷声明）、Kubernetes、Storage（存储）

### PersistentVolumeClaim (PVC) / 持久卷声明
- **中文**：持久卷声明
- **定义**：用户对存储资源的请求
- **说明**：PVC 请求特定大小和访问模式的存储；Kubernetes 将 PVC 绑定到合适的 PV；Pod 使用 PVC 作为卷
- **相关**：PersistentVolume（持久卷）、Kubernetes、Storage（存储）

### Pod / Pod
- **发音**：/pɒd/
- **中文**：Pod
- **定义**：Kubernetes 中最小的部署单元，包含一个或多个紧密耦合的容器
- **说明**：Pod 中的容器共享网络命名空间（IP 地址）和存储卷；通常一个 Pod 包含一个主容器和若干辅助容器（Sidecar）
- **相关**：Kubernetes、Container（容器）、Sidecar（边车）

### ReplicaSet / 副本集
- **中文**：副本集
- **定义**：Kubernetes 中确保指定数量 Pod 副本运行的控制器
- **说明**：ReplicaSet 根据标签选择器管理 Pod；通常不直接使用，而是由 Deployment 管理
- **相关**：Kubernetes、Pod、Deployment（部署）

### Rolling Update / 滚动更新
- **中文**：滚动更新
- **定义**：逐步替换旧版本 Pod 为新版本的更新策略
- **说明**：滚动更新保证更新过程中服务不中断；可以设置最大不可用数和最大浪涌数；如果更新失败可以回滚
- **相关**：Kubernetes、Deployment（部署）、Rollback（回滚）

### Secret / 密钥
- **音标**：/ˈsiːkrət/
- **中文**：密钥
- **定义**：Kubernetes 中存储敏感数据的对象
- **说明**：Secret 存储密码、令牌、密钥等敏感信息；数据 base64 编码存储（非加密），可以挂载为文件或作为环境变量；etcd 中可以加密存储
- **相关**：Kubernetes、ConfigMap（配置映射）、Pod

### Service Mesh / 服务网格
- **中文**：服务网格
- **定义**：管理微服务间通信的基础设施层
- **说明**：服务网格通过 Sidecar 代理（如 Envoy）拦截服务间流量，提供服务发现、负载均衡、加密、认证、监控、熔断等；代表：Istio、Linkerd、Consul Connect
- **相关**：Microservices（微服务）、Sidecar（边车）、Kubernetes

### Sidecar / 边车
- **音标**：/ˈsaɪdkɑːr/
- **中文**：边车
- **定义**：与主容器同在一个 Pod 中运行的辅助容器
- **说明**：Sidecar 模式用于扩展主容器的功能，如日志收集、监控、代理、配置重载等；Istio 使用 Sidecar 实现服务网格
- **相关**：Pod、Kubernetes、Service Mesh（服务网格）

### StatefulSet / 有状态集
- **中文**：有状态集
- **定义**：Kubernetes 中管理有状态应用的控制器
- **说明**：StatefulSet 为每个 Pod 提供稳定的网络标识（hostname）和存储（PersistentVolume）；Pod 按顺序创建/删除；适合数据库、消息队列等
- **相关**：Kubernetes、Pod、Deployment（部署）、PersistentVolume（持久卷）

### StorageClass / 存储类
- **中文**：存储类
- **定义**：定义不同存储"类"的配置模板
- **说明**：StorageClass 定义存储的提供者（Provisioner）、参数（如 SSD/HDD）、回收策略；允许动态创建 PV；如 fast（SSD）、standard（HDD）
- **相关**：PersistentVolume（持久卷）、Kubernetes、Storage（存储）
