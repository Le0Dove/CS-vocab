# 04. 敏捷与 DevOps (Agile & DevOps)

## 敏捷方法论

### Backlog / 待办列表
- **中文**：待办列表
- **定义**：记录所有需求、功能、技术任务的有序列表
- **说明**：产品待办列表（Product Backlog）：整个产品的需求池；冲刺待办列表（Sprint Backlog）：当前迭代要完成的任务；按优先级排序
- **相关**：Scrum、Sprint（冲刺）、User Story（用户故事）

### Daily Stand-up / 每日站会
- **中文**：每日站会
- **定义**：团队每天短时间（通常 15 分钟）同步进展的会议
- **说明**：三个问题：昨天做了什么、今天计划做什么、遇到什么障碍；站立进行以保持简短；不是问题解决会议
- **同义词**：Daily Scrum
- **相关**：Scrum、Agile（敏捷）、Team Collaboration（团队协作）

### Epic / 史诗
- **中文**：史诗
- **定义**：大型用户故事，包含多个相关功能，需多个迭代完成
- **说明**：Epic 分解为多个 User Story；代表大粒度的业务价值；如"用户认证系统"可分解为注册、登录、密码重置等 Story
- **相关**：User Story（用户故事）、Backlog（待办列表）、Agile（敏捷）

### Increment / 增量
- **中文**：增量
- **定义**：迭代结束时交付的、可工作的软件功能集合
- **说明**：增量是潜在可发布的；每个增量增加新功能；与迭代（Iteration）不同：迭代是时间盒，增量是产出物
- **相关**：Iteration（迭代）、Sprint（冲刺）、Release（发布）

### Iteration / 迭代
- **中文**：迭代
- **定义**：固定时间长度的开发周期（通常 1-4 周），结束时交付可用增量
- **说明**：包含：计划、设计、编码、测试、评审；短迭代提供快速反馈；是敏捷的核心机制
- **相关**：Sprint（冲刺）、Increment（增量）、Agile（敏捷）

### Kanban / 看板
- **中文**：看板
- **定义**：可视化工作流程、限制在制品数量以优化流动的敏捷方法
- **说明**：源于丰田生产系统；看板列：待办 → 进行中 → 完成；WIP 限制防止多任务；持续流动，无固定迭代
- **相关**：Agile（敏捷）、Lean（精益）、WIP（在制品）

### Product Owner / 产品负责人
- **中文**：产品负责人
- **定义**：Scrum 中负责定义产品愿景、管理待办列表优先级、代表利益相关者的角色
- **说明**：唯一有权决定待办列表优先级；与团队和客户沟通；确保开发工作产生最大业务价值
- **相关**：Scrum、Scrum Master、Backlog（待办列表）

### Retrospective / 回顾会议
- **中文**：回顾会议
- **定义**：迭代结束后团队反思过程、识别改进点的会议
- **说明**：三个问题：什么做得好、什么可改进、下个迭代如何改进；安全氛围鼓励坦诚；持续改进的核心实践
- **相关**：Scrum、Sprint（冲刺）、Continuous Improvement（持续改进）

### Scrum / Scrum
- **中文**：Scrum
- **定义**：迭代增量式的敏捷开发框架，通过固定时长的冲刺交付价值
- **说明**：角色：Product Owner、Scrum Master、开发团队；工件：Product Backlog、Sprint Backlog、Increment；活动：Sprint Planning、Daily Stand-up、Sprint Review、Retrospective
- **相关**：Agile（敏捷）、Sprint（冲刺）、Backlog（待办列表）

### Scrum Master / Scrum 教练
- **中文**：Scrum 教练
- **定义**：Scrum 中负责确保团队遵循 Scrum 实践、消除障碍的服务型领导
- **说明**：不是项目经理；保护团队免受干扰；促进会议；教练和指导团队自组织；是流程的守护者
- **相关**：Scrum、Product Owner、Agile Coach（敏捷教练）

### Sprint / 冲刺
- **中文**：冲刺
- **定义**：Scrum 中固定时长（通常 2 周）的迭代周期
- **说明**：Sprint 开始时做计划，结束时交付潜在可发布增量；时长固定，范围可调；提供节奏感和可预测性
- **相关**：Scrum、Iteration（迭代）、Backlog（待办列表）

