# 08. 算法设计策略 (Algorithm Design Strategies)
### Backtracking / 回溯
- **音标**：/ˈbæktrækɪŋ/
- **中文**：回溯
- **定义**：通过尝试所有可能的分支，遇到不可行分支时回退（剪枝）以找到所有解的算法
- **说明**：回溯是暴力搜索的优化（有剪枝）；用递归实现，遵循"选择→尝试→撤销"的模式；经典问题：N 皇后、数独、排列/组合、子集和
- **相关**：DFS（深度优先搜索）、Pruning（剪枝）、Recursion（递归）
- **例句**：Backtracking explores the solution space by trying choices and undoing them when they fail.
### Bit Manipulation / 位运算
- **中文**：位运算
- **定义**：直接操作整数的二进制位进行计算的技术
- **说明**：位运算包括：与（&）、或（|）、异或（^）、非（~）、左移（<<）、右移（>>）；快于算术运算；用于状态压缩、哈希布隆过滤器、权限控制、集合表示
- **相关**：Bit Mask（位掩码）、Bitwise Operation（按位操作）
### Branch and Bound / 分支限界
- **中文**：分支限界
- **定义**：在搜索过程中，通过计算当前分支的上下界，剪掉不可能产生更优解的分支
- **说明**：分支限界用于优化问题（如旅行商 TSP）；与回溯不同，分支限界关注最优解而不是所有解；用优先队列（最佳优先搜索）管理待扩展节点
- **相关**：Backtracking（回溯）、Bounding（定界）、Optimization（优化）
### Complexity Class / 复杂度类
- **中文**：复杂度类
- **定义**：根据计算所需资源对问题进行分类的集合
- **说明**：主要复杂度类：P（多项式时间）、NP（非确定性多项式时间）、NP-Complete、NP-Hard、PSPACE（多项式空间）、EXPTIME（指数时间）
- **相关**：P vs NP、NP-Complete、Time Complexity（时间复杂度）
### D&C (Divide and Conquer) / 分治
- **发音**：/diː ænd siː/
- **中文**：分治
- **定义**：将问题分解为多个子问题，分别求解后再合并为原问结果的算法设计策略
- **说明**：分治算法通常包含三个步骤：分解（Divide）、解决（Conquer）、合并（Combine）；经典应用：归并排序、快速排序、二分查找、FFT、矩阵乘法（Strassen）
- **相关**：Recursion（递归）、Merge Sort（归并排序）、Quick Sort（快速排序）
- **例句**：Divide and conquer breaks a problem into smaller subproblems, solves each, then combines.
### Enumeration / 枚举
- **音标**：/ɪˌnjuːməˈreɪʃn/
- **中文**：枚举
- **定义**：一一列出所有可能的情况来求解问题
- **说明**：枚举是简单的暴力方法；对于大规模问题通常不可行（组合爆炸）；组合枚举、子集枚举、排列枚举等
- **相关**：Brute Force（暴力枚举）、Combination（组合）、Permutation（排列）
### Horspool Algorithm / Horspool 算法
- **中文**：Horspool 算法
- **定义**：Boyer-Moore 算法的简化版字符串匹配算法
- **说明**：Horspool 仅使用坏字符规则（Bad Character Rule）进行跳转；预处理 O(m+|Σ|)，平均 O(n)，最坏 O(nm)；实践中效率不错
- **相关**：Boyer-Moore Algorithm（Boyer-Moore 算法）、KMP（KMP 算法）
### KMP (Knuth-Morris-Pratt) / KMP 算法
- **发音**：/keɪ-ɛm-piː/
- **中文**：KMP 算法
- **定义**：利用部分匹配表（next 数组/LPS 数组）避免主串指针回溯的线性时间字符串匹配算法
- **说明**：KMP 时间复杂度 O(n+m)，n 为文本长度，m 为模式长度；核心是构建前缀表（Prefix Table）；比朴素法高效，比 BM 简单
- **相关**：String Matching（字符串匹配）、LPS（最长公共前后缀）、Boyer-Moore Algorithm
- **例句**：KMP achieves O(n+m) string matching by precomputing a failure function.
### LPS (Longest Proper Prefix Suffix) / 最长公共前后缀
- **发音**：/ɛl-piː-ɛs/
- **中文**：最长公共前后缀
- **定义**：KMP 算法中构建的辅助数组，记录每个前缀的最长相等前后缀长度
- **说明**：LPS 数组使 KMP 算法在匹配失败时能知道模式串指针应该回退到哪个位置
- **相关**：KMP（KMP 算法）、Prefix（前缀）、Suffix（后缀）
### Manacher's Algorithm / Manacher 算法
- **中文**：Manacher 算法
- **定义**：用于在 O(n) 时间内找到字符串中最长回文子串的算法
- **说明**：Manacher 算法使用中心扩展思想，利用回文的对称性避免重复计算；插入分隔符统一处理奇偶回文
- **相关**：Palindrome（回文）、String Matching（字符串匹配）
### Moore's Voting Algorithm / 摩尔投票算法
- **中文**：摩尔投票算法
- **定义**：在线性时间和常数空间内找到数组中的多数元素（出现次数 > n/2）的算法
- **说明**：摩尔投票算法通过计数器维护候选元素；两两抵消不同元素，最后剩下的即为候选；需二次遍历验证
- **相关**：Majority Element（多数元素）、Linear Time（线性时间）
### Prefix Sum / 前缀和
- **音标**：/ˈpriːfɪks sʌm/
- **中文**：前缀和
- **定义**：预处理数组，pref[i] 存储原数组前 i 个元素的和，用于快速区间求和
- **说明**：一维前缀和 O(n) 预处理，O(1) 区间和查询；二维前缀和同理；扩展到前缀 XOR、前缀最大值等
- **相关**：Binary Indexed Tree（树状数组）、Range Query（区间查询）
### Pruning / 剪枝
- **音标**：/ˈpruːnɪŋ/
- **中文**：剪枝
- **定义**：在搜索过程中提前排除不可行解或非最优解的分支，减少搜索空间
- **说明**：剪枝是回溯和分支限界算法的核心优化；可行性剪枝（违反约束）、最优性剪枝（不可能更优）、对称性剪枝；好的剪枝可以将指数时间降到多项式
- **相关**：Backtracking（回溯）、Branch and Bound（分支限界）
### Rabin-Karp Algorithm / Rabin-Karp 算法
- **中文**：Rabin-Karp 算法
- **定义**：利用滚动哈希进行字符串匹配的算法
- **说明**：Rabin-Karp 计算模式串哈希值，在主串中滑动比较哈希值；平均 O(n+m)；可用于多模式串匹配（检查一组模式串）
- **相关**：Rolling Hash（滚动哈希）、KMP（KMP 算法）、String Matching（字符串匹配）
### State Machine / 状态机
- **中文**：状态机
- **定义**：由状态、转移条件和动作组成的计算模型
- **说明**：有限状态机（FSM）常用于字符串匹配（AC 自动机）、词法分析、游戏 AI；状态转移图描述从初始状态到终止状态的路径
- **同义词**：Finite State Machine (FSM)
- **相关**：Automata（自动机）、DFA（确定有限自动机）、NFA（非确定有限自动机）
### String Matching / 字符串匹配
- **中文**：字符串匹配
- **定义**：在文本字符串中查找给定模式串出现位置的问题
- **说明**：朴素算法 O(nm)；KMP O(n+m)；Boyer-Moore 平均亚线性；Rabin-Karp 滚动哈希；AC 自动机多模式匹配；应用：文本编辑器 Ctrl+F、搜索引擎、生物信息学
- **相关**：KMP、Boyer-Moore Algorithm（Boyer-Moore 算法）、Rabin-Karp Algorithm（Rabin-Karp 算法）
### Tabulation / 填表法
- **中文**：填表法
- **定义**：动态规划的自底向上实现方式，用数组逐个填入子问题解
- **说明**：填表法直接构建 DP 表；通常比记忆化递归更高效（无函数调用开销）；但需要确定正确的填表顺序（拓扑序）
- **同义词**：Bottom-up DP
- **相关**：Memoization（记忆化）、Dynamic Programming（动态规划）

