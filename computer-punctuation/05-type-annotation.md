# 05. 类型与注解 (Types & Annotations)

### Non-null Assertion / 非空断言
- **中文**：非空断言
- **定义**：TypeScript 中断言语法值不为 null 或 undefined 的后缀运算符
- **说明**：const el = document.getElementById("id")!；编译器跳过 null 检查；运行时若实际为 null 则报错；应谨慎使用
- **相关**：?.、??、TypeScript、Null Safety（空安全）

### Nullable / 可空标记
- **中文**：可空标记
- **定义**：表示值可能为 null 或 undefined 的问号后缀
- **说明**：TypeScript 可选参数：fn(x?: number)；可空类型：string | null；C#：int?；Kotlin：String?；与 !（非空断言）相对
- **相关**：!、??、Nullable（可空）、Optional（可选）

### Type Annotation / 类型注解
- **中文**：类型注解
- **定义**：在声明中指定变量、参数或返回值类型的冒号语法
- **说明**：TypeScript：let x: number = 1；Python：def fn(x: int) -> str:；Go：var x int；Swift：let x: Int；JSON Schema：类型声明；结构清晰
- **相关**：=>、TypeScript、Type Hint（类型提示）

### Generic / 泛型参数
- **中文**：泛型参数
- **定义**：声明类型参数的尖括号语法，使代码可适用于多种类型
- **说明**：function identity<T>(arg: T): T { return arg; }；约束：<T extends Comparable<T>>；多参数：<K, V>；Rust：<T: Display>；C++：template<typename T>
- **相关**：Generic（泛型）、Type Parameter（类型参数）、Type Constraint（类型约束）

### Type Assertion / 类型断言
- **中文**：类型断言
- **定义**：告诉编译器将值视为特定类型的关键字
- **说明**：TypeScript：value as Type；Python：无（用 typing.cast）；Kotlin：value as Type；Swift：value as! Type（强制）、value as? Type（可选）；与类型转换不同：不断行转换
- **相关**：is、instanceof、Type Casting（类型转换）

### Extends / 继承/约束
- **中文**：继承/约束
- **定义**：用于类继承或泛型约束的关键字
- **说明**：TypeScript/Java：class Child extends Parent {}；泛型约束：<T extends Base>；接口扩展：interface A extends B {}；表示"是...的子类型"
- **相关**：implements、inheritance、Generic Constraint（泛型约束）

### Implements / 实现
- **中文**：实现
- **定义**：类实现接口所定义契约的关键字
- **说明**：TypeScript/Java：class MyClass implements Interface {}；必须实现接口所有成员；一个类可实现多个接口；与 extends（继承）不同
- **相关**：extends、interface、OOP、Contract（契约）

### Infer / 推断
- **中文**：推断
- **定义**：TypeScript 条件类型中推断类型变量的关键字
- **说明**：type ReturnType<T> = T extends (...args: any[]) => infer R ? R : never；从类型表达式中抽取类型；高级类型编程核心
- **相关**：Conditional Type（条件类型）、TypeScript、Type Inference（类型推断）

### Interface / 接口
- **中文**：接口
- **定义**：定义对象形状和契约的代码结构
- **说明**：TypeScript/Java：interface Point { x: number; y: number }；无实现，纯类型；可扩展、可合并；与 type 别名不同：接口可声明合并
- **相关**：type、implements、class、OOP、Contract（契约）

### Keyof / 键类型
- **中文**：键类型
- **定义**：TypeScript 中获取对象所有键的联合类型的运算符
- **说明**：type PointKeys = keyof Point；// "x" | "y"；与映射类型配合：{ [K in keyof T]: T[K] }；类型编程中常用
- **相关**：typeof、Mapped Type（映射类型）、TypeScript、Union Type（联合类型）

