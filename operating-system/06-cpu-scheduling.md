# 06. CPU 调度 (CPU Scheduling)

### Aging / 老化
- **音标**：/ˈeɪdʒɪŋ/
- **中文**：老化
- **定义**：逐渐增加等待时间长的进程的优先级，防止饥饿
- **说明**：老化确保低优先级进程最终能获得 CPU；如每等待一定时间，优先级加 1
- **相关**：Priority Scheduling（优先级调度）、Starvation（饥饿）

### Completely Fair Scheduler (CFS) / 完全公平调度器
- **中文**：完全公平调度器
- **定义**：Linux 的默认 CPU 调度器（自 2.6.23 起）
- **说明**：CFS 使用红黑树管理可运行进程，目标是让每个进程获得公平的 CPU 时间份额；基于虚拟运行时间（vruntime）调度
- **相关**：Red-Black Tree（红黑树）、vruntime（虚拟运行时间）、Linux

### Context Switch Overhead / 上下文切换开销
- **中文**：上下文切换开销
- **定义**：上下文切换消耗的时间和资源
- **说明**：上下文切换需要保存/恢复进程状态，刷新 TLB 和缓存；频繁的上下文切换浪费 CPU 时间
- **相关**：Context Switch（上下文切换）、Cache（高速缓存）

### Cooperative Scheduling / 协作调度
- **中文**：协作调度
- **定义**：依赖进程主动放弃 CPU 的调度方式
- **说明**：协作调度中进程通过 yield() 主动让出 CPU；Windows 3.x、Mac OS 9 使用协作调度；实现简单但一个进程不释放 CPU 会卡住系统
- **相关**：Preemptive Scheduling（抢占式调度）、yield()

### CPU Scheduling / CPU 调度
- **中文**：CPU 调度
- **定义**：操作系统从就绪队列中选择一个进程并分配 CPU 的过程
- **说明**：CPU 调度是多道程序操作系统的基础；调度程序（Scheduler）决定哪个进程获得 CPU；调度频率很高（毫秒级）
- **相关**：Scheduler（调度器）、Dispatcher（分派程序）、Scheduling Algorithm（调度算法）

### CPU Utilization / CPU 利用率
- **中文**：CPU 利用率
- **定义**：CPU 处于忙碌状态的时间比例
- **说明**：理想的 CPU 利用率应尽可能高（接近 100%）；但过度追求利用率可能导致响应时间变差
- **相关**：Scheduling Criteria（调度准则）、Throughput（吞吐量）

### CPU-Bound / CPU 密集型
- **中文**：CPU 密集型
- **定义**：进程主要进行计算，使用大量 CPU 时间的特性
- **说明**：CPU 密集型进程有较长的 CPU 突发时间；科学计算、视频编码等属于 CPU 密集型
- **相关**：I/O-Bound（I/O 密集型）、Burst Time（突发时间）

### Deadline / 截止时间
- **音标**：/ˈdedlaɪn/
- **中文**：截止时间
- **定义**：任务必须完成的最后时间
- **说明**：实时系统中，错过截止时间可能导致严重后果（硬实时）或性能下降（软实时）
- **相关**：Real-Time Scheduling（实时调度）、Period（周期）

### Dispatch Latency / 分派延迟
- **中文**：分派延迟
- **定义**：分派程序停止一个进程并开始另一个进程所需的时间
- **说明**：分派延迟包括保存上下文、恢复上下文、切换到用户态的时间；典型值为 1-1000 微秒
- **相关**：Dispatcher（分派程序）、Context Switch（上下文切换）

### Dynamic Priority / 动态优先级
- **中文**：动态优先级
- **定义**：根据进程行为动态调整的优先级
- **说明**：如 I/O 密集型进程提高优先级（鼓励释放 CPU），CPU 密集型进程降低优先级；Linux CFS 使用动态优先级
- **相关**：Static Priority（静态优先级）、Priority Scheduling（优先级调度）

