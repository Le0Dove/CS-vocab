# 04. 语义分析 (Semantic Analysis)

## 类型系统

### Coercion / 强制类型转换
- **中文**：强制类型转换
- **定义**：编译器自动将一种数据类型转换为另一种兼容类型的隐式转换
- **说明**：如 int → float 在表达式中自动进行；窄化转换（如 float → int）可能丢失精度；语言定义允许哪些强制转换
- **同义词**：Implicit Conversion（隐式转换）
- **相关**：Type Conversion（类型转换）、Cast（强制转换）、Type System（类型系统）

### Polymorphism / 多态
- **中文**：多态
- **定义**：同一操作或名称在不同上下文中具有不同行为的特性
- **说明**：子类型多态（继承）、参数多态（泛型）、特设多态（重载）；提高代码复用性和灵活性
- **相关**：Inheritance（继承）、Overloading（重载）、Generic（泛型）

### Static Typing / 静态类型
- **中文**：静态类型
- **定义**：在编译时确定并检查变量类型的类型系统
- **说明**：编译时捕获类型错误；不需要运行时类型检查；代表语言：C、C++、Java、Rust；与动态类型相对
- **相关**：Dynamic Typing（动态类型）、Type Checking（类型检查）、Compiler（编译器）

### Strong Typing / 强类型
- **中文**：强类型
- **定义**：不允许隐式类型转换或只允许严格类型匹配的类型系统
- **说明**：类型错误在编译时或运行时严格检查；减少类型相关 Bug；Python 是强类型但动态类型；C 是静态类型但弱类型（允许隐式转换）
- **相关**：Weak Typing（弱类型）、Type Safety（类型安全）、Type System（类型系统）

### Type / 类型
- **中文**：类型
- **定义**：数据值的类别，定义了该值可执行的操作和内存表示
- **说明**：基本类型：int、float、bool、char；复合类型：array、struct、class、pointer；类型系统是编程语言的核心
- **相关**：Type System（类型系统）、Type Checking（类型检查）、Variable（变量）

### Type Checking / 类型检查
- **中文**：类型检查
- **定义**：验证程序中操作数的类型是否与操作符要求兼容的过程
- **说明**：静态类型检查（编译时）：C、Java；动态类型检查（运行时）：Python、JS；强类型 vs 弱类型；类型推断减少显式类型声明
- **相关**：Type System（类型系统）、Static Typing（静态类型）、Dynamic Typing（动态类型）

### Type Conversion / 类型转换
- **中文**：类型转换
- **定义**：将一种数据类型的值转换为另一种类型的操作
- **说明**：隐式转换（Implicit/Coercion）：编译器自动；显式转换（Explicit/Cast）：程序员指定；窄化转换可能丢失信息
- **同义词**：Type Casting（类型转换）
- **相关**：Coercion（强制转换）、Type System（类型系统）、Cast（强制转换）

### Type Inference / 类型推断
- **中文**：类型推断
- **定义**：编译器自动推导变量或表达式类型的机制
- **说明**：无需显式声明类型；Hindley-Milner 算法（用于 ML、Haskell）；现代语言：auto（C++11）、var（Java）、let（Rust）；提高代码简洁性
- **相关**：Type System（类型系统）、Static Typing（静态类型）、Compiler（编译器）

### Type Safety / 类型安全
- **中文**：类型安全
- **定义**：程序不会执行未定义类型操作的性质
- **说明**：类型安全语言防止：空指针解引用、缓冲区溢出（部分）、类型混淆；Rust 通过所有权系统实现内存和类型安全
- **相关**：Strong Typing（强类型）、Memory Safety（内存安全）、Type System（类型系统）

### Type System / 类型系统
- **中文**：类型系统
- **定义**：编程语言中定义数据类型及类型间规则的逻辑系统
- **说明**：分类：静态/动态、强/弱、显式/隐式；类型规则确保操作合法性；影响语言安全性、性能和表达能力
- **相关**：Type Checking（类型检查）、Type Safety（类型安全）、Programming Language（编程语言）

