# 02. 软件设计 (Software Design)

## 设计原则

### Composition over Inheritance / 组合优于继承
- **中文**：组合优于继承
- **定义**：优先使用对象组合而非类继承来实现代码复用的设计原则
- **说明**：继承是白盒复用（暴露父类实现细节），组合是黑盒复用（只依赖接口）；组合更灵活，避免继承层次过深；是 GoF 设计原则之一
- **相关**：Inheritance（继承）、Design Pattern（设计模式）、OOP

### DRY (Don't Repeat Yourself) / 不要重复自己
- **中文**：不要重复自己
- **定义**：避免代码重复，将公共逻辑提取到单一位置的原则
- **说明**：重复导致维护困难（修改需改多处）；实现方式：函数、类、模块、框架；与单一职责原则配合
- **相关**：KISS、Refactoring（重构）、Code Reuse（代码复用）

### Inversion of Control (IoC) / 控制反转
- **中文**：控制反转
- **定义**：将程序控制权从应用代码转移给外部框架或容器的原则
- **说明**：传统编程：代码调用库；IoC：框架调用代码（好莱坞原则："不要给我们打电话，我们会打给你"）；实现：依赖注入、事件驱动、模板方法
- **相关**：Dependency Injection（依赖注入）、Framework（框架）、Design Pattern（设计模式）

### KISS (Keep It Simple, Stupid) / 保持简单
- **中文**：保持简单
- **定义**：设计应尽量简单，避免不必要的复杂性的原则
- **说明**：简单设计易于理解、测试和维护；奥卡姆剃刀原则：如无必要，勿增实体；简单是终极的复杂
- **相关**：DRY、YAGNI、Simple Design（简单设计）

### Law of Demeter / 迪米特法则
- **中文**：迪米特法则
- **定义**：对象只应与直接朋友通信，不与陌生人说话的设计原则
- **说明**：也称最少知识原则（Least Knowledge Principle）；避免长调用链（a.getB().getC().doSomething()）；降低耦合、提高封装
- **相关**：Coupling（耦合）、Encapsulation（封装）、Design Principle（设计原则）

### Liskov Substitution Principle (LSP) / 里氏替换原则
- **中文**：里氏替换原则
- **定义**：子类对象必须能够替换父类对象而不影响程序正确性的原则
- **说明**：SOLID 原则之一；违反例子：正方形继承长方形（改变宽同时改变高）；要求子类不强化前置条件、不弱化后置条件
- **相关**：SOLID、Inheritance（继承）、Polymorphism（多态）

### Open/Closed Principle (OCP) / 开闭原则
- **中文**：开闭原则
- **定义**：软件实体应对扩展开放、对修改关闭的原则
- **说明**：SOLID 原则之一；通过抽象和接口实现扩展；如新增功能通过添加新类而非修改现有代码；提高稳定性
- **相关**：SOLID、Abstraction（抽象）、Extension（扩展）

### Separation of Concerns (SoC) / 关注点分离
- **中文**：关注点分离
- **定义**：将系统分解为独立部分、每部分处理单独关注点的设计原则
- **说明**：不同关注点：业务逻辑、数据访问、UI、日志、安全；实现：分层架构、MVC、AOP；降低复杂度、提高可维护性
- **相关**：Modularity（模块化）、Layered Architecture（分层架构）、AOP

### Single Responsibility Principle (SRP) / 单一职责原则
- **中文**：单一职责原则
- **定义**：一个类或模块应只有一个引起变化的原因
- **说明**：SOLID 原则之一；职责过多导致耦合、难以维护；判断标准：类名是否能清晰描述其职责；如将数据访问逻辑从业务逻辑中分离
- **相关**：SOLID、Cohesion（内聚）、Modularity（模块化）

### SOLID / SOLID 原则
- **中文**：SOLID 原则
- **定义**：面向对象设计的五个基本原则的首字母缩写
- **说明**：S - 单一职责（SRP）；O - 开闭原则（OCP）；L - 里氏替换（LSP）；I - 接口隔离（ISP）；D - 依赖倒置（DIP）；由 Robert C. Martin 提出
- **相关**：Design Principle（设计原则）、OOP、Clean Code（整洁代码）

### YAGNI (You Aren't Gonna Need It) / 你不会需要它
- **中文**：你不会需要它
- **定义**：不要实现当前不需要的功能，避免过度设计的原则
- **说明**：敏捷开发核心理念；避免预测未来需求导致的浪费；需要时再通过重构添加；与 KISS 互补
- **相关**：KISS、Agile（敏捷）、Refactoring（重构）

## 架构模式

