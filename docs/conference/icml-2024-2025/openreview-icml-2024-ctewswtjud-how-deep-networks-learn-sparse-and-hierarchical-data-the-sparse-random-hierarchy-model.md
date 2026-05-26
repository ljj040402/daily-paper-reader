---
title: "How Deep Networks Learn Sparse and Hierarchical Data: the Sparse Random Hierarchy Model"
title_zh: 深度网络如何学习稀疏和层次数据：稀疏随机层次模型
authors: "Umberto Maria Tomasini, Matthieu Wyart"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=CtEWswTjUd"
tags: ["query:ai-basics"]
score: 6.0
evidence: 研究深度网络学习机制，与深度学习基础相关
tldr: 该论文提出稀疏随机层次模型，统一了深度网络对不变性和层次表示的学习观点。通过引入稀疏性到生成层次模型，解释了深度网络为何能学习高维数据中的结构。研究揭示了数据稀疏性和层次结构在深度学习成功中的关键作用，为理解深度学习基础提供了理论视角。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-ctewswtjud/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1786, \"height\": 861, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ctewswtjud/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1614, \"height\": 1139, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ctewswtjud/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 898, \"height\": 823, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ctewswtjud/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1774, \"height\": 645, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ctewswtjud/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 710, \"height\": 578, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ctewswtjud/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1260, \"height\": 1076, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ctewswtjud/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1175, \"height\": 607, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ctewswtjud/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1164, \"height\": 600, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ctewswtjud/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1768, \"height\": 1020, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ctewswtjud/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1206, \"height\": 653, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ctewswtjud/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1235, \"height\": 603, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ctewswtjud/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1761, \"height\": 1358, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ctewswtjud/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 642, \"height\": 649, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ctewswtjud/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1238, \"height\": 1240, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ctewswtjud/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1760, \"height\": 1371, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ctewswtjud/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1143, \"height\": 563, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-ctewswtjud/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1157, \"height\": 1139, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-ctewswtjud/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1233, \"height\": 463, \"label\": \"Table\"}]"
motivation: 理解深度网络学习高维数据的根本原因，统一不变性和表示学习。
method: 提出稀疏随机层次模型，通过理论分析揭示数据稀疏性和层次结构的作用。
result: 模型成功解释了深度网络的学习行为，提供了理论支撑。
conclusion: 数据稀疏性和层次结构是深度学习成功的关键因素。
---

## Abstract
Understanding what makes high-dimensional data learnable is a fundamental question in machine learning. On the one hand, it is believed that the success of deep learning lies in its ability to build a hierarchy of representations that become increasingly more abstract with depth, going from simple features like edges to more complex concepts. On the other hand, learning to be insensitive to invariances of the task, such as smooth transformations for image datasets, has been argued to be important for deep networks and it strongly correlates with their performance. In this work, we aim to explain this correlation and unify these two viewpoints. We show that by introducing sparsity to generative hierarchical models of data, the task acquires insensitivity to spatial transformations that are discrete versions of smooth transformations. In particular, we introduce the Sparse Random Hierarchy Model (SRHM), where we observe and rationalize that a hierarchical representation mirroring the hierarchical model is learnt precisely when such insensitivity is learnt, thereby explaining the strong correlation between the latter and performance. Moreover, we quantify how the sample complexity of CNNs learning the SRHM depends on both the sparsity and hierarchical structure of the task.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义
- **研究动机**：深度神经网络在高维数据（如图像、文本）上表现优异，但理论上学习通用任务需要指数级样本。理解数据的结构是破解这一谜题的关键。已有两种主流视角：①深度网络通过构建层次化的抽象表示（从边缘到概念）来学习；②任务对平滑变换（如微分同胚）的不敏感性与网络性能高度相关。然而，这两种视角之间的内在联系尚不明确。
- **核心问题**：为何深度网络对平滑变换的敏感性与测试误差存在强相关？层次表示的学习与不变性的习得是否是同一过程？
- **整体含义**：论文通过引入**稀疏随机层次模型**，统一了上述两种视角。论证了数据中的空间稀疏性天然赋予了任务对离散光滑变换的不敏感性，并进一步发现：层次表示与对变换的不敏感性是在相同训练数据量下同时习得的，从而解释了二者的强相关性。

## 2. 方法论
- **核心思想**：在随机层次生成模型（RHM）的基础上引入**空间稀疏性**——每个生产规则包含 \( s \) 个信息特征和 \( s_0 \) 个无信息特征（空像素）。这种稀疏性使得输入中信息特征的位置可以发生位移而不改变类别，相当于离散版本的微分同胚变换。模型称为**稀疏随机层次模型**。
- **关键技术细节**：
  - 生成过程：从类别标签出发，通过 \( L \) 层随机生产规则生成输入。每层规则将高层特征映射为 \( s \) 个低层特征，其中每个信息特征嵌入在大小为 \( s_0+1 \) 的子块中（即周围有 \( s_0 \) 个空元素），形成总维度 \( d = (s(s_0+1))^L \) 的稀疏输入。
  - 两种稀疏方式（如图2）：A）信息特征在子块内固定相对位置；B）信息特征可任意排列但顺序不变。论文主要分析方式A，并证明B具有相同样本复杂度。
  - 网络架构：主要使用局部连接网络（LCN，无权重共享）和卷积神经网络（CNN）作为理论分析对象，并扩展到常见架构（VGG、ResNet、EfficientNet等）。
  - 定义两个关键敏感性指标：
    - 同义词交换敏感性 \( S_k \)：衡量网络内部层 \( k \) 对替换同义词的响应变化。
    - 微分同胚敏感性 \( D_k \)：衡量对随机位移信息特征（保持特征值不变）的响应变化。
  - 样本复杂度提取：固定测试误差阈值（如10%），记录所需最小训练样本数 \( P^* \)。
