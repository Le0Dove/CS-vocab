# 07. 同步与互斥 (Synchronization & Mutual Exclusion)

## 基础概念

### ABA Problem / ABA 问题
- **中文**：ABA 问题
- **定义**：CAS 的局限性，值从 A 变为 B 又变回 A，CAS 无法检测中间变化
- **说明**：ABA 问题可能导致数据结构损坏；解决方案包括使用版本号（Double-Word CAS）、 hazard pointer 等
- **相关**：CAS（比较并交换）、Lock-Free（无锁）

### Acquire Semantics / 获取语义
- **中文**：获取语义
- **定义**：内存排序语义，确保获取操作之后的读写不会在获取操作之前执行
- **说明**：获取语义用于锁的获取操作（如 lock）；保证临界区内的操作不会重排到锁之前
- **相关**：Release Semantics（释放语义）、Memory Barrier（内存屏障）

### acquire()
- **中文**：获取（锁/信号量）
- **定义**：获取锁或信号量的操作
- **相关**：release()、Lock（锁）、Mutex（互斥锁）

### Actor Model / Actor 模型
- **中文**：Actor 模型
- **定义**：并发计算模型，Actor 是独立的计算实体，通过异步消息传递通信
- **说明**：每个 Actor 有自己的状态和行为，不共享内存；Actor 接收消息、处理消息、发送消息、创建新 Actor；Erlang、Akka 使用 Actor 模型
- **相关**：Message Passing（消息传递）、Concurrency（并发）

### Async / 异步
- **音标**：/ˈeɪsɪŋk/ 或 /eɪˈsɪŋk/
- **中文**：异步
- **定义**：操作不阻塞调用者，完成后通过回调或通知返回结果
- **说明**：异步 I/O 允许程序在等待 I/O 时继续执行其他任务；Node.js 基于异步 I/O；C# async/await、Python asyncio
- **相关**：Sync（同步）、Callback（回调）、Promise

### Atomic Operation / 原子操作
- **中文**：原子操作
- **定义**：不可中断的操作，要么全部完成，要么完全不执行
- **说明**：原子操作不需要锁，效率高；现代 CPU 提供原子指令（如 x86 的 LOCK 前缀、XCHG、CMPXCHG；ARM 的 LDREX/STREX）；用于实现锁和无锁数据结构
- **相关**：CAS（比较并交换）、Memory Barrier（内存屏障）、Lock-Free（无锁）

### Barrier / 屏障
- **音标**：/ˈbæriər/
- **中文**：屏障
- **定义**：同步点，所有线程到达后才能继续执行
- **说明**：屏障用于并行算法中的阶段同步；如矩阵计算中，所有线程完成当前阶段后才能进入下一阶段；CyclicBarrier 是可重复使用的屏障
- **相关**：Synchronization（同步）、Parallel Computing（并行计算）

### Binary Semaphore / 二进制信号量
- **中文**：二进制信号量
- **定义**：取值只有 0 和 1 的信号量，功能同互斥锁
- **说明**：二进制信号量用于实现互斥或同步；wait() 减为 0 时阻塞，signal() 增为 1 时唤醒
- **相关**：Semaphore（信号量）、Mutex（互斥锁）

### Blocking / 阻塞
- **中文**：阻塞
- **定义**：进程因等待某个事件而暂停执行，让出 CPU
- **说明**：阻塞时进程进入等待状态，不消耗 CPU；事件发生后进程变为就绪；与忙等待相对
- **相关**：Busy Waiting（忙等待）、Sleep（睡眠）、Wake Up（唤醒）

### Blocking Queue / 阻塞队列
- **中文**：阻塞队列
- **定义**：支持阻塞插入和移除操作的队列
- **说明**：队列为空时，取元素操作阻塞；队列满时，插入操作阻塞；Java BlockingQueue 接口是典型实现
- **相关**：Queue（队列）、Producer-Consumer Problem（生产者-消费者问题）

### Bounded Buffer / 有界缓冲区
- **中文**：有界缓冲区
- **定义**：容量有限的缓冲区，用于生产者-消费者问题
- **说明**：有界缓冲区防止生产者无限生产；使用两个信号量：empty（空槽位数）和 full（满槽位数）
- **相关**：Buffer（缓冲区）、Producer-Consumer Problem（生产者-消费者问题）

