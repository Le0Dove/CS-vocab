# 05. 索引 (Indexing)

## 索引基础

### B+ Tree / B+ 树
- **中文**：B+ 树
- **定义**：数据库索引最常用的平衡树结构，所有数据存储在叶子节点
- **说明**：支持高效的范围查询和点查询；叶子节点通过指针链接，便于顺序扫描；InnoDB 聚簇索引使用 B+ 树；阶数（Order）决定每个节点键数
- **相关**：B-Tree、Index（索引）、Clustered Index（聚簇索引）

### Bitmap Index / 位图索引
- **中文**：位图索引
- **定义**：用位图（Bitmap）表示列值与行位置对应关系的索引
- **说明**：适合低基数列（如性别、状态）；通过位运算（AND/OR/NOT）高效处理复杂条件；不适合高并发写入场景
- **相关**：Index（索引）、Low Cardinality（低基数）、OLAP

### Covering Index / 覆盖索引
- **中文**：覆盖索引
- **定义**：包含查询所需所有列的索引，无需回表查数据行
- **说明**：索引即数据，避免回表（Table Lookup）；EXPLAIN 中显示 Using Index；是查询优化的重要手段
- **同义词**：Index-Only Scan
- **相关**：Index（索引）、Query Optimization（查询优化）、EXPLAIN

### Full-Text Index / 全文索引
- **中文**：全文索引
- **定义**：针对文本内容分词后建立的索引，支持关键词搜索
- **说明**：支持自然语言查询和布尔查询；MySQL 用 MATCH ... AGAINST，PostgreSQL 用 tsvector/tsquery；适合文章、文档搜索
- **相关**：Search Engine（搜索引擎）、Inverted Index（倒排索引）、Elasticsearch

### Hash Index / 哈希索引
- **中文**：哈希索引
- **定义**：基于哈希表实现的索引，通过哈希函数直接定位数据
- **说明**：仅支持等值查询（=、IN），不支持范围查询；查询时间复杂度 O(1)；哈希冲突时可能退化为链表扫描
- **相关**：B+ Tree、Index（索引）、Hash Function（哈希函数）

### Index / 索引
- **中文**：索引
- **定义**：加速数据查询的附加数据结构，类似书籍的目录
- **说明**：牺牲写入性能和存储空间换取查询速度；需权衡索引数量和列选择；过多索引会降低写入性能并占用空间
- **相关**：B+ Tree、Query Optimization（查询优化）、Execution Plan（执行计划）

### Index Scan / 索引扫描
- **中文**：索引扫描
- **定义**：数据库通过遍历索引结构查找匹配行的数据访问方式
- **说明**：比全表扫描效率高；范围查询时扫描索引叶子节点；覆盖索引时无需回表
- **相关**：Index（索引）、Table Scan（表扫描）、Query Optimizer（查询优化器）

### Unique Index / 唯一索引
- **中文**：唯一索引
- **定义**：保证索引列值唯一的索引，自动在插入/更新时检查重复
- **说明**：与 UNIQUE 约束等效；可加速等值查询；允许 NULL 值（但只能有一个，因数据库而异）
- **相关**：UNIQUE Constraint（唯一约束）、Primary Key（主键）、Index（索引）

---

## 索引类型

### Clustered Index / 聚簇索引
- **中文**：聚簇索引
- **定义**：数据行物理存储顺序与索引键顺序一致的索引
- **说明**：一个表只能有一个聚簇索引；InnoDB 主键即聚簇索引；范围查询性能优异；插入非顺序主键可能导致页分裂
- **相关**：Primary Key（主键）、Non-Clustered Index（非聚簇索引）、Page Split（页分裂）

### Composite Index / 复合索引
- **中文**：复合索引
- **定义**：在多个列上建立的索引
- **说明**：列顺序至关重要（最左前缀原则）；WHERE 条件需包含最左列才能使用；列顺序应将高选择性列放在前面
- **同义词**：Multi-Column Index、Combined Index
- **相关**：Index（索引）、Selectivity（选择性）、Leftmost Prefix（最左前缀）

