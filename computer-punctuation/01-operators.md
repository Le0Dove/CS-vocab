# 01. 运算符 (Operators)

### Logical NOT / 逻辑非
- **中文**：逻辑非
- **定义**：对布尔值取反的一元运算符
- **说明**：!true = false；!false = true；在 C/C++/Java/JavaScript/Python 中使用；双重否定 !! 常用于强制转换为布尔值
- **相关**：Boolean（布尔）、Logical Operator（逻辑运算符）、NOT

### Not Equal / 不等于
- **中文**：不等于
- **定义**：比较两个值是否不相等的二元运算符
- **说明**：大多数语言中使用；与 == 相对；注意：JavaScript 中 != 会进行类型转换，!== 不进行类型转换
- **相关**：==、===、Comparison Operator（比较运算符）

### Strict Not Equal / 严格不等于
- **中文**：严格不等于
- **定义**：比较两个值是否不相等且不进行类型转换的运算符
- **说明**：JavaScript/TypeScript 特有；先比较类型，类型不同直接返回 true；值和类型都相同时返回 false
- **相关**：===、!=、Type Coercion（类型强制转换）

### Modulo / 取模/取余
- **中文**：取模/取余
- **定义**：计算除法余数的算术运算符
- **说明**：a % b = a - b * trunc(a/b)；用途：判断奇偶、循环数组、限制范围、哈希计算；注意负数行为的语言差异
- **相关**：/、Arithmetic Operator（算术运算符）、Modulo

### Logical AND / 逻辑与
- **中文**：逻辑与
- **定义**：当且仅当两个操作数都为真时结果为真的二元运算符
- **说明**：短路求值：左侧为假时不计算右侧；可用于条件判断和设置默认值（旧方式）；优先级高于 ||
- **相关**：||、!、Logical Operator（逻辑运算符）、Short-Circuit Evaluation（短路求值）

### Logical AND Assignment / 逻辑与赋值
- **中文**：逻辑与赋值
- **定义**：当左侧为真时，将左侧与右侧进行逻辑与运算并赋给左侧的复合赋值运算符
- **说明**：ES2021 引入；a &&= b 等价于 a = a && b；适用于条件更新；如果 a 为 falsy 则保持原值
- **相关**：||=、??=、Assignment Operator（赋值运算符）、Logical Operator（逻辑运算符）

### Bitwise AND / 按位与
- **中文**：按位与
- **定义**：对两个操作数的二进制位逐位进行与运算的运算符
- **说明**：两个位都为 1 时结果为 1；用途：位掩码（Masking）、权限检查、清零特定位；优先级低于 ==
- **相关**：|、^、~、Bitwise Operator（位运算符）、Mask（掩码）

### Exponentiation / 幂运算
- **中文**：幂运算
- **定义**：计算左侧操作数的右侧操作数次幂的运算符
- **说明**：Python、JavaScript、Ruby 支持；2 ** 3 = 8；替代 Math.pow()；右结合运算符
- **相关**：Math.pow()、Arithmetic Operator（算术运算符）、Exponentiation（求幂）

### Multiplication Assignment / 乘赋值
- **中文**：乘赋值
- **定义**：将左侧变量与右侧值相乘后赋回左侧的复合赋值运算符
- **说明**：a *= b 等价于 a = a * b；所有主流语言支持；可用于累乘计算
- **相关**：/=、+=、-=、Assignment Operator（赋值运算符）

### Addition / 加号
- **中文**：加号
- **定义**：用于算术加法或字符串连接的二元运算符，也可作为正号一元运算符
- **说明**：数值相加：1 + 2 = 3；字符串连接："a" + "b" = "ab"；JavaScript 中需注意隐式类型转换；一元 + 可将字符串转为数字
- **相关**：-、*、/、Arithmetic Operator（算术运算符）、Concatenation（连接）

### Increment / 自增
- **中文**：自增
- **定义**：将变量值加 1 的一元运算符
- **说明**：前置 ++a：先自增再使用值；后置 a++：先使用值再自增；C/C++/Java/JavaScript 使用；Python 不支持
- **相关**：--、Increment（自增）、Unary Operator（一元运算符）