### Broadcast / 广播
- **音标**：/ˈbrɔːdkæst/
- **中文**：广播
- **定义**：唤醒等待条件变量的所有进程
- **说明**：broadcast()/notifyAll() 唤醒所有等待进程；被唤醒的进程竞争获取锁，只有一个能继续，其他继续等待；适合条件变化可能影响多个等待者的情况
- **同义词**：Notify All
- **相关**：Condition Variable（条件变量）、Signal（信号）

### Busy Waiting / 忙等待
- **中文**：忙等待
- **定义**：进程反复检查某个条件是否满足，而不是睡眠等待
- **说明**：忙等待浪费 CPU 时间，但延迟低；适合等待时间极短的场景；自旋锁使用忙等待
- **同义词**：Spinning、Busy Loop、Spin-wait
- **相关**：Spinlock（自旋锁）、Blocking（阻塞）

### Callback / 回调
- **音标**：/ˈkɔːlbæk/
- **中文**：回调
- **定义**：异步操作完成后调用的函数
- **说明**：回调是异步编程的基础；如读取文件完成后调用回调函数处理数据；回调地狱（Callback Hell）是过多嵌套回调的问题
- **相关**：Async（异步）、Promise、Event-Driven（事件驱动）

### CAS (Compare-and-Swap) / 比较并交换
- **发音**：/kæs/
- **中文**：比较并交换
- **定义**：原子操作，比较内存值与期望值，如果相等则更新为新值
- **说明**：CAS 是无锁编程的基础；如果比较失败，操作不执行；需要循环重试（自旋）；ABA 问题是 CAS 的局限性
- **同义词**：Compare-and-Set、Compare-and-Exchange
- **相关**：Atomic Operation（原子操作）、Lock-Free（无锁）

### Cigarette Smokers Problem / 吸烟者问题
- **中文**：吸烟者问题
- **定义**：经典的同步问题，三个吸烟者分别拥有烟草、纸和火柴，需要一个中介随机放两种材料在桌上，拥有第三种材料的吸烟者可以制作香烟并吸烟
- **说明**：需要同步中介和吸烟者；每个吸烟者等待自己需要的两种材料；使用信号量解决
- **相关**：Synchronization（同步）、Semaphore（信号量）

---

## 原子操作与内存模型

### Compare-and-Exchange / 比较并交换
- **中文**：比较并交换
- **定义**：同 CAS
- **相关**：CAS（比较并交换）

### Compare-and-Set / 比较并设置
- **中文**：比较并设置
- **定义**：同 CAS
- **相关**：CAS（比较并交换）

### Concurrency / 并发
- **音标**：/kənˈkʌrənsi/
- **中文**：并发
- **定义**：多个任务在重叠的时间段内执行，但不一定同时执行
- **说明**：并发是逻辑上的同时性；单核 CPU 上通过时间片轮转实现并发；并发需要处理同步和竞争问题
- **相关**：Parallelism（并行）、Synchronization（同步）、Race Condition（竞态条件）

### Condition Variable / 条件变量
- **中文**：条件变量
- **定义**：管程中的同步机制，允许进程等待某个条件成立
- **说明**：条件变量支持 wait()（释放锁并等待条件）、signal()/notify()（唤醒等待该条件的进程）、broadcast()/notifyAll()（唤醒所有等待进程）；用于实现复杂的同步逻辑，如生产者-消费者
- **相关**：Monitor（管程）、Wait（等待）、Signal（信号）

### Consumer / 消费者
- **音标**：/kənˈsjuːmər/
- **中文**：消费者
- **定义**：从缓冲区取出数据的进程/线程
- **相关**：Producer（生产者）、Producer-Consumer Problem（生产者-消费者问题）

### Coroutine / 协程
- **发音**：/koʊˈruːtiːn/
- **中文**：协程
- **定义**：可以暂停和恢复执行的函数，支持协作式多任务
- **说明**：协程比线程轻量，切换开销小；协程在用户空间调度，不需要内核介入；Python asyncio、Go goroutine、Kotlin 协程
- **相关**：Thread（线程）、Async（异步）、Yield（让出）

### CountDownLatch / 倒计时门闩
- **中文**：倒计时门闩
- **定义**：一种门闩实现，计数器减到 0 时打开
- **说明**：CountDownLatch 初始化为 N，每个线程完成任务后调用 countDown()；主线程调用 await() 等待计数器为 0
- **相关**：Latch（门闩）、Synchronization（同步）

