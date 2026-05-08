# 02. 内存管理 (Memory Management)

### Address Space / 地址空间
- **中文**：地址空间
- **定义**：进程可以访问的内存地址集合
- **说明**：每个进程拥有独立的虚拟地址空间，由操作系统映射到物理内存；地址空间大小取决于架构（32 位为 4GB，64 位为极大）
- **相关**：Virtual Address（虚拟地址）、Physical Address（物理地址）、Memory Mapping（内存映射）

### Base Register / 基址寄存器
- **中文**：基址寄存器
- **定义**：存储进程在物理内存中起始地址的寄存器
- **说明**：物理地址 = 逻辑地址 + 基址寄存器值；与限长寄存器配合实现内存保护
- **相关**：Limit Register（限长寄存器）、Relocation（重定位）

### Belady's Anomaly / Belady 异常
- **中文**：Belady 异常
- **定义**：某些页面置换算法（如 FIFO）在增加分配的页框数时反而增加页错误数的现象
- **说明**：LRU 和最优算法不会出现 Belady 异常；Belady 异常揭示了算法的栈特性缺失
- **相关**：FIFO（先进先出）、Page Replacement（页面置换）

### Best Fit / 最佳适应
- **中文**：最佳适应
- **定义**：内存分配算法，选择能满足要求的最小空闲块
- **说明**：减少空间浪费，但会产生大量微小碎片；查找速度较慢
- **相关**：First Fit（首次适应）、Worst Fit（最坏适应）

### BSS Segment / BSS 段
- **中文**：BSS 段
- **定义**：存储未初始化的全局变量和静态变量的内存区域
- **说明**：BSS（Block Started by Symbol）段在程序加载时由操作系统清零；不占用可执行文件空间
- **相关**：Data Segment（数据段）、Text Segment（代码段）

### Buffer Overflow / 缓冲区溢出
- **中文**：缓冲区溢出
- **定义**：向缓冲区写入超过其容量的数据，导致相邻内存被覆盖
- **说明**：缓冲区溢出是常见的安全漏洞，可以被利用执行恶意代码；通过边界检查、栈保护（Stack Canaries）等防范
- **相关**：Stack（栈）、Heap（堆）、Security（安全）

### Clock Algorithm / 时钟算法（第二次机会算法）
- **中文**：时钟算法（第二次机会算法）
- **定义**：使用访问位（Reference Bit）近似 LRU 的页面置换算法
- **说明**：页框组织成环形队列，指针顺时针移动；遇到访问位为 1 的页，清零并跳过；遇到访问位为 0 的页，置换该页
- **同义词**：Second-Chance Algorithm、NRU (Not Recently Used)
- **相关**：LRU（最近最少使用）、Reference Bit（访问位）

### Compaction / 紧缩
- **音标**：/kəmˈpækʃn/
- **中文**：紧缩（紧凑、压缩）
- **定义**：移动内存中的进程，使所有空闲内存合并为一块连续区域
- **说明**：紧缩只在运行时绑定（Run-time Binding）下可行；需要重定位寄存器支持
- **相关**：External Fragmentation（外部碎片）、Relocation（重定位）

### Contiguous Allocation / 连续分配
- **中文**：连续分配
- **定义**：为每个进程分配一段连续的物理内存区域
- **说明**：简单但会产生外部碎片（External Fragmentation）；包括固定分区（Fixed Partition）和动态分区（Dynamic Partition）
- **相关**：External Fragmentation（外部碎片）、Dynamic Partition（动态分区）、First Fit（首次适应）

### Copy-on-Write (COW) / 写时复制
- **中文**：写时复制
- **定义**：推迟实际复制操作，直到某一方试图修改共享数据时才进行复制
- **说明**：fork() 时使用 COW，父子进程共享物理页，直到某一进程写操作时才复制该页；减少不必要的内存拷贝
- **相关**：Fork（创建）、Shared Memory（共享内存）、Page Table（页表）

### Data Segment / 数据段
- **中文**：数据段
- **定义**：存储已初始化的全局变量和静态变量的内存区域
- **说明**：数据段在程序加载时从可执行文件初始化；可读写
- **相关**：BSS Segment（BSS 段）、Text Segment（代码段）

### Demand Paging / 请求分页
- **中文**：请求分页
- **定义**：仅在需要时才将页加载到内存中的技术
- **说明**：程序启动时不加载所有页，只有在访问某页且该页不在内存中时（页错误）才加载；减少启动时间和内存占用
- **相关**：Lazy Loading（惰性加载）、Page Fault（页错误）、Virtual Memory（虚拟内存）

