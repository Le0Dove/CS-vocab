# 04. I/O 系统 (I/O System)

### /dev
- **发音**：/dev/
- **中文**：设备目录
- **定义**：Unix/Linux 中存放设备文件的目录
- **说明**：/dev 下的文件代表系统设备；如 /dev/sda（第一块 SCSI/SATA 磁盘）、/dev/tty（终端）、/dev/null（空设备）
- **相关**：Device File（设备文件）、udev

### Block Device / 块设备
- **中文**：块设备
- **定义**：以固定大小块为单位进行数据传输的设备
- **说明**：块设备支持随机访问，数据缓存在块缓冲区；如硬盘、SSD、USB 存储设备
- **相关**：Character Device（字符设备）、Block（块）、Buffer（缓冲）

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

### Bus / 总线
- **音标**：/bʌs/
- **中文**：总线
- **定义**：连接计算机各组件并传输数据、地址和控制信号的通信系统
- **说明**：总线包括系统总线（连接 CPU、内存、I/O）、PCIe 总线、USB 总线、SATA 总线等
- **相关**：Controller（控制器）、Device（设备）

### C-SCAN (Circular SCAN) / 循环扫描
- **中文**：循环扫描
- **定义**：磁头从一端扫描到另一端后，立即返回到起始端继续扫描的磁盘调度算法
- **说明**：C-SCAN 提供更均匀的等待时间；返回途中不处理请求（快速返回）
- **相关**：SCAN（扫描算法）、FCFS、Disk Scheduling（磁盘调度）

### Cache / 缓存
- **音标**：/kæʃ/
- **中文**：缓存
- **定义**：高速存储层，存储经常访问的数据以加速后续访问
- **说明**：在 I/O 系统中，缓存用于减少磁盘访问次数；读缓存命中时直接返回数据，写缓存使用写回（Write-Back）或写穿透（Write-Through）策略
- **相关**：Buffer（缓冲）、Page Cache（页缓存）、Buffer Cache（缓冲缓存）

### Character Device / 字符设备
- **中文**：字符设备
- **定义**：以字符流为单位进行数据传输的设备
- **说明**：字符设备不支持随机访问，数据按顺序读写；如键盘、鼠标、串口、打印机
- **相关**：Block Device（块设备）、Stream（流）

### Controller / 控制器
- **音标**：/kənˈtroʊlər/
- **中文**：控制器
- **定义**：控制设备操作的硬件组件或芯片
- **说明**：设备控制器连接设备和系统总线，处理设备的细节操作；如磁盘控制器、USB 控制器、网络控制器
- **相关**：Device（设备）、Driver（驱动）、Bus（总线）

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
- **说明**：设备文件位于 /dev 目录；通过主设备号（Major Number）和次设备号（Minor Number）标识设备
- **相关**：Block Device（块设备）、Character Device（字符设备）、/dev

### Direct Memory Access (DMA) / 直接内存访问
- **中文**：直接内存访问
- **定义**：允许设备直接与内存传输数据，无需 CPU 参与的 I/O 方式
- **说明**：DMA 大大提高 I/O 效率，CPU 只需启动 DMA 传输，传输完成后接收中断；DMA 控制器管理传输
- **相关**：Interrupt（中断）、Interrupt-driven I/O（中断驱动 I/O）

### Disk Scheduling / 磁盘调度
- **中文**：磁盘调度
- **定义**：决定磁盘 I/O 请求执行顺序的算法
- **说明**：磁盘调度目标是减少寻道时间和旋转延迟，提高磁盘吞吐量；常见算法包括 FCFS、SSTF、SCAN、C-SCAN
- **相关**：Seek Time（寻道时间）、FCFS、SSTF、SCAN

### Double Buffering / 双缓冲
- **中文**：双缓冲
- **定义**：使用两个缓冲区交替进行 I/O 操作的技术
- **说明**：一个缓冲区用于 I/O 传输时，另一个供 CPU 处理；减少等待时间，提高并行性
- **相关**：Buffer（缓冲）

### First Come First Served (FCFS) / 先来先服务
- **发音**：/ɛf-siː-ɛf-ɛs/
- **中文**：先来先服务
- **定义**：按照请求到达的顺序依次处理的磁盘调度算法
- **说明**：FCFS 公平简单，但寻道时间长，性能较差；作为其他调度算法的性能对比基准
- **相关**：Disk Scheduling（磁盘调度）、SSTF、SCAN

### Input/Output (I/O) / 输入/输出
- **中文**：输入/输出
- **定义**：计算机与外部设备之间交换数据的过程
- **说明**：I/O 是操作系统的重要功能，包括设备管理、数据传输、缓冲管理等；I/O 操作通常比 CPU 计算慢几个数量级
- **相关**：Device（设备）、Driver（驱动）、Buffer（缓冲）