### Counting Semaphore / 计数信号量
- **中文**：计数信号量
- **定义**：取值可以是任意非负整数的信号量
- **说明**：计数信号量用于控制对有限数量资源的访问；如限制同时访问数据库连接的线程数为 10
- **相关**：Semaphore（信号量）、Resource Pool（资源池）

### CSP (Communicating Sequential Processes) / 通信顺序进程
- **发音**：/siː-es-piː/
- **中文**：通信顺序进程
- **定义**：Hoare 提出的并发编程模型，进程通过通信（channel）而非共享内存交互
- **说明**：CSP 是 Go 语言的并发模型基础；进程独立运行，通过同步通信交换数据；避免共享状态和锁
- **相关**：Channel（通道）、Go、Actor Model（Actor 模型）

### CyclicBarrier / 循环屏障
- **中文**：循环屏障
- **定义**：可重复使用的屏障，所有线程到达后执行可选动作，然后重置
- **说明**：CyclicBarrier 适合多阶段并行算法；可以指定 barrier action（所有线程到达后执行的操作）
- **相关**：Barrier（屏障）、Synchronization（同步）

### Data Race / 数据竞争
- **中文**：数据竞争
- **定义**：多个线程并发访问同一内存位置，至少一个是写操作，且没有同步的竞态条件
- **说明**：数据竞争是未定义行为的来源；C/C++ 中数据竞争导致未定义行为；Java 中影响可见性和有序性
- **相关**：Race Condition（竞态条件）、Synchronization（同步）、Memory Model（内存模型）

---

## 同步原语

### Dining Philosophers Problem / 哲学家就餐问题
- **中文**：哲学家就餐问题
- **定义**：经典的死锁和同步问题，五位哲学家围坐餐桌，每人需要两根筷子才能就餐
- **说明**：如果所有哲学家同时拿起左边的筷子，会导致死锁；解决方案包括：限制同时就餐人数、奇偶哲学家不同顺序拿筷子、使用管程等
- **相关**：Deadlock（死锁）、Synchronization（同步）、Chopstick（筷子）

### Empty Semaphore / 空信号量
- **中文**：空信号量
- **定义**：生产者-消费者问题中，记录缓冲区空槽位数的信号量
- **说明**：初始值为缓冲区大小；生产者 wait(empty) 后生产，消费者 signal(empty) 后消费
- **相关**：Full Semaphore（满信号量）、Producer-Consumer Problem（生产者-消费者问题）

### Event / 事件
- **音标**：/ɪˈvent/
- **中文**：事件
- **定义**：一种同步机制，一个线程通知其他线程某个事件已发生
- **说明**：事件有两种状态：有信号（Signaled）和无信号（Non-signaled）；线程等待事件变为有信号状态；Windows 中常用
- **相关**：Synchronization（同步）、Signal（信号）

### Event Flag / 事件标志
- **中文**：事件标志
- **定义**：一组二进制标志，用于线程间事件通知
- **相关**：Event（事件）、Synchronization（同步）

### Event Loop / 事件循环
- **中文**：事件循环
- **定义**：不断检查事件队列并分发事件到处理函数的运行时机制
- **说明**：事件循环是事件驱动编程的核心；单线程事件循环避免锁竞争，但需要非阻塞 I/O；JavaScript、Node.js 使用事件循环
- **相关**：Event-Driven（事件驱动）、Callback（回调）

### Event-Driven / 事件驱动
- **中文**：事件驱动
- **定义**：程序流程由事件（如用户输入、I/O 完成）触发的编程范式
- **说明**：事件驱动编程适合高并发场景（如 Web 服务器）；使用事件循环（Event Loop）处理事件；Node.js、GUI 编程使用事件驱动
- **相关**：Event Loop（事件循环）、Callback（回调）、Async（异步）

### Exclusive Lock / 排他锁
- **中文**：排他锁
- **定义**：同 Write Lock，同一时间只有一个线程可以持有
- **相关**：Read-Write Lock（读写锁）、Shared Lock（共享锁）

### False Sharing / 伪共享
- **中文**：伪共享
- **定义**：不同 CPU 上的线程访问不同变量，但变量位于同一缓存行，导致缓存行频繁失效
- **说明**：伪共享严重影响多线程性能；解决方法包括填充（Padding）使变量位于不同缓存行
- **相关**：Cache Line（缓存行）、Cache Coherence（缓存一致性）

### Fence / 栅栏
- **中文**：栅栏
- **定义**：同 Memory Barrier
- **相关**：Memory Barrier（内存屏障）

