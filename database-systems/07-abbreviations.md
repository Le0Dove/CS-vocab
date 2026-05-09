# 07. 缩写汇总 (Abbreviations)

### ACID
- **中文**：ACID 特性
- **全称**：Atomicity, Consistency, Isolation, Durability
- **说明**：数据库事务的四个基本属性
- **相关**：Transaction（事务）、BASE、CAP Theorem

### ARIES
- **中文**：ARIES 恢复算法
- **全称**：Algorithm for Recovery and Isolation Exploiting Semantics
- **说明**：IBM 开发的基于日志的数据库恢复算法，使用 Write-Ahead Logging、Redo 和 Undo
- **相关**：Crash Recovery（崩溃恢复）、WAL、REDO/UNDO Log

### BCNF
- **中文**：BCNF 范式
- **全称**：Boyce-Codd Normal Form
- **说明**：第三范式的加强版，要求所有函数依赖的决定因素都是候选键
- **相关**：3NF、Normalization（规范化）

### CAP
- **中文**：CAP 定理
- **全称**：Consistency, Availability, Partition Tolerance
- **说明**：分布式系统最多同时满足一致性、可用性、分区容错性中的两个
- **相关**：Distributed Database（分布式数据库）、BASE

### CTE
- **中文**：公用表表达式
- **全称**：Common Table Expression
- **说明**：使用 WITH 关键字定义的临时命名结果集
- **相关**：SQL、Recursive Query（递归查询）

### DBA
- **中文**：数据库管理员
- **全称**：Database Administrator
- **说明**：负责数据库安装、配置、监控、备份、优化和安全的专业人员
- **相关**：DBMS、Database（数据库）

### DBMS
- **中文**：数据库管理系统
- **全称**：Database Management System
- **说明**：管理数据库的软件系统，如 MySQL、PostgreSQL、Oracle
- **相关**：RDBMS、SQL、Database（数据库）

### DDL
- **中文**：数据定义语言
- **全称**：Data Definition Language
- **说明**：定义数据库对象的 SQL 语句（CREATE、ALTER、DROP）
- **相关**：DML、DCL、SQL

### DCL
- **中文**：数据控制语言
- **全称**：Data Control Language
- **说明**：控制数据库访问权限的 SQL 语句（GRANT、REVOKE）
- **相关**：DDL、DML、SQL

### DML
- **中文**：数据操作语言
- **全称**：Data Manipulation Language
- **说明**：查询和修改数据的 SQL 语句（SELECT、INSERT、UPDATE、DELETE）
- **相关**：DDL、DCL、SQL

### DW / DWH
- **中文**：数据仓库
- **全称**：Data Warehouse
- **说明**：面向分析的集成数据存储，用于决策支持
- **相关**：OLAP、ETL、Data Mining

### ERD
- **中文**：实体-关系图
- **全称**：Entity-Relationship Diagram
- **说明**：表示实体、属性和关系的数据库设计图
- **相关**：ER Model、Database Design

### ETL
- **中文**：抽取-转换-加载
- **全称**：Extract, Transform, Load
- **说明**：从多数据源提取、清洗转换后载入数据仓库的流程
- **相关**：Data Warehouse、Data Pipeline

### FK
- **中文**：外键
- **全称**：Foreign Key
- **说明**：引用另一表主键的约束，建立表间关系
- **相关**：PK、Referential Integrity

### HOLAP
- **中文**：混合联机分析处理
- **全称**：Hybrid Online Analytical Processing
- **说明**：结合 MOLAP 和 ROLAP 的 OLAP 实现方式
- **相关**：OLAP、MOLAP、ROLAP

### IAM
- **中文**：身份与访问管理
- **全称**：Identity and Access Management
- **说明**：数据库安全中管理用户身份和权限的机制
- **相关**：Authorization（授权）、Authentication（认证）

