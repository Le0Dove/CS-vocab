# 04. 自然语言处理 (Natural Language Processing)

## 基础概念

### BLEU / BLEU 分数
- **中文**：BLEU 分数
- **全称**：Bilingual Evaluation Understudy
- **定义**：衡量机器生成文本与参考文本相似度的自动评估指标
- **说明**：基于精确率和 N-gram 重叠；范围 0-1，越接近 1 越好；广泛用于机器翻译评估；对短句惩罚
- **相关**：Machine Translation（机器翻译）、N-gram、METEOR

### BERT / BERT 模型
- **中文**：BERT 模型
- **全称**：Bidirectional Encoder Representations from Transformers
- **定义**：Google 提出的基于 Transformer 编码器的双向预训练语言模型
- **说明**：双向上下文理解；预训练任务：掩码语言模型（MLM）和下一句预测（NSP）；通过微调适配下游任务；NLP 里程碑
- **相关**：Transformer、Pre-Trained Model（预训练模型）、Fine-Tuning（微调）

### Corpus / 语料库
- **中文**：语料库
- **定义**：用于语言研究和 NLP 模型训练的大规模文本集合
- **说明**：语料库需预处理（分词、去噪）；代表：Wikipedia、Common Crawl、BookCorpus；领域特定语料库提升领域模型性能
- **同义词**：Text Corpus、Dataset（数据集）
- **相关**：Tokenization（分词）、Preprocessing（预处理）、Language Model（语言模型）

### Embedding / 嵌入
- **中文**：嵌入
- **定义**：将词语、句子或文档映射到低维连续向量空间的技术
- **说明**：语义相近的词在向量空间中距离近；Word2Vec、GloVe 是经典词嵌入；BERT 提供上下文相关嵌入
- **相关**：Word2Vec、GloVe、Vector Space（向量空间）

### GPT / GPT 模型
- **中文**：GPT 模型
- **全称**：Generative Pre-trained Transformer
- **定义**：OpenAI 提出的基于 Transformer 解码器的自回归预训练语言模型
- **说明**：GPT-1/2/3/4 系列；使用因果语言模型（预测下一个词）预训练；GPT-3/4 展现少样本学习能力；ChatGPT 基于此
- **相关**：Transformer、LLM（大语言模型）、Prompt Engineering（提示工程）

### Language Model / 语言模型
- **中文**：语言模型
- **定义**：建模词语序列概率分布、预测下一个词或评估句子合理性的模型
- **说明**：N-gram 模型（统计方法）、神经网络语言模型（NNLM）、预训练语言模型（BERT、GPT）；是 NLP 的核心组件
- **相关**：NLP、BERT、GPT、Perplexity（困惑度）

### Natural Language Processing (NLP) / 自然语言处理
- **中文**：自然语言处理
- **定义**：使计算机理解、解释和生成人类语言的交叉学科
- **说明**：任务包括：分词、句法分析、语义理解、机器翻译、问答系统、文本摘要、情感分析；结合语言学和机器学习
- **相关**：NLU（自然语言理解）、NLG（自然语言生成）、Computational Linguistics（计算语言学）

### Natural Language Understanding (NLU) / 自然语言理解
- **中文**：自然语言理解
- **定义**：使计算机理解人类语言含义的技术
- **说明**：任务：意图识别、实体抽取、关系抽取、语义解析；是 NLP 的核心子领域；与 NLG（自然语言生成）相对
- **相关**：NLP、Intent Recognition（意图识别）、Named Entity Recognition（命名实体识别）

### Named Entity Recognition (NER) / 命名实体识别
- **中文**：命名实体识别
- **定义**：从文本中识别并分类命名实体（人名、地名、组织名等）的任务
- **说明**：通常建模为序列标注问题；使用 BIO/BILOU 标注方案；是信息抽取的基础步骤
- **相关**：Information Extraction（信息抽取）、Sequence Labeling（序列标注）、Token Classification（Token 分类）

