# 07. 缩写汇总 (Abbreviations)

### ABI
- **中文**：应用程序二进制接口
- **全称**：Application Binary Interface
- **说明**：定义程序模块间二进制接口的标准
- **相关**：API、Calling Convention、Object File

### ADT
- **中文**：抽象数据类型
- **全称**：Abstract Data Type
- **说明**：只定义行为而不指定实现的数据类型
- **相关**：Data Structure（数据结构）、Encapsulation（封装）

### AST
- **中文**：抽象语法树
- **全称**：Abstract Syntax Tree
- **说明**：源代码抽象语法结构的树形表示
- **相关**：Parse Tree（分析树）、Compiler（编译器）

### BNF
- **中文**：巴科斯-瑙尔范式
- **全称**：Backus-Naur Form
- **说明**：描述上下文无关文法的元语法表示法
- **相关**：CFG、Grammar（文法）

### CFG
- **中文**：上下文无关文法 / 控制流图
- **全称**：Context-Free Grammar / Control Flow Graph
- **说明**：根据上下文分别指代文法或程序控制流图
- **相关**：Grammar、Basic Block（基本块）

### CISC
- **中文**：复杂指令集计算机
- **全称**：Complex Instruction Set Computer
- **说明**：指令功能丰富、格式多样的处理器架构，如 x86
- **相关**：RISC、ISA、CPU

### CRT
- **中文**：C 运行时库
- **全称**：C Runtime Library
- **说明**：C 程序运行所需的基础库函数
- **相关**：Runtime、Standard Library（标准库）

### CSE
- **中文**：公共子表达式消除
- **全称**：Common Subexpression Elimination
- **说明**：消除重复计算相同表达式的优化
- **相关**：Optimization（优化）、Data Flow Analysis（数据流分析）

### DAG
- **中文**：有向无环图
- **全称**：Directed Acyclic Graph
- **说明**：无环的有向图，用于中间代码表示和依赖分析
- **相关**：Intermediate Code（中间代码）、Optimization（优化）

### DCE
- **中文**：死代码消除
- **全称**：Dead Code Elimination
- **说明**：删除不影响程序结果的代码
- **相关**：Optimization（优化）、Live Variable（活跃变量）

### DFA
- **中文**：确定有限自动机 / 数据流分析
- **全称**：Deterministic Finite Automaton / Data Flow Analysis
- **说明**：根据上下文分别指代自动机或分析技术
- **相关**：NFA、Finite Automaton（有限自动机）

### ELF
- **中文**：可执行与可链接格式
- **全称**：Executable and Linkable Format
- **说明**：Linux/Unix 系统的标准可执行文件格式
- **相关**：Object File（目标文件）、Linker（链接器）

### EBNF
- **中文**：扩展巴科斯-瑙尔范式
- **全称**：Extended Backus-Naur Form
- **说明**：BNF 的扩展，支持重复、可选等便利表示
- **相关**：BNF、Grammar（文法）

### GC
- **中文**：垃圾回收
- **全称**：Garbage Collection
- **说明**：自动回收不再使用内存的机制
- **相关**：Memory Management（内存管理）、Heap（堆）

### GIMPLE
- **中文**：GCC 中间表示
- **全称**：
- **说明**：GCC 编译器使用的三地址码形式的中间表示
- **相关**：GCC、IR、Intermediate Code（中间代码）

### IR
- **中文**：中间表示
- **全称**：Intermediate Representation
- **说明**：编译器内部使用的程序抽象表示
- **相关**：AST、Intermediate Code（中间代码）、Optimization（优化）

### ISA
- **中文**：指令集架构
- **全称**：Instruction Set Architecture
- **说明**：CPU 指令集、寄存器、数据类型的抽象规范
- **相关**：CPU、Assembly Language（汇编语言）、Microarchitecture（微体系结构）

### JIT
- **中文**：即时编译
- **全称**：Just-In-Time
- **说明**：运行时将字节码编译为机器码的技术
- **相关**：Interpreter（解释器）、Compiler（编译器）、Bytecode（字节码）

