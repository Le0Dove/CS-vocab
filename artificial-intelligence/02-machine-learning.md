# 02. 机器学习 (Machine Learning)

## 监督学习

### AdaBoost / 自适应提升
- **中文**：自适应提升
- **定义**：通过串行训练多个弱分类器、关注被前一个分类器分错样本的集成学习方法
- **说明**：调整样本权重使后续分类器重点关注难分样本；弱分类器组合成强分类器；对噪声敏感
- **相关**：Boosting、Ensemble Learning（集成学习）、Gradient Boosting（梯度提升）

### Bayes' Theorem / 贝叶斯定理
- **中文**：贝叶斯定理
- **定义**：描述条件概率关系的公式：P(A|B) = P(B|A) * P(A) / P(B)
- **说明**：机器学习基础；朴素贝叶斯分类器基于此定理；用于概率推理和不确定性建模
- **相关**：Naive Bayes（朴素贝叶斯）、Conditional Probability（条件概率）、Posterior Probability（后验概率）

### Boosting / 提升
- **中文**：提升
- **定义**：通过串行训练多个弱学习器，每轮关注前一轮错误样本，最后组合成强学习器的集成方法
- **说明**：代表算法：AdaBoost、Gradient Boosting、XGBoost、LightGBM、CatBoost；串行训练，不能并行化
- **相关**：Bagging、Ensemble Learning（集成学习）、AdaBoost

### Confusion Matrix / 混淆矩阵
- **中文**：混淆矩阵
- **定义**：展示分类模型预测结果与实际标签对比的表格
- **说明**：包含 TP（真正例）、FP（假正例）、TN（真负例）、FN（假负例）；用于计算准确率、精确率、召回率、F1 分数
- **相关**：Accuracy（准确率）、Precision（精确率）、Recall（召回率）、F1 Score（F1 分数）

### Cross-Entropy / 交叉熵
- **中文**：交叉熵
- **定义**：衡量两个概率分布之间差异的损失函数
- **说明**：分类任务的标准损失函数；二分类用 Binary Cross-Entropy，多分类用 Categorical Cross-Entropy；与 softmax 配合使用
- **相关**：Entropy（熵）、Loss Function（损失函数）、Softmax

### Decision Tree / 决策树
- **中文**：决策树
- **定义**：通过递归划分特征空间、基于树形结构进行决策的监督学习模型
- **说明**：易于理解和解释；可处理数值和类别特征；容易过拟合，需剪枝（Pruning）；代表：ID3、C4.5、CART
- **相关**：Random Forest（随机森林）、Information Gain（信息增益）、Pruning（剪枝）

### Ensemble Learning / 集成学习
- **中文**：集成学习
- **定义**：组合多个基学习器以提高整体预测性能的技术
- **说明**：策略：Bagging（并行，如随机森林）、Boosting（串行，如 XGBoost）、Stacking（堆叠）；降低方差或偏差
- **相关**：Bagging、Boosting、Random Forest（随机森林）

### F1 Score / F1 分数
- **中文**：F1 分数
- **定义**：精确率（Precision）和召回率（Recall）的调和平均数
- **说明**：公式：F1 = 2 * (Precision * Recall) / (Precision + Recall)；在类别不平衡时比准确率更有参考价值
- **相关**：Precision（精确率）、Recall（召回率）、Harmonic Mean（调和平均）

### False Negative (FN) / 假负例
- **中文**：假负例
- **定义**：实际为正类但被模型错误预测为负类的样本
- **说明**：在医学诊断中，假负例意味着漏诊；需要权衡假负例和假正例的成本
- **相关**：False Positive（假正例）、Confusion Matrix（混淆矩阵）、Recall（召回率）

### False Positive (FP) / 假正例
- **中文**：假正例
- **定义**：实际为负类但被模型错误预测为正类的样本
- **说明**：在垃圾邮件检测中，假正例意味着正常邮件被误判为垃圾邮件；影响用户体验
- **相关**：False Negative（假负例）、Confusion Matrix（混淆矩阵）、Precision（精确率）

### Gradient Boosting / 梯度提升
- **中文**：梯度提升
- **定义**：使用梯度下降优化、串行训练决策树以最小化损失函数的集成方法
- **说明**：每棵新树拟合前序模型的负梯度（残差）；代表：XGBoost、LightGBM、CatBoost；在许多竞赛中表现优异
- **相关**：Boosting、XGBoost、Ensemble Learning（集成学习）

