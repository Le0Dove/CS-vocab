# 02. 关系模型 (Relational Model)

### Attribute / 属性
- **中文**：属性
- **定义**：关系表中列的名称和类型，描述实体的特征
- **说明**：属性有数据类型（INT、VARCHAR 等）、域约束（取值范围）和默认值
- **同义词**：Column（列）、Field（字段）
- **相关**：Tuple（元组）、Relation（关系）、Domain（域）

### Candidate Key / 候选键
- **中文**：候选键
- **定义**：能唯一标识每条记录的最小属性集合
- **说明**：一个表可以有多个候选键，其中一个被选为主键（Primary Key）
- **相关**：Primary Key（主键）、Super Key（超键）、Foreign Key（外键）

### Cardinality / 基数
- **中文**：基数
- **定义**：关系中元组的数量，或索引中不同键值的数量
- **说明**：低基数（少量不同值，如性别男/女）；高基数（大量不同值，如身份证号）
- **相关**：Selectivity（选择性）、Index（索引）

### Cartesian Product / 笛卡尔积
- **中文**：笛卡尔积
- **定义**：两个关系之间所有可能的元组组合
- **说明**：笛卡尔积结果行数 = R 行数 × S 行数；通常在连接条件为空时产生
- **同义词**：Cross Join（交叉连接）
- **相关**：Join（连接）、Relation（关系）

### Composite Key / 复合键
- **中文**：复合键
- **定义**：由多个属性组成的主键或外键
- **说明**：用于单个属性无法唯一标识的场景（如订单明细中需要订单号+行号）
- **相关**：Primary Key（主键）、Candidate Key（候选键）

### Domain / 域
- **中文**：域
- **定义**：属性的允许取值范围
- **说明**：域约束限制数据的有效性
- **相关**：Attribute（属性）、Constraint（约束）

### Entity / 实体
- **中文**：实体
- **定义**：现实世界中可区分的独立对象，在数据库中对应表中的一条记录
- **说明**：实体有属性描述其特征；实体集是同类实体的集合（对应表）
- **同义词**：Entity
- **相关**：Attribute（属性）、Relationship（关系）

### ER Diagram (Entity-Relationship Diagram) / ER 图
- **中文**：实体-关系图
- **定义**：用图形表示实体、属性、关系的数据库设计工具
- **说明**：Chen 记法和 Crow's Foot 记法是两种常用画法
- **同义词**：ER Diagram、ERD
- **相关**：Entity（实体）、Relationship（关系）

### Foreign Key / 外键
- **中文**：外键
- **定义**：一个表中引用另一个表主键的属性，用于建立表间关系
- **说明**：外键维护引用完整性（Referential Integrity）；ON DELETE CASCADE/SET NULL 等选项定义级联行为
- **同义词**：FK
- **相关**：Primary Key（主键）、Referential Integrity（引用完整性）

### Functional Dependency / 函数依赖
- **中文**：函数依赖
- **定义**：属性 X 能唯一决定属性 Y 的约束关系（记为 X → Y）
- **说明**：函数依赖是规范化理论的基石；非主属性完全函数依赖于主键时满足 3NF
- **同义词**：FD
- **相关**：Normalization（规范化）、Closure（闭包）

### Index / 索引
- **中文**：索引
- **定义**：用于加速数据检索的附加数据结构，类似目录
- **说明**：索引建立在表的一个或多个列上；牺牲写入性能和存储空间换取查询速度
- **同义词**：Index
- **相关**：B+ Tree（B+ 树）、Hash Index（哈希索引）、Query Optimization（查询优化）

### Integrity / 完整性
- **中文**：完整性
- **定义**：数据库中数据的正确性、有效性、一致性
- **说明**：实体完整性（主键非空且唯一）、引用完整性（外键值必须引用存在的主键）、用户定义完整性（业务规则）
- **同义词**：Integrity
- **相关**：Constraint（约束）、ACID

### Join / 连接
- **中文**：连接
- **定义**：将两个或多个表中的行基于关联列组合起来的操作
- **说明**：INNER JOIN（只返回匹配行）、LEFT JOIN（保留左表所有行）、RIGHT JOIN、FULL OUTER JOIN；连接条件用 ON
- **相关**：Foreign Key（外键）、FROM