### N-gram / N 元语法
- **中文**：N 元语法
- **定义**：文本中连续出现的 N 个词组成的序列
- **说明**：N=1（Unigram）、N=2（Bigram）、N=3（Trigram）；基于马尔可夫假设；简单但无法捕捉长距离依赖
- **相关**：Language Model（语言模型）、Markov Assumption（马尔可夫假设）、Smoothing（平滑）

### Perplexity / 困惑度
- **中文**：困惑度
- **定义**：衡量语言模型预测能力的指标，表示模型对下一个词预测的不确定性
- **说明**：困惑度越低越好；可理解为模型面临的有效选择数；用于评估和比较语言模型
- **相关**：Language Model（语言模型）、Cross-Entropy（交叉熵）、Probability（概率）

### POS Tagging / 词性标注
- **中文**：词性标注
- **全称**：Part-of-Speech Tagging
- **定义**：为句子中每个词标注语法类别（名词、动词、形容词等）的任务
- **说明**：是句法分析的基础；现代方法使用序列标注模型（BiLSTM-CRF、BERT）；标注集如 Penn Treebank
- **相关**：Sequence Labeling（序列标注）、Syntax Analysis（句法分析）

### Sentiment Analysis / 情感分析
- **中文**：情感分析
- **定义**：识别和提取文本中主观信息（情感倾向）的任务
- **说明**：粒度和类别：文档级、句子级、方面级；极性：正面、负面、中性；应用：舆情监控、产品评价分析
- **同义词**：Opinion Mining（观点挖掘）
- **相关**：Text Classification（文本分类）、NLP、Classification（分类）

### Sequence Labeling / 序列标注
- **中文**：序列标注
- **定义**：为序列中每个元素分配标签的任务
- **说明**：应用：NER、POS 标注、分词；常用模型：HMM、CRF、BiLSTM-CRF、BERT；需考虑标签间的依赖关系
- **相关**：Named Entity Recognition（命名实体识别）、POS Tagging（词性标注）、CRF

### Stop Word / 停用词
- **中文**：停用词
- **定义**：在文本处理中被过滤掉的常见低信息词（如"的"、"是"、"the"、"a"）
- **说明**：减少噪声、降低维度；停用词表需根据任务和语言定制；某些任务（如情感分析）中保留停用词可能更好
- **相关**：Tokenization（分词）、Text Preprocessing（文本预处理）

### Syntax Analysis / 句法分析
- **中文**：句法分析
- **定义**：分析句子语法结构、确定词与词之间句法关系的任务
- **说明**：包括依存句法分析（Dependency Parsing）和成分句法分析（Constituency Parsing）；生成句法树
- **相关**：Parsing（解析）、POS Tagging（词性标注）、Grammar（语法）

### Token / 词元
- **中文**：词元
- **定义**：文本被分词后的最小单位，可以是词、子词或字符
- **说明**：Tokenization 方法：基于空格、BPE（Byte Pair Encoding）、WordPiece、SentencePiece；GPT 使用 BPE，BERT 使用 WordPiece
- **同义词**：Token
- **相关**：Tokenization（分词）、Vocabulary（词表）、Embedding（嵌入）

### Tokenization / 分词
- **中文**：分词
- **定义**：将连续文本切分为词元（Token）序列的过程
- **说明**：语言差异：英文按空格分词较简单，中文需要专门分词器（如 Jieba）；现代方法：BPE、WordPiece、SentencePiece；影响词表大小和模型性能
- **相关**：Token（词元）、Vocabulary（词表）、BPE

### Vocabulary / 词表
- **中文**：词表
- **定义**：模型知道的所有词元的集合
- **说明**：词表大小影响模型容量和计算量；BPE/WordPiece 构建子词词表平衡词表大小和覆盖度；OOV（Out-of-Vocabulary）问题
- **相关**：Token（词元）、Tokenization（分词）、Embedding（嵌入）

