# 03. CPU 架构与指令集 (CPU Architecture & Instruction Set)
### Addressing Mode / 寻址方式
- **中文**：寻址方式
- **定义**：指令中指定操作数位置的方式
- **说明**：立即寻址（操作数直接在指令中）、直接寻址、寄存器寻址、间接寻址、基址+偏移寻址、变址寻址等
- **相关**：ISA（指令集架构）、Operand（操作数）、Register（寄存器）
### Branch Prediction / 分支预测
- **中文**：分支预测
- **定义**：CPU 猜测条件分支指令走向，提前取指令执行以避免流水线停顿
- **说明**：分支预测正确率 > 95%，对高性能 CPU 至关重要
- **相关**：Pipeline（流水线）、Speculative Execution（推测执行）
### CISC (Complex Instruction Set Computer) / 复杂指令集计算机
- **中文**：复杂指令集计算机
- **定义**：指令数量多、指令长度可变、单条指令功能复杂的 CPU 架构
- **说明**：x86/x86-64 是 CISC 的代表（内部做与 RISC 类似的解码）
- **相关**：RISC（精简指令集计算机）、ISA
### Coprocessor / 协处理器
- **中文**：协处理器
- **定义**：辅助主 CPU 完成特定功能（如浮点运算、图形处理）的处理器
- **说明**：早期的 FPU 是协处理器；现代 GPU 可视为协处理器；已集成到 SOC
- **相关**：CPU、FPU、GPU
### Data Hazard / 数据冒险
- **中文**：数据冒险
- **定义**：流水线中某条指令依赖于前一条的结果还未完成而产生停顿
- **说明**：RAW（读后写）、WAW（写后写）、WAR（写后读）这三种数据相关类型中，流水线主要考虑 RAW，解决方案有转发、流水线互锁和编译器调度
- **同义词**：Data Hazard
- **相关**：Pipeline（流水线）、Hazard（冒险）、Control Hazard（控制冒险）
### EPIC (Explicitly Parallel Instruction Computing) / 显式并行指令计算
- **中文**：显式并行指令计算
- **定义**：由编译器显式编码指令级并行性的架构（如 Intel Itanium）
- **说明**：比 VLIW 更灵活
- **相关**：VLIW、Superscalar（超标量）
### FPU (Floating-Point Unit) / 浮点运算单元
- **中文**：浮点运算单元
- **定义**：专门进行浮点数算术运算的处理单元
- **说明**：早期为协处理器（x87），现在集成在 CPU 中；支持 IEEE 754
- **相关**：ALU（算术逻辑单元）、Floating-Point（浮点数）
### GPU (Graphics Processing Unit) / 图形处理单元
- **中文**：图形处理单元
- **定义**：最初专用于图形渲染、现广泛用于通用并行计算（GPGPU）的多核处理器
- **说明**：GPU 有数千个核心但每个核心简单；CUDA/OpenCL 用于科学计算、AI 训练和推理
- **同义词**：GPU
- **相关**：CPU、CUDA、GPGPU
### Harvard Architecture / 哈佛架构
- **中文**：哈佛架构
- **定义**：指令和数据使用独立的存储器和总线
- **说明**：指令和数据分存储，避免冲突；适合 DSP 和嵌入式微控制器
- **同义词**：Harvard Architecture
- **相关**：von Neumann Architecture（冯·诺依曼架构）
### Instruction Set / 指令集
- **中文**：指令集
- **定义**：CPU 能理解和执行的所有机器指令的集合
- **相关**：ISA、Opcode（操作码）、Instruction（指令）
### Interrupt / 中断
- **中文**：中断
- **定义**：硬件或软件信号，通知 CPU 暂停当前执行转到中断服务程序（ISR）
- **说明**：分为可屏蔽中断和不可屏蔽中断（NMI）
- **相关**：Exception（异常）、Interrupt Vector（中断向量）
### MIMD (Multiple Instruction Multiple Data) / 多指令多数据流
- **中文**：多指令多数据流
- **定义**：多个处理器各自执行自己的指令处理各自的数据
- **说明**：大多数现代多核处理器是 MIMD 架构
- **相关**：SIMD、SMP
### MMX (MultiMedia eXtension) / 多媒体扩展
- **中文**：多媒体扩展
- **定义**：Intel 早期引入的 SIMD 指令集
- **说明**：MMX 已被 SSE 和 AVX 取代
- **同义词**：MMX
- **相关**：SSE、AVX、SIMD
### Multicore / 多核
- **中文**：多核
- **定义**：在单个 CPU 芯片上集成多个处理器核心
- **说明**：双核、四核、八核等；每个核心可以独立执行指令
- **同义词**：Multi-core
- **相关**：SMP（对称多处理）、Multithreading（多线程）
### Multithreading / 多线程（硬件）
- **中文**：多线程（硬件）
- **定义**：同一核心同时运行多个线程的硬件技术
- **说明**：超线程（Hyper-Threading 是一种 SMT（同时多线程）；通过重复的寄存器文件让多个线程共享执行单元提高利用率
- **同义词**：SMT（Simultaneous Multithreading）
- **相关**：Hyper-Threading（超线程）、Pipeline（流水线）
### Opcode / 操作码
- **中文**：操作码
- **定义**：机器指令中指定操作类型的字段（如 ADD、MOV、JMP）
- **说明**：操作码+操作数=完整指令
- **相关**：Operand（操作数）、Instruction（指令）、ISA
### Operand / 操作数
- **中文**：操作数
- **定义**：指令中指定参与运算的数据的量
- **说明**：操作数可以是寄存器、立即数、内存地址
- **相关**：Opcode（操作码）、Instruction（指令）
### Out-of-Order Execution / 乱序执行
- **中文**：乱序执行
- **定义**：CPU 不严格按照指令在程序中的顺序，而是根据操作数就绪情况动态调度执行
- **说明**：乱序执行在数据准备好了就执行，减少流水线停顿；提交指令时按原顺序提交
- **同义词**：OoO（Out-of-Order）
- **相关**：Pipeline（流水线）、Data Hazard（数据冒险）
### Pipeline / 流水线
- **中文**：流水线
- **定义**：将一条指令的执行拆分为多个阶段，不同指令的不同阶段同时进行的并行技术
- **说明**：经典五级流水线：取指 → 译码 → 执行 → 访存 → 写回
- **相关**：Hazard（冒险）、Superscalar（超标量）
### Register File / 寄存器堆
- **中文**：寄存器堆
- **定义**：CPU 内部集成的一组高速寄存器
- **说明**：每个寄存器由专门的触法器组成，访问速度极快
- **相关**：Register（寄存器）、CPU
### RISC (Reduced Instruction Set Computer) / 精简指令集计算机
- **中文**：精简指令集计算机
- **定义**：指令数量较少、格式固定、单条指令功能简单的 CPU 架构
- **说明**：RISC 通常支持 Load/Store 架构（只通过 load 和 store 指令访问内存）；ARM、RISC-V 是 RISC
- **同义词**：RISC
- **相关**：CISC（复杂指令集计算机）、ISA
### SIMD (Single Instruction Multiple Data) / 单指令多数据
- **中文**：单指令多数据
- **定义**：一条指令同时对多个数据执行相同操作的并行计算技术
- **说明**：SIMD 用向量寄存器（如 SSE 128 位、AVX 256 位、AVX-512 512 位）处理数据；广泛用于多媒体处理、科学计算、AI 推理
- **同义词**：Vector Processing（向量处理）
- **相关**：SSE、AVX、MIMD（多指令多数据流）
### Speculative Execution / 推测执行
- **中文**：推测执行
- **定义**：CPU 在不确定条件分支结果的情况下，按预测方向预先执行指令
- **说明**：分支预测正确时推测执行大幅提升性能；预测错误时需要回退（Rollback）
- **同义词**：Speculative Execution
- **相关**：Branch Prediction（分支预测）、Pipeline（流水线）
### SSE (Streaming SIMD Extensions) / 流式 SIMD 扩展
- **中文**：流式 SIMD 扩展
- **定义**：Intel 的 SIMD 指令集扩展，操作 128 位 XMM 寄存器
- **说明**：SSE 经过 SSE2、SSE3、SSSE3、SSE4.x 迭代；广泛应用于多媒体、浮点密集计算
- **同义词**：SSE
- **相关**：AVX、SIMD
### Stack Pointer (SP) / 栈指针
- **中文**：栈指针
- **定义**：指向内存栈顶的特殊寄存器
- **说明**：PUSH 指令先递减 SP 再写数，POP 指令先读数再递加 SP；现代 CPU 中有独立的栈指针寄存器
- **同义词**：SP
- **相关**：Stack（栈）、Program Counter（程序计数器）
### Status Register / 状态寄存器
- **中文**：状态寄存器
- **定义**：存储 CPU 当前状态标志的特殊寄存器
- **说明**：标志位包括零标志 ZF、进位标志 CF、符号标志 SF、溢出标志 OF 等；条件分支指令根据标志位决定是否跳转
- **同义词**：Flag Register（标志寄存器）、Program Status Word (PSW)
- **相关**：ALU（算术逻辑单元）、Branch（分支）
### Superscalar / 超标量
- **中文**：超标量
- **定义**：一个时钟周期内能够发射并执行多条指令的微体系结构
- **说明**：超标量处理器通过多个执行单元实现 IPC > 1；需要编译器指令调度和硬件动态调度
- **同义词**：Superscalar
- **相关**：Pipeline（流水线）、Out-of-Order Execution（乱序执行）
### VLIW (Very Long Instruction Word) / 超长指令字
- **中文**：超长指令字
- **定义**：一条超长指令包含多个可以同时执行的独立操作
- **说明**：编译器静态调度并行性（与超标量不同）；Intel Itanium 是 VLIW 的变体
- **同义词**：VLIW
- **相关**：EPIC、Superscalar（超标量）
