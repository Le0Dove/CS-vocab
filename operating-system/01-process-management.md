# 01. 进程管理 (Process Management)

## 基础概念

### Context / 上下文
- **中文**：上下文
- **定义**：进程执行时的环境信息，包括寄存器值、程序计数器、内存状态等
- **说明**：上下文切换时，当前进程的上下文被保存到 PCB 中，新进程的上下文从 PCB 恢复
- **相关**：Context Switch（上下文切换）、Process State（进程状态）

### Context Switch / 上下文切换
- **中文**：上下文切换
- **定义**：CPU 从一个进程切换到另一个进程时保存和恢复进程状态的过程
- **说明**：上下文切换需要保存/恢复程序计数器、寄存器、内存映射等；频繁的上下文切换会带来性能开销
- **相关**：Process State（进程状态）、CPU Scheduler（CPU 调度器）、Overhead（开销）

### Process / 进程
- **音标**：/ˈprɑːses/
- **中文**：进程
- **定义**：程序的一次执行过程，是系统进行资源分配和调度的基本单位
- **说明**：进程是动态的，包含程序计数器、寄存器、变量等状态信息；每个进程拥有独立的地址空间
- **相关**：Program（程序）、Thread（线程）、Process Control Block（进程控制块）
- **例句**：The operating system creates a new process by fork-ing an existing one.

### Process Control Block (PCB) / 进程控制块
- **中文**：进程控制块
- **定义**：操作系统内核中用于描述和控制进程的数据结构
- **说明**：PCB 包含进程状态、程序计数器、CPU 寄存器、内存管理信息、记账信息、I/O 状态等；是进程存在的唯一标志
- **相关**：Task Control Block（任务控制块）、Process Descriptor（进程描述符）
- **同义词**：Task Control Block (TCB)、Process Descriptor

### Process Identifier (PID) / 进程标识符
- **中文**：进程标识符
- **定义**：操作系统分配给每个进程的唯一整数标识
- **说明**：PID 用于系统调用和命令中引用特定进程；init 进程的 PID 通常为 1
- **相关**：PPID（父进程标识符）、PGID（进程组标识符）、SID（会话标识符）

### Process State / 进程状态
- **中文**：进程状态
- **定义**：进程在其生命周期中所处的不同状态
- **说明**：操作系统通常定义三种基本状态：就绪（Ready）、运行（Running）、阻塞（Blocked/Waiting）

### Thread / 线程
- **音标**：/θred/
- **中文**：线程
- **定义**：进程中的一个执行流，是 CPU 调度的基本单位
- **说明**：同一进程内的线程共享地址空间、打开的文件等资源，但拥有独立的栈、寄存器和程序计数器
- **相关**：Process（进程）、Multithreading（多线程）、Lightweight Process（轻量级进程）
- **例句**：A process can have multiple threads executing concurrently.

---

## 进程间通信 (IPC)

### Critical Section / 临界区
- **中文**：临界区
- **定义**：访问共享资源的代码段，同一时刻只能有一个线程执行
- **说明**：进入临界区前需要获取锁，离开临界区后释放锁
- **相关**：Mutual Exclusion（互斥）、Lock（锁）、Semaphore（信号量）

### Inter-Process Communication (IPC) / 进程间通信
- **中文**：进程间通信
- **定义**：操作系统提供的允许进程之间交换数据和同步执行的机制
- **说明**：IPC 机制包括管道、消息队列、共享内存、信号量、套接字等
- **相关**：Pipe（管道）、Message Queue（消息队列）、Shared Memory（共享内存）、Socket（套接字）

### Message Queue / 消息队列
- **中文**：消息队列
- **定义**：一种允许进程以消息为单位进行异步通信的 IPC 机制
- **说明**：消息是有格式的数据块，包含类型和正文；支持消息的优先级和选择接收
- **相关**：Queue（队列）、Mailbox（邮箱）、Asynchronous Communication（异步通信）

