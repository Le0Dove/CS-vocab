# 01. 基础概念 (Basic Concepts)

### Activation Function / 激活函数
- **中文**：激活函数
- **定义**：神经网络中引入非线性变换的函数，决定神经元是否激活及输出值
- **说明**：常见激活函数：ReLU、Sigmoid、Tanh、Softmax、GELU；没有激活函数时神经网络只能学习线性关系；选择影响训练速度和模型表现
- **相关**：Neural Network（神经网络）、ReLU、Sigmoid、Gradient（梯度）

### Agent / 智能体
- **中文**：智能体
- **定义**：在环境中感知并采取行动以实现目标的自主实体
- **说明**：可以是物理机器人或软件程序；具备感知（Perception）、决策（Decision Making）、执行（Action）能力；强化学习的核心概念
- **相关**：Reinforcement Learning（强化学习）、Environment（环境）、State（状态）

### Algorithm / 算法
- **中文**：算法
- **定义**：解决特定问题的一系列明确步骤或规则
- **说明**：机器学习算法从数据中学习模式；包括监督学习、无监督学习、强化学习算法；选择取决于问题类型和数据特征
- **相关**：Model（模型）、Training（训练）、Optimization（优化）

### Artificial General Intelligence (AGI) / 通用人工智能
- **中文**：通用人工智能
- **定义**：具备人类水平通用认知能力，能在任意任务中表现出智能的 AI 系统
- **说明**：与 Narrow AI（窄人工智能，只能完成特定任务）相对；目前尚未实现；是 AI 研究的长期目标
- **同义词**：Strong AI（强人工智能）
- **相关**：Artificial Intelligence（人工智能）、Narrow AI（窄人工智能）

### Artificial Intelligence (AI) / 人工智能
- **中文**：人工智能
- **定义**：使机器能够模拟、延伸和扩展人类智能的理论、方法、技术及应用系统
- **说明**：分支包括机器学习、自然语言处理、计算机视觉、专家系统、机器人学；分为弱人工智能（特定任务）和强人工智能（通用智能）
- **相关**：Machine Learning（机器学习）、Deep Learning（深度学习）、AGI

### BackPropagation / 反向传播
- **中文**：反向传播
- **定义**：神经网络中通过链式法则从输出层向输入层逐层计算梯度并更新权重的算法
- **说明**：核心步骤：前向传播计算输出 → 计算损失 → 反向传播计算梯度 → 更新权重；是训练神经网络的基础
- **相关**：Gradient Descent（梯度下降）、Neural Network（神经网络）、Loss Function（损失函数）

### Bias / 偏置
- **中文**：偏置
- **定义**：神经元的额外输入参数，用于调整激活函数的输出偏移
- **说明**：允许模型拟合非过原点的数据；权重决定斜率，偏置决定截距；偏置项通常初始化为 0 或小的随机数
- **同义词**：Bias Term、Intercept
- **相关**：Weight（权重）、Neuron（神经元）、Linear Regression（线性回归）

### Classification / 分类
- **中文**：分类
- **定义**：将输入数据分配到一个预定义类别中的监督学习任务
- **说明**：二分类（两个类别，如是/否）、多分类（多个类别）；常用算法：逻辑回归、决策树、SVM、神经网络；输出是离散类别标签
- **相关**：Regression（回归）、Supervised Learning（监督学习）、Classifier（分类器）

### Clustering / 聚类
- **中文**：聚类
- **定义**：将数据分成若干组（簇），使组内相似度高、组间相似度低的无监督学习任务
- **说明**：常见算法：K-Means、层次聚类、DBSCAN、高斯混合模型；无需标注数据；应用于客户分群、图像分割等
- **相关**：Unsupervised Learning（无监督学习）、K-Means、Dimensionality Reduction（降维）

### Cost Function / 成本函数
- **中文**：成本函数
- **定义**：衡量模型预测值与真实值之间差异的函数，指导模型优化
- **说明**：也叫损失函数（Loss Function）；目标是最小化成本函数；常见：均方误差（MSE）、交叉熵（Cross-Entropy）
- **同义词**：Loss Function（损失函数）、Objective Function（目标函数）
- **相关**：Gradient Descent（梯度下降）、Optimization（优化）、BackPropagation（反向传播）

