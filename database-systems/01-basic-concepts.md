# 01. 基础概念 (Basic Concepts)

### ACID
- **中文**：ACID 特性
- **定义**：数据库事务正确执行的四个基本属性
- **说明**：Atomicity（原子性）：事务全部完成或全部不执行；Consistency（一致性）：事务前后数据保持一致状态；Isolation（隔离性）：并发事务互不干扰；Durability（持久性）：提交后的数据永久保存
- **相关**：Transaction（事务）、CAP Theorem（CAP 定理）

### CAP Theorem / CAP 定理
- **中文**：CAP 定理
- **定义**：分布式系统中，一致性（Consistency）、可用性（Availability）、分区容错性（Partition Tolerance）三者最多同时满足两个
- **说明**：CP 系统（牺牲可用性，如传统关系数据库集群）；AP 系统（牺牲一致性，如 Cassandra）；CA 系统（不能容忍网络分区）；BASE 理论是 CAP 的工程实践
- **相关**：BASE、Distributed Database（分布式数据库）、Consistency（一致性）

### Catalog / 数据字典
- **中文**：数据字典（系统目录）
- **定义**：存储数据库元数据（表结构、索引、约束、统计信息）的系统表集合
- **说明**：DBMS 通过查询数据字典获知数据库结构；用户也可查询（如 information_schema）
- **同义词**：Data Dictionary（数据字典）、System Catalog（系统目录）
- **相关**：Metadata（元数据）、Schema（模式）

### Constraint / 约束
- **中文**：约束
- **定义**：对数据库表中数据的限制规则，保证数据完整性
- **说明**：PRIMARY KEY（主键）、FOREIGN KEY（外键）、UNIQUE（唯一）、NOT NULL（非空）、CHECK（检查）、DEFAULT（默认）
- **相关**：Integrity（完整性）、Schema（模式）

### Cursor / 游标
- **中文**：游标
- **定义**：在 SQL 查询结果集中逐行移动的指针，用于逐行处理查询结果
- **说明**：游标用于存储过程或嵌入式 SQL 中逐行处理；分为隐式游标和显式游标；大量数据时性能差，应适用集合操作代替
- **相关**：SQL、Result Set（结果集）、Stored Procedure（存储过程）

### Data Warehouse / 数据仓库
- **中文**：数据仓库
- **定义**：面向主题的、集成的、稳定的、随时间变化的数据集合，用于决策支持
- **说明**：与 OLTP 相对，数据仓库支持 OLAP；星型模型（Star Schema）和雪花型模型（Snowflake Schema）；ETL 是数据仓库的关键流程
- **同义词**：Data Warehouse (DW)
- **相关**：OLAP、ETL、Data Mining（数据挖掘）

### DBMS (Database Management System) / 数据库管理系统
- **中文**：数据库管理系统
- **定义**：管理数据库的软件系统，提供数据定义、操作、控制等功能
- **说明**：代表：MySQL、PostgreSQL、Oracle、SQL Server、MongoDB；主要功能：数据定义语言（DDL）、数据操作语言（DML）、数据控制语言（DCL）、事务管理
- **相关**：Database（数据库）、SQL、RDBMS

### DDL (Data Definition Language) / 数据定义语言
- **中文**：数据定义语言
- **定义**：用于定义数据库对象（表、索引、视图等）的 SQL 语句
- **说明**：CREATE（创建）、ALTER（修改）、DROP（删除）、TRUNCATE（截断）、RENAME（重命名）；DDL 操作自动提交
- **相关**：DML（数据操作语言）、DCL（数据控制语言）、SQL

### DML (Data Manipulation Language) / 数据操作语言
- **中文**：数据操作语言
- **定义**：用于查询和修改数据的 SQL 语句
- **说明**：SELECT（查询）、INSERT（插入）、UPDATE（更新）、DELETE（删除）；DML 需要显式 COMMIT 提交事务
- **同义词**：DML
- **相关**：DDL（数据定义语言）、DCL、SQL

### DCL (Data Control Language) / 数据控制语言
- **中文**：数据控制语言
- **定义**：用于控制数据库访问权限的 SQL 语句
- **说明**：GRANT（授予权限）、REVOKE（收回权限）
- **同义词**：DCL
- **相关**：DDL（数据定义语言）、DML

### ETL (Extract, Transform, Load) / 抽取-转换-加载
- **中文**：抽取-转换-加载
- **定义**：从多个数据源提取数据，清洗转换后载入数据仓库的流程
- **说明**：E 抽取（从源数据库/文件/API）；T 转换（清洗、去重、格式转换、聚合）；L 加载（载入目标数据仓库）；现代 ETL 中变换在目标库进行（ELT）
- **相关**：Data Warehouse（数据仓库）、Data Pipeline（数据管道）

### OLAP (Online Analytical Processing) / 联机分析处理
- **中文**：联机分析处理
- **定义**：面向数据分析的查询密集型处理模式
- **说明**：OLAP 支持多维分析（上钻、切片、旋转）；多维数据模型（MOLAP/ROLAP/HOLAP）；场景：BI 报表、决策分析
- **相关**：OLTP（联机事务处理）、Data Warehouse（数据仓库）

### OLTP (Online Transaction Processing) / 联机事务处理
- **中文**：联机事务处理
- **定义**：面向日常事务操作的短查询频繁处理模式
- **说明**：OLTP 系统强调一致性、可用性、低延迟
- **相关**：OLAP（联机分析处理）、Transaction（事务）

### Procedure / 存储过程
- **中文**：存储过程
- **定义**：预编译并存储在数据库中的 SQL 语句集合，可带参数调用
- **说明**：存储过程减少网络传输提升性能；包含逻辑控制结构（IF/LOOP）；封装业务逻辑；缺点：难于调试和移植
- **同义词**：Stored Procedure
- **相关**：Function（函数）、Trigger（触发器）、SQL

### RDBMS (Relational DBMS) / 关系数据库管理系统
- **中文**：关系数据库管理系统
- **定义**：基于关系模型的数据库管理系统
- **说明**：以表（Relation）形式组织数据，通过 SQL 操作；代表：MySQL、PostgreSQL、Oracle、SQL Server
- **同义词**：RDBMS
- **相关**：SQL、Relational Model（关系模型）

### Schema / 模式
- **中文**：模式
- **定义**：数据库的逻辑结构描述，包括表、关系、约束等
- **说明**：三层模式体系：外模式（用户视图）、概念模式（全局逻辑结构）、内模式（物理存储）；模式是数据库的蓝图
- **同义词**：Database Schema（数据库模式）
- **相关**：DDL（数据定义语言）、Table（表）

### Trigger / 触发器
- **中文**：触发器
- **定义**：当特定事件（INSERT/UPDATE/DELETE）发生时由 DBMS 自动执行的存储过程
- **说明**：触发器用于审计日志、复杂约束检查、级联更新；行级触发和语句级触发
- **相关**：Stored Procedure（存储过程）、Event（事件）

### View / 视图
- **中文**：视图
- **定义**：基于一个或多个表的查询结果定义的虚拟表
- **说明**：视图不存储实际数据，只保存查询定义；简化复杂查询、提供安全（隐藏部分列）、可更新视图
- **同义词**：View
- **相关**：Table（表）、SELECT
