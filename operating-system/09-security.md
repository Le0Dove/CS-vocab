# 09. 安全与保护 (Security & Protection)

## 基础概念### 3DES (Triple DES) / 三重 DES
- **发音**：/θriː-diː-iː-ɛs/
- **中文**：三重 DES
- **定义**：应用 DES 三次的对称加密算法
- **说明**：3DES 提高安全性（有效密钥长度 112 或 168 位），但速度慢；已被 AES 取代，但仍用于兼容旧系统
- **相关**：DES、AES、Symmetric Encryption（对称加密）
### Accounting / 审计
- **音标**：/əˈkaʊntɪŋ/
- **中文**：审计（记账）
- **定义**：记录用户或进程访问资源的行为，用于事后分析和追责
- **说明**：审计日志记录谁、何时、做了什么操作；是安全事件调查的重要依据；也称为 Auditing
- **同义词**：Auditing、Audit Trail（审计跟踪）
### ACME (Automatic Certificate Management Environment) / 自动证书管理环境
- **发音**：/ˈækmiː/
- **中文**：自动证书管理环境
- **定义**：Let's Encrypt 使用的自动化证书管理协议
- **说明**：ACME 客户端（如 Certbot）自动完成域名验证、证书申请、安装和续期；简化 HTTPS 部署
- **相关**：Let's Encrypt、Certificate（证书）
### AES (Advanced Encryption Standard) / 高级加密标准
- **发音**：/eɪ-iː-ɛs/
- **中文**：高级加密标准
- **定义**：目前最广泛使用的对称加密算法
- **说明**：AES 由美国 NIST 标准化，替代 DES；支持 128、192、256 位密钥；快速、安全，广泛用于数据加密
- **相关**：Symmetric Encryption（对称加密）、DES、Encryption（加密）
### Alerting / 告警
- **中文**：告警
- **定义**：当指标超过阈值或检测到异常时通知管理员
- **说明**：告警渠道包括：邮件、短信、Slack、PagerDuty；需要避免告警疲劳（Alert Fatigue）；好的告警应可行动、有上下文
- **相关**：Monitoring（监控）、Incident Response（事件响应）
### AMD SEV (Secure Encrypted Virtualization) / 安全加密虚拟化
- **发音**：/eɪ-ɛm-diː-ɛs-iː-viː/
- **中文**：安全加密虚拟化
- **定义**：AMD 的虚拟机内存加密技术
- **说明**：SEV 使用密钥加密虚拟机内存，Hypervisor 无法读取 Guest VM 内存；SEV-SNP 增加完整性保护
- **相关**：Virtualization（虚拟化）、AMD、TEE（可信执行环境）
### Antivirus / 杀毒软件
- **音标**：/ˌæntiˈvaɪrəs/
- **中文**：杀毒软件
- **定义**：检测、预防和删除恶意软件的程序
- **说明**：传统杀毒软件基于签名检测；现代杀毒软件（EPP，Endpoint Protection Platform）结合行为分析、机器学习、沙箱；代表：Kaspersky、Bitdefender、Windows Defender
- **相关**：Malware（恶意软件）、EDR（端点检测与响应）
### APT (Advanced Persistent Threat) / 高级持续性威胁
- **发音**：/eɪ-piː-tiː/
- **中文**：高级持续性威胁
- **定义**：有组织、有目的、长期潜伏的高级攻击
- **说明**：APT 攻击者（如国家支持的黑客组织）使用定制工具、零日漏洞、社会工程，长期潜伏窃取数据；难以检测和防御
- **相关**：Threat Hunting（威胁狩猎）、Zero-Day（零日）
### Argon2
- **发音**：/ˈɑːrɡɒn-tuː/
- **中文**：Argon2
- **定义**：密码哈希竞赛 winner，推荐的密码哈希算法
- **说明**：Argon2 有三种变体：Argon2d（抵抗 GPU 破解）、Argon2i（抵抗侧信道攻击）、Argon2id（两者兼顾）；获得 2015 年密码哈希竞赛冠军
- **相关**：Password（密码）、Hash（哈希）、bcrypt
### ARP Spoofing / ARP 欺骗
- **中文**：ARP 欺骗
- **定义**：伪造 ARP 消息，将攻击者的 MAC 地址与他人的 IP 地址关联的攻击
- **说明**：ARP 欺骗用于中间人攻击、拒绝服务攻击；防御：静态 ARP 表、动态 ARP 检测（DAI）、使用 VLAN 隔离
- **相关**：MITM（中间人攻击）、ARP、Network Security（网络安全）
### Asymmetric Encryption / 非对称加密
- **中文**：非对称加密
- **定义**：使用公钥加密、私钥解密的加密方式
- **说明**：非对称加密速度慢，适合小数据量加密和密钥交换；公钥可以公开，私钥必须保密；算法包括 RSA、ECC、ElGamal
- **相关**：Symmetric Encryption（对称加密）、Public Key（公钥）、Private Key（私钥）
### Attack / 攻击
- **音标**：/əˈtæk/
- **中文**：攻击
- **定义**：利用漏洞或弱点对系统进行的恶意行为
- **说明**：攻击类型包括：拒绝服务、中间人、注入、缓冲区溢出、社会工程等
- **相关**：Threat（威胁）、Vulnerability（漏洞）、Exploit（利用）
### Attribute-Based Access Control (ABAC) / 基于属性的访问控制
- **中文**：基于属性的访问控制
- **定义**：根据用户、资源、环境的属性动态决定访问权限的模型
- **说明**：ABAC 比 RBAC 更灵活；策略如"工作时间且在公司网络的管理员可以访问财务数据"；现代云安全常用
- **相关**：RBAC（基于角色的访问控制）、Policy（策略）
### Audit Trail / 审计跟踪
- **中文**：审计跟踪
- **定义**：系统活动的 chronological 记录，用于安全审计
- **说明**：审计跟踪记录用户登录、文件访问、权限变更、系统调用等；需要保护审计日志本身的安全
- **相关**：Accounting（审计）、Log（日志）

---

## 访问控制模型
### Auditd
- **发音**：/ˈɔːdɪt-diː/
- **中文**：Auditd
- **定义**：Linux 审计守护进程
- **说明**：auditd 记录系统调用、文件访问、用户登录等安全相关事件；使用 auditctl 配置规则；日志存储在 /var/log/audit/
- **相关**：Audit（审计）、Log（日志）
### Auditing / 审计
- **中文**：审计
- **定义**：同 Accounting
- **相关**：Accounting（审计）
### Authentication / 认证
- **音标**：/ɔːˌθentɪˈkeɪʃn/
- **中文**：认证
- **定义**：验证用户或进程身份的过程
- **说明**：认证回答"你是谁"；方式包括：密码、生物识别（指纹、面部识别）、令牌、证书、双因素认证（2FA）等
- **相关**：Authorization（授权）、Identity（身份）
### Authorization / 授权
- **音标**：/ˌɔːθəraɪˈzeɪʃn/
- **中文**：授权
- **定义**：确定已认证用户或进程可以访问哪些资源、执行哪些操作
- **说明**：授权回答"你能做什么"；通过访问控制列表（ACL）、角色（Role）、能力（Capability）等实现
- **相关**：Authentication（认证）、Access Control（访问控制）、Permission（权限）
### Availability / 可用性
- **音标**：/əˌveɪləˈbɪləti/
- **中文**：可用性
- **定义**：确保授权用户在需要时可以访问系统和资源
- **说明**：可用性防止拒绝服务攻击（DoS）；通过冗余、备份、负载均衡、故障转移等实现；也称为 Reliability（可靠性）
- **相关**：Security（安全）、DoS（拒绝服务）、Reliability（可靠性）
### Backdoor / 后门
- **音标**：/ˈbækdɔːr/
- **中文**：后门
- **定义**：绕过正常认证机制访问系统的秘密入口
- **说明**：后门可以是开发者故意留下的（如调试后门），也可以是攻击者植入的；SolarWinds 事件是著名供应链后门攻击
- **相关**：Malware（恶意软件）、Trojan（木马）
### bcrypt
- **发音**：/biː-kript/
- **中文**：bcrypt
- **定义**：自适应密码哈希函数，基于 Blowfish 密码
- **说明**：bcrypt 内置 Salt，使用成本因子（工作因子）控制计算强度；成本因子可以随时间增加以对抗硬件进步；广泛用于密码存储
- **相关**：Password（密码）、Hash（哈希）、Key Stretching（密钥拉伸）
### Biometric / 生物识别
- **音标**：/ˌbaɪoʊˈmetrɪk/
- **中文**：生物识别
- **定义**：基于生理或行为特征的身份认证
- **说明**：生物识别包括指纹、面部识别、虹膜、声纹、步态等；方便但存在隐私和误识别问题
- **相关**：Authentication（认证）、Fingerprint（指纹）
### BitLocker
- **发音**：/bɪt-lɒkər/
- **中文**：BitLocker
- **定义**：Windows 全盘加密功能
- **说明**：BitLocker 使用 AES 加密整个卷；支持 TPM、密码、USB 密钥解锁；Windows 专业版/企业版可用
- **相关**：Disk Encryption（磁盘加密）、TPM（可信平台模块）
### Botnet / 僵尸网络
- **发音**：/ˈbɒt-nɛt/
- **中文**：僵尸网络
- **定义**：被攻击者控制的大量受感染计算机组成的网络
- **说明**：Botnet 用于 DDoS 攻击、发送垃圾邮件、挖矿、传播恶意软件；Mirai 是著名 IoT 僵尸网络
- **相关**：DDoS、Malware（恶意软件）
### Brute Force / 暴力破解
- **中文**：暴力破解
- **定义**：尝试所有可能的密码组合直到找到正确密码的攻击方法
- **说明**：暴力破解耗时但理论上总能成功；防御方法：使用长密码、限制登录尝试次数、使用验证码、账户锁定
- **相关**：Password（密码）、Dictionary Attack（字典攻击）
### CA (Certificate Authority) / 证书颁发机构
- **发音**：/siː-eɪ/
- **中文**：证书颁发机构
- **定义**：签发和管理数字证书的可信第三方
- **说明**：根 CA 证书预装在操作系统/浏览器中；中间 CA 由根 CA 授权；证书链（Certificate Chain）从服务器证书追溯到根 CA；代表：DigiCert、Let's Encrypt、GlobalSign
- **相关**：Certificate（证书）、PKI（公钥基础设施）、Root Certificate（根证书）
### Certificate / 证书
- **音标**：/sərˈtɪfɪkət/
- **中文**：证书
- **定义**：由证书颁发机构（CA）签名的数字文档，绑定公钥和身份
- **说明**：证书包含：公钥、所有者信息、有效期、CA 签名、序列号等；X.509 是标准证书格式；用于 HTTPS、代码签名、VPN 等
- **相关**：CA（证书颁发机构）、X.509、Public Key（公钥）
### Certificate Chain / 证书链
- **中文**：证书链
- **定义**：从服务器证书到根证书的验证路径
- **说明**：验证证书时，客户端从服务器证书开始，逐级验证上级证书，直到预装的根证书；如果链断裂，证书不被信任
- **相关**：Certificate（证书）、CA（证书颁发机构）、Root Certificate（根证书）
### Certificate Pinning / 证书固定
- **中文**：证书固定
- **定义**：应用程序硬编码预期的服务器证书或公钥，防止使用伪造证书
- **说明**：证书固定防止中间人攻击使用伪造或非法 CA 签发的证书；但如果合法证书更新，应用需要同步更新
- **相关**：Certificate（证书）、MITM（中间人攻击）

