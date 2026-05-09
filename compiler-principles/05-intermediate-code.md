# 05. 中间代码与优化 (Intermediate Code & Optimization)

## 中间表示

### Basic Block / 基本块
- **中文**：基本块
- **定义**：程序中顺序执行、无分支进入（除入口）和无分支退出（除出口）的最大连续语句序列
- **说明**：基本块是控制流图的节点；入口为块首语句，出口为终止语句（跳转、条件分支、返回）；优化和代码生成的基本单位
- **相关**：Control Flow Graph（控制流图）、Optimization（优化）、Code Generation（代码生成）

### Control Flow Graph (CFG) / 控制流图
- **中文**：控制流图
- **定义**：以基本块为节点、以可能的控制转移为边的有向图
- **说明**：入口块和出口块；边表示跳转关系；用于数据流分析、优化、代码生成；是编译器中间表示的重要形式
- **相关**：Basic Block（基本块）、Data Flow Analysis（数据流分析）、Optimization（优化）

### Intermediate Code / 中间代码
- **中文**：中间代码
- **定义**：介于源代码和目标代码之间、与源语言和目标机器无关的程序表示
- **说明**：优点：便于优化、可重定向（同一前端配多个后端）、简化编译器设计；形式：三地址码、四元式、SSA、控制流图
- **相关**：IR（中间表示）、Code Generation（代码生成）、Optimization（优化）

### IR (Intermediate Representation) / 中间表示
- **中文**：中间表示
- **定义**：编译器内部使用的程序抽象表示，连接前端和后端
- **说明**：层次：高层 IR（接近 AST，用于语义分析）、中层 IR（三地址码，用于优化）、低层 IR（接近机器码，用于代码生成）；LLVM IR 是著名实例
- **同义词**：Intermediate Code（中间代码）
- **相关**：AST、Optimization（优化）、Code Generation（代码生成）

### Quadruple / 四元式
- **中文**：四元式
- **定义**：每条指令包含四个字段（操作符、两个操作数、结果）的中间代码表示
- **说明**：形式：(op, arg1, arg2, result)；易于实现和优化；临时变量存储结果；是三地址码的一种结构化表示
- **相关**：Three-Address Code（三地址码）、Intermediate Code（中间代码）、TAC

### SSA (Static Single Assignment) / 静态单赋值形式
- **中文**：静态单赋值形式
- **定义**：每个变量只被赋值一次的中间表示形式
- **说明**：通过插入 φ（Phi）函数合并不同控制流路径上的变量值；简化数据流分析；现代编译器（LLVM、GCC）广泛使用
- **相关**：Intermediate Representation（中间表示）、Data Flow Analysis（数据流分析）、Phi Function（Phi 函数）

### TAC (Three-Address Code) / 三地址码
- **中文**：三地址码
- **定义**：每条指令最多包含三个地址（两个操作数和一个结果）的中间代码形式
- **说明**：形式：x = y op z；简单、规范、与机器无关；便于优化和代码生成；可表示为四元式、三元式或间接三元式
- **相关**：Intermediate Code（中间代码）、Quadruple（四元式）、Code Generation（代码生成）

### Triple / 三元式
- **中文**：三元式
- **定义**：每条指令包含三个字段（操作符、两个操作数）的中间代码表示，结果位置隐式确定
- **说明**：通过指令位置引用结果；节省存储空间；但不便于指令重排（重排需修改所有引用）
- **相关**：Quadruple（四元式）、Three-Address Code（三地址码）、Intermediate Code（中间代码）

## 优化技术

### Constant Folding / 常量折叠
- **中文**：常量折叠
- **定义**：在编译时计算常量表达式的值，用结果替换表达式的优化
- **说明**：如 x = 2 + 3 → x = 5；减少运行时计算；简单有效；常与常量传播结合使用
- **相关**：Constant Propagation（常量传播）、Optimization（优化）、Compile-Time Evaluation（编译时求值）

### Constant Propagation / 常量传播
- **中文**：常量传播
- **定义**：将已知的常量值替换变量使用处的优化
- **说明**：如 x = 5; y = x + 1 → y = 5 + 1 → y = 6（配合常量折叠）；需要数据流分析确定变量是否为常量
- **相关**：Constant Folding（常量折叠）、Data Flow Analysis（数据流分析）、Optimization（优化）

### Copy Propagation / 拷贝传播
- **中文**：拷贝传播
- **定义**：将变量赋值给另一个变量后，用源变量替换目标变量的使用
- **说明**：如 x = y; z = x + 1 → z = y + 1；减少变量依赖；为死代码消除创造条件
- **相关**：Dead Code Elimination（死代码消除）、Data Flow Analysis（数据流分析）、Optimization（优化）

