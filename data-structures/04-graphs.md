# 04. 图结构 (Graph Structures)

### Acyclic Graph / 无环图
- **音标**：/eɪˈsaɪklɪk ɡræf/
- **中文**：无环图
- **定义**：不包含任何环（cycle）的图
- **说明**：无向无环图是森林；有向无环图（DAG）常用于任务调度、表达式依赖分析、版本控制（Git）
- **相关**：DAG（有向无环图）、Cycle（环）、Tree（树）

### Adjacency List / 邻接表
- **音标**：/əˈdʒeɪsənsi lɪst/
- **中文**：邻接表
- **定义**：用链表或数组存储每个顶点的邻接顶点的图表示方法
- **说明**：邻接表空间复杂度 O(V+E)，适合稀疏图；可以快速遍历某顶点的所有邻接点；C++ vector<vector<int>>、Python 字典列表常用实现
- **相关**：Adjacency Matrix（邻接矩阵）、Graph（图）

### Adjacency Matrix / 邻接矩阵
- **音标**：/əˈdʒeɪsənsi ˈmeɪtrɪks/
- **中文**：邻接矩阵
- **定义**：用二维矩阵表示图，matrix[i][j] 表示顶点 i 到 j 的边信息
- **说明**：邻接矩阵空间复杂度 O(V²)，适合稠密图；查询两点是否有边为 O(1)；无权图用 0/1，有权图用权重值
- **相关**：Adjacency List（邻接表）、Graph（图）

### Bellman-Ford Algorithm / Bellman-Ford 算法
- **音标**：/ˈbelmən fɔːrd ˈælɡərɪðəm/
- **中文**：Bellman-Ford 算法
- **定义**：可处理负权边的单源最短路径算法
- **说明**：时间复杂度 O(VE)；通过 V-1 轮松弛操作逐步逼近最短路径；可检测负权环；适合稀疏图和含负权边的图
- **相关**：Dijkstra's Algorithm（Dijkstra 算法）、Shortest Path（最短路径）、Relaxation（松弛）

### Bipartite Graph / 二分图
- **音标**：/baɪˈpɑːrtaɪt ɡræf/
- **中文**：二分图
- **定义**：顶点可分为两个不相交集合，每条边的两个端点分别属于不同集合的图
- **说明**：二分图可用 BFS/DFS 染色判断（两种颜色）；应用：二分图匹配、任务分配；不含奇数长度环
- **相关**：Matching（匹配）、Graph Coloring（图着色）

### Bridge / 桥
- **音标**：/brɪdʒ/
- **中文**：桥
- **定义**：删除后会使图变得不连通的边
- **说明**：桥在通信网络和道路网络中代表关键链路；可用 Tarjan 算法在 O(V+E) 时间内找出所有桥
- **同义词**：Cut Edge（割边）
- **相关**：Articulation Point（割点）、Connected Component（连通分量）

### Connected Component / 连通分量
- **音标**：/kəˈnektɪd kəmˈpoʊnənt/
- **中文**：连通分量
- **定义**：无向图中极大连通子图，子图中任意两点可达
- **说明**：求连通分量可用 DFS/BFS 或并查集（Union-Find）；强连通分量（SCC）是有向图中的对应概念
- **相关**：Strongly Connected Component（强连通分量）、Union-Find（并查集）

### Cut Vertex / 割点
- **音标**：/kʌt ˈvɜːrtɛks/
- **中文**：割点
- **定义**：删除后会使图变得不连通的顶点
- **说明**：割点是网络中的关键节点；可用 Tarjan 算法在 O(V+E) 时间内找出所有割点；与桥（Bridge）概念类似
- **同义词**：Articulation Point（关节点）
- **相关**：Bridge（桥）、Connected Component（连通分量）

### Cycle / 环
- **音标**：/ˈsaɪkl/
- **中文**：环
- **定义**：图中起点和终点相同的路径，路径上至少有一条边
- **说明**：环可分为简单环（不重复顶点）和非简单环；检测环可用 DFS 或并查集；DAG（有向无环图）不含环
- **相关**：Acyclic Graph（无环图）、DAG（有向无环图）

### DAG (Directed Acyclic Graph) / 有向无环图
- **发音**：/dæɡ/
- **中文**：有向无环图
- **定义**：有方向边且不包含任何环的图
- **说明**：DAG 可以进行拓扑排序；应用：任务调度、编译依赖、表达式求值、版本控制（Git 提交历史）、区块链；是树结构的泛化
- **相关**：Topological Sort（拓扑排序）、Tree（树）

### Degree / 度
- **音标**：/dɪˈɡriː/
- **中文**：度
- **定义**：与顶点相连的边的数量
- **说明**：无向图中度 = 邻接边数；有向图分为入度（In-degree，指向该点的边数）和出度（Out-degree，从该点出发的边数）；所有顶点度数之和 = 2E
- **相关**：In-degree（入度）、Out-degree（出度）、Vertex（顶点）

