# 03. 软件测试 (Software Testing)

## 基础概念

### Acceptance Testing / 验收测试
- **中文**：验收测试
- **定义**：验证软件是否满足业务需求和用户期望的正式测试阶段
- **说明**：由用户或客户执行；类型：用户验收测试（UAT）、运营验收测试（OAT）、合同验收测试；通过标准：符合验收准则
- **相关**：Requirement（需求）、System Testing（系统测试）、User（用户）

### Assertion / 断言
- **中文**：断言
- **定义**：代码中检查预期条件是否为真的语句，失败时抛出错误
- **说明**：用于单元测试验证结果；如 assertEquals(expected, actual)；调试时检测不变量；生产环境可禁用
- **相关**：Unit Testing（单元测试）、TDD、Invariant（不变量）

### Black Box Testing / 黑盒测试
- **中文**：黑盒测试
- **定义**：不考虑内部实现、只基于输入输出规格进行测试的方法
- **说明**：测试人员无需代码知识；方法：等价类划分、边界值分析、决策表、状态转换测试；验证功能是否符合需求
- **相关**：White Box Testing（白盒测试）、Functional Testing（功能测试）、Test Case（测试用例）

### Bug / 缺陷
- **中文**：缺陷
- **定义**：软件中导致其行为与预期不符的错误、故障或遗漏
- **说明**：生命周期：新建 → 确认 → 分配 → 修复 → 验证 → 关闭；严重程度：致命、严重、一般、轻微；与 Feature Request（功能请求）区分
- **同义词**：Defect、Fault、Issue
- **相关**：Debugging（调试）、Bug Report（缺陷报告）、Fix（修复）

### Code Coverage / 代码覆盖率
- **中文**：代码覆盖率
- **定义**：度量测试用例执行代码程度的指标
- **说明**：类型：语句覆盖、分支覆盖、条件覆盖、路径覆盖、函数覆盖；工具：JaCoCo、Istanbul、Coverage.py、gcov；高覆盖率不等于高质量测试
- **相关**：Unit Testing（单元测试）、Testing（测试）、Quality Assurance（质量保证）

### Debugging / 调试
- **中文**：调试
- **定义**：定位、分析和修复软件缺陷的过程
- **说明**：方法：打印日志、断点调试、单元测试隔离、二分定位；工具：IDE 调试器（GDB、LLDB、Chrome DevTools）；是开发的核心技能
- **相关**：Bug（缺陷）、Troubleshooting（故障排查）、Debugger（调试器）

### Edge Case / 边界情况
- **中文**：边界情况
- **定义**：输入或条件处于极端或边界值时的程序行为场景
- **说明**：如空输入、最大值、最小值、负数；边界情况常隐藏缺陷；测试设计应重点关注；与 Corner Case（极端情况）类似
- **相关**：Boundary Value Analysis（边界值分析）、Test Case（测试用例）、Testing（测试）

### Error / 错误
- **中文**：错误
- **定义**：导致软件产生不正确结果的人为失误
- **说明**：错误（Error）→ 缺陷（Defect/Fault/Bug）→ 故障（Failure）；错误是根本原因；通过评审、测试、静态分析预防
- **相关**：Bug（缺陷）、Failure（故障）、Fault（故障）

### Failure / 故障
- **中文**：故障
- **定义**：软件在执行时表现出的与预期不符的外部行为
- **说明**：是缺陷（Bug）的可观察表现；并非所有缺陷都会触发故障（如未执行到的代码）；故障由外部观测
- **相关**：Bug（缺陷）、Error（错误）、Incident（事件）

### Functional Testing / 功能测试
- **中文**：功能测试
- **定义**：验证软件功能是否符合需求规格说明的测试
- **说明**：黑盒测试方法；关注"做什么"而非"怎么做"；类型：冒烟测试、回归测试、系统测试、验收测试
- **相关**：Non-Functional Testing（非功能测试）、Requirement（需求）、Black Box Testing（黑盒测试）