---

## 威胁与攻击
### ChaCha20
- **发音**：/tʃɑː-tʃɑː-twenti/
- **中文**：ChaCha20
- **定义**：流密码，作为 AES 的替代
- **说明**：ChaCha20 由 Daniel Bernstein 设计；在软件实现中比 AES 更快（特别是没有 AES 硬件加速的设备）；常与 Poly1305 认证算法结合使用（ChaCha20-Poly1305）
- **相关**：Symmetric Encryption（对称加密）、AES、TLS
### Chain of Custody / 保管链
- **中文**：保管链
- **定义**：记录证据从收集到呈堂全过程的文档
- **说明**：保管链证明证据未被篡改；包括谁、何时、何地、如何处理证据；是数字取证的核心要求
- **相关**：Forensics（取证）、Evidence（证据）
### CIA Triad / CIA 三元组
- **中文**：CIA 三元组
- **定义**：信息安全的三个核心目标：机密性（Confidentiality）、完整性（Integrity）、可用性（Availability）
- **说明**：CIA 是信息安全的基础框架；实际系统中需要在三者之间权衡
- **相关**：Confidentiality（机密性）、Integrity（完整性）、Availability（可用性）
### Cipher / 密码
- **音标**：/ˈsaɪfər/
- **中文**：密码（算法）
- **定义**：加密和解密数据的算法
- **说明**：古典密码（如凯撒密码、替换密码）已被破解；现代密码（如 AES、RSA、ChaCha20）使用复杂数学保证安全
- **相关**：Encryption（加密）、Algorithm（算法）
### Confidentiality / 机密性
- **音标**：/ˌkɒnfɪdenʃiˈæləti/
- **中文**：机密性
- **定义**：确保信息仅对授权用户可见
- **说明**：机密性防止未授权的信息泄露；通过加密、访问控制、权限管理等实现；也称为 Privacy（隐私）
- **同义词**：Privacy（隐私）、Secrecy
- **相关**：Security（安全）、Encryption（加密）、Access Control（访问控制）
### CRC (Cyclic Redundancy Check) / 循环冗余校验
- **发音**：/siː-ɑːr-siː/
- **中文**：循环冗余校验
- **定义**：用于检测数据传输错误的校验码
- **说明**：CRC 不是安全哈希，仅用于错误检测；可以轻易构造具有相同 CRC 的数据；不应用于安全场景
- **相关**：Checksum（校验和）、Hash（哈希）

---

## 其他安全概念
### CRL (Certificate Revocation List) / 证书撤销列表
- **发音**：/siː-ɑːr-ɛl/
- **中文**：证书撤销列表
- **定义**：被撤销（失效）证书的列表
- **说明**：证书可能在过期前被撤销（如私钥泄露）；客户端需要检查证书是否在 CRL 中；CRL 定期发布，可能有延迟
- **相关**：OCSP、Certificate（证书）、CA（证书颁发机构）
### CSIRT (Computer Security Incident Response Team) / 计算机安全事件响应团队
- **发音**：/siː-sɜːrt/
- **中文**：计算机安全事件响应团队
- **定义**：负责处理安全事件的专门团队
- **说明**：CSIRT 可以是企业内部团队或第三方服务；职责包括：事件处理、漏洞管理、安全咨询、培训
- **相关**：SOC（安全运营中心）、Incident Response（事件响应）
### CSRF (Cross-Site Request Forgery) / 跨站请求伪造
- **发音**：/siː-ɑːr-ɛs-ɛf/
- **中文**：跨站请求伪造
- **定义**：诱使已认证用户执行非预期操作的攻击
- **说明**：CSRF 利用用户已登录的状态，通过恶意链接或表单发送请求（如转账、修改密码）；防御：CSRF Token、SameSite Cookie、验证 Referer
- **相关**：Web Security（Web 安全）、XSS（跨站脚本）
### CVE (Common Vulnerabilities and Exposures) / 通用漏洞披露
- **发音**：/siː-viː-iː/
- **中文**：通用漏洞披露
- **定义**：公开已知漏洞的标准化标识系统
- **说明**：CVE 编号格式：CVE-年份-编号（如 CVE-2021-44228 Log4j 漏洞）；由 MITRE 管理；与 CVSS（严重性评分）配合使用
- **相关**：Vulnerability（漏洞）、CVSS、NVD
### CVSS (Common Vulnerability Scoring System) / 通用漏洞评分系统
- **发音**：/siː-viː-ɛs-ɛs/
- **中文**：通用漏洞评分系统
- **定义**：评估漏洞严重性的标准化评分系统
- **说明**：CVSS 分数 0-10：0 无、0.1-3.9 低、4.0-6.9 中、7.0-8.9 高、9.0-10.0 严重；包括基础分、时间分、环境分
- **相关**：CVE、Vulnerability（漏洞）
### Data Encryption at Rest / 静态数据加密
- **中文**：静态数据加密
- **定义**：存储在磁盘、数据库、备份中的数据加密
- **说明**：静态数据加密防止物理介质被盗或丢失导致的数据泄露；技术包括：全盘加密（BitLocker、FileVault）、数据库加密（TDE）、文件级加密
- **相关**：Encryption（加密）、Data Security（数据安全）
### Data Encryption in Transit / 传输中数据加密
- **中文**：传输中数据加密
- **定义**：在网络上传输的数据加密
- **说明**：传输中加密防止窃听和中间人攻击；使用 TLS/SSL、IPsec、SSH 等协议；现代标准：TLS 1.2+，禁用 SSLv3、TLS 1.0/1.1
- **相关**：Encryption（加密）、TLS、HTTPS
### Data Loss Prevention (DLP) / 数据丢失防护
- **发音**：/diː-ɛl-piː/
- **中文**：数据丢失防护
- **定义**：防止敏感数据泄露的技术和策略
- **说明**：DLP 监控、检测和阻止敏感数据的非授权传输（如邮件、USB、云上传）；包括网络 DLP、端点 DLP、云 DLP
- **相关**：Security（安全）、Confidentiality（机密性）
### Database Encryption / 数据库加密
- **中文**：数据库加密
- **定义**：加密数据库中的数据
- **说明**：数据库加密层次：TDE（透明数据加密，整个数据库）、列级加密（特定敏感列）、应用层加密（应用端加密后存储）；代表：Oracle TDE、SQL Server TDE、MySQL TDE
- **相关**：Encryption（加密）、TDE（透明数据加密）
### DDoS (Distributed Denial of Service) / 分布式拒绝服务
- **发音**：/diː-diː-oʊ-ɛs/
- **中文**：分布式拒绝服务
- **定义**：使用多个分布式源发起的拒绝服务攻击
- **说明**：DDoS 使用 Botnet 或反射放大（如 DNS 放大、NTP 放大）；难以防御，因为流量来自合法来源；防御：CDN、流量清洗、速率限制
- **相关**：DoS（拒绝服务）、Botnet（僵尸网络）
### Deception Technology / 欺骗技术
- **中文**：欺骗技术
- **定义**：使用诱饵（蜜罐、蜜标、假数据）欺骗和检测攻击者的技术
- **说明**：欺骗技术主动布设陷阱，让攻击者暴露；如部署假凭证（Honeytoken），攻击者使用假凭证时触发告警
- **相关**：Honeypot（蜜罐）

---

