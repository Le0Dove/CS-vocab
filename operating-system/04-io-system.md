# 04. I/O 系统 (I/O System)

## 基础概念### /dev
- **发音**：/dev/
- **中文**：设备目录
- **定义**：Unix/Linux 中存放设备文件的目录
- **说明**：/dev 下的文件代表系统设备；如 /dev/sda（第一块 SCSI/SATA 磁盘）、/dev/tty（终端）、/dev/null（空设备）
- **相关**：Device File（设备文件）、udev
### Adapter / 适配器
- **音标**：/əˈdæptər/
- **中文**：适配器
- **定义**：连接设备和计算机的接口卡或芯片
- **说明**：适配器通常包含控制器功能；如网络适配器（网卡）、显示适配器（显卡）、SCSI 适配器
- **同义词**：Interface Card、Controller（控制器）
- **相关**：Device（设备）、Controller（控制器）
### Advanced Programmable Interrupt Controller (APIC) / 高级可编程中断控制器
- **中文**：高级可编程中断控制器
- **定义**：现代多处理器系统中的中断控制器
- **说明**：APIC 包括本地 APIC（每个 CPU 一个）和 I/O APIC（一个系统一个）；支持多处理器中断分发、中断亲和性等
- **相关**：Interrupt Controller（中断控制器）、PIC、IRQ、SMP
### AFP (Apple Filing Protocol) / Apple 归档协议
- **发音**：/eɪ-ɛf-piː/
- **中文**：Apple 归档协议
- **定义**：Apple 开发的用于 macOS 的网络文件共享协议
- **说明**：AFP 已被 SMB2/SMB3 取代；现代 macOS 主要使用 SMB 进行文件共享
- **相关**：SMB、NFS
### BFQ (Budget Fair Queuing) / 预算公平队列
- **中文**：预算公平队列
- **定义**：CFQ 的改进版，基于请求数量而非时间片分配 I/O 预算
- **说明**：BFQ 提供更好的交互式响应和低延迟；适合桌面和移动设备
- **相关**：I/O Scheduler（I/O 调度器）、CFQ
### Block Device / 块设备
- **中文**：块设备
- **定义**：以固定大小块为单位进行数据传输的设备
- **说明**：块设备支持随机访问，数据缓存在块缓冲区；如硬盘、SSD、USB 存储设备
- **相关**：Character Device（字符设备）、Block（块）、Buffer（缓冲）
### Bottom Half / 下半部
- **中文**：下半部
- **定义**：中断处理中推迟执行的部分，处理复杂且耗时的工作
- **说明**：下半部可以被打断，不阻塞其他中断；实现方式包括软中断（Softirq）、Tasklet、工作队列（Workqueue）
- **相关**：Top Half（上半部）、Softirq（软中断）、Tasklet、Workqueue（工作队列）
### Buffer / 缓冲
- **音标**：/ˈbʌfər/
- **中文**：缓冲
- **定义**：用于临时存储数据的内存区域，协调速度不匹配的设备或处理过程
- **说明**：缓冲减少设备间的速度差异，减少 I/O 操作次数；分为单缓冲、双缓冲、循环缓冲等
- **相关**：Cache（缓存）、Buffer Cache（缓冲缓存）、Double Buffering（双缓冲）
### Buffer Cache / 缓冲缓存
- **中文**：缓冲缓存
- **定义**：操作系统中缓存磁盘块数据的内存区域
- **说明**：Buffer Cache 缓存磁盘 I/O 的数据块，减少磁盘访问；现代 Linux 使用页缓存（Page Cache）替代传统 Buffer Cache
- **相关**：Page Cache（页缓存）、Buffer（缓冲）、Disk I/O（磁盘 I/O）
### Buffer Pool / 缓冲池
- **中文**：缓冲池
- **定义**：预先分配的一组缓冲区，用于 I/O 操作
- **说明**：缓冲池减少动态分配缓冲区的开销；数据库系统通常使用缓冲池管理数据页
- **相关**：Buffer（缓冲）、Buffer Cache（缓冲缓存）
### Bus / 总线
- **音标**：/bʌs/
- **中文**：总线
- **定义**：连接计算机各组件并传输数据、地址和控制信号的通信系统
- **说明**：总线包括系统总线（连接 CPU、内存、I/O）、PCIe 总线、USB 总线、SATA 总线等
- **相关**：Controller（控制器）、Device（设备）
### C-LOOK (Circular LOOK) / 循环查看
- **中文**：循环查看
- **定义**：LOOK 的循环版本，磁头扫描到最远请求后快速返回最左请求继续
- **相关**：LOOK、C-SCAN、Disk Scheduling（磁盘调度）
### C-SCAN (Circular SCAN) / 循环扫描
- **中文**：循环扫描
- **定义**：磁头从一端扫描到另一端后，立即返回到起始端继续扫描的磁盘调度算法
- **说明**：C-SCAN 提供更均匀的等待时间；返回途中不处理请求（快速返回）
- **相关**：SCAN（扫描算法）、LOOK、Disk Scheduling（磁盘调度）
### CFQ (Completely Fair Queuing) / 完全公平队列
- **中文**：完全公平队列
- **定义**：Linux 的 I/O 调度器，为每个进程分配公平的磁盘时间片
- **说明**：CFQ 类似 CPU 的 CFS 调度器；适合桌面系统和多用户系统；已被 BFQ 取代
- **相关**：I/O Scheduler（I/O 调度器）、BFQ
### Channel / 通道
- **音标**：/ˈtʃænl/
- **中文**：通道
- **定义**：独立于 CPU 的专门 I/O 处理单元
- **说明**：大型机系统中使用通道处理 I/O，释放 CPU；现代系统中 DMA 控制器有类似功能
- **相关**：DMA（直接内存访问）、I/O Processor（I/O 处理器）
### Character Device / 字符设备
- **中文**：字符设备
- **定义**：以字符流为单位进行数据传输的设备
- **说明**：字符设备不支持随机访问，数据按顺序读写；如键盘、鼠标、串口、打印机
- **相关**：Block Device（块设备）、Stream（流）
### CIFS (Common Internet File System) / 通用互联网文件系统
- **发音**：/siː-ɛf-ɛs/
- **中文**：通用互联网文件系统
- **定义**：SMB 协议的扩展版本
- **相关**：SMB、NAS（网络附加存储）
### Circular Buffer / 循环缓冲
- **中文**：循环缓冲
- **定义**：首尾相连、循环利用的缓冲区
- **说明**：循环缓冲使用生产者-消费者模型；生产者写入数据，消费者读取数据；适用于流式数据处理
- **相关**：Buffer（缓冲）、Ring Buffer（环形缓冲）
### Controller / 控制器
- **音标**：/kənˈtroʊlər/
- **中文**：控制器
- **定义**：控制设备操作的硬件组件或芯片
- **说明**：设备控制器连接设备和系统总线，处理设备的细节操作；如磁盘控制器、USB 控制器、网络控制器
- **相关**：Device（设备）、Driver（驱动）、Bus（总线）
### Degraded Mode / 降级模式
- **中文**：降级模式
- **定义**：RAID 阵列中有磁盘故障但仍在运行的状态
- **说明**：降级模式下 RAID 失去冗余保护；需要尽快更换故障磁盘并重建（Rebuild）
- **相关**：RAID、Rebuild（重建）、Hot Spare（热备盘）
### Device / 设备
- **音标**：/dɪˈvaɪs/
- **中文**：设备
- **定义**：计算机系统中用于输入、输出、存储或通信的硬件组件
- **说明**：设备分为块设备（Block Device，如磁盘）和字符设备（Character Device，如键盘）
- **相关**：Hardware（硬件）、Peripheral（外设）、Controller（控制器）
### Device Driver / 设备驱动
- **中文**：设备驱动
- **定义**：操作系统中控制和管理特定设备的软件模块
- **说明**：设备驱动提供统一接口，屏蔽硬件差异；驱动程序与设备控制器交互，处理中断和 I/O 操作
- **相关**：Controller（控制器）、Kernel Module（内核模块）、Interrupt（中断）
### Device File / 设备文件
- **中文**：设备文件
- **定义**：Unix/Linux 中表示设备的特殊文件
- **说明**：设备文件位于 /dev 目录；块设备文件和字符设备文件通过主设备号（Major Number）和次设备号（Minor Number）标识设备
- **相关**：Block Device（块设备）、Character Device（字符设备）、/dev
### Device-Independent I/O Software / 设备独立性软件
- **中文**：设备独立性软件
- **定义**：与具体设备无关，提供统一 I/O 接口的操作系统层
- **说明**：负责设备命名、保护、缓冲、分配、错误处理等；如 Unix 的块设备层、缓冲缓存（Buffer Cache）
- **相关**：Device Driver（设备驱动）、Buffer Cache（缓冲缓存）
### Direct Memory Access (DMA) / 直接内存访问
- **中文**：直接内存访问
- **定义**：允许设备直接与内存传输数据，无需 CPU 参与的 I/O 方式
- **说明**：DMA 大大提高 I/O 效率，CPU 只需启动 DMA 传输，传输完成后接收中断；DMA 控制器管理传输
- **相关**：DMA Controller（DMA 控制器）、Interrupt（中断）
### Disk Scheduling / 磁盘调度
- **中文**：磁盘调度
- **定义**：决定磁盘 I/O 请求执行顺序的算法
- **说明**：磁盘调度目标是减少寻道时间和旋转延迟，提高磁盘吞吐量；常见算法包括 FCFS、SSTF、SCAN、C-SCAN 等
- **相关**：Seek Time（寻道时间）、I/O Scheduler（I/O 调度器）
### DMA Controller / DMA 控制器
- **中文**：DMA 控制器
- **定义**：管理 DMA 传输的硬件组件
- **说明**：DMA 控制器接收 CPU 的传输指令，控制总线直接在设备和内存间传输数据；传输完成后通知 CPU
- **相关**：DMA（直接内存访问）、Bus（总线）
### DMA Engine / DMA 引擎
- **中文**：DMA 引擎
- **定义**：现代系统中集成在设备或芯片组中的 DMA 控制器
- **说明**：现代 DMA 引擎支持分散/聚集（Scatter/Gather）、虚拟 DMA、IOMMU 等高级特性
- **相关**：DMA（直接内存访问）、Scatter/Gather（分散/聚集）
### Double Buffering / 双缓冲
- **中文**：双缓冲
- **定义**：使用两个缓冲区交替进行 I/O 操作的技术
- **说明**：一个缓冲区用于 I/O 传输时，另一个供 CPU 处理；减少等待时间，提高并行性
- **相关**：Buffer（缓冲）、Ping-Pong Buffer（乒乓缓冲）
### Driver / 驱动
- **音标**：/ˈdraɪvər/
- **中文**：驱动
- **定义**：同 Device Driver
- **相关**：Device Driver（设备驱动）
### Elevator Algorithm / 电梯算法
- **中文**：电梯算法
- **定义**：同 SCAN
- **相关**：SCAN（扫描算法）
### FCoE (Fibre Channel over Ethernet) / 以太网光纤通道
- **发音**：/ɛf-siː-oʊ-iː/
- **中文**：以太网光纤通道
- **定义**：在以太网上传输光纤通道帧的协议
- **说明**：FCoE 将存储网络（SAN）和数据网络（LAN）融合，减少线缆和交换机成本
- **相关**：Fibre Channel（光纤通道）、SAN（存储区域网络）、Ethernet（以太网）
### Fibre Channel / 光纤通道
- **音标**：/ˈfaɪbər ˈtʃænl/
- **中文**：光纤通道
- **定义**：高速网络技术，主要用于 SAN 存储网络
- **说明**：光纤通道提供高带宽、低延迟、长距离的块级存储访问；速率从 1Gbps 到 128Gbps
- **相关**：SAN（存储区域网络）、FCoE
### Firmware / 固件
- **音标**：/ˈfɜːrmwer/
- **中文**：固件
- **定义**：嵌入硬件设备中的软件程序
- **说明**：固件控制设备的基本操作；如 BIOS/UEFI、SSD 固件、路由器固件；可以更新（刷固件）
- **相关**：Hardware（硬件）、Device（设备）、Device Driver（设备驱动）

