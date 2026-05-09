# 03. SQL (Structured Query Language)

## 基础查询

### Aggregate Function / 聚合函数
- **中文**：聚合函数
- **定义**：对一组值进行计算并返回单一值的函数
- **说明**：常见聚合函数：COUNT（计数）、SUM（求和）、AVG（平均值）、MAX（最大值）、MIN（最小值）；通常与 GROUP BY 配合使用；聚合时 NULL 值通常被忽略（COUNT(*) 除外）
- **相关**：GROUP BY、HAVING、Window Function（窗口函数）

### Alias / 别名
- **中文**：别名
- **定义**：为表或列指定的临时替代名称
- **说明**：列别名用 AS 关键字（可省略）；表别名简化多表查询；别名只在当前查询有效
- **相关**：SELECT、JOIN、Subquery（子查询）

### CASE / 条件表达式
- **中文**：条件表达式
- **定义**：在 SQL 中实现条件逻辑的表达式
- **说明**：支持简单 CASE（等值比较）和搜索 CASE（条件判断）；常用于查询中的动态列值转换；可以嵌套使用
- **相关**：IF、DECODE、COALESCE

### CTE (Common Table Expression) / 公用表表达式
- **中文**：公用表表达式
- **定义**：在查询中定义的临时命名结果集，可在后续 SELECT 中引用
- **说明**：使用 WITH 关键字定义；可递归（Recursive CTE）处理层次数据；提高复杂查询可读性；比子查询更易维护
- **相关**：WITH、Subquery（子查询）、Recursive Query（递归查询）

### DISTINCT / 去重
- **中文**：去重
- **定义**：从查询结果中去除重复行的关键字
- **说明**：DISTINCT 作用于所有选定列的组合；与 GROUP BY 类似但不去聚合；大量数据时性能开销较大
- **相关**：SELECT、GROUP BY、UNIQUE

### GROUP BY / 分组
- **中文**：分组
- **定义**：将数据按指定列的值分组，以便对每组应用聚合函数
- **说明**：SELECT 中非聚合列必须出现在 GROUP BY 中（标准 SQL）；ROLLUP 和 CUBE 支持多维分组；HAVING 用于过滤分组结果
- **相关**：Aggregate Function（聚合函数）、HAVING、ROLLUP

### HAVING / 分组过滤
- **中文**：分组过滤
- **定义**：对 GROUP BY 分组后的结果进行条件过滤的子句
- **说明**：HAVING 过滤聚合结果，WHERE 过滤原始行；HAVING 可以使用聚合函数；执行顺序在 WHERE 之后
- **相关**：GROUP BY、WHERE、Aggregate Function（聚合函数）

### LIMIT / 限制行数
- **中文**：限制行数
- **定义**：限制查询返回结果集的行数
- **说明**：不同数据库语法不同：MySQL/PostgreSQL 用 LIMIT，SQL Server 用 TOP，Oracle 用 FETCH FIRST / ROWNUM；常与 OFFSET 配合实现分页
- **同义词**：TOP (SQL Server)、FETCH FIRST (Oracle)
- **相关**：OFFSET、Pagination（分页）

### NULL / 空值
- **中文**：空值
- **定义**：表示未知、缺失或未定义的值
- **说明**：NULL 不等于任何值（包括 NULL 本身）；判断 NULL 用 IS NULL / IS NOT NULL；聚合函数忽略 NULL；NULL 参与运算结果为 NULL
- **相关**：COALESCE、IS NULL、NVL

### OFFSET / 偏移量
- **中文**：偏移量
- **定义**：跳过查询结果的前 N 行
- **说明**：常与 LIMIT 配合实现分页；大数据量时 OFFSET 性能差，推荐使用键集分页（Keyset Pagination）
- **相关**：LIMIT、Pagination（分页）

### ORDER BY / 排序
- **中文**：排序
- **定义**：按指定列的值对查询结果进行升序或降序排列
- **说明**：ASC（升序，默认）、DESC（降序）；支持多列排序；NULL 排序行为因数据库而异（NULLS FIRST/LAST）
- **相关**：SELECT、GROUP BY、Index（索引）

### SELECT / 查询
- **中文**：查询
- **定义**：从数据库中检索数据的核心 SQL 语句
- **说明**：SELECT 指定列，FROM 指定表，WHERE 过滤条件；支持 *（所有列）或显式列名；是 SQL 中使用最频繁的语句
- **相关**：FROM、WHERE、INSERT、UPDATE、DELETE

### Subquery / 子查询
- **中文**：子查询
- **定义**：嵌套在另一个 SQL 语句中的查询
- **说明**：子查询可用在 SELECT、FROM、WHERE 中；相关子查询（Correlated Subquery）依赖外部查询；性能通常不如 JOIN
- **同义词**：Nested Query（嵌套查询）
- **相关**：JOIN、CTE、EXISTS、IN

