# 05. 死锁 (Deadlock)

### Banker's Algorithm / 银行家算法
- **中文**：银行家算法
- **定义**：由 Dijkstra 提出的死锁避免算法
- **说明**：算法模拟银行贷款：操作系统类比银行，资源类比资金，进程类比客户；分配资源前检查是否会导致不安全状态
- **相关**：Safe State（安全状态）、Unsafe State（不安全状态）

### Chopstick / 筷子
- **音标**：/ˈtʃɒpstɪk/
- **中文**：筷子
- **定义**：哲学家就餐问题中的资源（每位哲学家需要两根筷子）
- **相关**：Dining Philosophers Problem（哲学家就餐问题）

### Circular Wait / 循环等待
- **中文**：循环等待
- **定义**：存在一个进程等待链，链中的每个进程都等待下一个进程持有的资源的条件
- **说明**：可以通过资源排序（Resource Ordering）要求进程按固定顺序申请资源来破坏此条件
- **相关**：Wait-for Graph（等待图）、Resource Ordering（资源排序）

### Deadlock / 死锁
- **中文**：死锁
- **定义**：两个或多个进程互相等待对方持有的资源，导致所有进程都无法继续执行的状态
- **说明**：死锁是并发系统中的经典问题；操作系统需要通过预防、避免、检测或恢复机制处理死锁
- **相关**：Starvation（饥饿）、Livelock（活锁）

### Deadlock Avoidance / 死锁避免
- **中文**：死锁避免
- **定义**：在资源分配时通过算法判断是否会进入不安全状态，如果是则拒绝分配
- **说明**：死锁避免不需要破坏必要条件，而是在运行时动态判断；需要知道进程的最大资源需求；典型算法：银行家算法
- **相关**：Safe State（安全状态）、Unsafe State（不安全状态）、Banker's Algorithm（银行家算法）

### Deadlock Detection / 死锁检测
- **中文**：死锁检测
- **定义**：允许死锁发生，但定期检测系统中是否存在死锁
- **说明**：通过检测资源分配图或等待图中的环来实现；发现死锁后采取恢复措施
- **相关**：Resource Allocation Graph（资源分配图）、Wait-for Graph（等待图）、Deadlock Recovery（死锁恢复）

### Deadlock Handling / 死锁处理
- **中文**：死锁处理
- **定义**：操作系统应对死锁的策略和方法
- **说明**：四种基本策略：预防（Prevention）、避免（Avoidance）、检测（Detection）和恢复（Recovery）、忽略（Ignorance）
- **相关**：Deadlock Prevention（死锁预防）、Deadlock Avoidance（死锁避免）、Deadlock Detection（死锁检测）、Deadlock Recovery（死锁恢复）

### Deadlock Ignorance / 死锁忽略
- **中文**：死锁忽略
- **定义**：假设死锁不会发生，不采取任何预防、避免或检测措施
- **说明**：大多数操作系统（如 Windows、Unix/Linux）采用死锁忽略策略，因为死锁发生概率低，处理开销大；由程序员或用户处理死锁问题
- **同义词**：Ostrich Algorithm（鸵鸟算法）
- **相关**：Deadlock Handling（死锁处理）

### Deadlock Prevention / 死锁预防
- **中文**：死锁预防
- **定义**：通过破坏死锁四个必要条件之一来确保死锁不会发生
- **说明**：预防死锁可能降低资源利用率和系统吞吐量；四种方法：破坏互斥（通常不可行）、破坏持有并等待、破坏非抢占、破坏循环等待
- **相关**：Mutual Exclusion（互斥）、Hold and Wait（持有并等待）、No Preemption（非抢占）、Circular Wait（循环等待）

### Deadlock Recovery / 死锁恢复
- **中文**：死锁恢复
- **定义**：检测到死锁后，采取措施解除死锁
- **说明**：恢复方法包括：进程终止（终止一个或多个死锁进程）、资源抢占（抢占部分资源分配给其他进程）
- **相关**：Deadlock Detection（死锁检测）、Process Termination（进程终止）、Resource Preemption（资源抢占）

### Dining Philosophers Problem / 哲学家就餐问题
- **中文**：哲学家就餐问题
- **定义**：Dijkstra 提出的经典同步问题，描述资源分配与死锁的挑战
- **说明**：五位哲学家围坐圆桌，每人需要左右两根筷子才能就餐；展示了死锁、饥饿和资源分配问题的经典场景
- **相关**：Deadlock（死锁）、Starvation（饥饿）、Chopstick（筷子）