## 密码学与哈希算法
### Decryption / 解密
- **音标**：/diːˈkrɪpʃn/
- **中文**：解密
- **定义**：将密文恢复为明文的过程
- **相关**：Encryption（加密）、Key（密钥）
### Defense in Depth / 纵深防御
- **中文**：纵深防御
- **定义**：使用多层安全控制保护系统的策略
- **说明**：纵深防御假设任何单层防御都可能被突破；多层包括：物理安全、网络安全、主机安全、应用安全、数据安全；如防火墙 + IDS + 杀毒软件 + 加密
- **相关**：Security（安全）、Firewall（防火墙）、IDS（入侵检测系统）
### DES (Data Encryption Standard) / 数据加密标准
- **发音**：/diː-iː-ɛs/
- **中文**：数据加密标准
- **定义**：早期的对称加密标准
- **说明**：DES 使用 56 位密钥，已被暴力破解（1999 年 22 小时）；被 3DES 和 AES 取代
- **相关**：3DES、AES、Symmetric Encryption（对称加密）
### Dictionary Attack / 字典攻击
- **中文**：字典攻击
- **定义**：使用常见密码列表尝试登录的攻击方法
- **说明**：字典攻击比暴力破解快，因为只尝试常见密码；防御方法：使用复杂密码、限制尝试次数
- **相关**：Brute Force（暴力破解）、Password（密码）
### Diffie-Hellman (DH) / Diffie-Hellman 密钥交换
- **发音**：/ˈdɪfi-ˈhɛlmən/
- **中文**：Diffie-Hellman 密钥交换
- **定义**：允许双方在不安全通道上协商共享密钥的协议
- **说明**：DH 基于离散对数问题；是 TLS/SSL、SSH 等协议的基础；ECDHE（椭圆曲线 DH 临时密钥）提供前向保密
- **相关**：Key Exchange（密钥交换）、TLS、Forward Secrecy（前向保密）
### Digital Signature / 数字签名
- **中文**：数字签名
- **定义**：验证消息来源和完整性的加密机制
- **说明**：发送者用私钥签名，接收者用公钥验证；确保消息未被篡改且来自声称的发送者；算法包括 RSA、DSA、ECDSA、EdDSA
- **相关**：Public Key（公钥）、Private Key（私钥）、Hash（哈希）
### Discretionary Access Control (DAC) / 自主访问控制
- **中文**：自主访问控制
- **定义**：资源所有者决定谁可以访问资源以及访问权限
- **说明**：DAC 灵活但安全性较低；Unix 文件权限（rwx）是 DAC 的典型实现；所有者可以任意修改权限
- **相关**：MAC（强制访问控制）、RBAC（基于角色的访问控制）、Access Control（访问控制）
### Disk Encryption / 磁盘加密
- **中文**：磁盘加密
- **定义**：加密整个磁盘或分区的数据
- **说明**：磁盘加密保护静态数据；代表：BitLocker（Windows）、FileVault（macOS）、LUKS（Linux）；需要密码或 TPM 解锁
- **相关**：Encryption（加密）、Data Encryption at Rest（静态数据加密）
### DMZ (Demilitarized Zone) / 非军事区
- **发音**：/diː-ɛm-ziː/
- **中文**：非军事区
- **定义**：位于外网（Internet）和内网之间的隔离网络区域
- **说明**：DMZ 放置对外提供服务的服务器（如 Web 服务器、邮件服务器）；即使 DMZ 服务器被攻破，内网仍有防火墙保护
- **相关**：Firewall（防火墙）、Network Security（网络安全）
### DNAT (Destination NAT) / 目的地址转换
- **发音**：/diː-næt/
- **中文**：目的地址转换
- **定义**：修改数据包目的 IP 地址的 NAT
- **说明**：DNAT 用于外网访问内网服务时，将公网 IP+端口映射到内网 IP+端口；Linux 使用 iptables -t nat -A PREROUTING -j DNAT
- **相关**：NAT（网络地址转换）、SNAT（源地址转换）、Port Forwarding（端口转发）
### DoS (Denial of Service) / 拒绝服务
- **发音**：/diː-oʊ-ɛs/
- **中文**：拒绝服务
- **定义**：使系统或服务无法为正常用户提供服务的攻击
- **说明**：DoS 通过耗尽资源（带宽、CPU、内存、连接数）实现；简单 DoS 来自单一源
- **相关**：DDoS（分布式拒绝服务）、Attack（攻击）
### ECC (Elliptic Curve Cryptography) / 椭圆曲线密码学
- **发音**：/iː-siː-siː/
- **中文**：椭圆曲线密码学
- **定义**：基于椭圆曲线数学的非对称加密技术
- **说明**：ECC 提供与 RSA 相当的安全性但密钥更短（如 256 位 ECC ≈ 3072 位 RSA）；性能更好，适合移动设备和 IoT；用于 TLS、比特币等
- **相关**：Asymmetric Encryption（非对称加密）、RSA
### EDR (Endpoint Detection and Response) / 端点检测与响应
- **发音**：/iː-diː-ɑːr/
- **中文**：端点检测与响应
- **定义**：监控端点（PC、服务器）活动并响应威胁的安全解决方案
- **说明**：EDR 收集端点行为数据（进程、网络、文件），使用 AI/ML 检测异常；支持威胁狩猎（Threat Hunting）和事件响应；代表：CrowdStrike、SentinelOne
- **相关**：IDS（入侵检测系统）、Antivirus（杀毒软件）
### Encryption / 加密
- **音标**：/ɪnˈkrɪpʃn/
- **中文**：加密
- **定义**：将明文转换为密文的过程，防止未授权访问
- **说明**：加密算法分为对称加密（单密钥）和非对称加密（公钥/私钥对）；加密是保护机密性的核心手段
- **相关**：Decryption（解密）、Cipher（密码）、Key（密钥）
### Endpoint Security / 端点安全
- **中文**：端点安全
- **定义**：保护终端设备（PC、服务器、移动设备、IoT）免受威胁
- **说明**：端点安全措施包括：杀毒软件、EDR、磁盘加密、设备控制、补丁管理、用户行为分析
- **相关**：EDR（端点检测与响应）、Antivirus（杀毒软件）
### EPP (Endpoint Protection Platform) / 端点保护平台
- **发音**：/iː-piː-piː/
- **中文**：端点保护平台
- **定义**：集成杀毒、防火墙、设备控制等功能的端点安全解决方案
- **说明**：EPP 是下一代杀毒软件；与 EDR 结合形成 XDR（Extended Detection and Response）
- **相关**：Antivirus（杀毒软件）、EDR（端点检测与响应）
### Exploit / 利用
- **音标**：/ˈeksplɔɪt/
- **中文**：利用
- **定义**：利用漏洞进行攻击的代码或技术
- **说明**：Exploit 可以是已知的（有补丁但未打）或零日（Zero-day，无补丁）；metasploit 是著名的渗透测试框架
- **相关**：Vulnerability（漏洞）、Payload（载荷）
### Exploit Kit / 利用工具包
- **中文**：利用工具包
- **定义**：集成多种 Exploit 的自动化攻击工具
- **说明**：利用工具包（如 Angler、Nuclear）通过网页漏洞自动攻击访问者；检测浏览器和插件版本，选择合适的 Exploit
- **相关**：Exploit（利用）、Malware（恶意软件）
### Fail-Open / 故障开放
- **中文**：故障开放
- **定义**：系统故障时允许访问的默认行为
- **说明**：故障开放可用性高但安全性低；通常不用于安全关键系统；某些场景（如紧急通道）使用故障开放
- **相关**：Fail-Safe（故障安全）
### Fail-Safe / 故障安全
- **中文**：故障安全
- **定义**：系统故障时进入安全状态的默认行为
- **说明**：故障安全默认拒绝访问；如防火墙规则冲突时默认阻止流量；与 Fail-Open（故障开放，允许所有流量）相对
- **相关**：Security（安全）、Reliability（可靠性）
### File-Level Encryption / 文件级加密
- **中文**：文件级加密
- **定义**：选择性加密单个文件或文件夹
- **说明**：文件级加密比全盘加密灵活，可以加密特定敏感文件；如 EFS（Windows 加密文件系统）、PGP、GnuPG
- **相关**：Encryption（加密）、Data Encryption at Rest（静态数据加密）
### FileVault
- **发音**：/faɪl-vɔːlt/
- **中文**：FileVault
- **定义**：macOS 全盘加密功能
- **说明**：FileVault 2 使用 XTS-AES-128 加密启动卷；使用用户密码或恢复密钥解锁
- **相关**：Disk Encryption（磁盘加密）、macOS
### Firewall / 防火墙
- **音标**：/ˈfaɪərwɔːl/
- **中文**：防火墙
- **定义**：监控和控制网络流量的安全系统
- **说明**：防火墙可以是硬件（专用设备）或软件（操作系统内置）；规则基于 IP、端口、协议、状态等；Linux 使用 iptables/nftables，Windows 使用 Windows Defender Firewall
- **相关**：iptables、nftables、Packet Filtering（包过滤）
### Forensics / 取证
- **音标**：/fəˈrenzɪks/
- **中文**：取证
- **定义**：收集、保存、分析数字证据的科学过程
- **说明**：数字取证用于调查安全事件、犯罪；原则：证据完整性、链式 custody、可重复性；工具：EnCase、FTK、Autopsy、Sleuth Kit
- **相关**：Incident Response（事件响应）、Evidence（证据）
### Format String Attack / 格式化字符串攻击
- **中文**：格式化字符串攻击
- **定义**：利用格式化函数（如 printf）的格式说明符漏洞读取或写入内存
- **说明**：如果 printf(user_input) 而非 printf("%s", user_input)，攻击者可以使用 %n 写入内存，%x 读取内存；防御：始终使用格式字符串
- **相关**：Vulnerability（漏洞）、Exploit（利用）
### Forward Secrecy (FS) / 前向保密
- **中文**：前向保密
- **定义**：即使长期私钥泄露，过去的会话密钥也不会泄露的属性
- **说明**：前向保密通过为每个会话使用临时密钥实现；即使攻击者获得服务器私钥，也无法解密历史流量；TLS 1.3 强制要求前向保密
- **同义词**：Perfect Forward Secrecy (PFS)
- **相关**：Diffie-Hellman（DH）、TLS、Key Exchange（密钥交换）
### Full Disk Encryption (FDE) / 全盘加密
- **中文**：全盘加密
- **定义**：加密整个存储设备的数据
- **说明**：全盘加密保护所有数据（操作系统、应用、用户数据）；启动时需要预启动认证（PBA）；性能影响通常很小（现代 CPU 有 AES-NI 加速）
- **相关**：Disk Encryption（磁盘加密）、BitLocker、FileVault、LUKS
### Hash / 哈希
- **音标**：/hæʃ/
- **中文**：哈希
- **定义**：将任意长度数据映射为固定长度值的单向函数
- **说明**：密码哈希（如 bcrypt、scrypt、Argon2）用于安全存储密码；哈希是单向的，无法从哈希值反推原始数据；加密哈希（如 SHA-256）用于数据完整性校验
- **相关**：Salt（盐）、Encryption（加密）、Checksum（校验和）
### HIDS (Host IDS) / 主机入侵检测系统
- **发音**：/eɪtʃ-aɪ-diː-ɛs/
- **中文**：主机入侵检测系统
- **定义**：监控单个主机活动检测入侵的 IDS
- **说明**：HIDS 分析系统日志、文件完整性、进程行为；代表：OSSEC、Tripwire
- **相关**：IDS（入侵检测系统）、NIDS（网络入侵检测系统）
### HMAC (Hash-based Message Authentication Code) / 基于哈希的消息认证码
- **发音**：/eɪtʃ-mæk/
- **中文**：基于哈希的消息认证码
- **定义**：使用哈希函数和密钥生成消息认证码的算法
- **说明**：HMAC 提供消息完整性和认证；如 HMAC-SHA256；广泛用于 API 认证（JWT 签名）、TLS 等
- **相关**：Hash（哈希）、Digital Signature（数字签名）、MAC（消息认证码）
### Honeynet / 蜜网
- **中文**：蜜网
- **定义**：由多个蜜罐组成的网络
- **说明**：蜜网模拟完整的网络环境，提供更真实的攻击场景；用于深入研究攻击者的行为和工具
- **相关**：Honeypot（蜜罐）
### Honeypot / 蜜罐
- **音标**：/ˈhʌnipaɪ/
- **中文**：蜜罐
- **定义**：故意设置的诱饵系统，用于吸引和监控攻击者
- **说明**：蜜罐模拟有漏洞的服务，记录攻击者的行为和技术；用于研究威胁、延迟攻击、收集证据；分为低交互（模拟服务）和高交互（真实系统）
- **相关**：Deception Technology（欺骗技术）、Honeynet（蜜网）
### HSM (Hardware Security Module) / 硬件安全模块
- **发音**：/eɪtʃ-ɛs-ɛm/
- **中文**：硬件安全模块
- **定义**：专用硬件设备，用于安全地生成、存储和管理加密密钥
- **说明**：HSM 提供最高级别的密钥保护，防篡改、防提取；用于 CA、银行、加密货币；代表：Thales Luna、AWS CloudHSM
- **相关**：TPM（可信平台模块）、Encryption（加密）、Key Management（密钥管理）
### HSTS (HTTP Strict Transport Security) / HTTP 严格传输安全
- **发音**：/eɪtʃ-tiː-ɛs-tiː-ɛs/
- **中文**：HTTP 严格传输安全
- **定义**：强制浏览器始终使用 HTTPS 访问网站的策略
- **说明**：HSTS 通过 HTTP 头 Strict-Transport-Security 设置；防止 SSL 剥离攻击；有预加载列表（HSTS Preload List）
- **相关**：HTTPS、TLS、MITM（中间人攻击）
### HTTPS (HTTP Secure) / 安全超文本传输协议
- **发音**：/eɪtʃ-tiː-tiː-piː-iː-ɛs/
- **中文**：安全超文本传输协议
- **定义**：使用 TLS 加密的 HTTP 协议
- **说明**：HTTPS 防止窃听和中间人攻击；端口 443；现代浏览器强制要求 HTTPS；Let's Encrypt 推动免费 HTTPS 普及
- **相关**：HTTP、TLS（传输层安全）、Certificate（证书）
### Identity Provider (IdP) / 身份提供者
- **中文**：身份提供者
- **定义**：提供身份认证服务的系统
- **说明**：IdP 验证用户身份并颁发令牌；如 Google、Microsoft Azure AD、Okta、Keycloak
- **相关**：SSO（单点登录）、Authentication（认证）
### IDS (Intrusion Detection System) / 入侵检测系统
- **发音**：/aɪ-diː-ɛs/
- **中文**：入侵检测系统
- **定义**：监控网络或系统活动，检测潜在入侵的系统
- **说明**：IDS 分为 NIDS（网络 IDS）和 HIDS（主机 IDS）；检测方法：签名检测（已知攻击模式）、异常检测（偏离基线）；只检测不阻止
- **相关**：IPS（入侵防御系统）、Firewall（防火墙）
### Incident Response / 事件响应
- **中文**：事件响应
- **定义**：检测、分析、遏制、消除安全事件并从中恢复的过程
- **说明**：事件响应流程：准备 → 检测分析 → 遏制 → 根除 → 恢复 → 事后总结；需要事件响应计划和团队（CSIRT、SOC）
- **相关**：SOC（安全运营中心）、Forensics（取证）
### Integer Overflow / 整数溢出
- **中文**：整数溢出
- **定义**：整数运算结果超出其类型表示范围，导致意外行为
- **说明**：整数溢出可能导致缓冲区分配过小（分配负数大小的绝对值），进而导致缓冲区溢出；防御：范围检查、使用更大类型、安全整数库
- **相关**：Buffer Overflow（缓冲区溢出）、Vulnerability（漏洞）
### Integrity / 完整性
- **音标**：/ɪnˈteɡrəti/
- **中文**：完整性
- **定义**：确保信息不被未授权地修改或破坏
- **说明**：完整性防止数据被篡改；通过校验和、数字签名、访问控制、写保护等实现；包括数据完整性和系统完整性
- **相关**：Security（安全）、Checksum（校验和）、Digital Signature（数字签名）
### Intermediate Certificate / 中间证书
- **中文**：中间证书
- **定义**：由根 CA 签发、用于签发服务器证书的证书
- **说明**：中间证书减少根证书的使用频率，提高安全性；证书链通常包含服务器证书、中间证书、根证书
- **相关**：CA（证书颁发机构）、Certificate（证书）、Certificate Chain（证书链）
### IOC (Indicator of Compromise) / 失陷指标
- **发音**：/aɪ-oʊ-siː/
- **中文**：失陷指标
- **定义**：表明系统可能被入侵的 Artifact
- **说明**：IOC 包括：恶意 IP 地址、域名、URL、文件哈希、注册表键、文件路径等；用于检测已知威胁
- **相关**：Threat Intelligence（威胁情报）、APT（高级持续性威胁）
### IPS (Intrusion Prevention System) / 入侵防御系统
- **发音**：/aɪ-piː-ɛs/
- **中文**：入侵防御系统
- **定义**：检测并主动阻止入侵的系统
- **说明**：IPS 是 IDS 的增强版，可以自动阻止检测到的攻击；可能产生误报导致合法流量被阻断
- **相关**：IDS（入侵检测系统）、Firewall（防火墙）
### IPsec (Internet Protocol Security) / 互联网协议安全
- **发音**：/aɪ-piː-sɛk/
- **中文**：互联网协议安全
- **定义**：为 IP 通信提供加密和认证的协议套件
- **说明**：IPsec 包括 AH（认证头）和 ESP（封装安全载荷）；支持传输模式（端到端）和隧道模式（VPN）；使用 IKE（Internet Key Exchange）协商密钥
- **相关**：VPN（虚拟专用网络）、Encryption（加密）、IKE
### iptables
- **发音**：/aɪ-piː-teɪblz/
- **中文**：iptables
- **定义**：Linux 的包过滤防火墙工具
- **说明**：iptables 使用表（Table）、链（Chain）、规则（Rule）组织；表包括 filter（过滤）、nat（地址转换）、mangle（修改包）、raw；逐渐被 nftables 取代
- **相关**：nftables、Firewall（防火墙）、Netfilter
### JWT (JSON Web Token) / JSON Web 令牌
- **发音**：/dʒɒt/
- **中文**：JSON Web 令牌
- **定义**： compact、自包含的方式用于在各方之间安全传输信息
- **说明**：JWT 包含头部（算法）、载荷（声明）、签名；用于认证和信息交换；注意：JWT 内容可解码，不应包含敏感信息
- **相关**：OAuth、Authentication（认证）
### KDC (Key Distribution Center) / 密钥分发中心
- **中文**：密钥分发中心
- **定义**：Kerberos 中负责认证和票据分发的服务器
- **说明**：KDC 包括 AS（Authentication Server，认证服务器）和 TGS（Ticket Granting Server，票据授权服务器）
- **相关**：Kerberos、Ticket（票据）
### Kerberos
- **发音**：/ˈkɜːrbərɒs/
- **中文**：Kerberos
- **定义**：网络认证协议，使用对称密钥加密实现强认证
- **说明**：Kerberos 由 MIT 开发；使用票据（Ticket）和密钥分发中心（KDC）；Windows Active Directory 使用 Kerberos；防止窃听和重放攻击
- **相关**：Authentication（认证）、KDC（密钥分发中心）、Ticket（票据）
### Key / 密钥
- **音标**：/kiː/
- **中文**：密钥
- **定义**：加密和解密数据所需的秘密信息
- **说明**：对称加密使用单一密钥；非对称加密使用公钥（公开）和私钥（保密）；密钥管理是安全的关键
- **相关**：Encryption（加密）、Key Management（密钥管理）
### Key Exchange / 密钥交换
- **中文**：密钥交换
- **定义**：双方安全地协商共享密钥的过程
- **说明**：密钥交换协议包括 DH、ECDH、RSA 密钥传输等；现代协议优先使用提供前向保密的临时密钥交换
- **相关**：Diffie-Hellman（DH）、Forward Secrecy（前向保密）
### Key Management / 密钥管理
- **中文**：密钥管理
- **定义**：生成、存储、分发、轮换、销毁加密密钥的全生命周期管理
- **说明**：密钥管理是密码学的核心挑战；好的密钥管理包括：使用强随机数生成器、安全存储（HSM/TPM）、定期轮换、最小权限访问、密钥分离
- **相关**：Encryption（加密）、HSM（硬件安全模块）、Key（密钥）
### Key Stretching / 密钥拉伸
- **中文**：密钥拉伸
- **定义**：通过多次哈希迭代故意减慢哈希计算速度，增加暴力破解难度
- **说明**：密钥拉伸用于密码哈希；如 bcrypt（基于 Blowfish，自适应成本因子）、PBKDF2、scrypt、Argon2；成本因子随硬件提升可调整
- **相关**：Hash（哈希）、Password（密码）、bcrypt
### Keylogger / 键盘记录器
- **音标**：/ˈkiː-lɒɡər/
- **中文**：键盘记录器
- **定义**：记录用户键盘输入的软件或硬件
- **说明**：键盘记录器可以是恶意软件，也可以是合法监控工具；可以窃取密码、信用卡号等敏感信息
- **相关**：Spyware（间谍软件）、Malware（恶意软件）
### Let's Encrypt
- **发音**：/lɛts-ɛn-krɪpt/
- **中文**：Let's Encrypt
- **定义**：免费的自动化证书颁发机构
- **说明**：Let's Encrypt 由 ISRG 运营，提供免费的 DV（域名验证）证书；通过 ACME 协议自动化证书申请和续期；推动 HTTPS 普及
- **相关**：CA（证书颁发机构）、Certificate（证书）、ACME
### Log / 日志
- **音标**：/lɒɡ/
- **中文**：日志
- **定义**：系统或应用运行时事件的记录
- **说明**：日志包括：系统日志（syslog）、应用日志、安全日志、访问日志；用于故障排查、安全审计、性能分析；需要保护日志的完整性和机密性
- **相关**：Audit Trail（审计跟踪）、SIEM（安全信息和事件管理）
### Log Rotation / 日志轮转
- **中文**：日志轮转
- **定义**：自动归档和删除旧日志的机制
- **说明**：日志轮转防止日志文件无限增长；如 logrotate 按大小或时间轮转日志，压缩旧日志，删除过旧日志
- **相关**：Log（日志）、logrotate
### logrotate
- **发音**：/lɒɡ-roʊ-teɪt/
- **中文**：logrotate
- **定义**：Linux 日志轮转工具
- **说明**：logrotate 按配置定期轮转、压缩、删除日志；支持按大小、日期、数量轮转；防止磁盘空间耗尽
- **相关**：Log Rotation（日志轮转）、Log（日志）
### LUKS (Linux Unified Key Setup) / Linux 统一密钥设置
- **发音**：/luːks/
- **中文**：Linux 统一密钥设置
- **定义**：Linux 磁盘加密标准
- **说明**：LUKS 是 dm-crypt 的密钥管理扩展；支持多密码、密钥派生、Header 备份；是 Linux 全盘加密的事实标准
- **相关**：Disk Encryption（磁盘加密）、dm-crypt
### MAC (Message Authentication Code) / 消息认证码
- **发音**：/mæk/
- **中文**：消息认证码
- **定义**：用于验证消息完整性和来源的短信息
- **说明**：MAC 需要共享密钥；与数字签名不同，MAC 使用对称密钥；HMAC 和 CMAC 是常用 MAC 算法
- **相关**：HMAC、Digital Signature（数字签名）
### Malware / 恶意软件
- **音标**：/ˈmælwer/
- **中文**：恶意软件
- **定义**：旨在破坏、干扰或未经授权访问计算机系统的软件
- **说明**：恶意软件类型包括：病毒（Virus）、蠕虫（Worm）、木马（Trojan）、勒索软件（Ransomware）、间谍软件（Spyware）、广告软件（Adware）、Rootkit
- **相关**：Virus（病毒）、Worm（蠕虫）、Trojan（木马）
### Mandatory Access Control (MAC) / 强制访问控制
- **中文**：强制访问控制
- **定义**：由系统根据安全策略强制实施的访问控制，用户不能绕过
- **说明**：MAC 安全性高；每个主体（进程）和客体（资源）都有安全标签；访问决策基于标签比较；SELinux、AppArmor 实现 MAC
- **相关**：DAC（自主访问控制）、RBAC（基于角色的访问控制）、Security Policy（安全策略）
### Masking / 脱敏
- **中文**：脱敏
- **定义**：隐藏或替换敏感数据的部分内容
- **说明**：数据脱敏用于非生产环境（开发、测试）；如身份证号 123456**********；静态脱敏（永久修改）和动态脱敏（实时替换）
- **相关**：Data Security（数据安全）、Tokenization（令牌化）

