# 04. 特殊语法符号 (Special Syntax)

### Bytes Prefix / 字节字符串前缀
- **中文**：字节字符串前缀
- **定义**：Python 中表示字节串（bytes）而非字符串的前缀
- **说明**：b"hello" 生成 bytes 对象；用于处理二进制数据、网络协议、文件 I/O；与 str 不同，bytes 是不可变的字节序列
- **相关**：f、r、u、Bytes（字节）、String Prefix（字符串前缀）

### Format Prefix / 格式化字符串前缀
- **中文**：格式化字符串前缀
- **定义**：Python 中创建格式化字符串（f-string）的前缀
- **说明**：f"Hello {name}" 自动将变量嵌入字符串；支持表达式：f"{x + y}"；格式说明：f"{pi:.2f}"；Python 3.6+ 引入；比 % 和 str.format() 更简洁高效
- **相关**：b、r、u、F-String（格式化字符串）、String Interpolation（字符串插值）

### Raw Prefix / 原始字符串前缀
- **中文**：原始字符串前缀
- **定义**：Python 中表示原始字符串（不处理转义）的前缀
- **说明**：r"C:\Users\name" 中的 \ 不被当作转义符；正则表达式常用：r"\d+"；与双写反斜杠等价但更可读
- **相关**：b、f、u、Raw String（原始字符串）、Escape Character（转义字符）

### Unicode Prefix / Unicode 字符串前缀
- **中文**：Unicode 字符串前缀
- **定义**：Python 2 中表示 Unicode 字符串的前缀
- **说明**：Python 2：u"你好" 创建 unicode 对象；Python 3 中所有字符串默认 Unicode，u 前缀保留但无实际作用；兼容性用途
- **相关**：b、f、r、Unicode、Python 2/3

### Alias / 别名关键字
- **中文**：别名关键字
- **定义**：用于导入别名或类型转换的关键字/符号组合
- **说明**：Python：import numpy as np；TypeScript：as 类型断言（value as Type）；SQL：SELECT column AS alias；C#：using Alias = Namespace.Type
- **相关**：import、Type Assertion（类型断言）、Alias（别名）

### Async / 异步关键字
- **中文**：异步关键字
- **定义**：声明异步函数或上下文的关键字
- **说明**：async function fn() {}；async/await 语法；函数返回 Promise；Python：async def、await；C#：async/await；避免回调地狱
- **相关**：await、Promise、Asynchronous Programming（异步编程）

### Await / 等待关键字
- **中文**：等待关键字
- **定义**：等待异步操作完成并返回结果的关键字
- **说明**：const result = await promise；只能在 async 函数内使用；暂停执行但不阻塞线程；Python/C#/JS 支持；使异步代码看起来像同步代码
- **相关**：async、Promise、Asynchronous Programming（异步编程）

### Default Export / 默认导出
- **中文**：默认导出
- **定义**：ES Module 中每个模块的单一主要导出
- **说明**：export default function() {}；import name from './module'；一个模块只能有一个 default 导出；与命名导出相对
- **相关**：export、import、Named Export（命名导出）、ES Module

### Export / 导出关键字
- **中文**：导出关键字
- **定义**：将模块中的变量、函数或类暴露给其他模块使用的关键字
- **说明**：命名导出：export { a, b }、export const x = 1；默认导出：export default；ES Module 标准；Node.js、浏览器、TypeScript 支持
- **相关**：import、default、ES Module、Module System（模块系统）

### From / 来源关键字
- **中文**：来源关键字
- **定义**：指定导入模块来源路径的关键字
- **说明**：import { x } from './module'；Python：from module import x；SQL：SELECT * FROM table；与 import 配合使用
- **相关**：import、export、Module System（模块系统）

### Import / 导入关键字
- **中文**：导入关键字
- **定义**：从其他模块引入代码使用的关键字
- **说明**：ES Module：import { x } from './module'；Python：import module；CommonJS：const x = require('module')；Rust：use crate::module；Go：import "package"
- **相关**：export、from、require、Module System（模块系统）

### Instanceof / 实例检查
- **中文**：实例检查
- **定义**：检查对象是否为某类实例的运算符
- **说明**：obj instanceof Class；JavaScript/Java 使用；运行时类型检查；与 typeof 的区别：typeof 检查原始类型，instanceof 检查原型链
- **相关**：typeof、is、Type Checking（类型检查）、OOP