### Data Mining / 数据挖掘
- **中文**：数据挖掘
- **定义**：从大量数据中发现模式、关联、异常和趋势的过程
- **说明**：结合统计学、机器学习、数据库技术；常用技术：分类、聚类、关联规则、异常检测；应用于推荐系统、 fraud detection 等
- **相关**：Machine Learning（机器学习）、Big Data（大数据）、KDD

### Data Set / 数据集
- **中文**：数据集
- **定义**：用于训练、验证和测试模型的结构化数据集合
- **说明**：通常分为训练集（Training Set）、验证集（Validation Set）、测试集（Test Set）；质量直接影响模型性能；常见公开数据集：ImageNet、COCO、MNIST
- **相关**：Training（训练）、Test Set（测试集）、Overfitting（过拟合）

### Deep Learning / 深度学习
- **中文**：深度学习
- **定义**：基于多层神经网络（深层网络）的机器学习子领域
- **说明**：能自动学习数据的层次化特征表示；在图像、语音、NLP 领域表现卓越；需要大量数据和计算资源；代表：CNN、RNN、Transformer
- **相关**：Neural Network（神经网络）、Machine Learning（机器学习）、BackPropagation（反向传播）

### Dimensionality Reduction / 降维
- **中文**：降维
- **定义**：减少数据特征数量的技术，同时尽量保留重要信息
- **说明**：解决维度灾难（Curse of Dimensionality）；常用方法：PCA（主成分分析）、t-SNE、UMAP、Autoencoder；用于可视化和降噪
- **相关**：Feature Selection（特征选择）、PCA、Embedding（嵌入）

### Embedding / 嵌入
- **中文**：嵌入
- **定义**：将高维离散数据（如词语、用户 ID）映射到低维连续向量空间的技术
- **说明**：嵌入向量捕捉语义关系（如 Word2Vec 中 king - man + woman ≈ queen）；是深度学习和 NLP 的基础技术
- **相关**：Word2Vec、Vector Space（向量空间）、Representation Learning（表示学习）

### Environment / 环境
- **中文**：环境
- **定义**：强化学习中智能体所处的外部系统，智能体与之交互
- **说明**：环境定义了状态空间、动作空间和奖励函数；可以是真实世界或模拟环境（如游戏、仿真器）；智能体通过观察环境状态做决策
- **相关**：Agent（智能体）、State（状态）、Reward（奖励）

### Epoch / 轮次
- **中文**：轮次
- **定义**：训练过程中完整遍历整个训练数据集一次
- **说明**：通常需要多个 epoch 才能收敛；epoch 数过少导致欠拟合，过多导致过拟合；与 batch size 和 iteration 相关：1 epoch = 总样本数 / batch size 个 iteration
- **相关**：Batch Size（批量大小）、Iteration（迭代）、Training（训练）

### Feature / 特征
- **中文**：特征
- **定义**：描述数据样本的属性或变量，用于模型输入
- **说明**：特征可以是数值、类别、文本或图像；特征工程（Feature Engineering）是提升模型性能的关键步骤；好的特征比复杂模型更重要
- **同义词**：Attribute、Variable、Input Feature
- **相关**：Feature Engineering（特征工程）、Feature Selection（特征选择）、Dimensionality Reduction（降维）

### Feature Engineering / 特征工程
- **中文**：特征工程
- **定义**：通过领域知识和数据变换创建、选择和转换特征以提高模型性能的过程
- **说明**：包括特征提取、特征构造、特征缩放、编码分类变量、处理缺失值；是机器学习流程中最耗时的环节
- **相关**：Feature（特征）、Feature Selection（特征选择）、Preprocessing（预处理）

### Feature Selection / 特征选择
- **中文**：特征选择
- **定义**：从所有可用特征中选择最相关特征子集的过程
- **说明**：方法：过滤法（Filter）、包装法（Wrapper）、嵌入法（Embedded）；减少维度、防止过拟合、提高模型可解释性
- **相关**：Feature Engineering（特征工程）、Dimensionality Reduction（降维）

### Gradient / 梯度
- **中文**：梯度
- **定义**：函数在某点的导数向量，指向函数增长最快的方向
- **说明**：梯度下降算法沿负梯度方向更新参数以最小化损失；梯度消失和梯度爆炸是深层网络的训练难题
- **相关**：Gradient Descent（梯度下降）、BackPropagation（反向传播）、Derivative（导数）

