# 06. 数据库设计 (Database Design)

## 设计方法

### Conceptual Design / 概念设计
- **中文**：概念设计
- **定义**：建立独立于具体 DBMS 的高层次数据模型的过程
- **说明**：使用 ER 模型描述实体、属性和关系；不关心具体实现细节；产出概念模式（ER 图）
- **相关**：ER Model（实体-关系模型）、Logical Design（逻辑设计）、Schema（模式）

### Data Modeling / 数据建模
- **中文**：数据建模
- **定义**：为业务需求定义数据结构及其关系的过程
- **说明**：三个阶段：概念建模（ER 图）→ 逻辑建模（关系模式）→ 物理建模（表、索引、分区）；是数据库设计的基础
- **相关**：ER Diagram（ER 图）、Normalization（规范化）、Schema Design（模式设计）

### Logical Design / 逻辑设计
- **定义**：将概念模型转换为特定数据模型（如关系模型）的过程
- **说明**：将 ER 图转换为关系模式（表、列、键）；确定主键、外键、约束；规范化到适当范式
- **相关**：Conceptual Design（概念设计）、Physical Design（物理设计）、Normalization（规范化）

### Physical Design / 物理设计
- **中文**：物理设计
- **定义**：根据逻辑模型确定数据库物理存储结构和访问方式
- **说明**：选择存储引擎、设计索引策略、确定分区方案、配置集群参数；目标：优化性能和存储效率
- **相关**：Index（索引）、Partitioning（分区）、Storage Engine（存储引擎）

---

## 规范化

### Anomaly / 异常
- **中文**：异常
- **定义**：由于数据冗余导致的数据操作问题
- **说明**：三种异常：插入异常（无法插入独立信息）、更新异常（修改需改多行）、删除异常（删除会丢失其他信息）；规范化消除异常
- **相关**：Normalization（规范化）、Redundancy（冗余）、Data Integrity（数据完整性）

### Boyce-Codd Normal Form (BCNF) / BCNF 范式
- **中文**：BCNF 范式
- **定义**：3NF 的加强版，要求每个非平凡函数依赖的决定因素都是候选键
- **说明**：比 3NF 更严格，可能存在无损分解但无法保持所有函数依赖；实际中常与 3NF 一同考虑
- **相关**：3NF、Functional Dependency（函数依赖）、Normalization（规范化）

### Denormalization / 反规范化
- **中文**：反规范化
- **定义**：有意引入数据冗余以优化查询性能的过程
- **说明**：在规范化基础上适当冗余减少 JOIN；适合读多写少场景；代价：增加存储、数据一致性维护复杂
- **相关**：Normalization（规范化）、Redundancy（冗余）、Read Performance（读性能）

### First Normal Form (1NF) / 第一范式
- **中文**：第一范式
- **定义**：关系中每个属性都是原子值（不可再分）
- **说明**：消除重复组和复合属性；每行每列交点只有一个值；是基础范式，所有关系都应满足
- **相关**：Normalization（规范化）、Atomicity（原子性）

### Functional Dependency / 函数依赖
- **中文**：函数依赖
- **定义**：属性集 X 的值唯一确定属性集 Y 的值的约束关系，记为 X → Y
- **说明**：是规范化理论的数学基础；候选键函数决定所有其他属性；通过 Armstrong 公理推导依赖集
- **相关**：Normalization（规范化）、Candidate Key（候选键）、Closure（闭包）

### Normalization / 规范化
- **中文**：规范化
- **定义**：通过分解关系模式消除数据冗余和异常的系统性方法
- **说明**：从 1NF → 2NF → 3NF → BCNF 逐步消除各种依赖异常；过度规范化会导致过多 JOIN；实际常折中到 3NF/BCNF
- **相关**：Denormalization（反规范化）、Normal Form（范式）、Functional Dependency（函数依赖）