### Is / 身份/类型检查
- **中文**：身份/类型检查
- **定义**：检查对象身份或类型的关键字/运算符
- **说明**：Python：a is b（检查同一对象）、isinstance(obj, Type)；C#：x is Type；TypeScript：类型保护；SQL：IS NULL、IS NOT NULL；与 == 不同：is 检查身份而非相等
- **相关**：==、instanceof、typeof、Identity（身份）

### New / 实例化关键字
- **中文**：实例化关键字
- **定义**：创建类实例的关键字
- **说明**：const obj = new Class()；分配内存并调用构造函数；JavaScript/C++/Java/C# 使用；Python 不需要 new 直接调用类；注意 JavaScript 中 new 的行为细节
- **相关**：constructor、class、OOP、Instantiation（实例化）

### Typeof / 类型检测
- **中文**：类型检测
- **定义**：返回操作数原始类型的运算符
- **说明**：typeof "hello" === "string"；返回："undefined"、"object"、"boolean"、"number"、"bigint"、"string"、"symbol"、"function"；注意 typeof null === "object" 是历史 Bug
- **相关**：instanceof、is、Type Checking（类型检查）

### Yield / 产出关键字
- **中文**：产出关键字
- **定义**：生成器函数中暂停执行并返回一个值的关键字
- **说明**：function* gen() { yield 1; yield 2; }；生成器可迭代；yield* 委托给另一个生成器；Python/C#/JS 支持；实现惰性计算
- **相关**：Generator（生成器）、Iterator（迭代器）、Lazy Evaluation（惰性求值）

### Yield Delegate / 委托产出
- **中文**：委托产出
- **定义**：将迭代委托给另一个可迭代对象或生成器的运算符
- **说明**：function* gen() { yield* [1, 2, 3]; }；等价于依次 yield 每个元素；简化嵌套生成器；Python：yield from
- **相关**：yield、Generator（生成器）、Iterator（迭代器）

### Arrow Function / 箭头函数
- **中文**：箭头函数
- **定义**：定义简洁匿名函数的语法
- **说明**：const fn = (x) => x * 2；无自己的 this，继承外层 this；不能作为构造函数；单行隐式返回；多行需花括号并显式 return
- **相关**：function、Lambda、this、Anonymous Function（匿名函数）

### Return Type Arrow / 箭头（返回类型）
- **中文**：箭头（返回类型）
- **定义**：用于指示函数返回类型的箭头符号
- **说明**：Rust：fn add(x: i32) -> i32 { x + 1 }；C++11 尾置返回类型：auto fn() -> int；PHP 7+：function(): Type；Swift：-> Type
- **相关**：=>、Function Signature（函数签名）、Return Type（返回类型）

### Scope Resolution / 作用域解析
- **中文**：作用域解析
- **定义**：访问命名空间或类静态成员的双冒号运算符
- **说明**：C++：std::cout、MyClass::staticMethod()；PHP：ClassName::CONSTANT；Ruby：Module::Class；Python 3.10+ 类型别名；Rust 无 :: 路径分隔（用 ::）
- **相关**：.、->、Namespace（命名空间）、Static Member（静态成员）

### Type Annotation / 类型注解
- **中文**：类型注解
- **定义**：在变量或参数后声明类型的冒号符号
- **说明**：TypeScript：let x: number = 1；Python 3.5+：def fn(x: int) -> str:；Go：var x int；Swift：let x: Int；JSON Schema：类型声明
- **相关**：=>、TypeScript、Type Hint（类型提示）

### Generic Parameter / 泛型参数
- **中文**：泛型参数
- **定义**：声明泛型类型参数的尖括号语法
- **说明**：TypeScript/Java/C#：function fn<T>(x: T): T {}；Rust：fn fn<T>(x: T) -> T {}；约束：<T extends Comparable<T>>；多参数：<K, V>
- **相关**：Generic（泛型）、Type Parameter（类型参数）、Type Constraint（类型约束）

