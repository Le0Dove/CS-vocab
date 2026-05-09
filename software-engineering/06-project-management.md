# 06. 项目管理 (Project Management)

## 估算与规划

### COCOMO / COCOMO
- **中文**：构造性成本模型
- **全称**：Constructive Cost Model
- **定义**：基于软件规模估算开发工作量和进度的经验模型
- **说明**：三个层次：基本（仅代码量）、中级（增加成本驱动因子）、详细（按模块）；公式：Effort = a × (KLOC)^b；由 Barry Boehm 提出
- **相关**：Estimation（估算）、Software Metric（软件度量）、Function Point（功能点）

### Critical Path / 关键路径
- **中文**：关键路径
- **定义**：项目网络图中决定项目最短完成时间的活动序列
- **说明**：关键路径上活动的浮动时间为零；延迟关键路径活动将延迟整个项目；关键路径法（CPM）用于项目调度
- **相关**：Project Management（项目管理）、Scheduling（调度）、Gantt Chart（甘特图）

### Estimation / 估算
- **中文**：估算
- **定义**：对项目规模、工作量、成本、进度进行预测的过程
- **说明**：方法：专家判断、类比估算、参数化模型（COCOMO）、三点估算、计划扑克（Planning Poker）；不确定性高，应定期更新
- **相关**：Planning（规划）、COCOMO、Story Point（故事点）

### Gantt Chart / 甘特图
- **中文**：甘特图
- **定义**：以条形图展示项目任务、时间安排和进度的可视化工具
- **说明**：横轴：时间；纵轴：任务；条形长度表示持续时间；显示任务依赖关系；Microsoft Project、Jira、Asana 支持
- **相关**：Project Management（项目管理）、Scheduling（调度）、Timeline（时间线）

### Milestone / 里程碑
- **中文**：里程碑
- **定义**：项目中标志重要阶段完成的关键时间点或事件
- **说明**：无持续时间，是时间点；例子：需求冻结、设计评审通过、Alpha 版本、Beta 版本、正式发布；用于跟踪进度和决策
- **相关**：Project Management（项目管理）、Planning（规划）、Release（发布）

### Planning Poker / 计划扑克
- **中文**：计划扑克
- **定义**：敏捷团队通过出牌（斐波那契数）共识估算故事点的技术
- **说明**：流程：讲解故事 → 独立估算 → 同时亮牌 → 讨论差异 → 重新估算；利用群体智慧；避免锚定效应
- **相关**：Estimation（估算）、Story Point（故事点）、Agile（敏捷）

### PERT (Program Evaluation and Review Technique) / 计划评审技术
- **中文**：计划评审技术
- **定义**：使用三点估算（乐观、最可能、悲观）分析项目时间的网络图技术
- **说明**：公式：期望时间 = (乐观 + 4×最可能 + 悲观) / 6；考虑不确定性；与关键路径法（CPM）结合使用
- **相关**：Estimation（估算）、Critical Path（关键路径）、Project Management（项目管理）

### Scope / 范围
- **中文**：范围
- **定义**：项目需要交付的产品、服务和成果的边界
- **说明**：范围管理：定义、确认、控制范围；范围蔓延（Scope Creep）：未经控制的需求增加；防止：变更控制流程、明确验收标准
- **相关**：Requirement（需求）、Change Management（变更管理）、Scope Creep（范围蔓延）

### Scope Creep / 范围蔓延
- **中文**：范围蔓延
- **定义**：未经正式变更控制、项目范围逐渐扩大的现象
- **说明**：常见原因：需求不明确、利益相关者压力、镀金（Gold Plating）；后果：进度延迟、成本超支；控制：严格变更流程、明确范围基准
- **相关**：Scope（范围）、Change Management（变更管理）、Project Management（项目管理）

### WBS (Work Breakdown Structure) / 工作分解结构
- **中文**：工作分解结构
- **定义**：将项目可交付成果和工作逐层分解为更小、更易管理的组件的层级结构
- **说明**：分解到工作包（Work Package）级别；100% 规则：子层之和等于父层；是估算、计划、跟踪的基础
- **相关**：Project Management（项目管理）、Planning（规划）、Task（任务）