### Fetch-and-Add / 读取并增加
- **中文**：读取并增加
- **定义**：原子操作，读取内存值并将其增加指定值
- **说明**：Fetch-and-Add 用于实现计数器、队列等；x86 的 XADD 指令支持 Fetch-and-Add
- **相关**：Atomic Operation（原子操作）、Counter（计数器）

### Fork-Join / 分叉合并
- **中文**：分叉合并
- **定义**：一种并行编程模型，任务分叉为子任务并行执行，完成后合并结果
- **说明**：Fork-Join 是 divide-and-conquer 的并行版本；Java ForkJoinPool、Cilk 使用 Fork-Join 模型
- **相关**：Parallel Computing（并行计算）、Thread Pool（线程池）

---

## 并发问题与解决方案

### Full Barrier / 全屏障
- **中文**：全屏障
- **定义**：同时保证读写操作顺序的内存屏障
- **说明**：全屏障之前的所有内存操作在之后的所有内存操作之前完成；最严格但也最慢
- **相关**：Memory Barrier（内存屏障）

### Full Semaphore / 满信号量
- **中文**：满信号量
- **定义**：生产者-消费者问题中，记录缓冲区满槽位数的信号量
- **说明**：初始值为 0；消费者 wait(full) 后消费，生产者 signal(full) 后生产
- **相关**：Empty Semaphore（空信号量）、Producer-Consumer Problem（生产者-消费者问题）

### Future / 未来
- **音标**：/ˈfjuːtʃər/
- **中文**：未来
- **定义**：表示异步计算结果的对象
- **说明**：Future 允许提交任务后继续执行其他代码，稍后获取结果；get() 方法阻塞直到结果可用；Java Future、C++ std::future
- **相关**：Promise、Async（异步）、Concurrent Programming（并发编程）

### Goroutine
- **发音**：/ɡoʊ-ruːtiːn/
- **中文**：Goroutine
- **定义**：Go 语言中的轻量级线程
- **说明**：Goroutine 由 Go 运行时管理，初始栈很小（2KB），可以动态增长；使用 channel 进行通信；数以万计的 goroutine 可以轻松运行
- **相关**：Coroutine（协程）、Channel（通道）、Go

### Happens-Before / Happens-Before 关系
- **中文**：Happens-Before 关系
- **定义**：内存模型中定义的操作顺序关系，如果 A happens-before B，则 A 的结果对 B 可见
- **说明**：Happens-Before 关系通过同步操作（锁、volatile、线程启动/结束）建立；是分析并发程序正确性的基础
- **相关**：Memory Model（内存模型）、Synchronization（同步）

### Hoare Semantics / Hoare 语义
- **中文**：Hoare 语义
- **定义**：管程的一种语义，signal 后当前进程立即交出锁，被唤醒进程立即执行
- **说明**：Hoare 语义保证被唤醒进程立即执行，实现复杂但语义清晰；实际系统很少使用
- **相关**：Mesa Semantics（Mesa 语义）、Condition Variable（条件变量）

### Latch / 门闩
- **音标**：/lætʃ/
- **中文**：门闩
- **定义**：一次性使用的同步原语，一旦打开就保持打开状态
- **说明**：门闩用于等待某个事件发生后所有等待线程同时继续；与屏障不同，门闩是一次性的；CountDownLatch 是常见的实现
- **相关**：Barrier（屏障）、Synchronization（同步）

### Linearizability / 线性一致性
- **中文**：线性一致性
- **定义**：并发对象正确性标准，每个操作看起来在调用和返回之间的某个瞬间原子执行
- **说明**：线性一致性是最强的并发正确性保证；满足线性一致性的对象 behave 如同顺序执行
- **相关**：Sequential Consistency（顺序一致性）、Correctness（正确性）

### Load Barrier / 读屏障
- **中文**：读屏障
- **定义**：确保读操作按顺序执行的内存屏障
- **说明**：读屏障之前的读操作在之后的读操作之前完成；不影响写操作
- **相关**：Memory Barrier（内存屏障）、Store Barrier（写屏障）

### Load-Link/Store-Conditional (LL/SC) / 链接加载/条件存储
- **中文**：链接加载/条件存储
- **定义**：ARM、PowerPC 等架构中的原子操作对
- **说明**：LL 读取内存值并建立链接，SC 在链接未被打破时存储新值；如果链接被打破（其他线程写入），SC 失败；功能同 CAS
- **相关**：CAS（比较并交换）、Atomic Operation（原子操作）