### Non-null Assertion / 非空断言
- **中文**：非空断言
- **定义**：TypeScript 中告诉编译器值不为 null/undefined 的后缀运算符
- **说明**：const el = document.getElementById("id")!；忽略 null 检查；危险操作，应确保运行时确实不为空；与可选链 ?. 相对
- **相关**：?.、??、TypeScript、Null Safety（空安全）

### Optional / 可选标记
- **中文**：可选标记
- **定义**：表示参数、属性或类型可为空的问号后缀
- **说明**：TypeScript 可选参数：fn(x?: number)；可选属性：{ name: string; age?: number }；Nullable 类型：string | null；C#：可空值类型 int?
- **相关**：!、??、Optional（可选）、Nullable（可空）

### Decorator / 装饰器
- **中文**：装饰器
- **定义**：用于修改类、方法或属性的元编程语法
- **说明**：Python：@decorator；TypeScript/JavaScript：@Component、@Injectable；Java：@Override；面向切面编程（AOP）基础
- **相关**：Annotation（注解）、Metaprogramming（元编程）、AOP

### Shebang / Shebang
- **中文**：Shebang
- **定义**：脚本文件首行指定解释器路径的标记
- **说明**：#!/usr/bin/env python3；使脚本可直接执行：./script.py；常见：#!/bin/bash、#!/usr/bin/env node；必须位于文件第一行
- **相关**：Interpreter（解释器）、Script（脚本）、Executable（可执行文件）

