# 05. 质量与维护 (Quality & Maintenance)

## 代码质量

### Anti-Pattern / 反模式
- **中文**：反模式
- **定义**：看似有效但实际会导致负面后果的常见不良解决方案
- **说明**：与 Design Pattern 相对；例子：上帝类（God Class）、面条代码（Spaghetti Code）、拷贝粘贴编程（Copy-Paste Programming）、过早优化；识别并避免反模式
- **相关**：Design Pattern（设计模式）、Code Smell（代码异味）、Refactoring（重构）

### Boy Scout Rule / 童子军规则
- **中文**：童子军规则
- **定义**："让代码比你发现时更干净"，每次修改代码时顺便做小幅改进的原则
- **说明**：Kent Beck 提出；持续改进而非大规模重构；降低技术债务积累；与重构文化配合
- **相关**：Refactoring（重构）、Technical Debt（技术债务）、Clean Code（整洁代码）

### Clean Code / 整洁代码
- **中文**：整洁代码
- **定义**：易于阅读、理解、修改和测试的高质量代码
- **说明**：Robert C. Martin《Clean Code》；特征：有意义命名、短函数、单一职责、无重复、良好格式、完整测试；代码是写给人看的
- **相关**：Code Quality（代码质量）、Refactoring（重构）、Readable Code（可读代码）

### Code Review / 代码审查
- **中文**：代码审查
- **定义**：由其他开发者检查代码变更、发现缺陷和改进点的质量保证活动
- **说明**：形式：结对审查、小组审查、工具辅助（GitHub PR、GitLab MR）；关注：正确性、可读性、安全性、性能、测试覆盖；知识共享的重要途径
- **相关**：Quality Assurance（质量保证）、Pull Request（拉取请求）、Collaboration（协作）

### Code Smell / 代码异味
- **中文**：代码异味
- **定义**：代码中可能暗示更深层次问题的表面迹象
- **说明**：不是 Bug，但增加维护难度；例子：长方法、大类、重复代码、过多参数、消息链、中间人；由 Martin Fowler 提出
- **相关**：Refactoring（重构）、Anti-Pattern（反模式）、Technical Debt（技术债务）

### Complexity / 复杂度
- **中文**：复杂度
- **定义**：软件系统或代码难以理解、修改和测试的程度
- **说明**：度量：圈复杂度（Cyclomatic Complexity）、认知复杂度（Cognitive Complexity）；高复杂度导致缺陷率高；降低方法：分解、抽象、简化条件
- **相关**：Cyclomatic Complexity（圈复杂度）、Maintainability（可维护性）、Code Quality（代码质量）

### Cyclomatic Complexity / 圈复杂度
- **中文**：圈复杂度
- **定义**：度量代码线性独立路径数量的指标，反映控制流复杂度
- **说明**：公式：V(G) = E - N + 2P（边-节点+2*连通分量）；简单理解：决策点数量 + 1；推荐值：≤ 10；高圈复杂度难测试和维护
- **相关**：Complexity（复杂度）、Testing（测试）、Static Analysis（静态分析）

### Defect Density / 缺陷密度
- **中文**：缺陷密度
- **定义**：每千行代码（KLOC）或每个功能点的缺陷数量
- **说明**：度量软件质量；可用于比较模块质量、评估测试效果、预测剩余缺陷；行业标准：3-5 缺陷/KLOC（交付时）
- **相关**：Quality Metric（质量度量）、Bug（缺陷）、Code Quality（代码质量）

### Lint / 代码检查
- **中文**：代码检查
- **定义**：静态分析工具，检查代码风格问题和潜在错误
- **说明**：名称源自 C 语言工具 lint；现代工具：ESLint、Pylint、Checkstyle、SonarLint；集成到 IDE 和 CI 流水线
- **相关**：Static Analysis（静态分析）、Code Quality（代码质量）、Style Guide（风格指南）

### Maintainability Index / 可维护性指数
- **中文**：可维护性指数
- **定义**：综合代码复杂度、代码行数和注释率计算的可维护性度量指标
- **说明**：范围 0-100，越高越好；微软提出；用于识别需要重构的模块；需结合其他指标使用
- **相关**：Maintainability（可维护性）、Code Quality（代码质量）、Metric（度量）

### Quality Gate / 质量门禁
- **中文**：质量门禁
- **定义**：代码合并或发布前必须通过的一系列质量检查标准
- **说明**：检查项：代码覆盖率、静态分析问题数、测试通过率、安全漏洞；自动执行；不通过则阻止合并；SonarQube 提供质量门禁功能
- **相关**：CI/CD、Code Quality（代码质量）、SonarQube

### Readability / 可读性
- **中文**：可读性
- **定义**：代码易于被人类理解和阅读的程度
- **说明**：最重要代码质量属性；影响因素：命名、格式、结构、注释、复杂度；可读性高的代码 Bug 更少、维护更容易
- **相关**：Clean Code（整洁代码）、Code Quality（代码质量）、Naming（命名）

### Static Analysis / 静态分析
- **中文**：静态分析
- **定义**：在不执行代码的情况下分析代码结构、发现潜在问题的技术
- **说明**：发现：语法错误、类型错误、空指针、资源泄漏、安全漏洞、风格问题；工具：SonarQube、Coverity、Fortify、CodeQL
- **相关**：Code Review（代码审查）、Lint、Dynamic Analysis（动态分析）