### Lock / 锁
- **音标**：/lɒk/
- **中文**：锁
- **定义**：用于控制对共享资源访问的同步机制
- **说明**：锁分为互斥锁（Mutex）、读写锁（Read-Write Lock）、自旋锁（Spinlock）、递归锁（Recursive Lock）等
- **相关**：Mutex（互斥锁）、Unlock（解锁）、Acquire（获取）、Release（释放）

### lock()
- **中文**：加锁
- **定义**：获取锁的操作
- **相关**：unlock()、Lock（锁）、Mutex（互斥锁）

### Lock-Free / 无锁
- **中文**：无锁
- **定义**：不使用传统锁，通过原子操作实现同步的并发编程方式
- **说明**：无锁算法保证至少一个线程可以推进；使用 CAS、LL/SC 等原子操作；比基于锁的并发更复杂，但可以避免死锁和优先级反转
- **相关**：Atomic Operation（原子操作）、CAS（比较并交换）、Wait-Free（无等待）

### MapReduce / 映射归约
- **中文**：映射归约
- **定义**：一种并行编程模型，将大数据处理分为 Map（映射）和 Reduce（归约）两个阶段
- **说明**：Map 阶段将数据分割并并行处理，Reduce 阶段汇总结果；Hadoop、Spark 使用 MapReduce；适合数据并行任务
- **相关**：Parallel Computing（并行计算）、Big Data（大数据）

### Memory Model / 内存模型
- **中文**：内存模型
- **定义**：规定多线程程序中内存操作可见性和顺序的规则
- **说明**：不同语言/平台有不同内存模型：Java Memory Model (JMM)、C++ Memory Model、x86 TSO (Total Store Order)、ARM 弱内存模型等
- **相关**：Sequential Consistency（顺序一致性）、Memory Barrier（内存屏障）

### Mesa Semantics / Mesa 语义
- **中文**：Mesa 语义
- **定义**：管程的一种语义，signal 后当前进程继续执行，被唤醒进程移到就绪队列竞争锁
- **说明**：Mesa 语义实现简单，但被唤醒进程需要重新检查条件（使用 while 循环）；Java、Pthreads 使用 Mesa 语义
- **相关**：Hoare Semantics（Hoare 语义）、Condition Variable（条件变量）

### Monitor / 管程
- **音标**：/ˈmɒnɪtər/
- **中文**：管程
- **定义**：一种高级同步原语，封装共享变量和对它们的操作，提供自动互斥
- **说明**：管程由 Hoare 和 Brinch Hansen 提出；进程只能调用管程的过程访问共享数据；管程自动保证互斥；支持条件变量实现同步；Java 的 synchronized 块是管程的一种实现
- **相关**：Condition Variable（条件变量）、Mutex（互斥锁）、Synchronized（同步）

### MPI (Message Passing Interface) / 消息传递接口
- **发音**：/ɛm-piː-aɪ/
- **中文**：消息传递接口
- **定义**：并行计算中进程间消息传递的标准 API
- **说明**：MPI 是分布式内存并行编程的标准；提供点对点通信（send/recv）和集合通信（broadcast、reduce 等）；广泛用于 HPC
- **相关**：Message Passing（消息传递）、HPC（高性能计算）

### Mutex / 互斥锁
- **发音**：/ˈmjuːtɛks/ 或 /mjuː-teks/
- **中文**：互斥锁
- **定义**：提供独占访问的锁，同一时间只有一个线程可以持有
- **说明**：Mutex 用于保护临界区；lock()/acquire() 获取锁，unlock()/release() 释放锁；获取已被占用的锁会阻塞
- **全名**：Mutual Exclusion Lock
- **相关**：Lock（锁）、Critical Section（临界区）、Semaphore（信号量）

### Mutual Exclusion / 互斥
- **中文**：互斥
- **定义**：确保同一时刻只有一个进程/线程访问临界区或共享资源的机制
- **说明**：互斥是同步的一种特殊形式；通过锁、信号量、原子操作等实现
- **相关**：Critical Section（临界区）、Lock（锁）、Mutex（互斥锁）

### Obstruction-Free / 无障碍
- **中文**：无障碍
- **定义**：如果一个线程单独执行（不受其他线程干扰），可以在有限步骤内完成操作
- **说明**：无障碍是最弱的非阻塞保证；比无锁和无等待更容易实现，但并发度较低
- **相关**：Lock-Free（无锁）、Wait-Free（无等待）