### Dead Code Elimination / 死代码消除
- **中文**：死代码消除
- **定义**：删除对程序结果无影响的代码的优化
- **说明**：死代码：不可达代码、不使用的赋值、无副作用的纯计算；减少代码体积、提高缓存效率
- **同义词**：DCE
- **相关**：Optimization（优化）、Control Flow Analysis（控制流分析）、Live Variable（活跃变量）

### Function Inlining / 函数内联
- **中文**：函数内联
- **定义**：将函数调用处替换为函数体的优化
- **说明**：减少调用开销（栈帧建立、参数传递、跳转）；但增加代码体积；适合小函数；需权衡代码体积和速度
- **相关**：Inline Expansion（内联展开）、Optimization（优化）、Call Overhead（调用开销）

### Instruction Scheduling / 指令调度
- **中文**：指令调度
- **定义**：重排指令顺序以减少流水线停顿、提高指令级并行的优化
- **说明**：考虑数据依赖和硬件资源约束；列表调度是基本算法；现代 CPU 的乱序执行减少了对编译时调度的依赖
- **相关**：Pipeline（流水线）、Data Dependency（数据依赖）、Code Generation（代码生成）

### Loop Invariant Code Motion / 循环不变量外提
- **中文**：循环不变量外提
- **定义**：将循环内不随迭代变化的计算移到循环外部的优化
- **说明**：如 for 循环内计算数组长度或常量表达式；减少循环内计算量；需要证明表达式值在循环中不变
- **同义词**：Loop-Invariant Motion、Hoisting
- **相关**：Loop Optimization（循环优化）、Optimization（优化）、Data Flow Analysis（数据流分析）

### Loop Optimization / 循环优化
- **中文**：循环优化
- **定义**：针对循环结构的一系列优化技术，提高执行效率
- **说明**：技术：循环展开（Loop Unrolling）、循环不变量外提、强度削弱、归纳变量优化；循环是性能关键
- **相关**：Loop Unrolling（循环展开）、Strength Reduction（强度削弱）、Optimization（优化）

### Loop Unrolling / 循环展开
- **中文**：循环展开
- **定义**：复制循环体多次、减少循环控制开销的优化
- **说明**：如将循环体执行 1 次改为执行 4 次，步长改为 4；减少分支和计数器更新；但增加代码体积；适合小循环
- **相关**：Loop Optimization（循环优化）、Optimization（优化）、Instruction Scheduling（指令调度）

### Optimization Level / 优化级别
- **中文**：优化级别
- **定义**：编译器预设的一组优化策略的组合，通常用 -O0、-O1、-O2、-O3 表示
- **说明**：-O0：无优化，便于调试；-O1：基本优化；-O2：大多数优化，不开销过大的优化；-O3：激进优化；还有 -Os（优化大小）、-Ofast（不严格遵守标准）
- **相关**：Compiler（编译器）、Optimization（优化）、Compiler Flag（编译器选项）

### Peephole Optimization / 窥孔优化
- **中文**：窥孔优化
- **定义**：在生成的目标代码上，通过滑动一个小的"窗口"（窥孔）寻找并替换低效指令序列的局部优化
- **说明**：简单但有效；模式：冗余加载/存储消除、常量合并、代数化简、不可达代码删除；通常在代码生成后应用
- **相关**：Code Generation（代码生成）、Optimization（优化）、Instruction Selection（指令选择）

### Strength Reduction / 强度削弱
- **中文**：强度削弱
- **定义**：用开销较小的操作替换开销较大的操作的优化
- **说明**：如乘法替换为加法（归纳变量优化）、乘方替换为乘法、整数除法替换为移位；循环优化中常用
- **相关**：Loop Optimization（循环优化）、Optimization（优化）、Induction Variable（归纳变量）

## 数据流分析

### Available Expression / 可用表达式
- **中文**：可用表达式
- **定义**：在程序某点之前已经计算过、且之后没有被修改的表达式
- **说明**：数据流分析问题；用于公共子表达式消除（CSE）；前向数据流问题
- **相关**：Common Subexpression Elimination（公共子表达式消除）、Data Flow Analysis（数据流分析）、Optimization（优化）

