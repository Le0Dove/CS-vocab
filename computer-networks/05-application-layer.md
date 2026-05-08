# 05. 应用层 (Application Layer)
### CDN (Content Delivery Network) / 内容分发网络
- **发音**：/siː-diː-ɛn/
- **中文**：内容分发网络
- **定义**：地理分布的服务器网络，将内容缓存到离用户最近的边缘节点以加快访问
- **说明**：CDN 通过 DNS 或任播将请求导向最近的边缘节点；减少延迟、减轻源站压力、防护 DDoS；代表：Cloudflare、Akamai、AWS CloudFront
- **相关**：DNS、Edge Server（边缘服务器）、Caching（缓存）
### Cookie / Cookie
- **音标**：/ˈkʊki/
- **中文**：Cookie（HTTP Cookie）
- **定义**：服务器发送给浏览器存储的短小文本数据，用于保持无状态 HTTP 的状态信息
- **说明**：Cookie 字段：name、value、domain、path、expires、Secure、HttpOnly、SameSite；用于会话管理、个性化、追踪；第三方 Cookie 涉及隐私问题
- **相关**：HTTP、Session（会话）、Set-Cookie
### CORS (Cross-Origin Resource Sharing) / 跨域资源共享
- **发音**：/kɔːrs/
- **中文**：跨域资源共享
- **定义**：允许网页从不同源（域名/协议/端口）请求资源的 HTTP 安全机制
- **说明**：同源策略（Same-Origin Policy）默认禁止跨域请求；服务器用 Access-Control-Allow-Origin 等头部授权跨域
- **相关**：HTTP、Same-Origin Policy（同源策略）
### DNS (Domain Name System) / 域名系统
- **发音**：/diː-ɛn-ɛs/
- **中文**：域名系统
- **定义**：将域名翻译为 IP 地址的分层分布式命名系统
- **说明**：DNS 查询过程：递归查询和迭代查询；根 DNS → 顶级域 DNS → 权威 DNS；记录类型 A/AAAA（IP）、CNAME（别名）、MX（邮件）、NS（Name Server）、TXT（文本/SPF）等
- **相关**：Domain Name（域名）、IP Address、DNS Cache（DNS 缓存）
- **例句**：DNS translates human-readable domain names into IP addresses.
### DNS Cache / DNS 缓存
- **中文**：DNS 缓存
- **定义**：临时存储 DNS 查询结果以加速后续请求
- **说明**：浏览器缓存、操作系统缓存、递归解析器缓存；TTL 决定缓存有效期；DNS 缓存污染是安全问题
- **相关**：DNS、Caching（缓存）、TTL
### DNS Record / DNS 记录
- **中文**：DNS 记录
- **定义**：DNS 区域文件中存储的资源记录，包含域名与相关信息的映射
- **说明**：常见：A/AAAA、CNAME、MX、NS、TXT、SOA、PTR、SRV；TXT 记录可用于 SPF/DKIM 邮件验证
- **相关**：DNS、Zone File（区域文件）
### Domain Name / 域名
- **中文**：域名
- **定义**：互联网上标识和定位计算机的易于记忆的字符串
- **说明**：域名结构：主机名.子域名.二级域.顶级域（如 www.example.com）；由 ICANN 管理顶级域
- **相关**：DNS、FQDN（完全限定域名）、TLD（顶级域）
### FTP (File Transfer Protocol) / 文件传输协议
- **发音**：/ɛf-tiː-piː/
- **中文**：文件传输协议
- **定义**：在网络上进行文件上传和下载的标准协议
- **说明**：FTP 使用控制连接（21）和数据连接（20）；主动模式和被动模式（PASV）；使用明文不安全性，建议使用 SFTP 或 FTPS
- **相关**：SFTP、FTPS、SSH
### gRPC
- **发音**：/dʒiː-ɑːr-piː-siː/
- **中文**：gRPC
- **定义**：Google 开发的高性能 RPC 框架，使用 Protocol Buffers 序列化和 HTTP/2 传输
- **说明**：gRPC 比 REST/JSON 性能高；支持双向流、多语言；基于 HTTP/2 实现多路复用；微服务间通信首选
- **相关**：REST、HTTP/2、Protocol Buffers
### HTTP/2
- **中文**：HTTP/2
- **定义**：HTTP 协议的大版本改进，专注于性能
- **说明**：特性：二进制帧、多路复用（一条 TCP 连接并发多个请求/响应）、头部压缩（HPACK）、服务器推送（Server Push）；仍需 HTTPS 部署
- **相关**：HTTP/3、HTTP、TLS
### HTTP (HyperText Transfer Protocol) / 超文本传输协议
- **中文**：超文本传输协议
- **定义**：Web 上传输超文本文档（HTML）的应用层协议
- **说明**：HTTP 是请求-响应模型、无状态协议；方法：GET、POST、PUT、DELETE、HEAD 等；状态码：200 OK、301 永久重定向、404 Not Found、500 服务器错误
- **相关**：HTTPS、URL、REST
### HTTPS / 安全 HTTP
- **中文**：安全 HTTP
- **定义**：HTTP 经过 TLS 加密保护的版本
- **说明**：HTTPS 使用端口 443；防止窃听、篡改、冒充；通过 CA 签发的 SSL/TLS 证书验证身份
- **同义词**：HTTP over TLS
- **相关**：TLS（传输层安全）、Certificate（证书）、SSL
### IMAP (Internet Message Access Protocol) / 互联网消息访问协议
- **发音**：/aɪ-mæp/
- **中文**：互联网消息访问协议
- **定义**：从邮件服务器获取邮件的协议，保留邮件在服务器上
- **说明**：IMAP 支持文件夹、部分下载、标志标记；与 POP3 不同（POP3 将邮件下载到本地）；现代邮件访问首选 IMAP
- **相关**：SMTP、POP3、Email
### Keep-Alive / 保持连接
- **中文**：保持连接
- **定义**：HTTP 机制，允许同一 TCP 连接发送多个 HTTP 请求/响应
- **说明**：HTTP/1.0 默认连接每次关闭（Connection:close）；HTTP/1.1 默认保持连接；减少 TCP 握手开销
- **相关**：HTTP、Persistent Connection（持久连接）、TCP
### Load Balancer / 负载均衡器
- **中文**：负载均衡器
- **定义**：将进入的网络流量分发到多个后端服务器的设备或软件
- **说明**：算法：轮询（Round Robin）、最少连接（Least Connections）、IP Hash；四层负载均衡（传输层，直接转发）和七层负载均衡（应用层，基于内容路由）；代表：Nginx、HAProxy、AWS ALB
- **相关**：Reverse Proxy（反向代理）、High Availability（高可用）
### MIME (Multipurpose Internet Mail Extensions) / 多用途互联网邮件扩展
- **发音**：/maɪm/
- **中文**：多用途互联网邮件扩展
- **定义**：扩展电子邮件支持文本外内容（图片、音频、附件）的标准，也用于 HTTP
- **说明**：Content-Type 字段定义数据类型（如 text/html、image/png、application/json）；HTTP 使用 MIME 类型协商内容格式
- **相关**：HTTP、Email、Content-Type
### POP3 (Post Office Protocol v3) / 邮箱协议第 3 版
- **中文**：邮箱协议第 3 版
- **定义**：从邮件服务器将邮件下载到本地的协议
- **说明**：POP3 下载后通常删除服务器邮件；简单但限制多，现代用 IMAP 替代
- **相关**：IMAP、SMTP、Email
### Proxy / 代理
- **中文**：代理
- **定义**：充当中介、转发客户端和服务器之间请求和响应的服务器
- **说明**：正向代理（Forward Proxy）为客户端代理出站；反向代理（Reverse Proxy）为服务器代理入站
- **相关**：Reverse Proxy（反向代理）、VPN、Gateway（网关）
### QUIC
- **发音**：/kwɪk/
- **中文**：QUIC 协议
- **定义**：基于 UDP 的下一代传输协议，旨在减少连接延迟并改进性能
- **说明**：QUIC 内置 TLS 1.3 加密；0-RTT 连接建立；多路复用无队头阻塞；HTTP/3 构建于 QUIC 之上
- **相关**：HTTP/3、UDP、TLS
### REST (Representational State Transfer) / 表述性状态转移
- **中文**：表述性状态转移
- **定义**：一种基于 HTTP 的 Web API 架构风格
- **说明**：RESTful API 原则：资源由 URL 标识、使用 HTTP 方法（GET/POST/PUT/DELETE）操作资源、无状态、可缓存
- **同义词**：RESTful
- **相关**：HTTP、API、GraphQL
### Reverse Proxy / 反向代理
- **中文**：反向代理
- **定义**：代表后端服务器接收客户端请求的代理服务器
- **说明**：反向代理提供负载均衡、缓存、SSL 卸载、安全防护；Nginx、Apache、Cloudflare 可实现反向代理
- **相关**：Proxy（代理）、Load Balancer（负载均衡）、CDN
### Round Robin / 轮询
- **中文**：轮询（负载均衡）
- **定义**：负载均衡算法，将请求按顺序轮流分配给后端服务器
- **说明**：轮询实现简单但未考虑服务器负载差异；加权轮询（Weighted Round Robin）按权重分配比例
- **相关**：Load Balancer（负载均衡）、DNS Round Robin
### SMTP (Simple Mail Transfer Protocol) / 简单邮件传输协议
- **发音**：/ɛs-ɛm-tiː-piː/
- **中文**：简单邮件传输协议
- **定义**：从邮件客户端发送邮件到邮件服务器、在邮件服务器间传输邮件的协议
- **说明**：SMTP 使用端口 25/587/465（SMTPS）；与 IMAP/POP3 配合使用（SMTP 发送，IMAP/POP3 接收）
- **相关**：IMAP、POP3、Email
### SNI (Server Name Indication) / 服务器名称指示
- **中文**：服务器名称指示
- **定义**：TLS 扩展，允许客户端在握手时指出要连接的主机名
- **说明**：SNI 使同一 IP 地址托管多个 HTTPS 站点成为可能；TLS 1.3 对 SNI 进行加密保护；无 SNI 支持则每个 HTTPS 站点需要独立 IP
- **相关**：TLS、HTTPS、Virtual Hosting（虚拟主机）
### SSL/TLS / 安全套接层/传输层安全
- **中文**：SSL/TLS
- **定义**：见 operating-system 的 09-security.md
- **相关**：HTTPS、Certificate（证书）
### URI (Uniform Resource Identifier) / 统一资源标识符
- **发音**：/ˈjʊəri/
- **中文**：统一资源标识符
- **定义**：标识互联网上资源的字符串
- **说明**：URL（统一资源定位符）是 URI 的子集，含访问方式；URN（统一资源名称）是 URI 的另一个子集
- **相关**：URL、URN
### URL (Uniform Resource Locator) / 统一资源定位符
- **中文**：统一资源定位符
- **定义**：标识互联网资源位置和访问方式的字符串
- **说明**：URL 格式：scheme://user:password@host:port/path?query#fragment；用于 HTTP、FTP 等
- **相关**：URI、HTTP、DNS
### Virtual Hosting / 虚拟主机
- **中文**：虚拟主机
- **定义**：一台物理服务器托管多个网站的机制
- **说明**：基于名称的虚拟主机（HTTP Host 头区分）；基于 IP 的虚拟主机（每站点独立 IP）；基于端口的虚拟主机
- **相关**：HTTP、Web Server（Web 服务器）、SNI
### WebSocket
- **中文**：WebSocket
- **定义**：在单个 TCP 连接上提供全双工通信通道的协议
- **说明**：WebSocket 在 HTTP 握手后升级协议；低延迟双向通信；用于实时聊天、在线游戏、实时数据推送
- **相关**：HTTP、TCP、Real-time Communication（实时通信）
