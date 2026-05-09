# 06. 强化学习 (Reinforcement Learning)

## 基础概念

### Action / 动作
- **中文**：动作
- **定义**：智能体在给定状态下可以执行的操作
- **说明**：动作空间可以是离散的（如游戏按键）或连续的（如机器人关节角度）；策略决定选择哪个动作
- **相关**：Agent（智能体）、State（状态）、Policy（策略）、Action Space（动作空间）

### Action Space / 动作空间
- **中文**：动作空间
- **定义**：环境中所有可能动作的集合
- **说明**：离散动作空间（Discrete）：有限个动作，如 Atari 游戏按键；连续动作空间（Continuous）：动作是实数向量，如机器人控制
- **相关**：Action（动作）、State Space（状态空间）、Agent（智能体）

### Agent / 智能体
- **中文**：智能体
- **定义**：在环境中观察状态、执行动作、根据奖励学习的决策者
- **说明**：智能体目标是最大化累积奖励；可以是算法（如 Q-Learning）、神经网络（如 DQN）或人类；是 RL 的核心
- **相关**：Environment（环境）、Policy（策略）、Reward（奖励）

### Bellman Equation / 贝尔曼方程
- **中文**：贝尔曼方程
- **定义**：描述最优值函数递归关系的方程，是动态规划和强化学习的理论基础
- **说明**：将长期累积奖励分解为即时奖励和未来值；值迭代和策略迭代基于此方程；体现最优子结构
- **相关**：Value Function（值函数）、Dynamic Programming（动态规划）、Optimal Policy（最优策略）

### Discount Factor / 折扣因子
- **中文**：折扣因子
- **定义**：用于折现未来奖励的系数 γ（0 ≤ γ ≤ 1），表示未来奖励的当前价值
- **说明**：γ 接近 1 时关注长期奖励，接近 0 时关注即时奖励；保证累积奖励收敛；通常设为 0.9 或 0.99
- **同义词**：Gamma (γ)
- **相关**：Reward（奖励）、Cumulative Reward（累积奖励）、Return（回报）

### Environment / 环境
- **中文**：环境
- **定义**：智能体所处的外部系统，接收动作并返回新状态和奖励
- **说明**：环境定义了状态空间、动作空间和转移动力学；可以是真实世界、仿真器或游戏；智能体不可直接控制环境
- **相关**：Agent（智能体）、State（状态）、Reward（奖励）、MDP

### Episode / 回合
- **中文**：回合
- **定义**：智能体从初始状态到终止状态的完整交互序列
- **说明**：每轮 episode 独立；终止状态可以是达到目标、超时或失败；总奖励是 episode 内奖励之和
- **相关**：Step（步）、Terminal State（终止状态）、Cumulative Reward（累积奖励）

### Exploration vs Exploitation / 探索与利用
- **中文**：探索与利用
- **定义**：强化学习中平衡尝试新动作（探索）与选择已知最优动作（利用）的困境
- **说明**：纯利用可能陷入局部最优，纯探索浪费已知信息；策略：ε-贪心、上置信界（UCB）、玻尔兹曼探索
- **相关**：ε-Greedy、Multi-Armed Bandit（多臂老虎机）、Policy（策略）

### Markov Decision Process (MDP) / 马尔可夫决策过程
- **中文**：马尔可夫决策过程
- **定义**：描述强化学习问题的数学框架，包含状态、动作、转移概率、奖励和折扣因子
- **说明**：马尔可夫性：下一状态只依赖当前状态和动作，与历史无关；是 RL 的理论基础
- **相关**：State（状态）、Action（动作）、Reward（奖励）、Transition Probability（转移概率）

### Policy / 策略
- **中文**：策略
- **定义**：智能体在给定状态下选择动作的规则或映射
- **说明**：确定性策略：π(s) = a；随机策略：π(a|s) 表示状态 s 选择动作 a 的概率；策略可以是表格或神经网络
- **相关**：Agent（智能体）、Action（动作）、State（状态）、Optimal Policy（最优策略）

### Reward / 奖励
- **中文**：奖励
- **定义**：环境对智能体动作的即时反馈信号，标量值
- **说明**：正奖励鼓励行为，负奖励（惩罚）抑制行为；奖励设计是 RL 的关键挑战；稀疏奖励问题（Sparse Reward）
- **相关**：Reward Function（奖励函数）、Return（回报）、Cumulative Reward（累积奖励）