### Interrupt / 中断
- **音标**：/ˈɪntərʌpt/
- **中文**：中断
- **定义**：硬件或软件发出的信号，通知 CPU 需要立即处理的事件
- **说明**：中断允许设备异步通知 CPU，CPU 暂停当前任务，保存上下文，执行中断处理程序（Interrupt Handler），完成后恢复原任务
- **相关**：Interrupt-driven I/O（中断驱动 I/O）、Interrupt Handler（中断处理程序）、IRQ（中断请求）

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

### Kernel Module / 内核模块
- **中文**：内核模块
- **定义**：可以动态加载和卸载的内核代码
- **说明**：设备驱动通常以内核模块形式实现；使用 insmod/modprobe 加载，rmmod 卸载
- **相关**：Device Driver（设备驱动）、Loadable Kernel Module（可加载内核模块）

### NAS (Network Attached Storage) / 网络附加存储
- **发音**：/næs/
- **中文**：网络附加存储
- **定义**：通过网络提供文件级存储访问的专用设备
- **说明**：NAS 使用 NFS、SMB 等协议；易于部署和管理；适合文件共享和备份
- **相关**：SAN（存储区域网络）、NFS、SMB

### NFS (Network File System) / 网络文件系统
- **发音**：/ɛn-ɛf-ɛs/
- **中文**：网络文件系统
- **定义**：允许计算机通过网络访问远程文件系统的协议
- **说明**：NFS 由 Sun Microsystems 开发，现为标准网络文件共享协议；NFSv4 支持状态操作、增强安全性
- **相关**：SMB、NAS（网络附加存储）

### Page Cache / 页缓存
- **中文**：页缓存
- **定义**：操作系统中缓存文件数据的内存页
- **说明**：Page Cache 缓存从文件读取和写入文件的数据；读取时先查页缓存，写入时先写到页缓存（延迟写回）
- **相关**：Buffer Cache（缓冲缓存）、Cache（缓存）

### Peripheral / 外设
- **音标**：/pəˈrɪfərəl/
- **中文**：外设（外围设备）
- **定义**：连接到计算机主机的外部设备
- **说明**：外设包括输入设备（键盘、鼠标）、输出设备（显示器、打印机）、存储设备（磁盘、U 盘）、通信设备（网卡）
- **相关**：Device（设备）、I/O（输入/输出）

### Polling / 轮询
- **音标**：/ˈpoʊlɪŋ/
- **中文**：轮询
- **定义**：CPU 定期检查设备状态，判断是否可以进行 I/O 操作
- **说明**：轮询消耗 CPU 时间；适用于 I/O 频繁且延迟要求低的场景
- **相关**：Interrupt（中断）、Interrupt-driven I/O（中断驱动 I/O）

### Port / 端口
- **音标**：/pɔːrt/
- **中文**：端口
- **定义**：设备与计算机通信的接口点
- **说明**：端口可以是物理接口（如 USB 端口、串口）或逻辑标识（如 I/O 端口地址、TCP/UDP 端口）
- **相关**：Interface（接口）、I/O Port（I/O 端口）

### RAID (Redundant Array of Independent Disks) / 独立磁盘冗余阵列
- **发音**：/reɪd/
- **中文**：RAID（独立磁盘冗余阵列）
- **定义**：将多块独立磁盘组合成一个逻辑存储单元的技术
- **说明**：RAID 提供数据冗余、性能提升或两者兼顾；常见级别：RAID 0（条带化）、RAID 1（镜像）、RAID 5/6（分布式奇偶校验）、RAID 10（条带+镜像）
- **相关**：Hardware RAID（硬件 RAID）、Software RAID（软件 RAID）、RAID Controller（RAID 控制器）

### SAN (Storage Area Network) / 存储区域网络
- **发音**：/sæn/
- **中文**：存储区域网络
- **定义**：专用的高性能网络，连接服务器和块级存储设备
- **说明**：SAN 提供块级存储访问，区别于 NAS 的文件级访问；常用协议包括光纤通道、iSCSI
- **相关**：NAS（网络附加存储）、RAID

### SCAN / 扫描算法（电梯算法）
- **中文**：扫描算法（电梯算法）
- **定义**：磁头从一端扫描到另一端，处理沿途请求的磁盘调度算法
- **说明**：类似电梯上下运行；SCAN 避免饥饿，但两端请求等待时间较长
- **同义词**：Elevator Algorithm
- **相关**：Disk Scheduling（磁盘调度）、C-SCAN、SSTF

### SCSI (Small Computer Systems Interface) / 小型计算机系统接口
- **发音**：/ˈskʌzi/
- **中文**：小型计算机系统接口
- **定义**：用于连接计算机和外围设备的标准接口协议
- **说明**：SCSI 支持多设备连接、命令队列；现代系统使用 SAS（串行连接 SCSI）
- **相关**：Block Device（块设备）、SAS

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

### Virtual Device / 虚拟设备
- **中文**：虚拟设备
- **定义**：不对应物理硬件，由软件模拟的设备
- **说明**：虚拟设备包括 loop 设备（将文件作为块设备）、ramdisk（内存磁盘）、虚拟网卡等
- **相关**：Device（设备）、Virtualization（虚拟化）