### Earliest-Deadline-First (EDF) / 最早截止时间优先
- **中文**：最早截止时间优先
- **定义**：动态优先级实时调度算法，截止时间最早的任务优先级最高
- **说明**：EDF 是最优的动态优先级实时调度算法；CPU 利用率上限为 100%；但实现比 RMS 复杂
- **相关**：Rate-Monotonic Scheduling（速率单调调度）、Real-Time Scheduling（实时调度）

### Fairness / 公平性
- **音标**：/ˈfeərnəs/
- **中文**：公平性
- **定义**：每个进程获得合理的 CPU 时间份额
- **说明**：公平性确保没有进程被饿死（Starvation）；但公平性可能与效率冲突
- **相关**：Starvation（饥饿）、Scheduling Criteria（调度准则）

### First-Come-First-Served (FCFS) / 先来先服务
- **中文**：先来先服务
- **定义**：按进程到达顺序分配 CPU 的调度算法
- **说明**：FCFS 实现简单（使用 FIFO 队列），但平均等待时间可能很长；护航效应（Convoy Effect）严重
- **相关**：Convoy Effect（护航效应）、FIFO、Scheduling Algorithm（调度算法）

### Involuntary Context Switch / 非自愿上下文切换
- **中文**：非自愿上下文切换
- **定义**：进程被操作系统强制抢占导致的上下文切换
- **说明**：非自愿切换通常因为时间片到期或有更高优先级进程就绪；过多的非自愿切换表示系统负载高或竞争激烈
- **相关**：Voluntary Context Switch（自愿上下文切换）、Preemption（抢占）

### Load Balancing / 负载均衡
- **中文**：负载均衡
- **定义**：在多处理器系统中，将进程均匀分布到各个 CPU 的调度策略
- **说明**：Linux CFS 在每个 CPU 维护一个可运行队列，定期从负载重的 CPU 迁移进程到负载轻的 CPU
- **相关**：Multiprocessor Scheduling（多处理器调度）、CPU Affinity（CPU 亲和性）

### Multilevel Feedback Queue / 多级反馈队列
- **中文**：多级反馈队列
- **定义**：允许进程在队列之间移动的多级队列调度
- **说明**：I/O 密集型/交互式进程在高优先级队列（短时间片），CPU 密集型进程在低优先级队列（长时间片）；进程用完时间片降到下级队列；I/O 阻塞后升到上级队列
- **相关**：Multilevel Queue（多级队列）、Priority Scheduling（优先级调度）

### Multilevel Queue / 多级队列
- **中文**：多级队列
- **定义**：将就绪队列分为多个优先级不同的子队列，每个队列使用不同调度算法
- **说明**：如系统进程队列（优先级高，使用 RR）、交互进程队列（使用 RR）、批处理进程队列（使用 FCFS）；队列间通常使用固定优先级调度
- **相关**：Multilevel Feedback Queue（多级反馈队列）、Priority Scheduling（优先级调度）

### Multiprocessor Scheduling / 多处理器调度
- **中文**：多处理器调度
- **定义**：多 CPU/多核系统中的进程调度
- **说明**：多处理器调度需要考虑负载均衡、缓存亲和性、迁移开销等问题；分为对称多处理（SMP）调度和非对称多处理（AMP）调度
- **相关**：SMP（对称多处理）、Load Balancing（负载均衡）、CPU Affinity（CPU 亲和性）

### Period / 周期
- **音标**：/ˈpɪəriəd/
- **中文**：周期
- **定义**：周期性任务重复执行的时间间隔
- **说明**：周期任务每周期执行一次，必须在下一个周期开始前完成；如控制任务每 10ms 执行一次
- **相关**：Real-Time Scheduling（实时调度）、Deadline（截止时间）

### Preemptive SJF / 抢占式最短作业优先
- **中文**：抢占式最短作业优先
- **定义**：新进程到达时，如果其运行时间比当前进程剩余时间短，则抢占 CPU
- **说明**：也称为 Shortest-Remaining-Time-First (SRTF)；响应性更好，但上下文切换更频繁
- **同义词**：Shortest-Remaining-Time-First (SRTF)
- **相关**：SJF（最短作业优先）、Preemptive Scheduling（抢占式调度）