### Integration Testing / 集成测试
- **中文**：集成测试
- **定义**：验证多个模块或组件组合后能否协同工作的测试
- **说明**：策略：大爆炸集成（一次性全部集成）、增量集成（自顶向下、自底向上、三明治）、持续集成；关注接口和数据流
- **相关**：Unit Testing（单元测试）、System Testing（系统测试）、Interface（接口）

### Mock / 模拟对象
- **中文**：模拟对象
- **定义**：测试中替代真实依赖、模拟特定行为和响应的对象
- **说明**：与 Stub（桩）不同：Mock 验证交互行为，Stub 提供预定义响应；框架：Mockito、Moq、unittest.mock、Sinon.js
- **相关**：Stub（桩）、Unit Testing（单元测试）、Test Double（测试替身）

### Non-Functional Testing / 非功能测试
- **中文**：非功能测试
- **定义**：验证软件非功能特性（性能、安全、可用性等）的测试
- **说明**：类型：性能测试、负载测试、压力测试、安全测试、兼容性测试、可用性测试；与功能测试互补
- **相关**：Performance Testing（性能测试）、Security Testing（安全测试）、Functional Testing（功能测试）

### Regression Testing / 回归测试
- **中文**：回归测试
- **定义**：在代码变更后重新运行已有测试、确保未引入新缺陷的测试
- **说明**：可手动或自动执行；自动化回归测试是 CI/CD 的核心；测试套件应稳定、快速、可重复
- **相关**：CI/CD、Automation Testing（自动化测试）、Test Suite（测试套件）

### Smoke Testing / 冒烟测试
- **中文**：冒烟测试
- **定义**：验证软件基本功能是否正常、能否进入详细测试的快速检查
- **说明**：名称来源：硬件测试时通电看是否冒烟；覆盖核心流程；失败时无需继续详细测试；常作为 CI 的第一步
- **相关**：Sanity Testing（健全性测试）、CI/CD、Testing（测试）

### Stub / 桩
- **中文**：桩
- **定义**：测试中替代未实现或复杂依赖、返回预定义结果的简化实现
- **说明**：与 Mock 不同：Stub 仅提供数据，不验证交互；用于隔离被测单元；如数据库桩返回固定查询结果
- **相关**：Mock（模拟对象）、Test Double（测试替身）、Unit Testing（单元测试）

### System Testing / 系统测试
- **中文**：系统测试
- **定义**：在完整集成后的系统上验证是否符合需求规格的测试
- **说明**：覆盖端到端场景；包括功能和非功能测试；在类生产环境中执行；是发布前的最后验证阶段
- **相关**：Integration Testing（集成测试）、Acceptance Testing（验收测试）、End-to-End Testing（端到端测试）

### Test Case / 测试用例
- **中文**：测试用例
- **定义**：为验证特定功能或场景而设计的一组输入、执行条件和预期结果
- **说明**：要素：ID、标题、前置条件、输入数据、执行步骤、预期结果、优先级；应可重复执行；良好命名和文档化
- **相关**：Testing（测试）、Test Suite（测试套件）、Test Plan（测试计划）

### Test Double / 测试替身
- **中文**：测试替身
- **定义**：测试中替代真实协作对象的统称
- **说明**：类型：Dummy（占位）、Fake（简化实现）、Stub（桩）、Spy（间谍，记录交互）、Mock（模拟）；Gerard Meszaros 提出分类
- **相关**：Mock（模拟对象）、Stub（桩）、Unit Testing（单元测试）

### Test Plan / 测试计划
- **中文**：测试计划
- **定义**：描述测试策略、范围、资源、进度和风险的文档
- **说明**：内容：测试目标、测试项、方法、环境、人员、进度、风险；指导测试执行；IEEE 829 标准模板
- **相关**：Test Case（测试用例）、Testing（测试）、Project Management（项目管理）

### Test Suite / 测试套件
- **中文**：测试套件
- **定义**：一组相关测试用例的集合，通常按功能或模块组织
- **说明**：便于批量执行和管理；层次：单元测试套件、集成测试套件、系统测试套件；持续集成中自动运行
- **相关**：Test Case（测试用例）、Automation Testing（自动化测试）、CI/CD

