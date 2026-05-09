# 05. 计算机视觉 (Computer Vision)

## 基础概念

### Anchor Box / 锚框
- **中文**：锚框
- **定义**：在目标检测中预定义的一组具有不同尺寸和长宽比的候选框
- **说明**：模型基于锚框预测偏移量和类别；减少搜索空间；YOLO、Faster R-CNN、SSD 使用锚框机制
- **同义词**：Prior Box、Default Box
- **相关**：Object Detection（目标检测）、IoU、Bounding Box（边界框）

### Augmentation / 数据增强
- **中文**：数据增强
- **定义**：通过对图像进行变换（旋转、翻转、裁剪等）扩充训练数据的技术
- **说明**：提高模型泛化能力、防止过拟合；几何变换：旋转、缩放、翻转、裁剪；颜色变换：亮度、对比度、饱和度
- **相关**：Data Augmentation（数据增强）、Training（训练）、Overfitting（过拟合）

### Backbone / 主干网络
- **中文**：主干网络
- **定义**：从输入图像提取特征的卷积神经网络基础架构
- **说明**：常用 Backbone：ResNet、VGG、MobileNet、EfficientNet、Vision Transformer；提供多尺度特征图供后续任务使用
- **相关**：CNN、Feature Extraction（特征提取）、Neck（特征融合层）

### Bounding Box (BBox) / 边界框
- **中文**：边界框
- **定义**：用矩形框标注图像中目标位置的坐标表示
- **说明**：通常表示为 (x, y, width, height) 或 (x1, y1, x2, y2)；是目标检测的基础标注格式
- **相关**：Object Detection（目标检测）、Anchor Box（锚框）、IoU

### Channel / 通道
- **中文**：通道
- **定义**：图像或特征图的一个维度，表示特定类型的信息
- **说明**：RGB 图像有 3 个通道（红、绿、蓝）；特征图通道数逐层增加（如 64、128、256）；每个通道是二维矩阵
- **相关**：CNN、Feature Map（特征图）、RGB

### Classification / 图像分类
- **中文**：图像分类
- **定义**：将输入图像分配到预定义类别的任务
- **说明**：基础 CV 任务；从 AlexNet（2012）到 Vision Transformer（2020）；评估指标：Top-1/Top-5 准确率
- **相关**：CNN、ResNet、ImageNet

### Convolutional Layer / 卷积层
- **中文**：卷积层
- **定义**：使用卷积核提取局部空间特征的神经网络层
- **说明**：核心参数：卷积核大小（如 3×3）、步长（Stride）、填充（Padding）、输出通道数；参数共享减少计算量
- **相关**：CNN、Kernel（卷积核）、Feature Map（特征图）

### Feature Map / 特征图
- **中文**：特征图
- **定义**：卷积层输出的二维或三维数组，表示图像在不同位置的特征响应
- **说明**：浅层特征图提取边缘、纹理；深层特征图提取语义、对象部件；可视化特征图可理解模型关注区域
- **同义词**：Activation Map（激活图）
- **相关**：CNN、Convolutional Layer（卷积层）、Visualization（可视化）

### Feature Pyramid Network (FPN) / 特征金字塔网络
- **中文**：特征金字塔网络
- **定义**：融合多尺度特征以检测不同大小目标的网络结构
- **说明**：自底向上提取特征、自顶向下融合特征并横向连接；在目标检测中广泛使用；如 RetinaNet、Mask R-CNN
- **相关**：Object Detection（目标检测）、Multi-Scale（多尺度）、Backbone（主干网络）

### Grayscale / 灰度
- **中文**：灰度
- **定义**：只有亮度信息、无颜色信息的单通道图像
- **说明**：像素值范围通常为 0（黑）到 255（白）；可通过对 RGB 通道加权平均转换；某些任务（如边缘检测）使用灰度图
- **相关**：RGB、Image Processing（图像处理）、Channel（通道）

### ImageNet / ImageNet
- **中文**：ImageNet
- **定义**：大规模图像识别数据集，包含超过 1400 万张标注图像和 2 万多个类别
- **说明**：ImageNet 挑战赛（ILSVRC）推动深度学习发展；2012 年 AlexNet 在此夺冠开启深度学习时代；是预训练的标准数据集
- **相关**：Dataset（数据集）、Image Classification（图像分类）、Pre-Training（预训练）

### Intersection over Union (IoU) / 交并比
- **中文**：交并比
- **定义**：两个边界框交集面积与并集面积的比值
- **说明**：衡量目标检测框重叠程度；IoU ≥ 0.5 通常视为正样本；是目标检测评估和损失函数的基础
- **相关**：Bounding Box（边界框）、Object Detection（目标检测）、mAP

### Kernel / 卷积核
- **中文**：卷积核
- **定义**：卷积运算中用于提取特征的二维或三维权重矩阵
- **说明**：尺寸通常为 1×1、3×3、5×5；每个卷积核提取一种特征（如边缘、纹理）；1×1 卷积核用于降维和通道融合
- **同义词**：Filter（滤波器）
- **相关**：Convolution（卷积）、CNN、Feature Map（特征图）