### Common Subexpression Elimination (CSE) / 公共子表达式消除
- **中文**：公共子表达式消除
- **定义**：识别并消除重复计算相同表达式的优化
- **说明**：如 x = a+b; y = a+b → x = a+b; y = x；需要可用表达式分析；注意表达式中的变量值是否变化
- **同义词**：CSE
- **相关**：Available Expression（可用表达式）、Optimization（优化）、Data Flow Analysis（数据流分析）

### Data Flow / 数据流
- **中文**：数据流
- **定义**：程序中数据值在不同语句和控制路径之间的流动和传播
- **说明**：分析数据流可确定：变量定义是否被使用、表达式是否可复用、变量是否已初始化；是优化的基础
- **相关**：Data Flow Analysis（数据流分析）、Control Flow（控制流）、Optimization（优化）

### Def-Use Chain / 定义-使用链
- **中文**：定义-使用链
- **定义**：连接变量定义点和其所有使用点的数据结构
- **说明**：用于优化：常量传播、拷贝传播、活跃变量分析；需要到达定义分析
- **相关**：Reaching Definition（到达定义）、Data Flow Analysis（数据流分析）、Optimization（优化）

### Fixed-Point Iteration / 不动点迭代
- **中文**：不动点迭代
- **定义**：数据流分析中反复应用数据流方程直到结果不再变化的求解方法
- **说明**：由于数据流方程是单调的，迭代必收敛；收敛速度取决于控制流图结构和初始值
- **相关**：Data Flow Analysis（数据流分析）、Control Flow Graph（控制流图）、Convergence（收敛）

### Phi Function / Phi 函数
- **中文**：Phi 函数
- **定义**：SSA 形式中用于合并不同控制流路径上变量值的特殊函数
- **说明**：形式：x = φ(v1, v2, ..., vn)；根据控制流来自哪个前驱块选择对应值；是 SSA 的核心机制
- **相关**：SSA、Control Flow Graph（控制流图）、Intermediate Representation（中间表示）

### Reaching Definition / 到达定义
- **中文**：到达定义
- **定义**：能够到达程序某点、且中间没有被覆盖的变量赋值语句
- **说明**：前向数据流问题；用于常量传播、拷贝传播；每个变量的定义集在基本块入口和出口计算
- **相关**：Data Flow Analysis（数据流分析）、Constant Propagation（常量传播）、Optimization（优化）

### Use-Def Chain / 使用-定义链
- **中文**：使用-定义链
- **定义**：连接变量使用点和其所有可能定义点的数据结构
- **说明**：Use-Def 链与 Def-Use 链方向相反；用于变量重命名、寄存器分配、依赖分析
- **相关**：Def-Use Chain（定义-使用链）、Data Flow Analysis（数据流分析）、Optimization（优化）

## 全局优化

### Alias Analysis / 别名分析
- **中文**：别名分析
- **定义**：确定程序中哪些内存位置可能通过不同名称（指针）被访问的静态分析
- **说明**：保守分析：若不能确定不别名，则假设可能别名；影响优化：死存储消除、指令重排、向量化；难度：指针、数组、类型转换
- **相关**：Pointer Analysis（指针分析）、Optimization（优化）、Static Analysis（静态分析）

### Control Flow Analysis / 控制流分析
- **中文**：控制流分析
- **定义**：分析程序中基本块之间控制转移关系的技术
- **说明**：构建控制流图；识别循环、条件分支、不可达代码；是数据流分析和优化的前置步骤
- **相关**：Control Flow Graph（控制流图）、Data Flow Analysis（数据流分析）、Optimization（优化）

### Global Optimization / 全局优化
- **中文**：全局优化
- **定义**：在整个函数或程序范围内进行的优化（相对于局部/窥孔优化）
- **说明**：需要控制流图和数据流分析；包括：全局常量传播、全局公共子表达式消除、循环优化；效果通常比局部优化显著
- **相关**：Local Optimization（局部优化）、Data Flow Analysis（数据流分析）、Optimization（优化）

### Local Optimization / 局部优化
- **中文**：局部优化
- **定义**：在单个基本块内进行的优化
- **说明**：不需要控制流信息；包括：局部常量传播、局部公共子表达式消除、代数化简；实现简单、开销小
- **相关**：Global Optimization（全局优化）、Basic Block（基本块）、Optimization（优化）

### Tail Call Optimization / 尾调用优化
- **中文**：尾调用优化
- **定义**：将函数尾部的递归调用转换为跳转、避免栈增长的优化
- **说明**：尾递归：递归调用是函数的最后一个操作；优化后复用当前栈帧；函数式语言（如 Scheme）要求支持
- **相关**：Recursion（递归）、Function Call（函数调用）、Stack Frame（栈帧）
