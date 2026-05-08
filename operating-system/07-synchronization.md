# 07. 同步与互斥 (Synchronization & Mutual Exclusion)

### ABA Problem / ABA 问题
- **中文**：ABA 问题
- **定义**：CAS 的局限性，值从 A 变为 B 又变回 A，CAS 无法检测中间变化
- **说明**：ABA 问题可能导致数据结构损坏；解决方案包括使用版本号（Double-Word CAS）、hazard pointer 等
- **相关**：CAS（比较并交换）、Lock-Free（无锁）

### Atomic Operation / 原子操作
- **中文**：原子操作
- **定义**：不可中断的操作，要么全部完成，要么完全不执行
- **说明**：原子操作不需要锁，效率高；现代 CPU 提供原子指令（如 x86 的 LOCK 前缀、XCHG、CMPXCHG；ARM 的 LDREX/STREX）；用于实现锁和无锁数据结构
- **相关**：CAS（比较并交换）、Memory Barrier（内存屏障）、Lock-Free（无锁）

### Barrier / 屏障
- **音标**：/ˈbæriər/
- **中文**：屏障
- **定义**：同步点，所有线程到达后才能继续执行
- **说明**：屏障用于并行算法中的阶段同步；如矩阵计算中，所有线程完成当前阶段后才能进入下一阶段
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
- **说明**：队列为空时，取元素操作阻塞；队列满时，插入操作阻塞
- **相关**：Producer-Consumer Problem（生产者-消费者问题）

### Bounded Buffer / 有界缓冲区
- **中文**：有界缓冲区
- **定义**：容量有限的缓冲区，用于生产者-消费者问题
- **说明**：有界缓冲区防止生产者无限生产；使用两个信号量：empty（空槽位数）和 full（满槽位数）
- **相关**：Buffer（缓冲区）、Producer-Consumer Problem（生产者-消费者问题）

### Broadcast / 广播
- **音标**：/ˈbrɔːdkæst/
- **中文**：广播
- **定义**：唤醒等待条件变量的所有进程
- **说明**：broadcast()/notifyAll() 唤醒所有等待进程；被唤醒的进程竞争获取锁，只有一个能继续；适合条件变化可能影响多个等待者的情况
- **同义词**：Notify All
- **相关**：Condition Variable（条件变量）、Signal（信号）

### Busy Waiting / 忙等待
- **中文**：忙等待
- **定义**：进程反复检查某个条件是否满足，而不是睡眠等待
- **说明**：忙等待浪费 CPU 时间，但延迟低；适合等待时间极短的场景；自旋锁使用忙等待
- **同义词**：Spinning、Busy Loop、Spin-wait
- **相关**：Spinlock（自旋锁）、Blocking（阻塞）

### CAS (Compare-and-Swap) / 比较并交换
- **发音**：/kæs/
- **中文**：比较并交换
- **定义**：原子操作，比较内存值与期望值，如果相等则更新为新值
- **说明**：CAS 是无锁编程的基础；如果比较失败，操作不执行，需要循环重试（自旋）；ABA 问题是 CAS 的局限性
- **同义词**：Compare-and-Set、Compare-and-Exchange
- **相关**：Atomic Operation（原子操作）、Lock-Free（无锁）

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
- **相关**：Monitor（管程）、Mutex（互斥锁）

### Consumer / 消费者
- **音标**：/kənˈsjuːmər/
- **中文**：消费者
- **定义**：从缓冲区取出数据的进程/线程
- **相关**：Producer（生产者）、Producer-Consumer Problem（生产者-消费者问题）

### Critical Section / 临界区
- **中文**：临界区
- **定义**：访问共享资源的代码段，同一时间只能有一个进程/线程执行
- **说明**：临界区必须被保护以避免竞态条件；通过互斥锁、信号量等同步机制实现；解决方案需满足互斥（Mutual Exclusion）、进展（Progress）、有限等待（Bounded Waiting）三个条件
- **相关**：Mutual Exclusion（互斥）、Race Condition（竞态条件）、Lock（锁）

### Data Race / 数据竞争
- **中文**：数据竞争
- **定义**：多个线程并发访问同一内存位置，至少一个是写操作，且没有同步的竞态条件
- **说明**：数据竞争是未定义行为的来源；C/C++ 中数据竞争导致未定义行为；Java 中影响可见性和有序性
- **相关**：Race Condition（竞态条件）、Synchronization（同步）、Memory Model（内存模型）

### Deadlock / 死锁
- **中文**：死锁
- **定义**：两个或多个进程互相等待对方持有的资源，导致所有进程都无法继续执行
- **说明**：详见 05-deadlock；四个必要条件：互斥、持有并等待、不可抢占、循环等待
- **相关**：Lock（锁）、Mutex（互斥锁）、Dining Philosophers Problem（哲学家就餐问题）