### WHERE / 条件过滤
- **中文**：条件过滤
- **定义**：筛选满足指定条件的行
- **说明**：支持比较运算符（=、<>、>、<）、逻辑运算符（AND、OR、NOT）、范围（BETWEEN）、集合（IN）、模式匹配（LIKE）
- **相关**：SELECT、HAVING、JOIN

### Window Function / 窗口函数
- **中文**：窗口函数
- **定义**：对一组行（窗口）进行计算，但不改变结果集行数的函数
- **说明**：使用 OVER() 定义窗口；常用：ROW_NUMBER()、RANK()、DENSE_RANK()、LEAD()、LAG()、SUM() OVER()；在 OLAP 中广泛使用
- **同义词**：Analytic Function（分析函数）
- **相关**：OVER、PARTITION BY、ORDER BY

---

## 数据操作

### DELETE / 删除
- **中文**：删除
- **定义**：从表中删除满足条件的行
- **说明**：DELETE 可带 WHERE 条件；不带 WHERE 删除所有行（逐行删除，可回滚）；TRUNCATE 更快但不可回滚
- **相关**：TRUNCATE、DROP、WHERE

### INSERT / 插入
- **中文**：插入
- **定义**：向表中添加新行
- **说明**：INSERT INTO ... VALUES 插入单行或多行；INSERT INTO ... SELECT 从其他表插入；支持 RETURNING（PostgreSQL）获取插入值
- **相关**：UPDATE、DELETE、SELECT

### LIKE / 模式匹配
- **中文**：模式匹配
- **定义**：用于 WHERE 子句中进行字符串模糊匹配
- **说明**：% 匹配任意字符序列，_ 匹配单个字符；某些数据库支持正则表达式匹配（~、REGEXP）
- **相关**：WHERE、Wildcard（通配符）、Regular Expression（正则表达式）

### UPDATE / 更新
- **中文**：更新
- **定义**：修改表中已存在的数据行
- **说明**：UPDATE ... SET ... WHERE；WHERE 条件不可省略（否则更新全表）；支持多表 JOIN 更新（因数据库而异）
- **相关**：INSERT、DELETE、SET

### WITH / 临时结果集
- **中文**：临时结果集
- **定义**：定义 CTE 的关键字，创建可在查询中重复引用的临时命名结果集
- **说明**：支持多个 CTE 用逗号分隔；可递归定义处理树形结构；提升可读性和性能（某些数据库物化 CTE）
- **相关**：CTE、Subquery（子查询）

---

## 连接操作

### CROSS JOIN / 交叉连接
- **中文**：交叉连接
- **定义**：返回两个表所有行的笛卡尔积
- **说明**：结果行数 = 左表行数 × 右表行数；通常无意使用时性能极差；显式使用 CROSS JOIN 或省略 JOIN 条件
- **相关**：Cartesian Product（笛卡尔积）、JOIN

### FULL OUTER JOIN / 全外连接
- **中文**：全外连接
- **定义**：返回左右表所有行，匹配不上的用 NULL 填充
- **说明**：MySQL 不支持 FULL OUTER JOIN，需用 UNION 模拟；完整保留两个表的数据
- **相关**：LEFT JOIN、RIGHT JOIN、UNION

### INNER JOIN / 内连接
- **中文**：内连接
- **定义**：返回两个表中满足连接条件的匹配行
- **说明**：最常用的连接类型；ON 指定连接条件；与 WHERE 过滤不同，ON 在连接时过滤
- **同义词**：JOIN（默认 INNER）
- **相关**：OUTER JOIN、ON、WHERE

### LEFT JOIN / 左外连接
- **中文**：左外连接
- **定义**：返回左表所有行，右表匹配不上的用 NULL 填充
- **说明**：保留左表全部数据；右表条件应放在 ON 而非 WHERE 中；常用于查找缺失关联数据
- **同义词**：LEFT OUTER JOIN
- **相关**：RIGHT JOIN、FULL JOIN、INNER JOIN

### RIGHT JOIN / 右外连接
- **中文**：右外连接
- **定义**：返回右表所有行，左表匹配不上的用 NULL 填充
- **说明**：与 LEFT JOIN 方向相反；实际中较少使用，通常交换表顺序用 LEFT JOIN 替代
- **同义词**：RIGHT OUTER JOIN
- **相关**：LEFT JOIN、FULL JOIN

### SELF JOIN / 自连接
- **中文**：自连接
- **定义**：表与自身进行连接
- **说明**：必须使用别名区分同一表的不同实例；常用于层次数据（如员工-经理关系）
- **相关**：JOIN、Alias（别名）

### UNION / 并集
- **中文**：并集
- **定义**：合并两个查询结果集，去除重复行
- **说明**：UNION ALL 保留重复行且性能更好；要求两个查询列数和类型兼容；结果列名取自第一个查询
- **相关**：INTERSECT（交集）、EXCEPT（差集）、Subquery（子查询）