### Client-Server / 客户端-服务器
- **中文**：客户端-服务器
- **定义**：将系统分为请求服务的客户端和提供服务的服务器的分布式架构
- **说明**：经典架构；客户端：UI 和部分逻辑；服务器：数据存储和业务逻辑；变体：胖客户端、瘦客户端、三层架构
- **相关**：Distributed System（分布式系统）、Architecture Pattern（架构模式）、Peer-to-Peer（点对点）

### Event-Driven Architecture / 事件驱动架构
- **中文**：事件驱动架构
- **定义**：系统组件通过事件的产生、检测和消费进行通信的架构
- **说明**：组件松耦合；事件总线/消息队列协调通信；适合异步处理、实时系统、微服务；代表：Kafka、RabbitMQ、EventStore
- **相关**：Microservices（微服务）、Message Queue（消息队列）、Asynchronous（异步）

### Layered Architecture / 分层架构
- **中文**：分层架构
- **定义**：将系统按职责水平划分为多个层次、层间单向依赖的架构
- **说明**：经典分层：表示层 → 业务逻辑层 → 数据访问层 → 数据库层；优点：关注点分离、易于替换某层；层间通过接口通信
- **相关**：Separation of Concerns（关注点分离）、MVC、N-Tier Architecture（N 层架构）

### Microservices / 微服务
- **中文**：微服务
- **定义**：将应用拆分为小型、独立部署、围绕业务能力构建的服务的架构
- **说明**：特征：独立部署、去中心化治理、故障隔离、技术多样性；挑战：分布式复杂性、数据一致性、运维成本；与单体架构相对
- **相关**：Monolith（单体）、SOA、API Gateway（API 网关）

### Monolith / 单体架构
- **中文**：单体架构
- **定义**：所有功能模块集中在一个代码库和部署单元的架构
- **说明**：优点：开发简单、部署容易、性能高（无网络开销）；缺点：难以扩展、技术栈锁定、团队协调复杂；适合小型项目和初创公司
- **相关**：Microservices（微服务）、Modularity（模块化）、Architecture（架构）

### MVC (Model-View-Controller) / 模型-视图-控制器
- **中文**：模型-视图-控制器
- **定义**：将应用分为数据模型（Model）、用户界面（View）和控制逻辑（Controller）的架构模式
- **说明**：Model：数据和业务逻辑；View：UI 展示；Controller：接收输入、调用 Model、选择 View；变体：MVP、MVVM
- **相关**：Design Pattern（设计模式）、Layered Architecture（分层架构）、Separation of Concerns（关注点分离）

### MVVM (Model-View-ViewModel) / 模型-视图-视图模型
- **中文**：模型-视图-视图模型
- **定义**：MVC 的变体，引入 ViewModel 作为 View 和 Model 之间的抽象层
- **说明**：ViewModel：封装 View 的展示逻辑和数据；数据绑定（Data Binding）自动同步 View 和 ViewModel；广泛用于前端（Vue、Angular、WPF）
- **相关**：MVC、Data Binding（数据绑定）、Frontend（前端）

### N-Tier Architecture / N 层架构
- **中文**：N 层架构
- **定义**：将系统按职责分为 N 个物理或逻辑层次的架构
- **说明**：常见：三层架构（表示层、业务层、数据层）；层可部署在不同服务器；提高可扩展性和安全性；层间通信增加延迟
- **相关**：Layered Architecture（分层架构）、Distributed System（分布式系统）、Scalability（可扩展性）

### Peer-to-Peer (P2P) / 点对点
- **中文**：点对点
- **定义**：节点间直接通信、无中心服务器的分布式架构
- **说明**：每个节点既是客户端也是服务器；应用：BitTorrent、区块链、Skype；挑战：节点发现、数据一致性、安全性
- **相关**：Client-Server（客户端-服务器）、Distributed System（分布式系统）、Blockchain（区块链）

### Pipe and Filter / 管道和过滤器
- **中文**：管道和过滤器
- **定义**：将系统分解为一系列处理元素（过滤器），通过管道连接数据流的架构
- **说明**：过滤器独立、可复用；数据流单向流动；应用：UNIX Shell、编译器（词法分析→语法分析→语义分析）、ETL 工具
- **相关**：Architecture Pattern（架构模式）、Data Flow（数据流）、UNIX

### Publish-Subscribe / 发布-订阅
- **中文**：发布-订阅
- **定义**：消息发送者（发布者）不直接将消息发送给接收者（订阅者），而是通过消息代理转发的通信模式
- **说明**：发布者和订阅者解耦；订阅者按主题接收消息；代表：Kafka、RabbitMQ、Redis Pub/Sub；适合事件驱动架构
- **同义词**：Pub/Sub
- **相关**：Message Queue（消息队列）、Event-Driven（事件驱动）、Decoupling（解耦）

