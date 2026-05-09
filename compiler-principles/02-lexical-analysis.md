# 02. 词法分析 (Lexical Analysis)

## 基础概念

### Alphabet / 字母表
- **中文**：字母表
- **定义**：语言中允许使用的字符的有限集合
- **说明**：如 ASCII、Unicode；编程语言的字母表通常包含字母、数字、运算符和空白字符；是定义语言和文法的基础
- **相关**：String（字符串）、Language（语言）、Regular Expression（正则表达式）

### Deterministic Finite Automaton (DFA) / 确定有限自动机
- **中文**：确定有限自动机
- **定义**：每个状态对每个输入字符有且只有一个转移路径的有限状态机
- **说明**：易于实现（跳转表）；没有 ε 转移；用于词法分析器实现；可由 NFA 转换而来
- **相关**：NFA、Finite Automaton（有限自动机）、State Transition（状态转移）

### Finite Automaton (FA) / 有限自动机
- **中文**：有限自动机
- **定义**：具有有限个状态、根据输入字符在状态间转移的抽象计算模型
- **说明**：分为 DFA（确定型）和 NFA（非确定型）；是识别正则语言的计算模型；词法分析的理论基础
- **相关**：DFA、NFA、Regular Language（正则语言）

### Keyword / 关键字
- **中文**：关键字
- **定义**：编程语言中保留的、具有特殊含义的词法单元
- **说明**：如 if、else、while、return、class；不能用作标识符；通常不区分大小写（视语言而定）
- **同义词**：Reserved Word（保留字）
- **相关**：Token（词法单元）、Identifier（标识符）、Lexer（词法分析器）

### Lex / Lex
- **中文**：Lex
- **定义**：经典的词法分析器生成器，根据正则表达式规则自动生成扫描器
- **说明**：输入：正则表达式 + 动作；输出：C 语言词法分析器；GNU 版本：Flex；常与 Yacc/Bison 配合使用
- **相关**：Flex、Lexer Generator（词法分析器生成器）、Regular Expression（正则表达式）

### Lexer / 词法分析器
- **中文**：词法分析器
- **定义**：执行词法分析、将字符流转换为 Token 序列的程序
- **说明**：也叫 Scanner（扫描器）或 Tokenizer；跳过空白和注释；识别关键字、标识符、常量；可用工具（Lex/Flex）自动生成
- **同义词**：Scanner、Tokenizer、Lexical Analyzer
- **相关**：Token（词法单元）、Regular Expression（正则表达式）、DFA

### Literal / 常量
- **中文**：常量（字面量）
- **定义**：源代码中直接表示固定值的词法单元
- **说明**：类型：整数字面量（42）、浮点字面量（3.14）、字符串字面量（"hello"）、布尔字面量（true/false）、字符字面量（'a'）
- **同义词**：Constant
- **相关**：Token（词法单元）、Value（值）、Data Type（数据类型）

### Lookahead / 向前看
- **中文**：向前看
- **定义**：词法分析器读取当前字符后、需要查看后续字符才能确定当前 Token 类型的技术
- **说明**：例如区分 "==" 和 "="；lookahead 数量有限；某些语言需要无限 lookahead（如 Fortran）
- **相关**：Lexer（词法分析器）、Token（词法单元）、Parsing（解析）

### NFA (Non-Deterministic Finite Automaton) / 非确定有限自动机
- **中文**：非确定有限自动机
- **定义**：允许同一输入对应多个转移路径或 ε 转移（不消耗输入）的有限状态机
- **说明**：更容易从正则表达式构造；可通过子集构造法（Subset Construction）转换为等价的 DFA；NFA 和 DFA 识别能力相同
- **相关**：DFA、Epsilon Transition（ε 转移）、Subset Construction（子集构造法）

### Nondeterminism / 非确定性
- **中文**：非确定性
- **定义**：自动机或计算模型中，给定状态和输入可能存在多个可能的转移
- **说明**：NFA 具有非确定性；在理论分析中更便利；实现时需通过确定化或回溯模拟
- **相关**：NFA、DFA、Backtracking（回溯）

### Pattern / 模式
- **中文**：模式
- **定义**：描述一类词法单元特征的正则表达式或规则
- **说明**：如标识符模式：[a-zA-Z_][a-zA-Z0-9_]*；整数模式：[0-9]+；词法分析器按模式匹配输入字符
- **相关**：Regular Expression（正则表达式）、Token（词法单元）、Lexer（词法分析器）

### Regular Expression (Regex) / 正则表达式
- **中文**：正则表达式
- **定义**：描述正则语言的模式匹配语法，用于定义词法单元
- **说明**：基本操作：连接、选择（|）、闭包（*）、正闭包（+）、可选（?）；是定义 Token 的数学工具；与有限自动机等价
- **同义词**：Regex、Regexp
- **相关**：Regular Language（正则语言）、DFA、NFA、Pattern（模式）

### Regular Language / 正则语言
- **中文**：正则语言
- **定义**：可由正则表达式描述、或由有限自动机识别的形式语言类
- **说明**：最简单的乔姆斯基层级语言（Chomsky Type-3）；不能描述嵌套结构（如匹配括号）；是词法分析的理论基础
- **相关**：Regular Expression（正则表达式）、Finite Automaton（有限自动机）、Chomsky Hierarchy（乔姆斯基层级）

