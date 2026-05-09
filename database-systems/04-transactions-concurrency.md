# 04. 事务与并发 (Transactions & Concurrency)

## 事务基础

### Atomicity / 原子性
- **中文**：原子性
- **定义**：事务是一个不可分割的工作单位，要么全部执行成功，要么全部不执行
- **说明**：通过 UNDO 日志实现；事务中任何操作失败都会导致整个事务回滚；外部观察不到中间状态
- **相关**：ACID、Transaction（事务）、Rollback（回滚）

### Commit / 提交
- **中文**：提交
- **定义**：将事务中所有修改永久保存到数据库的操作
- **说明**：COMMIT 后事务对数据库的更改对其他事务可见；提交前修改仅在当前事务可见；DDL 语句通常隐式提交
- **相关**：Rollback（回滚）、Transaction（事务）、ACID

### Durability / 持久性
- **中文**：持久性
- **定义**：已提交的事务修改在系统故障后仍然保持
- **说明**：通过 Write-Ahead Logging（WAL）和磁盘持久化实现；数据库崩溃后恢复时重做已提交事务
- **相关**：ACID、WAL（预写日志）、Redo Log（重做日志）

### Rollback / 回滚
- **中文**：回滚
- **定义**：撤销事务中所有已执行的操作，恢复到事务开始前的状态
- **说明**：ROLLBACK 后事务中所有修改被撤销；可用于显式取消事务或发生错误时自动回滚；与 COMMIT 互斥
- **相关**：Commit（提交）、Transaction（事务）、UNDO Log（撤销日志）

### Savepoint / 保存点
- **中文**：保存点
- **定义**：事务内部设置的中间标记，允许回滚到该点而非事务起点
- **说明**：SAVEPOINT savepoint_name 设置；ROLLBACK TO savepoint_name 回滚到保存点；释放保存点前资源不释放
- **相关**：Transaction（事务）、Rollback（回滚）

### Transaction / 事务
- **中文**：事务
- **定义**：一组数据库操作的逻辑工作单元，满足 ACID 特性
- **说明**：事务保证数据库从一个一致状态转换到另一个一致状态；BEGIN/START TRANSACTION 开始，COMMIT/ROLLBACK 结束
- **相关**：ACID、Commit（提交）、Rollback（回滚）

---

## 隔离级别

### Isolation / 隔离性
- **中文**：隔离性
- **定义**：并发执行的事务互不干扰，每个事务感觉像在独占运行
- **说明**：完全隔离影响并发性能；通过隔离级别在一致性和并发性之间权衡；实现机制包括锁和 MVCC
- **相关**：ACID、Isolation Level（隔离级别）、Concurrency Control（并发控制）

### Isolation Level / 隔离级别
- **中文**：隔离级别
- **定义**：定义事务之间隔离程度的标准，平衡一致性和并发性能
- **说明**：四个标准级别：READ UNCOMMITTED（最低，脏读）→ READ COMMITTED（不可重复读）→ REPEATABLE READ（幻读）→ SERIALIZABLE（最高，完全隔离）
- **相关**：Dirty Read（脏读）、Non-Repeatable Read（不可重复读）、Phantom Read（幻读）

### READ COMMITTED / 读已提交
- **中文**：读已提交
- **定义**：事务只能读取其他事务已提交的数据，避免脏读
- **说明**：大多数数据库的默认隔离级别；可能发生不可重复读和幻读；每次读取都获取最新已提交快照
- **相关**：Isolation Level（隔离级别）、Dirty Read（脏读）、Non-Repeatable Read（不可重复读）

### READ UNCOMMITTED / 读未提交
- **中文**：读未提交
- **定义**：最低的隔离级别，事务可以读取其他事务未提交的数据
- **说明**：允许脏读（Dirty Read）；并发性能最高但一致性最差；实际中很少使用
- **相关**：Isolation Level（隔离级别）、Dirty Read（脏读）

### REPEATABLE READ / 可重复读
- **中文**：可重复读
- **定义**：同一事务中多次读取同一数据结果一致，避免不可重复读
- **说明**：InnoDB 默认级别；通过 MVCC 或锁实现；可能发生幻读（Phantom Read）；InnoDB 的间隙锁防止幻读
- **相关**：Isolation Level（隔离级别）、Non-Repeatable Read（不可重复读）、Phantom Read（幻读）

