# 05. 排序算法 (Sorting Algorithms)
### Bubble Sort / 冒泡排序
- **音标**：/ˈbʌbl sɔːrt/
- **中文**：冒泡排序
- **定义**：重复遍历数组，比较相邻元素并交换顺序错误的对，直到全部有序的简单排序算法
- **说明**：时间复杂度 O(n²)；稳定排序；原地排序；实现简单但效率最低；优化：设置标志位提前终止（最好情况 O(n)）
- **相关**：Insertion Sort（插入排序）、Selection Sort（选择排序）、Comparison Sort（比较排序）
- **例句**：Bubble sort repeatedly swaps adjacent elements that are out of order.
### Bucket Sort / 桶排序
- **音标**：/ˈbʌkɪt sɔːrt/
- **中文**：桶排序
- **定义**：将元素分配到多个桶中，每个桶内单独排序，再按顺序合并的排序算法
- **说明**：时间复杂度平均 O(n+k)，最坏 O(n²)；最好情况下接近 O(n)；适合数据均匀分布的场景
- **相关**：Radix Sort（基数排序）、Counting Sort（计数排序）、Distribution Sort（分配排序）
### Comparison Sort / 比较排序
- **中文**：比较排序
- **定义**：仅通过元素间比较来确定排序顺序的排序算法
- **说明**：任何比较排序的最坏时间复杂度下界为 Ω(n log n)；常见比较排序：快速排序、归并排序、堆排序、冒泡排序
- **相关**：Non-comparison Sort（非比较排序）、Lower Bound（下界）
### Counting Sort / 计数排序
- **音标**：/ˈkaʊntɪŋ sɔːrt/
- **中文**：计数排序
- **定义**：通过统计每个值出现的次数来确定元素位置的线性时间排序算法
- **说明**：时间复杂度 O(n+k)，k 为值域范围；稳定排序；非比较排序；要求数据是整数且范围不宜太大（过大浪费空间）
- **相关**：Bucket Sort（桶排序）、Radix Sort（基数排序）、Non-comparison Sort（非比较排序）
### External Sorting / 外部排序
- **中文**：外部排序
- **定义**：数据量太大无法全部加载到内存，需要借助外存（磁盘）进行排序的算法
- **说明**：外部排序通常使用 K 路归并排序（K-way Merge）；将数据分块读入内存排序写回，再多路归并；用于数据库、大数据处理
- **相关**：Merge Sort（归并排序）、K-way Merge（K 路归并）
### Heap Sort / 堆排序
- **音标**：/hiːp sɔːrt/
- **中文**：堆排序
- **定义**：利用堆数据结构实现的比较排序算法
- **说明**：时间复杂度 O(n log n)；原地排序；不稳定排序；步骤：建堆 O(n)，重复提取堆顶 O(n log n)
- **相关**：Heap（堆）、Priority Queue（优先队列）、Selection Sort（选择排序）
- **例句**：Heap sort is an O(n log n) comparison-based sorting algorithm.
### Insertion Sort / 插入排序
- **音标**：/ɪnˈsɜːrʃn sɔːrt/
- **中文**：插入排序
- **定义**：将未排序元素逐个插入到已排序序列的正确位置的排序算法
- **说明**：时间复杂度 O(n²)，最好 O(n)（已排序）；稳定排序；原地排序；对小规模数据或接近有序数据高效；Shell Sort 是其改进版
- **相关**：Selection Sort（选择排序）、Bubble Sort（冒泡排序）、Shell Sort（希尔排序）
- **例句**：Insertion sort is efficient for small or nearly sorted datasets.
### K-way Merge / K 路归并
- **中文**：K 路归并
- **定义**：将 K 个有序序列合并为一个有序序列的方法
- **说明**：使用最小堆可以在 O(N log K) 时间内完成 K 路归并；外部排序和数据库排序的核心操作
- **相关**：Merge Sort（归并排序）、External Sorting（外部排序）、Heap（堆）
### Merge Sort / 归并排序
- **音标**：/mɜːrdʒ sɔːrt/
- **中文**：归并排序
- **定义**：基于分治策略，将数组递归分成两半，排序后再合并的比较排序算法
- **说明**：时间复杂度 O(n log n)；稳定排序；需要 O(n) 额外空间（非原地）；适合大数据量和链表排序；归并过程是稳定合并
- **相关**：Quick Sort（快速排序）、Divide and Conquer（分治）、Stable（稳定的）
- **例句**：Merge sort guarantees O(n log n) time complexity in all cases.
### Non-comparison Sort / 非比较排序
- **中文**：非比较排序
- **定义**：不通过元素比较，利用数据特殊性质进行排序的算法
- **说明**：非比较排序可以突破 Ω(n log n) 下界达到 O(n)；常见：计数排序、基数排序、桶排序；要求数据满足特定条件（整数、范围小）
- **相关**：Comparison Sort（比较排序）、Counting Sort（计数排序）、Radix Sort（基数排序）
### Partition / 分区
- **音标**：/pɑːrˈtɪʃn/
- **中文**：分区
- **定义**：快速排序的核心操作，选定枢轴后将数组分为小于和大于枢轴的两部分
- **说明**：Lomuto 分区（简单但效率略低）和 Hoare 分区（原始实现，效率高）；分区后枢轴元素位于最终排序位置
- **相关**：Pivot（枢轴）、Quick Sort（快速排序）
### Pivot / 枢轴
- **音标**：/ˈpɪvət/
- **中文**：枢轴
- **定义**：快速排序中选定的基准元素，用于划分数组
- **说明**：枢轴选择影响快速排序性能；策略：固定首/尾（最差 O(n²)）、随机化、三数取中（Median of Three）；好的枢轴使分区均衡
- **相关**：Partition（分区）、Quick Sort（快速排序）
### Quick Sort / 快速排序
- **音标**：/kwɪk sɔːrt/
- **中文**：快速排序
- **定义**：基于分治策略，选择枢轴将数组分区后递归排序的比较排序算法
- **说明**：平均时间复杂度 O(n log n)，最坏 O(n²)；原地排序；不稳定排序；实际中最快的通用排序算法之一；大多数语言标准库使用其变种
- **相关**：Merge Sort（归并排序）、Partition（分区）、Pivot（枢轴）
- **例句**：Quick sort is often faster in practice than other O(n log n) algorithms.
### Radix Sort / 基数排序
- **音标**：/ˈreɪdɪks sɔːrt/
- **中文**：基数排序
- **定义**：按数字的每一位（从最低位或最高位）依次进行稳定排序的线性时间排序算法
- **说明**：LSD（最低位优先）和 MSD（最高位优先）；时间复杂度 O(d·(n+k))，d 为位数；要求稳定子排序（通常用计数排序）；适合定长整数或字符串
- **相关**：Counting Sort（计数排序）、Bucket Sort（桶排序）、Non-comparison Sort（非比较排序）
### Selection Sort / 选择排序
- **音标**：/sɪˈlekʃn sɔːrt/
- **中文**：选择排序
- **定义**：每次从未排序部分选择最小（或最大）元素，放到已排序部分末尾的排序算法
- **说明**：时间复杂度 O(n²)；原地排序；不稳定排序；交换次数少（O(n)），但比较次数固定；简单但效率低于插入排序
- **相关**：Insertion Sort（插入排序）、Bubble Sort（冒泡排序）
### Shell Sort / 希尔排序
- **音标**：/ʃɛl sɔːrt/
- **中文**：希尔排序
- **定义**：插入排序的改进，先对远距离元素排序（间隔递减），最终以间隔 1 做插入排序
- **说明**：时间复杂度取决于间隔序列（Gap Sequence）；常用间隔序列：Hibbard (O(n^1.5))、Sedgewick (O(n^4/3))；原地排序；不稳定排序
- **同义词**：Diminishing Increment Sort
- **相关**：Insertion Sort（插入排序）、Gap Sequence（间隔序列）
### Sorted / 有序的
- **音标**：/ˈsɔːrtɪd/
- **中文**：有序的
- **定义**：数据按某种顺序（升序或降序）排列的状态
- **说明**：有序数组可以用二分查找提升效率；有序性是很多算法优化的前提
- **相关**：Sorting（排序）、Ascending（升序）、Descending（降序）
### Sorting / 排序
- **音标**：/ˈsɔːrtɪŋ/
- **中文**：排序
- **定义**：将一组数据元素按指定顺序（升序或降序）重新排列的过程
- **说明**：排序是最基础、最常用的算法操作；内部排序（内存中）和外部排序（外存）；稳定 vs 不稳定；比较 vs 非比较
- **相关**：Ascending（升序）、Descending（降序）、Ordering（顺序）
- **例句**：Sorting is one of the most fundamental operations in computer science.
### Timsort / Timsort
- **音标**：/tɪm sɔːrt/
- **中文**：Timsort
- **定义**：由 Tim Peters 设计的混合排序算法，结合归并排序和插入排序
- **说明**：Timsort 是 Python（sorted/list.sort）、Java（Arrays.sort(Object[])）、Android 的默认排序算法；利用数据中已有的连续有序段（Run）；稳定排序；时间复杂度 O(n log n)，最好 O(n)
- **相关**：Merge Sort（归并排序）、Insertion Sort（插入排序）