---

## 日志与监控
### MD5 / 消息摘要算法 5
- **发音**：/ɛm-diː-faɪv/
- **中文**：MD5
- **定义**：广泛使用的 128 位哈希算法
- **说明**：MD5 已被证明不安全（碰撞攻击）；不再用于安全场景，但仍用于校验文件完整性（非安全场景）
- **相关**：Hash（哈希）、SHA-1、SHA-256
### Metrics / 指标
- **中文**：指标
- **定义**：可量化的系统性能度量
- **说明**：指标包括：CPU 使用率、内存使用率、请求延迟、错误率、吞吐量；时序数据库（如 Prometheus、InfluxDB）存储指标
- **相关**：Monitoring（监控）、Observability（可观测性）
### Micro-segmentation / 微分段
- **中文**：微分段
- **定义**：将网络划分为细小隔离区域的安全技术
- **说明**：微分段限制攻击者在网络中的横向移动；每个工作负载（VM、容器）有自己的安全策略；软件定义网络（SDN）实现微分段
- **相关**：Zero Trust（零信任）、Network Security（网络安全）
### MITM (Man-in-the-Middle) / 中间人攻击
- **发音**：/ɛm-aɪ-tiː-ɛm/
- **中文**：中间人攻击
- **定义**：攻击者插入通信双方之间，窃听或篡改通信内容的攻击
- **说明**：MITM 可以通过 ARP 欺骗、DNS 欺骗、伪造证书等实现；防御：使用 HTTPS/TLS、证书固定（Certificate Pinning）、HSTS
- **相关**：ARP Spoofing（ARP 欺骗）、HTTPS、TLS
### Monitoring / 监控
- **中文**：监控
- **定义**：持续观察系统和应用状态的活动
- **说明**：监控包括：基础设施监控（CPU、内存、磁盘、网络）、应用监控（性能、错误）、安全监控（告警、事件）；工具：Prometheus、Grafana、Zabbix、Nagios
- **相关**：Alerting（告警）、Metrics（指标）、Observability（可观测性）
### Multi-Factor Authentication (MFA) / 多因素认证
- **中文**：多因素认证
- **定义**：需要两种或更多认证因素的身份验证
- **说明**：MFA 比 2FA 更安全；如密码 + 手机验证码 + 指纹；企业系统 increasingly 要求 MFA
- **相关**：Two-Factor Authentication（双因素认证）、Authentication（认证）
### NAT (Network Address Translation) / 网络地址转换
- **发音**：/næt/
- **中文**：网络地址转换
- **定义**：修改网络包中的 IP 地址的技术
- **说明**：NAT 允许多个设备共享一个公网 IP；类型包括 SNAT（源 NAT）、DNAT（目的 NAT）、MASQUERADE；也提供一定的安全隔离
- **相关**：Firewall（防火墙）、IP Masquerade（IP 伪装）、Port Forwarding（端口转发）
### Netfilter
- **发音**：/nɛt-fɪltər/
- **中文**：Netfilter
- **定义**：Linux 内核的包过滤框架
- **说明**：Netfilter 是内核模块，提供包过滤、NAT、包修改的钩子点；iptables/nftables 是用户空间工具，通过 Netfilter 实现功能
- **相关**：iptables、nftables、Firewall（防火墙）
### nftables
- **发音**：/ɛn-ɛf-teɪblz/
- **中文**：nftables
- **定义**：Linux 新一代包过滤框架，替代 iptables
- **说明**：nftables 提供更统一的语法、更好的性能和可扩展性；使用单一工具 nft 替代 iptables、ip6tables、arptables、ebtables
- **相关**：iptables、Netfilter、Firewall（防火墙）
### NIDS (Network IDS) / 网络入侵检测系统
- **发音**：/ɛn-aɪ-diː-ɛs/
- **中文**：网络入侵检测系统
- **定义**：监控网络流量检测入侵的 IDS
- **说明**：NIDS 部署在网络关键点（如 DMZ 入口），分析所有经过的流量；代表：Snort、Suricata、Zeek
- **相关**：IDS（入侵检测系统）、HIDS（主机入侵检测系统）
### NVD (National Vulnerability Database) / 国家漏洞数据库
- **发音**：/ɛn-viː-diː/
- **中文**：国家漏洞数据库
- **定义**：美国 NIST 维护的漏洞数据库
- **说明**：NVD 包含 CVE 漏洞信息、CVSS 评分、CPE（通用平台枚举）；是漏洞管理的重要资源
- **相关**：CVE、CVSS、Vulnerability（漏洞）
### OAuth
- **发音**：/oʊ-ɔːθ/
- **中文**：OAuth
- **定义**：开放授权协议，允许第三方应用访问用户资源而无需密码
- **说明**：OAuth 2.0 是 Web 和移动应用的标准授权协议；用户授权后，应用获得访问令牌（Access Token）；如"使用 Google 登录"
- **相关**：Authentication（认证）、Authorization（授权）、OpenID Connect
### Object / 客体
- **音标**：/ˈɒbdʒɪkt/
- **中文**：客体
- **定义**：被访问的资源，如文件、进程、内存、设备
- **说明**：主体对客体执行操作；客体需要被保护，防止未授权访问
- **相关**：Subject（主体）、Access Control（访问控制）