### Type Query / 类型查询
- **中文**：类型查询
- **定义**：获取变量或表达式的类型的运算符
- **说明**：TypeScript：let s = "hello"; type T = typeof s; // string；与 JS 运行时 typeof 不同；用于从值推导类型
- **相关**：keyof、Type Inference（类型推断）、TypeScript

### Type Alias / 类型别名
- **中文**：类型别名
- **定义**：为类型创建新名称的关键字
- **说明**：TypeScript：type Point = { x: number; y: number }；与 interface 不同：type 可表示联合、交叉、元组；不可声明合并；Rust：type 用于类型别名
- **相关**：interface、alias、TypeScript、Union Type（联合类型）

### Unknown / 未知类型
- **中文**：未知类型
- **定义**：TypeScript 中表示未知类型的安全顶层类型
- **说明**：比 any 更安全；不可直接赋值给其他类型（除 any 和 unknown）；使用前必须类型收窄（typeof、instanceof、as）；TypeScript 3.0 引入
- **相关**：any、never、TypeScript、Type Safety（类型安全）

### Any / 任意类型
- **中文**：任意类型
- **定义**：TypeScript 中关闭类型检查的特殊类型
- **说明**：可赋值给任何类型、任何类型可赋值给它；绕过编译器检查；应尽量避免使用；与 unknown 不同：any 可任意操作
- **相关**：unknown、never、TypeScript、Type Safety（类型安全）

### Never / 永不类型
- **中文**：永不类型
- **定义**：表示永远不会发生的值的类型
- **说明**：无值可赋值给 never；never 可赋值给任何类型；用途：抛出异常的函数返回类型、 exhaustive check（穷尽检查）；TypeScript 最底层类型
- **相关**：any、unknown、void、TypeScript

### Void / 空类型
- **中文**：空类型
- **定义**：表示函数无返回值的类型
- **说明**：TypeScript/C/Java：function fn(): void {}；只能赋值为 undefined 或 null（strictNullChecks 关闭时）；与 undefined 不同：undefined 是值，void 是类型
- **相关**：undefined、null、never、Function Return Type（函数返回类型）

### Union / 联合类型
- **中文**：联合类型
- **定义**：TypeScript 中表示值可为多种类型之一的符号
- **说明**：type Status = "active" | "inactive" | "pending"；可配合类型守卫收窄；联合类型的交集操作是 &（交叉类型）
- **相关**：&、TypeScript、Union Type（联合类型）

### Intersection / 交叉类型
- **中文**：交叉类型
- **定义**：TypeScript 中表示值需满足多种类型的符号
- **说明**：type A = { a: number }; type B = { b: string }; type C = A & B; // { a: number; b: string }；合并对象形状；与 |（联合类型）相对
- **相关**：|、TypeScript、Intersection Type（交叉类型）

### Readonly / 只读修饰符
- **中文**：只读修饰符
- **定义**：标记属性或数组不可重新赋值的修饰符
- **说明**：TypeScript：readonly name: string；readonly arr: number[]；编译时检查，运行时不影响；与 const 不同：const 是变量，readonly 是属性
- **相关**：const、immutable、TypeScript

### Const / 常量声明
- **中文**：常量声明
- **定义**：声明不可重新绑定的变量的关键字
- **说明**：const x = 1；不可重新赋值（但对象内容可变）；块级作用域；ES6 引入；与 let（可变）和 var（函数作用域）区别；C/C++ 中也有
- **相关**：let、var、readonly、immutable

### Enum / 枚举
- **中文**：枚举
- **定义**：定义具名常量集合的关键字
- **说明**：TypeScript：enum Color { Red, Green, Blue }；默认数字枚举从 0 开始；可自定义值：enum Status { OK = 200 }；编译为对象
- **相关**：const、Literal Type（字面量类型）、TypeScript

### Abstract / 抽象
- **中文**：抽象
- **定义**：标记类或方法为抽象、不可实例化的关键字
- **说明**：abstract class Animal { abstract makeSound(): void }；子类必须实现抽象方法；不能直接 new 抽象类；与 interface 不同：抽象类可有实现
- **相关**：interface、class、OOP、Inheritance（继承）