### Reward Function / 奖励函数
- **中文**：奖励函数
- **定义**：定义在特定状态下执行特定动作所获得奖励的规则
- **说明**：奖励函数设计影响学习效果；好的奖励函数应引导智能体达成目标；塑造奖励（Reward Shaping）可加速学习
- **相关**：Reward（奖励）、Reward Shaping（奖励塑造）、Environment（环境）

### State / 状态
- **中文**：状态
- **定义**：环境在某一时刻的完整描述，包含智能体做决策所需的所有信息
- **说明**：状态空间可以是离散的或连续的；完全可观测环境：agent 看到完整状态；部分可观测环境：agent 只看到观测（Observation）
- **相关**：Observation（观测）、State Space（状态空间）、Agent（智能体）

### State Space / 状态空间
- **中文**：状态空间
- **定义**：环境中所有可能状态的集合
- **说明**：离散状态空间：有限个状态（如棋盘位置）；连续状态空间：无限个状态（如机器人关节角度）；状态空间大小影响算法选择
- **相关**：State（状态）、Action Space（动作空间）、MDP

### Step / 步
- **中文**：步
- **定义**：智能体与环境的一次完整交互：执行动作 → 环境返回新状态和奖励
- **说明**：时间步（Timestep）标记交互顺序；每步智能体根据当前策略选择动作
- **相关**：Episode（回合）、Action（动作）、State（状态）

### Trajectory / 轨迹
- **中文**：轨迹
- **定义**：智能体在环境中交互产生的状态-动作-奖励序列
- **说明**：轨迹是经验的基本单位；用于经验回放（Experience Replay）和策略梯度估计；记录智能体的行为历史
- **同义词**：Rollout、Path
- **相关**：Episode（回合）、Experience Replay（经验回放）

## 值函数方法

### Action-Value Function / 动作值函数
- **中文**：动作值函数
- **定义**：在状态 s 下执行动作 a 后、遵循策略 π 的期望累积回报，记为 Q^π(s, a)
- **说明**：Q 值评估在特定状态下选择特定动作的好坏；Q-Learning 直接学习最优 Q 函数
- **同义词**：Q-Function、Q-Value
- **相关**：Value Function（值函数）、Q-Learning、Policy（策略）

### Cumulative Reward / 累积奖励
- **中文**：累积奖励
- **定义**：智能体在一个 episode 中获得的折扣奖励之和
- **说明**：公式：G_t = r_{t+1} + γ*r_{t+2} + γ²*r_{t+3} + ... ；智能体目标是最大化期望累积奖励
- **同义词**：Return（回报）、Total Reward
- **相关**：Reward（奖励）、Discount Factor（折扣因子）、Episode（回合）

### Dynamic Programming (DP) / 动态规划
- **中文**：动态规划
- **定义**：在已知环境模型的情况下，通过贝尔曼方程迭代求解最优策略的方法
- **说明**：策略迭代（Policy Iteration）：策略评估 + 策略改进；值迭代（Value Iteration）：直接迭代值函数；需要完整的环境模型
- **相关**：Bellman Equation（贝尔曼方程）、Value Iteration（值迭代）、Policy Iteration（策略迭代）

### Model-Based RL / 基于模型的强化学习
- **中文**：基于模型的强化学习
- **定义**：学习环境转移模型（状态转移和奖励），并利用模型进行规划或生成模拟经验的 RL 方法
- **说明**：可模拟未来轨迹进行规划；样本效率高；挑战：模型误差会累积；代表：Dyna-Q、MBMF、MPC
- **相关**：Model-Free RL（无模型强化学习）、Planning（规划）、Transition Model（转移模型）

### Model-Free RL / 无模型强化学习
- **中文**：无模型强化学习
- **定义**：不学习环境模型、直接从与环境交互的经验中学习策略或值函数的 RL 方法
- **说明**：分为值函数方法（Q-Learning、DQN）和策略梯度方法（REINFORCE、PPO）；更通用但样本效率低
- **相关**：Model-Based RL（基于模型的强化学习）、Q-Learning、Policy Gradient（策略梯度）

### Q-Learning / Q 学习
- **中文**：Q 学习
- **定义**：无模型的离策略（Off-Policy）值函数算法，通过学习最优 Q 函数找到最优策略
- **说明**：更新规则：Q(s,a) ← Q(s,a) + α[r + γ*max(Q(s',a')) - Q(s,a)]；不需要知道环境模型；表格形式适合小状态空间
- **相关**：SARSA、DQN、Temporal Difference（时序差分）