### Story Point / 故事点
- **中文**：故事点
- **定义**：敏捷中用于估算用户故事相对工作量的抽象单位
- **说明**：考虑：复杂度、工作量、风险；使用斐波那契数列（1, 2, 3, 5, 8, 13...）；团队速度（Velocity）= 每 Sprint 完成的故事点
- **相关**：User Story（用户故事）、Estimation（估算）、Velocity（速度）

### User Story / 用户故事
- **中文**：用户故事
- **定义**：从用户角度描述需求的简短陈述，格式："作为...我想要...以便..."
- **说明**：INVEST 原则：Independent（独立）、Negotiable（可协商）、Valuable（有价值）、Estimable（可估算）、Small（小）、Testable（可测试）；验收标准定义完成条件
- **相关**：Epic（史诗）、Acceptance Criteria（验收标准）、Backlog（待办列表）

### Velocity / 速度
- **中文**：速度
- **定义**：团队在一个迭代周期内完成的故事点总和
- **说明**：用于预测未来交付能力；随时间趋于稳定；不应作为绩效指标（会导致估算膨胀）；帮助做发布规划
- **相关**：Story Point（故事点）、Sprint（冲刺）、Capacity Planning（容量规划）

### XP (Extreme Programming) / 极限编程
- **中文**：极限编程
- **定义**：强调工程实践和技术卓越的敏捷方法
- **说明**：核心实践：TDD、结对编程、持续集成、简单设计、重构、小版本发布、集体代码所有权；适合需求变化快的项目
- **相关**：Agile（敏捷）、TDD、Pair Programming（结对编程）

## DevOps

### AIOps / AIOps
- **中文**：智能运维
- **全称**：Artificial Intelligence for IT Operations
- **定义**：将人工智能应用于 IT 运维、实现自动化监控和故障处理的实践
- **说明**：应用场景：异常检测、根因分析、容量预测、自动化修复；减少人工干预；代表：Datadog、Dynatrace、Splunk
- **相关**：DevOps、Monitoring（监控）、Automation（自动化）

### Blue-Green Deployment / 蓝绿部署
- **中文**：蓝绿部署
- **定义**：维护两个相同的生产环境（蓝和绿），通过切换流量实现零停机部署
- **说明**：蓝环境运行当前版本，绿环境部署新版本；验证后切换流量；失败可快速回滚；需要双倍资源
- **相关**：Deployment（部署）、Zero Downtime（零停机）、Canary Release（金丝雀发布）

### Canary Release / 金丝雀发布
- **中文**：金丝雀发布
- **定义**：先将新版本发布给少量用户、验证无误后再全量发布的部署策略
- **说明**：名称来源：矿工用金丝雀检测有毒气体；逐步扩大流量比例（如 5% → 25% → 100%）；快速发现问题、降低影响范围
- **相关**：Deployment（部署）、Feature Flag（特性开关）、Blue-Green Deployment（蓝绿部署）

### Configuration as Code / 配置即代码
- **中文**：配置即代码
- **定义**：将基础设施和应用的配置以代码形式管理、版本控制和自动化部署的实践
- **说明**：好处：可审计、可复现、可回滚；工具：Ansible、Chef、Puppet、Terraform；与 IaC 密切相关
- **相关**：IaC（基础设施即代码）、GitOps、DevOps

### Container / 容器
- **中文**：容器
- **定义**：将应用及其依赖打包为标准化、可移植的运行单元的技术
- **说明**：与虚拟机不同：容器共享宿主机内核，更轻量；代表：Docker、containerd；容器编排：Kubernetes、Docker Swarm
- **相关**：Docker、Kubernetes、Virtualization（虚拟化）

### Containerization / 容器化
- **中文**：容器化
- **定义**：将应用及其运行环境打包为容器镜像的过程
- **说明**：解决"在我机器上能跑"问题；环境一致性（开发/测试/生产）；快速启动、资源高效；微服务部署的标准方式
- **相关**：Container（容器）、Docker、Microservices（微服务）

