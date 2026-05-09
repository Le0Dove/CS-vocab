# 03. 语法分析 (Syntax Analysis)

## 文法基础

### Ambiguity / 歧义性
- **中文**：歧义性
- **定义**：一个文法可以推导出多个不同的语法树（即存在多个最左/最右推导）
- **说明**：歧义文法使解析器无法确定程序结构；解决方法：重写文法消除歧义、使用优先级/结合性规则；经典例子：悬挂 else 问题
- **相关**：Grammar（文法）、Parse Tree（分析树）、Associativity（结合性）

### Backus-Naur Form (BNF) / 巴科斯-瑙尔范式
- **中文**：巴科斯-瑙尔范式
- **定义**：描述上下文无关文法的元语法（Meta-Syntax）表示法
- **说明**：A → B C | D 表示 A 可以推导出 BC 或 D；广泛用于编程语言规范；扩展形式：EBNF（扩展 BNF）
- **相关**：Context-Free Grammar（上下文无关文法）、Production Rule（产生式）

### Context-Free Grammar (CFG) / 上下文无关文法
- **中文**：上下文无关文法
- **定义**：产生式左部只有一个非终结符、不依赖上下文的形式文法
- **说明**：乔姆斯基层级 Type-2；足以描述大多数编程语言语法；由终结符、非终结符、产生式和开始符号组成；解析效率高
- **相关**：BNF、Parse Tree（分析树）、Parser（解析器）

### Derivation / 推导
- **中文**：推导
- **定义**：从文法开始符号出发、反复应用产生式规则生成终结符串的过程
- **说明**：最左推导（Leftmost Derivation）：每次替换最左非终结符；最右推导（Rightmost Derivation）：每次替换最右非终结符；每个推导对应一棵分析树
- **相关**：Grammar（文法）、Production Rule（产生式）、Parse Tree（分析树）

### Grammar / 文法
- **中文**：文法
- **定义**：形式化描述语言语法结构的规则集合
- **说明**：四元组 G = (V, T, P, S)：V（非终结符集）、T（终结符集）、P（产生式集）、S（开始符号）；分为：正则文法、上下文无关文法、上下文有关文法、无限制文法
- **相关**：Language（语言）、Production Rule（产生式）、Parser（解析器）

### Language / 语言
- **中文**：语言
- **定义**：由文法产生的所有合法句子（终结符串）的集合
- **说明**：形式语言是符号串的集合；编程语言是形式语言的实例；语言分类依据乔姆斯基层级
- **相关**：Grammar（文法）、Alphabet（字母表）、String（字符串）

### Left Recursion / 左递归
- **中文**：左递归
- **定义**：文法中非终结符 A 的产生式形式为 A → Aα（直接左递归）或 A 经多步推导出 Aα（间接左递归）
- **说明**：导致递归下降解析器无限递归；消除方法：提取左因子、改写文法（如 A → Aα | β 改写为 A → βA'，A' → αA' | ε）
- **相关**：Recursion（递归）、Parser（解析器）、Left Factoring（提取左因子）

### Non-Terminal / 非终结符
- **中文**：非终结符
- **定义**：文法中产生式左部出现的符号，可以被进一步推导替换
- **说明**：通常用大写字母表示（如 A, B, S）；表示语法结构类别（如 expr、stmt）；必须被推导为终结符串
- **相关**：Terminal（终结符）、Grammar（文法）、Production Rule（产生式）

### Parse Tree / 分析树
- **中文**：分析树
- **定义**：展示推导过程的树形结构，内部节点是非终结符，叶子节点是终结符
- **说明**：根节点是开始符号；每个内部节点和其子节点对应一条产生式；抽象语法树（AST）是分析树的压缩形式
- **同义词**：Derivation Tree（推导树）
- **相关**：AST（抽象语法树）、Grammar（文法）、Derivation（推导）