### Dirty Bit / 修改位（脏位）
- **中文**：修改位（脏位）
- **定义**：页表项中的标志位，表示该页是否被修改过
- **说明**：脏位为 1 表示页被修改过，换出时需要写回磁盘；为 0 表示未被修改，可以直接丢弃（因为磁盘上有副本）
- **同义词**：Modified Bit
- **相关**：Page Table Entry（页表项）、Page Replacement（页面置换）

### Dynamic Partition / 动态分区
- **中文**：动态分区
- **定义**：根据进程大小动态划分内存分区
- **说明**：没有内部碎片，但会产生外部碎片；需要内存紧缩（Compaction）或碎片整理
- **相关**：Fixed Partition（固定分区）、External Fragmentation（外部碎片）、Compaction（紧缩）

### External Fragmentation / 外部碎片
- **中文**：外部碎片
- **定义**：内存中存在大量不连续的小空闲块，总和足够但无法分配大进程
- **说明**：外部碎片是动态分区分配的主要问题；可以通过紧缩（Compaction）或分页解决
- **相关**：Internal Fragmentation（内部碎片）、Compaction（紧缩）、Paging（分页）

### First Fit / 首次适应
- **中文**：首次适应
- **定义**：内存分配算法，从头开始查找，选择第一个足够大的空闲块
- **说明**：实现简单、速度快；但会在内存低端留下许多小碎片
- **相关**：Best Fit（最佳适应）、Worst Fit（最坏适应）、Next Fit（下次适应）

### First-In-First-Out (FIFO) / 先进先出
- **中文**：先进先出
- **定义**：置换最早进入内存的页
- **说明**：实现简单（使用队列），但性能差；可能出现 Belady 异常（分配更多页框反而增加页错误）
- **相关**：Belady's Anomaly（Belady 异常）、Page Replacement（页面置换）

### Fixed Partition / 固定分区
- **中文**：固定分区
- **定义**：将内存预先划分为固定大小的分区，每个分区分配给一个进程
- **说明**：实现简单但会产生内部碎片（Internal Fragmentation）；分区大小需要合理设置
- **相关**：Dynamic Partition（动态分区）、Internal Fragmentation（内部碎片）

### Frame / 页框
- **音标**：/freɪm/
- **中文**：页框（页帧、物理页）
- **定义**：物理内存中的固定大小块，与页大小相同
- **说明**：页可以映射到任意空闲页框；页框号是物理地址的高位部分
- **同义词**：Page Frame、Physical Page
- **相关**：Page（页）、Page Table（页表）

### Garbage Collection (GC) / 垃圾回收
- **中文**：垃圾回收
- **定义**：自动回收程序不再使用的内存的机制
- **说明**：垃圾回收器识别并释放不可达对象占用的内存；Java、Python、Go 等语言使用垃圾回收
- **相关**：Memory Leak（内存泄漏）、Reference Counting（引用计数）、Mark-and-Sweep（标记-清除）

### Heap / 堆
- **音标**：/hiːp/
- **中文**：堆
- **定义**：进程中用于动态内存分配的内存区域
- **说明**：堆从低地址向高地址增长；通过 malloc/free 或 new/delete 管理；程序员手动管理或垃圾回收器自动管理
- **相关**：Stack（栈）、malloc、Dynamic Allocation（动态分配）

### Huge Page / 大页
- **中文**：大页
- **定义**：比普通页更大的内存页，通常为 2MB 或 1GB
- **说明**：大页减少页表项数量和 TLB 未命中，提高大内存应用的性能；但可能增加内部碎片
- **相关**：Page Size（页大小）、TLB（转换后备缓冲器）

### Internal Fragmentation / 内部碎片
- **中文**：内部碎片
- **定义**：分配给进程的内存块中未被使用的部分
- **说明**：内部碎片发生在固定分区或分页系统中；例如页大小为 4KB，进程需要 5KB，则第二页有 3KB 内部碎片
- **相关**：External Fragmentation（外部碎片）、Paging（分页）

### Inverted Page Table / 反置页表
- **中文**：反置页表
- **定义**：以物理页框为索引的页表，每个页框对应一个条目，记录哪个进程的哪个虚拟页映射到该页框
- **说明**：反置页表的大小与物理内存成正比，与虚拟地址空间无关；需要哈希表加速查找
- **相关**：Page Table（页表）、Hash Table（哈希表）

