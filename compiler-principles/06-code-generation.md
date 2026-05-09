# 06. 代码生成 (Code Generation)

## 目标代码

### Assembly Code / 汇编代码
- **中文**：汇编代码
- **定义**：机器指令的文本表示，使用助记符和操作数
- **说明**：与机器码一一对应；需通过汇编器转换为机器码；是编译器常用的目标代码形式；便于阅读和调试
- **相关**：Machine Code（机器码）、Assembler（汇编器）、Instruction（指令）

### Code Emitter / 代码发射器
- **中文**：代码发射器
- **定义**：编译器中负责输出目标代码（汇编或机器码）的组件
- **说明**：接收指令选择后的中间表示；生成特定目标架构的指令序列；处理指令格式和编码
- **相关**：Code Generation（代码生成）、Instruction Selection（指令选择）、Target Code（目标代码）

### Code Generation / 代码生成
- **中文**：代码生成
- **定义**：将中间表示转换为目标机器代码（汇编或机器码）的编译阶段
- **说明**：主要任务：指令选择（选择最优机器指令）、寄存器分配、指令调度、地址计算；需考虑目标 ISA 特性
- **相关**：IR（中间表示）、Instruction Selection（指令选择）、Register Allocation（寄存器分配）

### Executable / 可执行文件
- **中文**：可执行文件
- **定义**：可被操作系统加载并运行的程序文件
- **说明**：格式：ELF（Linux）、PE（Windows）、Mach-O（macOS）；包含：代码段、数据段、符号表、重定位信息；由链接器生成
- **相关**：Object File（目标文件）、Linker（链接器）、Loader（加载器）

### Instruction Selection / 指令选择
- **中文**：指令选择
- **定义**：将中间代码操作映射到目标机器指令序列的过程
- **说明**：需考虑指令功能、成本和约束；方法：树模式匹配（如 BURS）、基于规则的覆盖、动态规划；LLVM 使用 SelectionDAG
- **相关**：Code Generation（代码生成）、Peephole Optimization（窥孔优化）、Instruction Pattern（指令模式）

### Instruction Set Architecture (ISA) / 指令集架构
- **中文**：指令集架构
- **定义**：CPU 支持的指令集、寄存器、数据类型和寻址方式的抽象规范
- **说明**：代表：x86、ARM、RISC-V、MIPS；编译器后端依赖目标 ISA；ISA 分为 CISC（复杂指令集）和 RISC（精简指令集）
- **同义词**：ISA
- **相关**：CPU、Assembly Language（汇编语言）、Microarchitecture（微体系结构）

### Machine Code / 机器码
- **中文**：机器码
- **定义**：CPU 可直接执行的二进制指令序列
- **说明**：是编译的最终输出；与硬件架构绑定；人类不可读；通过汇编器或编译器直接生成
- **相关**：Assembly Code（汇编代码）、Instruction（指令）、Binary（二进制）

### Object Code / 目标代码
- **中文**：目标代码
- **定义**：编译器生成的、尚未链接的机器码或汇编代码
- **说明**：包含未解析的外部符号引用；需要链接器处理才能成为可执行文件；格式通常为 ELF/PE/Mach-O
- **相关**：Machine Code（机器码）、Linker（链接器）、Object File（目标文件）

### Target Architecture / 目标架构
- **中文**：目标架构
- **定义**：编译器生成代码所针对的硬件平台
- **说明**：包括：CPU 架构（x86、ARM）、操作系统（Linux、Windows）、ABI（应用程序二进制接口）；交叉编译针对不同目标架构
- **相关**：ISA（指令集架构）、Cross Compiler（交叉编译器）、ABI

### Target Code / 目标代码
- **中文**：目标代码
- **定义**：编译器生成的、针对特定目标机器的代码
- **说明**：可以是汇编代码或机器码；需经过汇编和链接才能成为可执行程序；优化的最终产物
- **相关**：Code Generation（代码生成）、Machine Code（机器码）、Assembly Code（汇编代码）