### Continuous Delivery (CD) / 持续交付
- **中文**：持续交付
- **定义**：软件随时保持可发布状态、通过手动触发部署到生产的实践
- **说明**：与持续部署的区别：持续交付需手动批准发布；自动化构建、测试、部署流水线；缩短发布周期、降低发布风险
- **相关**：Continuous Deployment（持续部署）、CI（持续集成）、DevOps

### Continuous Deployment / 持续部署
- **中文**：持续部署
- **定义**：代码通过自动化测试后自动部署到生产环境的实践
- **说明**：比持续交付更进一步，完全自动化；需要完善的测试覆盖和监控；代表：Netflix、Etsy、GitHub
- **相关**：Continuous Delivery（持续交付）、CI/CD、Automation（自动化）

### Continuous Integration (CI) / 持续集成
- **中文**：持续集成
- **定义**：频繁地将代码合并到主干、并自动构建和测试的实践
- **说明**：频率：每天多次；核心：自动化构建、自动化测试、快速反馈；工具：Jenkins、GitLab CI、GitHub Actions、Travis CI
- **相关**：CI/CD、DevOps、Automation Testing（自动化测试）

### Dark Launch / 暗发布
- **中文**：暗发布
- **定义**：将新功能部署到生产环境但不向用户展示、仅内部测试的发布策略
- **说明**：验证生产环境性能和行为；与用户无关的真实流量测试；常与 Feature Flag 配合；降低发布风险
- **相关**：Feature Flag（特性开关）、Canary Release（金丝雀发布）、Deployment（部署）

### DevOps / DevOps
- **中文**：DevOps
- **定义**：融合开发（Dev）和运维（Ops）、通过自动化和协作加速软件交付的文化和实践
- **说明**：CALMS 原则：Culture（文化）、Automation（自动化）、Lean（精益）、Measurement（度量）、Sharing（共享）；打破开发和运维壁垒
- **相关**：CI/CD、SRE（站点可靠性工程）、Agile（敏捷）

### Feature Flag / 特性开关
- **中文**：特性开关
- **定义**：在代码中通过配置控制功能启用/禁用的机制
- **说明**：好处：主干开发、渐进发布、快速回滚、A/B 测试；类型：发布开关、实验开关、运维开关；工具：LaunchDarkly、Unleash
- **同义词**：Feature Toggle
- **相关**：Dark Launch（暗发布）、Canary Release（金丝雀发布）、CI/CD

### GitOps / GitOps
- **中文**：GitOps
- **定义**：以 Git 仓库为唯一事实来源、通过自动化工具同步基础设施和应用状态的运维模式
- **说明**：声明式配置；Git 记录所有变更；Pull Request 驱动部署；工具：ArgoCD、Flux；实现可审计、可回滚的部署
- **相关**：DevOps、IaC（基础设施即代码）、Kubernetes

### IaC (Infrastructure as Code) / 基础设施即代码
- **中文**：基础设施即代码
- **定义**：通过代码管理和配置基础设施（服务器、网络、数据库）的实践
- **说明**：声明式（Terraform、CloudFormation）vs 命令式（Ansible、Chef）；好处：版本控制、可复用、自动化、一致性
- **相关**：DevOps、Configuration as Code（配置即代码）、Cloud Computing（云计算）

### Kubernetes / Kubernetes
- **中文**：Kubernetes
- **定义**：开源的容器编排平台，自动化部署、扩展和管理容器化应用
- **说明**：源于 Google Borg；核心概念：Pod、Service、Deployment、Ingress；生态：Helm、Prometheus、Istio；事实标准
- **同义词**：K8s
- **相关**：Container（容器）、Docker、DevOps

### Monitoring / 监控
- **中文**：监控
- **定义**：持续收集系统和应用指标、检测异常和性能问题的实践
- **说明**：指标类型：日志（Logs）、指标（Metrics）、追踪（Traces）；工具：Prometheus、Grafana、ELK Stack、Datadog；告警：PagerDuty、OpsGenie
- **相关**：Observability（可观测性）、Logging（日志）、Alerting（告警）