### Testing / 测试
- **中文**：测试
- **定义**：通过执行软件来发现缺陷、验证质量的活动
- **说明**：阶段：单元测试 → 集成测试 → 系统测试 → 验收测试；方法：手动测试、自动化测试；目标：发现缺陷、建立信心、预防缺陷
- **相关**：Quality Assurance（质量保证）、Bug（缺陷）、Verification（验证）

### Unit Testing / 单元测试
- **中文**：单元测试
- **定义**：对软件最小可测试单元（函数、类、模块）进行验证的测试
- **说明**：特点：隔离测试（Mock 依赖）、自动化、快速反馈；框架：JUnit、pytest、Jest、Mocha、Google Test；TDD 的基础
- **相关**：TDD、Mock（模拟对象）、Code Coverage（代码覆盖率）

### White Box Testing / 白盒测试
- **中文**：白盒测试
- **定义**：基于代码内部结构和逻辑进行测试的方法
- **说明**：测试人员需了解代码；方法：语句覆盖、分支覆盖、路径覆盖、条件覆盖；工具：代码覆盖率工具、静态分析工具
- **相关**：Black Box Testing（黑盒测试）、Code Coverage（代码覆盖率）、Unit Testing（单元测试）

## 测试方法论

### A/B Testing / A/B 测试
- **中文**：A/B 测试
- **定义**：将用户随机分为两组、分别展示不同版本以比较效果的实验方法
- **说明**：用于优化 UI、功能、算法；需要统计显著性检验；应用：网页优化、推荐算法、定价策略
- **相关**：Experimentation（实验）、Data-Driven（数据驱动）、Hypothesis Testing（假设检验）

### Boundary Value Analysis / 边界值分析
- **说明**：选择输入域边界值设计测试用例的黑盒技术；缺陷常出现在边界；如范围 [1, 100]，测试 0、1、100、101
- **相关**：Equivalence Partitioning（等价类划分）、Black Box Testing（黑盒测试）、Test Case（测试用例）

### Chaos Engineering / 混沌工程
- **中文**：混沌工程
- **定义**：在生产环境主动注入故障、验证系统韧性的实践
- **说明**：Netflix 提出（Chaos Monkey）；原则：假设稳态、引入真实事件、自动化实验、最小化爆炸半径；验证容错和恢复能力
- **相关**：Resilience（韧性）、Fault Tolerance（容错）、Production（生产环境）

### Equivalence Partitioning / 等价类划分
- **中文**：等价类划分
- **定义**：将输入域划分为若干等价类、每类选一个代表值测试的技术
- **说明**：假设同一等价类中的值行为相同；有效等价类（合法输入）和无效等价类（非法输入）；减少测试用例数量
- **相关**：Boundary Value Analysis（边界值分析）、Black Box Testing（黑盒测试）、Test Case（测试用例）

### Exploratory Testing / 探索性测试
- **中文**：探索性测试
- **定义**：测试人员同时设计测试、执行测试和学习被测系统的动态测试方法
- **说明**：无需预定义用例；依赖测试人员的经验和创造力；适合发现脚本化测试遗漏的缺陷；常与自动化测试互补
- **相关**：Manual Testing（手动测试）、Ad Hoc Testing（随机测试）、Testing（测试）

### Load Testing / 负载测试
- **中文**：负载测试
- **定义**：在预期负载下验证系统性能的测试
- **说明**：模拟正常和峰值用户量；指标：响应时间、吞吐量、资源利用率、错误率；工具：JMeter、LoadRunner、Gatling、k6
- **相关**：Performance Testing（性能测试）、Stress Testing（压力测试）、Scalability（可扩展性）

### Performance Testing / 性能测试
- **中文**：性能测试
- **定义**：评估系统在特定工作负载下响应速度、稳定性和资源消耗的测试
- **说明**：类型：负载测试、压力测试、 soak 测试（长时间运行）、 spike 测试（突发负载）；基线测试建立性能基准
- **相关**：Load Testing（负载测试）、Stress Testing（压力测试）、Benchmark（基准测试）