### Addition Assignment / 加赋值
- **中文**：加赋值
- **定义**：将左侧变量与右侧值相加后赋回左侧的复合赋值运算符
- **说明**：a += b 等价于 a = a + b；可用于数值累加或字符串拼接；所有主流语言支持
- **相关**：-=、*=、/=、Assignment Operator（赋值运算符）

### Comma Operator / 逗号运算符
- **中文**：逗号运算符
- **定义**：按顺序执行多个表达式、返回最后一个表达式结果的运算符
- **说明**：C/C++/JavaScript 支持；for 循环中常用：for (i=0, j=0; i<n; i++, j++)；注意与函数参数分隔符的区分
- **相关**：;、Operator（运算符）、Expression（表达式）

### Subtraction / 减号
- **中文**：减号
- **定义**：用于算术减法或取负的二元/一元运算符
- **说明**：二元：a - b；一元：-a（取负）；数值运算；日期相减可得时间差；注意浮点数精度问题
- **相关**：+、*、/、Arithmetic Operator（算术运算符）

### Decrement / 自减
- **中文**：自减
- **定义**：将变量值减 1 的一元运算符
- **说明**：前置 --a：先自减再使用值；后置 a--：先使用值再自减；C/C++/Java/JavaScript 使用；Python 不支持
- **相关**：++、Decrement（自减）、Unary Operator（一元运算符）

### Subtraction Assignment / 减赋值
- **中文**：减赋值
- **定义**：将左侧变量减去右侧值后赋回左侧的复合赋值运算符
- **说明**：a -= b 等价于 a = a - b；用于递减计算；所有主流语言支持
- **相关**：+=、*=、/=、Assignment Operator（赋值运算符）

### Arrow / Member Access / 箭头/成员访问
- **中文**：箭头/成员访问
- **定义**：C/C++ 中通过指针访问结构体/对象成员的运算符
- **说明**：ptr->member 等价于 (*ptr).member；用于指针类型；Rust 中 -> 用于函数返回类型；某些语言中用于 lambda
- **相关**：.、*、Pointer（指针）、Member Access（成员访问）

### Dot / 点号
- **中文**：点号
- **定义**：访问对象属性或方法、或作为小数点的符号
- **说明**：成员访问：obj.property；小数点：3.14；包/模块路径：java.util.List；级联调用：obj.method1().method2()
- **相关**：->、Member Access（成员访问）、Decimal Point（小数点）

### Division / 除号
- **中文**：除号
- **定义**：计算两个数相除结果的算术运算符
- **说明**：整数除法会截断小数部分（C/Java）；浮点除法保留小数；除零会抛出异常或返回 Infinity；Python 3 中 / 是浮点除，// 是整除
- **相关**：//、*、+、Arithmetic Operator（算术运算符）

### Floor Division / 整除/地板除
- **中文**：整除/地板除
- **定义**：计算除法结果并向下取整的运算符
- **说明**：Python：7 // 3 = 2；JavaScript/TypeScript 不支持原生整除；C/C++/Java 中整数相除自动整除；SQL 中也有 // 注释
- **相关**：/、%、Floor Division（地板除）、Arithmetic Operator（算术运算符）

### Division Assignment / 除赋值
- **中文**：除赋值
- **定义**：将左侧变量除以右侧值后赋回左侧的复合赋值运算符
- **说明**：a /= b 等价于 a = a / b；注意除零错误；所有主流语言支持
- **相关**：*=、+=、-=、Assignment Operator（赋值运算符）

### Scope Resolution / 作用域解析
- **中文**：作用域解析
- **定义**：访问命名空间、类或模块中成员的双冒号运算符
- **说明**：C++：std::cout；PHP：ClassName::staticMethod；Ruby：Module::Class；Python 3.10+ 也引入 :: 用于类型别名
- **相关**：.、->、Namespace（命名空间）、Scope Resolution（作用域解析）

