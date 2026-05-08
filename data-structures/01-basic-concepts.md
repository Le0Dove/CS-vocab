# 01. 基础概念 (Basic Concepts)
### Abstract Data Type (ADT) / 抽象数据类型
- **音标**：/ˈæbstrækt ˈdeɪtə taɪp/
- **中文**：抽象数据类型
- **定义**：由数据集合和定义在该集合上的一组操作组成的数学模型，不涉及具体实现
- **说明**：ADT 分离了接口（操作）和实现；例如栈 ADT 定义 push/pop 操作，可以用数组或链表实现
- **相关**：Data Structure（数据结构）、Interface（接口）、Encapsulation（封装）
- **例句**：A stack is an abstract data type that follows the LIFO principle.
### Algorithm / 算法
- **音标**：/ˈælɡərɪðəm/
- **中文**：算法
- **定义**：解决特定问题的一系列明确、有限的计算步骤
- **说明**：算法具有有穷性、确定性、可行性、输入、输出五个特性；同一问题可以有多种算法
- **相关**：Data Structure（数据结构）、Complexity（复杂度）、Pseudocode（伪代码）
- **例句**：Binary search is an efficient algorithm for finding an item in a sorted array.
### Amortized Analysis / 摊还分析
- **音标**：/ˈæmərtaɪzd əˈnæləsɪs/
- **中文**：摊还分析
- **定义**：分析一系列操作中每个操作的平均时间复杂度，考虑最坏情况下的上界
- **说明**：摊还分析用于某些数据结构（如动态数组扩容、并查集路径压缩），单次操作可能很慢，但平均很快；方法包括聚合分析、记账法、势能法
- **相关**：Time Complexity（时间复杂度）、Worst Case（最坏情况）、Average Case（平均情况）
- **例句**：The amortized time complexity of dynamic array expansion is O(1).
### Average Case / 平均情况
- **中文**：平均情况
- **定义**：算法在所有可能输入上的平均运行时间
- **说明**：平均情况分析假设输入服从某种分布（通常是均匀分布）；实际中比最坏情况更反映真实性能
- **相关**：Worst Case（最坏情况）、Best Case（最好情况）、Expected Value（期望值）
- **例句**：QuickSort has O(n log n) average-case time complexity.
### Best Case / 最好情况
- **中文**：最好情况
- **定义**：算法在所有可能输入中的最优运行时间
- **说明**：最好情况通常不具代表性；例如插入排序在已排序数组上为 O(n)，但一般情况为 O(n²)
- **相关**：Worst Case（最坏情况）、Average Case（平均情况）
### Big O Notation / 大 O 记号
- **音标**：/bɪɡ oʊ noʊˈteɪʃn/
- **中文**：大 O 记号
- **定义**：描述算法时间或空间复杂度的渐进上界的数学符号
- **说明**：O(f(n)) 表示当 n 足够大时，算法运行时间不超过 c·f(n)；常见：O(1)、O(log n)、O(n)、O(n log n)、O(n²)、O(2ⁿ)、O(n!)
- **同义词**：Big Oh、Asymptotic Upper Bound
- **相关**：Big Ω（大欧米伽）、Big Θ（大西塔）、Time Complexity（时间复杂度）
- **例句**：The time complexity of linear search is O(n).
### Big Θ (Theta) Notation / 大西塔记号
- **音标**：/bɪɡ ˈθeɪtə noʊˈteɪʃn/
- **中文**：大西塔记号
- **定义**：描述算法复杂度的紧确界，同时是上界和下界
- **说明**：Θ(f(n)) 表示算法时间既不超过也不低于 f(n) 的常数倍；当 Big O 和 Big Ω 相等时使用
- **相关**：Big O（大 O）、Big Ω（大欧米伽）
### Big Ω (Omega) Notation / 大欧米伽记号
- **音标**：/bɪɡ ˈoʊmeɡə noʊˈteɪʃn/
- **中文**：大欧米伽记号
- **定义**：描述算法复杂度的渐进下界
- **说明**：Ω(f(n)) 表示算法至少需要 c·f(n) 的时间；用于证明算法最优性
- **相关**：Big O（大 O）、Big Θ（大西塔）
### Brute Force / 暴力枚举
- **音标**：/bruːt fɔːrs/
- **中文**：暴力枚举
- **定义**：直接尝试所有可能解来解决问题的方法
- **说明**：暴力法简单但效率低；适合小规模问题或验证其他算法的正确性；很多优化算法是在暴力法基础上改进的
- **同义词**：Exhaustive Search（穷举搜索）
- **相关**：Optimization（优化）、Backtracking（回溯）
### Complexity / 复杂度
- **音标**：/kəmˈpleksəti/
- **中文**：复杂度
- **定义**：衡量算法所需资源（时间、空间）随输入规模增长的度量
- **说明**：分为时间复杂度（Time Complexity）和空间复杂度（Space Complexity）；用大 O 记号表示
- **相关**：Big O、Time Complexity（时间复杂度）、Space Complexity（空间复杂度）
### Computational Complexity / 计算复杂度
- **中文**：计算复杂度
- **定义**：从理论上分析问题的计算难度和算法效率的学科
- **说明**：计算复杂度分为时间复杂度和空间复杂度；P、NP、NP-Complete 等问题分类属于计算复杂度理论
- **相关**：P vs NP、Complexity Class（复杂度类）
### Constant Time / 常数时间
- **中文**：常数时间
- **定义**：算法运行时间不随输入规模变化，记为 O(1)
- **说明**：常数时间操作是最理想的；如数组按索引访问、哈希表查找（平均）
- **相关**：O(1)、Time Complexity（时间复杂度）
### Data Structure / 数据结构
- **音标**：/ˈdeɪtə ˈstrʌktʃər/
- **中文**：数据结构
- **定义**：计算机中存储、组织数据的方式，包括数据元素之间的逻辑关系和物理存储方式
- **说明**：数据结构 = 数据元素 + 元素之间的关系 + 操作；选择合适的数据结构可以提高算法效率；常见：数组、链表、栈、队列、树、图、哈希表
- **相关**：Algorithm（算法）、ADT（抽象数据类型）
### Dynamic Programming / 动态规划
- **音标**：/daɪˈnæmɪk ˈproʊɡræmɪŋ/
- **中文**：动态规划
- **定义**：通过将问题分解为重叠子问题，存储子问题解以避免重复计算的优化技术
- **说明**：DP 适用于具有最优子结构和重叠子问题性质的问题；实现方式：自顶向下（记忆化搜索）和自底向上（填表法）；经典问题：斐波那契、背包、最长公共子序列、最短路径
- **同义词**：DP
- **相关**：Memoization（记忆化）、Recursion（递归）、Optimal Substructure（最优子结构）
- **例句**：Dynamic programming solves the Fibonacci sequence in O(n) time by storing intermediate results.
### Encapsulation / 封装
- **音标**：/ɪnˈkæpsjuˈleɪʃn/
- **中文**：封装
- **定义**：将数据（属性）和操作数据的方法绑定在一起，并隐藏内部实现的机制
- **说明**：封装是面向对象编程的核心特性之一；通过访问控制（public/private/protected）实现信息隐藏
- **相关**：ADT（抽象数据类型）、OOP（面向对象编程）、Abstraction（抽象）
### Expected Value / 期望值
- **中文**：期望值
- **定义**：随机变量在大量重复实验中的平均值
- **说明**：在算法分析中，期望值用于平均情况分析；E[X] = Σx·P(X=x)
- **相关**：Average Case（平均情况）、Probability（概率）
### Greedy Algorithm / 贪心算法
- **音标**：/ˈɡriːdi ˈælɡərɪðəm/
- **中文**：贪心算法
- **定义**：在每一步选择中都采取当前最优（局部最优）策略，希望最终达到全局最优的算法
- **说明**：贪心算法不一定得到全局最优解，但效率高；适用于具有贪心选择性质的问题；经典问题：活动选择、哈夫曼编码、最小生成树（Prim/Kruskal）、Dijkstra 最短路径
- **相关**：Dynamic Programming（动态规划）、Optimal Substructure（最优子结构）
- **例句**：Dijkstra's algorithm is a greedy approach to finding the shortest path.
### Heuristic / 启发式
- **音标**：/hjuˈrɪstɪk/
- **中文**：启发式
- **定义**：基于经验和直觉的解决问题方法，不保证最优但通常高效
- **说明**：启发式算法用于 NP-hard 问题的近似求解；如 A* 算法的启发函数、模拟退火、遗传算法
- **相关**：Approximation Algorithm（近似算法）、Metaheuristic（元启发式）
### Implementation / 实现
- **音标**：/ˌɪmplɪmenˈteɪʃn/
- **中文**：实现
- **定义**：将算法或数据结构从理论设计转换为可执行代码的过程
- **说明**：同一 ADT 可以有不同的实现（如栈可用数组或链表）；实现选择影响时间/空间复杂度
- **相关**：ADT（抽象数据类型）、Algorithm（算法）
### In-Place / 原地
- **音标**：/ɪn pleɪs/
- **中文**：原地
- **定义**：算法在输入数据结构本身上进行操作，只使用常数额外空间的特性
- **说明**：原地算法空间复杂度为 O(1)（不包括输入）；如快速排序（原地）、堆排序、反转数组
- **相关**：Space Complexity（空间复杂度）、Out-of-Place（非原地）
### Input Size / 输入规模
- **中文**：输入规模
- **定义**：衡量问题大小的参数，通常记为 n
- **说明**：输入规模可以是数组元素个数、图的顶点数、数字的位数等；复杂度分析以输入规模为变量
- **相关**：Time Complexity（时间复杂度）、n
### Instance / 实例
- **音标**：/ˈɪnstəns/
- **中文**：实例
- **定义**：问题的具体输入数据
- **说明**：一个问题可以有多个实例；如排序问题的实例是一个具体的数组
- **相关**：Problem（问题）、Input（输入）
### Iteration / 迭代
- **音标**：/ˌɪtəˈreɪʃn/
- **中文**：迭代
- **定义**：通过循环重复执行一段代码直到满足条件的过程
- **说明**：迭代通常比递归更高效（无函数调用开销）；所有递归都可以转换为迭代（需要显式栈）
- **相关**：Recursion（递归）、Loop（循环）
- **例句**：The iterative version of Fibonacci uses a loop instead of recursive calls.
### Linear Time / 线性时间
- **中文**：线性时间
- **定义**：算法运行时间与输入规模成正比，记为 O(n)
- **说明**：线性时间算法每个元素平均只处理常数次；如遍历数组、线性查找
- **相关**：O(n)、Time Complexity（时间复杂度）
### Little o Notation / 小 o 记号
- **中文**：小 o 记号
- **定义**：表示严格小于的渐进上界
- **说明**：o(f(n)) 表示极限意义下比 f(n) 增长慢；如 n = o(n²)，但 n ≠ o(n)
- **相关**：Big O（大 O）、Asymptotic Analysis（渐进分析）
### Logarithmic Time / 对数时间
- **音标**：/ˌlɔːɡəˈrɪðmɪk taɪm/
- **中文**：对数时间
- **定义**：算法运行时间与输入规模的对数成正比，记为 O(log n)
- **说明**：对数时间非常高效；常见于二分查找、平衡二叉树操作、堆操作
- **相关**：O(log n)、Binary Search（二分查找）
### Master Theorem / 主定理
- **音标**：/ˈmæstər ˈθiːərəm/
- **中文**：主定理
- **定义**：用于求解分治算法时间复杂度的递归关系的定理
- **说明**：适用于 T(n) = aT(n/b) + f(n) 形式；根据 a、b、f(n) 的关系直接得出复杂度；分为三种情况
- **相关**：Divide and Conquer（分治）、Recurrence Relation（递归关系）
- **例句**：Using the Master Theorem, merge sort's time complexity is O(n log n).
### Memoization / 记忆化
- **音标**：/ˌmeməraɪˈzeɪʃn/
- **中文**：记忆化
- **定义**：在递归计算中缓存已计算结果以避免重复计算的技术
- **说明**：记忆化是动态规划的自顶向下实现方式；将指数时间降为多项式时间；通常使用数组或哈希表存储结果
- **同义词**：Memoisation（英式拼写）
- **相关**：Dynamic Programming（动态规划）、Cache（缓存）、Recursion（递归）
### n
- **发音**：/ɛn/
- **中文**：输入规模（n）
- **定义**：算法分析中表示输入规模的变量
- **说明**：n 通常表示数组长度、节点数、元素个数等；复杂度分析的核心变量
- **相关**：Input Size（输入规模）、Time Complexity（时间复杂度）
### NP-Complete / NP 完全
- **音标**：/ɛn-piː kəmˈpliːt/
- **中文**：NP 完全
- **定义**：一类既属于 NP 又具有 NP-hard 性质的问题，是 NP 中最难的问题
- **说明**：如果任一 NP-Complete 问题有多项式时间算法，则 P = NP；著名问题：旅行商问题、 SAT、3-SAT、背包问题、图着色
- **相关**：P vs NP、NP-Hard（NP 难）、Polynomial Time（多项式时间）
### NP-Hard / NP 难
- **音标**：/ɛn-piː hɑːrd/
- **中文**：NP 难
- **定义**：至少和 NP 中最难问题一样难的问题，但不要求本身属于 NP
- **说明**：NP-Hard 问题可能比 NP 更难；NP-Complete 是 NP-Hard 的子集（还需属于 NP）；如停机问题是 NP-Hard 但不是 NP-Complete
- **相关**：NP-Complete、P vs NP
### Optimal Substructure / 最优子结构
- **中文**：最优子结构
- **定义**：问题的最优解包含子问题的最优解的性质
- **说明**：具有最优子结构的问题适合用动态规划或贪心算法求解；如最短路径、最大子数组和
- **相关**：Dynamic Programming（动态规划）、Greedy Algorithm（贪心算法）
### Optimization Problem / 优化问题
- **中文**：优化问题
- **定义**：寻找满足约束条件下使目标函数最优（最大或最小）的解的问题
- **说明**：优化问题分为线性规划、整数规划、凸优化等；很多实际问题是 NP-hard 的优化问题
- **相关**：Constraint（约束）、Objective Function（目标函数）
### Out-of-Place / 非原地
- **中文**：非原地
- **定义**：算法需要额外空间存储结果，不修改原始输入数据
- **说明**：非原地算法空间复杂度通常为 O(n)；如归并排序需要额外数组
- **相关**：In-Place（原地）、Space Complexity（空间复杂度）
### Overlapping Subproblems / 重叠子问题
- **中文**：重叠子问题
- **定义**：问题的递归分解中，相同的子问题被多次计算的性质
- **说明**：重叠子问题是使用动态规划的标志；通过存储子问题解（记忆化或填表）避免重复计算
- **相关**：Dynamic Programming（动态规划）、Memoization（记忆化）
### P vs NP / P 对 NP 问题
- **中文**：P 对 NP 问题
- **定义**：计算机科学中最重要的未解决问题之一，问 P 类问题是否等于 NP 类问题
- **说明**：P = 多项式时间可解的问题；NP = 多项式时间可验证的问题；大多数人认为 P ≠ NP；克雷数学研究所悬赏 100 万美元
- **相关**：NP-Complete、Complexity Class（复杂度类）
### Polynomial Time / 多项式时间
- **音标**：/ˌpɒliˈnoʊmiəl taɪm/
- **中文**：多项式时间
- **定义**：算法运行时间是输入规模的多项式函数，如 O(n)、O(n²)、O(n³)
- **说明**：多项式时间被认为是"高效"的；指数时间 O(2ⁿ) 被认为是"低效"的；P 类问题就是多项式时间可解的
- **相关**：P vs NP、Exponential Time（指数时间）
### Pseudocode / 伪代码
- **音标**：/ˈsuːdoʊkoʊd/
- **中文**：伪代码
- **定义**：介于自然语言和编程语言之间，用于描述算法逻辑的简化表示
- **说明**：伪代码不遵循特定语法，注重表达算法思想；是教材和论文中描述算法的标准方式
- **相关**：Algorithm（算法）、Flowchart（流程图）
### Quadratic Time / 平方时间
- **音标**：/kwɒˈdrætɪk taɪm/
- **中文**：平方时间
- **定义**：算法运行时间与输入规模的平方成正比，记为 O(n²)
- **说明**：平方时间常见于双重循环；如冒泡排序、选择排序、插入排序最坏情况；对于大数据量性能差
- **相关**：O(n²)、Time Complexity（时间复杂度）
### Recurrence Relation / 递归关系
- **音标**：/rɪˈkʌrəns rɪˈleɪʃn/
- **中文**：递归关系
- **定义**：用自身定义自身的数学方程，用于描述递归算法的时间复杂度
- **说明**：常见递归关系：T(n) = T(n-1) + O(1)（线性）、T(n) = 2T(n/2) + O(n)（归并排序）；求解方法：代入法、递归树法、主定理
- **相关**：Recursion（递归）、Master Theorem（主定理）
### Recursive Algorithm / 递归算法
- **音标**：/rɪˈkɜːrsɪv ˈælɡərɪðəm/
- **中文**：递归算法
- **定义**：通过函数调用自身来解决问题的算法
- **说明**：递归需要基线条件（base case）和递归条件；代码简洁但可能有栈溢出风险；所有递归都可以改写为迭代
- **相关**：Recursion（递归）、Iteration（迭代）、Stack Overflow（栈溢出）
### Reduction / 归约
- **音标**：/rɪˈdʌkʃn/
- **中文**：归约
- **定义**：将一个问题转化为另一个已知问题的技术，用于证明问题的难度
- **说明**：如果问题 A 可以归约为问题 B，则 A 不比 B 难；NP-Complete 证明常用多项式时间归约
- **相关**：NP-Complete、Polynomial Time（多项式时间）
### Space Complexity / 空间复杂度
- **音标**：/speɪs kəmˈpleksəti/
- **中文**：空间复杂度
- **定义**：算法执行过程中所需的额外内存空间随输入规模增长的度量
- **说明**：空间复杂度关注辅助空间（不包括输入本身）；O(1) 表示原地算法；O(n) 表示需要与输入同规模的额外空间
- **相关**：Time Complexity（时间复杂度）、Auxiliary Space（辅助空间）
### Stable / 稳定
- **音标**：/ˈsteɪbl/
- **中文**：稳定的
- **定义**：排序算法中，相等元素的相对顺序在排序后保持不变的特性
- **说明**：稳定排序：冒泡排序、插入排序、归并排序、计数排序；不稳定排序：选择排序、快速排序、堆排序；稳定性对多关键字排序很重要
- **相关**：Sorting Algorithm（排序算法）、Unstable（不稳定）
- **例句**：Merge sort is a stable sorting algorithm.
### Subproblem / 子问题
- **音标**：/ˈsʌbprɒbləm/
- **中文**：子问题
- **定义**：原问题分解后得到的较小规模的问题
- **说明**：分治和动态规划都将问题分解为子问题；子问题的解组合成原问题的解
- **相关**：Divide and Conquer（分治）、Dynamic Programming（动态规划）
### Subroutine / 子程序
- **音标**：/ˈsʌbruːtiːn/
- **中文**：子程序
- **定义**：可独立调用执行的代码块，用于完成特定子任务
- **说明**：子程序包括函数（Function）和过程（Procedure）；提高代码复用性和模块化
- **同义词**：Function（函数）、Procedure（过程）
### Time Complexity / 时间复杂度
- **音标**：/taɪm kəmˈpleksəti/
- **中文**：时间复杂度
- **定义**：算法执行所需时间随输入规模增长的度量
- **说明**：时间复杂度通常关注最坏情况；常见：O(1) < O(log n) < O(n) < O(n log n) < O(n²) < O(2ⁿ)；是衡量算法效率的核心指标
- **相关**：Space Complexity（空间复杂度）、Big O、Algorithm（算法）
- **例句**：We analyze the time complexity to choose the most efficient algorithm.
### Trade-off / 权衡
- **音标**：/ˈtreɪd ɔːf/
- **中文**：权衡
- **定义**：在多个相互冲突的目标之间做出平衡选择
- **说明**：常见权衡：时间 vs 空间、正确性 vs 速度、内存 vs 磁盘、开发效率 vs 运行效率；数据结构选择就是典型的权衡
- **相关**：Optimization（优化）、Time-Space Trade-off（时间空间权衡）
### Turing Machine / 图灵机
- **音标**：/ˈtjʊərɪŋ məˈʃiːn/
- **中文**：图灵机
- **定义**：由 Alan Turing 提出的抽象计算模型，是现代计算机理论的基础
- **说明**：图灵机由无限长纸带、读写头、状态寄存器、控制规则组成；任何可计算问题都可以用图灵机描述；Church-Turing 论题认为图灵机是可计算性的极限
- **相关**：Computability（可计算性）、Algorithm（算法）、P vs NP
### Unstable / 不稳定
- **中文**：不稳定的
- **定义**：排序算法中，相等元素的相对顺序可能改变的特性
- **说明**：不稳定排序：选择排序、快速排序、堆排序；不稳定不一定不好，但某些场景需要稳定性
- **相关**：Stable（稳定的）、Sorting Algorithm（排序算法）
### Worst Case / 最坏情况
- **中文**：最坏情况
- **定义**：算法在所有可能输入中的最长运行时间
- **说明**：最坏情况分析保证算法的性能上界；通常用于算法分析；例如快速排序最坏 O(n²)，平均 O(n log n)
- **相关**：Best Case（最好情况）、Average Case（平均情况）、Big O