### Dining Philosophers Problem / 哲学家就餐问题
- **中文**：哲学家就餐问题
- **定义**：经典的死锁和同步问题，五位哲学家围坐餐桌，每人需要两根筷子才能就餐
- **说明**：如果所有哲学家同时拿起左边的筷子，会导致死锁；解决方案包括：限制同时就餐人数、奇偶哲学家不同顺序拿筷子、使用管程等
- **相关**：Deadlock（死锁）、Synchronization（同步）

### False Sharing / 伪共享
- **中文**：伪共享
- **定义**：不同 CPU 上的线程访问不同变量，但变量位于同一缓存行，导致缓存行频繁失效
- **说明**：伪共享严重影响多线程性能；解决方法包括填充（Padding）使变量位于不同缓存行
- **相关**：Cache Line（缓存行）、Cache Coherence（缓存一致性）

### Latch / 门闩
- **音标**：/lætʃ/
- **中文**：门闩
- **定义**：一次性使用的同步原语，一旦打开就保持打开状态
- **说明**：门闩用于等待某个事件发生后所有等待线程同时继续；与屏障不同，门闩是一次性的
- **相关**：Barrier（屏障）、Synchronization（同步）

### Linearizability / 线性一致性
- **中文**：线性一致性
- **定义**：并发对象正确性标准，每个操作看起来在调用和返回之间的某个瞬间原子执行
- **说明**：线性一致性是最强的并发正确性保证；满足线性一致性的对象行为如同顺序执行
- **相关**：Sequential Consistency（顺序一致性）、Correctness（正确性）

### Lock / 锁
- **音标**：/lɒk/
- **中文**：锁
- **定义**：用于控制对共享资源访问的同步机制
- **说明**：锁分为互斥锁（Mutex）、读写锁（Read-Write Lock）、自旋锁（Spinlock）、递归锁（Recursive Lock）等
- **相关**：Mutex（互斥锁）、Critical Section（临界区）

### Lock-Free / 无锁
- **中文**：无锁
- **定义**：不使用传统锁，通过原子操作实现同步的并发编程方式
- **说明**：无锁算法保证至少一个线程可以推进；使用 CAS、LL/SC 等原子操作；比基于锁的并发更复杂，但可以避免死锁和优先级反转
- **相关**：Atomic Operation（原子操作）、CAS（比较并交换）、Wait-Free（无等待）

### Memory Barrier / 内存屏障
- **中文**：内存屏障
- **定义**：硬件或编译器指令，强制内存操作按序执行，防止指令重排
- **说明**：内存屏障确保屏障前后的内存操作按序完成；分为读屏障、写屏障、全屏障；用于实现锁、无锁数据结构和正确的内存可见性
- **同义词**：Memory Fence、Fence
- **相关**：Atomic Operation（原子操作）、Visibility（可见性）、Memory Model（内存模型）

### Memory Model / 内存模型
- **中文**：内存模型
- **定义**：规定多线程程序中内存操作可见性和顺序的规则
- **说明**：不同语言/平台有不同内存模型：Java Memory Model (JMM)、C++ Memory Model、x86 TSO、ARM 弱内存模型等
- **相关**：Sequential Consistency（顺序一致性）、Memory Barrier（内存屏障）

### Monitor / 管程
- **音标**：/ˈmɒnɪtər/
- **中文**：管程
- **定义**：一种高级同步原语，封装共享变量和对它们的操作，提供自动互斥
- **说明**：管程由 Hoare 和 Brinch Hansen 提出；进程只能调用管程的过程访问共享数据；管程自动保证互斥；支持条件变量实现同步
- **相关**：Condition Variable（条件变量）、Mutex（互斥锁）

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

### P Operation / P 操作（Wait）
- **中文**：P 操作（等待操作）
- **定义**：信号量的等待操作
- **说明**：P 来自荷兰语"Proberen"（测试）；wait() 将信号量值减 1，如果结果 < 0，则调用者阻塞；也称为 down()、acquire()
- **同义词**：Wait Operation、Down Operation、Acquire Operation
- **相关**：V Operation（V 操作）、Semaphore（信号量）

### Parallelism / 并行
- **音标**：/ˈpærəlelɪzəm/
- **中文**：并行
- **定义**：多个任务在同一时刻真正同时执行
- **说明**：并行需要多核 CPU 或多处理器；并行是物理上的同时性；并行计算可以提高性能
- **相关**：Concurrency（并发）、Multicore（多核）

### Priority Inheritance / 优先级继承
- **中文**：优先级继承
- **定义**：低优先级进程持有高优先级进程需要的资源时，临时提升低优先级进程的优先级
- **说明**：优先级继承避免中优先级进程抢占低优先级进程，从而阻塞高优先级进程；资源释放后恢复原始优先级
- **相关**：Priority Inversion（优先级反转）

### Priority Inversion / 优先级反转
- **中文**：优先级反转
- **定义**：高优先级进程被低优先级进程阻塞，而中优先级进程在运行的现象
- **说明**：优先级反转导致高优先级进程无法及时执行；解决方案：优先级继承（Priority Inheritance）、优先级天花板（Priority Ceiling）
- **相关**：Priority Inheritance（优先级继承）、Mutex（互斥锁）

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

