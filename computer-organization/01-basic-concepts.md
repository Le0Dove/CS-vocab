# 01. 基础概念 (Basic Concepts)
### Accumulator (ACC) / 累加器
- **音标**：/əˈkjuːmjəleɪtər/
- **中文**：累加器
- **定义**：CPU 中用于存储算术和逻辑运算结果的特殊寄存器
- **说明**：早期 CPU 以累加器为核心设计；单累加器架构中所有运算结果存入累加器；现代 CPU 有多通用寄存器替代
- **相关**：Register（寄存器）、ALU（算术逻辑单元）
### ALU (Arithmetic Logic Unit) / 算术逻辑单元
- **中文**：算术逻辑单元
- **定义**：CPU 中执行算术运算（加减乘除）和逻辑运算（与或非）的电路
- **说明**：ALU 接收操作数，根据控制信号选择运算（如 ADD、OR），输出结果和标志位（零、溢出、进位）
- **相关**：CPU、Control Unit（控制器）、Register（寄存器）
### BCD (Binary-Coded Decimal) / 二进制编码十进制
- **中文**：二进制编码十进制
- **定义**：每四位二进制表示一位十进制数（0-9）的编码方式
- **说明**：BCD 便于十进制数字输入输出和显示（计算器），但占用空间更大；1010-1111 无效
- **同义词**：BCD
- **相关**：Binary（二进制）、Decimal（十进制）
### Big Endian / 大端序
- **中文**：大端序
- **定义**：多字节数据的高位字节存储在低地址的字节序
- **说明**：网络字节序（网络传数据）使用大端序；Motorola 68000、网络字节序、部分 RISC 处理器；与 Little Endian 相反
- **同义词**：Big-Endian
- **相关**：Little Endian（小端序）、Byte Order（字节序）
### Bit / 比特
- **中文**：比特（位）
- **定义**：计算机数据的最小单位，取值为 0 或 1
- **说明**：8 比特 = 1 字节；比特是信息量的基本单位
- **相关**：Byte（字节）、Word（字）
### Byte / 字节
- **中文**：字节
- **定义**：由 8 个比特组成的数据单元
- **说明**：字节是大多数计算机寻址的最小单位；1 Byte = 8 Bits = 2 Nibbles（半字节）；KB、MB、GB 基于字节
- **相关**：Bit（比特）、Word（字）、Kilobyte（千字节）
### Clock Cycle / 时钟周期
- **中文**：时钟周期
- **定义**：计算机时钟信号的一个完整振荡周期
- **说明**：周期 = 1/频率（如 3GHz CPU 周期约 0.33ns）；一条指令可能需要多周期；CPI（每指令周期数）衡量性能
- **相关**：Clock Speed（时钟频率）、CPI、Instruction Cycle（指令周期）
### Clock Speed / 时钟频率
- **中文**：时钟频率（主频）
- **定义**：CPU 时钟每秒产生的周期数，单位为 Hz
- **说明**：现代 CPU 频率 2-5GHz；更高频率不直接等于更快（IPC 不同）；多核时代频率不再是最重要指标
- **相关**：Clock Cycle（时钟周期）、CPU、Overclocking（超频）
### CMOS (Complementary Metal-Oxide-Semiconductor) / 互补金属氧化物半导体
- **中文**：互补金属氧化物半导体
- **定义**：制造集成电路的主流半导体工艺；PC 中 CMOS 指存储 BIOS 设置的芯片
- **说明**：CMOS 功耗低、集成度高；CMOS 电池保持 RTC（实时时钟）和 BIOS 设置
- **相关**：BIOS、Transistor（晶体管）
### Combinational Logic / 组合逻辑
- **中文**：组合逻辑
- **定义**：输出仅取决于当前输入、无记忆功能的数字电路
- **说明**：常见组合逻辑：加法器、解码器、多路选择器；与 Sequential Logic 相对
- **相关**：Sequential Logic（时序逻辑）、Gate（门电路）
### Computer Architecture / 计算机体系结构
- **中文**：计算机体系结构
- **定义**：计算机系统的抽象设计，包括指令集、数据通路、控制单元的功能规范
- **说明**：与微体系结构（Microarchitecture）区分：架构是接口（程序员可见），微体系是具体实现
- **相关**：ISA（指令集架构）、CPU、Microarchitecture（微体系结构）
### Control Unit (CU) / 控制器
- **中文**：控制器
- **定义**：CPU 中指挥数据通路、控制指令执行的部件
- **说明**：控制器根据指令操作码产生控制信号（如 ALU 选择、寄存器写入使能）；分为硬布线（Hardwired）和微程序（Microprogrammed）
- **同义词**：CU
- **相关**：ALU（算术逻辑单元）、Data Path（数据通路）、CPU
### CPI (Cycles Per Instruction) / 每条指令时钟周期数
- **中文**：每条指令时钟周期数
- **定义**：执行一条指令平均所需的时钟周期数
- **说明**：CPI = 1/IPC（每周期指令数）；CPI 越低性能越好
- **相关**：Clock Cycle（时钟周期）、IPC
### CPU (Central Processing Unit) / 中央处理器
- **中文**：中央处理器
- **定义**：计算机的核心计算和控制部件，执行指令、处理数据
- **说明**：CPU 包含 ALU、控制单元、寄存器；现代 CPU 多核、多级缓存、支持超线程/超标量
- **相关**：ALU、Control Unit（控制器）、Register（寄存器）
### Data Path / 数据通路
- **中文**：数据通路
- **定义**：CPU 中数据流经的路径，包含寄存器、ALU、多路选择器、总线等
- **说明**：数据通路指不同指令执行周期中数据流动的路径；配合控制信号实现指令执行
- **同义词**：Datapath
- **相关**：Control Unit（控制器）、Bus（总线）、CPU
### Fetch-Decode-Execute Cycle / 取指-译码-执行循环
- **中文**：取指-译码-执行循环
- **定义**：CPU 的基本工作循环：从内存取出指令 → 译码确定操作 → 执行操作
- **说明**：现代 CPU 额外阶段：访存（Memory Access）、写回（Write Back）；流水线同时处理不同指令的不同阶段
- **同义词**：Instruction Cycle（指令周期）
- **相关**：Pipeline（流水线）、CPU、Instruction（指令）
### Firmware / 固件
- **中文**：固件
- **定义**：存储在非易失存储器（ROM、Flash）中的低级软件，直接控制硬件
- **说明**：BIOS/UEFI 是固件；固件可以更新（更新）；比操作系统更接近硬件
- **相关**：BIOS、UEFI、Driver（驱动）
### Flip-Flop / 触发器
- **中文**：触发器
- **定义**：具有两个稳定状态、可存储一比特数据的时序逻辑电路
- **说明**：D 触法器（边沿触发）是最常用的存储元件；寄存器由多个触法器构成；SRAM 存储单元基于触法器
- **同义词**：Bistable Multivibrator
- **相关**：Latch（锁存器）、Register（寄存器）、Sequential Logic（时序逻辑）
### Gate / 门（逻辑门）
- **中文**：逻辑门
- **定义**：实现基本布尔函数的基本数字电路单元
- **说明**：基本门：AND（与）、OR（或）、NOT（非）、NAND（与非）、NOR（或非）、XOR（异或）；NAND 门是通用门（Functional Completeness）
- **同义词**：Logic Gate（逻辑门）
- **相关**：Boolean Algebra（布尔代数）、Combinational Logic（组合逻辑）
### IPC (Instructions Per Cycle) / 每周期指令数
- **中文**：每周期指令数
- **定义**：每个时钟周期平均能完成的指令条数
- **说明**：IPC = 1/CPI；超标量处理器 IPC > 1；IPC 是衡量 CPU 微体系结构效率的指标
- **相关**：CPI、Superscalar（超标量）
### ISA (Instruction Set Architecture) / 指令集架构
- **中文**：指令集架构
- **定义**：CPU 支持的完整指令集和编程模型的抽象规范
- **说明**：ISA 定义：指令格式、寻址方式、寄存器、数据类型、异常处理；向下兼容；两大阵营：CISC（x86）和 RISC（ARM、RISC-V）
- **同义词**：ISA
- **相关**：CISC（复杂指令集计算机）、RISC（精简指令集计算机）
### Latency / 延迟
- **中文**：延迟
- **定义**：从发起到操作完成所需的时间
- **说明**：内存延迟（CAS Latency）、指令延迟等；低延迟对性能关键
- **相关**：Throughput（吞吐量）、Wait State（等待态）、Clock Cycle（时钟周期）
### Little Endian / 小端序
- **中文**：小端序
- **定义**：多字节数据的低位字节存储在低地址的字节序
- **说明**：x86/x64 处理器默认小端序；大多数 ARM 可切换；编程时需注意字节序导致的可移植性问题
- **同义词**：Little-Endian
- **相关**：Big Endian（大端序）、Byte Order（字节序）
### Memory Hierarchy / 存储层次
- **中文**：存储层次
- **定义**：从快而小到慢而大的多层存储结构（寄存器 → 缓存 → 主存 → 外存）
- **说明**：越靠近 CPU 速度越快、容量越小、成本越高；利用局部性原理提高平均访问速度
- **同义词**：Memory Hierarchy
- **相关**：Cache（高速缓存）、RAM、Temporal Locality（时间局部性）
### Microarchitecture / 微体系结构
- **中文**：微体系结构
- **定义**：指令集架构的具体硬件实现方式
- **说明**：同一 ISA 可有不同微体系结构（如 Intel Core vs AMD Zen 都实现 x86-64）；微体系包含流水线、缓存、分支预测等
- **相关**：ISA（指令集架构）、CPU、Pipeline（流水线）
### Microcode / 微码
- **中文**：微码
- **定义**：存储在 ROM 中的低级控制程序，将机器指令翻译为硬件控制信号
- **说明**：CISC 处理器常用微码实现复杂指令；微码可更新以修复 CPU Bug（微码更新）；RISC 通常不需要微码
- **同义词**：Microprogramming（微程序）
- **相关**：Control Unit（控制器）、Firmware（固件）
### Moore's Law / 摩尔定律
- **中文**：摩尔定律
- **定义**：Gordon Moore 1965 年的预测：集成电路上可容纳的晶体管数约每两年翻一倍
- **说明**：摩尔定律推动计算机行业几十年增长；近年晶体管密度增长放缓（物理极限）；已演变为"每美元计算能力"
- **相关**：CPU、Transistor（晶体管）、Dennard Scaling
### Nanometer (nm) / 纳米
- **中文**：纳米（制程）
- **定义**：半导体工艺的特征尺寸单位（如 5nm、3nm）
- **说明**：制程越小晶体管越密、功耗越低；但数字不等于物理晶体管尺寸；2024 年最先进制程 3nm/2nm
- **同义词**：Process Node（工艺节点）
- **相关**：Moore's Law（摩尔定律）、Transistor（晶体管）
### Register / 寄存器
- **中文**：寄存器
- **定义**：CPU 内部的高速存储单元，用于保存操作数和中间结果
- **说明**：寄存器是速度最快的存储器（<1ns 访问）；x86-64 有 16 个 64 位通用寄存器；PC（程序计数器）、SP（栈指针）是特殊寄存器
- **同义词**：Register
- **相关**：CPU、Cache（高速缓存）、Latch（锁存器）
### Sequential Logic / 时序逻辑
- **中文**：时序逻辑
- **定义**：输出不仅取决于当前输入，还与历史状态有关的数字电路
- **说明**：触法器、寄存器、计数器、状态机都是时序逻辑；通过时钟信号同步状态变迁；具有记忆功能
- **同义词**：Sequential Circuit（时序电路）
- **相关**：Combinational Logic（组合逻辑）、Clock（时钟）、Flip-Flop（触发器）
### Stored-Program Concept / 存储程序概念
- **中文**：存储程序概念
- **定义**：将程序指令和数据都存储在相同内存中的计算机设计原则
- **说明**：冯·诺依曼架构的核心思想；使得程序可以动态加载和修改；与哈佛架构（指令和数据分离）对比
- **同义词**：von Neumann Concept（冯·诺依曼概念）
- **相关**：von Neumann Architecture（冯·诺依曼架构）、Harvard Architecture（哈佛架构）
### Transistor / 晶体管
- **中文**：晶体管
- **定义**：现代电子学的基本构建块，可放大或开关电信号的半导体器件
- **说明**：MOSFET 是数字电路最常用的晶体管；数十亿晶体管集成在 CPU 中；栅极控制源极和漏极间的导电性
- **相关**：CMOS、Integrated Circuit（集成电路）、Moore's Law（摩尔定律）
### von Neumann Architecture / 冯·诺依曼架构
- **中文**：冯·诺依曼架构
- **定义**：程序和数据共享同一存储器和总线的计算机架构
- **说明**：五大部分：输入设备、输出设备、存储器、控制器、运算器；指令和数据使用同一总线（von Neumann Bottleneck）
- **同义词**：Princeton Architecture（普林斯顿架构）
- **相关**：Harvard Architecture（哈佛架构）、CPU、Stored-Program Concept（存储程序概念）
### Word / 字
- **中文**：字
- **定义**：计算机中作为整体处理的数据单位，通常等于 CPU 通用寄存器宽度
- **说明**：32 位系统字长 = 32 位 = 4 字节；64 位系统字长 = 64 位 = 8 字节
- **同义词**：Word Size（字长）
- **相关**：Byte（字节）、Bit（比特）、Register（寄存器）