### Least Recently Used (LRU) / 最近最少使用
- **中文**：最近最少使用
- **定义**：置换最长时间未被访问的页
- **说明**：LRU 利用时间局部性，性能接近最优；实现需要硬件支持（计数器或栈）或软件近似
- **相关**：Page Replacement（页面置换）、Clock Algorithm（时钟算法）

### Limit Register / 限长寄存器
- **中文**：限长寄存器
- **定义**：存储进程地址空间大小的寄存器
- **说明**：如果逻辑地址超过限长寄存器值，触发越界错误；与基址寄存器配合实现内存保护
- **相关**：Base Register（基址寄存器）、Memory Protection（内存保护）

### Locality / 局部性
- **中文**：局部性
- **定义**：程序访问内存时倾向于访问最近访问过的数据或其邻近数据的特性
- **说明**：分为时间局部性（Temporal Locality，最近访问的数据很可能再次被访问）和空间局部性（Spatial Locality，访问某个地址后很可能访问邻近地址）
- **相关**：Temporal Locality（时间局部性）、Spatial Locality（空间局部性）、Cache（高速缓存）

### Logical Address / 逻辑地址
- **中文**：逻辑地址
- **定义**：同 Virtual Address，是 CPU 生成的地址
- **说明**：逻辑地址在编译时生成，运行时通过重定位（Relocation）转换为物理地址
- **同义词**：Virtual Address
- **相关**：Physical Address（物理地址）、Relocation（重定位）

### Memory Leak / 内存泄漏
- **中文**：内存泄漏
- **定义**：程序动态分配内存后未释放，导致可用内存逐渐减少
- **说明**：长期运行的程序发生内存泄漏会导致系统变慢或崩溃；需要通过垃圾回收或手动管理避免
- **相关**：Garbage Collection（垃圾回收）、Dynamic Allocation（动态分配）

### Memory Management Unit (MMU) / 内存管理单元
- **中文**：内存管理单元
- **定义**：硬件组件，负责将虚拟地址转换为物理地址
- **说明**：MMU 使用页表（Page Table）进行地址转换；现代 CPU 中 MMU 集成在 CPU 芯片内
- **相关**：Page Table（页表）、Virtual Address（虚拟地址）、Physical Address（物理地址）、TLB（转换后备缓冲器）

### Memory Protection / 内存保护
- **中文**：内存保护
- **定义**：防止进程非法访问其他进程或操作系统内存的机制
- **说明**：通过基址寄存器、限长寄存器、页表保护位、段表限长等实现；确保进程隔离和系统安全
- **相关**：Base Register（基址寄存器）、Limit Register（限长寄存器）、Protection Bit（保护位）

### Multi-Level Page Table / 多级页表
- **中文**：多级页表
- **定义**：将页表分级存储，减少页表占用的连续内存空间
- **说明**：例如二级页表：外层页表（Page Directory）指向内层页表（Page Table）；x86 使用两级页表，x86-64 使用四级或五级页表
- **相关**：Page Table（页表）、Page Directory（页目录）、Inverted Page Table（反置页表）

### Not Recently Used (NRU) / 最近未使用
- **中文**：最近未使用
- **定义**：根据访问位和修改位将页分为四类，随机选择最低非空类的页置换
- **说明**：四类：0-未访问未修改、1-未访问已修改、2-已访问未修改、3-已访问已修改；优先置换 0 类
- **相关**：Clock Algorithm（时钟算法）、LRU（最近最少使用）

### Optimal Page Replacement / 最优页面置换
- **中文**：最优页面置换
- **定义**：置换在未来最长时间内不会被访问的页
- **说明**：理论上最优，但无法实现（需要预知未来）；用于评估其他算法的性能上限
- **同义词**：OPT、MIN
- **相关**：Page Replacement（页面置换）、Belady's Anomaly（Belady 异常）

### Page / 页
- **音标**：/peɪdʒ/
- **中文**：页（页面）
- **定义**：虚拟地址空间中的固定大小块
- **说明**：虚拟地址分为页号和页内偏移；页号是页表的索引
- **相关**：Frame（页框）、Page Table（页表）、Page Size（页大小）