### Functional Index / 函数索引
- **中文**：函数索引
- **定义**：基于表达式或函数计算结果建立的索引
- **说明**：如 INDEX ON UPPER(name)；用于加速带函数的查询；PostgreSQL 12+ 和 MySQL 8.0+ 支持
- **相关**：Index（索引）、Expression（表达式）

### Non-Clustered Index / 非聚簇索引
- **中文**：非聚簇索引
- **定义**：索引结构与数据行物理存储分离的索引
- **说明**：索引叶子节点存储指向数据行的指针（或主键值）；一个表可以有多个非聚簇索引；MyISAM 所有索引均为非聚簇
- **同义词**：Secondary Index（二级索引）
- **相关**：Clustered Index（聚簇索引）、Index（索引）

### Partial Index / 部分索引
- **中文**：部分索引
- **定义**：只对表中满足特定条件的行建立索引
- **说明**：减少索引大小和维护开销；适合大表中仅查询热点数据的场景；PostgreSQL 支持，MySQL 不支持
- **相关**：Index（索引）、Condition（条件）、Filter（过滤）

### Primary Index / 主索引
- **中文**：主索引
- **定义**：在表的主键上建立的索引
- **说明**：主索引通常即聚簇索引；自动创建且不能为空；是表数据组织的基础
- **相关**：Primary Key（主键）、Clustered Index（聚簇索引）

### Reverse Index / 反向索引
- **中文**：反向索引
- **定义**：将索引键的字节反转后存储的索引
- **说明**：用于解决单调递增键（如序列号）的索引热点问题；将连续值分散到不同叶子节点；Oracle 支持，MySQL 可通过前缀反转模拟
- **相关**：Index（索引）、Hotspot（热点）、Sequential Key（顺序键）

### Secondary Index / 二级索引
- **中文**：二级索引
- **定义**：除主索引外的其他索引，通常是非聚簇索引
- **说明**：二级索引叶子节点存储主键值；查询时需先查二级索引再回表查聚簇索引（回表操作）；过多二级索引影响写入性能
- **相关**：Non-Clustered Index（非聚簇索引）、Primary Key（主键）、Covering Index（覆盖索引）

---

## 索引优化

### Cardinality / 基数
- **中文**：基数
- **定义**：索引列中不重复值的数量
- **说明**：高基数列（如身份证号）适合建索引；低基数列（如性别）不适合单独建索引；基数/总行数 = 选择性
- **相关**：Selectivity（选择性）、Index（索引）、Statistics（统计信息）

### Index Hint / 索引提示
- **中文**：索引提示
- **定义**：在 SQL 中显式指定数据库使用或忽略某个索引的语法
- **说明**：如 MySQL 的 USE INDEX、FORCE INDEX；用于纠正优化器选择不当；但可能随数据变化失效，应谨慎使用
- **相关**：Query Optimizer（查询优化器）、Index（索引）、Execution Plan（执行计划）

### Index Merge / 索引合并
- **中文**：索引合并
- **定义**：查询优化器使用多个索引分别查找，然后合并结果的技术
- **说明**：适用于 WHERE 条件有多个独立索引列；合并方式：Union（OR 条件）、Intersection（AND 条件）、Sort-Union；MySQL 支持
- **相关**：Query Optimizer（查询优化器）、Index（索引）

### Index Tuning / 索引调优
- **中文**：索引调优
- **定义**：通过分析和调整索引结构来优化查询性能的过程
- **说明**：步骤：分析慢查询 → 检查执行计划 → 评估现有索引 → 添加/删除/修改索引 → 验证效果；需平衡读写性能
- **相关**：Query Optimization（查询优化）、EXPLAIN、Slow Query（慢查询）

