# 03. 分隔符与包裹符 (Delimiters & Enclosures)

### Triple Quotes / 三引号
- **中文**：三引号
- **定义**：用于多行字符串或文档字符串的三重引号
- **说明**：Python：多行字符串、docstring；JavaScript/TypeScript 不支持原生三引号（用反引号代替）；SQL 中某些方言支持；方便包含换行和引号
- **相关**：''、``、Multi-line String（多行字符串）、Docstring（文档字符串）

### Parentheses / 圆括号
- **中文**：圆括号
- **定义**：用于函数调用、表达式分组、元组或控制流的多功能符号
- **说明**：函数调用：fn()；分组：(a + b) * c；元组：(1, 2, 3)；控制流：if (condition)；生成器：(x for x in range(10))；箭头函数参数：(x) => x；类型转换：int()
- **相关**：[]、{}、Function Call（函数调用）、Tuple（元组）

### Single Quotes / 单引号
- **中文**：单引号
- **定义**：用于包裹字符串字面量的符号
- **说明**：Python/JavaScript/Ruby：'string' 和 "string" 等价；SQL：'string literal'；C/C++/Java：单引号用于字符（char）'a'；HTML 属性：value='text'
- **相关**：""、``、String Literal（字符串字面量）、Char（字符）

### Double Quotes / 双引号
- **中文**：双引号
- **定义**：用于包裹字符串字面量的符号
- **说明**：C/C++/Java/JavaScript："string"；JSON 键和值必须用双引号；Shell 中保留变量扩展："$HOME"；SQL 中标识符（某些方言）；与单引号可互换（部分语言）
- **相关**：''、``、String Literal（字符串字面量）、JSON

### Backtick / 反引号
- **中文**：反引号
- **定义**：用于模板字符串、命令替换或标识符引用的符号
- **说明**：JavaScript/TypeScript：模板字符串 `Hello ${name}`；Shell：命令替换 `date`（现代推荐 $(date)）；MySQL：引用标识符 `table_name`；Markdown：行内代码 `code`
- **相关**：''、""、Template Literal（模板字符串）、Command Substitution（命令替换）

### Square Brackets / 方括号
- **中文**：方括号
- **定义**：用于数组索引、列表字面量、属性访问或泛型的符号
- **说明**：数组索引：arr[0]；列表：[1, 2, 3]；属性访问：obj['key']；泛型：List<T>；Python 列表/字典；解构赋值；正则表达式字符类：[abc]
- **相关**：()、{}、Array（数组）、Index（索引）

### Curly Braces / 花括号
- **中文**：花括号
- **定义**：用于代码块、对象/字典字面量、集合或占位符的符号
- **说明**：代码块：function() { ... }；对象：{a: 1, b: 2}；集合：{1, 2, 3}；格式化字符串：f"{var}"；模板占位符：${var}；JSON；CSS 规则块
- **相关**：()、[]、Block（代码块）、Object（对象）

### Slash / 斜杠
- **中文**：斜杠
- **定义**：用于路径分隔、除法或正则表达式定界的符号
- **说明**：Unix 路径：/home/user；URL：http://example.com/；除法：a / b；正则表达式：/pattern/flags；注释：//、/* */；XML/HTML 闭合标签：</tag>
- **相关**：\、Path（路径）、Division（除法）

### Colon / 冒号
- **中文**：冒号
- **定义**：用于键值对分隔、语句结束、类型注解或切片的符号
- **说明**：键值对：key: value；Python 控制流：if x:；三元运算符：a ? b : c；类型注解：x: number；URL 协议：scheme://；时间：12:00；切片：arr[1:5]
- **相关**：;、Key-Value Pair（键值对）、Type Annotation（类型注解）

### Semicolon / 分号
- **中文**：分号
- **定义**：用于语句结束或分隔的标点符号
- **说明**：C/C++/Java/JavaScript 语句结束符；for 循环内分隔：for (i=0; i<n; i++)；SQL 语句结束；CSS 属性分隔；Python 中可选（一行多语句时必需）
- **相关**：:、Statement Terminator（语句终止符）

### Angle Brackets / 尖括号
- **中文**：尖括号
- **定义**：用于泛型参数、HTML/XML 标签或比较运算的符号
- **说明**：泛型：List<String>、Map<K, V>；HTML：<div>、</div>；XML：<?xml version="1.0"?>；比较：a < b、a > b；类型参数约束：T extends Comparable<T>
- **相关**：()、[]、Generic（泛型）、HTML Tag（HTML 标签）