---

## I/O 控制方式
### Flushing / 刷新
- **中文**：刷新
- **定义**：将缓冲区的数据强制写入目标设备
- **说明**：操作系统定期自动刷新缓冲区；应用程序可以通过 sync、fsync、fflush 等强制刷新
- **相关**：Buffer（缓冲）、Sync（同步）、fsync

---

## 磁盘 I/O 调度
### Hardware RAID / 硬件 RAID
- **中文**：硬件 RAID
- **定义**：由专用 RAID 控制器硬件实现的 RAID
- **说明**：硬件 RAID 性能高，不占用 CPU；控制器有独立处理器和缓存；成本较高
- **相关**：Software RAID（软件 RAID）、RAID Controller（RAID 控制器）
### Hot Spare / 热备盘
- **中文**：热备盘
- **定义**：RAID 阵列中预先配置的备用磁盘，当成员盘故障时自动替换
- **说明**：热备盘减少 RAID 降级状态的持续时间，降低数据丢失风险
- **相关**：Hot Swap（热插拔）、RAID、Degraded Mode（降级模式）
### Hot Swap / 热插拔
- **中文**：热插拔
- **定义**：在不关闭系统的情况下更换设备
- **说明**：热插拔允许在线更换故障磁盘；RAID 阵列支持热插拔以实现不停机维护
- **相关**：Hot Spare（热备盘）、RAID
### IDE (Integrated Drive Electronics) / 集成驱动电子设备
- **发音**：/aɪ-diː-iː/
- **中文**：集成驱动电子设备
- **定义**：同 PATA，旧式硬盘接口标准
- **相关**：PATA、SATA
### Input/Output (I/O) / 输入/输出
- **中文**：输入/输出
- **定义**：计算机与外部设备之间交换数据的过程
- **说明**：I/O 是操作系统的重要功能，包括设备管理、数据传输、缓冲管理等；I/O 操作通常比 CPU 计算慢几个数量级
- **相关**：Device（设备）、Driver（驱动）、Buffer（缓冲）
### Interface / 接口
- **音标**：/ˈɪntərfeɪs/
- **中文**：接口
- **定义**：设备与系统或其他设备之间交互的边界和规范
- **说明**：接口定义了电气特性、信号协议、数据格式等；如 SATA 接口、USB 接口、PCIe 接口
- **相关**：Port（端口）、Protocol（协议）

