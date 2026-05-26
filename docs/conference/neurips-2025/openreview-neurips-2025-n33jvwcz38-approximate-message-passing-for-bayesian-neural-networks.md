---
title: Approximate Message Passing for Bayesian Neural Networks
title_zh: 贝叶斯神经网络的近似消息传递方法
authors: "Romeo Sommerfeld, Christian Helms, Jan Niklas Groeneveld, Rainer Schlosser, Ralf Herbrich"
date: 2025-05-09
pdf: "https://openreview.net/pdf?id=n33JVwCz38"
tags: ["query:ai"]
score: 7.0
evidence: 通过消息传递实现贝叶斯神经网络，推进人工智能方法
tldr: 贝叶斯神经网络在不确定性量化方面具有潜力，但现有方法常面临过度自信、后验坍缩等问题。本文提出利用消息传递将贝叶斯神经网络的预测后验建模为因子图，不同于传统方法，该技术能有效缓解上述缺陷。实验表明，新方法在不确定性校准和预测精度上均优于现有贝叶斯神经网络，为可信AI提供了有力工具。
source: NeurIPS-2025-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-n33jvwcz38/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1481, \"height\": 547, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-n33jvwcz38/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1024, \"height\": 618, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-n33jvwcz38/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1442, \"height\": 390, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-n33jvwcz38/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1229, \"height\": 130, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-n33jvwcz38/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1306, \"height\": 1934, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-n33jvwcz38/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1313, \"height\": 1955, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-n33jvwcz38/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1345, \"height\": 1789, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-n33jvwcz38/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1438, \"height\": 429, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-n33jvwcz38/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1311, \"height\": 257, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-n33jvwcz38/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1460, \"height\": 1136, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-n33jvwcz38/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1299, \"height\": 688, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-n33jvwcz38/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1625, \"height\": 2190, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-n33jvwcz38/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1504, \"height\": 1490, \"label\": \"Table\"}]"
motivation: 现有贝叶斯神经网络方法存在过度自信和后验坍缩等局限性。
method: 利用消息传递将预测后验建模为因子图，提出新的近似推理方法。
result: 在不确定性校准和预测精度上优于现有贝叶斯神经网络。
conclusion: 消息传递框架能有效改进贝叶斯神经网络的推理质量。
---

## Abstract
Bayesian methods have the ability to consider model uncertainty within a single framework and provide a powerful tool for decision-making. Bayesian neural networks (BNNs) hold great potential for better uncertainty quantification and data efficiency, making them promising candidates for more trustworthy AI in critical applications, and as backbones in data-constrained settings such as real-world reinforcement learning.  However, current approaches often face limitations such as overconfidence, sensitivity to hyperparameters, and posterior collapse, highlighting the need for alternative approaches. In this paper, we introduce a novel method that leverages message passing (MP) to model the predictive posterior of BNNs as a factor graph. Unlike previous MP-based methods, our framework is the first to support convolutional neural networks (CNNs) while addressing the issue of double-counting training data, which has been a key source of overconfidence in prior work. Multiple open datasets are used to demonstrate the general applicability of the method and to illustrate its differences to existing inference methods.

---

## 论文详细总结（自动生成）

# 论文中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- 贝叶斯神经网络（BNN）能够量化模型不确定性，在关键应用（如医疗、自动驾驶）中提供更可信的 AI。
- 现有 BNN 方法主要分为采样方法（如 HMC）和变分推断（VI，如 Bayes By Backprop、IVON）。但这些方法普遍存在以下问题：
  - 过度自信（overconfidence）
  - 对超参数敏感
  - 后验坍缩（posterior collapse）
  - 计算成本高、难以规模部署
- 消息传递（Message Passing, MP）是另一种概率推断框架，之前的工作（如 Expectation Backpropagation、Probabilistic Backpropagation、Lucibello et al. 2022）存在 **双重计算训练数据（double-counting）** 的缺陷，导致过度自信，并且仅限于小规模 MLP。
- 本文提出 **首个避免 double-counting、支持 CNN 的 MP 框架**，将 BNN 的预测后验建模为因子图，通过近似信念传播计算边际分布。

## 2. 论文提出的方法论：核心思想、关键技术细节

### 核心思想
- 将 BNN 的联合分布（后验）分解为因子图：每个训练样本对应一条网络分支，共享权重变量；新增预测分支用于推断。
- 通过 **高斯密度族**（自然参数 τ, ρ）近似消息，因为高斯在乘法下封闭，且自然参数加法对应高斯乘法。
- 使用 **loopy belief propagation**，通过前向-后向交替传递消息来近似边际。