### Hold and Wait / 持有并等待
- **中文**：持有并等待
- **定义**：进程持有至少一个资源，同时等待获取其他进程持有的资源的条件
- **说明**：可以通过要求进程一次性申请所有资源来破坏此条件
- **相关**：Deadlock Prevention（死锁预防）、Necessary Conditions for Deadlock（死锁必要条件）

### Livelock / 活锁
- **中文**：活锁
- **定义**：进程不断改变状态以响应其他进程，但没有任何进程能继续执行的状态
- **说明**：活锁中进程是活跃的（不断运行），但没有实际进展；类似两人在走廊互相让路但始终过不去
- **相关**：Deadlock（死锁）、Starvation（饥饿）

### Mutual Exclusion / 互斥
- **音标**：/ˈmjuːtʃuəl ɪkˈskluːʒən/
- **中文**：互斥
- **定义**：至少一个资源必须处于非共享模式，即同一时间只能被一个进程使用
- **说明**：死锁的四个必要条件之一；共享资源本身不需要互斥，但许多资源（如打印机、文件写操作）本质上需要互斥访问
- **相关**：Necessary Conditions for Deadlock（死锁必要条件）、Deadlock Prevention（死锁预防）

### Necessary Conditions for Deadlock / 死锁必要条件
- **中文**：死锁必要条件
- **定义**：死锁发生必须同时满足的四个条件
- **说明**：四个条件缺一不可：互斥、持有并等待、非抢占、循环等待
- **相关**：Mutual Exclusion（互斥）、Hold and Wait（持有并等待）、No Preemption（非抢占）、Circular Wait（循环等待）

### No Preemption / 非抢占
- **中文**：非抢占
- **定义**：已分配给进程的资源不能被强制回收，只能由持有进程主动释放的条件
- **说明**：如果允许抢占资源，可以破坏此条件；但有些资源（如打印机）不适合抢占
- **相关**：Resource Preemption（资源抢占）、Deadlock Prevention（死锁预防）

### Process Termination / 进程终止
- **中文**：进程终止
- **定义**：通过终止一个或多个死锁进程来解除死锁
- **说明**：可以终止所有死锁进程，或一次终止一个直到死锁解除；选择终止进程时需要考虑进程优先级、已计算时间、资源占用等
- **相关**：Deadlock Recovery（死锁恢复）、Victim（牺牲品）

### Reader / 读者
- **中文**：读者
- **定义**：只读取数据不修改的进程/线程
- **说明**：多个读者可以同时访问共享数据；读者之间不需要互斥
- **相关**：Writer（写者）、Readers-Writers Problem（读者-写者问题）

### Readers-Writers Problem / 读者-写者问题
- **中文**：读者-写者问题
- **定义**：管理对共享数据的并发访问，其中读者只读不写，写者需要独占访问
- **说明**：多个读者可同时访问；写者需要独占访问；常见方案包括读者优先、写者优先和公平方案
- **相关**：Reader（读者）、Writer（写者）、Mutual Exclusion（互斥）

### Resource / 资源
- **音标**：/ˈriːsɔːrs/
- **中文**：资源
- **定义**：系统中供进程使用的实体，如 CPU、内存、I/O 设备、文件等
- **说明**：资源分为可抢占资源（如 CPU、内存）和不可抢占资源（如打印机、磁带机）
- **相关**：Resource Type（资源类型）、Resource Instance（资源实例）

### Resource Allocation / 资源分配
- **中文**：资源分配
- **定义**：操作系统将资源分配给进程的过程
- **说明**：资源分配需要避免死锁；策略包括静态分配（一次性分配所有资源）和动态分配（按需分配）
- **相关**：Resource（资源）、Deadlock Prevention（死锁预防）

### Resource Allocation Graph / 资源分配图
- **中文**：资源分配图
- **定义**：用有向图表示进程和资源之间分配和请求关系的方法
- **说明**：进程中用圆表示，资源类型用方框表示（方框内的小圆表示实例）；请求边（进程→资源）和分配边（资源→进程）；图中存在环可能表示死锁
- **相关**：Wait-for Graph（等待图）、Deadlock Detection（死锁检测）

### Resource Instance / 资源实例
- **中文**：资源实例
- **定义**：资源类型的具体实体
- **说明**：如系统中两台打印机是打印机资源类型的两个实例
- **相关**：Resource（资源）、Resource Type（资源类型）

### Resource Ordering / 资源排序
- **中文**：资源排序
- **定义**：为所有资源类型分配全局顺序号，要求进程按递增顺序申请资源
- **说明**：资源排序破坏循环等待条件，从而预防死锁
- **相关**：Circular Wait（循环等待）、Deadlock Prevention（死锁预防）