### Dijkstra's Algorithm / Dijkstra 算法
- **音标**：/ˈdaɪkstrəz ˈælɡərɪðəm/
- **中文**：Dijkstra 算法
- **定义**：求解非负权图中单源最短路径的经典贪心算法
- **说明**：时间复杂度 O((V+E)log V)（用优先队列）；每次选择距离源点最近的未访问顶点进行松弛；不能处理负权边；应用：地图导航、网络路由
- **相关**：Shortest Path（最短路径）、Greedy Algorithm（贪心算法）、Priority Queue（优先队列）
- **例句**：Dijkstra's algorithm is widely used in GPS navigation systems.

### Directed Graph / 有向图
- **音标**：/dəˈrektɪd ɡræf/
- **中文**：有向图
- **定义**：边有方向的图，边从一个顶点指向另一个顶点
- **说明**：有向图的边也称为弧（Arc）；有向图的路径遵循边的方向；入度和出度概念只适用于有向图
- **同义词**：Digraph
- **相关**：Undirected Graph（无向图）、DAG（有向无环图）

### Edge / 边
- **音标**：/ɛdʒ/
- **中文**：边
- **定义**：连接图中两个顶点的线，可以是有向的或无向的
- **说明**：边可以有权重（Weight）表示代价或距离；无向图的边 (u, v) 和 (v, u) 相同；有向图的边 <u, v> 有方向
- **同义词**：Arc（弧，有向图）、Link（连接）
- **相关**：Vertex（顶点）、Weight（权重）

### Floyd-Warshall Algorithm / Floyd-Warshall 算法
- **音标**：/flɔɪd ˈwɔːrʃɔːl ˈælɡərɪðəm/
- **中文**：Floyd-Warshall 算法
- **定义**：求解所有顶点对之间最短路径的动态规划算法
- **说明**：时间复杂度 O(V³)，适合稠密图；基于中间顶点 k 逐步优化最短路径；可以检测负权环；代码简洁（三重循环）
- **同义词**：Floyd's Algorithm
- **相关**：Shortest Path（最短路径）、Dynamic Programming（动态规划）

### Graph / 图
- **音标**：/ɡræf/
- **中文**：图
- **定义**：由顶点（Vertex）集合和边（Edge）集合组成的数据结构，用于表示多对多关系
- **说明**：图分为有向图和无向图；表示方式：邻接矩阵、邻接表；遍历方式：DFS、BFS；应用：社交网络、地图、网络拓扑、依赖关系
- **相关**：Vertex（顶点）、Edge（边）、Tree（树）

### In-degree / 入度
- **音标**：/ɪn dɪˈɡriː/
- **中文**：入度
- **定义**：有向图中指向该顶点的边的数量
- **说明**：拓扑排序从入度为 0 的顶点开始；所有顶点入度之和 = 出度之和 = E
- **相关**：Out-degree（出度）、Degree（度）、Topological Sort（拓扑排序）

### Kruskal's Algorithm / Kruskal 算法
- **音标**：/ˈkrʌskəlz ˈælɡərɪðəm/
- **中文**：Kruskal 算法
- **定义**：基于贪心策略的最小生成树算法，按边权从小到大选择边
- **说明**：时间复杂度 O(E log E)（排序边）；使用并查集判断加入边是否形成环；适合稀疏图
- **相关**：Minimum Spanning Tree（最小生成树）、Union-Find（并查集）、Prim's Algorithm（Prim 算法）

### Minimum Spanning Tree (MST) / 最小生成树
- **音标**：/ˈmɪnɪməm ˈspænɪŋ triː/
- **中文**：最小生成树
- **定义**：连接图中所有顶点的边权之和最小的生成树
- **说明**：生成树包含 V-1 条边，无环，连通所有顶点；经典算法：Prim（适合稠密图）、Kruskal（适合稀疏图）；应用：网络设计、电路布线
- **同义词**：MST
- **相关**：Prim's Algorithm（Prim 算法）、Kruskal's Algorithm（Kruskal 算法）、Spanning Tree（生成树）

### Negative Cycle / 负权环
- **音标**：/ˈneɡətɪv ˈsaɪkl/
- **中文**：负权环
- **定义**：环上所有边权之和为负数的环
- **说明**：存在负权环的图没有最短路径定义（可以无限绕环减小距离）；Bellman-Ford 可以检测负权环；SPFA 算法也可检测
- **相关**：Bellman-Ford Algorithm（Bellman-Ford 算法）、Shortest Path（最短路径）

### Out-degree / 出度
- **音标**：/aʊt dɪˈɡriː/
- **中文**：出度
- **定义**：有向图中从该顶点出发的边的数量
- **说明**：出度为 0 的顶点是汇点（sink）；所有顶点出度之和 = E
- **相关**：In-degree（入度）、Degree（度）