---

## 经典同步问题

### P Operation / P 操作（Wait）
- **中文**：P 操作（等待操作）
- **定义**：信号量的等待操作
- **说明**：P 来自荷兰语"Proberen"（测试）；wait() 将信号量值减 1，如果结果 < 0，则调用者阻塞；也称为 down()、acquire()
- **同义词**：Wait Operation、Down Operation、Acquire Operation
- **相关**：V Operation（V 操作）、Semaphore（信号量）

### Padding / 填充
- **中文**：填充
- **定义**：在变量之间插入无用字节，使变量位于不同缓存行
- **说明**：填充用于避免伪共享；如 64 字节缓存行中，一个变量占 8 字节，后面填充 56 字节
- **相关**：False Sharing（伪共享）、Cache Line（缓存行）

---

## 并发编程模型

### Parallelism / 并行
- **音标**：/ˈpærəlelɪzəm/
- **中文**：并行
- **定义**：多个任务在同一时刻真正同时执行
- **说明**：并行需要多核 CPU 或多处理器；并行是物理上的同时性；并行计算可以提高性能
- **相关**：Concurrency（并发）、Multicore（多核）、Multiprocessor（多处理器）

### Priority Ceiling / 优先级天花板
- **中文**：优先级天花板
- **定义**：将持有资源的进程优先级提升到可能访问该资源的所有进程的最高优先级
- **说明**：优先级天花板是更激进的优先级继承，提前提升优先级；实现简单但可能不必要地提升优先级
- **相关**：Priority Inversion（优先级反转）、Priority Inheritance（优先级继承）

### Priority Inheritance / 优先级继承
- **中文**：优先级继承
- **定义**：低优先级进程持有高优先级进程需要的资源时，临时提升低优先级进程的优先级
- **说明**：优先级继承避免中优先级进程抢占低优先级进程，从而阻塞高优先级进程；资源释放后恢复原始优先级
- **相关**：Priority Inversion（优先级反转）、Priority Ceiling（优先级天花板）

### Priority Inversion / 优先级反转
- **中文**：优先级反转
- **定义**：高优先级进程被低优先级进程阻塞，而中优先级进程在运行的现象
- **说明**：优先级反转导致高优先级进程无法及时执行；解决方案：优先级继承（Priority Inheritance）、优先级天花板（Priority Ceiling）
- **相关**：Priority Inheritance（优先级继承）、Priority Ceiling（优先级天花板）、Mutex（互斥锁）

### Producer / 生产者
- **音标**：/prəˈdjuːsər/
- **中文**：生产者
- **定义**：向缓冲区添加数据的进程/线程
- **相关**：Consumer（消费者）、Producer-Consumer Problem（生产者-消费者问题）

### Producer-Consumer Problem / 生产者-消费者问题
- **中文**：生产者-消费者问题
- **定义**：经典的同步问题，生产者向缓冲区生产数据，消费者从缓冲区消费数据
- **说明**：需要同步：缓冲区满时生产者等待，缓冲区空时消费者等待；需要互斥：生产者和消费者不能同时操作缓冲区；使用信号量或管程解决
- **相关**：Bounded Buffer（有界缓冲区）、Semaphore（信号量）、Monitor（管程）

### Promise / 承诺
- **音标**：/ˈprɒmɪs/
- **中文**：承诺
- **定义**：与 Future 配对的机制，用于设置异步计算的结果
- **说明**：Promise 提供 setValue()/setException() 方法设置结果；Future 通过 Promise 获取结果；JavaScript Promise、C++ std::promise
- **相关**：Future、Async（异步）

### Read-Write Lock / 读写锁
- **中文**：读写锁
- **定义**：允许多个读者同时访问或一个写者独占访问的锁
- **说明**：读操作之间不互斥，读和写互斥，写和写互斥；适合读多写少的场景；也称为 Shared-Exclusive Lock
- **同义词**：Shared Lock、Reader-Writer Lock、RWLock
- **相关**：Mutex（互斥锁）、Lock（锁）

### Readers-Writers Problem / 读者-写者问题
- **中文**：读者-写者问题
- **定义**：经典的同步问题，多个读者可以同时读，但写者需要独占访问
- **说明**：三种变体：读者优先、写者优先、公平方案；使用信号量或读写锁解决
- **相关**：Reader（读者）、Writer（写者）、Read-Write Lock（读写锁）