### Observability / 可观测性
- **中文**：可观测性
- **定义**：通过系统外部输出（日志、指标、追踪）推断内部状态的能力
- **说明**：三大支柱：Metrics（指标）、Logs（日志）、Traces（追踪）；与 Monitoring 不同：Monitoring 是已知问题的检测，Observability 是未知问题的探索
- **相关**：Monitoring（监控）、Logging（日志）、Distributed Tracing（分布式追踪）

### Rollback / 回滚
- **中文**：回滚
- **定义**：将系统恢复到之前稳定版本的操作
- **说明**：部署失败时的应急措施；策略：数据库迁移回滚、蓝绿切换、版本标签回退；需预先规划回滚策略；与 Roll-forward（向前修复）相对
- **相关**：Deployment（部署）、Version Control（版本控制）、Disaster Recovery（灾难恢复）

### SRE (Site Reliability Engineering) / 站点可靠性工程
- **中文**：站点可靠性工程
- **定义**：Google 提出的、用软件工程方法解决运维问题的学科
- **说明**：核心：错误预算（Error Budget）、SLI/SLO/SLA、自动化运维、故障演练；SRE 团队开发工具替代人工操作
- **相关**：DevOps、SLA、Monitoring（监控）

## 协作与工具

### Agile Coach / 敏捷教练
- **中文**：敏捷教练
- **定义**：指导团队和组织采用敏捷实践、提升效能的专业角色
- **说明**：不同于 Scrum Master（聚焦团队），Agile Coach 关注组织层面；培训、辅导、引导变革；帮助建立敏捷文化
- **相关**：Agile（敏捷）、Scrum Master、Transformation（转型）

### Burndown Chart / 燃尽图
- **中文**：燃尽图
- **定义**：展示迭代或项目剩余工作量随时间减少趋势的图表
- **说明**：横轴：时间；纵轴：剩余工作量；理想线 vs 实际线；直观显示进度和偏差；Scrum 常用工具
- **相关**：Scrum、Sprint（冲刺）、Progress Tracking（进度跟踪）

### DevSecOps / DevSecOps
- **中文**：DevSecOps
- **定义**：将安全实践集成到 DevOps 流程中的方法论
- **说明**："Shift Left"：尽早发现和修复安全问题；自动化安全扫描：SAST（静态）、DAST（动态）、依赖检查；安全是每个人的责任
- **相关**：DevOps、Security（安全）、Shift Left（左移）

### Pair Programming / 结对编程
- **中文**：结对编程
- **定义**：两名开发者在同一台电脑上协作编程的实践
- **说明**：角色：驾驶员（Driver，写代码）、领航员（Navigator，审查和思考）；好处：知识共享、即时审查、减少缺陷；XP 核心实践
- **相关**：XP、Code Review（代码审查）、Collaboration（协作）

### Post-Mortem / 事后分析
- **中文**：事后分析
- **定义**：对生产事故进行系统性回顾、分析根因并制定改进措施的过程
- **说明**：无责文化（Blameless）；聚焦系统和流程改进而非追责；输出：事故时间线、根因、行动计划；SRE 核心实践
- **同义词**：Incident Review（事故复盘）
- **相关**：SRE、Incident Management（事故管理）、Continuous Improvement（持续改进）

### SLA (Service Level Agreement) / 服务等级协议
- **中文**：服务等级协议
- **定义**：服务提供方与客户之间约定的服务质量标准
- **说明**：指标：可用性（如 99.99%）、响应时间、吞吐量；违约后果：赔偿或服务信用；与 SLO、SLI 配合使用
- **相关**：SLO、SLI、SRE、Availability（可用性）

### SLI (Service Level Indicator) / 服务等级指标
- **中文**：服务等级指标
- **定义**：衡量服务质量的定量指标
- **说明**：例子：请求延迟、错误率、吞吐量、可用性；SLI 应具体、可测量、可理解；是定义 SLO 的基础
- **相关**：SLO、SLA、SRE、Metric（指标）

### SLO (Service Level Objective) / 服务等级目标
- **中文**：服务等级目标
- **定义**：服务等级指标的目标值
- **说明**：例子：P99 延迟 < 200ms、错误率 < 0.1%；基于 SLI 设定；错误预算 = 1 - SLO（如 99.9% 对应 0.1% 错误预算）
- **相关**：SLI、SLA、SRE、Error Budget（错误预算）