### Path / 路径
- **音标**：/pæθ/
- **中文**：路径
- **定义**：图中从一个顶点到另一个顶点经过的顶点和边的序列
- **说明**：简单路径（Simple Path）：不重复顶点；路径长度可以是边数或权重和；最短路径是长度最小的路径
- **相关**：Shortest Path（最短路径）、Cycle（环）

### Prim's Algorithm / Prim 算法
- **音标**：/prɪmz ˈælɡərɪðəm/
- **中文**：Prim 算法
- **定义**：基于贪心策略的最小生成树算法，从单一顶点开始逐步扩展树
- **说明**：时间复杂度 O((V+E)log V)（用优先队列）；类似 Dijkstra，但维护的是到树的最小距离而非到源点的距离；适合稠密图
- **相关**：Minimum Spanning Tree（最小生成树）、Kruskal's Algorithm（Kruskal 算法）

### Relaxation / 松弛
- **音标**：/ˌriːlækˈseɪʃn/
- **中文**：松弛
- **定义**：最短路径算法中，检查并更新某顶点到源点的最短距离的操作
- **说明**：松弛操作：如果 dist[u] + w(u,v) < dist[v]，则更新 dist[v]；Dijkstra 和 Bellman-Ford 的核心操作
- **相关**：Dijkstra's Algorithm（Dijkstra 算法）、Bellman-Ford Algorithm（Bellman-Ford 算法）、Shortest Path（最短路径）

### Shortest Path / 最短路径
- **音标**：/ˈʃɔːrtɪst pæθ/
- **中文**：最短路径
- **定义**：图中两点之间边权之和最小的路径
- **说明**：单源最短路径：Dijkstra（非负权）、Bellman-Ford（可负权）；全源最短路径：Floyd-Warshall；应用：导航、网络路由、社交网络分析
- **相关**：Dijkstra's Algorithm（Dijkstra 算法）、Bellman-Ford Algorithm（Bellman-Ford 算法）、Relaxation（松弛）

### Spanning Tree / 生成树
- **音标**：/ˈspænɪŋ triː/
- **中文**：生成树
- **定义**：包含图中所有顶点的树，由 V-1 条边组成
- **说明**：连通图有多个生成树；生成树是图的极大连通无环子图；最小生成树（MST）是边权和最小的生成树
- **相关**：Minimum Spanning Tree（最小生成树）、Tree（树）

### Strongly Connected Component (SCC) / 强连通分量
- **音标**：/ˈstrɒŋli kəˈnektɪd kəmˈpoʊnənt/
- **中文**：强连通分量
- **定义**：有向图中极大强连通子图，子图中任意两顶点互相可达
- **说明**：求 SCC 算法：Kosaraju 算法（两次 DFS）、Tarjan 算法（一次 DFS）；应用：缩点（将 SCC 缩为一个点得到 DAG）、2-SAT
- **同义词**：SCC
- **相关**：Connected Component（连通分量）、DAG（有向无环图）

### Topological Sort / 拓扑排序
- **音标**：/ˌtɒpəˈlɒdʒɪkl sɔːrt/
- **中文**：拓扑排序
- **定义**：对有向无环图（DAG）的顶点进行线性排序，使得每条边的起点在终点之前
- **说明**：拓扑排序不唯一；算法：Kahn 算法（基于入度，BFS）或 DFS（后序遍历的逆序）；应用：任务调度、课程选修计划、编译顺序
- **相关**：DAG（有向无环图）、In-degree（入度）、Kahn's Algorithm（Kahn 算法）

### Undirected Graph / 无向图
- **音标**：/ʌndəˈrektɪd ɡræf/
- **中文**：无向图
- **定义**：边没有方向的图，边 (u, v) 和 (v, u) 等价
- **说明**：无向图中度 = 入度 = 出度；连通分量概念适用于无向图；最小生成树在无向图中定义
- **相关**：Directed Graph（有向图）、Edge（边）

### Vertex / 顶点
- **音标**：/ˈvɜːrtɛks/
- **中文**：顶点
- **定义**：图中的基本单元，也称为节点（Node）
- **说明**：顶点可以有属性（如权重、颜色、标签）；图通常记为 G = (V, E)，V 是顶点集，E 是边集
- **同义词**：Node（节点）
- **相关**：Edge（边）、Graph（图）

### Weight / 权重
- **音标**：/weɪt/
- **中文**：权重
- **定义**：边上标注的数值，表示代价、距离、容量等
- **说明**：权重可以是正数、负数或零；有权图（Weighted Graph）需要考虑权重进行最短路径、最小生成树等计算
- **相关**：Edge（边）、Weighted Graph（有权图）

### Weighted Graph / 有权图
- **音标**：/ˈweɪtɪd ɡræf/
- **中文**：有权图
- **定义**：边上带有权重值的图
- **说明**：有权图用于表示具有成本的网络；无权图可以视为所有权重为 1 的有权图
- **相关**：Weight（权重）、Unweighted Graph（无权图）