### Word2Vec / Word2Vec
- **中文**：Word2Vec
- **定义**：Google 提出的用于学习词向量表示的浅层神经网络模型
- **说明**：两种架构：CBOW（根据上下文预测中心词）、Skip-gram（根据中心词预测上下文）；捕捉词语语义关系
- **相关**：Word Embedding（词嵌入）、GloVe、Skip-gram

---

## 高级主题

### Attention Is All You Need / Attention Is All You Need
- **中文**：Attention Is All You Need
- **定义**：2017 年 Google 提出的 Transformer 架构的奠基性论文
- **说明**：提出完全基于注意力机制的 Transformer，摒弃 RNN 和 CNN；成为现代 NLP 和深度学习的基石
- **相关**：Transformer、Self-Attention（自注意力）、BERT、GPT

### Byte Pair Encoding (BPE) / 字节对编码
- **中文**：字节对编码
- **定义**：通过合并频率最高的字符对来构建子词词表的分词算法
- **说明**：处理未登录词（OOV）；平衡词表大小和表达能力；被 GPT、RoBERTa 使用
- **相关**：Tokenization（分词）、Subword（子词）、Vocabulary（词表）

### Chain-of-Thought (CoT) / 思维链
- **中文**：思维链
- **定义**：引导大语言模型逐步推理、生成中间步骤再得出最终答案的提示技术
- **说明**：提升复杂推理能力；Few-Shot CoT 提供示例推理步骤；Zero-Shot CoT 用"Let's think step by step"触发
- **相关**：Prompt Engineering（提示工程）、LLM（大语言模型）、Reasoning（推理）

### Few-Shot Learning / 少样本学习
- **中文**：少样本学习
- **定义**：模型仅从少量示例中学习并泛化到新任务的能力
- **说明**：大语言模型（如 GPT-3）展现强大的 Few-Shot 能力；提示中包含几个示例即可完成任务
- **相关**：Zero-Shot、Prompt Engineering（提示工程）、In-Context Learning（上下文学习）

### Fine-Tuning / 微调
- **中文**：微调
- **定义**：在预训练语言模型基础上用特定任务数据调整参数的过程
- **说明**：全量微调（Full Fine-Tuning）更新所有参数；参数高效微调（PEFT）：LoRA、Adapter、Prompt Tuning 只更新少量参数
- **相关**：Pre-Trained Model（预训练模型）、Transfer Learning（迁移学习）、LoRA

### In-Context Learning / 上下文学习
- **中文**：上下文学习
- **定义**：大语言模型仅通过提示中的上下文示例学习新任务、无需参数更新的能力
- **说明**：是 Few-Shot Learning 的一种形式；模型从上下文推断任务模式和输出格式
- **相关**：Few-Shot、Prompt Engineering（提示工程）、LLM（大语言模型）

### LoRA (Low-Rank Adaptation) / 低秩适配
- **中文**：低秩适配
- **定义**：通过低秩矩阵分解微调预训练模型、大幅减少可训练参数的参数高效微调方法
- **说明**：冻结原始权重，只训练低秩分解矩阵；参数量减少为原来的 1% 以下；适合大模型微调
- **相关**：Fine-Tuning（微调）、PEFT、Parameter-Efficient Fine-Tuning（参数高效微调）

### Masked Language Model (MLM) / 掩码语言模型
- **中文**：掩码语言模型
- **定义**：随机掩盖输入序列中的部分词元、让模型预测被掩盖词的训练任务
- **说明**：BERT 的核心预训练任务；双向上下文理解；掩码比例通常 15%
- **相关**：BERT、Pre-Training（预训练）、Causal Language Model（因果语言模型）

### Machine Translation / 机器翻译
- **中文**：机器翻译
- **定义**：使用计算机将一种自然语言自动翻译为另一种语言的任务
- **说明**：发展：基于规则 → 统计机器翻译（SMT）→ 神经机器翻译（NMT）；Transformer 使 NMT 成为主流；评估指标：BLEU、METEOR
- **相关**：NMT（神经机器翻译）、Seq2Seq、Transformer、BLEU