### Information Gain / 信息增益
- **中文**：信息增益
- **定义**：使用某个特征划分数据集后熵的减少量，衡量特征的重要性
- **说明**：信息增益越大，特征越重要；ID3 算法使用信息增益选择划分特征；偏向多值特征
- **相关**：Entropy（熵）、Decision Tree（决策树）、Gini Index（基尼指数）

### K-Fold Cross Validation / K 折交叉验证
- **中文**：K 折交叉验证
- **定义**：将数据集分成 K 个子集，每次用 K-1 个子集训练、1 个子集验证，循环 K 次取平均
- **说明**：更充分利用数据；K 常取 5 或 10；减少验证结果的方差；防止因数据划分导致的性能估计偏差
- **相关**：Cross Validation（交叉验证）、Training Set（训练集）、Validation Set（验证集）

### K-Nearest Neighbors (KNN) / K 近邻
- **中文**：K 近邻
- **定义**：基于实例的学习算法，通过查找训练集中与新样本最近的 K 个邻居进行预测
- **说明**：非参数方法，无训练阶段；距离度量：欧氏距离、曼哈顿距离；K 值和距离度量是关键超参数
- **相关**：Distance Metric（距离度量）、Lazy Learning（惰性学习）

### Linear Regression / 线性回归
- **中文**：线性回归
- **定义**：假设输入特征与目标值之间呈线性关系、通过最小化均方误差拟合直线的回归算法
- **说明**：最简单基础的回归方法；可扩展到多元线性回归（多个特征）和多项式回归；易受异常值影响
- **相关**：Regression（回归）、Least Squares（最小二乘法）、Ridge Regression（岭回归）

### Logistic Regression / 逻辑回归
- **中文**：逻辑回归
- **定义**：使用 Sigmoid 函数将线性组合映射到 [0,1] 概率的二分类算法
- **说明**：尽管名为"回归"，实际是分类算法；输出可解释为概率；可扩展到多分类（Softmax Regression）；简单高效
- **相关**：Sigmoid、Classification（分类）、Odds Ratio（优势比）

### Naive Bayes / 朴素贝叶斯
- **中文**：朴素贝叶斯
- **定义**：基于贝叶斯定理、假设特征间条件独立的简单概率分类器
- **说明**："朴素"指特征独立性假设；训练速度快，对高维数据有效；变体：高斯朴素贝叶斯、多项式朴素贝叶斯；常用于文本分类
- **相关**：Bayes' Theorem（贝叶斯定理）、Text Classification（文本分类）

### Precision / 精确率
- **中文**：精确率
- **定义**：预测为正类的样本中真正为正类的比例：TP / (TP + FP)
- **说明**：高精确率意味着少误报；与召回率存在权衡关系；垃圾邮件过滤更关注精确率
- **相关**：Recall（召回率）、F1 Score（F1 分数）、False Positive（假正例）

### Random Forest / 随机森林
- **中文**：随机森林
- **定义**：通过 Bagging 集成多棵决策树、每棵树随机选择特征的集成学习方法
- **说明**：每棵树用自助采样（Bootstrap）训练；最终预测取多数投票（分类）或平均（回归）；抗过拟合能力强
- **相关**：Bagging、Decision Tree（决策树）、Ensemble Learning（集成学习）

### Recall / 召回率
- **中文**：召回率
- **定义**：实际为正类的样本中被正确预测为正类的比例：TP / (TP + FN)
- **说明**：高召回率意味着少漏报；医学诊断中更关注召回率；也叫 Sensitivity（灵敏度）或 True Positive Rate
- **相关**：Precision（精确率）、F1 Score（F1 分数）、False Negative（假负例）

### ROC Curve / ROC 曲线
- **中文**：ROC 曲线
- **定义**：以假正例率（FPR）为横轴、真正例率（TPR）为纵轴绘制的分类器性能曲线
- **说明**：曲线下面积 AUC 衡量模型整体性能；AUC = 0.5 相当于随机猜测，AUC = 1 为完美分类器；不受类别不平衡影响
- **相关**：AUC、True Positive Rate（真正例率）、False Positive Rate（假正例率）