## 寄存器分配

### Caller-Saved Register / 调用者保存寄存器
- **中文**：调用者保存寄存器
- **定义**：函数调用时由调用者负责保存和恢复的寄存器
- **说明**：被调用函数可自由使用；调用者若需要寄存器值，需在调用前保存、返回后恢复；如 x86 的 EAX、ECX、EDX
- **同义词**：Volatile Register（易变寄存器）
- **相关**：Callee-Saved Register（被调用者保存寄存器）、Calling Convention（调用约定）、Register（寄存器）

### Callee-Saved Register / 被调用者保存寄存器
- **中文**：被调用者保存寄存器
- **定义**：函数调用时由被调用函数负责保存和恢复的寄存器
- **说明**：函数若使用这些寄存器，需在入口保存、出口恢复；保证调用前后值不变；如 x86 的 EBX、ESI、EDI
- **同义词**：Non-Volatile Register（非易变寄存器）
- **相关**：Caller-Saved Register（调用者保存寄存器）、Calling Convention（调用约定）、Register（寄存器）

### Calling Convention / 调用约定
- **中文**：调用约定
- **定义**：规定函数调用时参数传递、寄存器使用和栈管理的标准
- **说明**：包括：参数传递顺序（栈或寄存器）、返回值位置、哪些寄存器调用者/被调用者保存、栈清理责任；常见：cdecl、stdcall、fastcall、System V AMD64 ABI
- **相关**：ABI、Function Call（函数调用）、Stack Frame（栈帧）

### Chaitin's Algorithm / Chaitin 算法
- **中文**：Chaitin 算法
- **定义**：基于图着色的全局寄存器分配算法
- **说明**：将寄存器分配建模为图着色问题；节点：变量；边：同时活跃的变量；颜色：寄存器；若图不可着色则溢出（Spill）变量到内存
- **相关**：Register Allocation（寄存器分配）、Graph Coloring（图着色）、Spill（溢出）

### Graph Coloring / 图着色
- **中文**：图着色
- **定义**：给图的顶点分配颜色、使相邻顶点颜色不同的组合优化问题
- **说明**：寄存器分配中：节点=变量，边=冲突（同时活跃），颜色=寄存器；NP 完全问题；使用启发式算法近似求解
- **相关**：Register Allocation（寄存器分配）、Chaitin's Algorithm、NP-Complete（NP 完全）

### Live Range / 活跃区间
- **中文**：活跃区间
- **定义**：变量从定义到最后一次使用之间的程序区间
- **说明**：活跃区间分析是寄存器分配的基础；两个变量活跃区间重叠则冲突（不能分配同一寄存器）；区间可拆分以优化分配
- **相关**：Register Allocation（寄存器分配）、Live Variable（活跃变量）、Interval（区间）

### Register / 寄存器
- **中文**：寄存器
- **定义**：CPU 内部的高速存储单元，用于保存操作数和中间结果
- **说明**：通用寄存器（用于计算）和特殊寄存器（PC、SP 等）；数量有限（如 x86-64 有 16 个通用寄存器）；寄存器分配是编译优化的关键
- **相关**：CPU、Register Allocation（寄存器分配）、Memory（内存）

### Register Allocation / 寄存器分配
- **中文**：寄存器分配
- **定义**：将程序中的变量映射到有限的 CPU 寄存器的编译过程
- **说明**：方法：局部寄存器分配（基本块内）、全局寄存器分配（函数范围）；算法：图着色、线性扫描；寄存器不足时将变量溢出（Spill）到栈
- **相关**：Graph Coloring（图着色）、Spill（溢出）、Live Variable（活跃变量）

### Register Pressure / 寄存器压力
- **中文**：寄存器压力
- **定义**：程序某点同时活跃的变量数量与可用寄存器数量的比值
- **说明**：寄存器压力高时需将变量溢出到内存；降低寄存器压力的方法：减少同时活跃的变量、拆分活跃区间、重新计算而非存储
- **相关**：Register Allocation（寄存器分配）、Spill（溢出）、Live Variable（活跃变量）