### Repository Pattern / 仓储模式
- **中文**：仓储模式
- **定义**：将数据访问逻辑封装在仓储对象中、为业务逻辑提供统一数据接口的模式
- **说明**：隔离业务逻辑和数据访问；便于切换数据源（如从 SQL 换到 NoSQL）；与 DAO 模式类似但更抽象
- **相关**：DAO、Data Access（数据访问）、Design Pattern（设计模式）

### SOA (Service-Oriented Architecture) / 面向服务的架构
- **中文**：面向服务的架构
- **定义**：将应用功能封装为可复用服务的架构风格
- **说明**：服务通过标准协议（SOAP、REST）通信；企业级集成方案；与微服务相比，SOA 服务粒度更大、强调企业级治理
- **相关**：Microservices（微服务）、ESB（企业服务总线）、Service（服务）

## 设计模式

### Abstract Factory / 抽象工厂
- **中文**：抽象工厂
- **定义**：创建相关对象族而不指定具体类的创建型模式
- **说明**：提供一个创建一系列相关或相互依赖对象的接口；如 UI 组件库（Windows 风格/Mac 风格）；符合开闭原则
- **相关**：Factory Pattern（工厂模式）、Builder Pattern（建造者模式）、Creational Pattern（创建型模式）

### Adapter / 适配器
- **中文**：适配器
- **定义**：将不兼容接口转换为兼容接口的结构型模式
- **说明**：使原本不能协同工作的类可以一起工作；如第三方库接口适配；实现：对象适配器（组合）、类适配器（继承）
- **相关**：Structural Pattern（结构型模式）、Facade（外观）、Wrapper（包装器）

### Bridge / 桥接
- **中文**：桥接
- **定义**：将抽象部分与实现部分分离、使它们可以独立变化的结构型模式
- **说明**：避免抽象和实现的静态绑定；如图形绘制系统（形状 vs 渲染 API）；与策略模式类似但关注层次结构
- **相关**：Structural Pattern（结构型模式）、Abstraction（抽象）、Implementation（实现）

### Builder / 建造者
- **中文**：建造者
- **定义**：分步骤构建复杂对象的创建型模式
- **说明**：将构造过程与表示分离；适合构造参数多的对象；如 StringBuilder、Lombok @Builder、OkHttp Request.Builder
- **相关**：Creational Pattern（创建型模式）、Factory Pattern（工厂模式）、Fluent Interface（流畅接口）

### Command / 命令
- **中文**：命令
- **定义**：将请求封装为对象、支持参数化和队列化的行为型模式
- **说明**：解耦调用者和执行者；支持撤销（Undo）、重做（Redo）、宏命令；应用：GUI 操作、事务系统、线程池
- **相关**：Behavioral Pattern（行为型模式）、Undo/Redo、Queue（队列）

### Decorator / 装饰器
- **中文**：装饰器
- **定义**：动态给对象添加额外职责的结构型模式
- **说明**：比继承更灵活；支持职责组合；应用：Java I/O 流、Python @decorator、中间件；符合开闭原则
- **相关**：Structural Pattern（结构型模式）、Wrapper（包装器）、Proxy（代理）

### Dependency Injection (DI) / 依赖注入
- **中文**：依赖注入
- **定义**：将依赖对象从外部传入而非在内部创建的设计模式/原则
- **说明**：IoC 的实现方式之一；注入方式：构造函数注入（推荐）、Setter 注入、接口注入；框架：Spring、Angular、Dagger
- **相关**：Inversion of Control（控制反转）、IoC Container（IoC 容器）、Decoupling（解耦）

### Design Pattern / 设计模式
- **中文**：设计模式
- **定义**：软件设计中常见问题的通用、可复用解决方案
- **说明**：GoF《设计模式》提出 23 种经典模式；分类：创建型（5）、结构型（7）、行为型（11）；不是代码，而是解决方案模板
- **相关**：GoF、Software Design（软件设计）、OOP

### Facade / 外观
- **中文**：外观
- **定义**：为复杂子系统提供统一简化接口的结构型模式
- **说明**：减少客户端与子系统的交互复杂度；不禁止直接访问子系统；如编译器接口（编译、链接一站式调用）
- **相关**：Structural Pattern（结构型模式）、API、Encapsulation（封装）

### Factory Pattern / 工厂模式
- **中文**：工厂模式
- **定义**：定义创建对象的接口、由子类决定实例化哪个类的创建型模式
- **说明**：分离对象创建和使用；简单工厂、工厂方法、抽象工厂；如 JDBC DriverManager.getConnection()；符合开闭原则
- **相关**：Abstract Factory（抽象工厂）、Creational Pattern（创建型模式）、Instantiation（实例化）

### GoF / GoF
- **中文**：四人组
- **全称**：Gang of Four
- **定义**：Erich Gamma、Richard Helm、Ralph Johnson、John Vlissides，经典《设计模式》作者
- **说明**：1994 年出版《Design Patterns: Elements of Reusable Object-Oriented Software》；提出 23 种设计模式；奠定面向对象设计模式基础
- **相关**：Design Pattern（设计模式）、OOP