### Support Vector Machine (SVM) / 支持向量机
- **中文**：支持向量机
- **定义**：通过寻找最优超平面最大化类别间隔的线性分类器
- **说明**：核技巧（Kernel Trick）可处理非线性问题；对高维数据有效；支持向量决定决策边界；对异常值敏感
- **相关**：Kernel（核函数）、Margin（间隔）、Classification（分类）

### True Negative (TN) / 真负例
- **中文**：真负例
- **定义**：实际为负类且被模型正确预测为负类的样本
- **说明**：TN 是正确拒绝的样本；与 TP 一起构成正确分类的样本
- **相关**：True Positive（真正例）、Confusion Matrix（混淆矩阵）

### True Positive (TP) / 真正例
- **中文**：真正例
- **定义**：实际为正类且被模型正确预测为正类的样本
- **说明**：TP 是正确识别的正类样本；是召回率和精确率的分子
- **相关**：False Positive（假正例）、Recall（召回率）、Precision（精确率）

---

## 无监督学习

### Autoencoder / 自编码器
- **中文**：自编码器
- **定义**：通过编码器将输入压缩到低维表示、再通过解码器重构输入的神经网络
- **说明**：训练目标是最小化重构误差；用于降维、去噪、特征学习、异常检测；变体：VAE、Denoising Autoencoder
- **相关**：Neural Network（神经网络）、Dimensionality Reduction（降维）、VAE（变分自编码器）

### DBSCAN / 基于密度的空间聚类
- **中文**：基于密度的空间聚类
- **全称**：Density-Based Spatial Clustering of Applications with Noise
- **定义**：基于样本密度、能发现任意形状簇并识别噪声点的聚类算法
- **说明**：参数：邻域半径（eps）、最小点数（minPts）；不需预先指定簇数；对密度不均数据效果可能不佳
- **相关**：Clustering（聚类）、K-Means、Density（密度）

### Gaussian Mixture Model (GMM) / 高斯混合模型
- **中文**：高斯混合模型
- **定义**：假设数据由多个高斯分布混合生成的概率模型
- **说明**：通过 EM 算法估计参数；可进行软聚类（给出属于各簇的概率）；比 K-Means 更灵活
- **相关**：Expectation-Maximization（期望最大化）、Clustering（聚类）、Probability Distribution（概率分布）

### K-Means / K 均值
- **中文**：K 均值
- **定义**：通过迭代更新簇中心、将样本分配到最近中心的聚类算法
- **说明**：步骤：初始化 K 个中心 → 分配样本 → 更新中心 → 重复直到收敛；需预先指定 K；对初始值敏感
- **相关**：Clustering（聚类）、Centroid（质心）、Lloyd's Algorithm

### PCA (Principal Component Analysis) / 主成分分析
- **中文**：主成分分析
- **定义**：通过线性变换将数据投影到方差最大的正交方向上、实现降维的技术
- **说明**：第一主成分方向数据方差最大；去相关性；用于降维、降噪、可视化；是无监督方法
- **相关**：Dimensionality Reduction（降维）、Eigenvalue（特征值）、Eigenvector（特征向量）

---

## 模型评估与调优

### AUC (Area Under Curve) / 曲线下面积
- **中文**：曲线下面积
- **定义**：ROC 曲线下方的面积，衡量二分类模型的整体性能
- **说明**：AUC = 0.5 等价于随机猜测；AUC = 1 为完美分类；AUC 对类别不平衡不敏感；取值范围 [0, 1]
- **相关**：ROC Curve（ROC 曲线）、Classification（分类）

### Accuracy / 准确率
- **中文**：准确率
- **定义**：模型正确预测的样本数占总样本数的比例：(TP + TN) / (TP + TN + FP + FN)
- **说明**：类别不平衡时可能误导；如 99% 负样本时全预测为负也有 99% 准确率；需结合精确率、召回率
- **相关**：Precision（精确率）、Recall（召回率）、Confusion Matrix（混淆矩阵）

### Bagging / 装袋
- **中文**：装袋
- **定义**：通过自助采样（Bootstrap）并行训练多个模型并取平均的集成方法
- **说明**：降低方差，减少过拟合；代表算法：Random Forest（随机森林）；与 Boosting 相对
- **相关**：Boosting、Random Forest（随机森林）、Ensemble Learning（集成学习）