---

## 约束与完整性

### CHECK / 检查约束
- **中文**：检查约束
- **定义**：限制列值必须满足指定布尔表达式的约束
- **说明**：如 CHECK (age >= 0 AND age <= 150)；插入或更新时自动验证；部分数据库支持命名约束
- **相关**：Constraint（约束）、NOT NULL、DEFAULT

### DEFAULT / 默认值
- **中文**：默认值
- **定义**：当插入行未指定列值时自动使用的值
- **说明**：可以是常量、表达式或函数（如 CURRENT_TIMESTAMP）；减少 INSERT 语句的列数
- **相关**：INSERT、Constraint（约束）

### FOREIGN KEY / 外键
- **中文**：外键
- **定义**：建立两个表之间关联关系的约束
- **说明**：FOREIGN KEY 列引用另一表的主键；支持 ON DELETE CASCADE/SET NULL/RESTRICT 等级联行为
- **同义词**：FK
- **相关**：PRIMARY KEY、Referential Integrity（引用完整性）、JOIN

### NOT NULL / 非空
- **中文**：非空
- **定义**：限制列值不能为 NULL 的约束
- **说明**：确保列必须有值；常用于主键和必填字段；与 DEFAULT 配合使用可确保总有值
- **相关**：NULL、Constraint（约束）、CHECK

### PRIMARY KEY / 主键
- **中文**：主键
- **定义**：唯一标识表中每行的列或列组合
- **说明**：主键自动具有 NOT NULL 和 UNIQUE 约束；每个表只能有一个主键；通常用于建立表间关系
- **同义词**：PK
- **相关**：FOREIGN KEY、UNIQUE、Index（索引）

### UNIQUE / 唯一约束
- **中文**：唯一约束
- **定义**：限制列或列组合的值必须唯一，但允许 NULL
- **说明**：与主键不同，UNIQUE 允许 NULL；可有多列组合唯一约束；自动创建唯一索引
- **相关**：PRIMARY KEY、Index（索引）、Constraint（约束）

---

## 高级特性

### EXPLAIN / 执行计划
- **中文**：执行计划
- **定义**：显示数据库查询优化器生成的查询执行方案
- **说明**：分析查询性能的关键工具；显示扫描方式、连接算法、成本估计；不同数据库输出格式不同
- **同义词**：DESC (MySQL)、QUERY PLAN (PostgreSQL)
- **相关**：Query Optimizer（查询优化器）、Index（索引）

### MERGE / 合并
- **中文**：合并
- **定义**：根据条件判断执行 INSERT 或 UPDATE 的复合操作
- **说明**：MERGE INTO ... USING ... ON ... WHEN MATCHED ... WHEN NOT MATCHED；避免先查询再决定插入或更新
- **同义词**：UPSERT（非标准）、INSERT ... ON CONFLICT（PostgreSQL）
- **相关**：INSERT、UPDATE、Conflict Resolution（冲突解决）

### PIVOT / 透视
- **中文**：透视
- **定义**：将行数据转换为列数据的转换操作
- **说明**：将分组聚合结果从长格式转为宽格式；SQL Server/Oracle 支持 PIVOT 语法；其他数据库可用 CASE + GROUP BY 模拟
- **相关**：UNPIVOT、CASE、GROUP BY

### Recursive Query / 递归查询
- **中文**：递归查询
- **定义**：使用 Recursive CTE 反复引用自身结果处理层次或图数据的查询
- **说明**：必须包含递归终止条件；常用于组织结构、树遍历、路径查找；需注意递归深度限制
- **相关**：CTE、Hierarchical Data（层次数据）、Tree Traversal（树遍历）

### Stored Procedure / 存储过程
- **中文**：存储过程
- **定义**：预编译并存储在数据库中的一组 SQL 语句和控制逻辑
- **说明**：可带输入输出参数；封装业务逻辑减少网络传输；不同数据库语法差异大（PL/SQL、T-SQL）
- **相关**：Function（函数）、Trigger（触发器）、SQL

### Transaction / 事务
- **中文**：事务
- **定义**：一组作为单个逻辑工作单元执行的 SQL 操作
- **说明**：BEGIN/START TRANSACTION 开始，COMMIT 提交，ROLLBACK 回滚；保证 ACID 特性
- **相关**：ACID、COMMIT、ROLLBACK、Isolation Level（隔离级别）

### View / 视图
- **中文**：视图
- **定义**：基于查询结果定义的虚拟表，不存储实际数据
- **说明**：简化复杂查询、提供安全访问控制（隐藏列）；可更新视图需满足特定条件；物化视图存储实际数据
- **相关**：SELECT、Table（表）、Materialized View（物化视图）