### Pipe / 管道
- **音标**：/paɪp/
- **中文**：管道
- **定义**：一种单向的、基于字节流的 IPC 机制
- **说明**：管道是半双工的，数据只能单向流动；匿名管道用于父子进程间通信；命名管道（Named Pipe/FIFO）可用于无关进程间通信
- **相关**：FIFO、Named Pipe（命名管道）、Pipeline（管道线）

### Race Condition / 竞态条件
- **中文**：竞态条件
- **定义**：多个线程/进程访问共享数据，最终结果依赖于执行顺序的缺陷
- **说明**：竞态条件会导致不可预测的行为和数据不一致；需要通过同步机制避免
- **相关**：Critical Section（临界区）、Mutual Exclusion（互斥）、Synchronization（同步）

### Shared Memory / 共享内存
- **中文**：共享内存
- **定义**：允许多个进程访问同一块物理内存区域的 IPC 机制
- **说明**：是最快的 IPC 方式，因为避免了数据拷贝；需要配合信号量或互斥锁进行同步
- **相关**：Memory Mapping（内存映射）、Semaphore（信号量）、Mutual Exclusion（互斥）

### Signal / 信号
- **音标**：/ˈsɪɡnəl/
- **中文**：信号
- **定义**：一种异步的进程间通信机制，用于通知进程发生了某个事件
- **说明**：信号是软件中断；常见信号包括 SIGINT（中断）、SIGTERM（终止）、SIGKILL（强制终止）、SIGSEGV（段错误）
- **相关**：Interrupt（中断）、Signal Handler（信号处理函数）、Asynchronous（异步）

### Socket / 套接字
- **音标**：/ˈsɑːkɪt/
- **中文**：套接字
- **定义**：网络通信的端点，可用于同一台或不同计算机上的进程间通信
- **说明**：套接字支持 TCP（面向连接）和 UDP（无连接）协议；是网络编程的基础
- **相关**：Port（端口）、IP Address（IP 地址）、Network Protocol（网络协议）

---

## 进程关系

### Background Process / 后台进程
- **中文**：后台进程
- **定义**：不与用户终端交互，在后台执行的进程
- **说明**：用户可以在前台继续工作；通常通过 & 符号在 Shell 中启动
- **相关**：Foreground Process（前台进程）、Daemon（守护进程）

### Child Process / 子进程
- **中文**：子进程
- **定义**：由父进程通过 fork() 创建的进程
- **说明**：子进程继承父进程的部分属性，但拥有独立的 PID；子进程终止时向父进程发送 SIGCHLD 信号
- **相关**：Parent Process（父进程）、Orphan Process（孤儿进程）

### Daemon / 守护进程
- **音标**：/ˈdiːmən/
- **中文**：守护进程
- **定义**：在后台运行的系统服务进程，通常在系统启动时启动
- **说明**：守护进程没有控制终端，独立于用户会话运行；如 httpd、sshd、cron 等
- **相关**：Background Process（后台进程）、Service（服务）
- **例句**：The print spooler runs as a daemon in the background.

### Foreground Process / 前台进程
- **中文**：前台进程
- **定义**：与用户终端交互，控制终端的进程
- **说明**：前台进程接收用户的键盘输入，输出显示在终端上
- **相关**：Background Process（后台进程）

### Orphan Process / 孤儿进程
- **中文**：孤儿进程
- **定义**：父进程已终止但自身仍在运行的进程
- **说明**：孤儿进程会被 init 进程（PID 1）收养，由 init 进程负责回收
- **相关**：Zombie Process（僵尸进程）、Init Process（初始化进程）

### Parent Process / 父进程
- **中文**：父进程
- **定义**：通过 fork() 创建其他进程（子进程）的进程
- **说明**：父进程通常需要等待子进程结束并收集其退出状态
- **相关**：Child Process（子进程）、Process Tree（进程树）

### Zombie Process / 僵尸进程
- **中文**：僵尸进程
- **定义**：已终止但其父进程尚未读取其退出状态的进程
- **说明**：僵尸进程占用 PCB 资源但不占用内存；如果父进程不处理，会导致资源泄漏
- **相关**：Orphan Process（孤儿进程）、Wait System Call（等待系统调用）

---

## 进程操作