### Private Field / 私有字段
- **中文**：私有字段
- **定义**：JavaScript/TypeScript 中定义类私有成员的前缀符号
- **说明**：class C { #field = 1; #method() {} }；真正私有（外部不可访问）；与 _convention 不同（_ 只是约定）；Chrome 74+、Node.js 12+ 支持
- **相关**：class、OOP、Encapsulation（封装）

### Template Interpolation / 模板插值
- **中文**：模板插值
- **定义**：模板字符串中嵌入表达式的美元大括号语法
- **说明**：JavaScript：\`Hello ${name}\`；支持任意表达式：\`Result: ${a + b}\`；Shell：${VAR} 变量扩展；与 f-string 的 {} 类似
- **相关**：``、Template Literal（模板字符串）、String Interpolation（字符串插值）

### Template String / 模板字符串
- **中文**：模板字符串
- **定义**：支持多行文本和嵌入表达式的反引号字符串
- **说明**：JavaScript：\`Hello ${name}\`；Python 无原生模板字符串（用 f-string）； tagged template：fn\`Hello ${name}\`；支持换行
- **相关**：''、""、$、Template Literal（模板字符串）

### Start Anchor / 起始锚点
- **中文**：起始锚点
- **定义**：正则表达式中匹配字符串或行起始位置的锚点
- **说明**：^hello 匹配以 hello 开头的字符串；多行模式下匹配行首；在字符类 [^abc] 中表示否定；与 $（结束锚点）相对
- **相关**：$、Regex（正则表达式）、Anchor（锚点）

### End Anchor / 结束锚点
- **中文**：结束锚点
- **定义**：正则表达式中匹配字符串或行结束位置的锚点
- **说明**：world$ 匹配以 world 结尾的字符串；多行模式下匹配行尾；与 ^ 相对；在替换字符串中表示捕获组：$1、$&
- **相关**：^、Regex（正则表达式）、Anchor（锚点）

### Escape / 转义符
- **中文**：转义符
- **定义**：改变后续字符含义的特殊字符
- **说明**：\n（换行）、\t（制表符）、\\（反斜杠）、\"（双引号）、\uXXXX（Unicode）；正则表达式：\. 匹配字面量点；字符串中必须成对出现
- **相关**：r、Raw String（原始字符串）、Escape Sequence（转义序列）

### Regex Alternation / 正则选择
- **中文**：正则选择
- **定义**：正则表达式中表示"或"关系的竖线符号
- **说明**：cat|dog 匹配 cat 或 dog；结合括号分组：(a|b)c 匹配 ac 或 bc；优先级最低；与字符类 [abc] 不同：| 是表达式级别，[] 是字符级别
- **相关**：[]、()、Regex（正则表达式）、Alternation（选择）

### Regex Wildcard / 正则通配
- **中文**：正则通配
- **定义**：正则表达式中匹配除换行符外任意单个字符的符号
- **说明**：a.c 匹配 abc、acc、a_c；不匹配换行符（除非 dotAll 标志 s）；与 * + ? 配合：.* 匹配任意长度；. 在字符类中匹配字面量点
- **相关**：*、+、?、Regex（正则表达式）

### Regex Star / 正则量词
- **中文**：正则量词
- **定义**：正则表达式中匹配前项零次或多次的符号
- **说明**：a* 匹配 "", "a", "aaa"；贪婪匹配（尽可能多）；懒惰匹配 *?（尽可能少）；与 +（一次或多次）、?（零次或一次）相对
- **相关**：+、?、{}、Regex（正则表达式）、Quantifier（量词）

### Regex Plus / 正则量词
- **中文**：正则量词
- **定义**：正则表达式中匹配前项一次或多次的符号
- **说明**：a+ 匹配 "a", "aaa"；不匹配空字符串；贪婪匹配；懒惰版本 +?；常用于匹配至少一个字符的场景
- **相关**：*、?、{}、Regex（正则表达式）、Quantifier（量词）

### Regex Question / 正则量词
- **中文**：正则量词
- **定义**：正则表达式中匹配前项零次或一次的符号
- **说明**：colou?r 匹配 color 或 colour；使前项可选；懒惰量词的修饰符：*?、+?、??；与 *（零次或多次）区别
- **相关**：*、+、Regex（正则表达式）、Quantifier（量词）

### Regex Range / 正则范围量词
- **中文**：正则范围量词
- **定义**：正则表达式中匹配前项 n 到 m 次的符号
- **说明**：a{3} 匹配 "aaa"；a{2,4} 匹配 "aa", "aaa", "aaaa"；a{2,} 匹配两次或以上；贪婪匹配；懒惰版本 {n,m}?
- **相关**：*、+、?、Regex（正则表达式）、Quantifier（量词）

### Positive Lookahead / 正向前瞻
- **中文**：正向前瞻
- **定义**：正则表达式中匹配后面跟随某模式但不消耗字符的断言
- **说明**：hello(?= world) 匹配 hello 且后面有 world；不捕获 world；用于条件匹配；与 (?! ) 负向前瞻相对
- **相关**：(?!)、Regex（正则表达式）、Lookahead（前瞻）

### Negative Lookahead / 负向前瞻
- **中文**：负向前瞻
- **定义**：正则表达式中匹配后面不跟随某模式且不消耗字符的断言
- **说明**：hello(?! world) 匹配 hello 且后面没有 world；不消耗字符；与 (?=) 正向前瞻相对；用于排除特定场景
- **相关**：(?=)、Regex（正则表达式）、Lookahead（前瞻）

### Positive Lookbehind / 正向后顾
- **中文**：正向后顾
- **定义**：正则表达式中匹配前面是某模式且不消耗字符的断言
- **说明**：(?<=\$)\d+ 匹配前面有 $ 的数字；JavaScript ES2018+ 支持；与 (?<! ) 负向后顾相对；长度必须固定
- **相关**：(?<!)、Regex（正则表达式）、Lookbehind（后顾）

### Negative Lookbehind / 负向后顾
- **中文**：负向后顾
- **定义**：正则表达式中匹配前面不是某模式且不消耗字符的断言
- **说明**：(?<!\$)\d+ 匹配前面没有 $ 的数字；ES2018+ 支持；长度必须固定；与 (?<=) 正向后顾相对
- **相关**：(?<=)、Regex（正则表达式）、Lookbehind（后顾）

### Non-capturing Group / 非捕获组
- **中文**：非捕获组
- **定义**：正则表达式中用于分组但不捕获匹配的括号
- **说明**：(?:abc)+ 匹配 abcabc 但不捕获；提高性能、减少内存；与捕获组 () 区别；在不需要反向引用时使用
- **相关**：()、Regex（正则表达式）、Capture Group（捕获组）

### Named Group / 命名捕获组
- **中文**：命名捕获组
- **定义**：正则表达式中带名称的捕获组
- **说明**：(?<year>\d{4})-(?<month>\d{2})；通过名称引用：match.groups.year；ES2018+、Python、.NET 支持；提高可读性
- **相关**：()、Regex（正则表达式）、Capture Group（捕获组）