### Observer / 观察者
- **中文**：观察者
- **定义**：定义对象间一对多依赖、当主题变化时自动通知所有观察者的行为型模式
- **说明**：松耦合；应用：事件监听、MVC（Model 通知 View）、消息系统；变体：发布-订阅（增加消息代理）
- **相关**：Behavioral Pattern（行为型模式）、Publish-Subscribe（发布-订阅）、Event-Driven（事件驱动）

### Proxy / 代理
- **中文**：代理
- **定义**：为其他对象提供代理以控制访问的结构型模式
- **说明**：类型：远程代理（访问远程对象）、虚拟代理（延迟加载）、保护代理（权限控制）、智能引用；应用：Spring AOP、Hibernate 懒加载
- **相关**：Structural Pattern（结构型模式）、Decorator（装饰器）、AOP

### Singleton / 单例
- **中文**：单例
- **定义**：确保类只有一个实例、并提供全局访问点的创建型模式
- **说明**：注意线程安全；实现方式：饿汉式、懒汉式（双重检查锁）、枚举（Java 推荐）；过度使用导致全局状态、难以测试
- **相关**：Creational Pattern（创建型模式）、Global State（全局状态）、Thread Safety（线程安全）

### Strategy / 策略
- **中文**：策略
- **定义**：定义算法族、分别封装、使它们可互换的行为型模式
- **说明**：将算法独立于使用它的客户端；应用：排序策略、支付策略、压缩算法选择；与状态模式相似但意图不同
- **相关**：Behavioral Pattern（行为型模式）、Algorithm（算法）、Polymorphism（多态）

## UML 与设计工具

### Aggregation / 聚合
- **中文**：聚合
- **定义**：表示整体与部分关系的弱关联，部分可独立存在
- **说明**：UML 空心菱形；如大学（整体）和教授（部分），教授可独立存在；与组合（Composition）相比关联更弱
- **相关**：Composition（组合）、Association（关联）、UML

### Association / 关联
- **中文**：关联
- **定义**：表示两个类之间有联系的 UML 关系
- **说明**：可以是双向或单向；可带多重性（1..*、0..1）；普通关联无整体-部分语义；与依赖相比关联更强
- **相关**：Dependency（依赖）、Aggregation（聚合）、UML

### Class Diagram / 类图
- **中文**：类图
- **定义**：展示系统中类、属性、方法及类间关系的静态结构图
- **说明**：UML 最常用的图；关系：继承（空心三角）、关联（直线）、聚合（空心菱形）、组合（实心菱形）、依赖（虚线箭头）
- **相关**：UML、Object-Oriented Design（面向对象设计）、Inheritance（继承）

### Composition / 组合
- **中文**：组合
- **定义**：表示整体与部分关系的强关联，部分不能独立存在
- **说明**：UML 实心菱形；如订单（整体）和订单项（部分），订单项随订单创建和销毁；生命周期相同
- **相关**：Aggregation（聚合）、Association（关联）、UML

### Dependency / 依赖
- **中文**：依赖
- **定义**：一个类的变化可能影响另一个类的 UML 关系
- **说明**：UML 虚线箭头；如 A 类使用 B 类作为方法参数；最弱的关系；应尽量减少依赖
- **相关**：Association（关联）、Coupling（耦合）、UML

### Sequence Diagram / 序列图
- **中文**：序列图
- **定义**：展示对象间消息交互时序的动态行为图
- **说明**：纵向：时间轴；横向：参与对象；箭头：消息调用；可表示同步/异步消息、条件分支、循环；适合分析交互流程
- **相关**：UML、Interaction Diagram（交互图）、Collaboration（协作）

### State Machine / 状态机
- **中文**：状态机
- **定义**：描述对象在不同状态间转移及触发条件的动态行为模型
- **说明**：要素：状态、事件、转移、动作；应用：订单状态、线程状态、UI 状态；UML 状态图可视化状态机
- **相关**：State Diagram（状态图）、UML、Event（事件）

### UML (Unified Modeling Language) / 统一建模语言
- **中文**：统一建模语言
- **定义**：标准化软件系统可视化建模的图形语言
- **说明**：分类：结构图（类图、组件图、部署图）和行为图（用例图、序列图、状态图）；工具：PlantUML、StarUML、Visio
- **相关**：Modeling（建模）、Software Design（软件设计）、Diagram（图）

### Use Case Diagram / 用例图
- **中文**：用例图
- **定义**：展示系统功能和外部参与者交互的 UML 行为图
- **说明**：元素：参与者（Actor，小人图标）、用例（椭圆）、系统边界（矩形）、关系（关联、包含、扩展、泛化）
- **相关**：UML、Requirement（需求）、Actor（参与者）