---

## 设备分类
### Interrupt Affinity / 中断亲和性
- **中文**：中断亲和性
- **定义**：将特定中断绑定到特定 CPU 核心处理的配置
- **说明**：中断亲和性减少缓存失效，提高 I/O 性能；通过 /proc/irq/IRQ/smp_affinity 设置
- **相关**：APIC、Interrupt（中断）、CPU Affinity（CPU 亲和性）
### Interrupt Controller / 中断控制器
- **中文**：中断控制器
- **定义**：管理和分发中断信号的硬件
- **说明**：传统 x86 使用 PIC（可编程中断控制器，如 8259A）；现代系统使用 APIC（高级可编程中断控制器）
- **相关**：Interrupt（中断）、IRQ（中断请求）、APIC
### Interrupt Descriptor Table (IDT) / 中断描述符表
- **中文**：中断描述符表
- **定义**：x86 架构中存储中断和异常处理程序地址的数据结构
- **说明**：IDT 包含 256 个条目，对应不同的中断和异常；通过 lidt 指令加载
- **相关**：Interrupt Vector（中断向量）、Interrupt（中断）
### Interrupt Request (IRQ) / 中断请求
- **中文**：中断请求
- **定义**：设备向中断控制器发出的中断信号
- **说明**：每个设备分配一个 IRQ 号；x86 系统有 16 个传统 IRQ（IRQ0-IRQ15），现代系统使用 APIC 支持更多中断
- **相关**：Interrupt（中断）、Interrupt Controller（中断控制器）
### Interrupt Service Routine (ISR) / 中断服务例程
- **中文**：中断服务例程
- **定义**：同 Interrupt Handler
- **相关**：Interrupt Handler（中断处理程序）
### Interrupt Vector / 中断向量
- **中文**：中断向量
- **定义**：中断处理程序入口地址的数组或表
- **说明**：CPU 根据中断号查找中断向量表，跳转到对应的中断处理程序；x86 使用 IDT（中断描述符表）
- **相关**：Interrupt（中断）、Interrupt Descriptor Table（中断描述符表）
### Interrupt-driven I/O / 中断驱动 I/O
- **中文**：中断驱动 I/O
- **定义**：设备就绪时通过中断通知 CPU，CPU 再进行数据传输
- **说明**：中断驱动 I/O 提高 CPU 效率，CPU 可以在设备准备期间执行其他任务；但每个数据传输仍需 CPU 参与
- **相关**：Interrupt（中断）、DMA（直接内存访问）
### ioctl
- **发音**：/aɪ-ɒk-təl/ 或 /ɪ-ɒk-təl/
- **中文**：I/O 控制（系统调用）
- **定义**：用于设备特定控制操作的系统调用
- **说明**：ioctl 是"input/output control"的缩写；用于配置设备参数、查询设备状态等非标准读写操作
- **相关**：System Call（系统调用）、Device Driver（设备驱动）