### Override / 重写标记
- **中文**：重写标记
- **定义**：显式标记方法重写父类方法的关键字
- **说明**：TypeScript 4.3+：override method() {}；若父类无此方法则报错；防止拼写错误；Java 的 @Override 注解类似
- **相关**：extends、class、OOP、Polymorphism（多态）

### Private / 私有修饰符
- **中文**：私有修饰符
- **定义**：限制成员只能在类内部访问的访问修饰符
- **说明**：TypeScript：private name: string；传统实现是编译时检查；ES2022 #field 是真正的运行时私有；与 protected、public 相对
- **相关**：protected、public、#、Encapsulation（封装）

### Protected / 受保护修饰符
- **中文**：受保护修饰符
- **定义**：限制成员只能在类及其子类中访问的访问修饰符
- **说明**：TypeScript/Java/C#：protected name: string；子类可访问；外部实例不可访问；介于 private 和 public 之间
- **相关**：private、public、OOP、Inheritance（继承）

### Public / 公共修饰符
- **中文**：公共修饰符
- **定义**：允许在任何地方访问成员的访问修饰符
- **说明**：TypeScript 默认值（可省略）；Java/C# 需显式声明；接口成员默认 public；与 private、protected 相对
- **相关**：private、protected、OOP、Encapsulation（封装）

### Static / 静态修饰符
- **中文**：静态修饰符
- **定义**：标记成员属于类而非实例的关键字
- **说明**：TypeScript/Java/C#：static count = 0；通过类名访问：ClassName.count；所有实例共享；可用于工具方法、计数器、单例模式
- **相关**：class、OOP、Singleton（单例模式）

### This / 当前实例
- **中文**：当前实例
- **定义**：引用当前对象实例的关键字
- **说明**：方法中访问自身属性和方法：this.name；构造函数中调用其他构造函数：this()；JavaScript 中 this 指向依赖调用方式；箭头函数无自己的 this
- **相关**：self、class、OOP、Context（上下文）

### Super / 父类引用
- **中文**：父类引用
- **定义**：引用父类（超类）的关键字
- **说明**：调用父类构造函数：super()；调用父类方法：super.method()；子类构造函数中必须在使用 this 前调用 super()；OOP 继承机制核心
- **相关**：extends、this、class、OOP、Inheritance（继承）

### Instanceof / 实例检查
- **中文**：实例检查
- **定义**：检查对象是否为某类实例的运算符
- **说明**：obj instanceof Class；JavaScript/Java 使用；运行时检查原型链；与 typeof（检查原始类型）互补；类型守卫可与 if 配合
- **相关**：typeof、is、class、OOP、Type Guard（类型守卫）

### Is / 类型守卫
- **中文**：类型守卫
- **定义**：TypeScript 中自定义类型谓词的关键字
- **说明**：function isString(x: unknown): x is string { return typeof x === "string" }；配合 if 使用可收窄类型；自定义类型检查函数
- **相关**：instanceof、typeof、TypeScript、Type Guard（类型守卫）

### Satisfies / 满足运算符
- **中文**：满足运算符
- **定义**：TypeScript 4.9+ 中验证表达式满足某类型但不改变推断类型的运算符
- **说明**：const config = { host: "localhost" } satisfies Config；推断最具体类型同时检查约束；比 as 更安全；解决类型推断过宽问题
- **相关**：as、type、TypeScript、Type Inference（类型推断）

### In / 属性检查
- **中文**：属性检查
- **定义**：检查对象是否包含某属性的运算符
- **说明**：JavaScript："key" in obj；TypeScript 类型守卫：if ("name" in obj) { ... }；for...in 遍历对象键；与 hasOwnProperty 不同：in 检查原型链
- **相关**：hasOwnProperty、keyof、Type Guard（类型守卫）