### Object Detection / 目标检测
- **中文**：目标检测
- **定义**：在图像中定位并识别所有感兴趣目标的计算机视觉任务
- **说明**：输出：边界框（位置）+ 类别（类别）；两阶段检测器：Faster R-CNN（先提候选框再分类）；单阶段检测器：YOLO、SSD（直接预测）
- **相关**：Bounding Box（边界框）、Classification（分类）、Anchor Box（锚框）

### Pooling Layer / 池化层
- **中文**：池化层
- **定义**：对特征图进行下采样、降低空间尺寸的网络层
- **说明**：最大池化（Max Pooling）取窗口内最大值；平均池化（Average Pooling）取平均值；减少参数量、提供平移不变性
- **相关**：CNN、Downsampling（下采样）、Stride（步长）

### Receptive Field / 感受野
- **中文**：感受野
- **定义**：卷积神经网络中某特征图上的一个点对应输入图像的区域大小
- **说明**：感受野越大，特征包含的全局信息越多；通过堆叠卷积层和池化层扩大感受野；大感受野对理解上下文重要
- **相关**：CNN、Feature Map（特征图）、Dilated Convolution（空洞卷积）

### Region Proposal / 区域提议
- **中文**：区域提议
- **定义**：目标检测中生成可能包含目标的候选区域的方法
- **说明**：传统方法：选择性搜索（Selective Search）；深度学习方法：RPN（Region Proposal Network）；两阶段检测器的第一个阶段
- **相关**：RPN、Object Detection（目标检测）、Faster R-CNN

### RGB / RGB
- **中文**：红绿蓝
- **全称**：Red, Green, Blue
- **定义**：使用红、绿、蓝三个颜色通道表示彩色图像的颜色模型
- **说明**：每个通道 8 位（0-255），三个通道组合可表示约 1670 万种颜色；是数字图像的标准表示
- **相关**：Channel（通道）、Grayscale（灰度）、Color Space（色彩空间）

### Segmentation / 图像分割
- **中文**：图像分割
- **定义**：将图像划分为多个区域或像素级类别的任务
- **说明**：语义分割（Semantic Segmentation）：每个像素分配类别；实例分割（Instance Segmentation）：区分同类不同个体；全景分割：语义+实例
- **相关**：Object Detection（目标检测）、Semantic Segmentation（语义分割）、Mask R-CNN

### Semantic Segmentation / 语义分割
- **中文**：语义分割
- **定义**：将图像中每个像素分配到预定义语义类别的任务
- **说明**：输出与输入同分辨率的分割图；经典网络：FCN、U-Net、DeepLab；应用：自动驾驶、医学影像
- **相关**：Segmentation（图像分割）、Pixel-Level Classification（像素级分类）、U-Net

### Stride / 步长
- **中文**：步长
- **定义**：卷积核在输入上每次滑动的距离
- **说明**：步长越大，输出特征图尺寸越小；Stride=1 保持分辨率，Stride=2 下采样；影响感受野和计算量
- **相关**：Convolution（卷积）、Padding（填充）、Feature Map（特征图）

---

## 目标检测算法

### Faster R-CNN / Faster R-CNN
- **中文**：Faster R-CNN
- **定义**：两阶段目标检测网络，使用 RPN 自动生成候选框
- **说明**：RPN 与检测网络共享特征；端到端训练；精度高但速度较慢；是目标检测的重要里程碑
- **相关**：RPN、R-CNN、Object Detection（目标检测）

### mAP (mean Average Precision) / 平均精度均值
- **中文**：平均精度均值
- **定义**：目标检测中衡量模型性能的核心指标，计算所有类别 AP 的平均值
- **说明**：AP 是 PR 曲线下的面积；mAP@0.5 表示 IoU 阈值为 0.5；mAP@0.5:0.95 表示多阈值平均；值越接近 1 越好
- **相关**：IoU、Precision（精确率）、Recall（召回率）、Object Detection（目标检测）

### NMS (Non-Maximum Suppression) / 非极大值抑制
- **中文**：非极大值抑制
- **定义**：去除目标检测中重叠冗余边界框的算法
- **说明**：保留置信度最高的框，移除与之 IoU 超过阈值的其他框；防止对同一目标重复检测；是目标检测的后处理步骤
- **相关**：IoU、Object Detection（目标检测）、Bounding Box（边界框）

### R-CNN / R-CNN
- **中文**：R-CNN
- **全称**：Regions with Convolutional Neural Networks
- **定义**：使用选择性搜索提取候选区域、再用 CNN 提取特征进行分类的早期两阶段检测器
- **说明**：R-CNN → Fast R-CNN → Faster R-CNN 逐步改进；开创深度学习目标检测先河
- **相关**：Fast R-CNN、Faster R-CNN、Object Detection（目标检测）

