# 05. 总线与输入输出 (Bus & I/O)
### AGP (Accelerated Graphics Port) / 加速图形端口
- **中文**：加速图形端口
- **定义**：专门用于显卡的高速接口标准
- **说明**：AGP 是 PCI 的图形增强版本，已被 PCIe 取代
- **同义词**：AGP
- **相关**：PCIe（PCI 快速接口）、GPU
### Arbitration / 仲裁
- **中文**：仲裁
- **定义**：多个设备请求总线控制权时决定哪个设备获得控制权的机制
- **说明**：仲裁分为集中式仲裁和分布式仲裁；常见仲裁算法有轮询、优先级固定仲裁等
- **同义词**：Bus Arbitration（总线仲裁）
- **相关**：Bus（总线）、DMA（直接内存访问）
### Bus / 总线
- **中文**：总线
- **定义**：计算机各部件之间共享的通信线路
- **说明**：总线分为数据总线、地址总线、控制总线；现代计算机采用多层次总线架构；总线带宽决定传输速度
- **同义词**：Bus
- **相关**：Arbitration（仲裁）、Bridge（桥接）
### Control Bus / 控制总线
- **中文**：控制总线
- **定义**：传输控制信号（读/写使能、中断请求）的总线
- **同义词**：Control Bus
- **相关**：Bus（总线）、Data Bus（数据总线）、Address Bus（地址总线）
### DMA (Direct Memory Access) / 直接内存访问
- **中文**：直接内存访问
- **定义**：见 operating-system/04-io-system.md
- **同义词**：DMA
- **相关**：Interrupt（中断）、I/O Controller（I/O 控制器）
### Handshake / 握手
- **中文**：握手
- **定义**：双方通过控制信号交换确认建立通信同步的机制
- **说明**：异步握手常用 REQ/ACK 或 VALID/READY 信号
- **同义词**：Handshake
- **相关**：Bus（总线）、Synchronization（同步）
### I/O Address Space / I/O 地址空间
- **中文**：I/O 地址空间
- **定义**：与内存地址空间独立或映射到内存空间的设备寄存器访问地址区域
- **说明**：x86 提供 I/O 独立地址空间（PMIO）和内存映射 I/O（MMIO）；MMIO 更常见
- **同义词**：I/O Space（I/O 空间）
- **相关**：MMIO（内存映射 I/O）、Device Register（设备寄存器）
### Interrupt Controller / 中断控制器
- **中文**：中断控制器
- **定义**：管理和分发硬件中断请求的电路
- **说明**：APIC 是现代 x86 的中断控制器
- **同义词**：Interrupt Controller
- **相关**：Interrupt（中断）、APIC（高级可编程中断控制器）
### Interrupt Request / 中断请求
- **中文**：中断请求
- **定义**：设备向 CPU 发出的请求处理的硬件信号
- **说明**：每个 IRQ 映射到一个中断源；中断请求通过控制器排队等待处理
- **同义词**：IRQ
- **相关**：Interrupt（中断）、Interrupt Controller（中断控制器）
### Memory-Mapped I/O (MMIO) / 内存映射 I/O
- **中文**：内存映射 I/O
- **定义**：见 operating-system/04-io-system.md
- **同义词**：MMIO
- **相关**：PMIO（端口映射 I/O）、I/O Address Space（I/O 地址空间）
### PCIe (Peripheral Component Interconnect Express) / PCI Express
- **中文**：PCI Express
- **定义**：高速串行点对点总线接口标准
- **说明**：PCIe 通道宽度 x1、x4、x8、x16 决定带宽；目前广泛用于显卡、NVMe SSD 等高速设备
- **同义词**：PCI Express
- **相关**：PCI（外围组件互联）、GPU、NVMe
### Plug and Play / 即插即用
- **中文**：即插即用
- **定义**：系统自动检测和配置硬件设备的机制，无需手动跳线或驱动
- **说明**：通过即插即用的 BIOS + 操作系统驱动自动分配 IRQ、I/O 地址等资源
- **同义词**：PnP
- **相关**：Device Driver（设备驱动）、BIOS
### Polling / 轮询
- **中文**：轮询
- **定义**：见 operating-system/04-io-system.md
- **同义词**：Polling
- **相关**：Interrupt（中断）
### Port-Mapped I/O (PMIO) / 端口映射 I/O
- **中文**：端口映射 I/O
- **定义**：见 operating-system/04-io-system.md
- **同义词**：PMIO
- **相关**：MMIO（内存映射 I/O）
### Programmed I/O / 程序控制 I/O
- **中文**：程序控制 I/O
- **定义**：见 operating-system/04-io-system.md
- **同义词**：PIO
- **相关**：DMA（直接内存访问）、Interrupt（中断）
### System Bus / 系统总线
- **中文**：系统总线
- **定义**：连接 CPU、内存和 I/O 的基本总线架构
- **同义词**：System Bus
- **相关**：Data Bus（数据总线）、Address Bus（地址总线）、Control Bus（控制总线）
