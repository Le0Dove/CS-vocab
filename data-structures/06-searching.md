# 06. 搜索与哈希 (Searching & Hashing)
### Binary Search / 二分查找
- **音标**：/ˈbaɪnəri sɜːrtʃ/
- **中文**：二分查找
- **定义**：在有序数组中，每次将搜索范围减半的查找算法
- **说明**：时间复杂度 O(log n)；必须用于有序数组；寻找左侧边界、右侧边界、精确匹配的变体；mid 计算需避免溢出（用 lo + (hi-lo)//2）
- **相关**：Search Algorithm（搜索算法）、Sorted Array（有序数组）、Divide and Conquer（分治）
- **例句**：Binary search reduces the search space by half at each step.
### Bloom Filter / 布隆过滤器
- **音标**：/bluːm ˈfɪltər/
- **中文**：布隆过滤器
- **定义**：概率性数据结构，用于高效判断元素是否可能存在于集合中
- **说明**：布隆过滤器使用多个哈希函数在位向量上标记；可能误报（False Positive），但不会漏报（False Negative）；空间效率极高；Redis、HBase、Chrome 恶意网址检测中使用
- **相关**：Hash Function（哈希函数）、Bit Vector（位向量）、Set（集合）
- **例句**：A Bloom filter can answer "is this element in the set" with some false positive probability.
### Chaining / 链地址法
- **音标**：/ˈtʃeɪnɪŋ/
- **中文**：链地址法
- **定义**：哈希表冲突解决方法，每个桶维护一个链表（或其他结构）存储冲突元素
- **说明**：链地址法负载因子可超过 1；最坏查找 O(n)，平均 O(1)；Java HashMap 使用链地址法（链表超出阈值转红黑树）
- **同义词**：Separate Chaining（分离链接法）
- **相关**：Open Addressing（开放寻址）、Hash Table（哈希表）
### Collision / 冲突
- **音标**：/kəˈlɪʒn/
- **中文**：冲突
- **定义**：两个不同的键通过哈希函数映射到同一索引的现象
- **说明**：冲突不可避免（鸽巢原理）；解决方法：链地址法、开放寻址法；冲突率影响哈希表性能
- **相关**：Hash Table（哈希表）、Collision Resolution（冲突解决）
### Consistent Hashing / 一致性哈希
- **中文**：一致性哈希
- **定义**：一种分布式哈希方案，增加或减少节点时只影响少量键的映射
- **说明**：一致性哈希将哈希空间组织成环形；用虚拟节点（Virtual Node）解决数据倾斜；广泛用于分布式缓存（Memcached、Redis Cluster）、CDN
- **相关**：Hash Ring（哈希环）、Load Balancing（负载均衡）、Distributed System（分布式系统）
### Exponential Search / 指数查找
- **中文**：指数查找
- **定义**：先用指数增长步长确定搜索范围，再用二分查找精确定位的算法
- **说明**：时间复杂度 O(log n)；适合无界数组或搜索范围未知的场景；步长从 1 开始翻倍
- **同义词**：Galloping Search
- **相关**：Binary Search（二分查找）、Interpolation Search（插值查找）
### Hash Code / 哈希码
- **中文**：哈希码
- **定义**：哈希函数计算出的整数值，用于确定键在哈希表中的存储位置
- **说明**：Java 中 hashCode() 方法返回对象的哈希码；equals() 和 hashCode() 契约：相等对象必须同哈希码
- **相关**：Hash Function（哈希函数）、Hash Table（哈希表）
### Hash Function / 哈希函数
- **音标**：/hæʃ ˈfʌŋkʃn/
- **中文**：哈希函数
- **定义**：将任意大小数据映射为固定大小值的函数
- **说明**：好的哈希函数应：均匀分布、计算快速、低碰撞率；常见：除留余数法、乘法哈希、MD5、SHA-256；密码哈希和非密码哈希用途不同
- **相关**：Hash Table（哈希表）、Hash Collision（哈希冲突）、Hash Code（哈希码）
### Hash Table / 哈希表
- **音标**：/hæʃ ˈteɪbl/
- **中文**：哈希表
- **定义**：通过哈希函数将键映射到数组索引，实现 O(1) 平均时间查找、插入和删除的数据结构
- **说明**：哈希表核心参数：负载因子（Load Factor）、桶数（Buckets）；空间换时间；最坏 O(n)；Java HashMap、Python dict、C++ unordered_map
- **同义词**：Hash Map、Dictionary（字典）、Associative Array（关联数组）
- **相关**：Hash Function（哈希函数）、Collision（冲突）、Load Factor（负载因子）
- **例句**：A hash table provides O(1) average time complexity for insert, delete, and lookup operations.
### Interpolation Search / 插值查找
- **中文**：插值查找
- **定义**：二分查找的变种，根据键值大小估计查找位置而非直接取中点
- **说明**：平均时间复杂度 O(log log n)（均匀分布），最坏 O(n)；公式：pos = lo + ((x-a[lo])*(hi-lo)/(a[hi]-a[lo]))
- **相关**：Binary Search（二分查找）、Search Algorithm（搜索算法）
### Linear Probing / 线性探测
- **中文**：线性探测
- **定义**：开放寻址法的冲突解决方式，从冲突位置依次向后查找空位
- **说明**：探查序列：h(k)、h(k)+1、h(k)+2...；会出现聚集现象（clustering）；删除需要特殊标记（tombstone）防止查找中断
- **相关**：Quadratic Probing（平方探测）、Double Hashing（双重哈希）、Open Addressing（开放寻址）
### Load Factor / 负载因子
- **音标**：/loʊd ˈfæktər/
- **中文**：负载因子
- **定义**：哈希表中已存储元素数量与桶数量的比值 = n / capacity
- **说明**：负载因子超过阈值（通常 0.75）触发 rehash（扩容）；低负载因子空间浪费，高负载因子增加冲突；Java HashMap 默认负载因子 0.75
- **相关**：Hash Table（哈希表）、Rehash（重新哈希）
### Open Addressing / 开放寻址
- **音标**：/ˈoʊpən əˈdrɛsɪŋ/
- **中文**：开放寻址
- **定义**：哈希表冲突解决方法，所有元素存储在哈希表数组内，通过探查序列寻找空位
- **说明**：探查方法：线性探测（Linear Probing）、平方探测（Quadratic Probing）、双重哈希（Double Hashing）；负载因子不能超过 1
- **相关**：Chaining（链地址法）、Hash Table（哈希表）、Probing（探测）
### Quadratic Probing / 平方探测
- **中文**：平方探测
- **定义**：开放寻址法的冲突解决方式，探查步长以平方增长
- **说明**：探查序列：h(k)+1²、h(k)+2²、h(k)+3²...；避免线性探测的聚集问题；表大小应为素数确保能探查所有位置
- **相关**：Linear Probing（线性探测）、Double Hashing（双重哈希）、Open Addressing（开放寻址）
### Rehash / 重新哈希
- **中文**：重新哈希
- **定义**：哈希表扩容或缩容时，重新计算所有元素的哈希值并放入新数组的过程
- **说明**：Rehash 时间复杂度 O(n)；扩容通常为 2x，避免频繁 rehash；Python dict 使用 1:2 到 2:3 之间的半动态扩容
- **相关**：Hash Table（哈希表）、Load Factor（负载因子）
### Search Algorithm / 搜索算法
- **中文**：搜索算法
- **定义**：在数据结构中查找特定目标元素的算法
- **说明**：搜索算法分为：线性查找（无序数据）、二分查找（有序数据）、哈希查找（键值）、树查找（BST/Trie）、图搜索（DFS/BFS）
- **相关**：Binary Search（二分查找）、Linear Search（线性查找）、Lookup（查找）
### Ternary Search / 三分查找
- **中文**：三分查找
- **定义**：每次将搜索区间分为三部分，缩小搜索范围的查找算法
- **说明**：用于查找单峰函数（Unimodal Function）的极值点；用于二分查找的变体；时间复杂度 O(log n)
- **相关**：Binary Search（二分查找）、Unimodal Function（单峰函数）
