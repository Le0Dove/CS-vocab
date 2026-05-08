# 03. 网络层 (Network Layer)
### Anycast / 任播
- **中文**：任播
- **定义**：将数据发送给一组节点中最近的一个的通信方式
- **说明**：任播使用相同 IP 地址分配给多个节点，路由到拓扑距离最近的节点；CDN 和 DNS 根服务器使用任播
- **相关**：Unicast（单播）、Multicast（多播）、CDN
### Autonomous System (AS) / 自治系统
- **中文**：自治系统
- **定义**：由单一组织管理的一组 IP 网络和路由器，使用统一的路由策略
- **说明**：每个 AS 有唯一 ASN；分为 AS 内路由（IGP：OSPF、RIP）和 AS 间路由（EGP：BGP）；互联网由数万个 AS 组成
- **相关**：BGP、OSPF、IGP、EGP
### BGP (Border Gateway Protocol) / 边界网关协议
- **发音**：/biː-dʒiː-piː/
- **中文**：边界网关协议
- **定义**：互联网核心路由协议，在自治系统之间交换路由信息
- **说明**：BGP 是路径向量协议（Path Vector Protocol）；基于策略（Policy-based）而非纯度量；通告 AS 路径属性；BGP 劫持是严重安全问题
- **相关**：Autonomous System（自治系统）、EGP、Route（路由）
### CIDR (Classless Inter-Domain Routing) / 无类别域间路由
- **音标**：/ˈsaɪdər/
- **中文**：无类别域间路由
- **定义**：不固定 IP 地址类而使用前缀长度表示的 IP 分配和路由方法
- **说明**：格式：IP/前缀长度（如 192.168.1.0/24）；支持任意长度子网划分；替代有类别寻址
- **相关**：Subnet Mask（子网掩码）、IP Address（IP 地址）、VLSM
### Default Gateway / 默认网关
- **中文**：默认网关
- **定义**：当路由表中无特定条目时发往的下一跳地址
- **说明**：主机配置默认网关 = 路由器的接口地址；默认路由 0.0.0.0/0
- **相关**：Router（路由器）、Routing Table（路由表）
### DHCP (Dynamic Host Configuration Protocol) / 动态主机配置协议
- **发音**：/diː-eɪtʃ-siː-piː/
- **中文**：动态主机配置协议
- **定义**：自动为网络设备分配 IP 地址、子网掩码、默认网关、DNS 等配置的协议
- **说明**：DORA 四步：Discover → Offer → Request → Acknowledge；DHCP 服务器管理地址池和租约
- **相关**：IP Address（IP 地址）、DNS、BOOTP
### Distance Vector Routing / 距离向量路由
- **中文**：距离向量路由
- **定义**：每个路由器向邻居通告自己到各目的地的距离（跳数），基于贝尔曼-福特算法的路由策略
- **说明**：RIP 使用距离向量算法；简单但收敛慢；可能出现计数到无穷（Count-to-Infinity）问题
- **相关**：Link State Routing（链路状态路由）、RIP、Routing Protocol（路由协议）
### EGP (Exterior Gateway Protocol) / 外部网关协议
- **中文**：外部网关协议
- **定义**：在自治系统之间交换路由信息的路由协议
- **说明**：BGP 是唯一的 EGP；关注策略而非纯粹效率
- **相关**：IGP（内部网关协议）、BGP、Autonomous System（自治系统）
### Fragmentation / 分片
- **中文**：分片
- **定义**：将过大不能通过某链路的 IP 数据包拆分为更小片的过程
- **说明**：IPv4 路由器可分片，目的主机重组；IPv6 禁止中间路由器分片，源端自行分片；分片字段：Identification、Flags（DF/MF）、Fragment Offset
- **相关**：MTU（最大传输单元）、Reassembly（重组）、IPv4、IPv6
### ICMP (Internet Control Message Protocol) / 互联网控制消息协议
- **发音**：/aɪ-siː-ɛm-piː/
- **中文**：互联网控制消息协议
- **定义**：用于在网络设备间传递错误报告和诊断信息的协议
- **说明**：ping 使用 ICMP Echo Request/Reply；traceroute 使用 ICMP Time Exceeded；类型：目的不可达、超时、重定向等
- **相关**：ping、traceroute、IP
### IGP (Interior Gateway Protocol) / 内部网关协议
- **中文**：内部网关协议
- **定义**：在自治系统内部交换路由信息的路由协议
- **说明**：IGP 分为距离向量协议（RIP、EIGRP）和链路状态协议（OSPF、IS-IS）
- **相关**：EGP（外部网关协议）、OSPF、RIP
### IP Address / IP 地址
- **中文**：IP 地址
- **定义**：分配给网络中每个设备的逻辑地址，用于在网络层标识和定位设备
- **说明**：IPv4: 32 位（如 192.168.1.1）；IPv6: 128 位（如 2001:db8::1）；分为网络部分和主机部分
- **相关**：IPv4、IPv6、Subnet Mask（子网掩码）
### IPv4 / 互联网协议第 4 版
- **中文**：IPv4
- **定义**：32 位地址空间的互联网协议版本
- **说明**：IPv4 地址已耗尽（IANA 2011 年分配完毕）；NAT 缓解耗尽；头部 20-60 字节；约 43 亿个地址
- **相关**：IPv6、NAT（网络地址转换）、IP Address
### IPv6 / 互联网协议第 6 版
- **中文**：IPv6
- **定义**：128 位地址空间的互联网协议版本
- **说明**：IPv6 地址空间极大（3.4×10³⁸）；头部简化到 40 字节；内置 IPsec；无广播、无分片；表示：8 组 16 进制如 2001:db8::1
- **相关**：IPv4、IP Address、IPsec
### Link State Routing / 链路状态路由
- **中文**：链路状态路由
- **定义**：每个节点掌握整个网络拓扑（链路状态数据库），使用 Dijkstra 算法计算最短路径的路由策略
- **说明**：OSPF 和 IS-IS 使用链路状态路由；收敛快、无环路；每路由器泛洪（Flooding）LSA 共享拓扑
- **相关**：Distance Vector Routing（距离向量路由）、OSPF、Dijkstra's Algorithm（Dijkstra 算法）
### Loopback / 环回
- **中文**：环回
- **定义**：将数据发送回本机的虚拟网络接口，地址通常为 127.0.0.1（IPv4）或 ::1（IPv6）
- **说明**：loopback 接口用于本地测试和诊断；localhost 域名解析到 127.0.0.1
- **相关**：localhost、127.0.0.1
### NAT (Network Address Translation) / 网络地址转换
- **音标**：/næt/
- **中文**：网络地址转换
- **定义**：将私有 IP 地址改写为公网 IP 地址的技术
- **说明**：SNAT（源 NAT）用于出站；DNAT（目的 NAT）/端口转发用于入站；NAPT（端口 NAT）使用端口区分不同内网主机；IPv6 的天然替代方案
- **相关**：Private IP（私有 IP）、Public IP（公网 IP）、PAT
### OSPF (Open Shortest Path First) / 开放最短路径优先
- **发音**：/oʊ-ɛs-piː-ɛf/
- **中文**：开放最短路径优先
- **定义**：链路状态内部网关路由协议，使用 Dijkstra 算法计算最短路径
- **说明**：OSPF 支持区域（Area）概念（Area 0 为骨干区域）；度量基于带宽；较 RIP 收敛更快、支持更大网络；广泛用于企业网络
- **相关**：Link State Routing（链路状态路由）、Dijkstra's Algorithm（Dijkstra 算法）、IGP
### ping
- **中文**：ping 命令
- **定义**：使用 ICMP Echo Request/Reply 测试主机可达性和 RTT 的网络诊断工具
- **说明**：ping 发送 ICMP 包测量往返时间；防火墙可能阻止 ICMP 导致 ping 不通但不代表不可达
- **相关**：ICMP、RTT（往返时间）、traceroute
### Prefix / 前缀
- **中文**：前缀
- **定义**：IP 地址的网络部分，用 CIDR 表示法（如 /24）指示长度
- **说明**：前缀长度决定了网络包含的 IP 地址范围；路由表根据最长前缀匹配（Longest Prefix Match）转发
- **相关**：CIDR、Subnet Mask（子网掩码）、IP Address
### Private IP / 私有 IP 地址
- **中文**：私有 IP 地址
- **定义**：只在内部网络使用、不直接在互联网上路由的 IP 地址
- **说明**：IPv4 私有地址段：10.0.0.0/8、172.16.0.0/12、192.168.0.0/16；通过 NAT 访问互联网
- **相关**：Public IP（公网 IP）、NAT（网络地址转换）
### Router / 路由器
- **中文**：路由器
- **定义**：工作在网络层的设备，根据 IP 地址和路由表将数据包转发到目的网络
- **说明**：路由器隔离广播域；通过路由协议（OSPF、BGP 等）学习路由；每个数据包独立选路（逐跳路由）；家庭路由器集成 NAT、DHCP、DNS 等功能
- **相关**：Routing Table（路由表）、Switch（交换机）、Packet（数据包）
### Routing Protocol / 路由协议
- **中文**：路由协议
- **定义**：路由器之间交换路由信息、计算最优路径的协议
- **说明**：分为 IGP（内部网关协议）和 EGP（外部网关协议）；指标：跳数、带宽、延迟、可靠性等
- **相关**：OSPF、BGP、RIP、Routing Table（路由表）
### Routing Table / 路由表
- **中文**：路由表
- **定义**：路由器或主机中存储的网络目的地与下一跳对应关系的数据表
- **说明**：路由表条目：目的网络、子网掩码、下一跳、接口；最长前缀匹配选择最优路由
- **相关**：Router（路由器）、Prefix（前缀）
### Subnet / 子网
- **中文**：子网
- **定义**：较大 IP 网络通过子网划分得到的逻辑子网络
- **说明**：子网掩码划分网络部分和主机部分；VLSM 支持可变长子网划分
- **相关**：Subnet Mask（子网掩码）、CIDR、IP Address
### Subnet Mask / 子网掩码
- **中文**：子网掩码
- **定义**：与 IP 地址按位与得到网络地址的 32 位掩码
- **说明**：子网掩码连续的 1 表示网络位，0 表示主机位；如 255.255.255.0 = /24；255.255.255.128 = /25
- **相关**：Subnet（子网）、CIDR、Prefix（前缀）
### TTL (Time to Live) / 生存时间
- **发音**：/tiː-tiː-ɛl/
- **中文**：生存时间
- **定义**：IP 数据包中的字段，每经过一跳减 1，减到 0 时丢弃
- **说明**：防止数据包无限循环；traceroute 利用 TTL 超时发现路径；默认值 64（Linux）、128（Windows）、255
- **相关**：Hop（跳）、traceroute、IP
