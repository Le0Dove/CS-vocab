# 02. 物理层与数据链路层 (Physical & Data Link Layer)
### 5G
- **发音**：/faɪv dʒiː/
- **中文**：第五代移动通信
- **定义**：第五代移动通信技术标准
- **说明**：5G 特征：高带宽（eMBB，20Gbps）、低延迟（URLLC，1ms）、大连接（mMTC）；频段：Sub-6GHz 和 mmWave（毫米波）；网络切片技术
- **相关**：4G/LTE、Cellular Network（蜂窝网络）、mmWave（毫米波）
### Access Point (AP) / 接入点
- **中文**：接入点
- **定义**：连接无线设备和有线网络的网络设备，通常指 Wi-Fi 热点
- **说明**：AP 接收无线信号转换为有线帧；家用路由器集成了 AP、路由器、交换机功能；企业 AP 由无线控制器集中管理
- **相关**：Wi-Fi、Wireless Router（无线路由器）、WLAN
### ARP (Address Resolution Protocol) / 地址解析协议
- **发音**：/ɑːrp/
- **中文**：地址解析协议
- **定义**：将 IP 地址解析为 MAC 地址的协议
- **说明**：ARP 在局域网内广播查询"谁有这 IP），目标主机回复 MAC 地址；ARP 缓存存储映射关系；ARP 欺骗（Spoofing）是常见攻击方式
- **相关**：MAC Address（MAC 地址）、IP Address（IP 地址）、ARP Spoofing
### Bridge / 网桥
- **中文**：网桥
- **定义**：连接两个 LAN 段的二层设备，根据 MAC 地址转发帧
- **说明**：网桥隔离冲突域但共享广播域；学习地址表决定转发或过滤；现代交换机是多端口网桥
- **相关**：Switch（交换机）、Collision Domain（冲突域）
### Byte Stuffing / 字节填充
- **中文**：字节填充
- **定义**：在数据中插入特殊转义字节以区分控制字符和数据的成帧技术
- **说明**：当数据中出现帧定界符时，在其前插入转义字符（ESC）；PPP 协议使用字节填充；接收端去除填充还原数据
- **同义词**：Character Stuffing（字符填充）
- **相关**：Bit Stuffing（比特填充）、Framing（成帧）、PPP
### Cell / 小区（蜂窝）
- **中文**：小区
- **定义**：蜂窝网络中最基本的无线覆盖单元
- **说明**：每个小区由一个基站（Base Station）覆盖；频率可跨区复用
- **相关**：Cellular Network（蜂窝网络）、Base Station（基站）
### Cellular Network / 蜂窝网络
- **中文**：蜂窝网络
- **定义**：将服务区划分为多个小区，每个小区由基站覆盖的移动通信网络架构
- **说明**：蜂窝网络通过小区间频率复用提高频谱效率；切换（Handover）支持移动用户跨小区通信；从 1G 到 5G 迭代
- **相关**：Base Station（基站）、Handover（切换）、4G、5G
### Checksum / 校验和
- **中文**：校验和
- **定义**：对数据段进行数学运算（如求和取反）得到的错误检测码
- **说明**：UDP/TCP/IP 使用校验和检测传输错误；简单但检测能力有限；与 CRC 相比，校验和更快但检错能力弱
- **相关**：CRC（循环冗余校验）、Error Detection（错误检测）
### Collision / 冲突
- **中文**：冲突
- **定义**：共享介质上两个节点同时发送数据导致信号叠加、数据丢失
- **说明**：Hub 连接的半双工以太网可能发生冲突；CSMA/CD 处理冲突；交换机消除了冲突域
- **相关**：CSMA/CD、Collision Domain（冲突域）、Half Duplex
### Collision Domain / 冲突域
- **中文**：冲突域
- **定义**：可能发生信号冲突的网络区域
- **说明**：Hub 连接的所有端口在同一冲突域；交换机每个端口是独立冲突域
- **相关**：Broadcast Domain（广播域）、Collision（冲突）、Hub
### CRC (Cyclic Redundancy Check) / 循环冗余校验
- **发音**：/siː-ɑːr-siː/
- **中文**：循环冗余校验
- **定义**：使用多项式除法生成校验码的错误检测技术
- **说明**：CRC 能检测多位错误、突发错误；以太网 FCS 字段使用 CRC-32；比校验和检错能力强
- **相关**：Checksum（校验和）、Error Detection（错误检测）、FCS
### CSMA/CD (Carrier Sense Multiple Access with Collision Detection) / 载波监听多路访问/冲突检测
- **中文**：载波监听多路访问/冲突检测
- **定义**：以太网使用的介质访问控制协议，先侦听再发送，遇到冲突则退避重试
- **说明**：标准 IEEE 802.3；工作时序：① 侦听载波 → ② 信道闲则发送 → ③ 检测冲突 → ④ 冲突后二进制指数退避（Binary Exponential Backoff）；全双工交换机不需要 CSMA/CD
- **相关**：Ethernet（以太网）、Collision（冲突）、CSMA/CA
### Destination MAC / 目的 MAC 地址
- **中文**：目的 MAC 地址
- **定义**：以太网帧中标识接收端的 6 字节 MAC 地址字段
- **说明**：帧到达交换机时查找 MAC 地址表确定转发端口；广播帧目的 MAC 为 FF:FF:FF:FF:FF:FF
- **相关**：MAC Address（MAC 地址）、Source MAC（源 MAC 地址）
### DIFS (DCF Interframe Space) / DCF 帧间间隔
- **中文**：DCF 帧间间隔
- **定义**：802.11 中数据帧发送前需空闲的最短时间
- **说明**：DIFS > SIFS，确保控制帧（ACK/CTS）优先级高于数据帧；在 DCF 模式下使用
- **相关**：SIFS、CSMA/CA、Wi-Fi
### Duplex / 双工
- **中文**：双工
- **定义**：通信双方可双向传输的模式
- **说明**：双工分为全双工和半双工；全双工同时收发，半双工交替收发
- **相关**：Full Duplex（全双工）、Half Duplex（半双工）
### Error Detection / 错误检测
- **中文**：错误检测
- **定义**：检测数据传输中是否发生错误的技术
- **说明**：常用方法：奇偶校验、校验和、CRC；检测到错误后可以请求重传（ARQ）或丢弃
- **相关**：Error Correction（错误纠错）、CRC（循环冗余校验）、Checksum（校验和）
### Ethernet / 以太网
- **中文**：以太网
- **定义**：最广泛使用的有线局域网技术，标准 IEEE 802.3
- **说明**：以太网帧格式：目的 MAC | 源 MAC | 类型/长度 | 数据 | FCS；速率：10M → 100M → 1G → 10G → 100G → 400G；使用 CSMA/CD 或全双工交换
- **相关**：MAC Address（MAC 地址）、Switch（交换机）、IEEE 802.3
### FCS (Frame Check Sequence) / 帧检验序列
- **中文**：帧检验序列
- **定义**：以太网帧尾部的 CRC-32 校验字段，用于检测帧在传输中是否损坏
- **说明**：发送端计算 CRC 填充 FCS；接收端重新计算 CRC 对比，不一致则丢弃帧
- **相关**：CRC（循环冗余校验）、Ethernet（以太网）、Frame（帧）
### Fiber Optic / 光纤
- **中文**：光纤
- **定义**：利用光在玻璃纤维中全反射传输数据的传输介质
- **说明**：光纤分为单模光纤（SMF，远距高带宽）和多模光纤（MMF，短距低成本）；抗电磁干扰、带宽极高；FTTH（光纤到户）
- **相关**：Twisted Pair（双绞线）、Coaxial Cable（同轴电缆）、WDM（波分复用）
### Frame / 帧
- **中文**：帧
- **定义**：数据链路层的数据传输单元，封装网络层数据包
- **说明**：帧包含：帧头、载荷、帧尾；帧是二层交换机处理的基本单位
- **相关**：Packet（数据包）、Ethernet（以太网）、Framing（成帧）
### Framing / 成帧
- **中文**：成帧
- **定义**：将比特流划分为有意义的帧的过程，标识帧的起始和结束
- **说明**：成帧方法：字符计数、字节填充、比特填充、物理层编码违例；成帧使接收方能正确识别帧边界
- **相关**：Frame（帧）、Bit Stuffing（比特填充）
### Hub / 集线器
- **中文**：集线器
- **定义**：工作在物理层的网络设备，将输入信号复制到所有其他端口
- **说明**：Hub 所有端口共享带宽和冲突域；已被交换机取代；仅用于简单网络或故障排查
- **相关**：Switch（交换机）、Collision Domain（冲突域）
### IEEE 802.3 / IEEE 802.3 标准
- **中文**：IEEE 802.3 标准
- **定义**：IEEE 制定的以太网技术标准
- **说明**：802.3 定义 CSMA/CD；802.3ab 定义 1000BASE-T（千兆以太网）；802.3ae 定义万兆光纤等
- **相关**：Ethernet（以太网）、IEEE 802.11（Wi-Fi）
### MAC Address / MAC 地址
- **中文**：MAC 地址
- **定义**：分配网络接口卡的 48 位物理地址，数据链路层使用
- **说明**：格式：XX:XX:XX:XX:XX:XX（十六进制），前 24 位 OUI（组织唯一标识符），后 24 位设备标识；全球唯一（理论上）
- **同义词**：Physical Address（物理地址）、Hardware Address（硬件地址）
- **相关**：ARP、Ethernet（以太网）、NIC
### MAC Table / MAC 地址表
- **中文**：MAC 地址表
- **定义**：交换机中存储 MAC 地址与端口映射关系的表
- **说明**：交换机通过学习源 MAC 地址建立转发表；未知目的 MAC 时洪泛（Flooding）；老化时间后删除
- **同义词**：Forwarding Table（转发）、CAM Table（内容可寻址存储器表）
- **相关**：Switch（交换机）、MAC Address（MAC 地址）
### Manchester Encoding / 曼彻斯特编码
- **中文**：曼彻斯特编码
- **定义**：每比特中间有跳变，将时钟信号嵌入数据的一种比特编码方式
- **说明**：10M 以太网使用曼彻斯特编码；上升沿 = 1，下降沿 = 0；带宽效率低（2 倍），但自带时钟同步
- **相关**：NRZ（不归零编码）、Line Code（线路编码）
### Modulation / 调制
- **中文**：调制
- **定义**：将数字信号转换为适合传输介质的模拟信号的过程
- **说明**：基本调制方式：幅移键控（ASK）、频移键控（FSK）、相移键控（PSK）、正交幅度调制（QAM）；Wi-Fi 使用 OFDM
- **相关**：Demodulation（解调）、OFDM（正交频分复用）、Signal（信号）
### MTU (Maximum Transmission Unit) / 最大传输单元
- **发音**：/ɛm-tiː-juː/
- **中文**：最大传输单元
- **定义**：网络接口层能传输的最大数据包大小
- **说明**：以太网 MTU 通常为 1500 字节；超过 MTU 需要分片（Fragmentation）或路径 MTU 发现；IP 分片在路由器进行，IPv6 禁止中间路由器分片
- **相关**：Fragmentation（分片）、Path MTU Discovery（路径 MTU 发现）
### NIC (Network Interface Card) / 网卡
- **发音**：/nɪk/
- **中文**：网络接口卡
- **定义**：连接计算机到网络的硬件设备
- **说明**：每块 NIC 有唯一 MAC 地址；处理物理层信号和链路层帧；速率：1Gbps、10Gbps 等
- **相关**：MAC Address（MAC 地址）、Driver（驱动）
### OFDM (Orthogonal Frequency Division Multiplexing) / 正交频分复用
- **发音**：/oʊ-ɛf-diː-ɛm/
- **中文**：正交频分复用
- **定义**：将高速数据流分成多个低速子载波并行传输的调制技术
- **说明**：OFDM 抗多径衰落效果好；Wi-Fi (802.11a/g/n/ac/ax)、4G/5G、ADSL 使用 OFDM；子载波正交无干扰
- **相关**：Modulation（调制）、Wi-Fi、4G/5G
### PPP (Point-to-Point Protocol) / 点对点协议
- **发音**：/piː-piː-piː/
- **中文**：点对点协议
- **定义**：两点间直接通信的数据链路层协议
- **说明**：PPP 用于串行链路、拨号连接、PPPoE（宽带接入）；支持认证（PAP/CHAP）、多协议封装
- **同义词**：PPP
- **相关**：HDLC（高级数据链路控制）、PPP over Ethernet
### RTS/CTS (Request to Send / Clear to Send) / 请求发送/允许发送
- **中文**：请求发送/允许发送
- **定义**：802.11 中用于解决隐藏终端问题的可选握手协议
- **说明**：发送前先发 RTS，AP 回复 CTS；CTS 通知覆盖范围内的所有节点退避；降低冲突概率但增加开销
- **相关**：CSMA/CA、Wi-Fi、Hidden Terminal Problem（隐藏终端问题）
### SIFS (Short Interframe Space) / 短帧间间隔
- **中文**：短帧间间隔
- **定义**：802.11 中控制帧（ACK、CTS）发送前需空闲的最短时间
- **说明**：SIFS < DIFS，确保控制帧有最高优先级；ACK 帧在接收数据后 SIFS 时间发送
- **相关**：DIFS、CSMA/CA、Wi-Fi
### Source MAC / 源 MAC 地址
- **中文**：源 MAC 地址
- **定义**：以太网帧中标识发送端的 MAC 地址字段
- **说明**：交换机根据源 MAC 地址学习端口映射
- **相关**：MAC Address（MAC 地址）、Destination MAC（目的 MAC 地址）
### STP (Spanning Tree Protocol) / 生成树协议
- **发音**：/ɛs-tiː-piː/
- **中文**：生成树协议
- **定义**：防止二层环路导致广播风暴的协议，通过阻塞部分端口形成无环逻辑拓扑
- **说明**：IEEE 802.1D；通过 BPDU 选举根桥（Root Bridge），确定每个网段指定桥和端口状态，阻塞冗余端口；RSTP（快速 STP）、MSTP（多实例 STP）是其改进
- **相关**：Broadcast Storm（广播风暴）、Loop（环路）、Switch（交换机）
### Switch / 交换机
- **中文**：交换机
- **定义**：工作在数据链路层的网络设备，根据 MAC 地址转发帧
- **说明**：交换机学习 MAC 地址建立转发表；每个端口隔离冲突域；VLAN 隔离广播域；分为非管理型和网管型（支持 VLAN、STP 等）
- **相关**：MAC Address（MAC 地址）、VLAN、Bridge（网桥）
### Twisted Pair / 双绞线
- **中文**：双绞线
- **定义**：将两根绝缘铜线绞合在一起的有线传输介质
- **说明**：双绞线分为 UTP（非屏蔽双绞线）和 STP（屏蔽双绞线）；Cat5e、Cat6、Cat6a、Cat7 等类决定传输速率
- **相关**：Ethernet（以太网）、RJ45、Fiber Optic（光纤）
### VLAN (Virtual LAN) / 虚拟局域网
- **中文**：虚拟局域网
- **定义**：将物理网络逻辑分割为多个隔离广播域的虚拟网络
- **说明**：IEEE 802.1Q；不同 VLAN 间通信需要路由器或三层交换机；VLAN Tag（标签）标识帧属于哪个 VLAN；Trunk 链路承载多个 VLAN
- **相关**：Broadcast Domain（广播域）、Switch（交换机）、IEEE 802.1Q
### Wi-Fi / 无线局域网
- **中文**：Wi-Fi
- **定义**：基于 IEEE 802.11 标准的无线局域网技术
- **说明**：代际演进：802.11b → a/g → n (Wi-Fi 4) → ac (Wi-Fi 5) → ax (Wi-Fi 6/6E) → be (Wi-Fi 7)；频段 2.4GHz、5GHz、6GHz
- **相关**：IEEE 802.11、Access Point（接入点）、CSMA/CA