### SERIALIZABLE / 串行化
- **中文**：串行化
- **定义**：最高的隔离级别，事务完全串行执行，避免所有并发异常
- **说明**：通过范围锁或完全串行化实现；并发性能最差；严格保证数据一致性
- **相关**：Isolation Level（隔离级别）、Phantom Read（幻读）、Lock（锁）

### Snapshot Isolation / 快照隔离
- **中文**：快照隔离
- **定义**：事务开始时获取数据库的一致性快照，期间不受其他事务影响
- **说明**：避免脏读、不可重复读和幻读；写冲突时可能更新丢失（Write Skew）；实际中比 SERIALIZABLE 更常用
- **相关**：MVCC、Isolation Level（隔离级别）、Write Skew（写偏斜）

---

## 并发异常

### Dirty Read / 脏读
- **中文**：脏读
- **定义**：一个事务读取了另一个事务尚未提交的修改数据
- **说明**：如果对方事务回滚，读取的数据就是无效的；READ COMMITTED 及以上级别可避免
- **相关**：Isolation Level（隔离级别）、READ UNCOMMITTED、Rollback（回滚）

### Lost Update / 丢失更新
- **中文**：丢失更新
- **定义**：两个事务同时读取并修改同一数据，后提交的事务覆盖了先提交的事务的修改
- **说明**：典型的并发冲突；可通过乐观锁（版本号）或悲观锁（行锁）避免
- **相关**：Concurrency Control（并发控制）、Optimistic Locking（乐观锁）、Pessimistic Locking（悲观锁）

### Non-Repeatable Read / 不可重复读
- **中文**：不可重复读
- **定义**：同一事务内两次读取同一行数据，结果不一致（中间被其他事务修改并提交）
- **说明**：与脏读不同，不可重复读读取的是已提交数据；REPEATABLE READ 及以上级别可避免
- **相关**：Isolation Level（隔离级别）、Dirty Read（脏读）、Phantom Read（幻读）

### Phantom Read / 幻读
- **中文**：幻读
- **定义**：同一事务内两次执行相同条件查询，结果集行数不同（中间有其他事务插入/删除符合条件的行）
- **说明**：与不可重复读不同，幻读关注行的增减而非值的变化；SERIALIZABLE 级别可避免
- **相关**：Isolation Level（隔离级别）、Non-Repeatable Read（不可重复读）、Gap Lock（间隙锁）

### Write Skew / 写偏斜
- **中文**：写偏斜
- **定义**：两个并发事务基于各自读取的数据快照进行修改，合起来违反业务约束
- **说明**：发生在 Snapshot Isolation 下；经典例子：两个医生同时值班，各自读取后都决定下班；需要 SERIALIZABLE 或外部约束解决
- **相关**：Snapshot Isolation（快照隔离）、SERIALIZABLE、Constraint（约束）

---

## 并发控制机制

### Concurrency Control / 并发控制
- **中文**：并发控制
- **定义**：保证多个事务并发执行时数据库一致性的机制
- **说明**：主要方法：锁机制（Locking）、多版本并发控制（MVCC）、乐观并发控制；目标是最大化并发同时避免异常
- **相关**：Transaction（事务）、Isolation Level（隔离级别）、Lock（锁）

### Deadlock / 死锁
- **中文**：死锁
- **定义**：两个或多个事务互相等待对方释放资源，导致无限等待
- **说明**：死锁必要条件：互斥、占有且等待、不可抢占、循环等待；解决方法：超时检测、等待图检测、按固定顺序加锁
- **相关**：Lock（锁）、Wait-for Graph（等待图）、Timeout（超时）

### Lock / 锁
- **中文**：锁
- **定义**：控制并发事务对数据访问的同步机制
- **说明**：锁类型：共享锁（S Lock，读锁）、排他锁（X Lock，写锁）；粒度：行锁、表锁、页锁；意向锁（IS/IX）用于表级和行级锁协调
- **相关**：Concurrency Control（并发控制）、Deadlock（死锁）、Two-Phase Locking（两阶段锁）

### Lock Escalation / 锁升级
- **中文**：锁升级
- **定义**：数据库将多个细粒度锁（行锁）合并为粗粒度锁（表锁）以减少锁开销
- **说明**：行锁过多时自动触发；减少内存占用但降低并发度；不同数据库触发阈值不同
- **相关**：Lock（锁）、Granularity（粒度）、Concurrency（并发）