### Priority / 优先级
- **音标**：/praɪˈɒrəti/
- **中文**：优先级
- **定义**：表示进程重要性的数值，用于调度决策
- **说明**：优先级数值可以是数字越小优先级越高（如 Unix，0 最高），或数字越大优先级越高（如 Windows）；分为静态优先级和动态优先级
- **相关**：Priority Scheduling（优先级调度）、Nice Value（Nice 值）

### Priority Scheduling / 优先级调度
- **中文**：优先级调度
- **定义**：根据进程优先级分配 CPU，优先级高的先执行
- **说明**：优先级可以是静态（固定）或动态（根据行为调整）；低优先级进程可能饥饿；可以通过老化（Aging）解决
- **相关**：Priority（优先级）、Aging（老化）、Starvation（饥饿）

### Quantum Expiration / 时间片到期
- **中文**：时间片到期
- **定义**：进程的时间片用完，触发抢占
- **说明**：时间片到期后，进程被放入就绪队列末尾，调度器选择下一个进程；定时器中断触发时间片到期
- **相关**：Time Quantum（时间量子）、Round Robin（时间片轮转）、Preemption（抢占）

### Rate-Monotonic Scheduling (RMS) / 速率单调调度
- **中文**：速率单调调度
- **定义**：静态优先级实时调度算法，周期短的任务优先级高
- **说明**：RMS 是最优的静态优先级实时调度算法；如果任务集可以被任何静态优先级算法调度，RMS 也可以调度；CPU 利用率上限为 ln(2) ≈ 69.3%
- **相关**：Earliest Deadline First（最早截止时间优先）、Real-Time Scheduling（实时调度）

### Real-Time Scheduling / 实时调度
- **中文**：实时调度
- **定义**：满足截止时间（Deadline）要求的调度
- **说明**：实时调度分为硬实时（必须满足截止时间）和软实时（尽量满足截止时间）；需要知道任务的执行时间和截止时间
- **相关**：Deadline（截止时间）、Hard Real-Time（硬实时）、Soft Real-Time（软实时）

### Response Time Analysis / 响应时间分析
- **中文**：响应时间分析
- **定义**：计算实时任务最坏响应时间的方法
- **说明**：响应时间 = 任务执行时间 + 高优先级任务干扰时间；如果响应时间 ≤ 截止时间，则任务可调度
- **相关**：Schedulability Test（可调度性测试）、Real-Time Scheduling（实时调度）

### Round Robin (RR) / 时间片轮转
- **中文**：时间片轮转
- **定义**：每个进程分配一个固定时间片，时间片用完则排到就绪队列末尾
- **说明**：RR 是抢占式调度；时间片大小很重要：太大退化为 FCFS，太小上下文切换开销大；通常 10-100ms
- **相关**：Time Quantum（时间片）、Time Slice（时间片）、FCFS

### Schedulability Test / 可调度性测试
- **中文**：可调度性测试
- **定义**：判断一组实时任务是否可以被调度的测试
- **说明**：RMS 的可调度性测试：CPU 利用率 ≤ n(2^(1/n)-1)（充分条件）或计算响应时间；EDF 的可调度性测试：CPU 利用率 ≤ 1（充要条件）
- **相关**：Real-Time Scheduling（实时调度）、Rate-Monotonic Scheduling（速率单调调度）

### Scheduler / 调度器
- **音标**：/ˈskedʒuːlər/
- **中文**：调度器
- **定义**：操作系统中负责决定进程执行顺序的组件
- **说明**：调度器分为长期调度器（Long-term Scheduler）、中期调度器（Medium-term Scheduler）、短期调度器（Short-term Scheduler）
- **相关**：CPU Scheduling（CPU 调度）、Dispatcher（分派程序）

### Scheduling Algorithm / 调度算法
- **中文**：调度算法
- **定义**：决定进程执行顺序的规则或策略
- **说明**：调度算法分为非抢占式（Non-preemptive）和抢占式（Preemptive）
- **相关**：Preemptive Scheduling（抢占式调度）、Non-preemptive Scheduling（非抢占式调度）