### Recursive Lock / 递归锁
- **中文**：递归锁
- **定义**：允许同一线程多次获取而不会死锁的锁
- **说明**：递归锁记录持有线程和递归计数；同一线程多次 lock() 增加计数，unlock() 减少计数，计数为 0 时真正释放；也称为 Reentrant Lock
- **同义词**：Reentrant Lock
- **相关**：Mutex（互斥锁）、Deadlock（死锁）

### Reentrant Lock / 可重入锁
- **中文**：可重入锁
- **定义**：同 Recursive Lock
- **相关**：Recursive Lock（递归锁）

### Release Semantics / 释放语义
- **中文**：释放语义
- **定义**：内存排序语义，确保释放操作之前的读写不会在释放操作之后执行
- **说明**：释放语义用于锁的释放操作（如 unlock）；保证临界区内的操作不会重排到锁之后
- **相关**：Acquire Semantics（获取语义）、Memory Barrier（内存屏障）

### release()
- **中文**：释放（锁/信号量）
- **定义**：释放锁或信号量的操作
- **相关**：acquire()、Unlock（解锁）

### Semaphore / 信号量
- **音标**：/ˈseməfɔːr/
- **中文**：信号量
- **定义**：用于控制多个线程访问共享资源的计数器同步机制
- **说明**：信号量由 Dijkstra 提出；wait(P) 减少计数器，为负时阻塞；signal(V) 增加计数器，唤醒等待线程；分为二进制信号量和计数信号量
- **相关**：P Operation（P 操作）、V Operation（V 操作）、Mutex（互斥锁）

### Sequential Consistency / 顺序一致性
- **中文**：顺序一致性
- **定义**：最强的内存模型，所有线程看到的内存操作顺序一致
- **说明**：顺序一致性是最直观的模型，但性能差；现代 CPU 通常提供较弱的内存模型（如 TSO、PSO、宽松模型）
- **相关**：Memory Model（内存模型）、Linearizability（线性一致性）

### Shared Lock / 共享锁
- **中文**：共享锁
- **定义**：同 Read Lock，允许多个线程同时持有
- **相关**：Read-Write Lock（读写锁）、Exclusive Lock（排他锁）

### signal()
- **中文**：信号操作
- **定义**：释放信号量或通知等待线程的操作
- **相关**：wait()、V Operation（V 操作）、Release（释放）

### Sleep / 睡眠
- **音标**：/sliːp/
- **中文**：睡眠
- **定义**：进程主动放弃 CPU 并进入等待状态一段时间
- **说明**：sleep() 使进程暂停执行指定时间；睡眠时间到后进程变为就绪；与忙等待不同，睡眠不消耗 CPU
- **相关**：Wake Up（唤醒）、Blocking（阻塞）

### Sleeping Barber Problem / 睡眠理发师问题
- **中文**：睡眠理发师问题
- **定义**：经典的同步问题，理发师在椅子上睡觉，有顾客来时理发，没有顾客时继续睡觉；理发店有有限个等待座位
- **说明**：需要同步理发师和顾客；使用信号量：customers（等待顾客数）、barber（理发师状态）、mutex（互斥访问等待计数）
- **相关**：Producer-Consumer Problem（生产者-消费者问题）、Semaphore（信号量）

### Spinlock / 自旋锁
- **发音**：/ˈspɪn-lɒk/
- **中文**：自旋锁
- **定义**：获取锁失败时循环等待（自旋）而不是阻塞的锁
- **说明**：自旋锁适合保护极短的临界区（多处理器上）；自旋期间 CPU 忙等待，不切换上下文；内核中常用
- **相关**：Mutex（互斥锁）、Busy Waiting（忙等待）、Lock（锁）

### Store Barrier / 写屏障
- **中文**：写屏障
- **定义**：确保写操作按顺序执行的内存屏障
- **说明**：写屏障之前的写操作在之后的写操作之前完成；不影响读操作
- **相关**：Memory Barrier（内存屏障）、Load Barrier（读屏障）

### Synchronization / 同步
- **音标**：/ˌsɪŋkrənaɪˈzeɪʃn/
- **中文**：同步
- **定义**：协调多个进程/线程的执行顺序，使它们按一定规则协作
- **说明**：同步确保共享资源的有序访问和事件的有序发生；分为互斥（Mutual Exclusion）和条件同步（Condition Synchronization）
- **相关**：Mutual Exclusion（互斥）、Concurrency（并发）、Parallelism（并行）