### Pipe / 竖线/管道符
- **中文**：竖线/管道符
- **定义**：用于按位或、管道连接或类型联合的符号
- **说明**：Shell 管道：cmd1 | cmd2；按位或：a | b；正则表达式选择：a|b；TypeScript 联合类型：string | number；Rust 模式匹配：match x { A | B => ... }；表格分隔（Markdown）
- **相关**：||、&、Pipe（管道）

### Double Pipe / 双竖线
- **中文**：双竖线
- **定义**：用于逻辑或或默认值设置的双竖线运算符
- **说明**：逻辑或：a || b；默认值：val = input || default；短路求值；Shell 中 || 表示前命令失败时执行后命令
- **相关**：&&、??、Logical OR（逻辑或）

### Ellipsis / Spread / 展开/省略号
- **中文**：展开/省略号
- **定义**：用于剩余参数、展开运算符或省略表示的三点符号
- **说明**：JavaScript：剩余参数 fn(...args)、展开数组 [...arr1, ...arr2]；Python：*args、**kwargs；Rust：.. 范围；C/C++ 变参函数：int printf(const char* fmt, ...)；通用省略号
- **相关**：*、Spread Operator（展开运算符）、Rest Parameter（剩余参数）

### Question Mark / 问号
- **中文**：问号
- **定义**：用于条件运算、可选标记或通配符的符号
- **说明**：三元运算符：condition ? a : b；可选链：obj?.prop；可选参数：fn(x?: number)；正则：?（零次或一次）；通配符：file?.txt；泛型约束：T extends U ? X : Y
- **相关**：?:、?.、Optional（可选）

### At Sign / At 符号
- **中文**：At 符号
- **定义**：用于装饰器、注解或矩阵乘法的符号
- **说明**：Python/JS/TS 装饰器：@decorator；Java 注解：@Override；Python 3.5+ 矩阵乘法：A @ B；电子邮件分隔符；社交媒体提及；路径别名前缀（Webpack/Vite）
- **相关**：Decorator（装饰器）、Annotation（注解）

### Hash / 井号
- **中文**：井号
- **定义**：用于注释、预处理器、私有字段或标题标记的符号
- **说明**：注释：#（Python/Ruby/Shell）、//（C 风格）；预处理器：#include、#define；私有字段：class C { #private }；Markdown 标题：## H2；URL 片段：#section；shebang：#!/bin/sh
- **相关**：#!、//、/* */、Comment（注释）

### Dollar Sign / 美元符号
- **中文**：美元符号
- **定义**：用于变量前缀、字符串插值或正则表达式结束锚点的符号
- **说明**：Shell/PHP/Perl 变量：$var；JavaScript 模板字符串插值：${var}；jQuery：$()；正则表达式结束锚点：$（行尾）；提示符：$（普通用户）；LaTeX 数学模式
- **相关**：Variable（变量）、Template Literal（模板字符串）、Regex Anchor（正则锚点）

### Percent / 百分号
- **中文**：百分号
- **定义**：用于取模运算、格式化字符串或 URL 编码的符号
- **说明**：取模：a % b；Python 旧格式化："%s %d" % ("hi", 1)；URL 编码：%20（空格）；CSS 单位：50%；Markdown 中无特殊含义；LaTeX 注释
- **相关**：Modulo（取模）、URL Encoding（URL 编码）、Format String（格式化字符串）

### Ampersand / 与号
- **中文**：与号
- **定义**：用于按位与、取地址或逻辑与（某些语言）的符号
- **说明**：C/C++ 取地址：&var；按位与：a & b；引用类型：int &ref = var；HTML 实体：&amp;；URL 参数分隔：?a=1&b=2；正则表达式：&（某些方言）
- **相关**：&&、|、Address-of（取地址）、Reference（引用）

### Asterisk / 星号
- **中文**：星号
- **定义**：用于乘法、指针、解引用、通配符或注释的符号
- **说明**：乘法：a * b；指针：int *p；解引用：*p；通配符：*.txt；注释块：/* */；正则：*（零次或多次）；Markdown 列表：* item；Python **kwargs
- **相关**：**、Pointer（指针）、Wildcard（通配符）

### Plus / 加号
- **中文**：加号
- **定义**：用于加法、正号或连接的多功能符号
- **说明**：加法：a + b；正号：+a；字符串连接："a" + "b"；URL 空格编码：+；正则：+（一次或多次）；Markdown 标题：+（Setext 风格，较少用）；CSS 相邻兄弟选择器
- **相关**：-、++、Arithmetic Operator（算术运算符）

### Equals / 等号
- **中文**：等号
- **定义**：用于赋值或相等比较的符号
- **说明**：赋值：a = 1；比较：==（相等）、===（严格相等）；箭头函数：=>；默认参数：fn(x = 1)；解构赋值：[a, b] = [1, 2]；与 == 的区别
- **相关**：==、===、=>、Assignment（赋值）