### Production Rule / 产生式
- **中文**：产生式
- **定义**：文法中描述符号替换规则的式子，形式为 左部 → 右部
- **说明**：如 E → E + T | T；左部是非终结符；右部是终结符和非终结符的串；是定义语言的核心
- **同义词**：Production、Rewrite Rule（重写规则）
- **相关**：Grammar（文法）、Non-Terminal（非终结符）、Derivation（推导）

### Sentence / 句子
- **中文**：句子
- **定义**：文法产生的、仅由终结符组成的合法串
- **说明**：是语言的元素；程序是编程语言文法的一个句子；语法分析器检查输入是否为文法的句子
- **相关**：Grammar（文法）、Language（语言）、Terminal（终结符）

### Terminal / 终结符
- **中文**：终结符
- **定义**：文法中不能再被推导的基本符号，是语言的实际词汇单元
- **说明**：通常用小写字母或具体符号表示；对应词法分析器输出的 Token；是分析树的叶子节点
- **相关**：Non-Terminal（非终结符）、Token（词法单元）、Grammar（文法）

### Yield / 产出
- **中文**：产出
- **定义**：分析树从左到右排列的所有叶子节点（终结符）组成的串
- **说明**：分析树的产出是一个句子；推导的最终结果就是产出；语法分析的目标就是构建产出为输入串的分析树
- **相关**：Parse Tree（分析树）、Sentence（句子）、Derivation（推导）

---

## 自顶向下分析

### Abstract Syntax Tree (AST) / 抽象语法树
- **中文**：抽象语法树
- **定义**：分析树的压缩形式，只保留语法结构必要信息、去除冗余节点
- **说明**：去掉括号、关键字等冗余；每个节点表示一个语法结构（如表达式、语句）；是编译器中间表示的主要形式
- **相关**：Parse Tree（分析树）、Syntax Analysis（语法分析）、Code Generation（代码生成）

### First Set / First 集合
- **中文**：First 集合
- **定义**：从文法符号串 α 推导出的所有可能句子的首终结符集合
- **说明**：计算：First(ε) = {ε}；First(aα) = {a}；First(Aα) = First(A)（若 A 可推 ε 则继续 α）；用于 LL 分析表构造和预测分析
- **相关**：Follow Set（Follow 集合）、LL Parser（LL 解析器）、Predictive Parsing（预测分析）

### Follow Set / Follow 集合
- **定义**：文法符号 A 后面可能出现的所有终结符集合
- **说明**：Follow(S) 包含 $（输入结束标记）；若 A → αBβ，则 First(β)-{ε} ⊆ Follow(B)；若 β 可推 ε 或 A → αB，则 Follow(A) ⊆ Follow(B)；用于 LL 分析
- **相关**：First Set（First 集合）、LL Parser（LL 解析器）、Non-Terminal（非终结符）

### Left Factoring / 提取左因子
- **中文**：提取左因子
- **定义**：将具有相同前缀的产生式改写为公共前缀加新非终结符的技术
- **说明**：A → αβ | αγ 改写为 A → αA'，A' → β | γ；消除解析时的不确定性；是自顶向下分析的必要步骤
- **相关**：Left Recursion（左递归）、LL Parser（LL 解析器）、Grammar Transformation（文法变换）

### LL Parser / LL 解析器
- **中文**：LL 解析器
- **定义**：自顶向下、从左到右扫描输入、进行最左推导的确定型解析器
- **说明**：LL(k) 表示向前看 k 个符号；LL(1) 最常用（一个 lookahead）；要求文法无左递归且提取左因子；可用递归下降或预测分析表实现
- **相关**：Recursive Descent（递归下降）、Predictive Parsing（预测分析）、First Set（First 集合）

### Predictive Parsing / 预测分析
- **中文**：预测分析
- **定义**：根据当前非终结符和 lookahead 符号、用预测分析表确定使用哪个产生式的 LL 分析方法
- **说明**：非递归实现（使用显式栈）；分析表由 First 和 Follow 集合构造；若表项无冲突则文法是 LL(1)
- **相关**：LL Parser（LL 解析器）、Parsing Table（分析表）、First Set（First 集合）