### Partial Dependency / 部分依赖
- **中文**：部分依赖
- **定义**：非主属性依赖于候选键的一部分（而非整个候选键）
- **说明**：部分依赖违反 2NF；通过将依赖部分和主属性拆分到新表消除
- **相关**：2NF、Functional Dependency（函数依赖）、Composite Key（复合键）

### Second Normal Form (2NF) / 第二范式
- **中文**：第二范式
- **定义**：满足 1NF 且不存在非主属性对候选键的部分依赖
- **说明**：仅对复合候选键有意义（单属性主键自动满足 2NF）；消除部分依赖以减少冗余
- **相关**：1NF、3NF、Partial Dependency（部分依赖）

### Third Normal Form (3NF) / 第三范式
- **中文**：第三范式
- **定义**：满足 2NF 且不存在非主属性对候选键的传递依赖
- **说明**：传递依赖：A → B → C，则 A → C 为传递依赖；3NF 消除传递依赖；工程实践中最常用的目标范式
- **相关**：2NF、BCNF、Transitive Dependency（传递依赖）

### Transitive Dependency / 传递依赖
- **中文**：传递依赖
- **定义**：非主属性通过另一个非主属性间接依赖于候选键
- **说明**：如 学生 → 班级 → 班主任，则学生 → 班主任 为传递依赖；违反 3NF；通过拆分表消除
- **相关**：3NF、Functional Dependency（函数依赖）

---

## 设计模式

### Bridge Table / 桥接表
- **中文**：桥接表
- **定义**：用于实现多对多关系的中间关联表
- **说明**：包含两个外键分别引用关联的表；可额外存储关系属性（如关联时间、权重）；也叫 Junction Table、Associative Entity
- **同义词**：Junction Table、Associative Table、Link Table
- **相关**：Many-to-Many（多对多）、Foreign Key（外键）

### Entity / 实体
- **中文**：实体
- **定义**：现实世界中可区分的对象，在数据库中对应表
- **说明**：实体有属性（列）和标识符（主键）；实体间通过关系（Relationship）关联；强实体不依赖其他实体存在
- **相关**：Attribute（属性）、Relationship（关系）、ER Model（实体-关系模型）

### Entity-Relationship Model (ER Model) / 实体-关系模型
- **中文**：实体-关系模型
- **定义**：用实体、属性和关系描述现实世界的概念数据模型
- **说明**：Chen 记法：矩形（实体）、椭圆（属性）、菱形（关系）；Crow's Foot 记法更常用；是数据库概念设计的基础工具
- **相关**：ER Diagram（ER 图）、Entity（实体）、Relationship（关系）

### Many-to-Many Relationship / 多对多关系
- **中文**：多对多关系
- **定义**：两个实体集中，一个实体的实例可关联另一个实体集中的多个实例，反之亦然
- **说明**：关系数据库中需引入桥接表（关联实体）实现；如学生与课程的关系
- **相关**：Bridge Table（桥接表）、One-to-Many（一对多）、Relationship（关系）

### One-to-Many Relationship / 一对多关系
- **中文**：一对多关系
- **定义**：实体 A 的一个实例对应实体 B 的多个实例，但 B 的一个实例只对应 A 的一个实例
- **说明**：通过在"多"方添加外键实现；最常见的关联类型；如部门与员工
- **相关**：Foreign Key（外键）、One-to-One（一对一）、Relationship（关系）

### One-to-One Relationship / 一对一关系
- **中文**：一对一关系
- **定义**：两个实体集中，一个实体的实例最多关联另一个实体集中的一个实例
- **说明**：实现方式：共享主键或外键加唯一约束；常用于垂直拆分（将宽表拆分为两个关联表）
- **相关**：Primary Key（主键）、UNIQUE Constraint（唯一约束）

### Star Schema / 星型模式
- **中文**：星型模式
- **定义**：数据仓库中事实表周围环绕多个维度表的设计模式
- **说明**：事实表存储度量（销售额、数量），维度表存储描述信息（时间、产品、地区）；查询简单高效；是数据仓库最常用模式
- **相关**：Snowflake Schema（雪花模式）、Fact Table（事实表）、Dimension Table（维度表）