### Exec / 执行（exec）
- **音标**：/ɪɡˈzek/
- **中文**：执行（exec）
- **定义**：用于在当前进程上下文中加载并执行新程序的系统调用族
- **说明**：exec 不创建新进程，而是用新程序替换当前进程的地址空间；包括 execl、execv、execle、execve 等变体
- **相关**：Fork（创建）、Spawn（生成）
- **例句**：After fork(), the child process typically calls exec() to run a new program.

### Exit / 退出
- **音标**：/ˈeksɪt/
- **中文**：退出
- **定义**：进程终止执行并返回退出状态给操作系统
- **说明**：进程可以调用 exit() 正常终止，或被信号异常终止；退出状态码 0 通常表示成功
- **相关**：Terminate（终止）、Abort（中止）、Kill（杀死）

### Fork / 创建（fork）
- **音标**：/fɔːrk/
- **中文**：创建（fork）
- **定义**：Unix/Linux 系统中用于创建新进程的系统调用
- **说明**：fork() 创建调用进程的副本（子进程）；子进程获得父进程数据空间的副本；采用写时复制（Copy-on-Write）优化
- **相关**：Clone（克隆）、Exec（执行）、Wait（等待）
- **例句**：The parent process calls fork() to create a child process.

### Interrupt / 中断
- **音标**：/ˈɪntərʌpt/
- **中文**：中断
- **定义**：硬件或软件发出的异步信号，用于通知 CPU 需要立即处理某个事件
- **说明**：中断发生后，CPU 暂停当前执行，转而执行中断处理程序；中断处理完成后恢复执行
- **相关**：Interrupt Handler（中断处理程序）、IRQ（中断请求）、Trap（陷入）

### Kill / 杀死
- **音标**：/kɪl/
- **中文**：杀死
- **定义**：向进程发送信号以终止其执行
- **说明**：kill 命令/系统调用可以发送各种信号，SIGKILL（信号 9）强制终止进程，不可捕获
- **相关**：Signal（信号）、SIGKILL、SIGTERM

### System Call / 系统调用
- **中文**：系统调用
- **定义**：用户程序请求操作系统内核提供服务的接口
- **说明**：系统调用是用户态进入内核态的唯一受控方式；如 fork、exec、read、write、open 等
- **相关**：API、Kernel Mode（内核态）、Trap（陷入）

### Wait / 等待
- **音标**：/weɪt/
- **中文**：等待
- **定义**：父进程等待子进程终止并收集其退出状态的系统调用
- **说明**：wait() 阻塞直到任意子进程结束；waitpid() 可以等待特定子进程
- **相关**：Exit（退出）、Zombie Process（僵尸进程）

---

## 进程状态

### Blocked / 阻塞
- **音标**：/blɒkt/
- **中文**：阻塞状态（等待状态）
- **定义**：进程因等待某个事件（如 I/O 完成、信号量）而暂停执行
- **说明**：即使 CPU 空闲，阻塞进程也不能执行；事件发生后转为就绪状态
- **同义词**：Waiting State、Wait State
- **相关**：I/O Wait（I/O 等待）、Sleep（睡眠）

### Kernel Mode / 内核态
- **中文**：内核态
- **定义**：CPU 执行操作系统内核代码的特权模式
- **说明**：内核态可以执行所有指令、访问所有内存和硬件；用户程序通过系统调用进入内核态
- **同义词**：System Mode、Privileged Mode、Supervisor Mode
- **相关**：User Mode（用户态）、System Call（系统调用）、Privilege Level（特权级）

### Ready / 就绪
- **中文**：就绪状态
- **定义**：进程已准备好执行，等待 CPU 调度
- **说明**：进程拥有除 CPU 外的所有必要资源；多个就绪进程组成就绪队列（Ready Queue）
- **相关**：Ready Queue（就绪队列）、Scheduler（调度器）

### Running / 运行
- **中文**：运行状态
- **定义**：进程正在 CPU 上执行指令
- **说明**：单核 CPU 上只有一个进程处于运行状态；多核 CPU 上可以有多个进程同时运行
- **相关**：Time Slice（时间片）、Context Switch（上下文切换）