## 风险管理

### Contingency Plan / 应急计划
- **中文**：应急计划
- **定义**：风险发生时的预备响应方案
- **说明**：与风险缓解不同：缓解降低发生概率，应急计划是发生后的应对；例子：核心人员离职的备份方案、供应商违约的替代方案
- **相关**：Risk Management（风险管理）、Mitigation（缓解）、Fallback Plan（回退计划）

### Mitigation / 缓解
- **中文**：缓解
- **定义**：降低风险发生概率或影响程度的措施
- **说明**：策略：避免、转移、减轻、接受；例子：代码审查缓解质量风险、购买保险转移财务风险、原型验证缓解技术风险
- **相关**：Risk Management（风险管理）、Risk（风险）、Contingency Plan（应急计划）

### Risk / 风险
- **中文**：风险
- **定义**：可能对项目目标产生负面影响的不确定事件或条件
- **说明**：属性：概率（Likelihood）和影响（Impact）；管理过程：识别 → 分析 → 规划应对 → 监控；积极风险 = 机会
- **相关**：Risk Management（风险管理）、Mitigation（缓解）、Uncertainty（不确定性）

### Risk Management / 风险管理
- **中文**：风险管理
- **定义**：识别、分析、应对和监控项目风险的过程
- **说明**：定性分析：评估概率和影响；定量分析：蒙特卡洛模拟、决策树；风险登记册（Risk Register）跟踪所有风险
- **相关**：Risk（风险）、Mitigation（缓解）、Project Management（项目管理）

### Technical Risk / 技术风险
- **中文**：技术风险
- **定义**：与技术选择、实现难度、性能要求相关的不确定性
- **说明**：例子：新技术不成熟、性能不达标、集成困难、安全漏洞；缓解：原型验证、Spike、技术预研、渐进采用
- **相关**：Risk（风险）、Prototype（原型）、Proof of Concept（概念验证）

## 团队协作

### Bus Factor / 巴士因子
- **中文**：巴士因子
- **定义**：项目因关键人员流失而受影响的度量，指最少多少人离开会导致项目停滞
- **说明**：巴士因子 = 1 表示只有一个人掌握关键知识，风险极高；提高方法：知识共享、结对编程、文档化、代码审查；理想值 ≥ 2
- **相关**：Knowledge Sharing（知识共享）、Risk（风险）、Team Collaboration（团队协作）

### Cross-Functional Team / 跨职能团队
- **中文**：跨职能团队
- **定义**：包含不同专业技能（开发、测试、设计、产品）成员的团队
- **说明**：敏捷和 Scrum 推荐；减少交接和依赖；团队对交付物端到端负责；T 型人才（一专多能）是理想成员
- **相关**：Scrum、Agile（敏捷）、Team（团队）

### Knowledge Sharing / 知识共享
- **中文**：知识共享
- **定义**：在团队内部分享经验、技能和最佳实践的活动
- **说明**：形式：技术分享会、文档、Wiki、结对编程、代码审查；好处：减少单点故障、提升整体能力、加速新人融入
- **相关**：Bus Factor（巴士因子）、Collaboration（协作）、Documentation（文档）

### Onboarding / 入职培训
- **中文**：入职培训
- **定义**：帮助新团队成员快速融入和上手工作的过程
- **说明**：内容：技术栈、代码规范、工具使用、团队流程、领域知识；好的 onboarding 缩短产出时间、降低流失率
- **相关**：Team（团队）、Knowledge Sharing（知识共享）、Documentation（文档）

### Retrospective / 回顾会议
- **中文**：回顾会议
- **定义**：团队定期反思工作方式、识别改进机会的会议
- **说明**：Start-Stop-Continue 格式；安全氛围鼓励坦诚；产生可执行的行动项；持续改进文化的核心
- **相关**：Agile（敏捷）、Scrum、Continuous Improvement（持续改进）

