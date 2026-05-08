# 07. 高级数据结构 (Advanced Data Structures)
### Binary Indexed Tree / 树状数组
- **音标**：/ˈbaɪnəri ˈɪndɛkst triː/
- **中文**：树状数组
- **定义**：支持高效前缀和查询和单点更新的数据结构
- **说明**：树状数组用数组实现；前缀和查询 O(log n)，单点更新 O(log n)；空间 O(n)；实现简单、常数小；区间和/区间更新需差分
- **同义词**：Fenwick Tree
- **相关**：Segment Tree（线段树）、Prefix Sum（前缀和）、Range Query（区间查询）
- **例句**：A Fenwick tree can compute prefix sums and perform point updates in O(log n).
### Disjoint Set / 并查集
- **音标**：/dɪsˈdʒɔɪnt sɛt/
- **中文**：并查集
- **定义**：管理若干不相交集合的数据结构，支持合并（Union）和查询所属集合（Find）操作
- **说明**：优化：路径压缩（Path Compression）+ 按秩合并（Union by Rank/Size）；均摊时间复杂度接近 O(1)（阿克曼函数反函数）；应用：Kruskal 算法、连通分量、等价类
- **同义词**：Union-Find（并查集）
- **相关**：Connected Component（连通分量）、Kruskal's Algorithm（Kruskal 算法）
### Disjoint Set Union (DSU) / 并查集
- **发音**：/diː-ɛs-juː/
- **中文**：并查集
- **定义**：同 Disjoint Set，竞赛编程常用术语
- **相关**：Disjoint Set（并查集）
### Interval Tree / 区间树
- **中文**：区间树
- **定义**：用于存储区间并支持区间重叠查询的数据结构
- **说明**：线段树是区间特的例；区间树可以 O(log n + k) 找出与查询区间重叠的所有 k 个区间
- **相关**：Segment Tree（线段树）、Range Query（区间查询）
### Lazy Propagation / 懒惰传播
- **英文**：Lazy Propagation
- **中文**：懒惰传播
- **定义**：线段树优化技术，区间更新时推迟子节点更新直到需要
- **说明**：懒惰传播使区间更新复杂度降为 O(log n)；维护 lazy tag 标记未下推的更新；查询和更新时下推（push down）
- **相关**：Segment Tree（线段树）、Range Update（区间更新）
### LCA (Lowest Common Ancestor) / 最近公共祖先
- **发音**：/ɛl-siː-eɪ/
- **中文**：最近公共祖先
- **定义**：树中两个节点的最深的公共祖先节点
- **说明**：求 LCA 方法：朴素法 O(h)、倍增法（Binary Lifting）O(log n) 预处理 O(n log n)、Tarjan 离线法 O(n+Q)、欧拉序列 + RMQ O(n log n)
- **相关**：Tree（树）、Binary Lifting（倍增法）、RMQ（区间最小值查询）
### Monotonic Queue / 单调队列
- **中文**：单调队列
- **定义**：队列内元素保持单调递增或递减顺序的特殊队列结构
- **说明**：单调队列用于滑动窗口最大值/最小值问题；使用双端队列（deque）实现
- **相关**：Queue（队列）、Sliding Window（滑动窗口）、Deque（双端队列）
### Monotonic Stack / 单调栈
- **中文**：单调栈
- **定义**：栈内元素保持单调递增或递减顺序的特殊栈结构
- **说明**：单调栈用于找下一个更大元素（Next Greater Element）、直方图最大矩形、接雨水等问题；每次操作弹出破坏单调性的元素；时间复杂度 O(n)
- **相关**：Stack（栈）、Monotonic Queue（单调队列）
### Persistent Data Structure / 持久化数据结构
- **中文**：持久化数据结构
- **定义**：保留所有历史版本的数据结构，修改操作产生新版本而不覆盖旧版本
- **说明**：部分持久化（可访问任意历史版本，只能修改最新版本）和完全持久化（可修改任意历史版本）；常用于函数式编程、时间旅行调试、版本控制
- **相关**：Immutable（不可变）、Functional Programming（函数式编程）
### RMQ (Range Minimum Query) / 区间最小值查询
- **发音**：/ɑːr-ɛm-kjuː/
- **中文**：区间最小值查询
- **定义**：在数组中查询任意区间的最小值的操作
- **说明**：RMQ 可用稀疏表（Sparse Table）O(n log n) 预处理 O(1) 查询；或用线段树 O(log n) 查询支持更新；LCA 可归约为 RMQ
- **相关**：Segment Tree（线段树）、Sparse Table（稀疏表）、LCA（最近公共祖先）
### Rolling Hash / 滚动哈希
- **中文**：滚动哈希
- **定义**：以 O(1) 时间从当前子串哈希值计算滑动一个字符后的新哈希值的技巧
- **说明**：滚动哈希用于 Rabin-Karp 字符串匹配算法、最长回文子串、重复子串检测；通常使用多项式哈希
- **相关**：Rabin-Karp Algorithm（Rabin-Karp 算法）、String Matching（字符串匹配）
### Sparse Table / 稀疏表
- **中文**：稀疏表
- **定义**：用于不可变数组上 RMQ 的静态数据结构，预处理 O(n log n)、查询 O(1)
- **说明**：基于倍增思想，st[i][j] 表示从 i 开始长度 2^j 的区间信息；适合多次查询无更新的场景
- **相关**：RMQ（区间最小值查询）、Binary Lifting（倍增法）
### Suffix Array / 后缀数组
- **音标**：/ˈsʌfɪks əˈreɪ/
- **中文**：后缀数组
- **定义**：存储字符串所有后缀按字典序排列后各后缀起始位置的有序数组
- **说明**：后缀数组可用于字符串匹配、最长公共前缀、最长重复子串等问题；构建 O(n log n) 或 O(n)；通常与 LCP（最长公共前缀）数组配合使用
- **相关**：Suffix Tree（后缀树）、LCP Array（最长公共前缀数组）、String（字符串）
### Suffix Tree / 后缀树
- **音标**：/ˈsʌfɪks triː/
- **中文**：后缀树
- **定义**：包含字符串所有后缀的压缩 Trie，每个叶子对应一个后缀
- **说明**：后缀树可在 O(m) 时间内查找长度为 m 的子串；构建 O(n)（Ukkonen 算法）；内存消耗大；应用：字符串匹配、最长重复子串、最长公共子串
- **相关**：Suffix Array（后缀数组）、Trie（前缀树）、String（字符串）
### Union-Find / 并查集
- **发音**：/ˈjuːnjən faɪnd/
- **中文**：并查集
- **定义**：同 Disjoint Set
- **相关**：Disjoint Set（并查集）
### Vector / 向量（动态数组）
- **音标**：/ˈvɛktər/
- **中文**：向量
- **定义**：C++ STL 中动态数组的实现
- **说明**：vector 在连续内存中存储，支持 O(1) 尾插入（均摊），O(1) 随机访问；扩容策略通常为 1.5x 或 2x；size() 返回元素数，capacity() 返回容量
- **相关**：Dynamic Array（动态数组）、ArrayList