### Neural Machine Translation (NMT) / 神经机器翻译
- **中文**：神经机器翻译
- **定义**：使用神经网络（通常是编码器-解码器架构）进行机器翻译的方法
- **说明**：NMT 翻译更流畅、能学习语义；注意力机制改善长句翻译；代表：Google Neural Machine Translation、OpenNMT
- **相关**：Machine Translation（机器翻译）、Seq2Seq、Attention Mechanism（注意力机制）

### Next Sentence Prediction (NSP) / 下一句预测
- **中文**：下一句预测
- **定义**：BERT 预训练任务之一，判断句子 B 是否是句子 A 的下一句
- **说明**：帮助模型学习句子级关系；在 RoBERTa 等后续工作中被证明贡献有限而被移除
- **相关**：BERT、MLM、Pre-Training（预训练）

### Prompt / 提示
- **中文**：提示
- **定义**：输入给大语言模型的文本指令或问题，引导模型生成期望输出
- **说明**：提示设计影响输出质量；类型：Zero-Shot Prompt（无示例）、Few-Shot Prompt（含示例）、System Prompt（系统提示）
- **相关**：Prompt Engineering（提示工程）、LLM（大语言模型）、In-Context Learning（上下文学习）

### Question Answering (QA) / 问答系统
- **中文**：问答系统
- **定义**：根据给定问题从文本或知识库中自动提取或生成答案的系统
- **说明**：类型：抽取式 QA（从文本中抽答案）、生成式 QA（生成答案）、多跳 QA（需推理多个文档）；应用：智能客服、搜索引擎
- **相关**：Information Retrieval（信息检索）、NLP、MRC（机器阅读理解）

### Seq2Seq (Sequence-to-Sequence) / 序列到序列
- **中文**：序列到序列
- **定义**：将输入序列映射到输出序列的模型架构
- **说明**：经典结构：编码器（Encoder）+ 解码器（Decoder）；用于机器翻译、文本摘要、语音识别；注意力机制增强效果
- **同义词**：Encoder-Decoder
- **相关**：Encoder-Decoder、Attention Mechanism（注意力机制）、Machine Translation（机器翻译）

### Syntactic Parsing / 句法解析
- **中文**：句法解析
- **定义**：分析句子语法结构、构建句法树的过程
- **说明**：依存解析（Dependency Parsing）关注词间关系；成分解析（Constituency Parsing）关注短语结构；是 NLP 的基础任务
- **相关**：Syntax Analysis（句法分析）、Grammar（语法）、Tree（树）

### Text Classification / 文本分类
- **中文**：文本分类
- **定义**：将文本分配到一个或多个预定义类别的任务
- **说明**：应用：垃圾邮件检测、情感分析、主题分类、意图识别；传统方法：TF-IDF + SVM；现代方法：BERT 微调
- **相关**：Classification（分类）、Sentiment Analysis（情感分析）、TF-IDF

### TF-IDF / 词频-逆文档频率
- **中文**：词频-逆文档频率
- **定义**：衡量词语在文档中重要性的统计指标，结合词频和逆文档频率
- **说明**：TF（词频）：词在文档中出现次数；IDF（逆文档频率）：log(总文档数/包含该词的文档数)；常用于信息检索和文本分类
- **相关**：Text Classification（文本分类）、Information Retrieval（信息检索）、Bag of Words（词袋模型）

### Zero-Shot / 零样本
- **中文**：零样本
- **定义**：模型在完全没有见过任务示例的情况下执行新任务的能力
- **说明**：大语言模型的重要能力；通过自然语言指令描述任务；与 Few-Shot 相对
- **相关**：Few-Shot、Prompt Engineering（提示工程）、LLM（大语言模型）