### Page Fault / 页错误（缺页中断）
- **中文**：页错误（缺页中断）
- **定义**：访问的虚拟页不在物理内存中时触发的中断/异常
- **说明**：页错误处理程序需要从磁盘（交换区或文件）加载该页到内存；如果内存已满，需要先置换一页
- **相关**：Page Replacement（页面置换）、Virtual Memory（虚拟内存）、Trap（陷入）

### Page In / 页换入
- **中文**：页换入
- **定义**：将交换空间中的页读入物理内存
- **相关**：Page Out（页换出）、Swap In（换入）

### Page Out / 页换出
- **中文**：页换出
- **定义**：将物理内存中的页写入交换空间并释放该页框
- **相关**：Page In（页换入）、Swap Out（换出）、Page Replacement（页面置换）

### Page Replacement / 页面置换
- **中文**：页面置换
- **定义**：当物理内存已满且需要加载新页时，选择一个页换出以腾出空间
- **说明**：页面置换算法的目标是最小化页错误率；被置换的页如果是脏页需要先写回磁盘
- **相关**：Page Replacement Algorithm（页面置换算法）、Frame（页框）、Page Fault（页错误）

### Page Replacement Algorithm / 页面置换算法
- **中文**：页面置换算法
- **定义**：选择哪个页框被释放以供新页使用的策略
- **说明**：常见算法包括 FIFO、Optimal、LRU、Clock 等；好的算法应遵循局部性原理
- **相关**：Page Replacement（页面置换）、Belady's Anomaly（Belady 异常）

### Page Size / 页大小
- **中文**：页大小
- **定义**：单个页/页框的大小
- **说明**：常见页大小为 4KB、8KB、16KB、64KB；大页（Huge Page）可以是 2MB 或 1GB
- **相关**：Page（页）、Frame（页框）、Huge Page（大页）

### Page Table / 页表
- **中文**：页表
- **定义**：操作系统维护的数据结构，用于存储虚拟页到物理页框的映射关系
- **说明**：每个进程有自己的页表；页表项（PTE）包含页框号、有效位、保护位、修改位、访问位等
- **相关**：Page Table Entry（页表项）、Virtual Address（虚拟地址）、Physical Address（物理地址）

### Page Table Entry (PTE) / 页表项
- **中文**：页表项
- **定义**：页表中的单个条目，描述一个虚拟页的映射信息
- **说明**：PTE 包含：页框号（Frame Number）、有效位（Valid Bit）、保护位（Protection Bits）、修改位（Dirty Bit）、访问位（Reference Bit）、缓存禁用位等
- **相关**：Page Table（页表）、Valid Bit（有效位）、Dirty Bit（修改位）

### Paging / 分页
- **音标**：/ˈpeɪdʒɪŋ/
- **中文**：分页
- **定义**：将物理内存和虚拟地址空间都划分为固定大小的块，通过页表映射
- **说明**：分页消除了外部碎片，简化了内存管理；页大小通常为 4KB（x86）或 16KB（ARM）
- **相关**：Page（页）、Frame（页框）、Page Table（页表）、Virtual Memory（虚拟内存）

### Physical Address / 物理地址
- **中文**：物理地址
- **定义**：内存硬件中的实际存储位置地址
- **说明**：物理地址是内存芯片上的真实地址；多个进程的虚拟地址可能映射到同一个物理地址（共享内存）
- **相关**：Virtual Address（虚拟地址）、Frame（页框）、Page Table（页表）

### Protection Bit / 保护位
- **中文**：保护位
- **定义**：页表项中的标志位，控制对该页的访问权限
- **说明**：保护位定义读（Read）、写（Write）、执行（Execute）权限；非法访问会触发保护错误
- **相关**：Page Table Entry（页表项）、Access Control（访问控制）

### Reference Bit / 访问位（引用位）
- **中文**：访问位（引用位）
- **定义**：页表项中的标志位，表示该页是否被访问过
- **说明**：访问位用于页面置换算法（如 Clock 算法）；硬件在访问页时自动置位，操作系统定期清零
- **同义词**：Access Bit、Referenced Bit
- **相关**：Page Table Entry（页表项）、Page Replacement（页面置换）、Clock Algorithm（时钟算法）

### Reference String / 引用串
- **中文**：引用串
- **定义**：进程访问页的序列，用于分析和模拟页面置换算法
- **说明**：例如引用串 "1, 2, 3, 4, 1, 2, 5, 1, 2, 3, 4, 5"；用于计算给定算法和页框数的页错误次数
- **相关**：Page Replacement（页面置换）