### State / 状态
- **中文**：状态
- **定义**：有限自动机中的节点，表示识别过程中的某个阶段
- **说明**：初态（Start State）：自动机开始状态；终态（Accepting/Final State）：识别成功的状态；转移：状态间的连接
- **相关**：Finite Automaton（有限自动机）、State Transition（状态转移）、Accepting State（接受状态）

### State Transition / 状态转移
- **中文**：状态转移
- **定义**：有限自动机根据输入字符从一个状态转到另一个状态的行为
- **说明**：用状态转移图或转移表表示；DFA 每个（状态，输入）对唯一确定下一个状态；ε 转移不消耗输入
- **相关**：DFA、NFA、Transition Table（转移表）

### Token / 词法单元
- **中文**：词法单元
- **定义**：词法分析输出的、具有语义意义的最小语法单位
- **说明**：包含类型（Token Type）和值（Lexeme）；如 IDENTIFIER("count")、NUMBER(42)、PLUS("+")；是语法分析的输入
- **同义词**：Lexeme（词素）
- **相关**：Lexer（词法分析器）、Syntax Analysis（语法分析）、Grammar（文法）

### Transition Table / 转移表
- **中文**：转移表
- **定义**：用二维数组表示有限自动机状态转移的数据结构
- **说明**：行：状态；列：输入字符；元素：下一个状态；DFA 可直接用转移表实现；查找时间 O(1)
- **相关**：DFA、State Transition（状态转移）、Finite Automaton（有限自动机）

## 高级主题

### Epsilon Closure / ε 闭包
- **中文**：ε 闭包
- **定义**：从某个状态出发、只通过 ε 转移（不消耗输入）能到达的所有状态的集合
- **说明**：子集构造法的核心操作；将 NFA 转换为 DFA 时计算状态集合；通常用 BFS/DFS 计算
- **相关**：NFA、Subset Construction（子集构造法）、Epsilon Transition（ε 转移）

### Epsilon Transition / ε 转移
- **中文**：ε 转移
- **定义**：不消耗输入字符、只改变状态的自动机转移
- **说明**：NFA 特有；方便表示可选、连接和重复；DFA 不允许 ε 转移；在 NFA 转 DFA 时消除
- **同义词**：Empty Transition、Lambda Transition
- **相关**：NFA、Epsilon Closure（ε 闭包）、DFA

### Finite State Machine (FSM) / 有限状态机
- **中文**：有限状态机
- **定义**：具有有限个状态、根据输入在状态间转移的数学计算模型
- **说明**：与有限自动机（FA）基本同义；分为 Mealy 机（输出与转移相关）和 Moore 机（输出与状态相关）；广泛用于协议设计和词法分析
- **同义词**：Finite Automaton（有限自动机）
- **相关**：DFA、NFA、State Machine（状态机）

### Kleene Closure / 克林闭包
- **中文**：克林闭包
- **定义**：对语言 L，L* 表示由 L 中零个或多个字符串连接而成的所有字符串的集合
- **说明**：正则表达式中 * 操作符；包含空串 ε；L+ = LL* 为正闭包（至少一个）
- **相关**：Regular Expression（正则表达式）、Regular Language（正则语言）、Concatenation（连接）

### Lexical Error / 词法错误
- **中文**：词法错误
- **定义**：源代码中出现无法识别为任何 Token 的字符序列
- **说明**：如非法字符、未终止的字符串、数字格式错误；通常以 panic 模式恢复：跳过字符直到找到合法 Token
- **相关**：Syntax Error（语法错误）、Error Recovery（错误恢复）、Lexer（词法分析器）

### Longest Match / 最长匹配
- **中文**：最长匹配
- **定义**：词法分析中选择能匹配最长输入序列的 Token 规则的策略
- **说明**：默认策略；例如 ">=" 应匹配为单个 GE 操作符而非 ">" 和 "="；避免歧义的关键规则
- **相关**：Lexer（词法分析器）、Token（词法单元）、Lookahead（向前看）

### Panic Mode / 恐慌模式
- **中文**：恐慌模式
- **定义**：编译器遇到错误时，跳过输入直到找到同步 Token 再继续分析的错误恢复策略
- **说明**：最简单的错误恢复方法；词法分析中跳过非法字符；语法分析中跳过分隔符（如分号、右括号）；可能跳过大量输入
- **相关**：Error Recovery（错误恢复）、Synchronization（同步）、Lexer（词法分析器）

### Reserved Word / 保留字
- **中文**：保留字
- **定义**：编程语言中不能用作标识符的词汇，包括关键字和将来可能使用的词
- **说明**：所有关键字都是保留字；保留字不一定是关键字（如 Java 中的 goto 是保留字但不是关键字）；避免命名冲突
- **相关**：Keyword（关键字）、Identifier（标识符）、Lexer（词法分析器）

### Subset Construction / 子集构造法
- **中文**：子集构造法
- **定义**：将 NFA 转换为等价的 DFA 的算法，通过计算 ε 闭包和状态子集
- **说明**：NFA 的 n 个状态可能产生 2^n 个 DFA 状态；实际中大多不可达状态不会被构造；是词法分析器自动生成的理论基础
- **相关**：NFA、DFA、Epsilon Closure（ε 闭包）

### Thompson's Construction / Thompson 构造法
- **中文**：Thompson 构造法
- **定义**：将正则表达式系统性地转换为等价的 NFA 的算法
- **说明**：由 Ken Thompson 提出；递归构造：基本表达式 → NFA，组合表达式 → 组合 NFA；是 Lex/Flex 等工具的基础
- **相关**：Regular Expression（正则表达式）、NFA、Lexer Generator（词法分析器生成器）