### Recursive Descent / 递归下降
- **中文**：递归下降
- **定义**：为每个非终结符编写一个递归函数、根据 lookahead 选择产生式的自顶向下解析方法
- **说明**：直观易实现；要求文法是 LL(1)；每个非终结符对应一个函数；直接反映文法结构；手工编写解析器的常用方法
- **相关**：LL Parser（LL 解析器）、Top-Down Parsing（自顶向下分析）、Parser（解析器）

### Top-Down Parsing / 自顶向下分析
- **中文**：自顶向下分析
- **定义**：从根节点（开始符号）出发、向叶子节点推导构建分析树的解析方法
- **说明**：分为递归下降和预测分析；直观但受限（需消除左递归）；适合 LL 文法；不能处理左递归文法
- **相关**：Bottom-Up Parsing（自底向上分析）、LL Parser（LL 解析器）、Recursive Descent（递归下降）

---

## 自底向上分析

### Bottom-Up Parsing / 自底向上分析
- **中文**：自底向上分析
- **定义**：从叶子节点（终结符）出发、向上归约构建分析树的解析方法
- **说明**：也称为移进-归约分析（Shift-Reduce Parsing）；比自顶向下更强大；可处理更多文法；代表：LR 解析器
- **相关**：Top-Down Parsing（自顶向下分析）、Shift-Reduce Parsing（移进-归约分析）、LR Parser（LR 解析器）

### Canonical LR / 规范 LR
- **中文**：规范 LR
- **定义**：使用所有 LR(1) 项集构造的、能力最强的 LR 解析器
- **说明**：LR(1) 项 = 产生式 + 圆点位置 + 向前看符号；状态数可能很多；实用中使用 SLR 或 LALR 简化
- **相关**：LR Parser（LR 解析器）、LR(1)、LALR

### Conflict / 冲突
- **中文**：冲突
- **定义**：解析表中某个单元格有多个动作、导致解析器无法确定下一步的情况
- **说明**：移进-归约冲突（Shift-Reduce Conflict）：可移进也可归约；归约-归约冲突（Reduce-Reduce Conflict）：多个产生式可归约；说明文法不是 LR
- **相关**：LR Parser（LR 解析器）、Ambiguity（歧义性）、Parsing Table（分析表）

### Handle / 句柄
- **中文**：句柄
- **定义**：句型中匹配某个产生式右部的子串，且该子串的归约对应最右推导的逆过程
- **说明**：自底向上分析的核心概念；句柄是应当被归约的子串；识别句柄是移进-归约分析的关键
- **相关**：Shift-Reduce Parsing（移进-归约分析）、Bottom-Up Parsing（自底向上分析）、Reduction（归约）

### LALR / LALR
- **中文**：Look Ahead LR
- **定义**：通过合并 LR(1) 项集中核心（忽略向前看符号）相同的状态来减少状态数的 LR 解析器
- **说明**：状态数与 SLR 相同，能力接近 LR(1)；Yacc/Bison 使用 LALR(1)；现代编译器（如 GCC）使用更强大的 IELR
- **相关**：LR Parser（LR 解析器）、SLR、Yacc

### LR Parser / LR 解析器
- **中文**：LR 解析器
- **定义**：自底向上、从左到右扫描输入、进行最右推导的逆（最左归约）的确定型解析器
- **说明**：最通用的确定型解析器；LR(0) 最简单但能力弱；SLR、LALR(1)、LR(1) 能力递增；Yacc/Bison 生成 LALR(1)
- **相关**：LALR、SLR、Shift-Reduce Parsing（移进-归约分析）

### Reduce / 归约
- **中文**：归约
- **定义**：自底向上分析中将栈顶的句柄替换为对应产生式左部非终结符的操作
- **说明**：归约是推导的逆过程；每次归约对应分析树中一个内部节点的创建；目标是归约到开始符号
- **相关**：Shift（移进）、Handle（句柄）、Bottom-Up Parsing（自底向上分析）

