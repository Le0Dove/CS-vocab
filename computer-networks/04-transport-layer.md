# 04. 传输层 (Transport Layer)
### ACK (Acknowledgment) / 确认
- **发音**：/æk/
- **中文**：确认
- **定义**：接收方发送的回执，告知发送方已成功接收数据
- **说明**：TCP 的可靠性建立在 ACK 机制上；积累 ACK（Cumulative ACK）确认该序号之前的所有字节；选择 ACK（SACK）可确认不连续段
- **相关**：TCP、NAK（否定确认）、Retransmission（重传）
### AIMD (Additive Increase Multiplicative Decrease) / 加性增加乘性减少
- **中文**：加性增加乘性减少
- **定义**：TCP 拥塞控制的基本算法策略
- **说明**：拥塞窗口在成功传输时线性增加（+1），丢包时乘性减少（÷2）；形成锯齿形窗口变化；已过时，现在使用 CUBIC、BBR 等新算法
- **相关**：Congestion Control（拥塞控制）、TCP、Congestion Window（cwnd）
### Congestion Control / 拥塞控制
- **中文**：拥塞控制
- **定义**：TCP 防止发送过多数据导致网络拥塞的机制
- **说明**：拥塞窗口（cwnd）限制发送速率；主要算法：慢启动、拥塞避免、快重传、快恢复；CUBIC 是 Linux 默认算法；BBR 是基于延迟的新算法
- **相关**：Flow Control（流量控制）、TCP、Congestion Window（cwnd）
### Congestion Window (cwnd) / 拥塞窗口
- **中文**：拥塞窗口
- **定义**：TCP 发送方内部维护的拥塞控制窗口，限制已发送未确认的数据量
- **说明**：实际发送窗口 = min(cwnd, rwnd)；拥塞控制器根据 ACK 和丢包调节 cwnd；慢启动阶段 cwnd 指数增长
- **相关**：Congestion Control（拥塞控制）、TCP、Receive Window（rwnd）
### Cumulative ACK / 积累式确认
- **中文**：积累式确认
- **定义**：TCP 默认的确认方式，ACK 号表示该号之前所有字节都已收到
- **说明**：积累式 ACK 只确认连续收到的最高序号；不能指示后续不连续已收到段
- **相关**：SACK（选择确认）、ACK、TCP
### Ephemeral Port / 临时端口
- **中文**：临时端口
- **定义**：客户端临时分配用于出站连接的高编号端口（通常 49152-65535）
- **说明**：每次连接客户端分配不同临时端口；连接关闭后回收；五元组标识连接唯一性
- **相关**：Port（端口）、Five-tuple（五元组）
### FIN (Finish) / 结束
- **音标**：/fɪn/
- **中文**：结束
- **定义**：TCP 标志位，表示发送方已完成数据发送，请求关闭连接
- **说明**：四次挥手过程：FIN → ACK → FIN → ACK；TIME_WAIT 状态等待 2MSL
- **相关**：TCP、Four-Way Handshake（四次挥手）、SYN
### Five-Tuple / 五元组
- **中文**：五元组
- **定义**：唯一标识一个网络连接的五个字段：(源 IP, 源端口, 目的 IP, 目的端口, 协议)
- **说明**：TCP/UDP 连接通过五元组唯一区分；多连接复用同一 IP 但用不同端口
- **相关**：TCP、UDP、Port（端口）
### Flow Control / 流量控制
- **中文**：流量控制
- **定义**：防止发送方发送速度超过接收方处理能力的机制
- **说明**：TCP 用滑动窗口实现流量控制；接收方在 ACK 中通告窗口大小（rwnd）；窗口为 0 时发送方停止发送
- **相关**：Congestion Control（拥塞控制）、TCP、Receive Window（rwnd）
### Four-Way Handshake / 四次挥手
- **中文**：四次挥手
- **定义**：TCP 连接关闭过程，双方各发送 FIN 和 ACK 共四个报文段
- **说明**：步骤：① A→B FIN → ② B→A ACK → ③ B→A FIN → ④ A→B ACK；A 进入 TIME_WAIT 等待 2MSL
- **相关**：Three-Way Handshake（三次握手）、TCP、FIN
### MSS (Maximum Segment Size) / 最大分段大小
- **中文**：最大分段大小
- **定义**：TCP 连接中每个段允许携带的最大数据量
- **说明**：MSS = MTU - TCP 头大小；通常在三次握手时协商；影响数据分段和效率
- **相关**：MTU（最大传输单元）、TCP、Segment（段）
### Multiplexing / 多路复用
- **中文**：多路复用
- **定义**：多个应用层连接共享同一网络层连接的技术
- **说明**：传输层通过端口号实现多路复用；TCP 和 UDP 同时复用 IP 层；接收端根据端口号分用（Demultiplexing）
- **相关**：Demultiplexing（分用）、Port（端口）、TCP
### NAK (Negative Acknowledgment) / 否定确认
- **发音**：/næk/
- **中文**：否定确认
- **定义**：接收方通知发送方指定序号数据未收到或已损坏的机制
- **说明**：TCP 不使用显式 NAK，而是用重复 ACK 隐式通知丢包；某些可靠传输协议使用 NAK
- **相关**：ACK、Retransmission（重传）
### Port / 端口
- **中文**：端口
- **定义**：标识主机上特定应用或服务的 16 位数字
- **说明**：熟知端口 0-1023（HTTP 80, HTTPS 443, SSH 22）；注册端口 1024-49151；动态/临时端口 49152-65535
- **相关**：Socket（套接字）、TCP、UDP
### Receive Window (rwnd) / 接收窗口
- **中文**：接收窗口
- **定义**：接收方通知发送方其可用缓冲区大小的流量控制字段
- **说明**：rwnd = 接收方空闲缓冲区大小；窗口为 0 时发送方暂停发送；窗口缩放（Window Scale）选项支持大于 65535 的窗口
- **相关**：Flow Control（流量控制）、TCP、Congestion Window（cwnd）
### Retransmission / 重传
- **中文**：重传
- **定义**：当检测到数据丢失或损坏时重新发送数据的机制
- **说明**：TCP 通过 RTO（重传超时）和快重传两种方式触发；快重传通过三个重复 ACK 触发，无需等待超时；选择性重传（SACK）精确重传丢失段
- **相关**：RTO（重传超时）、TCP、SACK
### RST (Reset) / 复位
- **中文**：复位
- **定义**：TCP 标志位，强制立即终止连接
- **说明**：收到 RST 段表明连接异常（端口未监听、连接被拒绝）；不经过四次挥手直接关闭连接
- **相关**：TCP、FIN
### RTO (Retransmission Timeout) / 重传超时
- **中文**：重传超时
- **定义**：重传数据前等待 ACK 的最大时间
- **说明**：RTO 基于 RTT 估算和平滑变化；如果超时，重新发送最早未确认段并大幅减小拥塞窗口
- **相关**：Retransmission（重传）、TCP、RTT
### SACK (Selective Acknowledgment) / 选择确认
- **中文**：选择确认
- **定义**：TCP 选项，允许接收方确认多个不连续的段
- **说明**：SACK 帮助发送方精确了解哪些段已收到、哪些丢失；减少不必要的重传
- **相关**：ACK、Cumulative ACK、Retransmission
### Sequence Number / 序列号
- **中文**：序列号
- **定义**：TCP 段中标识数据字节流的 32 位编号
- **说明**：三次握手时随机初始化序列号（ISN）；保证有序交付和重复检测；每次超过 2³² 时回绕
- **相关**：TCP、ACK、Acknowledgment Number
### Silly Window Syndrome / 糊涂窗口综合征
- **中文**：糊涂窗口综合征
- **定义**：接收方每次只确认极少数据导致传输效率低下的问题
- **说明**：原因：接收方窗口极小或发送方发送极小段；Nagle 算法（Nagle's Algorithm）和 Clark 解决方案分别从发送和接收端解决
- **相关**：Flow Control（流量控制）、Nagle's Algorithm
### Socket / 套接字
- **中文**：套接字
- **定义**：应用程序与网络协议栈之间的编程接口，由 IP 地址和端口号组成
- **说明**：socket = IP:Port；伯克利套接字 API（socket/bind/listen/accept/connect）是网络编程基础
- **同义词**：Socket
- **相关**：Port（端口）、IP Address、TCP
### SYN (Synchronize) / 同步
- **中文**：同步
- **定义**：TCP 标志位，用于建立连接时同步序列号
- **说明**：三次握手中双方各发一次 SYN（SYN 和 ACK 标志可同时置位为 SYN+ACK）；SYN 洪泛是常见 DDoS 攻击
- **相关**：Three-Way Handshake（三次握手）、TCP、ACK
### TCP (Transmission Control Protocol) / 传输控制协议
- **发音**：/tiː-siː-piː/
- **中文**：传输控制协议
- **定义**：面向连接的可靠字节流传输协议，确保数据正确、有序、无重复交付
- **说明**：TCP 特性：三次握手建立连接、停止等待协议保证可靠性、滑动窗口提高效率、拥塞控制节制发送速率、流量控制保护接收方；是互联网最重要的传输协议
- **相关**：UDP、Flow Control、Congestion Control
- **例句**：TCP guarantees reliable, in-order delivery of data.
### Three-Way Handshake / 三次握手
- **中文**：三次握手
- **定义**：TCP 连接建立过程，双方交换三个报文段同步初始序列号
- **说明**：步骤：① A→B SYN → ② B→A SYN+ACK → ③ A→B ACK；确保双方收发能力正常；SYN Cookie 防御 SYN 泛洪攻击
- **相关**：Four-Way Handshake（四次挥手）、TCP、SYN
### UDP (User Datagram Protocol) / 用户数据报协议
- **发音**：/juː-diː-piː/
- **中文**：用户数据报协议
- **定义**：不可靠、无连接、低开销的传输层协议
- **说明**：UDP 无握手、无确认、无重传；头部仅 8 字节（源端口、目的端口、长度、校验和）；适实时应用（VoIP、视频流）、DNS 查询、多播
- **相关**：TCP、Datagram（数据报）、Connectionless
### Urgent Pointer / 紧急指针
- **中文**：紧急指针
- **定义**：TCP 头部字段，指向紧急数据的最后一个字节的偏移
- **说明**：紧急数据不常用；用于发送带外数据（如 Telnet 中断）、已过时
- **相关**：TCP、Out-of-Band Data