### Property-Based Testing / 基于属性的测试
- **中文**：基于属性的测试
- **定义**：定义输入输出的通用属性、由框架自动生成大量随机数据进行验证的测试方法
- **说明**：与传统示例测试不同；发现边界情况和反例；框架：QuickCheck（Haskell）、Hypothesis（Python）、ScalaCheck
- **相关**：Unit Testing（单元测试）、Fuzzing（模糊测试）、Generative Testing（生成式测试）

### Security Testing / 安全测试
- **中文**：安全测试
- **定义**：发现系统安全漏洞、验证安全机制有效性的测试
- **说明**：类型：渗透测试、漏洞扫描、代码审计、模糊测试；OWASP Top 10 是常见威胁清单；工具：Burp Suite、OWASP ZAP、SonarQube
- **相关**：Penetration Testing（渗透测试）、Vulnerability（漏洞）、OWASP

### Stress Testing / 压力测试
- **中文**：压力测试
- **定义**：在超出正常负载的极端条件下验证系统行为的测试
- **说明**：目标：发现系统瓶颈、验证恢复能力、确定崩溃点；与负载测试不同：压力测试故意超载
- **相关**：Load Testing（负载测试）、Performance Testing（性能测试）、Resilience（韧性）

### TDD (Test-Driven Development) / 测试驱动开发
- **中文**：测试驱动开发
- **定义**：先编写失败的测试、再编写最小代码使测试通过、最后重构的迭代开发方法
- **说明**：红-绿-重构循环；提高设计质量、确保可测试性、提供回归保护；是 XP 和敏捷的核心实践
- **相关**：Unit Testing（单元测试）、Red-Green-Refactor、XP

## 测试工具与自动化

### Automation Testing / 自动化测试
- **中文**：自动化测试
- **定义**：使用脚本和工具自动执行测试、比较实际结果与预期结果的方法
- **说明**：适合：回归测试、重复性测试、大数据量测试；不适合：探索性测试、一次性测试；框架：Selenium、Cypress、Appium、Robot Framework
- **相关**：Manual Testing（手动测试）、CI/CD、Test Script（测试脚本）

### CI/CD (Continuous Integration / Continuous Deployment) / 持续集成/持续部署
- **中文**：持续集成/持续部署
- **定义**：自动化构建、测试和部署软件的工程实践
- **说明**：CI：频繁合并代码、自动构建和测试；CD：自动部署到生产环境（或需手动审批）；工具：Jenkins、GitLab CI、GitHub Actions、CircleCI
- **相关**：DevOps、Automation（自动化）、Agile（敏捷）

### Fuzzing / 模糊测试
- **中文**：模糊测试
- **定义**：自动生成大量随机或畸形输入、监测程序异常行为的安全测试技术
- **说明**：可发现内存泄漏、崩溃、安全漏洞；覆盖率导向的模糊测试（AFL、libFuzzer）更高效；广泛应用于浏览器、操作系统测试
- **相关**：Security Testing（安全测试）、Property-Based Testing（基于属性的测试）、Vulnerability（漏洞）

### Manual Testing / 手动测试
- **中文**：手动测试
- **定义**：由测试人员手工执行测试用例、观察结果的测试方法
- **说明**：适合：探索性测试、可用性测试、一次性测试；优点：发现直觉性问题；缺点：耗时、不可重复、易遗漏
- **相关**：Automation Testing（自动化测试）、Exploratory Testing（探索性测试）、Testing（测试）

### Penetration Testing / 渗透测试
- **中文**：渗透测试
- **定义**：模拟攻击者手段、主动发现系统安全漏洞的授权测试
- **说明**：类型：黑盒（无信息）、灰盒（部分信息）、白盒（完整信息）；步骤：侦察 → 扫描 → 漏洞利用 → 后渗透 → 报告
- **相关**：Security Testing（安全测试）、Ethical Hacking（道德黑客）、Vulnerability（漏洞）

### Selenium / Selenium
- **中文**：Selenium
- **定义**：开源的 Web 应用自动化测试框架
- **说明**：支持多浏览器（Chrome、Firefox、Safari）；多语言绑定（Java、Python、JavaScript）；组件：WebDriver、IDE、Grid；行业标准
- **相关**：Automation Testing（自动化测试）、Web Testing（Web 测试）、Cypress