---

## 缓冲与缓存
### iSCSI (Internet Small Computer Systems Interface) / 互联网小型计算机系统接口
- **发音**：/aɪ-ˈskʌzi/
- **中文**：互联网小型计算机系统接口
- **定义**：通过 IP 网络传输 SCSI 命令的存储协议
- **说明**：iSCSI 将块级存储设备通过网络暴露；比光纤通道 SAN 成本低，但性能稍差
- **相关**：SCSI、SAN（存储区域网络）、Block Device（块设备）
### Kernel Module / 内核模块
- **中文**：内核模块
- **定义**：可以动态加载和卸载的内核代码
- **说明**：设备驱动通常以内核模块形式实现；使用 insmod/modprobe 加载，rmmod 卸载
- **相关**：Device Driver（设备驱动）、Loadable Kernel Module（可加载内核模块）
### Kyber / Kyber（I/O 调度器）
- **中文**：Kyber（I/O 调度器）
- **定义**：Linux 的高性能 I/O 调度器，针对快速设备优化
- **说明**：Kyber 使用多个队列和令牌机制，适合 NVMe SSD 等高速设备
- **相关**：I/O Scheduler（I/O 调度器）、NVMe、SSD
### Loadable Kernel Module (LKM) / 可加载内核模块
- **中文**：可加载内核模块
- **定义**：可以在运行时被加载到内核或从内核卸载的代码
- **说明**：LKM 提高内核的灵活性和可扩展性；设备驱动、文件系统、网络协议等可以模块化
- **相关**：Kernel Module（内核模块）、Device Driver（设备驱动）
### LOOK / 查看算法
- **中文**：查看算法
- **定义**：SCAN 的改进，磁头只移动到最远请求位置，而不是磁盘两端
- **说明**：LOOK 减少不必要的磁头移动；C-LOOK 是 LOOK 的循环版本
- **相关**：SCAN（扫描算法）、C-SCAN、C-LOOK
### Loop Device / 循环设备
- **中文**：循环设备
- **定义**：将普通文件作为块设备使用的虚拟设备
- **说明**：loop 设备允许挂载磁盘镜像文件（如 ISO、IMG）；如 /dev/loop0
- **相关**：Virtual Device（虚拟设备）、Mount（挂载）
### M.2
- **发音**：/em-dɒt-tuː/
- **中文**：M.2 接口
- **定义**：小型化的内部扩展卡接口标准，常用于 SSD 和无线网卡
- **说明**：M.2 支持 SATA 和 PCIe/NVMe 协议；尺寸规格如 2280（宽 22mm，长 80mm）
- **相关**：NVMe、SATA、SSD
### Major Number / 主设备号
- **中文**：主设备号
- **定义**：标识设备类型的编号
- **说明**：主设备号对应特定的设备驱动程序；如 SCSI 磁盘主设备号为 8，TTY 主设备号为 4
- **相关**：Minor Number（次设备号）、Device File（设备文件）
### Minor Number / 次设备号
- **中文**：次设备号
- **定义**：标识同类设备中具体设备的编号
- **说明**：次设备号区分同一驱动程序控制的不同设备；如 /dev/sda 次设备号为 0，/dev/sda1 次设备号为 1
- **相关**：Major Number（主设备号）、Device File（设备文件）