## 作用域与符号

### Block / 块
- **中文**：块
- **定义**：由花括号 {} 包围的代码区域，形成局部作用域
- **说明**：块内声明的变量只在块内可见；支持嵌套；C/C++/Java 中使用；进入块时分配空间，退出时释放
- **相关**：Scope（作用域）、Local Variable（局部变量）、Lifetime（生命周期）

### Binding / 绑定
- **中文**：绑定
- **定义**：将名称（变量、函数）与其实体（内存地址、值、代码）关联的过程
- **说明**：静态绑定（编译时确定，如 C 函数调用）；动态绑定（运行时确定，如虚函数）；作用域规则决定绑定的可见性
- **相关**：Scope（作用域）、Name Resolution（名称解析）、Symbol Table（符号表）

### Declaration / 声明
- **中文**：声明
- **定义**：引入名称并指定其类型的语句，通常不分配值
- **说明**：如 extern int x;（C）、function declaration；与定义（Definition）不同，声明不创建实际对象；一个定义可对应多个声明
- **相关**：Definition（定义）、Symbol Table（符号表）、Scope（作用域）

### Definition / 定义
- **中文**：定义
- **定义**：创建实际变量或函数、分配存储空间或提供函数体的语句
- **说明**：如 int x = 10;、function body；每个实体只能定义一次（ODR：One Definition Rule）；声明可多次但定义只能一次
- **相关**：Declaration（声明）、Symbol Table（符号表）、Storage Allocation（存储分配）

### Identifier / 标识符
- **中文**：标识符
- **定义**：程序员定义的、用于命名变量、函数、类等程序实体的名称
- **说明**：规则：通常以字母或下划线开头，后跟字母、数字、下划线；区分大小写（视语言而定）；不能与关键字冲突
- **相关**：Variable（变量）、Keyword（关键字）、Symbol Table（符号表）

### Lifetime / 生命周期
- **中文**：生命周期
- **定义**：变量从创建到销毁的时间段
- **说明**：分类：静态（程序全程）、自动（块内）、动态（堆上手动管理）；生命周期与作用域不同（作用域是可见性，生命周期是存在时间）
- **相关**：Scope（作用域）、Storage Class（存储类别）、Memory Management（内存管理）

### Local Variable / 局部变量
- **中文**：局部变量
- **定义**：在函数或块内声明、只在该作用域内可见的变量
- **说明**：函数调用时分配、返回时释放（栈上）；避免命名冲突；不同函数可有同名局部变量
- **相关**：Global Variable（全局变量）、Scope（作用域）、Stack（栈）

### Name Resolution / 名称解析
- **中文**：名称解析
- **定义**：根据作用域规则查找标识符对应声明的过程
- **说明**：从内层作用域向外层查找；考虑命名空间、using/import 声明；静态语言编译时解析，动态语言运行时解析
- **相关**：Scope（作用域）、Binding（绑定）、Symbol Table（符号表）

### Namespace / 命名空间
- **中文**：命名空间
- **定义**：将全局作用域划分为独立区域的机制，避免名称冲突
- **说明**：C++ 使用 namespace；Java 使用 package；Python 使用 module；同名标识符可在不同命名空间共存
- **相关**：Scope（作用域）、Name Resolution（名称解析）、Identifier（标识符）

### Overloading / 重载
- **中文**：重载
- **定义**：同一作用域中允许多个同名函数或运算符具有不同参数列表的机制
- **说明**：函数重载：参数个数/类型不同；运算符重载：自定义运算符行为（如 C++）；编译时根据参数选择正确版本
- **相关**：Polymorphism（多态）、Function Signature（函数签名）、Static Binding（静态绑定）