### Snowflake Schema / 雪花模式
- **中文**：雪花模式
- **定义**：星型模式的规范化变体，维度表进一步规范化
- **说明**：减少维度表冗余，节省存储；但查询需要更多 JOIN，性能略低于星型模式；适合维度属性多且复杂的场景
- **相关**：Star Schema（星型模式）、Normalization（规范化）

---

## 物理设计

### Partitioning / 分区
- **中文**：分区
- **定义**：将大表物理拆分为更小、更易管理的片段（分区）
- **说明**：分区方式：Range（范围）、List（列表）、Hash（哈希）、Composite（复合）；提升查询性能（分区裁剪）和维护效率；对应用透明
- **相关**：Sharding（分片）、Partition Pruning（分区裁剪）、Table（表）

### Replication / 复制
- **中文**：复制
- **定义**：将数据从一个数据库服务器（主节点）复制到其他服务器（从节点）的技术
- **说明**：用途：读写分离（主写从读）、高可用（故障切换）、数据备份；方式：异步复制、半同步复制、同步复制
- **相关**：Master-Slave（主从）、Failover（故障转移）、High Availability（高可用）

### Sharding / 分片
- **中文**：分片
- **定义**：将数据水平拆分到多个独立数据库实例（分片）的技术
- **说明**：每个分片存储部分数据；分片键决定数据分布；解决单节点容量和性能瓶颈；跨分片查询复杂
- **同义词**：Horizontal Partitioning（水平分区）
- **相关**：Partitioning（分区）、Distributed Database（分布式数据库）、Shard Key（分片键）

### Storage Engine / 存储引擎
- **中文**：存储引擎
- **定义**：数据库中负责数据存储和提取的底层软件模块
- **说明**：不同引擎特性不同：InnoDB（事务、行锁、MVCC）、MyISAM（表锁、全文索引）、Memory（内存存储）；MySQL 支持多引擎
- **相关**：InnoDB、MyISAM、Table（表）

---

## 数据完整性

### Data Integrity / 数据完整性
- **中文**：数据完整性
- **定义**：数据库中数据的准确性、一致性和有效性的统称
- **说明**：类型：实体完整性（主键约束）、引用完整性（外键约束）、域完整性（数据类型/范围/格式）、用户定义完整性（业务规则）
- **相关**：Constraint（约束）、ACID、Validation（验证）

### Referential Integrity / 引用完整性
- **中文**：引用完整性
- **定义**：外键值必须等于被引用表主键值或为 NULL 的约束规则
- **说明**：DBMS 自动强制；违反时拒绝操作或级联处理（CASCADE/SET NULL）；保证表间关系一致性
- **相关**：Foreign Key（外键）、Primary Key（主键）、Constraint（约束）

### Surrogate Key / 代理键
- **中文**：代理键
- **定义**：无业务含义、由系统自动生成的唯一标识符
- **说明**：如自增 ID、UUID；稳定性高，不随业务变化；与自然键（Natural Key，有业务含义）相对；推荐作为主键
- **相关**：Primary Key（主键）、Natural Key（自然键）、UUID

---

## 文档与工具

### Data Dictionary / 数据字典
- **中文**：数据字典
- **定义**：描述数据库中所有对象（表、列、约束、索引）的元数据集合
- **说明**：包括对象名称、数据类型、长度、约束、所有者、创建时间等；用户可查询（如 information_schema）；是数据库文档的核心
- **同义词**：System Catalog（系统目录）、Metadata Repository（元数据仓库）
- **相关**：Catalog（目录）、Schema（模式）、Metadata（元数据）

### Schema / 模式
- **中文**：模式
- **定义**：数据库的逻辑结构描述，包括表、视图、索引、约束等对象的定义
- **说明**：三层模式：外模式（用户视图）、概念模式（全局逻辑结构）、内模式（物理存储）；Schema 是数据库设计的蓝图
- **相关**：Database Design（数据库设计）、Table（表）、DDL（数据定义语言）