### RPN (Region Proposal Network) / 区域提议网络
- **中文**：区域提议网络
- **定义**：Faster R-CNN 中用于自动生成候选区域的子网络
- **说明**：在特征图上滑动小网络预测锚框的类别（前景/背景）和边界框回归；与检测网络共享卷积特征
- **相关**：Faster R-CNN、Region Proposal（区域提议）、Anchor Box（锚框）

### SSD (Single Shot MultiBox Detector) / 单发多框检测器
- **中文**：单发多框检测器
- **定义**：单阶段目标检测网络，在不同尺度的特征图上直接预测类别和位置
- **说明**：比 Faster R-CNN 更快；使用多尺度特征图和默认框（Default Box）；速度与精度的平衡
- **相关**：YOLO、Object Detection（目标检测）、Multi-Scale（多尺度）

### YOLO (You Only Look Once) / YOLO
- **中文**：YOLO
- **定义**：将目标检测视为回归问题、单次前向传播直接预测所有边界框和类别的单阶段检测器
- **说明**：速度极快（实时检测）；YOLOv1/v2/v3/v4/v5/v8 持续改进；v8 支持检测、分割、姿态估计
- **相关**：Object Detection（目标检测）、Real-Time Detection（实时检测）、Single-Stage Detector（单阶段检测器）

---

## 图像生成与高级主题

### GAN / 生成对抗网络
- **中文**：生成对抗网络
- **定义**：由生成器和判别器对抗训练生成逼真图像的模型
- **说明**：CV 中用于图像生成、风格迁移、超分辨率、图像修复；代表：DCGAN、StyleGAN、CycleGAN
- **相关**：Generator（生成器）、Discriminator（判别器）、Style Transfer（风格迁移）

### Image Generation / 图像生成
- **中文**：图像生成
- **定义**：从噪声或文本描述生成新图像的任务
- **说明**：方法：GAN、VAE、Diffusion Model、Autoregressive Model；代表：DALL-E、Stable Diffusion、Midjourney
- **相关**：Generative Model（生成模型）、Diffusion Model（扩散模型）、Text-to-Image（文生图）

### Object Tracking / 目标跟踪
- **中文**：目标跟踪
- **定义**：在视频序列中持续定位并识别特定目标的任务
- **说明**：单目标跟踪（SOT）vs 多目标跟踪（MOT）；挑战：遮挡、形变、光照变化；方法：相关滤波、Siamese 网络、Transformer
- **相关**：Object Detection（目标检测）、Video Analysis（视频分析）

### OCR (Optical Character Recognition) / 光学字符识别
- **中文**：光学字符识别
- **定义**：从图像中自动识别并提取文字的技术
- **说明**：步骤：文本检测（定位文字区域）+ 文本识别（识别字符）；应用：证件识别、文档数字化、车牌识别
- **相关**：Text Detection（文本检测）、Computer Vision（计算机视觉）、NLP

### Pose Estimation / 姿态估计
- **中文**：姿态估计
- **定义**：检测图像或视频中人体关键关节点位置并估计姿态的任务
- **说明**：2D 姿态估计：检测关键点（如 COCO 格式 17 个点）；3D 姿态估计：估计三维空间坐标；应用：动作识别、AR/VR
- **相关**：Keypoint Detection（关键点检测）、Human Pose（人体姿态）

### Style Transfer / 风格迁移
- **中文**：风格迁移
- **定义**：将一幅图像的艺术风格应用到另一幅图像内容上的技术
- **说明**：Gatys 等（2015）首次使用 CNN 实现；分离内容表示和风格表示；快速风格迁移可实时处理
- **相关**：CNN、GAN、Image Generation（图像生成）

### Super-Resolution / 超分辨率
- **中文**：超分辨率
- **定义**：从低分辨率图像重建高分辨率图像的技术
- **说明**：方法：插值、基于重建、基于学习（SRCNN、ESRGAN）；应用：卫星图像、医学影像、视频增强
- **相关**：Image Processing（图像处理）、GAN、CNN

### Transfer Learning / 迁移学习
- **中文**：迁移学习
- **定义**：将在 ImageNet 等大规模数据集上预训练的视觉模型迁移到特定视觉任务的技术
- **说明**：冻结 Backbone 权重、微调顶层；或作为特征提取器；显著减少数据需求和训练时间
- **相关**：Fine-Tuning（微调）、Pre-Trained Model（预训练模型）、Backbone（主干网络）

### ViT (Vision Transformer) / 视觉 Transformer
- **中文**：视觉 Transformer
- **定义**：将 Transformer 架构应用于图像分类、将图像分块作为序列输入的模型
- **说明**：2020 年 Google 提出（"An Image is Worth 16x16 Words"）；在大规模数据上训练可超越 CNN；代表：ViT、Swin Transformer、DeiT
- **相关**：Transformer、Image Classification（图像分类）、Attention Mechanism（注意力机制）