- **公式（文字说明）**：
  - LCN的样本复杂度：\( P^*_{\text{LCN}} \sim C_0(s,L) (s_0+1)^L n_c m^L \)，其中 \( C_0 \sim s^{L/2} \)。
  - CNN的样本复杂度：\( P^*_{\text{CNN}} \sim C_1 (s_0+1)^2 n_c m^L \)。
  - 这说明两种网络都能以多项式级样本复杂度（相对于指数级维度）学习任务，而权重共享使CNN对稀疏性的依赖更弱（仅平方项而非指数项）。

## 3. 实验设计
- **数据**：使用SRHM合成数据，输入维度 \( d = (s(s_0+1))^L \)，每个信息特征用 one-hot 编码（维度 \( v \)），类别数 \( n_c = v \)，同义词数 \( m = v^{s-1} \)（最大化情况）。生成不同参数组合的大量训练集。
- **Benchmark**：没有外部真实数据集，而是以合成SRHM为基准任务。对比方法主要是不同网络架构（LCN、CNN、FCN）以及常见架构（VGG11/16、ResNet18/34、EfficientNetB0）。
- **对比与观测**：
  - 改变参数 \( s, s_0, v, L \)、训练样本数 \( P \)，记录测试误差和敏感性。
  - 提取样本复杂度，验证理论预测。
  - 分析内部层敏感性随训练集大小的变化，检验层次表示与不变性的同步性。
  - 消融实验：比较稀疏方式A和B，确认样本复杂度一致；比较不同网络类型（LCN vs CNN vs FCN），验证结论的普适性。

## 4. 资源与算力
- 文中**未明确说明**使用的GPU型号、数量或总训练时长。仅提到优化器为SGD（batch size=4，momentum=0.9），学习率通过网格搜索确定（LCN: 0.01或0.003；CNN: 0.01或0.003），训练停止条件为交叉熵损失降至10^{-3}或10^{-2}。
- 实验参数范围较广（多种\( s, s_0, v, L \)组合），但未披露具体计算资源消耗，可能相对适中（合成数据维度有限、网络规模较小）。

## 5. 实验数量与充分性
- **实验数量**：论文进行了大量系统性实验，包括：
  - 改变 \( s \)（2,3）、\( s_0 \)（0,1,2,4,6）、\( v \)（4,6,8,10）、\( L \)（2,3）。
  - 对比网络：LCN、CNN、FCN，以及5种常见架构（VGG11、VGG16、ResNet18、ResNet34、EfficientNetB0）。
  - 对每种参数组合，测量样本复杂度、敏感性，并验证理论公式。
  - 在附录中展示了多种消融实验（如稀疏方式A vs B、不同深度、不同同义词组合）。
- **充分性与公平性**：
  - 实验覆盖了理论预测的主要依赖参数，结果与公式高度吻合，具有较强说服力。
  - 但所有实验均使用合成数据，缺乏在真实图像数据集（如CIFAR-10、ImageNet）上的直接验证（尽管论文指出CIFAR-10上已有类似关联现象，但未在同一框架下进行定量比较）。
  - 常见架构的训练过程未详细与LCN/CNN标准化（如学习率、通道数、正则化等），存在一定公平性争议，但作者在附录中给出了部分细节。

## 6. 主要结论与发现
- **层次表示与不变性同时学习**：同义词交换敏感性和微分同胚敏感性在相同的训练样本量 \( P^* \) 处大幅下降，恰好是测试误差显著降低的时刻。这一现象在LCN、CNN、FCN以及常见架构中均成立。
- **样本复杂度公式**：LCN的样本复杂度与 \( (s_0+1)^L \) 成正比，CNN的样本复杂度与 \( (s_0+1)^2 \) 成正比（权重共享降低了维度依赖）。两种网络均能多项式级样本复杂度“击败维度诅咒”。
- **稀疏性的收益**：在固定输入维度 \( d \) 下，更大稀疏性（更小的相关分数 \( F \)）使任务更容易（样本复杂度更低）。
- **统一理论**：SRHM成功复现了CIFAR-10上测试误差与微分同胚敏感性的强相关性，为理解深度学习的成功提供了理论框架。

## 7. 优点
- **理论贡献突出**：首次将层次模型与对光滑变换的不变性有机结合，统一了两种长期独立的研究视角，提供了可解释的机制。
- **实验设计细致**：系统性地改变了多个参数，验证了样本复杂度的精确标度律，且结论在多种网络结构上一致，增强了泛化性。
- **方法新颖**：通过引入稀疏性这一简单概念，自然导出了不变性，避免了预先编码特定不变性的需要，更符合实际数据（如图像中的背景/冗余像素）。
- **量化清晰**：给出了样本复杂度的显式表达式，有助于解释深度学习中的标度律和迁移学习等现象。

## 8. 不足与局限
- **缺乏真实数据集验证**：所有实验基于合成数据SRHM，未在真实图像（如CIFAR-10、ImageNet）上直接测试“同义词不敏感性”（因为真实数据中缺乏明确定义的同义词），限制了结论的直接迁移。作者也承认这一点。
- **模型假设较强**：SRHM假设严格的分层结构、随机生产规则、最大化同义词数等，真实数据可能更为复杂（如层级不严格、特征间有噪声干扰）。
- **训练细节不完整**：不同网络架构的优化超参数未统一标准化（如VGG等使用了不同的学习率和正则化），可能影响样本复杂度的可比性。
- **计算资源未报告**：缺乏对训练时间和硬件的明确说明，不利于可复现性评估。
- **实际应用局限性**：论文主要关注分类任务，未探讨在生成模型、语言模型等其他场景下的适用性。

（完）