---

## 身份认证
### Observability / 可观测性
- **中文**：可观测性
- **定义**：通过系统输出来理解系统内部状态的能力
- **说明**：可观测性三大支柱：Metrics（指标）、Logs（日志）、Traces（追踪）；比传统监控更主动；代表：Prometheus + Grafana + Jaeger/Zipkin
- **相关**：Monitoring（监控）、Metrics（指标）、Tracing（追踪）
### OCSP (Online Certificate Status Protocol) / 在线证书状态协议
- **发音**：/oʊ-siː-ɛs-piː/
- **中文**：在线证书状态协议
- **定义**：实时查询证书状态的协议
- **说明**：OCSP 比 CRL 更高效（只查询单个证书状态）；但存在隐私问题（OCSP 服务器知道用户访问哪些网站）；OCSP Stapling 解决隐私问题
- **相关**：CRL（证书撤销列表）、Certificate（证书）
### OCSP Stapling / OCSP 装订
- **中文**：OCSP 装订
- **定义**：服务器预先获取 OCSP 响应并随证书一起发送给客户端
- **说明**：OCSP Stapling 减少客户端查询 OCSP 的延迟和隐私问题；响应有有效期，需要定期更新
- **相关**：OCSP、Certificate（证书）、TLS
### OpenID Connect (OIDC) / OpenID 连接
- **发音**：/oʊ-pən-aɪ-diː-kəˈnekt/
- **中文**：OpenID 连接
- **定义**：基于 OAuth 2.0 的身份层协议
- **说明**：OIDC 在 OAuth 2.0 上添加身份认证，返回 ID Token（包含用户信息的 JWT）；是现代 Web SSO 的标准
- **相关**：OAuth、Authentication（认证）、JWT
### Packet Filtering / 包过滤
- **中文**：包过滤
- **定义**：根据规则检查每个网络包并决定允许或拒绝的技术
- **说明**：包过滤是最基本的防火墙功能；检查包头信息（源/目的 IP、端口、协议）；无状态包过滤不跟踪连接状态
- **相关**：Firewall（防火墙）、Stateful Inspection（状态检测）
### Password / 密码
- **音标**：/ˈpæswɜːrd/
- **中文**：密码
- **定义**：用户用于证明身份的字符串
- **说明**：密码应足够长、复杂（大小写字母、数字、符号）；不应明文存储，应存储哈希值（Hash）和盐（Salt）
- **相关**：Hash（哈希）、Salt（盐）、Authentication（认证）
### Patch / 补丁
- **音标**：/pætʃ/
- **中文**：补丁
- **定义**：修复软件漏洞或错误的更新
- **说明**：及时打补丁是防止漏洞利用的关键；补丁管理（Patch Management）是企业安全的重要流程；Windows Update、yum update、apt upgrade
- **相关**：Vulnerability（漏洞）、Update（更新）
### Payload / 载荷
- **音标**：/ˈpeɪloʊd/
- **中文**：载荷
- **定义**：攻击中实际执行的恶意代码
- **说明**：Exploit 利用漏洞后，Payload 执行恶意操作（如反向 Shell、植入木马、加密文件）
- **相关**：Exploit（利用）、Malware（恶意软件）
### PBKDF2 (Password-Based Key Derivation Function 2) / 基于密码的密钥派生函数 2
- **发音**：/piː-biː-keɪ-diː-ɛf-tuː/
- **中文**：基于密码的密钥派生函数 2
- **定义**：从密码生成密钥的标准算法
- **说明**：PBKDF2 使用伪随机函数（如 HMAC-SHA256）多次迭代；NIST 推荐；用于 WPA2、FileVault 等
- **相关**：Password（密码）、Key Derivation（密钥派生）
### Pepper / 胡椒
- **音标**：/ˈpepər/
- **中文**：胡椒
- **定义**：类似于盐，但存储在服务器端（不随哈希值存储）的额外随机数据
- **说明**：Pepper 是全局秘密值，即使数据库泄露，没有 Pepper 也无法破解密码；与 Salt 配合使用
- **相关**：Salt（盐）、Hash（哈希）、Password（密码）
### Phishing / 钓鱼
- **发音**：/ˈfɪʃɪŋ/
- **中文**：钓鱼
- **定义**：伪装成可信实体发送欺诈性通信（通常是邮件），诱骗用户提供敏感信息
- **说明**：钓鱼邮件通常包含恶意链接或附件；变种包括 Spear Phishing（定向钓鱼）、Whaling（鲸钓，针对高管）；防御：邮件过滤、用户教育、双因素认证
- **相关**：Social Engineering（社会工程）、Attack（攻击）
### PKI (Public Key Infrastructure) / 公钥基础设施
- **发音**：/piː-keɪ-aɪ/
- **中文**：公钥基础设施
- **定义**：管理公钥加密密钥和数字证书的系统
- **说明**：PKI 包括：CA、RA（注册机构）、证书库、证书撤销列表（CRL）、OCSP 等；是数字信任的基础
- **相关**：CA（证书颁发机构）、Certificate（证书）、Digital Signature（数字签名）
### Port Forwarding / 端口转发
- **中文**：端口转发
- **定义**：将网络包从一个端口转发到另一个端口或主机的技术
- **说明**：端口转发用于外网访问内网服务、负载均衡等；可以通过 DNAT 或应用层（如 SSH 端口转发）实现
- **相关**：NAT（网络地址转换）、DNAT（目的地址转换）
### Principal / 主体
- **音标**：/ˈprɪnsəpl/
- **中文**：主体
- **定义**：请求访问资源的实体，可以是用户、进程、服务
- **说明**：安全模型中，主体（Subject）对客体（Object）执行操作；主体需要被认证和授权
- **相关**：Subject（主体）、Object（客体）、Access Control（访问控制）
### Principle of Least Privilege / 最小权限原则
- **中文**：最小权限原则
- **定义**：每个进程/用户只获得完成工作所需的最小权限
- **说明**：最小权限原则减少攻击面；如普通用户不应有 root 权限，Web 服务器不应有 shell 访问权限；容器和微服务架构遵循此原则
- **相关**：Access Control（访问控制）、Capability（能力）
### Private Key / 私钥
- **中文**：私钥
- **定义**：非对称加密中必须保密的密钥
- **说明**：私钥用于解密数据或生成签名；泄露私钥会导致安全风险；需要安全存储（如硬件安全模块 HSM）
- **相关**：Public Key（公钥）、Asymmetric Encryption（非对称加密）
### Privilege Escalation / 权限提升
- **中文**：权限提升
- **定义**：从低权限用户获取更高权限的攻击
- **说明**：权限提升分为水平提升（访问同级其他用户数据）和垂直提升（从普通用户到管理员）；利用系统漏洞、配置错误、弱密码等
- **相关**：Vulnerability（漏洞）、Exploit（利用）