### Lock Timeout / 锁超时
- **中文**：锁超时
- **定义**：事务等待获取锁超过指定时间后自动放弃或回滚
- **说明**：防止无限等待和死锁；需平衡：超时太短增加重试，太长影响响应
- **相关**：Deadlock（死锁）、Lock（锁）、Retry（重试）

### MVCC (Multi-Version Concurrency Control) / 多版本并发控制
- **中文**：多版本并发控制
- **定义**：通过维护数据的多个版本实现读写不阻塞的并发控制机制
- **说明**：读操作读取历史版本快照，写操作创建新版本；避免读阻塞写、写阻塞读；PostgreSQL 和 InnoDB 均使用 MVCC
- **相关**：Snapshot Isolation（快照隔离）、Transaction ID、Undo Log（撤销日志）

### Optimistic Locking / 乐观锁
- **中文**：乐观锁
- **定义**：假设冲突很少发生，提交时检查数据是否被其他事务修改的并发控制策略
- **说明**：通常通过版本号（Version）或时间戳实现；适合读多写少场景；冲突时重试或报错
- **相关**：Pessimistic Locking（悲观锁）、Version（版本号）、CAS（比较并交换）

### Pessimistic Locking / 悲观锁
- **中文**：悲观锁
- **定义**：假设冲突经常发生，在读取数据时立即加锁防止其他事务修改的策略
- **说明**：SELECT ... FOR UPDATE 显式加排他锁；适合写多读少、冲突频繁场景；可能降低并发性能
- **相关**：Optimistic Locking（乐观锁）、Lock（锁）、FOR UPDATE

### Two-Phase Locking (2PL) / 两阶段锁
- **中文**：两阶段锁
- **定义**：事务分为加锁阶段（只能加锁）和解锁阶段（只能解锁）的锁协议
- **说明**：基本 2PL 可能发生死锁；严格两阶段锁（Strict 2PL）事务结束才释放排他锁，避免级联回滚；是 SERIALIZABLE 的充分条件
- **相关**：Lock（锁）、Serializability（可串行化）、Deadlock（死锁）

### Wait-for Graph / 等待图
- **中文**：等待图
- **定义**：用于死锁检测的有向图，节点是事务，边表示等待关系
- **说明**：图中存在环表示发生死锁；DBMS 定期检测并选择牺牲者（回滚成本最小的事务）解除死锁
- **相关**：Deadlock（死锁）、Detection（检测）、Timeout（超时）

---

## 恢复机制

### CheckPoint / 检查点
- **中文**：检查点
- **定义**：将内存中已提交事务的修改强制写入磁盘，并记录日志位置的机制
- **说明**：减少系统恢复时间；检查点之前的已提交事务无需重做；定期自动触发或手动执行
- **相关**：Recovery（恢复）、WAL（预写日志）、Redo Log（重做日志）

### Crash Recovery / 崩溃恢复
- **中文**：崩溃恢复
- **定义**：数据库系统从故障（崩溃、断电）中恢复到一致状态的过程
- **说明**：使用 Redo Log 重做已提交事务，UNDO Log 撤销未提交事务；ARIES 是经典恢复算法
- **相关**：WAL（预写日志）、Redo Log（重做日志）、UNDO Log（撤销日志）

### REDO Log / 重做日志
- **中文**：重做日志
- **定义**：记录已提交事务修改的日志，用于故障后重新应用这些修改
- **说明**：先写日志再写磁盘（WAL 原则）；崩溃恢复时按日志重做；顺序写入性能高
- **相关**：UNDO Log（撤销日志）、WAL（预写日志）、Crash Recovery（崩溃恢复）

### UNDO Log / 撤销日志
- **中文**：撤销日志
- **定义**：记录事务修改前数据状态的日志，用于事务回滚或崩溃恢复时撤销未提交修改
- **说明**：事务失败或回滚时使用；MVCC 也利用 UNDO Log 构建历史版本；与 REDO Log 配合使用
- **相关**：REDO Log（重做日志）、Rollback（回滚）、MVCC

### WAL (Write-Ahead Logging) / 预写日志
- **中文**：预写日志
- **定义**：在数据修改写入磁盘前，先将对应的日志记录写入持久存储的原则
- **说明**：WAL 保证已提交事务的持久性；日志顺序写入，磁盘随机写入；是现代数据库恢复机制的基础
- **相关**：REDO Log（重做日志）、Durability（持久性）、Crash Recovery（崩溃恢复）