### Resident Set / 驻留集
- **中文**：驻留集
- **定义**：当前驻留在物理内存中的进程的页的集合
- **说明**：驻留集大小可以固定或动态调整；操作系统通过页面置换算法管理驻留集
- **相关**：Working Set（工作集）、Page Replacement（页面置换）

### Segment / 段
- **音标**：/ˈseɡmənt/
- **中文**：段
- **定义**：程序的一个逻辑单元，如代码段、数据段、栈段等
- **说明**：每个段有段名/段号和段长；段内地址由段号和段内偏移组成
- **相关**：Segmentation（分段）、Segment Table（段表）

### Segment Table / 段表
- **中文**：段表
- **定义**：存储每个段的基址（Base Address）和限长（Limit）的数据结构
- **说明**：段表项包含段基址、段限长、保护位等；物理地址 = 段基址 + 段内偏移
- **相关**：Segment（段）、Segmentation（分段）

### Segmentation / 分段
- **音标**：/ˌseɡmenˈteɪʃn/
- **中文**：分段
- **定义**：将程序按逻辑单位（代码段、数据段、栈段等）划分为不同大小的段，每段独立映射到物理内存
- **说明**：分段符合程序的逻辑结构，便于保护和共享；但会产生外部碎片
- **相关**：Segment（段）、Segment Table（段表）、Segmentation Fault（段错误）

### Segmentation Fault / 段错误
- **中文**：段错误
- **定义**：程序访问了非法内存地址或越界访问段时触发的错误
- **说明**：段错误通常导致程序终止（SIGSEGV 信号）；常见原因包括访问空指针、数组越界、栈溢出等
- **同义词**：Segfault、SIGSEGV
- **相关**：Segmentation（分段）、Memory Protection（内存保护）、Null Pointer（空指针）

### Shared Page / 共享页
- **中文**：共享页
- **定义**：多个进程的虚拟地址空间映射到同一个物理页框的页
- **说明**：用于共享库（Shared Library）、共享内存（Shared Memory）；共享页需要写保护，修改时触发 COW
- **相关**：Copy-on-Write（写时复制）、Shared Memory（共享内存）、Shared Library（共享库）

### Stack / 栈
- **音标**：/stæk/
- **中文**：栈
- **定义**：进程中用于存储局部变量、函数参数、返回地址的内存区域
- **说明**：栈从高地址向低地址增长；由编译器自动管理；栈空间有限，溢出会导致段错误
- **相关**：Heap（堆）、Stack Frame（栈帧）、Stack Overflow（栈溢出）

### Swap File / 交换文件
- **中文**：交换文件
- **定义**：文件系统中用于交换空间的文件
- **说明**：交换文件比交换分区更灵活，可以随时调整大小；但性能可能略低
- **相关**：Swap Space（交换空间）、File System（文件系统）

### Swap In / 换入
- **中文**：换入
- **定义**：将交换空间中的页或进程移回内存
- **说明**：换入通常在访问被换出的页时（页错误）发生
- **相关**：Swap Out（换出）、Swapping（交换）、Page In（页换入）

### Swap Out / 换出
- **中文**：换出
- **定义**：将内存中的页或进程移到交换空间
- **说明**：换出释放物理内存；换出脏页需要先写回磁盘
- **相关**：Swap In（换入）、Swapping（交换）、Page Out（页换出）

### Swap Partition / 交换分区
- **中文**：交换分区
- **定义**：磁盘上专门用于交换空间的分区
- **相关**：Swap Space（交换空间）、Partition（分区）

### Swap Space / 交换空间
- **中文**：交换空间
- **定义**：磁盘上用于存储换出页或进程的特殊区域
- **说明**：交换空间可以是专门的交换分区（Swap Partition）或交换文件（Swap File）；大小通常为物理内存的 1-2 倍
- **相关**：Swapping（交换）、Swap Partition（交换分区）、Swap File（交换文件）

### Swapping / 交换
- **音标**：/ˈswɒpɪŋ/
- **中文**：交换
- **定义**：将整个进程或页从内存移到磁盘（换出）或从磁盘移回内存（换入）的技术
- **说明**：交换用于内存紧张时释放内存；现代系统通常采用页交换（Paging）而非整个进程交换
- **相关**：Swap Space（交换空间）、Swap Out（换出）、Swap In（换入）