### Gradient Descent / 梯度下降
- **中文**：梯度下降
- **定义**：通过沿损失函数负梯度方向迭代更新参数来最小化成本的优化算法
- **说明**：变种：批量梯度下降（Batch GD）、随机梯度下降（SGD）、小批量梯度下降（Mini-batch GD）；学习率控制步长；是训练神经网络的核心算法
- **相关**：Learning Rate（学习率）、Optimizer（优化器）、Stochastic Gradient Descent（随机梯度下降）

### Ground Truth / 真实值
- **中文**：真实值（标注数据）
- **定义**：数据的真实标签或实际测量值，作为模型训练和评估的标准
- **说明**：监督学习需要 ground truth 标注；标注质量直接影响模型性能；获取 ground truth 可能昂贵且耗时
- **同义词**：Label（标签）、True Label
- **相关**：Label（标签）、Supervised Learning（监督学习）、Accuracy（准确率）

### Hyperparameter / 超参数
- **中文**：超参数
- **定义**：模型训练前需要手动设置的参数，控制学习过程
- **说明**：如学习率、批量大小、层数、神经元数、正则化系数；通过验证集或交叉验证调优；不同于模型参数（如权重）
- **相关**：Parameter（参数）、Grid Search（网格搜索）、Cross Validation（交叉验证）

### Inference / 推理
- **中文**：推理
- **定义**：使用训练好的模型对新数据进行预测的过程
- **说明**：推理阶段不涉及参数更新；关注延迟和吞吐量；模型压缩和量化常用于加速推理；与训练（Training）相对
- **相关**：Prediction（预测）、Training（训练）、Model Deployment（模型部署）

### Label / 标签
- **中文**：标签
- **定义**：数据样本的目标输出值或类别标识
- **说明**：监督学习需要标签数据；分类任务中标签是类别；回归任务中标签是连续值；标注（Labeling）是为数据添加标签的过程
- **同义词**：Target、Ground Truth、Annotation
- **相关**：Supervised Learning（监督学习）、Classification（分类）、Regression（回归）

### Learning Rate / 学习率
- **中文**：学习率
- **定义**：梯度下降中每次参数更新的步长大小
- **说明**：学习率过大导致震荡不收敛，过小导致收敛缓慢；常用策略：学习率衰减（Decay）、自适应学习率（Adam、RMSprop）；是最重要的超参数之一
- **相关**：Gradient Descent（梯度下降）、Optimizer（优化器）、Hyperparameter（超参数）

### Loss Function / 损失函数
- **中文**：损失函数
- **定义**：衡量单个样本预测值与真实值差异的函数
- **说明**：常见损失函数：均方误差（MSE，回归）、交叉熵（Cross-Entropy，分类）、对比损失（Contrastive Loss）；目标是最小化总体损失
- **同义词**：Cost Function（成本函数）
- **相关**：Cost Function（成本函数）、Gradient Descent（梯度下降）、BackPropagation（反向传播）

### Machine Learning (ML) / 机器学习
- **中文**：机器学习
- **定义**：使计算机能够从数据中学习规律并做出预测或决策，而无需显式编程的技术
- **说明**：三大类：监督学习（有标签）、无监督学习（无标签）、强化学习（通过与环境交互学习）；是 AI 的核心子领域
- **相关**：Deep Learning（深度学习）、Artificial Intelligence（人工智能）、Algorithm（算法）

### Model / 模型
- **中文**：模型
- **定义**：从数据中学习到的、用于预测或决策的数学表示
- **说明**：模型包含参数（权重和偏置）和结构（网络架构）；训练后保存为文件可复用；常见：线性模型、决策树、神经网络
- **相关**：Training（训练）、Parameter（参数）、Inference（推理）

### Narrow AI / 窄人工智能
- **中文**：窄人工智能
- **定义**：只能在特定任务或领域中表现出智能的 AI 系统
- **说明**：目前所有商用 AI 都是窄 AI，如语音识别、图像分类、推荐系统；与 AGI（通用人工智能）相对
- **同义词**：Weak AI（弱人工智能）
- **相关**：Artificial General Intelligence（通用人工智能）、Artificial Intelligence（人工智能）

### Neural Network / 神经网络
- **中文**：神经网络
- **定义**：受人脑神经元结构启发的计算模型，由大量相互连接的节点（神经元）组成
- **说明**：基本单元：输入层 → 隐藏层 → 输出层；通过调整连接权重学习输入输出映射；深度学习使用深层网络（多层隐藏层）
- **相关**：Deep Learning（深度学习）、Neuron（神经元）、Weight（权重）