### User Mode / 用户态
- **中文**：用户态
- **定义**：CPU 执行用户程序代码的非特权模式
- **说明**：用户态不能执行特权指令或直接访问硬件；用户程序在用户态运行以保证系统安全
- **相关**：Kernel Mode（内核态）、System Call（系统调用）

---

## 进程调度相关

### Convoy Effect / 护航效应
- **中文**：护航效应
- **定义**：非抢占式调度中，短进程等待长进程释放 CPU 的现象
- **说明**：类似车队中慢车拖慢整个车队；导致平均等待时间增加
- **相关**：Non-preemptive Scheduling（非抢占式调度）、FCFS（先来先服务）

### Non-preemptive Scheduling / 非抢占式调度
- **中文**：非抢占式调度
- **定义**：一旦进程获得 CPU，就会一直运行直到主动放弃或终止的调度方式
- **说明**：实现简单，上下文切换少；但可能导致短进程等待长进程（护航效应）
- **相关**：Preemptive Scheduling（抢占式调度）、Convoy Effect（护航效应）

### Preemption / 抢占
- **音标**：/prɪˈempʃn/
- **中文**：抢占
- **定义**：操作系统强制收回当前进程的 CPU 使用权并分配给其他进程
- **说明**：抢占式调度允许更高优先级进程中断低优先级进程；非抢占式调度则不允许
- **相关**：Preemptive Scheduling（抢占式调度）、Non-preemptive Scheduling（非抢占式调度）

### Preemptive Scheduling / 抢占式调度
- **中文**：抢占式调度
- **定义**：允许操作系统中断正在运行的进程并将 CPU 分配给其他进程的调度方式
- **说明**：响应性好，适合交互式系统；但上下文切换开销较大
- **相关**：Non-preemptive Scheduling（非抢占式调度）、Preemption（抢占）

### Response Time / 响应时间
- **中文**：响应时间
- **定义**：从提交请求到系统首次响应的时间
- **说明**：对于交互式系统很重要；响应时间快意味着用户体验好
- **相关**：Turnaround Time（周转时间）、Waiting Time（等待时间）

### Throughput / 吞吐量
- **音标**：/ˈθruːpʊt/
- **中文**：吞吐量
- **定义**：单位时间内系统完成的作业数量
- **说明**：是衡量系统性能的重要指标；受 CPU 速度、I/O 效率、调度算法等影响
- **相关**：Turnaround Time（周转时间）、Waiting Time（等待时间）、Response Time（响应时间）

### Time Slice / 时间片
- **中文**：时间片
- **定义**：分时系统中分配给每个进程的 CPU 时间单位
- **说明**：时间片用完，进程被抢占并放回就绪队列；时间片大小影响系统响应性和吞吐量
- **同义词**：Time Quantum、Quantum
- **相关**：Round Robin（轮转调度）、Preemption（抢占）

### Turnaround Time / 周转时间
- **中文**：周转时间
- **定义**：从作业提交到作业完成的时间间隔
- **说明**：周转时间 = 等待时间 + 执行时间 + I/O 时间；是衡量批处理系统性能的重要指标
- **相关**：Waiting Time（等待时间）、Burst Time（突发时间）

### Waiting Time / 等待时间
- **中文**：等待时间
- **定义**：进程在就绪队列中等待 CPU 的总时间
- **说明**：等待时间不包括 I/O 等待时间；调度算法的目标之一是减少平均等待时间
- **相关**：Turnaround Time（周转时间）、Response Time（响应时间）

---

## 线程相关

### Multithreading / 多线程
- **中文**：多线程
- **定义**：在一个进程内同时运行多个线程的技术
- **说明**：多线程可以提高程序的并发性和响应性；线程共享进程的地址空间，切换开销小于进程
- **相关**：Thread（线程）、Concurrency（并发）、Parallelism（并行）

### Thread-Safe / 线程安全
- **中文**：线程安全
- **定义**：代码在多线程环境下正确执行，不会出现数据竞争或不一致
- **说明**：线程安全通常通过同步机制（锁、原子操作）实现
- **相关**：Reentrant（可重入）、Race Condition（竞态条件）