### Reduction / 归约
- **中文**：归约
- **定义**：在自底向上分析中，将子串替换为产生式左部非终结符的操作
- **说明**：对应最右推导的逆步骤；每次归约减少栈中符号数；最终目标是归约到开始符号并接受输入
- **相关**：Reduce（归约）、Shift（移进）、Handle（句柄）

### Shift / 移进
- **中文**：移进
- **定义**：自底向上分析中将输入符号压入分析栈的操作
- **说明**：与归约交替进行；移进直到栈顶形成句柄；然后归约；是移进-归约分析的基本动作
- **相关**：Reduce（归约）、Shift-Reduce Parsing（移进-归约分析）、Parsing Stack（分析栈）

### Shift-Reduce Parsing / 移进-归约分析
- **中文**：移进-归约分析
- **定义**：自底向上解析方法，通过反复移进输入符号或归约栈顶句柄来构建分析树
- **说明**：核心问题：何时移进、何时归约、归约哪个产生式；用分析表（Action/Goto）指导；LR 解析器是确定型的移进-归约分析
- **相关**：LR Parser（LR 解析器）、Bottom-Up Parsing（自底向上分析）、Handle（句柄）

### SLR (Simple LR) / 简单 LR
- **中文**：简单 LR
- **定义**：使用 LR(0) 项集和 Follow 集合构造的简化 LR 解析器
- **说明**：比 LALR 和 LR(1) 弱；构造简单；某些文法会产生不必要的冲突；教学常用，工业少用
- **相关**：LR Parser（LR 解析器）、LALR、Follow Set（Follow 集合）

## 语法分析辅助

### Chomsky Hierarchy / 乔姆斯基层级
- **中文**：乔姆斯基层级
- **定义**：由诺姆·乔姆斯基提出的、按表达能力对形式文法进行分类的四个层级
- **说明**：Type-0（无限制文法，图灵机）→ Type-1（上下文有关文法）→ Type-2（上下文无关文法）→ Type-3（正则文法，有限自动机）；层级越低表达能力越强
- **相关**：Context-Free Grammar（上下文无关文法）、Regular Language（正则语言）、Turing Machine（图灵机）

### Operator Precedence / 运算符优先级
- **中文**：运算符优先级
- **定义**：定义不同运算符在表达式中计算先后顺序的规则
- **说明**：如 * 优先级高于 +；用于消除表达式文法的歧义；解析器使用优先级表解决移进-归约冲突
- **相关**：Associativity（结合性）、Ambiguity（歧义性）、Expression（表达式）

### Precedence / 优先级
- **中文**：优先级
- **定义**：运算符或产生式在解析时的优先顺序
- **说明**：高优先级运算符先结合；用于消除歧义（如 if-else 的悬挂问题）；Yacc/Bison 中可声明优先级
- **相关**：Operator Precedence（运算符优先级）、Associativity（结合性）、Parser Generator（解析器生成器）

### Syntax Error / 语法错误
- **中文**：语法错误
- **定义**：源代码违反语言语法规则的错误
- **说明**：如缺少分号、括号不匹配、关键字拼写错误；语法分析器检测并报告；恢复策略：恐慌模式、短语级恢复、错误产生式
- **相关**：Semantic Error（语义错误）、Lexical Error（词法错误）、Error Recovery（错误恢复）

### Syntax-Directed Translation / 语法制导翻译
- **中文**：语法制导翻译
- **定义**：在语法分析的同时执行语义动作（如代码生成）的技术
- **说明**：为文法产生式附加语义规则；分析树遍历时计算属性值；是编译器前端连接语义分析和代码生成的桥梁
- **相关**：Semantic Analysis（语义分析）、Attribute Grammar（属性文法）、Code Generation（代码生成）