### 关键技术细节
1. **消息近似**（三大基础因子）：
   - **加权和**：精确计算，消息仍为高斯。
   - **非线性（LeakyReLU/ReLU）**：无法解析，采用 **矩匹配**（moment matching）拟合高斯，分为直接近似和边际近似两种策略。对于 LeakyReLU，推导了闭合形式的矩公式。
   - **乘积**：使用变分消息传递（Stern et al. 2009）打破对称性，组合加权和构成内积消息。

2. **训练流程**：
   - 采用 **小批量（batching）**：一次只更新活跃批次的消息，其他批次的消息被聚合存储在 Trainer 对象中。切换批次时，通过除法去除旧贡献，乘法加入新贡献，严格避免双重计算。
   - 迭代顺序：在一个批次内，对每个样本执行前向-后向传递；所有样本处理完称为一次 "iteration"。逐步增加每个批次的迭代次数以实现精细更新。

3. **预测**：
   - 训练后，将权重后验近似为对角高斯 q̂(θ)，将其作为先验在预测分支前向传播，得到目标 y 的边际。

4. **实现优化**：
   - 层式表示而非逐个标量节点，每个层实例处理整个批次的向量化操作。
   - 使用 Julia 的 CUDA.jl 和 Tullio.jl 进行 GPU 加速。
   - 数值稳定性：自然参数计算、防除零、方差限制、消息阻尼等。

5. **权重先验**：
   - 零中心对角高斯，方差按谱初始化（spectral parametrization）设置，避免方差随深度指数爆炸。但实际仍存在增长，当前选择基于经验。

## 3. 实验设计

### 数据集与场景
| 数据集 | 类型 | 规模 | 用途 |
|-------|------|------|------|
| MNIST | 分类 | 60k 样本 | 不同训练样本量（80 到 60k）下的准确率与校准 |
| CIFAR-10 | 分类 | 50k 训练 | 与 SOTA 优化器对比 |
| UCI 回归（California Housing、Abalone、Wine Quality、Bike Sharing、Forest Fires、Heart Failure、Real Estate Taiwan） | 回归 | 数百到 2 万样本 | 评估泛化与过拟合 |
| 合成数据（sin 函数加噪声） | 回归 | 200 样本 | 深度缩放与不确定性评估 |

### Benchmark 与对比方法
- 分类任务：
  - **SGD**（PyTorch，含 softmax 和回归两种输出）
  - **AdamW**（标准非贝叶斯优化器）
  - **IVON**（SOTA 变分推断方法，Shen et al. 2024）
- 回归任务：
  - 标准 PyTorch 神经网络（两层 MLP，ReLU，weight decay 1e-4）

### 评估指标
- 分类：测试准确率、ECE（期望校准误差）、相对校准 AUC、OOD 检测 AUROC（使用 FashionMNIST 或 SVHN）
- 回归：RMSE（标准化后）、z-score 校准曲线

### 网络架构
- MNIST：3 层 MLP（宽度 64~2000）、LeNet-5
- CIFAR-10：6 层卷积网络（约 890k 参数），无残差连接/归一化
- UCI：2 层 MLP（64-64 神经元）
- 合成：3~5 层 MLP

## 4. 资源与算力

论文未明确给出 GPU 型号、数量、训练总时长等具体数值。仅在 **局限性** 部分指出：
- 训练时间比 AdamW 慢 **两个数量级**，且 GPU 内存消耗更大（因为每个参数需要两个 8 字节浮点数，而 AdamW 可用 4 字节；每条训练样本需存储与参数数量成比例的消息）。
- 本研究使用 Julia 的 CUDA 后端（CUDA.jl + Tullio.jl），但缺乏像 PyTorch 那样的底层优化，且默认使用 FP64 精度拖慢速度。
- 作者强调若采用更高效的消息更新调度（并行批处理）以及用 CUDA C++ 重写核心代码，可大幅降低开销。

## 5. 实验数量与充分性

### 实验数量
- **分类**：MNIST 上对比 MP（R-MP, AM-MP）与 SGD（R-SGD, SM-SGD）共约 8 种数据量的组合（表 1）；CIFAR-10 上 MP 与 AdamW、IVON 对比（表 2）；OOD 检测见图 3c；校准分析见图 3a、3b。
- **回归**：7 个 UCI 数据集（表 4、图 5、图 6），包含学习曲线和校准分布。
- **合成数据**：深度缩放（3/4/5 层）和不确定性覆盖率（100 次随机种子）。
- **消融实验**：无明确消融（如不同消息近似策略、先验方差选择等）。