### Scheduling Criteria / 调度准则
- **中文**：调度准则
- **定义**：评价调度算法性能的标准
- **说明**：常用准则包括：CPU 利用率、吞吐量、周转时间、等待时间、响应时间、公平性
- **相关**：CPU Utilization（CPU 利用率）、Throughput（吞吐量）、Turnaround Time（周转时间）

### Scheduling Policy / 调度策略
- **中文**：调度策略
- **定义**：操作系统采用的调度规则和参数设置
- **说明**：调度策略决定了系统的响应性、吞吐量、公平性等特性；不同场景（桌面、服务器、嵌入式）需要不同策略
- **相关**：Scheduling Algorithm（调度算法）、Scheduler（调度器）

### Short-Term Scheduler / 短期调度器
- **中文**：短期调度器（CPU 调度器）
- **定义**：决定哪个就绪进程获得 CPU 的调度器
- **说明**：短期调度器执行频率最高（毫秒级），需要非常快；是操作系统最核心的调度器
- **同义词**：CPU Scheduler（CPU 调度器）
- **相关**：Dispatcher（分派程序）、Scheduling Algorithm（调度算法）

### Shortest-Job-First (SJF) / 最短作业优先
- **中文**：最短作业优先
- **定义**：优先执行预计运行时间最短的进程
- **说明**：SJF 最小化平均等待时间；但可能导致长进程饥饿；需要预知或估计进程的运行时间
- **同义词**：Shortest Process Next (SPN)
- **相关**：FCFS、Preemptive SJF（抢占式最短作业优先）、Starvation（饥饿）

### Shortest-Remaining-Time-First (SRTF) / 最短剩余时间优先
- **中文**：最短剩余时间优先
- **定义**：同 Preemptive SJF
- **相关**：Preemptive SJF（抢占式最短作业优先）

### SMP (Symmetric Multiprocessing) / 对称多处理
- **中文**：对称多处理
- **定义**：所有处理器对等，共享同一内存和 I/O 的多处理器架构
- **说明**：SMP 中任何处理器都可以运行任何进程；操作系统可以在任意处理器上调度进程；现代多核 CPU 使用 SMP
- **相关**：Multiprocessor Scheduling（多处理器调度）、NUMA（非统一内存访问）

### Starvation / 饥饿
- **中文**：饥饿
- **定义**：进程长时间无法获得所需资源而无法推进的状态
- **说明**：饥饿与死锁不同，饥饿的进程可能最终获得资源；优先级调度中低优先级进程容易饥饿
- **相关**：Aging（老化）、Priority Scheduling（优先级调度）、Deadlock（死锁）

### Static Priority / 静态优先级
- **中文**：静态优先级
- **定义**：进程创建时确定且不变的优先级
- **说明**：静态优先级实现简单但不灵活；无法适应进程行为变化
- **相关**：Dynamic Priority（动态优先级）、Priority Scheduling（优先级调度）

### Thread Affinity / 线程亲和性
- **中文**：线程亲和性
- **定义**：将线程绑定到特定 CPU 核心
- **说明**：线程亲和性确保线程总是在同一核心上运行，提高缓存命中率；在实时系统和 HPC 中常用
- **相关**：CPU Affinity（CPU 亲和性）、Thread（线程）

### Timer Interrupt / 定时器中断
- **中文**：定时器中断
- **定义**：定时器硬件周期性产生的中断，用于时间片到期和计时
- **说明**：定时器中断频率（如 100Hz、250Hz、1000Hz）决定时间片粒度；高频率提高响应性但增加开销
- **相关**：Time Quantum（时间量子）、Preemption（抢占）、Interrupt（中断）

### Voluntary Context Switch / 自愿上下文切换
- **中文**：自愿上下文切换
- **定义**：进程主动放弃 CPU 导致的上下文切换
- **说明**：进程因 I/O 请求、等待信号量、调用 sleep/yield 等主动放弃 CPU；自愿切换是正常且必要的
- **相关**：Involuntary Context Switch（非自愿上下文切换）、Context Switch（上下文切换）
