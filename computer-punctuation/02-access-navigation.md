# 02. 访问与导航 (Access & Navigation)

### Hash / 井号
- **中文**：井号
- **定义**：用于注释、预处理器指令、私有字段或标记的多功能符号
- **说明**：Python/Ruby/Shell 注释：# comment；C/C++ 预处理器：#include、#define；JavaScript 私有字段：#privateField；Markdown 标题：# H1；URL 片段标识：page#section
- **相关**：//、/* */、Preprocessor（预处理器）、Private Field（私有字段）

### Double Hash / 双井号
- **中文**：双井号
- **定义**：C/C++ 预处理器中连接两个标记的运算符
- **说明**：宏定义中使用：#define CONCAT(a,b) a##b → CONCAT(x,y) 得到 xy；用于生成变量名或函数名
- **相关**：#、#define、Macro（宏）、Preprocessor（预处理器）

### Shebang / Shebang
- **中文**：Shebang
- **定义**：脚本文件第一行指定解释器路径的特殊标记
- **说明**：格式：#!/usr/bin/env python3；操作系统根据此路径调用解释器执行脚本；常见于 Shell、Python、Ruby 脚本；必须位于文件第一行
- **同义词**：Hashbang
- **相关**：Interpreter（解释器）、Script（脚本）、Executable（可执行文件）

### At Sign / At 符号
- **中文**：At 符号
- **定义**：用于装饰器、注解、提及或电子邮件的多功能符号
- **说明**：Python/JavaScript/TypeScript 装饰器：@decorator；Java 注解：@Override；Python 矩阵乘法：A @ B；电子邮件：user@domain.com；社交媒体提及
- **相关**：Decorator（装饰器）、Annotation（注解）、Matrix Multiplication（矩阵乘法）

### Asterisk / 星号
- **中文**：星号
- **定义**：用于乘法、指针、解引用、通配符或可变参数的多功能符号
- **说明**：算术：a * b；C/C++ 指针：int *p、*p（解引用）；Python 解包：*args、**kwargs；通配符：*.txt；注释标记：/* */；正则表达式：匹配零次或多次
- **相关**：Pointer（指针）、Dereference（解引用）、Wildcard（通配符）

### Double Asterisk / 双星号
- **中文**：双星号
- **定义**：用于幂运算或关键字参数解包的双星号符号
- **说明**：Python：a ** b（幂运算）、**kwargs（字典解包）；Markdown：粗体 **text**；Glob：**.txt（递归匹配）；数学注释：脚注标记
- **相关**：*、Exponentiation（幂运算）、Unpacking（解包）

### Arrow / 箭头
- **中文**：箭头
- **定义**：用于指针成员访问、函数返回类型或 lambda 的运算符
- **说明**：C/C++：ptr->member；Rust/C++11：fn() -> Type（返回类型）；某些语言 lambda：x -> x*2；与 => 的区别
- **相关**：.、=>、Pointer（指针）、Return Type（返回类型）

### Dot / Period / 点号/句号
- **中文**：点号/句号
- **定义**：访问对象成员、小数点或包路径分隔的多功能符号
- **说明**：成员访问：obj.method()；小数点：3.14；包路径：com.company.project；相对路径：./file；级联调用；正则表达式：匹配任意字符
- **相关**：->、Member Access（成员访问）、Package（包）

### Double Dot / 双点号
- **中文**：双点号
- **定义**：用于父目录访问或范围表示的双点符号
- **说明**：文件路径：../parent（父目录）；Python：from ..module import；Ruby：范围 1..5（含结束）；Go：多值返回中忽略值：_, _ = fn()
- **相关**：.、Path（路径）、Range（范围）

### Ellipsis / Spread / 展开/省略
- **中文**：展开/省略
- **定义**：用于展开运算符、可变参数或省略表示的三点符号
- **说明**：JavaScript/TypeScript：展开 [...arr]、剩余参数 fn(...args)；Python：*args（函数内），列表解包 [*a, *b]；Rust：.. 范围；通用省略号
- **相关**：*、Spread Operator（展开运算符）、Rest Parameter（剩余参数）

### Slash / 斜杠
- **中文**：斜杠
- **定义**：用于除法、路径分隔或注释开始的多功能符号
- **说明**：算术除法：a / b；Unix 路径分隔：/home/user；URL 路径：example.com/path；注释：//、/* */；正则表达式定界符：/pattern/
- **相关**：\、Path Separator（路径分隔符）、Division（除法）

### Colon / 冒号
- **中文**：冒号
- **定义**：用于语句结束、键值对、类型注解或切片的多功能符号
- **说明**：Python 语句：if x > 0:；JSON：{"key": "value"}；TypeScript 类型：let x: number；三元运算符：condition ? a : b；时间：12:30；URL 协议：http://
- **相关**：;、Key-Value Pair（键值对）、Type Annotation（类型注解）

### Double Colon / 双冒号
- **中文**：双冒号
- **定义**：用于作用域解析、命名空间访问或类型引用的双冒号运算符
- **说明**：C++：std::cout、ClassName::method()；PHP：ClassName::staticMethod()；Rust：module::function()；Python 3.10+ 类型别名；文件路径（Windows 盘符 C::）
- **相关**：.、Namespace（命名空间）、Scope Resolution（作用域解析）