### Natural Join / 自然连接
- **中文**：自然连接
- **定义**：自动基于所有同名列进行等值连接，结果中同名去重
- **说明**：无需指定连接条件；如果同名列值不同，行不会出现在结果中
- **相关**：Equi-Join（等值连接）、Inner Join（内连接）

### Normal Form / 范式
- **中文**：范式
- **定义**：关系数据库设计中用于减少数据冗余的规范化规则层级
- **说明**：1NF: 属性不可再分 → 2NF: 消除部分依赖 → 3NF: 消除传递依赖 → BCNF: 所有决定因素都是候选键 → 4NF → 5NF；工程实践中通常做到 3NF/BCNF
- **同义词**：Normal Form (NF)
- **相关**：Normalization（规范化）、Functional Dependency（函数依赖）

### Normalization / 规范化
- **中文**：规范化
- **定义**：按范式规则将表逐步分解以消除数据冗余和异常的过程
- **说明**：规范化解决更新异常、插入异常、删除异常；过度规范化会导致大量 JOIN 降低性能；实际中需要反规范化折中
- **同义词**：Normalization
- **相关**：Denormalization（反规范化）、Normal Form（范式）

### Primary Key / 主键
- **中文**：主键
- **定义**：被选为记录唯一标识符的候选键
- **说明**：每个表只有一个主键；主键值必须非空且唯一
- **同义词**：PK
- **相关**：Candidate Key（候选键）、Foreign Key（外键）

### Query / 查询
- **中文**：查询
- **定义**：向数据库发送的数据检索或操作请求
- **说明**：查询语言（SQL）允许描述想要的数据而非如何获取（声明式）；查询优化器负责生成高效执行计划
- **同义词**：Query
- **相关**：SQL、SELECT、Query Optimizer（查询优化器）

### Referential Integrity / 引用完整性
- **中文**：引用完整性
- **定义**：外键值必须等于被引用表中某行主键值或为 NULL
- **说明**：DBMS 自动强制引用完整性；违反时拒绝操作或级联更新/删除
- **同义词**：Referential Integrity
- **相关**：Foreign Key（外键）、Constraint（约束）

### Relation / 关系
- **中文**：关系
- **定义**：关系模型中的二维表结构，由属性（列）和元组（行）组成
- **说明**：关系模式 R(A1, A2, ..., An) 表示关系名和属性列表
- **同义词**：Table（表）
- **相关**：Tuple（元组）、Attribute（属性）

### Relationship / 联系
- **中文**：联系
- **定义**：实体之间的关联方式
- **说明**：一对一（1:1）、一对多（1:N）、多对多（M:N）三种类型；多对多联系需要转换为中间表（关联实体）
- **同义词**：Relationship
- **相关**：Entity（实体）、Foreign Key（外键）

### Super Key / 超键
- **中文**：超键
- **定义**：能唯一标识表中每条记录的属性集合
- **说明**：候选键是最小的超键（无冗余属性）；所有候选键都是超键，超键不一定是候选键
- **相关**：Candidate Key（候选键）、Primary Key（主键）

### Surrogate Key / 代理键
- **中文**：代理键
- **定义**：无业务含义、由系统生成的自增 ID 作为主键
- **说明**：如自增整数（AUTO_INCREMENT）或 UUID；代理键稳定不变、无业务耦合；与 Natural Key（自然键，有实际含义）相对
- **同义词**：Surrogate Key
- **相关**：Primary Key（主键）、AUTO_INCREMENT

### Table / 表
- **中文**：表
- **定义**：关系模型中的基本数据存储单元，行代表记录，列代表字段
- **同义词**：Table
- **相关**：Relation（关系）、Schema（模式）

### Tuple / 元组
- **中文**：元组
- **定义**：关系中的一条记录
- **说明**：元组是属性的有序集合，每个属性的值不可再分
- **同义词**：Row（行）、Record（记录）
- **相关**：Attribute（属性）、Relation（关系）

### Union / 并
- **中文**：并
- **定义**：两个关系所有元组的集合操作（去除重复）
- **说明**：UNION 合并两个查询结果（要求列数和类型兼容）；UNION ALL 保留重复且效率更高
- **同义词**：UNION
- **相关**：Intersection（交）、Difference（差）、Set Operation（集合操作）