### SARSA / SARSA
- **中文**：SARSA
- **定义**：无模型的在策略（On-Policy）值函数算法，使用实际采取的动作更新 Q 值
- **说明**：更新规则：Q(s,a) ← Q(s,a) + α[r + γ*Q(s',a') - Q(s,a)]；比 Q-Learning 更保守；名称来自序列 (s,a,r,s',a')
- **相关**：Q-Learning、On-Policy（在策略）、Temporal Difference（时序差分）

### State-Value Function / 状态值函数
- **中文**：状态值函数
- **定义**：在状态 s 下遵循策略 π 的期望累积回报，记为 V^π(s)
- **说明**：V 值评估状态的好坏；与 Q 值关系：V^π(s) = Σ π(a|s) * Q^π(s,a)；策略迭代中直接优化 V
- **同义词**：V-Function、V-Value
- **相关**：Action-Value Function（动作值函数）、Policy Evaluation（策略评估）

### Temporal Difference (TD) / 时序差分
- **中文**：时序差分
- **定义**：使用当前估计和下一步估计的差值来更新值函数的 RL 方法
- **说明**：TD(0)：单步更新；TD(λ)：多步更新；结合蒙特卡洛（无偏但高方差）和动态规划（低方差但有偏）的优点
- **相关**：Q-Learning、SARSA、Monte Carlo（蒙特卡洛）

### Value Function / 值函数
- **中文**：值函数
- **定义**：评估状态或状态-动作对好坏的函数，表示遵循某策略的期望累积回报
- **说明**：状态值函数 V(s) 和动作值函数 Q(s,a)；值函数可以通过贝尔曼方程迭代求解；是值函数方法的核心
- **相关**：Bellman Equation（贝尔曼方程）、Policy Evaluation（策略评估）、Q-Learning

## 策略梯度方法

### Actor-Critic / 演员-评论家
- **中文**：演员-评论家
- **定义**：结合策略梯度（Actor）和值函数估计（Critic）的强化学习架构
- **说明**：Actor 更新策略，Critic 评估策略并减少方差；经典算法：A2C、A3C；平衡策略梯度的方差和偏差
- **相关**：Policy Gradient（策略梯度）、Value Function（值函数）、A2C

### Advantage Function / 优势函数
- **中文**：优势函数
- **定义**：衡量某个动作相对于当前策略平均水平的好坏的函数：A(s,a) = Q(s,a) - V(s)
- **说明**：优势为正表示动作优于平均；用于减少策略梯度的方差；是 A2C、PPO 等算法的核心
- **相关**：Value Function（值函数）、Policy Gradient（策略梯度）、A2C

### Deterministic Policy Gradient / 确定性策略梯度
- **中文**：确定性策略梯度
- **定义**：适用于连续动作空间的策略梯度方法，策略直接输出确定动作
- **说明**：与随机策略梯度不同；代表算法：DDPG、TD3；在连续控制任务中表现优异
- **相关**：DDPG、Policy Gradient（策略梯度）、Continuous Action（连续动作）

### Off-Policy / 离策略
- **中文**：离策略
- **定义**：学习的目标策略与生成数据的探索策略不同的 RL 方法
- **说明**：可用旧数据（经验回放）；学习效率高；代表：Q-Learning、DQN；挑战：分布偏移
- **相关**：On-Policy（在策略）、Experience Replay（经验回放）、Q-Learning

### On-Policy / 在策略
- **中文**：在策略
- **定义**：学习的目标策略与生成数据的探索策略相同的 RL 方法
- **说明**：只能用当前策略生成的数据；样本效率较低但更稳定；代表：SARSA、A2C、PPO
- **相关**：Off-Policy（离策略）、Policy Gradient（策略梯度）、SARSA

### Policy Gradient / 策略梯度
- **中文**：策略梯度
- **定义**：直接对策略参数化并通过梯度上升最大化累积奖励的 RL 方法
- **说明**：REINFORCE 是基础算法；通过蒙特卡洛采样估计梯度；适合连续动作空间和高维状态空间
- **相关**：REINFORCE、Actor-Critic、Stochastic Policy（随机策略）

### Proximal Policy Optimization (PPO) / 近端策略优化
- **中文**：近端策略优化
- **定义**：OpenAI 提出的策略梯度算法，通过裁剪目标函数限制策略更新幅度
- **说明**：解决策略梯度更新过大的问题；实现简单、性能稳定；是当前最常用的 RL 算法之一；应用：OpenAI Five、ChatGPT RLHF
- **相关**：Policy Gradient（策略梯度）、TRPO、Clip Objective（裁剪目标）