### Neuron / 神经元
- **中文**：神经元
- **定义**：神经网络中的基本计算单元，接收输入、加权求和、经激活函数产生输出
- **说明**：模拟生物神经元；输入 × 权重 + 偏置 → 激活函数 → 输出；多个神经元组成层
- **同义词**：Node（节点）、Unit（单元）
- **相关**：Neural Network（神经网络）、Activation Function（激活函数）、Weight（权重）

### Noise / 噪声
- **中文**：噪声
- **定义**：数据中随机、无关或错误的信息，干扰模型学习真实模式
- **说明**：噪声来源：测量误差、标注错误、数据污染；处理方法：平滑、滤波、正则化、增加训练数据
- **相关**：Overfitting（过拟合）、Regularization（正则化）、Data Cleaning（数据清洗）

### Normalization / 归一化
- **中文**：归一化
- **定义**：将数据缩放到特定范围（如 [0,1] 或均值为 0、方差为 1）的预处理技术
- **说明**：加速模型收敛、防止梯度爆炸、使不同特征具有可比性；方法：Min-Max 归一化、Z-Score 标准化、Batch Normalization
- **相关**：Standardization（标准化）、Batch Normalization（批归一化）、Feature Scaling（特征缩放）

### Objective Function / 目标函数
- **中文**：目标函数
- **定义**：模型训练过程中需要最大化或最小化的函数
- **说明**：通常是最小化损失函数（或最大化似然函数）；优化算法（如梯度下降）的目标就是找到目标函数的最优值
- **同义词**：Cost Function（成本函数）、Loss Function（损失函数）
- **相关**：Optimization（优化）、Loss Function（损失函数）

### Optimization / 优化
- **中文**：优化
- **定义**：调整模型参数以最小化损失函数或最大化目标函数的过程
- **说明**：优化算法：梯度下降、Adam、RMSprop、SGD；优化问题可能面临局部最优、鞍点、收敛速度慢等挑战
- **相关**：Gradient Descent（梯度下降）、Optimizer（优化器）、Convergence（收敛）

### Optimizer / 优化器
- **中文**：优化器
- **定义**：实现参数更新策略的算法，用于最小化损失函数
- **说明**：常见优化器：SGD、Momentum、AdaGrad、RMSprop、Adam、AdamW；自适应优化器（如 Adam）自动调整每个参数的学习率
- **相关**：Gradient Descent（梯度下降）、Learning Rate（学习率）、Training（训练）

### Overfitting / 过拟合
- **中文**：过拟合
- **定义**：模型在训练数据上表现很好但在新数据上表现差的现象，即模型记住了训练数据的噪声而非学习通用规律
- **说明**：解决方法：正则化、Dropout、增加数据、早停、简化模型；与 Underfitting（欠拟合）相对
- **相关**：Underfitting（欠拟合）、Regularization（正则化）、Generalization（泛化）

### Parameter / 参数
- **中文**：参数
- **定义**：模型从训练数据中学习得到的内部变量
- **说明**：如神经网络的权重（Weight）和偏置（Bias）；参数在训练过程中自动更新；模型容量与参数数量相关
- **相关**：Weight（权重）、Bias（偏置）、Hyperparameter（超参数）

### Preprocessing / 预处理
- **中文**：预处理
- **定义**：在输入模型前对原始数据进行清洗、转换和标准化的过程
- **说明**：步骤：数据清洗（缺失值、异常值）、特征缩放、编码、降维、数据增强；好的预处理显著提升模型性能
- **相关**：Feature Engineering（特征工程）、Normalization（归一化）、Data Cleaning（数据清洗）

### Regression / 回归
- **中文**：回归
- **定义**：预测连续数值输出的监督学习任务
- **说明**：常用算法：线性回归、多项式回归、岭回归、Lasso、神经网络；评估指标：MSE、RMSE、MAE、R²
- **相关**：Classification（分类）、Supervised Learning（监督学习）、Linear Regression（线性回归）

### Regularization / 正则化
- **中文**：正则化
- **定义**：在损失函数中添加惩罚项以防止过拟合的技术
- **说明**：常见方法：L1 正则化（Lasso，产生稀疏权重）、L2 正则化（Ridge，权重衰减）、Dropout；控制模型复杂度
- **相关**：Overfitting（过拟合）、L1/L2 Regularization、Dropout