### Task Queue / 任务队列
- **中文**：任务队列
- **定义**：存储等待执行任务的队列
- **说明**：线程池中的工作线程从任务队列获取任务执行；可以使用有界队列或无界队列
- **相关**：Thread Pool（线程池）、Blocking Queue（阻塞队列）

### Test-and-Set / 测试并设置
- **中文**：测试并设置
- **定义**：原子操作，读取内存值并将其设置为 1
- **说明**：Test-and-Set 用于实现自旋锁；虽然简单但可能导致饥饿；x86 的 XCHG 指令可以实现 Test-and-Set
- **相关**：Atomic Operation（原子操作）、Spinlock（自旋锁）

### Thundering Herd Problem / 惊群问题
- **中文**：惊群问题
- **定义**：多个进程/线程等待同一事件，事件发生时所有等待者被唤醒，但只有一个能成功处理
- **说明**：惊群导致大量不必要的上下文切换和竞争；解决方案：使用互斥锁保护条件检查，或使用条件变量的广播替代信号
- **相关**：Condition Variable（条件变量）、Mutex（互斥锁）

### Timed Lock / 限时锁
- **中文**：限时锁
- **定义**：尝试获取锁，如果在指定时间内未获取则返回失败
- **说明**：timed_lock() 避免无限期等待；适用于需要超时控制的场景
- **相关**：Lock（锁）、Try-Lock（尝试加锁）

---

## 高级同步机制

### Try-Lock / 尝试加锁
- **中文**：尝试加锁
- **定义**：尝试获取锁，如果锁不可用立即返回失败而不阻塞
- **说明**：try_lock() 是非阻塞的锁获取；适用于需要避免阻塞或需要超时的场景
- **相关**：Lock（锁）、Mutex（互斥锁）、Non-blocking（非阻塞）

### unlock()
- **中文**：解锁
- **定义**：释放锁的操作
- **相关**：lock()、Release（释放）

### V Operation / V 操作（Signal）
- **中文**：V 操作（信号操作）
- **定义**：信号量的信号操作
- **说明**：V 来自荷兰语"Verhogen"（增加）；signal() 将信号量值加 1，如果有等待线程则唤醒一个；也称为 up()、release()
- **同义词**：Signal Operation、Up Operation、Release Operation
- **相关**：P Operation（P 操作）、Semaphore（信号量）

### Visibility / 可见性
- **音标**：/ˌvɪzəˈbɪləti/
- **中文**：可见性
- **定义**：一个线程对共享变量的修改对其他线程可见的保证
- **说明**：没有同步的情况下，一个线程的修改可能对其他线程不可见（缓存、寄存器优化）；volatile 和锁保证可见性
- **相关**：Memory Model（内存模型）、volatile、Synchronization（同步）

### volatile
- **发音**：/ˈvɒlətaɪl/
- **中文**：易失的（关键字）
- **定义**：C/C++/Java 中的关键字，禁止编译器对变量进行优化，保证可见性
- **说明**：volatile 保证变量的读写直接访问内存（而非寄存器/缓存），但不保证原子性和有序性；Java 的 volatile 提供更强的保证（禁止指令重排）
- **相关**：Visibility（可见性）、Memory Model（内存模型）

### wait()
- **中文**：等待操作
- **定义**：获取信号量或锁的操作，如果不可用则阻塞
- **相关**：signal()、P Operation（P 操作）、Acquire（获取）

### Wait-Free / 无等待
- **中文**：无等待
- **定义**：比无锁更强的保证，每个线程都可以在有限步骤内完成操作
- **说明**：无等待算法保证所有线程都能推进，不会被其他线程无限期延迟；实现最复杂但并发度最高
- **相关**：Lock-Free（无锁）、Atomic Operation（原子操作）

### Wake Up / 唤醒
- **中文**：唤醒
- **定义**：将等待状态的进程变为就绪状态
- **说明**：唤醒操作由信号量、条件变量、中断等触发；被唤醒的进程不一定立即执行，需要等待 CPU 调度
- **相关**：Sleep（睡眠）、Blocking（阻塞）

### Yield / 让出
- **音标**：/jiːld/
- **中文**：让出（CPU）
- **定义**：进程主动放弃 CPU
- **说明**：sched_yield() 将当前进程放到同优先级队列末尾；让出 CPU 给其他同优先级进程；协作调度中必须调用 yield
- **相关**：Sleep（睡眠）、Blocking（阻塞）、Cooperative Scheduling（协作调度）