### Page Split / 页分裂
- **中文**：页分裂
- **定义**：B+ 树索引页已满时插入新数据，导致页分裂为两个页的操作
- **说明**：页分裂增加 I/O 开销并可能导致碎片；顺序插入可减少分裂；大量随机插入会降低索引效率
- **相关**：B+ Tree、Index（索引）、Fragmentation（碎片）

### Query Optimizer / 查询优化器
- **中文**：查询优化器
- **定义**：数据库中自动选择最优查询执行计划的组件
- **说明**：基于统计信息（表大小、索引基数、数据分布）评估不同执行计划成本；选择成本最低的方案
- **相关**：Execution Plan（执行计划）、Statistics（统计信息）、Cost Model（成本模型）

### Selectivity / 选择性
- **中文**：选择性
- **定义**：索引列中不重复值占总行数的比例
- **说明**：选择性 = Cardinality / Total Rows；选择性越高（接近 1），索引越有效；选择性低（<0.1）的列建索引效果差
- **相关**：Cardinality（基数）、Index（索引）

### Slow Query / 慢查询
- **中文**：慢查询
- **定义**：执行时间超过设定阈值的 SQL 查询
- **说明**：数据库提供慢查询日志记录；分析慢查询是性能优化的起点；常见原因：缺少索引、索引失效、大表扫描、复杂 JOIN
- **相关**：Index Tuning（索引调优）、Query Optimization（查询优化）、EXPLAIN

### Table Scan / 表扫描
- **中文**：表扫描
- **定义**：逐行扫描整个表的数据以查找匹配行的访问方式
- **说明**：全表扫描（Full Table Scan）性能差，但小表或高选择性查询时可能比索引快；EXPLAIN 中显示 ALL（MySQL）或 Seq Scan（PostgreSQL）
- **相关**：Index Scan（索引扫描）、Query Optimizer（查询优化器）

---

## 执行计划

### Cost Model / 成本模型
- **中文**：成本模型
- **定义**：查询优化器用于估算不同执行计划开销的数学模型
- **说明**：成本因素包括 I/O 次数、CPU 消耗、内存使用；基于统计信息计算；数据库自动收集统计信息
- **相关**：Query Optimizer（查询优化器）、Statistics（统计信息）、Execution Plan（执行计划）

### Execution Plan / 执行计划
- **定义**：数据库执行 SQL 查询的具体步骤和算法
- **说明**：通过 EXPLAIN 查看；包含扫描方式、连接算法、排序方法、成本估计；是 SQL 调优的核心依据
- **相关**：EXPLAIN、Query Optimizer（查询优化器）、Index（索引）

### Filter / 过滤
- **中文**：过滤
- **定义**：根据 WHERE 条件从扫描结果中筛选匹配行的操作
- **说明**：先扫描后过滤效率低；理想情况用索引直接定位；EXPLAIN 中显示 Filter 条件
- **相关**：WHERE、Index（索引）、Execution Plan（执行计划）

### Join Algorithm / 连接算法
- **中文**：连接算法
- **定义**：数据库执行表连接操作的具体算法
- **说明**：常见算法：Nested Loop Join（嵌套循环，适合小表）、Hash Join（哈希连接，适合无索引大表）、Merge Join（归并连接，适合已排序数据）
- **相关**：JOIN、Query Optimizer（查询优化器）、Execution Plan（执行计划）

### Predicate Pushdown / 谓词下推
- **中文**：谓词下推
- **定义**：将 WHERE 条件尽可能提前到数据源层执行的优化技术
- **说明**：减少数据传输和中间结果；对视图、子查询、分区表尤为重要；现代数据库优化器自动完成
- **相关**：Query Optimization（查询优化）、Filter（过滤）、Execution Plan（执行计划）

### Statistics / 统计信息
- **中文**：统计信息
- **定义**：数据库收集的关于表、列、索引的数据分布信息
- **说明**：包括行数、唯一值数、最大最小值、直方图等；优化器依赖统计信息选择执行计划；需定期更新（ANALYZE）
- **相关**：Query Optimizer（查询优化器）、Cost Model（成本模型）、ANALYZE