### Technical Debt / 技术债务
- **中文**：技术债务
- **定义**：因选择快速但非最优的技术方案而积累的额外工作成本
- **说明**：来源： deadline 压力、缺乏重构、过时的技术、文档缺失；需定期"偿还"（重构）；否则导致开发速度下降；Ward Cunningham 提出
- **相关**：Refactoring（重构）、Code Smell（代码异味）、Maintainability（可维护性）

## 重构与维护

### Extract Method / 提取方法
- **中文**：提取方法
- **定义**：将长方法中的逻辑片段提取为独立方法的重构手法
- **说明**：Martin Fowler《重构》中最常用的重构；提高可读性、复用性、测试性；新方法名应清晰表达意图
- **相关**：Refactoring（重构）、Code Smell（代码异味）、Long Method（长方法）

### Long Method / 长方法
- **中文**：长方法
- **定义**：包含过多逻辑、难以理解和测试的方法
- **说明**：常见 Code Smell；判断标准：通常 > 20 行（视语言而定）；解决：提取方法、提取类、使用策略模式
- **相关**：Code Smell（代码异味）、Extract Method（提取方法）、Refactoring（重构）

### Refactoring / 重构
- **中文**：重构
- **定义**：在不改变外部行为的前提下改进代码内部结构的过程
- **说明**：目的：提高可读性、降低复杂度、消除重复、便于扩展；手法：提取方法、重命名、移动方法、内联、替换算法；应配合自动化测试
- **相关**：Technical Debt（技术债务）、Code Smell（代码异味）、Clean Code（整洁代码）

### Reverse Engineering / 逆向工程
- **中文**：逆向工程
- **定义**：通过分析已有系统（代码、数据库）来推导其设计和规格的过程
- **说明**：用于：理解遗留系统、恢复丢失文档、迁移系统、安全审计；工具：UML 逆向工具、反编译器；与正向工程相对
- **相关**：Legacy System（遗留系统）、Documentation（文档）、Reengineering（再工程）

### Reengineering / 再工程
- **中文**：再工程
- **定义**：检查和改造现有系统以重构为新形式的过程
- **说明**：阶段：逆向工程（理解）→ 重构或重新设计 → 正向工程（实现）；目的是提高可维护性和功能；比重写风险低
- **相关**：Reverse Engineering（逆向工程）、Refactoring（重构）、Legacy System（遗留系统）

### Spaghetti Code / 面条代码
- **中文**：面条代码
- **定义**：缺乏结构、控制流混乱缠绕、难以理解和维护的代码
- **说明**：常见于缺乏设计、长期未经重构的代码；特征：大量全局变量、深层嵌套、goto、重复代码；解决：重构为结构化设计
- **相关**：Anti-Pattern（反模式）、Code Smell（代码异味）、Refactoring（重构）

## 软件度量

### Function Point / 功能点
- **中文**：功能点
- **定义**：基于软件功能需求度量软件规模的单位
- **说明**：考虑：输入、输出、查询、内部文件、外部接口；与实现技术无关；用于估算工作量、成本和进度；IFPUG 标准方法
- **相关**：Estimation（估算）、Software Metric（软件度量）、COCOMO

### KLOC (Kilo Lines of Code) / 千行代码
- **中文**：千行代码
- **定义**：软件规模的度量单位，表示代码行数（以千为单位）
- **说明**：简单但粗糙；不同语言不可比；用途：估算缺陷密度、生产率；现代更倾向功能点或故事点
- **相关**：Software Metric（软件度量）、Code Quality（代码质量）、Estimation（估算）

### Lead Time / 前置时间
- **中文**：前置时间
- **定义**：从需求提出到功能交付给用户的总时间
- **说明**：DevOps 核心度量之一；包括：需求分析、开发、测试、部署；缩短 Lead Time 是持续交付的目标；与 Cycle Time 不同
- **相关**：Cycle Time（周期时间）、DevOps、Delivery（交付）

### Metric / 度量
- **中文**：度量
- **定义**：对软件产品、过程或资源的定量测量
- **说明**：分类：规模度量（KLOC、功能点）、质量度量（缺陷密度）、过程度量（Lead Time、Cycle Time）、项目度量（成本、进度）；应可比较、可行动
- **相关**：Measurement（测量）、KPI、Software Quality（软件质量）

### MTBF (Mean Time Between Failures) / 平均故障间隔时间
- **中文**：平均故障间隔时间
- **定义**：系统两次故障之间的平均时间
- **说明**：度量系统可靠性；MTBF 越长越可靠；与 MTTR（平均修复时间）一起使用；可用性 = MTBF / (MTBF + MTTR)
- **相关**：MTTR、Reliability（可靠性）、Availability（可用性）

### MTTR (Mean Time To Repair/Recovery) / 平均修复/恢复时间
- **中文**：平均修复/恢复时间
- **定义**：系统从故障发生到恢复正常运行的平均时间
- **说明**：度量运维效率；MTTR 越短越好；减少 MTTR 方法：监控告警、自动化修复、Runbook、混沌工程
- **相关**：MTBF、SRE、Incident Management（事故管理）

### Software Metric / 软件度量
- **中文**：软件度量
- **定义**：对软件产品、过程或项目属性的定量测量
- **说明**：目的：理解、控制、改进；类型：过程度量（效率）、产品度量（质量）、项目度量（进度/成本）；应 SMART（具体、可衡量、可达成、相关、有时限）
- **相关**：Metric（度量）、KPI、Quality Assurance（质量保证）
