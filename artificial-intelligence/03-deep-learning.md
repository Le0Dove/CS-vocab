# 03. 深度学习 (Deep Learning)

## 神经网络架构

### Attention Mechanism / 注意力机制
- **中文**：注意力机制
- **定义**：允许模型在处理序列时动态关注输入不同部分的技术
- **说明**：模拟人类视觉注意力；计算查询（Query）与键（Key）的相似度得到注意力权重，加权求和值（Value）；是 Transformer 的核心
- **相关**：Transformer、Self-Attention（自注意力）、Query-Key-Value（QKV）

### Batch Normalization / 批归一化
- **中文**：批归一化
- **定义**：对每个小批量数据的每一层输入进行标准化（均值为 0、方差为 1）的技术
- **说明**：加速训练收敛、允许更高学习率、减少对初始化的依赖、有轻微正则化效果；训练和推理时行为不同
- **相关**：Normalization（归一化）、Layer Normalization（层归一化）、Training（训练）

### CNN (Convolutional Neural Network) / 卷积神经网络
- **中文**：卷积神经网络
- **定义**：使用卷积层提取空间层次特征的深度神经网络，特别适合图像数据
- **说明**：核心组件：卷积层（提取特征）、池化层（降采样）、全连接层（分类）；经典架构：LeNet、AlexNet、VGG、ResNet
- **相关**：Convolution（卷积）、Pooling（池化）、Computer Vision（计算机视觉）

### Convolution / 卷积
- **中文**：卷积
- **定义**：用滤波器（卷积核）在输入数据上滑动进行局部加权求和的运算
- **说明**：提取局部特征（如边缘、纹理）；参数共享减少参数量；输出特征图（Feature Map）；有 padding 和 stride 控制输出大小
- **相关**：CNN、Kernel（卷积核）、Feature Map（特征图）

### Dense Layer / 全连接层
- **中文**：全连接层
- **定义**：每个输入与每个输出都有连接的神经网络层
- **说明**：也叫 Linear Layer 或 Fully Connected Layer；通常位于网络后端用于分类；参数量大；是神经网络的基础层
- **同义词**：Fully Connected Layer、Linear Layer
- **相关**：Neural Network（神经网络）、Weight（权重）、Activation Function（激活函数）

### Dropout / 随机失活
- **中文**：随机失活
- **定义**：训练时以一定概率随机丢弃神经元、防止过拟合的正则化技术
- **说明**：丢弃概率通常设为 0.2-0.5；推理时所有神经元激活但输出缩放；可看作模型集成的近似
- **相关**：Regularization（正则化）、Overfitting（过拟合）、Ensemble Learning（集成学习）

### Encoder-Decoder / 编码器-解码器
- **中文**：编码器-解码器
- **定义**：将输入序列编码为上下文向量再解码为输出序列的架构
- **说明**：广泛用于机器翻译、文本摘要、语音识别；编码器提取输入特征，解码器生成输出；注意力机制改进长序列效果
- **同义词**：Seq2Seq（序列到序列）
- **相关**：Sequence-to-Sequence、Attention Mechanism（注意力机制）、Transformer

### GAN (Generative Adversarial Network) / 生成对抗网络
- **中文**：生成对抗网络
- **定义**：由生成器（Generator）和判别器（Discriminator）相互对抗训练的无监督生成模型
- **说明**：生成器生成假样本，判别器区分真假；两者博弈使生成器最终产生逼真数据；应用：图像生成、风格迁移、超分辨率
- **相关**：Generator（生成器）、Discriminator（判别器）、Generative Model（生成模型）

### LSTM (Long Short-Term Memory) / 长短期记忆网络
- **中文**：长短期记忆网络
- **定义**：改进的循环神经网络，通过门控机制解决长序列梯度消失问题
- **说明**：包含输入门、遗忘门、输出门和细胞状态；能记忆长期依赖；广泛用于 NLP 和时间序列预测
- **相关**：RNN、GRU、Vanishing Gradient（梯度消失）

### Multi-Head Attention / 多头注意力
- **中文**：多头注意力
- **定义**：并行计算多组注意力、将不同子空间表示拼接的注意力机制
- **说明**：不同头关注不同方面（语法、语义、指代等）；增加模型表达能力；是 Transformer 的核心组件
- **相关**：Attention Mechanism（注意力机制）、Transformer、Self-Attention（自注意力）

### Pooling / 池化
- **中文**：池化
- **定义**：通过下采样减少特征图空间尺寸、保留主要特征的操作
- **说明**：常见方式：最大池化（Max Pooling，取最大值）、平均池化（Average Pooling）；减少参数量、提供平移不变性
- **相关**：CNN、Downsampling（下采样）、Stride（步长）