### Semicolon / 分号
- **中文**：分号
- **定义**：用于语句结束或分隔的标点符号
- **说明**：C/C++/Java/JavaScript 语句结束：let x = 1;；for 循环分隔：for (i=0; i<n; i++)；SQL 语句结束；Python/Go 中可选或不用
- **相关**：:、Statement Terminator（语句终止符）

### Question Mark / 问号
- **中文**：问号
- **定义**：用于条件判断、可选链、通配符或正则表达式量词的符号
- **说明**：三元运算符：condition ? a : b；可选链：obj?.prop；TypeScript 可选参数：fn(x?: number)；正则：?（零次或一次）；泛型约束：T extends U ? X : Y；通配符：?
- **相关**：?:、?.、Optional（可选）、Wildcard（通配符）

### Optional Chaining / 可选链
- **中文**：可选链
- **定义**：当左侧对象存在时访问其属性、否则返回 undefined 的运算符
- **说明**：ES2020 引入；obj?.prop?.method?.()；避免深层属性访问时的空指针错误；短路求值；不能用于赋值左侧
- **相关**：??、?.[]、?.()、Nullish Coalescing（空值合并）

### Optional Call / 可选调用
- **中文**：可选调用
- **定义**：当函数存在时调用、否则返回 undefined 的运算符
- **说明**：ES2020 引入；obj.method?.()；obj 或 method 为 null/undefined 时返回 undefined 而非抛错；与 ?. 配合使用
- **相关**：?.、??、Optional Chaining（可选链）

### Optional Property Access / 可选属性访问
- **中文**：可选属性访问
- **定义**：通过计算属性名进行可选链访问的运算符
- **说明**：ES2020 引入；obj?.[propName]；当 obj 为 null/undefined 时返回 undefined；适用于动态属性名
- **相关**：?.、?.()、Optional Chaining（可选链）

### Square Brackets / 方括号
- **中文**：方括号
- **定义**：用于数组索引、属性访问、数组/列表字面量或泛型参数的符号
- **说明**：数组索引：arr[0]；属性访问：obj["property"]；数组字面量：[1, 2, 3]；泛型：List<T>（部分语言）；Python 列表/字典；解构赋值：[a, b] = arr
- **相关**：()、{}、Array（数组）、Index（索引）

### Backslash / 反斜杠
- **中文**：反斜杠
- **定义**：用于转义字符、行继续符或 Windows 路径分隔的符号
- **说明**：转义：\n（换行）、\t（制表符）、\\（反斜杠）；行继续：Python 中长行分割；Windows 路径：C:\Users\name；正则表达式：转义特殊字符
- **相关**：/、Escape Character（转义字符）、Line Continuation（行继续）

### Caret / 脱字符
- **中文**：脱字符/插入符号
- **定义**：用于按位异或、幂运算或正则表达式起始锚点的符号
- **说明**：Python：a ** b（幂运算替代）；按位异或：a ^ b；正则表达式：^ 匹配行首；类型标注：逆变；Ctrl 键符号：^C
- **相关**：XOR、Exponentiation（幂运算）、Regex Anchor（正则锚点）

### Underscore / 下划线
- **中文**：下划线
- **定义**：用于变量命名、私有约定、数字分隔或忽略值的多功能符号
- **说明**：蛇形命名：my_variable；私有约定：_private；Python 忽略值：for _ in range(10)；数字分隔：1_000_000；国际化函数：gettext _()；前一个表达式结果（REPL）
- **相关**：camelCase、snake_case、Naming Convention（命名规范）

### Curly Braces / 花括号
- **中文**：花括号
- **定义**：用于代码块、对象字面量、集合或格式字符串的符号
- **说明**：代码块：if (x) { ... }；对象/字典：{key: value}；集合：{1, 2, 3}；格式化：f"Hello {name}"；模板字符串：${}；JSON；解构赋值：{a, b} = obj
- **相关**：()、[]、Block（代码块）、Object Literal（对象字面量）

### Pipe / 管道符
- **中文**：管道符
- **定义**：用于按位或、逻辑或（某些语言）或 Shell 管道连接的符号
- **说明**：Shell：cmd1 | cmd2（将前者输出作为后者输入）；按位或：a | b；类型联合：TypeScript string | number；模式匹配：Rust match；Elixir/F# 管道：data |\> fn
- **相关**：||、&、Pipe（管道）、Union Type（联合类型）

### Double Pipe / 双竖线
- **中文**：双竖线
- **定义**：用于逻辑或或默认值设置的双竖线运算符
- **说明**：逻辑或：a || b；默认值：const val = input || "default"；短路求值；注意 falsy 值问题（0、''、false 会被替换）
- **相关**：&&、??、Logical OR（逻辑或）

### Tilde / 波浪号/ tilde
- **中文**：波浪号/ tilde
- **定义**：用于按位非、析构（Rust）、或主目录的符号
- **说明**：按位非：~a = -(a+1)；Shell 主目录：~user；TypeScript 接口中只读数组的索引签名；Rust：~ 用于析构；Node.js npm：~1.2.3 允许小版本更新
- **相关**：Bitwise NOT（按位非）、Home Directory（主目录）、semver