### Colon / 冒号
- **中文**：冒号
- **定义**：用于语句标签、键值对分隔、类型注解、条件表达式等的多功能符号
- **说明**：Python：if/else/for/while/def/class 语句结尾；JSON：键值对分隔；TypeScript：类型注解 let x: number；三元运算符 condition ? a : b
- **相关**：;、Key-Value Pair（键值对）、Type Annotation（类型注解）

### Less Than / 小于
- **中文**：小于
- **定义**：比较左侧值是否小于右侧值的比较运算符
- **说明**：返回布尔值；支持数值、字符串（字典序）、日期等类型；链式比较：a < b < c
- **相关**：>、<=、>=、Comparison Operator（比较运算符）

### Left Shift / 左移
- **中文**：左移
- **定义**：将操作数的二进制位向左移动指定位数的位运算符
- **说明**：a << b 等价于 a * 2^b；右侧补 0；用途：快速乘法、标志位操作；注意溢出
- **相关**：>>、>>>、Bitwise Operator（位运算符）

### Left Shift Assignment / 左移赋值
- **中文**：左移赋值
- **定义**：将左侧变量左移右侧位数后赋回的复合赋值运算符
- **说明**：a <<= b 等价于 a = a << b；C/C++/Java/JavaScript 支持
- **相关**：>>=、&=、Assignment Operator（赋值运算符）

### Less Than or Equal / 小于等于
- **中文**：小于等于
- **定义**：比较左侧值是否小于或等于右侧值的比较运算符
- **说明**：返回布尔值；数值比较、日期比较；注意浮点数精度问题
- **相关**：>=、<、>、Comparison Operator（比较运算符）

### Spaceship / 太空船运算符
- **中文**：太空船运算符
- **定义**：比较两个值、返回 -1/0/1 的三向比较运算符
- **说明**：PHP、Ruby、Perl、C++20 支持；a <=> b：a<b 返回 -1，a==b 返回 0，a>b 返回 1；用于排序比较
- **相关**：<、>、Comparison Operator（比较运算符）

### Assignment / 赋值
- **中文**：赋值
- **定义**：将右侧表达式的值赋给左侧变量的运算符
- **说明**：与 == 区分；支持连续赋值：a = b = c = 1；解构赋值： [a, b] = arr；Python 支持海象运算符 :=
- **相关**：==、:=、Assignment Operator（赋值运算符）

### Equal / 等于
- **中文**：等于
- **定义**：比较两个值是否相等的二元运算符
- **说明**：大多数语言中使用；注意：JavaScript 中 == 会进行类型转换（1 == "1" 为 true）；=== 不进行类型转换
- **相关**：!=、===、Comparison Operator（比较运算符）

### Strict Equal / 严格等于
- **中文**：严格等于
- **定义**：比较两个值是否相等且不进行类型转换的运算符
- **说明**：JavaScript/TypeScript 特有；值和类型都必须相同；推荐优先使用 === 避免隐式转换陷阱
- **相关**：==、!==、Type Coercion（类型强制转换）

### Fat Arrow / 胖箭头
- **中文**：胖箭头
- **定义**：定义箭头函数（lambda 表达式）或映射关系的运算符
- **说明**：JavaScript：const fn = (x) => x * 2；C#：LINQ 表达式；Python 中 => 用于匹配语句（3.10+）；与 -> 的区别
- **相关**：->、Arrow Function（箭头函数）、Lambda

### Greater Than / 大于
- **中文**：大于
- **定义**：比较左侧值是否大于右侧值的比较运算符
- **说明**：返回布尔值；支持数值、字符串（字典序）、日期；链式比较：a > b > c
- **相关**：<、>=、<=、Comparison Operator（比较运算符）

### Greater Than or Equal / 大于等于
- **中文**：大于等于
- **定义**：比较左侧值是否大于或等于右侧值的比较运算符
- **说明**：返回布尔值；与 <= 相对；数值、日期比较常用
- **相关**：<=、>、<、Comparison Operator（比较运算符）

### Right Shift / 右移
- **中文**：右移
- **定义**：将操作数的二进制位向右移动指定位数的位运算符
- **说明**：a >> b 等价于 floor(a / 2^b)；左侧补符号位（算术右移）；用途：快速除法、标志位操作
- **相关**：<<、>>>、Bitwise Operator（位运算符）