### ResNet (Residual Network) / 残差网络
- **中文**：残差网络
- **定义**：通过跳跃连接（Skip Connection）解决深层网络退化问题的卷积神经网络
- **说明**：引入残差块：输出 = F(x) + x；可训练超过 1000 层的网络；ImageNet 2015 冠军；革命性架构
- **相关**：Skip Connection（跳跃连接）、CNN、Deep Learning（深度学习）

### RNN (Recurrent Neural Network) / 循环神经网络
- **中文**：循环神经网络
- **定义**：具有循环连接、能处理序列数据的神经网络，隐藏状态传递历史信息
- **说明**：适合时间序列、文本等有序数据；变体：LSTM、GRU、双向 RNN；存在梯度消失/爆炸问题
- **相关**：LSTM、GRU、Sequence Modeling（序列建模）

### Skip Connection / 跳跃连接
- **中文**：跳跃连接
- **定义**：将网络某层的输入直接加到后面层输出的连接方式
- **说明**：缓解梯度消失、允许训练更深的网络；代表：ResNet 的残差连接、DenseNet 的密集连接
- **同义词**：Residual Connection（残差连接）、Shortcut Connection
- **相关**：ResNet、BackPropagation（反向传播）、Deep Network（深层网络）

### Transformer / Transformer
- **中文**：Transformer
- **定义**：完全基于自注意力机制、摒弃循环和卷积的序列转换模型
- **说明**：2017 年 Google 提出（"Attention Is All You Need"）；编码器-解码器结构；并行计算效率高；是 GPT、BERT 等的基础
- **相关**：Self-Attention（自注意力）、BERT、GPT、Attention Mechanism（注意力机制）

---

## 生成模型

### Auto-Regressive Model / 自回归模型
- **中文**：自回归模型
- **定义**：按顺序逐个生成输出序列元素、每个元素依赖之前生成结果的生成模型
- **说明**：如 GPT 系列；训练时预测下一个 token；生成时自回归采样；适合文本、音频生成
- **相关**：GPT、Sequence Generation（序列生成）、Language Model（语言模型）

### Diffusion Model / 扩散模型
- **中文**：扩散模型
- **定义**：通过逐步向数据添加噪声再学习去噪过程来生成数据的模型
- **说明**：包含前向扩散（加噪）和反向去噪（生成）两个过程；Stable Diffusion、DALL-E 2、Midjourney 基于此；生成质量高
- **相关**：Generative Model（生成模型）、Stable Diffusion、Denoising（去噪）

### Discriminator / 判别器
- **中文**：判别器
- **定义**：GAN 中判断输入是真实数据还是生成器生成假数据的网络
- **说明**：二元分类器；训练目标是最大化区分真假的能力；与生成器交替训练
- **相关**：GAN、Generator（生成器）、Binary Classification（二分类）

### Generative Model / 生成模型
- **中文**：生成模型
- **定义**：学习数据分布、能生成新样本的模型
- **说明**：代表：GAN、VAE、Flow-based Model、Diffusion Model；与判别模型（Discriminative Model）相对；可生成图像、文本、音频
- **相关**：GAN、VAE、Diffusion Model、Discriminative Model（判别模型）

### Generator / 生成器
- **中文**：生成器
- **定义**：GAN 中从随机噪声生成假样本的网络
- **说明**：输入是随机向量（Latent Vector），输出生成样本；训练目标是欺骗判别器；生成质量随训练提升
- **相关**：GAN、Discriminator（判别器）、Latent Space（潜在空间）

### Latent Space / 潜在空间
- **中文**：潜在空间
- **定义**：生成模型中低维的、编码数据语义特征的连续向量空间
- **说明**：潜在空间中的插值对应数据的平滑过渡（如人脸渐变）；是可解释性研究的重点
- **相关**：Embedding（嵌入）、Generative Model（生成模型）、Interpolation（插值）

### VAE (Variational Autoencoder) / 变分自编码器
- **中文**：变分自编码器
- **定义**：在自编码器基础上引入概率建模、能生成新样本的生成模型
- **说明**：编码器输出潜在变量的分布参数（均值和方差）；通过重参数化技巧采样；生成平滑且有结构的潜在空间
- **相关**：Autoencoder（自编码器）、Generative Model（生成模型）、Latent Space（潜在空间）

---

## 训练技术