### MOLAP
- **中文**：多维联机分析处理
- **全称**：Multidimensional Online Analytical Processing
- **说明**：将数据存储在多维数组中的 OLAP 方式，查询速度快
- **相关**：OLAP、ROLAP、HOLAP

### MVCC
- **中文**：多版本并发控制
- **全称**：Multi-Version Concurrency Control
- **说明**：通过维护数据多个版本实现读写不阻塞的并发控制
- **相关**：Snapshot Isolation、Transaction

### NoSQL
- **中文**：非关系型数据库
- **全称**：Not Only SQL
- **说明**：非关系型数据库统称，包括键值、文档、列族、图数据库等
- **相关**：SQL、MongoDB、Cassandra

### OLAP
- **中文**：联机分析处理
- **全称**：Online Analytical Processing
- **说明**：面向数据分析的查询密集型处理模式
- **相关**：OLTP、Data Warehouse、BI

### OLTP
- **中文**：联机事务处理
- **全称**：Online Transaction Processing
- **说明**：面向日常事务操作的短查询频繁处理模式
- **相关**：OLAP、Transaction

### ORM
- **中文**：对象关系映射
- **全称**：Object-Relational Mapping
- **说明**：将面向对象编程中的对象映射到数据库表的编程技术
- **相关**：Hibernate、Entity Framework、SQL

### PK
- **中文**：主键
- **全称**：Primary Key
- **说明**：唯一标识表中每行的列或列组合
- **相关**：FK、UNIQUE、Clustered Index

### RDBMS
- **中文**：关系数据库管理系统
- **全称**：Relational Database Management System
- **说明**：基于关系模型的数据库系统，如 MySQL、PostgreSQL、Oracle
- **相关**：DBMS、SQL、Relational Model

### ROLAP
- **中文**：关系联机分析处理
- **全称**：Relational Online Analytical Processing
- **说明**：基于关系数据库存储的 OLAP 方式，可扩展性好
- **相关**：OLAP、MOLAP、HOLAP

### SLA
- **中文**：服务等级协议
- **全称**：Service Level Agreement
- **说明**：数据库服务可用性、性能、恢复时间等指标的承诺
- **相关**：High Availability、Disaster Recovery

### SQL
- **中文**：结构化查询语言
- **全称**：Structured Query Language
- **说明**：关系数据库的标准查询和操作语言
- **相关**：RDBMS、DML、DDL

### TPC
- **中文**：事务处理性能委员会
- **全称**：Transaction Processing Performance Council
- **说明**：制定数据库性能基准测试标准的组织（如 TPC-C、TPC-H）
- **相关**：Benchmark（基准测试）

### T-SQL
- **中文**：Transact-SQL
- **全称**：Transact-SQL
- **说明**：Microsoft SQL Server 和 Sybase 的 SQL 扩展，含过程化编程
- **相关**：SQL、SQL Server、PL/SQL

### WAL
- **中文**：预写日志
- **全称**：Write-Ahead Logging
- **说明**：数据修改前先写日志的原则，保证持久性和恢复
- **相关**：REDO Log、Durability、Crash Recovery

### 2NF
- **中文**：第二范式
- **全称**：Second Normal Form
- **说明**：满足 1NF 且消除非主属性对候选键的部分依赖
- **相关**：1NF、3NF、Normalization

### 2PC
- **中文**：两阶段提交
- **全称**：Two-Phase Commit
- **说明**：分布式事务中保证所有节点一致提交或回滚的协议
- **相关**：Distributed Transaction、XA、ACID

### 2PL
- **中文**：两阶段锁
- **全称**：Two-Phase Locking
- **说明**：事务分为加锁阶段和解锁阶段的并发控制协议
- **相关**：Lock、Serializability、Concurrency Control

### 3NF
- **中文**：第三范式
- **全称**：Third Normal Form
- **说明**：满足 2NF 且消除非主属性对候选键的传递依赖
- **相关**：2NF、BCNF、Normalization