### Race Condition / 竞态条件
- **中文**：竞态条件
- **定义**：多个进程/线程并发访问共享数据，最终结果依赖于执行顺序的现象
- **说明**：竞态条件导致不可预测的结果和难以复现的 bug；通过同步机制（锁、信号量、原子操作）防止
- **相关**：Data Race（数据竞争）、Critical Section（临界区）、Synchronization（同步）

### Readers-Writers Problem / 读者-写者问题
- **中文**：读者-写者问题
- **定义**：经典的同步问题，多个读者可以同时读，但写者需要独占访问
- **说明**：三种变体：读者优先、写者优先、公平方案；使用信号量或读写锁解决
- **相关**：Read-Write Lock（读写锁）

### Read-Write Lock / 读写锁
- **中文**：读写锁
- **定义**：允许多个读者同时访问或一个写者独占访问的锁
- **说明**：读操作之间不互斥，读和写互斥，写和写互斥；适合读多写少的场景
- **同义词**：Shared-Exclusive Lock、RWLock
- **相关**：Mutex（互斥锁）、Readers-Writers Problem（读者-写者问题）

### Recursive Lock / 递归锁
- **中文**：递归锁
- **定义**：允许同一线程多次获取而不会死锁的锁
- **说明**：递归锁记录持有线程和递归计数；同一线程多次 lock() 增加计数，unlock() 减少计数，计数为 0 时真正释放
- **同义词**：Reentrant Lock
- **相关**：Mutex（互斥锁）、Deadlock（死锁）

### Semaphore / 信号量
- **音标**：/ˈseməfɔːr/
- **中文**：信号量
- **定义**：用于控制多个线程访问共享资源的计数器同步机制
- **说明**：信号量由 Dijkstra 提出；wait(P) 减少计数器，为负时阻塞；signal(V) 增加计数器，唤醒等待线程；分为二进制信号量和计数信号量
- **相关**：P Operation（P 操作）、V Operation（V 操作）、Mutex（互斥锁）

### Sequential Consistency / 顺序一致性
- **中文**：顺序一致性
- **定义**：最强的内存模型，所有线程看到的内存操作顺序一致
- **说明**：顺序一致性是最直观的模型，但性能差；现代 CPU 通常提供较弱的内存模型
- **相关**：Memory Model（内存模型）、Linearizability（线性一致性）

### Sleep / 睡眠
- **音标**：/sliːp/
- **中文**：睡眠
- **定义**：进程主动放弃 CPU 并进入等待状态一段时间
- **说明**：sleep() 使进程暂停执行指定时间；睡眠时间到后进程变为就绪；与忙等待不同，睡眠不消耗 CPU
- **相关**：Wake Up（唤醒）、Blocking（阻塞）

### Spinlock / 自旋锁
- **发音**：/ˈspɪn-lɒk/
- **中文**：自旋锁
- **定义**：获取锁失败时循环等待（自旋）而不是阻塞的锁
- **说明**：自旋锁适合保护极短的临界区（多处理器上）；自旋期间 CPU 忙等待，不切换上下文；内核中常用
- **相关**：Mutex（互斥锁）、Busy Waiting（忙等待）

### Synchronization / 同步
- **音标**：/ˌsɪŋkrənaɪˈzeɪʃn/
- **中文**：同步
- **定义**：协调多个进程/线程的执行顺序，使它们按一定规则协作
- **说明**：同步确保共享资源的有序访问和事件的有序发生；分为互斥（Mutual Exclusion）和条件同步（Condition Synchronization）
- **相关**：Mutual Exclusion（互斥）、Concurrency（并发）、Race Condition（竞态条件）

### Test-and-Set / 测试并设置
- **中文**：测试并设置
- **定义**：原子操作，读取内存值并将其设置为 1
- **说明**：Test-and-Set 用于实现自旋锁；虽然简单但可能导致饥饿
- **相关**：Atomic Operation（原子操作）、Spinlock（自旋锁）

### Thundering Herd Problem / 惊群问题
- **中文**：惊群问题
- **定义**：多个进程/线程等待同一事件，事件发生时所有等待者被唤醒，但只有一个能成功处理
- **说明**：惊群导致大量不必要的上下文切换和竞争；解决方案：使用互斥锁保护条件检查
- **相关**：Condition Variable（条件变量）、Mutex（互斥锁）

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
- **说明**：没有同步的情况下，一个线程的修改可能对其他线程不可见（缓存、寄存器优化）；锁和内存屏障保证可见性
- **相关**：Memory Model（内存模型）、Memory Barrier（内存屏障）

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
- **说明**：sched_yield() 将当前进程放到同优先级队列末尾；让出 CPU 给其他同优先级进程
- **相关**：Sleep（睡眠）、Blocking（阻塞）