### 充分性评价
- **客观性**：实验设计规范，对比了当前 SOTA 方法（IVON、AdamW），并公开了代码（https://github.com/neurips-submission-19866/submission）。评估指标全面（准确率、NLL、ECE、Brier、OOD-AUROC、RMSE）。
- **有限性**：
  - 缺乏更大规模数据集（如 ImageNet）或 Transformer 架构的实验。
  - 在 CIFAR-10 上只测试了一种简单卷积网络（无残差、无归一化），且结果略低于 Shen et al. 2024 报告的 ResNet 水平，但作者认为是架构差异所致。
  - 仅使用了 LeakyReLU 激活函数，未验证其他激活。
  - UCI 回归中，部分小数据集（Forest Fires）无论 MP 还是 PyTorch 表现均较差，但作者未深入分析原因。
  - 未报告多次运行的标准差或置信区间（除了合成数据的不确定性实验）。
- **公平性**：超参数选择策略描述清楚（对每种方法固定学习率、batch size 等），但未做全面超参数搜索，可能会使 MP 或基线处于非最优状态。

总体而言，实验覆盖了典型小/中规模任务，验证了方法的核心优势（校准好、抗过拟合），但 **规模不足** 是主要短板。

## 6. 论文的主要结论与发现

1. **MP 方法在小数据量下显著优于 SGD**：MNIST 上仅 640 个样本时，MP 准确率 85.69% vs SGD 58.85%；校准误差 ECE 低一个数量级。
2. **在 CIFAR-10 上可与 SOTA 优化器（AdamW、IVON）竞争**：NLL 和 ECE 甚至更优（NLL 0.997 vs IVON 1.316；ECE 0.029 vs 0.035）。
3. **有效避免过拟合**：在 UCI 回归实验中，MP 的训练和验证误差曲线几乎重合，而 PyTorch 网络严重过拟合（尤其在小数据集）。
4. **不确定性量化良好**：MP 的 z-score 分布接近标准正态（校准好），特别是在 Abalone、California Housing、Real Estate Taiwan 数据集上。
5. **训练效率是主要瓶颈**：内存和速度远落后于非贝叶斯方法，限制了当前在大规模任务上的直接应用。

## 7. 优点：方法或实验设计上的亮点

- **方法创新**：
  - 首次提出同时支持 MLP 和 CNN 的 MP 框架，避免了之前 MP 方法的 double-counting 问题。
  - 推导了加权和、非线性（LeakyReLU）、乘积等基本因子的精确或近似消息方程，具有通用性。
  - 采用批处理策略（aggregate messages）在保持贝叶斯一致性的同时控制内存。
- **实验设计**：
  - 在 MNIST 上系统观察不同训练数据量下的行为，凸显小样本优势。
  - 校准评估充分：不仅使用 ECE，还使用相对校准 AUC、ROC 曲线；在回归中使用 z-score 分布。
  - 对 UCI 回归进行了详细的过拟合分析和校准可视化，直观展示 BNN 的稳健性。
  - 代码开源，便于复现。

## 8. 不足与局限：包括实验覆盖、偏差风险、应用限制

- **计算效率低**：训练时间比 AdamW 慢约 100 倍，GPU 内存消耗大，无法处理大模型或大数据集。
- **架构支持有限**：尚未实现残差连接、层归一化（LayerNorm/BatchNorm），因此无法直接套用 ResNet、Transformer 等现代架构。作者虽提出扩展方向，但未验证。
- **激活函数单一**：仅使用 LeakyReLU，未测试 ReLU、Swish 等；对于 ReLU（α=0）只能使用边际近似，可能影响性能。
- **先验选择依赖经验**：作者承认所推导的先验方差仍导致深度网络方差爆炸，最终采用基于实验的启发式设置，缺乏理论保证。
- **实验规模有限**：最大数据集为 CIFAR-10（50k 样本），未在 ImageNet（1.2M 样本）上测试；模型参数最多约 890k，远小于现代 LLM。
- **缺少消融分析**：未系统比较不同消息近似策略（直接 vs 边际匹配）、不同批处理策略、不同先验设置对结果的影响，难以判断各部分贡献。
- **潜在偏差风险**：UCI 回归的 PyTorch 对比方法仅做了简单 weight decay，未使用早停、dropout 等更强正则化，可能低估了非贝叶斯方法的泛化能力。
- **未报告多次运行统计量**：除了合成数据实验外，未给出准确率的标准差，无法评估方法本身的稳定性。

（完）