### Data Augmentation / 数据增强
- **中文**：数据增强
- **定义**：通过对训练数据进行变换（旋转、裁剪、翻转等）生成新样本、扩充数据集的技术
- **说明**：提高模型泛化能力、减少过拟合；图像增强：旋转、缩放、裁剪、颜色抖动；文本增强：同义词替换、回译
- **相关**：Overfitting（过拟合）、Training Set（训练集）、Regularization（正则化）

### Fine-Tuning / 微调
- **中文**：微调
- **定义**：在大规模预训练模型的基础上，用特定任务数据调整模型参数的过程
- **说明**：比从头训练更快、数据需求更少；可微调全部层或只微调顶层；迁移学习的核心步骤
- **相关**：Transfer Learning（迁移学习）、Pre-Trained Model（预训练模型）、Training（训练）

### Learning Rate Decay / 学习率衰减
- **中文**：学习率衰减
- **定义**：训练过程中逐步降低学习率的策略
- **说明**：帮助模型更精细地收敛到最优解；策略：阶梯衰减、指数衰减、余弦退火；防止训练后期震荡
- **相关**：Learning Rate（学习率）、Optimizer（优化器）、Convergence（收敛）

### Mini-Batch / 小批量
- **中文**：小批量
- **定义**：每次梯度更新使用的小批量样本集合
- **说明**：平衡计算效率和梯度估计稳定性；大小通常为 16、32、64、128、256；Batch Size 影响内存使用和收敛速度
- **相关**：Batch Size（批量大小）、Gradient Descent（梯度下降）、Stochastic Gradient Descent（随机梯度下降）

### Pre-Trained Model / 预训练模型
- **中文**：预训练模型
- **定义**：在大规模通用数据集上预先训练好的模型
- **说明**：预训练模型学到通用特征表示；通过微调适配下游任务；代表：BERT、GPT、ResNet、VGG
- **相关**：Fine-Tuning（微调）、Transfer Learning（迁移学习）、Foundation Model（基础模型）

### Transfer Learning / 迁移学习
- **中文**：迁移学习
- **定义**：将在源任务上学到的知识应用到不同但相关的目标任务上的技术
- **说明**：减少数据需求和训练时间；常用做法：使用预训练模型作为特征提取器或微调；广泛应用于 CV 和 NLP
- **相关**：Pre-Trained Model（预训练模型）、Fine-Tuning（微调）、Domain Adaptation（域适应）

### Weight Initialization / 权重初始化
- **中文**：权重初始化
- **定义**：神经网络训练前对权重设置初始值的方法
- **说明**：好的初始化加速收敛、防止梯度消失/爆炸；方法：Xavier/Glorot 初始化、He 初始化、正态分布初始化
- **相关**：Training（训练）、Convergence（收敛）、Vanishing Gradient（梯度消失）

---

## 优化器与损失

### Adam / Adam 优化器
- **中文**：Adam 优化器
- **全称**：Adaptive Moment Estimation
- **定义**：结合动量（Momentum）和自适应学习率、为每个参数单独调整学习率的优化算法
- **说明**：计算梯度的一阶矩（均值）和二阶矩（方差）估计；默认超参数：β1=0.9, β2=0.999, ε=1e-8；最常用的优化器之一
- **相关**：Optimizer（优化器）、Momentum（动量）、Learning Rate（学习率）

### Cross-Entropy Loss / 交叉熵损失
- **中文**：交叉熵损失
- **定义**：分类任务中衡量预测概率分布与真实标签差异的损失函数
- **说明**：二分类用 Binary Cross-Entropy，多分类用 Categorical Cross-Entropy；常与 Softmax 配合使用
- **相关**：Loss Function（损失函数）、Entropy（熵）、Softmax

### Gradient Clipping / 梯度裁剪
- **中文**：梯度裁剪
- **定义**：当梯度超过阈值时将其缩放到阈值范围内的技术
- **说明**：防止梯度爆炸；对 RNN 训练尤为重要；裁剪方式：按值裁剪、按范数裁剪
- **相关**：Gradient（梯度）、Exploding Gradient（梯度爆炸）、RNN

### Learning Rate Scheduling / 学习率调度
- **中文**：学习率调度
- **定义**：根据训练进度动态调整学习率的策略
- **说明**：策略：Step Decay（阶梯衰减）、Exponential Decay（指数衰减）、Cosine Annealing（余弦退火）、Warmup（预热）；影响收敛速度和最终性能
- **相关**：Learning Rate（学习率）、Optimizer（优化器）、Training（训练）

### Momentum / 动量
- **中文**：动量
- **定义**：在梯度下降中引入速度累积、加速沿同一方向更新并抑制震荡的技术
- **说明**：模拟物理动量；参数更新不仅依赖当前梯度还依赖历史梯度；常用系数 0.9；加速收敛
- **相关**：Gradient Descent（梯度下降）、Optimizer（优化器）、SGD