### Spill / 溢出
- **中文**：溢出
- **定义**：当寄存器不足时、将变量值临时存储到内存（栈）的操作
- **说明**：增加内存访问开销（Load/Store）；编译器尽量避免溢出；选择溢出代价最小的变量（使用频率低、不在内层循环）
- **相关**：Register Allocation（寄存器分配）、Memory Access（内存访问）、Stack（栈）

## 指令与内存

### Addressing Mode / 寻址方式
- **中文**：寻址方式
- **定义**：指令指定操作数位置的方法
- **说明**：常见方式：立即寻址（操作数在指令中）、寄存器寻址（操作数在寄存器中）、直接寻址（操作数地址在指令中）、间接寻址（地址在寄存器/内存中）、基址+偏移寻址、变址寻址
- **相关**：Instruction（指令）、Operand（操作数）、Memory（内存）

### Alignment / 对齐
- **中文**：对齐
- **定义**：数据在内存中按特定地址边界存储的要求
- **说明**：如 4 字节整数应存储在 4 的倍数地址；未对齐访问可能性能下降（x86）或触发异常（ARM）；编译器自动插入填充（Padding）
- **相关**：Memory（内存）、Data Layout（数据布局）、Padding（填充）

### Branch / 分支
- **中文**：分支
- **定义**：改变程序执行顺序、跳转到另一地址的指令
- **说明**：条件分支（Conditional Branch）：根据条件跳转（如 if）；无条件分支（Unconditional Branch）：总是跳转（如 goto）；分支预测影响性能
- **相关**：Control Flow（控制流）、Branch Prediction（分支预测）、Jump（跳转）

### Branch Prediction / 分支预测
- **中文**：分支预测
- **定义**：CPU 猜测条件分支的走向、提前执行预测路径的硬件机制
- **说明**：预测正确提升性能，预测错误需刷新流水线；静态预测（编译器提示）和动态预测（硬件历史表）；编译器可生成利于预测的代码
- **相关**：Branch（分支）、Pipeline（流水线）、CPU

### Instruction Scheduling / 指令调度
- **中文**：指令调度
- **定义**：重排指令顺序以减少流水线停顿、提高指令级并行的优化
- **说明**：列表调度是基本算法；考虑数据依赖、功能单元可用性、延迟；现代 CPU 乱序执行减少了编译时调度的必要性
- **相关**：Pipeline（流水线）、Data Dependency（数据依赖）、Optimization（优化）

### Memory Hierarchy / 存储层次
- **中文**：存储层次
- **定义**：从快到慢的多层存储结构（寄存器 → 缓存 → 内存 → 磁盘）
- **说明**：编译器优化需考虑存储层次：寄存器分配（最快）、缓存优化（局部性）、内存访问对齐；影响代码性能
- **相关**：Cache（高速缓存）、Register（寄存器）、Optimization（优化）

### Memory Operand / 内存操作数
- **中文**：内存操作数
- **定义**：指令中引用内存位置的参数
- **说明**：比寄存器操作数慢；涉及地址计算和内存访问；编译器尽量将频繁使用的变量分配到寄存器
- **相关**：Register Operand（寄存器操作数）、Addressing Mode（寻址方式）、Memory Access（内存访问）

### Operand / 操作数
- **中文**：操作数
- **定义**：指令操作的数据或数据位置
- **说明**：类型：寄存器操作数、内存操作数、立即数操作数（常量）；指令格式由操作码和操作数组成
- **相关**：Instruction（指令）、Addressing Mode（寻址方式）、Register（寄存器）

### Stack Frame / 栈帧
- **中文**：栈帧
- **定义**：函数调用时在运行时栈上分配的内存区域，存储局部变量、参数和返回地址
- **说明**：结构：返回地址、保存的寄存器、局部变量、参数；进入函数时建立（prologue），退出时销毁（epilogue）；由基址指针（BP）和栈指针（SP）管理
- **同义词**：Activation Record（活动记录）
- **相关**：Stack（栈）、Function Call（函数调用）、Calling Convention（调用约定）