---

## 安全机制
### Protection / 保护
- **音标**：/prəˈtekʃn/
- **中文**：保护
- **定义**：操作系统提供的机制，控制进程对系统资源的访问
- **说明**：保护是操作系统内部的安全机制；包括内存保护、文件保护、CPU 保护等；防止进程有意或无意地破坏其他进程或操作系统
- **相关**：Security（安全）、Access Control（访问控制）、Privilege（特权）
### Public Key / 公钥
- **中文**：公钥
- **定义**：非对称加密中可以公开的密钥
- **说明**：公钥用于加密数据或验证签名；可以安全地分发给任何人；与私钥成对生成
- **相关**：Private Key（私钥）、Asymmetric Encryption（非对称加密）
### Rainbow Table / 彩虹表
- **中文**：彩虹表
- **定义**：预计算的密码哈希表，用于快速破解哈希密码
- **说明**：彩虹表通过时间-内存权衡加速密码破解；使用盐可以使彩虹表失效
- **相关**：Hash（哈希）、Salt（盐）、Password（密码）
### Ransomware / 勒索软件
- **音标**：/ˈrænsəmwer/
- **中文**：勒索软件
- **定义**：加密用户文件并要求赎金解密的恶意软件
- **说明**：勒索软件（如 WannaCry、NotPetya、Locky）造成巨大损失；防御：备份、及时补丁、用户教育
- **相关**：Malware（恶意软件）、Encryption（加密）
### Role / 角色
- **音标**：/roʊl/
- **中文**：角色
- **定义**：一组权限的集合，代表用户在组织中的职能
- **说明**：RBAC 中，角色简化权限管理；如"管理员"角色拥有所有权限，"编辑"角色拥有读写权限，"访客"角色只有读权限
- **相关**：RBAC（基于角色的访问控制）、Permission（权限）
### Role-Based Access Control (RBAC) / 基于角色的访问控制
- **中文**：基于角色的访问控制
- **定义**：根据用户的角色分配权限的访问控制模型
- **说明**：RBAC 中，权限与角色关联，用户与角色关联；简化权限管理；如管理员角色、普通用户角色、访客角色
- **相关**：DAC（自主访问控制）、MAC（强制访问控制）、Role（角色）
### Root Certificate / 根证书
- **中文**：根证书
- **定义**：证书链顶端的自签名证书，预装在系统中
- **说明**：根证书是信任锚；如果根证书被泄露或错误签发，影响范围极大；根 CA 通常离线保存根证书私钥
- **相关**：CA（证书颁发机构）、Certificate（证书）、Certificate Chain（证书链）
### Rootkit / Root 工具包
- **发音**：/ˈruːt-kɪt/
- **中文**：Root 工具包
- **定义**：隐藏自身和其他恶意软件存在的工具集
- **说明**：Rootkit 修改操作系统内核或系统工具，隐藏进程、文件、网络连接；极难检测和清除；可能需要重装系统
- **相关**：Malware（恶意软件）、Backdoor（后门）
### RSA
- **发音**：/ɑːr-ɛs-eɪ/
- **中文**：RSA
- **定义**：广泛使用的非对称加密算法
- **说明**：RSA 基于大整数分解的数学难题；用于加密、数字签名、密钥交换；密钥长度通常为 2048 或 4096 位
- **相关**：Asymmetric Encryption（非对称加密）、Public Key（公钥）、Digital Signature（数字签名）
### rsyslog
- **发音**：/ɑːr-ˈsɪslɒɡ/
- **中文**：rsyslog
- **定义**：增强版 Syslog 守护进程
- **说明**：rsyslog 是 Linux 默认日志系统；支持 TCP、TLS、过滤、模板、数据库输出、高吞吐量；替代传统 syslogd
- **相关**：Syslog、Log（日志）
### Salt / 盐
- **音标**：/sɔːlt/
- **中文**：盐
- **定义**：添加到密码之前的随机数据，用于增加哈希的唯一性
- **说明**：相同密码使用不同盐会得到不同哈希值；防止彩虹表攻击；每个密码应使用独立随机盐
- **相关**：Hash（哈希）、Password（密码）、Rainbow Table（彩虹表）
### SAML (Security Assertion Markup Language) / 安全断言标记语言
- **发音**：/sæməl/
- **中文**：安全断言标记语言
- **定义**：基于 XML 的 SSO 和身份联合标准
- **说明**：SAML 用于企业级 Web SSO；定义身份提供者（IdP）和服务提供者（SP）之间的断言交换；逐渐被 OIDC 取代
- **相关**：SSO（单点登录）、Authentication（认证）

---

## 加密
### SAN (Subject Alternative Name) / 主题备用名称
- **中文**：主题备用名称
- **定义**：证书扩展字段，包含证书适用的额外域名或 IP 地址
- **说明**：SAN 证书可以保护多个不同域名（如 example.com、example.org）；比通配符证书更灵活安全
- **相关**：Certificate（证书）、Wildcard Certificate（通配符证书）

---