---

## 设备驱动
### Module / 模块
- **音标**：/ˈmɒdjuːl/
- **中文**：模块
- **定义**：独立的软件组件，可以动态加载
- **相关**：Kernel Module（内核模块）、Device Driver（设备驱动）
### NAS (Network Attached Storage) / 网络附加存储
- **发音**：/næs/
- **中文**：网络附加存储
- **定义**：通过网络提供文件级存储访问的专用设备
- **说明**：NAS 使用 NFS、SMB/CIFS 等协议；易于部署和管理；适合文件共享和备份
- **相关**：SAN（存储区域网络）、NFS、SMB/CIFS
### Network Device / 网络设备
- **中文**：网络设备
- **定义**：用于网络通信的设备
- **说明**：网络设备（如网卡）在 Linux 中通过套接字接口访问，不作为块设备或字符设备处理
- **相关**：Network Interface Card（网卡）、Socket（套接字）
### NFS (Network File System) / 网络文件系统
- **发音**：/ɛn-ɛf-ɛs/
- **中文**：网络文件系统
- **定义**：允许计算机通过网络访问远程文件系统的协议
- **说明**：NFS 由 Sun Microsystems 开发，现为标准网络文件共享协议；NFSv4 支持状态操作、安全性增强
- **相关**：SMB/CIFS、NAS（网络附加存储）、RPC（远程过程调用）
### NOOP (No Operation) / 空操作
- **中文**：空操作（I/O 调度器）
- **定义**：最简单的 I/O 调度器，不进行重排序，直接合并相邻请求后提交
- **说明**：NOOP 适合 SSD 等无机械延迟的设备；因为 SSD 不需要寻道，重排序没有收益
- **相关**：I/O Scheduler（I/O 调度器）、SSD
### NVMe (Non-Volatile Memory Express) / 非易失性内存主机控制器接口规范
- **发音**：/ɛn-viː-ɛm-iː/
- **中文**：NVMe
- **定义**：为基于闪存的存储设备设计的高性能接口规范
- **说明**：NVMe 通过 PCIe 总线连接 SSD，支持多队列、低延迟、高并发；性能远高于 SATA SSD
- **相关**：SSD、PCIe、M.2、U.2
### Page Cache / 页缓存
- **中文**：页缓存
- **定义**：操作系统中缓存文件数据的内存页
- **说明**：Page Cache 缓存从文件读取的数据和写入文件的数据；读取时先查页缓存，写入时先写到页缓存（延迟写回）
- **相关**：Buffer Cache（缓冲缓存）、Write-Back（写回）、Swap Cache（交换缓存）
### PATA (Parallel ATA) / 并行 ATA
- **发音**：/ˈpɑːtə/
- **中文**：并行 ATA
- **定义**：旧式的并行接口标准，也称为 IDE
- **说明**：PATA 使用宽排线（40/80 针），已被 SATA 取代
- **同义词**：IDE (Integrated Drive Electronics)
- **相关**：SATA、IDE
### PCIe (Peripheral Component Interconnect Express) / 外围组件互联快速接口
- **发音**：/piː-siː-iː-iː/
- **中文**：PCIe
- **定义**：高速串行计算机扩展总线标准
- **说明**：PCIe 用于连接显卡、网卡、NVMe SSD 等高速设备；支持多通道（x1、x4、x8、x16），带宽随版本提升
- **相关**：PCI、NVMe、Bus（总线）
### Peripheral / 外设
- **音标**：/pəˈrɪfərəl/
- **中文**：外设（外围设备）
- **定义**：连接到计算机主机的外部设备
- **说明**：外设包括输入设备（键盘、鼠标）、输出设备（显示器、打印机）、存储设备（磁盘、U 盘）、通信设备（网卡）
- **相关**：Device（设备）、I/O（输入/输出）
### Ping-Pong Buffer / 乒乓缓冲
- **中文**：乒乓缓冲
- **定义**：同双缓冲
- **相关**：Double Buffering（双缓冲）
### Polling / 轮询
- **音标**：/ˈpoʊlɪŋ/
- **中文**：轮询
- **定义**：CPU 定期检查设备状态，判断是否可以进行 I/O 操作
- **说明**：轮询消耗 CPU 时间；适用于 I/O 频繁且延迟要求低的场景
- **相关**：Programmed I/O（程序控制 I/O）、Interrupt（中断）
### Port / 端口
- **音标**：/pɔːrt/
- **中文**：端口
- **定义**：设备与计算机通信的接口点
- **说明**：端口可以是物理接口（如 USB 端口、串口）或逻辑标识（如 I/O 端口地址、TCP/UDP 端口）
- **相关**：I/O Port（I/O 端口）、Interface（接口）
### Port-Mapped I/O (PMIO) / 端口映射 I/O
- **中文**：端口映射 I/O
- **定义**：使用专门的 I/O 指令（如 x86 的 in/out）访问独立的 I/O 地址空间
- **说明**：x86 架构支持 PMIO，I/O 端口地址空间为 64KB；与 MMIO 相对
- **相关**：Memory-Mapped I/O（内存映射 I/O）、I/O Port（I/O 端口）