### Bias-Variance Tradeoff / 偏差-方差权衡
- **中文**：偏差-方差权衡
- **定义**：模型复杂度增加会降低偏差但增加方差，需要在两者之间寻找平衡
- **说明**：高偏差导致欠拟合，高方差导致过拟合；目标是找到最优复杂度使总误差最小
- **相关**：Overfitting（过拟合）、Underfitting（欠拟合）、Model Complexity（模型复杂度）

### Early Stopping / 早停
- **中文**：早停
- **定义**：在验证集性能不再提升时提前终止训练以防止过拟合的策略
- **说明**：监控验证损失或指标；连续多个 epoch 无改善则停止；节省训练时间并防止过拟合
- **相关**：Overfitting（过拟合）、Validation Set（验证集）、Patience（耐心值）

### Grid Search / 网格搜索
- **中文**：网格搜索
- **定义**：在预定义的超参数空间中穷举所有组合、通过交叉验证找到最优超参数的方法
- **说明**：简单但计算成本高；超参数多时适用随机搜索（Random Search）或贝叶斯优化
- **相关**：Hyperparameter Tuning（超参数调优）、Cross Validation（交叉验证）

### Hyperparameter Tuning / 超参数调优
- **中文**：超参数调优
- **定义**：寻找最优超参数组合以最大化模型性能的过程
- **说明**：方法：网格搜索、随机搜索、贝叶斯优化、遗传算法；通常使用验证集或交叉验证评估
- **相关**：Hyperparameter（超参数）、Grid Search（网格搜索）、Cross Validation（交叉验证）

### Regularization / 正则化
- **中文**：正则化
- **定义**：在损失函数中添加惩罚项以限制模型复杂度、防止过拟合的技术
- **说明**：L1 正则化（Lasso）：产生稀疏解，用于特征选择；L2 正则化（Ridge）：权重衰减；Elastic Net：L1 + L2 组合
- **相关**：Overfitting（过拟合）、L1/L2 Regularization、Dropout

---

## 经典机器学习概念

### Curse of Dimensionality / 维度灾难
- **中文**：维度灾难
- **定义**：随着特征维度增加，数据变得稀疏、距离度量失效、模型性能下降的现象
- **说明**：高维空间中数据点间距离趋于相似；需要指数级增加数据量；解决方法：降维、特征选择、正则化
- **相关**：Dimensionality Reduction（降维）、Feature Selection（特征选择）

### EM Algorithm / 期望最大化算法
- **中文**：期望最大化算法
- **定义**：用于含有隐变量的概率模型参数估计的迭代优化算法
- **说明**：E 步（Expectation）：计算隐变量的期望；M 步（Maximization）：最大化似然函数更新参数；用于 GMM、隐马尔可夫模型
- **相关**：Maximum Likelihood Estimation（最大似然估计）、GMM、Hidden Markov Model（隐马尔可夫模型）

### Kernel / 核函数
- **中文**：核函数
- **定义**：将低维数据映射到高维特征空间的函数，使线性不可分问题变得可分
- **说明**：常见核函数：线性核、多项式核、RBF（高斯）核、Sigmoid 核；核技巧避免显式计算高维映射
- **相关**：SVM（支持向量机）、Kernel Trick（核技巧）、Feature Space（特征空间）

### Maximum Likelihood Estimation (MLE) / 最大似然估计
- **中文**：最大似然估计
- **定义**：找到使观测数据出现概率最大的模型参数的估计方法
- **说明**：最大化似然函数或等价地最小化负对数似然；统计推断的基础；在逻辑回归、高斯模型中广泛使用
- **相关**：Probability（概率）、Log-Likelihood（对数似然）、Bayesian Estimation（贝叶斯估计）

### Posterior Probability / 后验概率
- **中文**：后验概率
- **定义**：观察到数据后某假设成立的概率 P(H|D)
- **说明**：贝叶斯推断的核心；Posterior ∝ Likelihood × Prior；从先验概率通过数据更新得到
- **相关**：Prior Probability（先验概率）、Likelihood（似然）、Bayes' Theorem（贝叶斯定理）

### Prior Probability / 先验概率
- **中文**：先验概率
- **定义**：在观察到数据之前某假设成立的概率 P(H)
- **说明**：基于经验或领域知识的主观估计；后验概率通过贝叶斯定理结合先验和似然得到
- **相关**：Posterior Probability（后验概率）、Bayesian Inference（贝叶斯推断）