## 网络安全
### Sandbox / 沙箱
- **音标**：/ˈsændbɒks/
- **中文**：沙箱
- **定义**：同 Sandboxing
- **相关**：Sandboxing（沙箱）
### Sandboxing / 沙箱
- **中文**：沙箱
- **定义**：隔离运行不可信代码的安全机制
- **说明**：沙箱限制代码的访问权限（文件系统、网络、系统调用）；浏览器使用沙箱隔离网页代码；容器、虚拟机也是沙箱技术
- **相关**：Container（容器）、Virtual Machine（虚拟机）、Seccomp
### scrypt
- **发音**：/ɛs-kript/
- **中文**：scrypt
- **定义**：密码密钥派生函数，设计为对硬件攻击（ASIC、FPGA）有抵抗力
- **说明**：scrypt 需要大量内存，使专用硬件的优势降低；用于加密货币（Litecoin）和密码存储
- **相关**：Password（密码）、Hash（哈希）、bcrypt
### Secure Boot / 安全启动
- **中文**：安全启动
- **定义**：确保系统只加载可信软件的启动过程
- **说明**：Secure Boot 使用 UEFI 和数字签名验证引导加载程序、操作系统内核的签名；防止 Rootkit 和 Bootkit 攻击；Windows、Linux 支持
- **相关**：UEFI、Bootloader（引导加载程序）、Digital Signature（数字签名）
### Security / 安全
- **音标**：/sɪˈkjʊərəti/
- **中文**：安全
- **定义**：保护系统资源免受未经授权的访问、使用、披露、破坏、修改或破坏
- **说明**：安全涵盖物理安全、网络安全、操作系统安全、应用安全、数据安全等多个层面；目标是确保机密性（Confidentiality）、完整性（Integrity）、可用性（Availability）
- **相关**：Protection（保护）、Confidentiality（机密性）、Integrity（完整性）、Availability（可用性）
### Self-Signed Certificate / 自签名证书
- **中文**：自签名证书
- **定义**：由证书所有者自己签名的证书，而非由 CA 签名
- **说明**：自签名证书免费且易于创建，但不被浏览器/操作系统信任（需要手动添加例外）；适合内部测试环境
- **相关**：Certificate（证书）、CA（证书颁发机构）
### Separation of Duties / 职责分离
- **中文**：职责分离
- **定义**：将关键任务分解给多个人的安全策略
- **说明**：职责分离防止单个人滥用权限；如银行中，一个人不能同时审批和付款；IT 中，开发人员不应直接部署生产环境
- **相关**：Access Control（访问控制）、Security（安全）
### SGX (Software Guard Extensions) / 软件保护扩展
- **发音**：/ɛs-dʒiː-ɛks/
- **中文**：软件保护扩展
- **定义**：Intel 的 TEE 技术，允许应用创建安全的 enclave（飞地）
- **说明**：SGX enclave 是 CPU 保护的内存区域，连操作系统和 Hypervisor 都无法访问；用于保护敏感计算；但有侧信道攻击风险
- **相关**：TEE（可信执行环境）、Intel
### SHA-1 / 安全哈希算法 1
- **发音**：/ʃɑː-wʌn/
- **中文**：SHA-1
- **定义**：160 位哈希算法
- **说明**：SHA-1 已被证明不安全（Google 2017 年成功碰撞）；逐步被淘汰；用于旧系统兼容
- **相关**：SHA-256、MD5、Hash（哈希）
### SHA-256 / 安全哈希算法 256
- **发音**：/ʃɑː-tuː-fɪf-tiː-sɪks/
- **中文**：SHA-256
- **定义**：256 位哈希算法，SHA-2 家族成员
- **说明**：SHA-256 目前安全，广泛用于区块链（比特币）、数字签名、证书；SHA-2 家族还包括 SHA-384、SHA-512
- **相关**：SHA-1、SHA-3、Hash（哈希）
### SHA-3 / 安全哈希算法 3
- **发音**：/ʃɑː-thriː/
- **中文**：SHA-3
- **定义**：基于 Keccak 算法的哈希标准
- **说明**：SHA-3 与 SHA-2 设计不同，提供备用方案；目前 SHA-2 仍安全，SHA-3 用于需要不同设计的场景
- **相关**：SHA-256、Keccak、Hash（哈希）
### SIEM (Security Information and Event Management) / 安全信息和事件管理
- **发音**：/siːm/
- **中文**：安全信息和事件管理
- **定义**：收集、分析、关联安全日志和事件的平台
- **说明**：SIEM 聚合防火墙、IDS、服务器、应用等日志；实时检测威胁、生成告警、支持调查；代表：Splunk、IBM QRadar、ArcSight
- **相关**：IDS（入侵检测系统）、Log Management（日志管理）
### Single Sign-On (SSO) / 单点登录
- **中文**：单点登录
- **定义**：用户一次认证后可以访问多个系统的机制
- **说明**：SSO 提高用户体验，减少密码管理；实现协议包括 SAML、OAuth、OpenID Connect、Kerberos
- **相关**：Authentication（认证）、Identity Provider（身份提供者）
### SNAT (Source NAT) / 源地址转换
- **发音**：/ɛs-næt/
- **中文**：源地址转换
- **定义**：修改数据包源 IP 地址的 NAT
- **说明**：SNAT 用于内网设备访问外网时，将私有 IP 转换为公网 IP；Linux 使用 iptables -t nat -A POSTROUTING -j SNAT
- **相关**：NAT（网络地址转换）、DNAT（目的地址转换）
### SOC (Security Operations Center) / 安全运营中心
- **发音**：/ɛs-oʊ-siː/
- **中文**：安全运营中心
- **定义**：集中监控和响应安全事件的团队/设施
- **说明**：SOC 7x24 监控安全告警，进行事件分析、调查和响应；使用 SIEM、EDR、威胁情报等工具
- **相关**：SIEM（安全信息和事件管理）、Incident Response（事件响应）
### Social Engineering / 社会工程
- **中文**：社会工程
- **定义**：通过欺骗、操纵人来获取信息或访问权限的攻击
- **说明**：社会工程不利用技术漏洞，而是利用人的弱点；如钓鱼邮件（Phishing）、假冒身份、 tailgating；防御：安全培训、验证流程
- **相关**：Phishing（钓鱼）、Attack（攻击）
### Spear Phishing / 定向钓鱼
- **中文**：定向钓鱼
- **定义**：针对特定个人或组织的钓鱼攻击
- **说明**：Spear Phishing 使用个人信息（如姓名、职位）提高可信度；比广撒网式钓鱼更危险
- **相关**：Phishing（钓鱼）、Social Engineering（社会工程）
### Spyware / 间谍软件
- **音标**：/ˈspaɪwer/
- **中文**：间谍软件
- **定义**：秘密收集用户信息的恶意软件
- **说明**：间谍软件窃取密码、浏览历史、键盘输入等；通常与合法软件捆绑安装
- **相关**：Malware（恶意软件）、Keylogger（键盘记录器）
### SQL Injection / SQL 注入
- **中文**：SQL 注入
- **定义**：通过输入恶意 SQL 代码来操纵数据库的攻击
- **说明**：SQL 注入是 Web 应用最常见的漏洞之一；可以读取、修改、删除数据库数据，甚至执行系统命令；防御：参数化查询、ORM、输入验证
- **相关**：Injection（注入）、Web Security（Web 安全）
### SSH (Secure Shell) / 安全外壳协议
- **发音**：/ɛs-ɛs-eɪtʃ/
- **中文**：安全外壳协议
- **定义**：安全的远程登录和命令执行协议
- **说明**：SSH 替代不安全的 Telnet；使用公钥认证；支持端口转发、文件传输（SCP/SFTP）；端口 22；OpenSSH 是最常用实现
- **相关**：Telnet、Public Key（公钥）、Port Forwarding（端口转发）
### SSL (Secure Sockets Layer) / 安全套接层
- **发音**：/ɛs-ɛs-ɛl/
- **中文**：安全套接层
- **定义**：TLS 的前身，已废弃
- **说明**：SSL 3.0 有严重漏洞（POODLE 攻击）；所有现代系统应使用 TLS 1.2 或 TLS 1.3
- **相关**：TLS（传输层安全）、HTTPS
### Stateful Inspection / 状态检测
- **中文**：状态检测
- **定义**：跟踪网络连接状态并根据状态允许流量的防火墙技术
- **说明**：状态检测防火墙维护连接表，允许已建立连接的返回流量；比无状态包过滤更安全灵活
- **相关**：Firewall（防火墙）、Packet Filtering（包过滤）
### Subject / 主体
- **中文**：主体
- **定义**：同 Principal
- **相关**：Principal（主体）、Object（客体）
### Symmetric Encryption / 对称加密
- **中文**：对称加密
- **定义**：加密和解密使用相同密钥的加密方式
- **说明**：对称加密速度快，适合大数据量加密；但需要安全地共享密钥；算法包括 AES、DES、3DES、ChaCha20
- **相关**：Asymmetric Encryption（非对称加密）、AES、DES
### Syslog
- **发音**：/ˈsɪslɒɡ/
- **中文**：Syslog
- **定义**：Unix/Linux 系统的标准日志协议
- **说明**：Syslog 通过 UDP/TCP 514 端口传输日志；分为 facility（日志来源）和 priority（严重级别）；现代系统使用 rsyslog、syslog-ng
- **相关**：Log（日志）、rsyslog
### TDE (Transparent Data Encryption) / 透明数据加密
- **发音**：/tiː-diː-iː/
- **中文**：透明数据加密
- **定义**：数据库自动加密数据的存储层加密技术
- **说明**：TDE 对应用透明，无需修改应用；加密数据库文件和备份；运行时数据在内存中是明文的；代表：SQL Server TDE、Oracle TDE、MySQL TDE
- **相关**：Database Encryption（数据库加密）、Encryption（加密）
### TEE (Trusted Execution Environment) / 可信执行环境
- **发音**：/tiː-iː-iː/
- **中文**：可信执行环境
- **定义**：与主操作系统隔离的安全执行环境
- **说明**：TEE 保证代码和数据的机密性和完整性；实现包括 ARM TrustZone、Intel SGX、AMD SEV；用于安全支付、密钥管理、隐私计算
- **相关**：Trust Zone（信任区）、Secure Boot（安全启动）
### Telnet
- **发音**：/ˈtɛlnɛt/
- **中文**：Telnet
- **定义**：不安全的远程登录协议
- **说明**：Telnet 以明文传输数据（包括密码）；已被 SSH 取代；现在仅用于测试或嵌入式设备调试
- **相关**：SSH（安全外壳协议）
### Threat / 威胁
- **音标**：/θret/
- **中文**：威胁
- **定义**：可能对系统安全造成危害的潜在事件或行为
- **说明**：威胁来源包括：恶意软件、黑客、内部人员、自然灾害等；威胁建模（Threat Modeling）用于识别和评估威胁
- **相关**：Attack（攻击）、Vulnerability（漏洞）、Risk（风险）
### Threat Hunting / 威胁狩猎
- **中文**：威胁狩猎
- **定义**：主动搜索网络中潜伏的高级威胁（APT）的安全活动
- **说明**：威胁狩猎假设攻击者已经入侵系统，主动搜索其痕迹；基于假设驱动，使用日志分析、行为分析、威胁情报
- **相关**：APT（高级持续性威胁）、EDR（端点检测与响应）
### Threat Intelligence / 威胁情报
- **中文**：威胁情报
- **定义**：关于现有或新兴威胁的知识和数据
- **说明**：威胁情报包括：IOC（失陷指标，如恶意 IP、域名、文件哈希）、TTP（战术、技术和程序）、威胁行为者信息；用于主动防御和检测
- **相关**：IOC（失陷指标）、APT（高级持续性威胁）
### Ticket / 票据
- **音标**：/ˈtɪkɪt/
- **中文**：票据
- **定义**：Kerberos 中用于证明身份和访问权限的加密凭证
- **说明**：票据授予票据（TGT）用于获取服务票据（Service Ticket）；票据有时效性，过期后需要重新获取
- **相关**：Kerberos、KDC（密钥分发中心）
### TLS (Transport Layer Security) / 传输层安全
- **发音**：/tiː-ɛl-ɛs/
- **中文**：传输层安全
- **定义**：为网络通信提供加密和认证的协议
- **说明**：TLS 是 SSL 的继任者；TLS 1.2 和 TLS 1.3 是现行版本；用于 HTTPS、SMTPS、IMAPS 等；握手过程协商加密算法和密钥
- **同义词**：SSL（Secure Sockets Layer，已废弃）
- **相关**：HTTPS、Encryption（加密）、Certificate（证书）
### TOCTOU (Time-of-Check to Time-of-Use) / 检查时间到使用时间
- **发音**：/tɒk-tuː/
- **中文**：检查时间到使用时间
- **定义**：在检查条件和使用资源之间，条件被改变的竞态条件
- **说明**：如程序检查文件权限后打开文件，但攻击者在检查和打开之间替换文件；防御：原子操作、文件描述符传递
- **相关**：Race Condition（竞态条件）、Vulnerability（漏洞）
### Token / 令牌
- **音标**：/ˈtoʊkən/
- **中文**：令牌
- **定义**：用于身份验证的物理或数字凭证
- **说明**：物理令牌（如 RSA SecurID、YubiKey）生成一次性密码；数字令牌（如 JWT、OAuth Token）用于 Web 认证
- **相关**：Authentication（认证）、OAuth、JWT
### Tokenization / 令牌化
- **中文**：令牌化
- **定义**：将敏感数据替换为无意义的令牌（Token）的技术
- **说明**：令牌化用于支付卡号（PCI DSS）、身份证号等敏感数据；原始数据存储在安全保险库中；令牌可以保留格式（如信用卡号格式）
- **相关**：Data Security（数据安全）、Encryption（加密）
### TPM (Trusted Platform Module) / 可信平台模块
- **发音**：/tiː-piː-ɛm/
- **中文**：可信平台模块
- **定义**：硬件安全芯片，提供加密密钥管理和平台完整性验证
- **说明**：TPM 存储密钥、证书、哈希值；支持安全启动、BitLocker、Windows Hello；TPM 2.0 是当前标准
- **相关**：Secure Boot（安全启动）、Encryption（加密）
### Tracing / 追踪
- **中文**：追踪
- **定义**：记录请求在分布式系统中传播路径的技术
- **说明**：分布式追踪（如 OpenTelemetry、Jaeger、Zipkin）帮助定位性能瓶颈和故障；每个请求有唯一的 Trace ID，跨服务传递
- **相关**：Observability（可观测性）、Distributed System（分布式系统）
### Trojan / 木马
- **音标**：/ˈtroʊdʒən/
- **中文**：木马
- **定义**：伪装成合法软件的恶意软件
- **说明**：木马不会自我复制，但会窃取数据、创建后门、下载其他恶意软件；用户被欺骗安装
- **相关**：Malware（恶意软件）、Backdoor（后门）
### Trust Zone / 信任区
- **中文**：信任区
- **定义**：ARM 处理器的安全技术，将系统分为安全世界（Secure World）和普通世界（Normal World）
- **说明**：TrustZone 用于移动支付、DRM、生物识别等安全敏感功能；安全世界运行可信操作系统（如 OP-TEE）
- **相关**：ARM、Secure Boot（安全启动）、TEE（可信执行环境）
### Two-Factor Authentication (2FA) / 双因素认证
- **中文**：双因素认证
- **定义**：需要两种不同认证因素的身份验证
- **说明**：三种认证因素：所知（密码）、所有（手机、令牌）、所是（指纹、面部）；2FA 通常结合密码和手机验证码
- **相关**：Multi-Factor Authentication（多因素认证）、Authentication（认证）
### Virus / 病毒
- **音标**：/ˈvaɪrəs/
- **中文**：病毒
- **定义**：依附于其他程序并自我复制的恶意软件
- **说明**：病毒需要宿主程序才能执行；感染文件后传播；需要用户执行（如打开邮件附件）
- **相关**：Malware（恶意软件）、Worm（蠕虫）
### VPN (Virtual Private Network) / 虚拟专用网络
- **发音**：/viː-piː-ɛn/
- **中文**：虚拟专用网络
- **定义**：在公共网络上建立加密隧道的技术，提供安全的远程访问
- **说明**：VPN 协议包括：IPsec、SSL/TLS VPN（OpenVPN）、WireGuard、PPTP、L2TP；用于远程办公、绕过地理限制、保护隐私
- **相关**：Tunnel（隧道）、Encryption（加密）、IPsec
### Vulnerability / 漏洞
- **音标**：/ˌvʌlnərəˈbɪləti/
- **中文**：漏洞
- **定义**：系统中被攻击者利用的弱点或缺陷
- **说明**：漏洞来源：软件 Bug、配置错误、设计缺陷、人为失误；漏洞通常有 CVE 编号；需要及时打补丁
- **相关**：Exploit（利用）、CVE、Patch（补丁）
### Whaling / 鲸钓
- **中文**：鲸钓
- **定义**：针对高管或重要人物的定向钓鱼
- **说明**：鲸钓目标是有权访问敏感信息或财务权限的高层；一旦成功，损失巨大
- **相关**：Spear Phishing（定向钓鱼）、Phishing（钓鱼）
### Wildcard Certificate / 通配符证书
- **中文**：通配符证书
- **定义**：可以匹配多个子域名的证书
- **说明**：通配符证书使用 * 匹配子域名，如 *.example.com 匹配 www.example.com、mail.example.com 等；方便但安全风险较大（一个私钥保护多个子域名）
- **相关**：Certificate（证书）、Subdomain（子域名）
### Worm / 蠕虫
- **音标**：/wɜːrm/
- **中文**：蠕虫
- **定义**：独立运行并自我传播的恶意软件
- **说明**：蠕虫不需要宿主程序，通过网络漏洞自动传播；传播速度快，可以造成大规模感染（如 WannaCry、Conficker）
- **相关**：Malware（恶意软件）、Virus（病毒）
### X.509
- **发音**：/ɛks-faɪv-oʊ-naɪn/
- **中文**：X.509
- **定义**：公钥基础设施（PKI）的标准证书格式
- **说明**：X.509 证书包含版本、序列号、签名算法、颁发者、有效期、主体、公钥、扩展、签名；是 TLS/SSL 的基础
- **相关**：Certificate（证书）、PKI（公钥基础设施）
### XDR (Extended Detection and Response) / 扩展检测与响应
- **发音**：/ɛks-diː-ɑːr/
- **中文**：扩展检测与响应
- **定义**：跨端点、网络、云、邮件的统一威胁检测和响应平台
- **说明**：XDR 打破安全孤岛，关联多源数据检测高级威胁；代表：Palo Alto Cortex XDR、Microsoft Defender XDR
- **相关**：EDR（端点检测与响应）、SIEM（安全信息和事件管理）
### XSS (Cross-Site Scripting) / 跨站脚本
- **发音**：/ɛks-ɛs-ɛs/
- **中文**：跨站脚本
- **定义**：在网页中注入恶意脚本的攻击
- **说明**：XSS 分为反射型（Reflected）、存储型（Stored）、DOM 型；可以窃取用户 Cookie、会话令牌，执行恶意操作；防御：输入过滤、输出编码、CSP
- **相关**：Web Security（Web 安全）、CSP（内容安全策略）
### Zero Trust / 零信任
- **中文**：零信任
- **定义**：不信任任何内部或外部网络，始终验证和授权的安全模型
- **说明**：零信任原则：从不信任，始终验证；最小权限；假设 breach（假设已经被入侵）；微分段；多因素认证；持续监控；代表：Google BeyondCorp
- **相关**：Security（安全）、Authentication（认证）、Access Control（访问控制）
### Zero-Day / 零日
- **发音**：/ˈzɪroʊ-deɪ/
- **中文**：零日
- **定义**：软件供应商尚未知晓或尚未发布补丁的漏洞
- **说明**：零日漏洞极其危险，因为无补丁可打；零日漏洞在地下市场交易；防御：纵深防御、最小权限、行为检测
- **相关**：Vulnerability（漏洞）、Exploit（利用）、Patch（补丁）