## 运行时支持

### ABI (Application Binary Interface) / 应用程序二进制接口
- **中文**：应用程序二进制接口
- **定义**：定义程序模块间二进制接口的标准，包括调用约定、数据类型、系统调用接口等
- **说明**：ABI 保证不同编译器生成的目标文件可链接；包括：函数调用约定、寄存器使用、栈布局、名称修饰（Name Mangling）；与 API 不同，ABI 是二进制级别的
- **相关**：API、Calling Convention（调用约定）、Object File（目标文件）

### Dynamic Linking / 动态链接
- **中文**：动态链接
- **定义**：程序运行时加载和链接共享库的技术
- **说明**：可执行文件小、共享库可更新、节省内存（多个进程共享同一份库代码）；启动稍慢；代表：.so（Linux）、.dll（Windows）、.dylib（macOS）
- **相关**：Static Linking（静态链接）、Shared Library（共享库）、Loader（加载器）

### Garbage Collection (GC) / 垃圾回收
- **中文**：垃圾回收
- **定义**：自动回收程序不再使用的内存空间的机制
- **说明**：算法：标记-清除（Mark-Sweep）、复制（Copying）、标记-整理（Mark-Compact）、引用计数（Reference Counting）、分代收集（Generational）；语言：Java、Go、C#、Python
- **同义词**：GC
- **相关**：Memory Management（内存管理）、Heap（堆）、Reference（引用）

### Heap / 堆
- **中文**：堆
- **定义**：程序运行时动态分配内存的区域
- **说明**：分配：malloc/new，释放：free/delete；生存期由程序员控制（或垃圾回收器）；与栈不同，堆分配无固定模式
- **相关**：Stack（栈）、Memory Allocation（内存分配）、Garbage Collection（垃圾回收）

### Memory Allocation / 内存分配
- **中文**：内存分配
- **定义**：为程序变量和数据结构分配内存空间的过程
- **说明**：静态分配（编译时确定）、栈分配（函数调用时自动）、堆分配（运行时手动/自动）；分配策略影响性能和内存碎片
- **相关**：Heap（堆）、Stack（栈）、Garbage Collection（垃圾回收）

### Memory Layout / 内存布局
- **中文**：内存布局
- **定义**：程序在内存中的组织方式，包括代码段、数据段、堆、栈等区域
- **说明**：文本段（代码）、数据段（全局/静态变量）、BSS 段（未初始化全局变量）、堆（动态分配）、栈（函数调用）；编译器和链接器决定布局
- **相关**：Segment（段）、Linker（链接器）、Loader（加载器）

### Runtime / 运行时
- **中文**：运行时
- **定义**：程序执行期间提供支持服务的库和环境
- **说明**：包括：内存管理（分配/回收）、异常处理、类型信息（RTTI）、垃圾回收、线程管理；C 运行时（CRT）、Java 运行时（JRE）
- **相关**：Runtime Library（运行时库）、Memory Management（内存管理）、Execution（执行）

### Stack / 栈
- **中文**：栈
- **定义**：用于函数调用管理的后进先出（LIFO）内存区域
- **说明**：存储：返回地址、函数参数、局部变量、保存的寄存器；自动分配和释放；栈指针（SP）管理；栈溢出（Stack Overflow）是常见错误
- **相关**：Stack Frame（栈帧）、Heap（堆）、Function Call（函数调用）

### Static Linking / 静态链接
- **中文**：静态链接
- **定义**：将库代码复制到可执行文件中的链接方式
- **说明**：可执行文件独立运行、不依赖外部库；文件较大；库更新需重新链接；.a（Linux）、.lib（Windows）
- **相关**：Dynamic Linking（动态链接）、Linker（链接器）、Library（库）