### Reinforcement Learning (RL) / 强化学习
- **中文**：强化学习
- **定义**：智能体通过与环境交互、根据奖励反馈学习最优策略的机器学习方法
- **说明**：核心要素：状态（State）、动作（Action）、奖励（Reward）、策略（Policy）；应用：游戏（AlphaGo）、机器人控制、自动驾驶
- **相关**：Agent（智能体）、Environment（环境）、Q-Learning、Policy Gradient（策略梯度）

### Representation Learning / 表示学习
- **中文**：表示学习
- **定义**：自动学习数据的有效特征表示（向量）的技术
- **说明**：深度学习就是表示学习；好的表示使下游任务更简单；包括：词嵌入、图像特征、图嵌入
- **相关**：Embedding（嵌入）、Feature Learning（特征学习）、Deep Learning（深度学习）

### Supervised Learning / 监督学习
- **中文**：监督学习
- **定义**：使用带标签数据训练模型，学习输入到输出的映射关系
- **说明**：任务类型：分类（离散标签）、回归（连续值）；需要大量标注数据；代表算法：决策树、SVM、神经网络
- **相关**：Unsupervised Learning（无监督学习）、Label（标签）、Classification（分类）

### Target / 目标
- **中文**：目标
- **定义**：模型需要预测的真实值或期望输出
- **说明**：监督学习中 target 是已知标签；强化学习中 target 是累积奖励；模型输出与 target 的差异构成损失
- **同义词**：Label、Ground Truth
- **相关**：Label（标签）、Prediction（预测）、Loss Function（损失函数）

### Test Set / 测试集
- **中文**：测试集
- **定义**：用于评估模型最终性能的、未在训练中使用过的数据集
- **说明**：测试集只能使用一次（在模型开发完成后）；反映模型对未知数据的泛化能力；与训练集、验证集相互独立
- **相关**：Training Set（训练集）、Validation Set（验证集）、Generalization（泛化）

### Training / 训练
- **中文**：训练
- **定义**：使用数据调整模型参数以学习输入输出映射的过程
- **说明**：训练涉及前向传播、计算损失、反向传播、参数更新；需要选择合适的优化器、学习率和批次大小
- **相关**：Training Set（训练集）、BackPropagation（反向传播）、Convergence（收敛）

### Training Set / 训练集
- **中文**：训练集
- **定义**：用于训练模型参数的数据子集
- **说明**：通常占总数据的 60-80%；模型通过训练集学习特征和模式；训练集需要足够大且有代表性
- **相关**：Test Set（测试集）、Validation Set（验证集）、Epoch（轮次）

### Underfitting / 欠拟合
- **中文**：欠拟合
- **定义**：模型过于简单，无法捕捉数据的基本模式，在训练集和测试集上表现都差
- **说明**：解决方法：增加模型复杂度、增加特征、减少正则化、增加训练时间；与 Overfitting（过拟合）相对
- **相关**：Overfitting（过拟合）、Model Capacity（模型容量）、Bias-Variance Tradeoff（偏差-方差权衡）

### Unsupervised Learning / 无监督学习
- **中文**：无监督学习
- **定义**：从无标签数据中自动发现隐藏模式或结构的机器学习方法
- **说明**：主要任务：聚类（Clustering）、降维（Dimensionality Reduction）、密度估计、异常检测；代表算法：K-Means、PCA、Autoencoder
- **相关**：Supervised Learning（监督学习）、Clustering（聚类）、Dimensionality Reduction（降维）

### Validation Set / 验证集
- **中文**：验证集
- **定义**：用于调整超参数和评估模型在训练过程中表现的独立数据集
- **说明**：不参与参数更新；用于早停（Early Stopping）和模型选择；防止过拟合训练集；通常占总数据的 10-20%
- **相关**：Training Set（训练集）、Test Set（测试集）、Cross Validation（交叉验证）

### Weight / 权重
- **中文**：权重
- **定义**：神经网络中连接神经元的参数，决定输入信号的重要性
- **说明**：权重在训练过程中通过反向传播和梯度下降更新；权重初始化影响训练效果；权重矩阵是网络的核心参数
- **同义词**：Weight Matrix、Connection Weight
- **相关**：Bias（偏置）、Parameter（参数）、Neural Network（神经网络）