### Stakeholder Management / 利益相关者管理
- **中文**：利益相关者管理
- **定义**：识别、分析和沟通利益相关者期望、确保项目支持的过程
- **说明**：利益相关者矩阵：权力/利益分析；高权力高利益者需重点管理；定期沟通、管理期望、解决冲突
- **相关**：Stakeholder（利益相关者）、Communication（沟通）、Project Management（项目管理）

### Team Velocity / 团队速度
- **中文**：团队速度
- **定义**：敏捷团队每个迭代完成的故事点总量
- **说明**：用于预测未来交付能力；应稳定而非最大化；不用于跨团队比较（不同团队故事点基准不同）；帮助做发布规划
- **相关**：Velocity（速度）、Sprint（冲刺）、Agile（敏捷）

## 工程管理

### Capacity Planning / 容量规划
- **中文**：容量规划
- **定义**：评估和确保系统资源（计算、存储、网络）满足未来需求的过程
- **说明**：考虑：增长趋势、峰值负载、冗余、成本；方法：垂直扩展、水平扩展、云弹性伸缩；与性能测试配合
- **相关**：Scalability（可扩展性）、Load Testing（负载测试）、Resource Management（资源管理）

### Change Management / 变更管理
- **中文**：变更管理
- **定义**：控制和管理软件或系统变更的流程
- **说明**：流程：请求 → 评估影响 → 审批 → 实施 → 验证；目的：最小化变更风险、保持可追溯性；工具：Jira、ServiceNow、Remedy
- **相关**：Configuration Management（配置管理）、Release Management（发布管理）、Risk（风险）

### Incident Management / 事故管理
- **中文**：事故管理
- **定义**：处理服务中断或质量下降事件、恢复正常服务的流程
- **说明**：流程：检测 → 响应 → 诊断 → 修复 → 复盘；指标：MTTR、MTBF；工具：PagerDuty、OpsGenie、Jira Service Management
- **相关**：SRE、Post-Mortem（事后分析）、Monitoring（监控）

### Release Management / 发布管理
- **中文**：发布管理
- **定义**：规划、调度和控制软件发布到生产环境的过程
- **说明**：包括：版本规划、环境准备、部署执行、验证、回滚准备；策略：大爆炸发布、滚动发布、蓝绿部署、金丝雀发布
- **相关**：Deployment（部署）、CI/CD、Change Management（变更管理）

### Resource Allocation / 资源分配
- **中文**：资源分配
- **定义**：将人力、时间、设备等资源分配给项目任务的过程
- **说明**：考虑：技能匹配、可用性、优先级、依赖关系；避免过度分配；工具：Microsoft Project、Jira、Asana、Monday.com
- **相关**：Project Management（项目管理）、Scheduling（调度）、Capacity（容量）

### Root Cause Analysis / 根因分析
- **中文**：根因分析
- **定义**：系统性识别问题根本原因、防止再次发生的方法
- **说明**：方法：5 Whys（五个为什么）、鱼骨图（Ishikawa）、故障树分析（FTA）；聚焦系统改进而非追责；SRE 事后分析核心
- **相关**：Post-Mortem（事后分析）、Problem Solving（问题解决）、Continuous Improvement（持续改进）

### Runbook / 运行手册
- **中文**：运行手册
- **定义**：记录标准操作流程、故障处理步骤的文档
- **说明**：用于运维和事故响应；内容：常见警报处理、故障排查步骤、回滚流程、联系人；自动化 Runbook（如 Rundeck）提高效率
- **相关**：SRE、Incident Management（事故管理）、Documentation（文档）

### Timeboxing / 时间盒
- **中文**：时间盒
- **定义**：为活动设定固定时间限制、到时停止的技术
- **说明**：敏捷和 Scrum 核心：Sprint 是时间盒；好处：强制优先级排序、防止完美主义、提供节奏感；时间到则交付当前成果
- **相关**：Sprint（冲刺）、Agile（敏捷）、Time Management（时间管理）