### LL
- **中文**：从左到右扫描、最左推导
- **全称**：Left-to-right, Leftmost derivation
- **说明**：自顶向下解析算法类（LL(k)、LL(1)）
- **相关**：Recursive Descent（递归下降）、Parser（解析器）

### LR
- **中文**：从左到右扫描、最右推导的逆
- **全称**：Left-to-right, Rightmost derivation in reverse
- **说明**：自底向上解析算法类（SLR、LALR、LR(1)）
- **相关**：Yacc、Shift-Reduce（移进-归约）、Parser（解析器）

### LALR
- **中文**：向前看 LR
- **全称**：Look Ahead LR
- **说明**：合并同心项集减少状态数的 LR 解析器
- **相关**：LR、SLR、Yacc

### LLVM
- **中文**：底层虚拟机
- **全称**：Low Level Virtual Machine
- **说明**：模块化和可重用的编译器和工具链技术
- **相关**：Compiler（编译器）、IR、Clang

### NF
- **中文**：范式
- **全称**：Normal Form
- **说明**：文法或布尔公式的标准形式
- **相关**：Chomsky Normal Form（乔姆斯基范式）

### NFA
- **中文**：非确定有限自动机
- **全称**：Non-Deterministic Finite Automaton
- **说明**：允许非确定转移和 ε 转移的有限自动机
- **相关**：DFA、Regular Expression（正则表达式）

### ODR
- **中文**：单一定义规则
- **全称**：One Definition Rule
- **说明**：C++ 中每个实体只能定义一次的规则
- **相关**：Definition（定义）、Linker（链接器）

### PC
- **中文**：程序计数器
- **全称**：Program Counter
- **说明**：存储下一条要执行指令地址的寄存器
- **相关**：CPU、Register（寄存器）

### PE
- **中文**：可移植可执行文件
- **全称**：Portable Executable
- **说明**：Windows 系统的可执行文件格式
- **相关**：ELF、Executable（可执行文件）

### REPL
- **中文**：读取-求值-输出循环
- **全称**：Read-Eval-Print Loop
- **说明**：交互式解释执行代码的环境
- **相关**：Interpreter（解释器）、Shell

### RISC
- **中文**：精简指令集计算机
- **全称**：Reduced Instruction Set Computer
- **说明**：指令简洁、格式规整的处理器架构，如 ARM、RISC-V
- **相关**：CISC、ISA、CPU

### RTL
- **中文**：寄存器传输语言
- **全称**：Register Transfer Language
- **说明**：描述数据在寄存器间传输和操作的中间表示
- **相关**：IR、Code Generation（代码生成）

### RTTI
- **中文**：运行时类型信息
- **全称**：Run-Time Type Information
- **说明**：程序运行时获取对象类型信息的机制
- **相关**：Type System（类型系统）、Dynamic Cast（动态类型转换）

### SLR
- **中文**：简单 LR
- **全称**：Simple LR
- **说明**：使用 LR(0) 项集和 Follow 集合的简化 LR 解析器
- **相关**：LR、LALR、Parser（解析器）

### SP
- **中文**：栈指针
- **全称**：Stack Pointer
- **说明**：指向栈顶的寄存器
- **相关**：Stack（栈）、Stack Frame（栈帧）、Register（寄存器）

### SSA
- **中文**：静态单赋值形式
- **全称**：Static Single Assignment
- **说明**：每个变量只赋值一次的中间表示
- **相关**：IR、Phi Function（Phi 函数）、Optimization（优化）

### TAC
- **中文**：三地址码
- **全称**：Three-Address Code
- **说明**：每条指令最多三个地址的中间代码
- **相关**：Intermediate Code（中间代码）、Quadruple（四元式）

### VM
- **中文**：虚拟机
- **全称**：Virtual Machine
- **说明**：模拟硬件执行中间代码的软件环境
- **相关**：JVM、Interpreter（解释器）、Bytecode（字节码）

### Yacc
- **中文**：又一个编译器的编译器
- **全称**：Yet Another Compiler Compiler
- **说明**：经典的 LALR 解析器生成器
- **相关**：Bison、Parser Generator（解析器生成器）、Lex