### RMSprop / RMSprop
- **中文**：均方根传播
- **定义**：自适应调整每个参数学习率的优化算法，使用梯度的指数移动平均
- **说明**：解决 AdaGrad 学习率单调递减问题；适合非平稳目标；是 Adam 的基础组件之一
- **相关**：AdaGrad、Adam、Optimizer（优化器）

### SGD (Stochastic Gradient Descent) / 随机梯度下降
- **中文**：随机梯度下降
- **定义**：每次迭代使用单个或小批量随机样本估计梯度并更新参数的优化算法
- **说明**：计算速度快、内存需求低；引入噪声有助于跳出局部最优；配合动量效果更好
- **相关**：Gradient Descent（梯度下降）、Mini-Batch（小批量）、Momentum（动量）

### Warmup / 预热
- **中文**：预热
- **定义**：训练开始时从很小的学习率逐步增加到设定值的学习率调度策略
- **说明**：防止初期大学习率导致的不稳定；特别适用于 Transformer 等大模型；通常预热几个 epoch 或步数
- **相关**：Learning Rate Scheduling（学习率调度）、Transformer、Training（训练）

### Weight Decay / 权重衰减
- **中文**：权重衰减
- **定义**：L2 正则化的实现方式，在参数更新时将权重乘以略小于 1 的系数
- **说明**：等价于在损失函数中添加 L2 惩罚；防止权重过大导致过拟合；AdamW 将权重衰减与梯度更新解耦
- **相关**：L2 Regularization（L2 正则化）、AdamW、Overfitting（过拟合）

---

## 大模型与前沿

### Foundation Model / 基础模型
- **中文**：基础模型
- **定义**：在大规模无标注数据上预训练、可适配多种下游任务的大型模型
- **说明**：代表：GPT、BERT、CLIP、DALL-E；通过微调或提示工程适配特定任务；是 AI 发展的重要范式
- **相关**：Pre-Trained Model（预训练模型）、Transfer Learning（迁移学习）、LLM（大语言模型）

### Large Language Model (LLM) / 大语言模型
- **中文**：大语言模型
- **定义**：参数量巨大（通常数十亿到数千亿）、在海量文本上训练的语言模型
- **说明**：代表：GPT-4、Claude、LLaMA、ChatGLM；具备涌现能力（Emergent Ability）；应用：对话、代码生成、推理
- **相关**：Foundation Model（基础模型）、Transformer、Prompt Engineering（提示工程）

### Prompt Engineering / 提示工程
- **中文**：提示工程
- **定义**：设计和优化输入提示（Prompt）以引导大语言模型生成期望输出的技术
- **说明**：包括零样本提示（Zero-Shot）、少样本提示（Few-Shot）、思维链（Chain-of-Thought）；无需微调即可适配任务
- **相关**：LLM（大语言模型）、Zero-Shot、Few-Shot、Chain-of-Thought（思维链）

---

## 常见问题

### Catastrophic Forgetting / 灾难性遗忘
- **中文**：灾难性遗忘
- **定义**：神经网络在学习新任务后遗忘已学旧任务知识的现象
- **说明**：连续学习（Continual Learning）的核心问题；解决方法：弹性权重巩固（EWC）、回放（Replay）、参数隔离
- **相关**：Continual Learning（持续学习）、Transfer Learning（迁移学习）

### Exploding Gradient / 梯度爆炸
- **中文**：梯度爆炸
- **定义**：反向传播时梯度变得极大、导致参数更新过大、训练不稳定的现象
- **说明**：常见于深层网络和 RNN；解决方法：梯度裁剪、权重正则化、使用 ReLU、残差连接
- **相关**：Vanishing Gradient（梯度消失）、Gradient Clipping（梯度裁剪）、RNN

### Mode Collapse / 模式坍塌
- **中文**：模式坍塌
- **定义**：GAN 中生成器只生成有限种类样本、无法覆盖数据全部分布的问题
- **说明**：判别器无法区分时生成器失去多样性动力；解决方法：Wasserstein GAN、多样性损失、unrolled GAN
- **相关**：GAN、Generative Model（生成模型）、Diversity（多样性）

### Vanishing Gradient / 梯度消失
- **中文**：梯度消失
- **定义**：反向传播时梯度逐层减小、导致浅层网络参数几乎不更新的现象
- **说明**：常见于深层网络和 sigmoid/tanh 激活函数；解决方法：ReLU、残差连接、批归一化、更好的初始化
- **相关**：Exploding Gradient（梯度爆炸）、BackPropagation（反向传播）、ReLU