---

## I/O 软件层次
### Programmable Interrupt Controller (PIC) / 可编程中断控制器
- **中文**：可编程中断控制器
- **定义**：传统的中断控制器，管理硬件中断请求
- **说明**：x86 系统使用两个级联的 8259A PIC，支持 15 个外部中断（IRQ0-IRQ15）；已被 APIC 取代
- **相关**：Interrupt Controller（中断控制器）、APIC、IRQ
### Programmed I/O / 程序控制 I/O
- **中文**：程序控制 I/O
- **定义**：CPU 直接通过指令控制 I/O 设备的数据传输
- **说明**：CPU 轮询设备状态，等待设备就绪后读写数据；简单但 CPU 效率极低
- **同义词**：Polling I/O
- **相关**：Polling（轮询）、Interrupt-driven I/O（中断驱动 I/O）
### RAID Controller / RAID 控制器
- **中文**：RAID 控制器
- **定义**：管理 RAID 阵列的专用硬件卡
- **说明**：RAID 控制器处理数据分条、镜像、奇偶校验计算等；通常带有缓存电池保护
- **相关**：Hardware RAID（硬件 RAID）、Cache（缓存）
### Raw Device / 原始设备
- **中文**：原始设备
- **定义**：绕过文件系统缓存，直接访问块设备的接口
- **说明**：原始设备用于数据库等需要直接控制 I/O 的应用；如 /dev/raw、O_DIRECT 标志
- **相关**：Block Device（块设备）、Direct I/O（直接 I/O）
### Read-Ahead / 预读
- **中文**：预读
- **定义**：在实际请求之前预先读取后续数据的技术
- **说明**：预读利用空间局部性，减少后续读请求的等待时间；操作系统自动进行顺序预读
- **相关**：Prefetching（预取）、Locality（局部性）