### REINFORCE / REINFORCE
- **中文**：REINFORCE
- **定义**：基础的蒙特卡洛策略梯度算法，通过完整 episode 的回报估计梯度
- **说明**：梯度公式：∇J = E[G_t * ∇log π(a_t|s_t)]；高方差；可通过基线（Baseline）减少方差
- **相关**：Policy Gradient（策略梯度）、Monte Carlo（蒙特卡洛）、Baseline（基线）

## 深度学习强化学习

### A3C (Asynchronous Advantage Actor-Critic) / 异步优势演员-评论家
- **中文**：异步优势演员-评论家
- **定义**：DeepMind 提出的异步并行训练多个智能体的 Actor-Critic 算法
- **说明**：多个并行 worker 与环境交互，异步更新全局网络；无需经验回放；训练速度快
- **相关**：A2C、Actor-Critic、Parallel Training（并行训练）

### DDPG (Deep Deterministic Policy Gradient) / 深度确定性策略梯度
- **中文**：深度确定性策略梯度
- **定义**：适用于连续动作空间的 Off-Policy Actor-Critic 算法
- **说明**：Actor 输出确定动作，Critic 评估 Q 值；使用经验回放和目标网络；是 TD3、SAC 的基础
- **相关**：Actor-Critic、Continuous Control（连续控制）、Experience Replay（经验回放）

### Deep Q-Network (DQN) / 深度 Q 网络
- **中文**：深度 Q 网络
- **定义**：DeepMind 提出的使用深度神经网络近似 Q 函数的强化学习算法
- **说明**：关键技术：经验回放（Experience Replay）和目标网络（Target Network）；在 Atari 游戏上达到人类水平
- **相关**：Q-Learning、Neural Network（神经网络）、Experience Replay（经验回放）

### Dueling DQN / 对决 DQN
- **中文**：对决 DQN
- **定义**：将 Q 函数分解为状态值 V(s) 和优势值 A(s,a) 的 DQN 改进架构
- **说明**：某些状态下所有动作价值相近时，直接学习 V(s) 更高效；结构：共享卷积层 → 两个分支（V 和 A）→ 聚合
- **相关**：DQN、Advantage Function（优势函数）、Value Function（值函数）

### Experience Replay / 经验回放
- **中文**：经验回放
- **定义**：存储智能体交互经验（s,a,r,s'）并随机采样进行训练的机制
- **说明**：打破数据相关性、提高样本效率；优先经验回放（PER）根据 TD 误差加权采样；是 DQN 的关键创新
- **相关**：DQN、Off-Policy（离策略）、Sample Efficiency（样本效率）

### Multi-Agent RL / 多智能体强化学习
- **中文**：多智能体强化学习
- **定义**：多个智能体在同一环境中学习、相互影响的强化学习设定
- **说明**：挑战：非平稳环境、信用分配、通信与协作；应用：自动驾驶、机器人协作、游戏 AI
- **相关**：Agent（智能体）、MADDPG、Game Theory（博弈论）

### Rainbow / Rainbow
- **中文**：Rainbow
- **定义**：将六种 DQN 改进技术（DDQN、Dueling、PER、A3C、Distributional、Noisy Net）整合的算法
- **说明**：DeepMind 2017 年提出；在 Atari 上达到当时最优性能；证明多种技术可以互补
- **相关**：DQN、Prioritized Experience Replay（优先经验回放）、Dueling DQN

### Target Network / 目标网络
- **中文**：目标网络
- **定义**：DQN 中用于计算目标 Q 值的延迟更新网络，与主网络结构相同但参数更新较慢
- **说明**：减少训练震荡和目标值追逐；定期从主网络复制参数；提高训练稳定性
- **相关**：DQN、Experience Replay（经验回放）、Stability（稳定性）

## 高级主题

### Curriculum Learning / 课程学习
- **中文**：课程学习
- **定义**：让智能体从简单任务开始、逐步增加难度的训练策略
- **说明**：模仿人类学习过程；加速收敛、提高最终性能；自动课程学习（Automatic Curriculum Learning）自动设计任务序列
- **相关**：Transfer Learning（迁移学习）、Training Strategy（训练策略）

### Hierarchical RL / 分层强化学习
- **中文**：分层强化学习
- **定义**：将任务分解为高层策略（选择子任务）和低层策略（执行动作）的 RL 方法
- **说明**：解决稀疏奖励和长时程问题；高层提供内在奖励；代表：Option Framework、Feudal Networks
- **相关**：Sparse Reward（稀疏奖励）、Option、Temporal Abstraction（时间抽象）