### Right Shift Assignment / 右移赋值
- **中文**：右移赋值
- **定义**：将左侧变量右移右侧位数后赋回的复合赋值运算符
- **说明**：a >>= b 等价于 a = a >> b；C/C++/Java/JavaScript 支持
- **相关**：<<=、&=、Assignment Operator（赋值运算符）

### Unsigned Right Shift / 无符号右移
- **中文**：无符号右移
- **定义**：将二进制位向右移动、左侧补 0 的位运算符
- **说明**：JavaScript 特有；与 >> 的区别：>> 补符号位，>>> 补 0；用于处理无符号整数
- **相关**：>>、<<、Bitwise Operator（位运算符）、Unsigned（无符号）

### Ternary / 三元运算符
- **中文**：三元运算符
- **定义**：根据条件选择两个表达式之一的条件运算符
- **说明**：格式：condition ? expr_if_true : expr_if_false；唯一的三元运算符；可嵌套但不宜过多层
- **相关**：if-else、Conditional Operator（条件运算符）、Expression（表达式）

### Nullish Coalescing / 空值合并
- **中文**：空值合并
- **定义**：当左侧为 null 或 undefined 时返回右侧值的逻辑运算符
- **说明**：ES2020 引入；与 || 的区别：|| 对 falsy 值（0, '', false）生效，?? 只对 null/undefined 生效；更安全的默认值设置
- **相关**：||、?.、Nullish Coalescing（空值合并）

### Nullish Coalescing Assignment / 空值合并赋值
- **中文**：空值合并赋值
- **定义**：当左侧为 null 或 undefined 时，将右侧值赋给左侧的复合赋值运算符
- **说明**：ES2021 引入；a ??= b 等价于 a = a ?? b；仅在需要时赋值；适用于设置默认值
- **相关**：||=、&&=、??、Assignment Operator（赋值运算符）

### Bitwise XOR Assignment / 按位异或赋值
- **中文**：按位异或赋值
- **定义**：将左侧变量与右侧值按位异或后赋回的复合赋值运算符
- **说明**：a ^= b 等价于 a = a ^ b；用途：切换标志位、简单加密
- **相关**：&=、|=、Assignment Operator（赋值运算符）

### Bitwise OR / 按位或
- **中文**：按位或
- **定义**：对两个操作数的二进制位逐位进行或运算的运算符
- **说明**：任一位为 1 则结果为 1；用途：设置标志位、合并权限、位掩码；注意与逻辑或 || 的区别
- **相关**：&、^、||、Bitwise Operator（位运算符）

### Bitwise OR Assignment / 按位或赋值
- **中文**：按位或赋值
- **定义**：将左侧变量与右侧值按位或后赋回的复合赋值运算符
- **说明**：a |= b 等价于 a = a | b；常用于设置标志位
- **相关**：&=、^=、Assignment Operator（赋值运算符）

### Logical OR / 逻辑或
- **中文**：逻辑或
- **定义**：当任一操作数为真时结果为真的二元运算符
- **说明**：短路求值：左侧为真时不计算右侧；常用于设置默认值：const val = input || default；注意 0 和 '' 被视为 falsy
- **相关**：&&、!、??、Logical Operator（逻辑运算符）

### Logical OR Assignment / 逻辑或赋值
- **中文**：逻辑或赋值
- **定义**：当左侧为假值时，将右侧值赋给左侧的复合赋值运算符
- **说明**：ES2021 引入；a ||= b 等价于 a = a || b；用于设置默认值（但 ??= 更安全）；如果 a 为 truthy 则保持原值
- **相关**：&&=、??=、Assignment Operator（赋值运算符）

### Bitwise NOT / 按位非
- **中文**：按位非
- **定义**：对操作数的二进制位逐位取反的一元运算符
- **说明**：~a = -(a+1)；用途：位掩码取反、flags = ~flags；注意：在 JavaScript 中 ~-1 = 0，常用于 indexOf 检查 (~arr.indexOf(x))
- **相关**：&、|、^、Bitwise Operator（位运算符）