### Text Segment / 代码段
- **中文**：代码段（文本段）
- **定义**：存储程序可执行指令的内存区域
- **说明**：代码段通常是只读的，可以被多个进程共享（共享库）；也称为 Text Section
- **同义词**：Code Segment、Text Section
- **相关**：Data Segment（数据段）、BSS Segment（BSS 段）

### Thrashing / 抖动
- **音标**：/ˈθræʃɪŋ/
- **中文**：抖动（颠簸）
- **定义**：系统频繁进行页面置换，导致大部分时间用于换入换出而非执行程序
- **说明**：抖动发生在内存严重不足或工作集大于物理内存时；可以通过增加内存或减少进程数解决
- **相关**：Working Set（工作集）、Page Fault Rate（页错误率）、Page Replacement（页面置换）

### TLB Hit / TLB 命中
- **中文**：TLB 命中
- **定义**：虚拟地址的页表项在 TLB 中找到
- **说明**：TLB 命中时，地址转换几乎瞬间完成；TLB 未命中时需要访问页表
- **相关**：TLB Miss（TLB 未命中）、TLB（转换后备缓冲器）

### TLB Miss / TLB 未命中
- **中文**：TLB 未命中
- **定义**：虚拟地址的页表项不在 TLB 中
- **说明**：TLB 未命中时，硬件自动访问页表获取页表项并更新 TLB（硬件管理 TLB）或由操作系统处理（软件管理 TLB）
- **相关**：TLB Hit（TLB 命中）、Page Table Walk（页表遍历）

### Translation Lookaside Buffer (TLB) / 转换后备缓冲器
- **中文**：转换后备缓冲器
- **定义**：缓存最近使用的页表项的高速缓存
- **说明**：TLB 用于加速虚拟地址到物理地址的转换；TLB 命中可以避免访问页表；TLB 是硬件管理的关联存储器
- **相关**：MMU（内存管理单元）、Page Table（页表）、Cache（高速缓存）

### Valid Bit / 有效位
- **中文**：有效位
- **定义**：页表项中的标志位，表示该页是否在物理内存中
- **说明**：有效位为 1 表示页在内存中，为 0 表示页不在内存中（可能在磁盘上）；访问有效位为 0 的页会触发页错误（Page Fault）
- **相关**：Page Table Entry（页表项）、Page Fault（页错误）

### Virtual Address / 虚拟地址
- **中文**：虚拟地址
- **定义**：进程看到的逻辑内存地址
- **说明**：虚拟地址需要通过地址转换机制（MMU）映射为物理地址；虚拟地址空间可以大于物理内存
- **相关**：Physical Address（物理地址）、Virtual Address Space（虚拟地址空间）、MMU（内存管理单元）

### Virtual Address Space / 虚拟地址空间
- **中文**：虚拟地址空间
- **定义**：进程可以使用的全部虚拟地址集合
- **说明**：虚拟地址空间通常分为代码段、数据段、堆、栈等区域；32 位系统为 4GB，64 位系统极大
- **相关**：Address Space（地址空间）、Virtual Memory（虚拟内存）

### Virtual Memory / 虚拟内存
- **中文**：虚拟内存
- **定义**：操作系统提供的抽象，使每个进程拥有独立的、连续的、大于物理内存的地址空间
- **说明**：虚拟内存通过请求分页和页面置换实现；使得程序可以运行大于物理内存的进程，并提供内存隔离
- **相关**：Paging（分页）、Page Replacement（页面置换）、Address Space（地址空间）

### Working Set / 工作集
- **中文**：工作集
- **定义**：进程在最近一段时间（工作集窗口）内访问的页的集合
- **说明**：工作集模型用于指导页面置换；如果工作集大于可用物理内存，会发生抖动
- **相关**：Thrashing（抖动）、Locality（局部性）、Page Fault（页错误）

### Working Set Model / 工作集模型
- **中文**：工作集模型
- **定义**：基于工作集概念的内存管理模型，确保进程的工作集保留在内存中
- **说明**：工作集模型可以减少抖动；操作系统跟踪每个进程的工作集，优先保留工作集中的页
- **相关**：Working Set（工作集）、Thrashing（抖动）

### Worst Fit / 最坏适应
- **中文**：最坏适应
- **定义**：内存分配算法，选择最大的空闲块进行分配
- **说明**：分配后剩余的空闲块较大，可以继续使用；但大进程可能找不到足够空间
- **相关**：First Fit（首次适应）、Best Fit（最佳适应）