### Imitation Learning / 模仿学习
- **中文**：模仿学习
- **定义**：从专家示范（演示）中学习策略、无需奖励信号的机器学习方法
- **说明**：行为克隆（Behavior Cloning）：直接监督学习；逆强化学习（IRL）：从示范推断奖励函数；应用：自动驾驶、机器人
- **相关**：Inverse RL（逆强化学习）、Behavior Cloning（行为克隆）、Demonstration（示范）

### Inverse RL / 逆强化学习
- **中文**：逆强化学习
- **定义**：从专家示范中推断奖励函数、再基于奖励函数学习策略的方法
- **说明**：解决奖励函数设计困难问题；假设专家行为近似最优；代表算法：IRL、MaxEnt IRL、GAIL
- **相关**：Imitation Learning（模仿学习）、Reward Function（奖励函数）、GAIL

### Model Predictive Control (MPC) / 模型预测控制
- **中文**：模型预测控制
- **定义**：在每一步通过优化未来动作序列、只执行第一个动作的规划方法
- **说明**：结合基于模型的 RL 和规划；可处理约束；在机器人控制中广泛应用
- **相关**：Model-Based RL（基于模型的强化学习）、Planning（规划）、Control（控制）

### Monte Carlo Method / 蒙特卡洛方法
- **中文**：蒙特卡洛方法
- **定义**：通过采样完整 episode 并计算实际回报来估计值函数的 RL 方法
- **说明**：无偏估计但方差大；必须等待 episode 结束才能更新；适合 episode 较短的任务
- **相关**：Temporal Difference（时序差分）、Sampling（采样）、Return（回报）

### Option / 选项
- **中文**：选项
- **定义**：分层强化学习中的时间抽象单元，表示一组动作组成的宏动作
- **说明**：选项有策略、终止条件和启动集；Sutton 等提出；减少决策频率、加速学习
- **相关**：Hierarchical RL（分层强化学习）、Temporal Abstraction（时间抽象）

### Reward Shaping / 奖励塑造
- **中文**：奖励塑造
- **定义**：通过设计额外的辅助奖励信号来引导智能体更快学习的技术
- **说明**：需保证最优策略不变（如基于势函数的塑造）；加速稀疏奖励环境下的学习；设计不当可能引入次优策略
- **相关**：Reward Function（奖励函数）、Sparse Reward（稀疏奖励）、Potential-Based Shaping

### RLHF (Reinforcement Learning from Human Feedback) / 人类反馈强化学习
- **中文**：人类反馈强化学习
- **定义**：利用人类偏好反馈训练奖励模型、再用强化学习优化语言模型的技术
- **说明**：ChatGPT 等模型的核心技术；步骤：监督微调 → 奖励模型训练 → RL 优化（PPO）；使模型输出更符合人类偏好
- **相关**：PPO、Reward Model（奖励模型）、LLM（大语言模型）

### Sparse Reward / 稀疏奖励
- **中文**：稀疏奖励
- **定义**：智能体在大多数步骤获得零奖励、只在极少数关键状态获得非零奖励的环境
- **说明**：使学习困难（信用分配问题）；解决方法：奖励塑造、课程学习、分层 RL、内在动机（Intrinsic Motivation）
- **相关**：Reward Shaping（奖励塑造）、Curriculum Learning（课程学习）、Credit Assignment（信用分配）

## 应用领域

### Game AI / 游戏 AI
- **中文**：游戏 AI
- **定义**：使用强化学习训练玩游戏的人工智能
- **说明**：里程碑：DQN（Atari）、AlphaGo（围棋）、OpenAI Five（Dota 2）、AlphaStar（星际争霸）；证明 RL 在复杂决策中的能力
- **相关**：DQN、AlphaGo、Multi-Agent RL（多智能体强化学习）

### Robotics / 机器人学
- **中文**：机器人学
- **定义**：将强化学习应用于机器人控制和操作的技术
- **说明**：挑战：样本收集昂贵、安全性要求高、Sim-to-Real 差距；应用：行走、抓取、导航、装配
- **相关**：Continuous Control（连续控制）、Sim-to-Real（仿真到现实）

### Sim-to-Real / 仿真到现实
- **中文**：仿真到现实
- **定义**：将在仿真环境中训练的策略迁移到真实物理世界的技术
- **说明**：仿真提供廉价数据、现实提供真实反馈；域随机化（Domain Randomization）缩小差距；是机器人 RL 的关键挑战
- **相关**：Robotics（机器人学）、Domain Randomization（域随机化）、Transfer Learning（迁移学习）