### Scope / 作用域
- **中文**：作用域
- **定义**：程序中某个名称可见和可引用的区域
- **说明**：分类：词法作用域（静态作用域，大多数语言）、动态作用域（少数语言如 Lisp 早期版本）；嵌套作用域：内层可访问外层，反之不可
- **相关**：Lifetime（生命周期）、Block（块）、Name Resolution（名称解析）

### Scope Resolution / 作用域解析
- **中文**：作用域解析
- **定义**：确定标识符所属作用域并找到其定义的机制
- **说明**：C++ 的 :: 运算符；this 指针解析成员变量；编译器通过符号表和作用域链实现
- **相关**：Scope（作用域）、Name Resolution（名称解析）、Symbol Table（符号表）

### Symbol / 符号
- **中文**：符号
- **定义**：程序中定义的实体（变量、函数、类等）的名称和属性
- **说明**：符号表记录符号信息：名称、类型、作用域、地址、行号等；是语义分析和代码生成的基础
- **相关**：Symbol Table（符号表）、Identifier（标识符）、Name Resolution（名称解析）

## 属性文法

### Attribute / 属性
- **中文**：属性
- **定义**：附着在文法符号上的信息（如类型、值、地址），用于语义计算
- **说明**：综合属性（Synthesized）：从子节点向父节点传递；继承属性（Inherited）：从父节点或兄弟节点传递
- **相关**：Attribute Grammar（属性文法）、Syntax-Directed Translation（语法制导翻译）、Semantic Analysis（语义分析）

### Attribute Grammar / 属性文法
- **中文**：属性文法
- **定义**：为上下文无关文法的每个符号附加属性和语义规则的形式化框架
- **说明**：用于描述静态语义（类型检查、翻译）；属性传递方式：综合属性（自底向上）、继承属性（自顶向下）
- **相关**：Syntax-Directed Translation（语法制导翻译）、Semantic Analysis（语义分析）、Attribute（属性）

### Decorated Parse Tree / 装饰分析树
- **中文**：装饰分析树
- **定义**：每个节点都标注了属性值的分析树
- **说明**：展示属性计算过程；通过遍历分析树计算属性值；是属性文法的可视化表示
- **相关**：Attribute Grammar（属性文法）、Parse Tree（分析树）、Attribute（属性）

### Inherited Attribute / 继承属性
- **中文**：继承属性
- **定义**：从父节点或兄弟节点获取值的属性
- **说明**：用于传递上下文信息（如类型环境）；如声明中类型传递给变量名；依赖分析树中节点的兄弟或父节点
- **相关**：Synthesized Attribute（综合属性）、Attribute Grammar（属性文法）、Parse Tree（分析树）

### Semantic Action / 语义动作
- **中文**：语义动作
- **定义**：在语法分析过程中执行的代码片段，用于计算属性或生成中间代码
- **说明**：嵌入在产生式中；如 E → E1 + T { E.val = E1.val + T.val }；Yacc/Bison 支持语义动作
- **相关**：Syntax-Directed Translation（语法制导翻译）、Attribute Grammar（属性文法）、Parser Generator（解析器生成器）

### Semantic Rule / 语义规则
- **中文**：语义规则
- **定义**：定义属性如何计算的形式化规则
- **说明**：与文法产生式关联；无副作用的纯函数式规则；确保属性值唯一确定
- **相关**：Attribute Grammar（属性文法）、Semantic Action（语义动作）、Attribute（属性）

### S-Attributed Definition / S 属性定义
- **中文**：S 属性定义
- **定义**：只使用综合属性的属性文法
- **说明**：可在自底向上分析时同时计算；不需要分析树，只用分析栈；实现简单高效
- **相关**：L-Attributed Definition（L 属性定义）、Synthesized Attribute（综合属性）、Attribute Grammar（属性文法）