### Resource Preemption / 资源抢占
- **中文**：资源抢占
- **定义**：从死锁进程中抢占部分资源分配给其他进程以解除死锁
- **说明**：资源抢占需要处理三个问题：选择牺牲品（哪个进程的资源被抢占）、回滚（将进程状态恢复到获取资源前）、饥饿（避免同一进程总是被抢占）
- **相关**：Rollback（回滚）、Victim（牺牲品）、Deadlock Recovery（死锁恢复）

### Resource Release / 资源释放
- **中文**：资源释放
- **定义**：进程使用完资源后将其归还给操作系统
- **说明**：及时释放资源可以减少死锁风险
- **相关**：Resource Allocation（资源分配）、Resource Request（资源请求）

### Resource Request / 资源请求
- **中文**：资源请求
- **定义**：进程向操作系统申请资源的行为
- **说明**：资源请求可能成功（资源可用）或失败（资源已被占用）；失败时进程通常阻塞等待
- **相关**：Resource Allocation（资源分配）、Resource Release（资源释放）

### Resource Type / 资源类型
- **中文**：资源类型
- **定义**：一类资源的抽象，如打印机、磁带机、CPU 等
- **说明**：每种资源类型可以有多个实例；如系统有 3 台打印机，则打印机资源类型有 3 个实例
- **相关**：Resource（资源）、Resource Instance（资源实例）

### Rollback / 回滚
- **音标**：/ˈroʊlbæk/
- **中文**：回滚
- **定义**：将进程状态恢复到之前的某个检查点
- **说明**：资源抢占后，被抢占的进程需要回滚到获取该资源之前的状态
- **相关**：Checkpoint（检查点）、Resource Preemption（资源抢占）

### Safe Sequence / 安全序列
- **中文**：安全序列
- **定义**：一个进程执行顺序，使得对于每个 Pi，其资源需求可以被当前可用资源加上之前所有进程释放的资源满足
- **说明**：安全序列可能不唯一；如果存在安全序列，系统处于安全状态
- **相关**：Safe State（安全状态）、Banker's Algorithm（银行家算法）

### Safe State / 安全状态
- **中文**：安全状态
- **定义**：存在一个进程执行序列，使得每个进程都能顺利完成（获得所需资源并释放）的状态
- **说明**：安全状态一定不会死锁；系统处于安全状态时，至少有一个进程可以完成
- **相关**：Unsafe State（不安全状态）、Safe Sequence（安全序列）、Banker's Algorithm（银行家算法）

### Starvation / 饥饿
- **音标**：/stɑːrˈveɪʃən/
- **中文**：饥饿
- **定义**：进程长时间等待资源但系统仍在正常运行的状态
- **说明**：与死锁不同，饥饿中系统整体仍在进步，只是某个进程得不到服务；可能由不公平调度或资源抢占引起
- **相关**：Deadlock（死锁）、Livelock（活锁）

### Think / 思考
- **中文**：思考
- **定义**：哲学家不需要筷子的状态
- **相关**：Eat（就餐）、Dining Philosophers Problem（哲学家就餐问题）

### Unsafe State / 不安全状态
- **中文**：不安全状态
- **定义**：不存在安全序列的状态
- **说明**：不安全状态不一定死锁，但有可能死锁；银行家算法拒绝导致不安全状态的资源分配请求
- **相关**：Safe State（安全状态）、Safe Sequence（安全序列）、Banker's Algorithm（银行家算法）

### Victim / 牺牲品
- **音标**：/ˈvɪktɪm/
- **中文**：牺牲品
- **定义**：被选中终止或被抢占资源的进程
- **说明**：选择牺牲品的目标是最小化代价；考虑因素包括进程优先级、已执行时间、还需资源等
- **相关**：Resource Preemption（资源抢占）、Process Termination（进程终止）

### Wait-for Graph / 等待图
- **中文**：等待图
- **定义**：资源分配图的简化，只保留进程节点，边表示进程等待关系
- **说明**：等待图中，Pi → Pj 表示进程 Pi 等待进程 Pj 释放资源；图中存在环表示死锁（单实例资源时）
- **相关**：Resource Allocation Graph（资源分配图）、Deadlock Detection（死锁检测）

### Wait-for Graph Algorithm / 等待图算法
- **中文**：等待图算法
- **定义**：通过检测等待图中是否存在环来检测死锁的算法
- **说明**：适用于资源类型只有单实例的情况；使用图遍历算法（如 DFS）检测环
- **相关**：Wait-for Graph（等待图）、Deadlock Detection（死锁检测）

### Writer / 写者
- **中文**：写者
- **定义**：修改数据的进程/线程
- **说明**：写者需要独占访问，不能有其他读者或写者同时访问
- **相关**：Reader（读者）、Readers-Writers Problem（读者-写者问题）
