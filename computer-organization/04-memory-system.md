# 04. 存储系统 (Memory System)
### Access Time / 访问时间
- **中文**：访问时间
- **定义**：从发出地址到数据就绪所需的时间
- **说明**：内存访问时间（约 50ns）、缓存访问时间（1-5ns）
- **相关**：Memory Latency（内存延迟）、Hit Time（命中时间）
### Address Decoder / 地址译码器
- **中文**：地址译码器
- **定义**：将 CPU 发出的内存地址转换为选中某个存储单元芯片的信号的电路
- **说明**：通过地址位确定芯片选择信号（CS）和行列选择线；配合多路复用器（MUX）完成寻址和数据输出
- **同义词**：Address Decoder
- **相关**：RAM、Memory Controller（内存控制器）
### Associative Memory / 相联存储器
- **中文**：相联存储器
- **定义**：不按地址而是根据内容特征搜索并取出数据的存储器
- **说明**：相联存储器用于 Cache 的 Tag 查找、TLB（Translation Lookaside Buffer）；并行对比所有条目，命中后输出数据和匹配信号
- **同义词**：CAM (Content-Addressable Memory)
- **相关**：Cache（高速缓存）、TLB（转换后备缓冲器）
### Cache / 高速缓存
- **中文**：高速缓存
- **定义**：见 operating-system/02-memory-management.md
- **相关**：Cache Hit（缓存命中）、Cache Miss（缓存未命中）
### Capacity Miss / 容量未命中
- **中文**：容量未命中
- **定义**：缓存容量不足以容纳程序当前工作集导致的未命中
- **说明**：增加缓存大小可减少
- **相关**：Compulsory Miss（强制未命中）、Conflict Miss（冲突未命中）
### CAS Latency / CAS 延迟
- **中文**：CAS 延迟
- **定义**：DRAM 列地址选通脉冲的延迟周期数
- **说明**：内存时序参数如 CL16-18-18-38 中第一个数为 CAS 延迟；CAS 延迟越低越快
- **同义词**：CL
- **相关**：DRAM（动态随机存取存储器）、Memory Latency（内存延迟）
### Compulsory Miss / 强制未命中
- **中文**：强制未命中
- **定义**：首次引用某地址时，该地址数据尚未进入缓存导致的不可避免的未命中
- **同义词**：Cold Miss（冷未命中）
- **相关**：Capacity Miss（容量未命中）、Conflict Miss（冲突未命中）
### Conflict Miss / 冲突未命中
- **中文**：冲突未命中
- **定义**：多个内存块映射到同一缓存位置导致互相驱逐引起的未命中
- **说明**：直接映射缓存冲突未命中严重；增加相联度可减少冲突未命中
- **同义词**：Collision Miss
- **相关**：Capacity Miss（容量未命中）、Compulsory Miss（强制未命中）
### DDR (Double Data Rate) / 双倍数据速率
- **中文**：双倍数据速率
- **定义**：在时钟上升沿和下降沿都传输数据的 SDRAM 标准
- **说明**：DDR → DDR2 → DDR3 → DDR4 → DDR5（每一代速率提高、电压降低）；DDR5 带宽可达 51.2 GB/s
- **同义词**：DDR SDRAM
- **相关**：DRAM（动态随机存取存储器）、Memory Bandwidth（内存带宽）
### Direct-Mapped Cache / 直接映射缓存
- **中文**：直接映射缓存
- **定义**：每个内存块只能映射到唯一确定的缓存行
- **说明**：实现最简单、速度快，但冲突未命中最多
- **相关**：Fully-Associative Cache（全相联缓存）、Set-Associative Cache（组相联缓存）
### DRAM (Dynamic RAM) / 动态随机存取存储器
- **中文**：动态随机存取存储器
- **定义**：见 operating-system/02-memory-management.md
- **同义词**：DRAM
- **相关**：SRAM（静态随机存取存储器）、Memory（内存）
### Dual-Channel / 双通道
- **中文**：双通道
- **定义**：同时使用两条内存通道提高带宽的技术
- **说明**：双通道内存带宽翻倍，但需要成对匹配的内存条；四通道、八通道用于高性能场景
- **同义词**：Dual Channel
- **相关**：Memory Bandwidth（内存带宽）
### ECC (Error-Correcting Code) / 纠错码
- **中文**：纠错码
- **定义**：可检测并纠正存储或传输中错误比特的编码技术
- **说明**：ECC 内存能纠正单比特错误、检测双比特错误（SEC-DED）；服务器和数据中心必须使用 ECC
- **同义词**：ECC Memory（ECC 内存）
- **相关**：Parity Bit（奇偶校验位）、Error Detection（错误检测）
### Flash Memory / 闪存
- **中文**：闪存
- **定义**：见 operating-system/03-file-system.md
- **同义词**：Flash Memory
- **相关**：SSD、NAND
### Fully-Associative Cache / 全相联缓存
- **中文**：全相联缓存
- **定义**：任何内存块可映射到任意缓存行
- **说明**：冲突未命中最少，但全硬件并行查找复杂，只适合小容量 TLB
- **相关**：Direct-Mapped Cache（直接映射缓存）、Set-Associative Cache（组相联缓存）
### Hard Disk Drive (HDD) / 硬盘驱动器
- **中文**：硬盘驱动器
- **定义**：见 operating-system/03-file-system.md
- **同义词**：HDD
- **相关**：SSD、Storage（存储）
### Locality / 局部性
- **中文**：局部性
- **定义**：见 operating-system/02-memory-management.md
- **同义词**：Locality
- **相关**：Cache（高速缓存）、Temporal Locality（时间局部性）
### Magnetic Disk / 磁盘
- **中文**：磁盘
- **定义**：利用磁性材料存储数据的高速旋转盘片
- **说明**：磁道（Track）、扇区（Sector）、柱面（Cylinder）组织数据；有旋转延迟和寻道时间；已逐渐被 SSD 取代
- **同义词**：Hard Disk（磁盘）
- **相关**：SSD、Sector（扇区）、Track（磁道）
### Memory Bus / 内存总线
- **中文**：内存总线
- **定义**：连接 CPU（或内存控制器）与主存的传输通道
- **说明**：内存总线宽度影响数据传输速率；双通道即同时使用两条独立总线提高带宽
- **同义词**：Memory Bus
- **相关**：Memory Controller（内存控制器）、Front-Side Bus
### Memory Controller / 内存控制器
- **中文**：内存控制器
- **定义**：管理 CPU 与主存之间数据流访问的逻辑电路
- **说明**：现代 CPU 集成内存控制器以降低延迟；刷新 DRAM、调度请求是控制器核心功能
- **同义词**：Memory Controller
- **相关**：Memory Bus（内存总线）、DRAM（动态随机存取存储器）
### MMU (Memory Management Unit) / 内存管理单元
- **中文**：内存管理单元
- **定义**：见 operating-system/02-memory-management.md
- **同义词**：MMU
- **相关**：TLB（转换后备缓冲器）、Page Table（页表）
### NAND Flash / NAND 闪存
- **中文**：NAND 闪存
- **定义**：见 operating-system/03-file-system.md
- **同义词**：NAND
- **相关**：SSD、Flash Memory（闪存）
### Page / 页
- **中文**：页
- **定义**：内存管理中将虚拟地址空间划分为固定大小的块
- **说明**：虚拟内存以页为单位映射到物理内存页框；页大小通常 4KB；大页面（2MB/1GB）提高 TLB 覆盖
- **同义词**：Page
- **相关**：Page Table（页表）、TLB（转换后备缓冲器）
### Page Table / 页表
- **中文**：页表
- **定义**：见 operating-system/02-memory-management.md
- **同义词**：Page Table
- **相关**：MMU（内存管理单元）、TLB（转换后备缓冲器）
### ROM (Read-Only Memory) / 只读存储器
- **中文**：只读存储器
- **定义**：见 operating-system/02-memory-management.md
- **同义词**：ROM
- **相关**：Firmware（固件）、BIOS
### Set-Associative Cache / 组相联缓存
- **中文**：组相联缓存
- **定义**：每个组内全相联组间直接映射的折中缓存结构
- **说明**：n 路组相联缓存（如 8-way）是实际 CPU 缓存的常用设计；适度减少冲突未命中
- **同义词**：Set-Associative
- **相关**：Direct-Mapped Cache（直接映射缓存）、Fully-Associative Cache（全相联缓存）
### SRAM (Static RAM) / 静态随机存取存储器
- **中文**：静态随机存取存储器
- **定义**：见 operating-system/02-memory-management.md
- **同义词**：SRAM
- **相关**：Cache（高速缓存）、DRAM（动态随机存取存储器）
### SSD (Solid State Drive) / 固态驱动器
- **中文**：固态驱动器
- **定义**：见 operating-system/03-file-system.md
- **同义词**：SSD
- **相关**：NAND Flash、HDD
### TLB (Translation Lookaside Buffer) / 转换后备缓冲器
- **中文**：转换后备缓冲器
- **定义**：页表条目的专用高速缓存，加速虚拟地址到物理地址的转换
- **说明**：TLB 每核心独立，容量较小（几十到几百项）；TLB 命中可避免访问内存页表
- **同义词**：TLB
- **相关**：MMU（内存管理单元）、Page Table（页表）
### Virtual Memory / 虚拟内存
- **中文**：虚拟内存
- **定义**：见 operating-system/02-memory-management.md
- **同义词**：Virtual Memory
- **相关**：Page Table（页表）、MMU（内存管理单元）
### Write-Back / 写回
- **中文**：写回
- **定义**：写操作只更新缓存，仅在被替换时才写回主存
- **说明**：写回性能高但需要脏位（Dirty Bit）跟踪；多核环境下需要缓存一致性协议
- **同义词**：Write-Back
- **相关**：Write-Through（写直达）、Cache（高速缓存）
### Write-Through / 写直达
- **中文**：写直达
- **定义**：写操作同时更新缓存和主存
- **说明**：写直达实现简单、一致性好但性能较低；通常配合写缓冲区使用
- **同义词**：Write-Through
- **相关**：Write-Back（写回）、Cache（高速缓存）