---

## 存储技术
### Rebuild / 重建
- **音标**：/ˌriːˈbɪld/
- **中文**：重建
- **定义**：RAID 阵列中更换故障磁盘后，根据冗余数据恢复新磁盘数据的过程
- **说明**：重建过程耗时且影响性能；重建期间 RAID 仍处于脆弱状态
- **相关**：RAID、Degraded Mode（降级模式）
### Request Merging / 请求合并
- **中文**：请求合并
- **定义**：将多个相邻或重叠的 I/O 请求合并为一个请求的技术
- **说明**：请求合并减少磁盘 I/O 次数，提高效率；I/O 调度器自动进行请求合并
- **相关**：I/O Scheduler（I/O 调度器）、Request Queue（请求队列）
### Request Queue / 请求队列
- **中文**：请求队列
- **定义**：操作系统中等待处理的 I/O 请求队列
- **说明**：I/O 调度器管理请求队列，对请求进行合并、排序和调度
- **相关**：I/O Scheduler（I/O 调度器）、Disk Scheduling（磁盘调度）
### Ring Buffer / 环形缓冲
- **中文**：环形缓冲
- **定义**：同循环缓冲
- **相关**：Circular Buffer（循环缓冲）
### Samba
- **发音**：/ˈsɑːmbə/
- **中文**：Samba
- **定义**：在 Unix/Linux 系统上实现 SMB/CIFS 协议的开源软件
- **说明**：Samba 允许 Linux 服务器提供 Windows 文件共享服务；也可以作为 Active Directory 域控制器
- **相关**：SMB、CIFS、NAS（网络附加存储）
### SAN (Storage Area Network) / 存储区域网络
- **发音**：/sæn/
- **中文**：存储区域网络
- **定义**：专用的、高性能的网络，连接服务器和存储设备
- **说明**：SAN 使用光纤通道（Fibre Channel）或 iSCSI 协议；提供块级存储访问；与 NAS（文件级）不同
- **相关**：NAS（网络附加存储）、Fibre Channel（光纤通道）、iSCSI
### SAS (Serial Attached SCSI) / 串行连接 SCSI
- **发音**：/sæs/
- **中文**：串行连接 SCSI
- **定义**：SCSI 的串行版本，用于连接硬盘、SSD 等存储设备
- **说明**：SAS 兼容 SATA 设备，支持双端口、热插拔、命令队列；企业级存储常用
- **相关**：SCSI、SATA、HDD、SSD
### SATA (Serial ATA) / 串行 ATA
- **发音**：/ˈsɑːtə/
- **中文**：串行 ATA
- **定义**：用于连接存储设备的串行接口标准
- **说明**：SATA 替代并行 ATA（PATA/IDE），支持热插拔、更高传输速率；消费级硬盘和 SSD 常用
- **相关**：PATA、SAS、HDD、SSD
### SCAN / 扫描算法（电梯算法）
- **中文**：扫描算法（电梯算法）
- **定义**：磁头从一端扫描到另一端，处理沿途请求的磁盘调度算法
- **说明**：类似电梯上下运行；SCAN 避免饥饿，但两端请求等待时间较长
- **同义词**：Elevator Algorithm
- **相关**：Disk Scheduling（磁盘调度）、C-SCAN、LOOK
### Scatter/Gather / 分散/聚集
- **中文**：分散/聚集
- **定义**：DMA 传输中，从多个不连续的内存位置读取数据（Gather）或写入到多个不连续位置（Scatter）
- **说明**：分散/聚集允许 DMA 直接传输分散在内存中的数据，无需 CPU 预先拷贝到连续缓冲区
- **相关**：DMA（直接内存访问）、DMA Engine（DMA 引擎）
### SCSI (Small Computer Systems Interface) / 小型计算机系统接口
- **发音**：/ˈskʌzi/
- **中文**：小型计算机系统接口
- **定义**：用于连接计算机和外围设备（如磁盘、磁带、扫描仪）的标准接口
- **说明**：SCSI 支持多设备连接、高传输速率、命令队列；现代系统使用 SAS（Serial Attached SCSI）
- **相关**：SAS、iSCSI、Block Device（块设备）
### Shortest Seek Time First (SSTF) / 最短寻道时间优先
- **中文**：最短寻道时间优先
- **定义**：优先处理离当前磁头位置最近的请求的磁盘调度算法
- **说明**：SSTF 减少平均寻道时间，但可能导致远端请求饥饿（Starvation）
- **相关**：Disk Scheduling（磁盘调度）、FCFS、SCAN
### SMB (Server Message Block) / 服务器消息块
- **发音**：/ɛs-ɛm-biː/
- **中文**：服务器消息块
- **定义**：微软开发的网络文件共享协议
- **说明**：SMB 用于 Windows 文件共享和打印机共享；CIFS（Common Internet File System）是 SMB 的扩展
- **同义词**：CIFS (Common Internet File System)
- **相关**：NFS、Samba、NAS（网络附加存储）
### Softirq / 软中断
- **发音**：/ˈsɒft-ɜːrk/
- **中文**：软中断
- **定义**：Linux 中下半部的一种实现，运行在中断上下文但允许其他软中断
- **说明**：软中断在硬件中断返回时执行；同一类型的软中断可以在多个 CPU 上并行执行
- **相关**：Bottom Half（下半部）、Tasklet、Interrupt（中断）
### Software RAID / 软件 RAID
- **中文**：软件 RAID
- **定义**：由操作系统软件实现的 RAID
- **说明**：软件 RAID 成本低，灵活性高，但占用 CPU 资源；Linux mdadm 工具管理软件 RAID
- **相关**：Hardware RAID（硬件 RAID）、mdadm
### System Call Interface / 系统调用接口
- **中文**：系统调用接口
- **定义**：用户程序请求内核 I/O 服务的接口
- **说明**：系统调用包括 open、read、write、close、ioctl、mmap 等；是用户空间与内核的边界
- **相关**：System Call（系统调用）、Kernel（内核）
### Tasklet / 任务片
- **发音**：/ˈtæsk-lɪt/
- **中文**：任务片
- **定义**：Linux 中基于软中断的下半部机制
- **说明**：Tasklet 在同一时刻只能在一个 CPU 上执行（同类型），不能睡眠；比工作队列更快但限制更多
- **相关**：Softirq（软中断）、Workqueue（工作队列）、Bottom Half（下半部）
### Top Half / 上半部
- **中文**：上半部
- **定义**：中断处理程序中立即执行的部分，处理紧急且快速的工作
- **说明**：上半部屏蔽中断，快速响应硬件；将非紧急工作交给下半部处理
- **相关**：Bottom Half（下半部）、Interrupt Handler（中断处理程序）
### U.2
- **发音**：/juː-dɒt-tuː/
- **中文**：U.2 接口
- **定义**：用于连接 2.5 英寸 NVMe SSD 的接口标准
- **说明**：U.2（原 SFF-8639）兼容 SAS/SATA，支持热插拔；主要用于企业级服务器
- **相关**：NVMe、SAS、SSD
### User-Space I/O Library / 用户空间 I/O 库
- **中文**：用户空间 I/O 库
- **定义**：提供用户程序 I/O 接口的库函数
- **说明**：如 C 标准库的 stdio（fopen、fread、fwrite）；在库中进行缓冲，减少系统调用次数
- **相关**：stdio、System Call（系统调用）
### Virtual Device / 虚拟设备
- **中文**：虚拟设备
- **定义**：不对应物理硬件，由软件模拟的设备
- **说明**：虚拟设备包括 loop 设备（将文件作为块设备）、ramdisk（内存磁盘）、虚拟网卡等
- **相关**：Device（设备）、Virtualization（虚拟化）
### WebDAV (Web Distributed Authoring and Versioning) / Web 分布式创作和版本控制
- **发音**：/wɛb-dæv/
- **中文**：WebDAV
- **定义**：基于 HTTP 的协议，允许用户远程编辑和管理文件
- **说明**：WebDAV 扩展 HTTP，支持文件锁定、属性管理、命名空间操作；常用于内容管理系统
- **相关**：HTTP、NFS、SMB
### Workqueue / 工作队列
- **中文**：工作队列
- **定义**：Linux 中在进程上下文执行工作的机制
- **说明**：工作队列中的工作函数可以睡眠，可以使用阻塞操作；适合需要长时间或可能阻塞的下半部工作
- **相关**：Bottom Half（下半部）、Tasklet、Kernel Thread（内核线程）