### Synthesized Attribute / 综合属性
- **中文**：综合属性
- **定义**：从子节点计算得到的、向父节点传递的属性
- **说明**：如表达式节点的值由子表达式计算；适合自底向上计算；S 属性文法只使用综合属性
- **相关**：Inherited Attribute（继承属性）、Attribute Grammar（属性文法）、Parse Tree（分析树）

## 高级语义分析

### Control Flow / 控制流
- **中文**：控制流
- **定义**：程序中语句执行的顺序和路径
- **说明**：控制流结构：顺序、选择（if/switch）、循环（for/while）、跳转（break/continue/return/goto）；控制流分析是优化的基础
- **相关**：Control Flow Graph（控制流图）、Basic Block（基本块）、Optimization（优化）

### Control Flow Graph (CFG) / 控制流图
- **中文**：控制流图
- **定义**：用节点表示基本块、边表示跳转关系的程序控制流表示
- **说明**：节点：基本块（无分支的连续语句序列）；边：条件/无条件跳转；用于数据流分析和代码优化
- **同义词**：Flow Graph
- **相关**：Basic Block（基本块）、Data Flow Analysis（数据流分析）、Optimization（优化）

### Data Flow Analysis / 数据流分析
- **中文**：数据流分析
- **定义**：静态分析程序中数据如何在控制流路径上传播和变化的技术
- **说明**：分析：到达定义（Reaching Definitions）、活跃变量（Live Variables）、可用表达式（Available Expressions）；用于优化和错误检测
- **相关**：Control Flow Graph（控制流图）、Optimization（优化）、Static Analysis（静态分析）

### Dependency Analysis / 依赖分析
- **中文**：依赖分析
- **定义**：分析程序中语句之间数据依赖和控制依赖关系的技术
- **说明**：数据依赖：流依赖（RAW）、反依赖（WAR）、输出依赖（WAW）；用于并行化和优化；循环依赖分析用于向量化
- **相关**：Data Flow Analysis（数据流分析）、Parallelization（并行化）、Optimization（优化）

### Induction Variable / 归纳变量
- **中文**：归纳变量
- **定义**：循环中每次迭代按固定量递增/递减的变量
- **说明**：如 for(i=0; i<n; i++) 中的 i；识别归纳变量可优化强度削弱（用加法代替乘法）、删除冗余计算
- **相关**：Loop Optimization（循环优化）、Strength Reduction（强度削弱）、Data Flow Analysis（数据流分析）

### Live Variable / 活跃变量
- **中文**：活跃变量
- **定义**：在程序某点之后可能被使用的变量
- **说明**：数据流分析概念；活跃变量分析用于寄存器分配（两个变量不同时活跃可共用寄存器）和死代码消除
- **相关**：Data Flow Analysis（数据流分析）、Register Allocation（寄存器分配）、Dead Code Elimination（死代码消除）

### Reaching Definition / 到达定义
- **中文**：到达定义
- **定义**：能够到达程序某点而不被重新定义的变量赋值语句
- **说明**：数据流分析基本概念；用于常量传播、拷贝传播、无用定义删除；是程序优化的基础
- **相关**：Data Flow Analysis（数据流分析）、Constant Propagation（常量传播）、Optimization（优化）

### Static Analysis / 静态分析
- **中文**：静态分析
- **定义**：在不执行程序的情况下分析代码性质和发现潜在错误的技术
- **说明**：包括：类型检查、数据流分析、指针分析、控制流分析；工具：编译器、Lint、SonarQube、Coverity；发现：空指针、内存泄漏、未初始化变量
- **相关**：Compiler（编译器）、Data Flow Analysis（数据流分析）、Type Checking（类型检查）

### Type Environment / 类型环境
- **中文**：类型环境
- **定义**：在程序某点记录所有可见变量及其类型的映射
- **说明**：随作用域变化；用于类型检查；形式化为 Γ（Gamma）：变量 → 类型的映射函数
- **相关**：Type System（类型系统）、Type Checking（类型检查）、Scope（作用域）
