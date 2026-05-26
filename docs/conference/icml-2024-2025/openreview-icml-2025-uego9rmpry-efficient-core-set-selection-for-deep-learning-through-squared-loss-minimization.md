---
title: Efficient Core-set Selection for Deep Learning Through Squared Loss Minimization
title_zh: 通过平方损失最小化的高效深度学习核心集选择
authors: Jianting Chen
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=UeGo9RmpRY"
tags: ["query:ai"]
score: 7.0
evidence: 通过平方损失最小化进行深度学习核心集选择
tldr: 该论文提出了一种基于平方损失最小化的核心集选择方法MRMC，通过自适应平衡核心样本与非核心样本的损失，识别对收敛贡献最大的样本。引入平衡约束确保子集代表性。在图像分类等多个深度学习任务上，MRMC在保持模型性能的同时显著减少了训练数据量，提高了训练效率。该方法在效率和效果之间取得了良好平衡。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-uego9rmpry/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1668, \"height\": 955, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-uego9rmpry/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 860, \"height\": 736, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-uego9rmpry/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 862, \"height\": 721, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-uego9rmpry/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1733, \"height\": 762, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-uego9rmpry/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 681, \"height\": 240, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-uego9rmpry/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 713, \"height\": 541, \"label\": \"Table\"}]"
motivation: 现有核心集选择方法依赖启发式或复杂优化，效率与效果难以兼顾。
method: 提出MRMC准则，以平方损失最小化为目标，选择使损失最大程度降低的样本。
result: 在多个数据集上，MRMC在减少训练数据的同时维持了模型性能。
conclusion: 基于损失减少的核心集选择为深度学习训练加速提供了有效方案。
---

## Abstract
Core-set selection (CS) for deep learning has become crucial for enhancing training efficiency and understanding datasets by identifying the most informative subsets. However, most existing methods rely on heuristics or complex optimization, struggling to balance efficiency and effectiveness. To address this, we propose a novel CS objective that adaptively balances losses between core-set and non-core-set samples by minimizing the sum of squared losses across all samples. Building on this objective, we introduce the
Maximum Reduction as Maximum Contribution criterion (MRMC), which identifies samples with the maximal reduction in loss as those making the maximal contribution to overall convergence. Additionally, a balance constraint is incorporated to ensure an even distribution of contributions from the core-set. Experimental results demonstrate that MRMC improves training efficiency significantly while preserving model performance with minimal cost.

---

## 论文详细总结（自动生成）

# 详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- 核心问题：深度学习中**核心集选择（Core-set Selection, CS）** 旨在从大规模数据集中挑选最具信息量的子集以加速训练、降低资源消耗。然而，现有方法要么依赖启发式（如基于不确定性、几何多样性），要么使用复杂的双层优化，难以兼顾**效率**（计算成本低）与**效果**（保持模型性能）。
- 研究动机：现有方法存在两个主要矛盾：① **多样性 vs. 不确定性**的平衡难；② **启发式 vs. 原理性**方法的鸿沟——启发式简单但缺乏理论，原理性方法计算昂贵。
- 整体含义：本文试图通过**平方损失最小化**这一简洁目标，自适应地平衡核心集与非核心集的损失，从而提出一种既高效又有理论支撑的CS方法。

## 2. 论文提出的方法论

### 核心思想
- 将CS的目标定义为**最小化全部样本的平方损失之和**：\(\min \sum_{i} (l_i^K)^2\)。平方损失放大高损失样本的惩罚，防止模型过拟合到核心集，促进对非核心集的泛化。
- 在初始损失恒定的假设下，该目标分解为两个成分：**最大化总损失减少**（优化项）和**平衡损失减少**（正则项）。
- 引入**损失减少归因（Loss Reduction Attribution）**：通过泰勒展开和SGD更新近似，单个样本的损失减少可表示为所有训练样本对其梯度内积贡献之和。
- 基于此，提出 **MRMC准则（Maximum Reduction as Maximum Contribution）**：选择**损失减少最大**的样本，因为这些样本对整体收敛贡献最大。
- 为增强多样性，引入**代理正则化（Proxy-based Regularization）**：先选MRMC得分最高的前 \(\rho|C|\) 个样本组成初始子集，再训练一个轻量代理模型（仅输出层），选择与初始子集梯度差异大的剩余样本（用指数损失衡量）。

### 关键技术细节
- **损失减少计算**：对每个样本记录R个epoch的损失序列，拟合成负指数衰减模型 \(l^{(r)}_j \approx q_j \cdot w_j^{-r}\)，从而得到 \(\Delta l_j = q_j(1 - w_j^{-R})\)。
- **正则化得分**：\(\phi_{\text{reg}}(z_i) = \exp(-L(z_i, \theta'))\)，其中 \(\theta'\) 是代理模型参数。
- **最终得分**：\(\phi(z_j) = \phi_{\text{MRMC}}(z_j) - \gamma \cdot \phi_{\text{reg}}(z_j)\)。
- 算法流程：
  1. 在全数据集上训练R个epoch，收集每个样本的损失序列和特征。
  2. 计算MRMC分数。
  3. 若不使用正则化，直接选Top \(|C|\) 样本；若使用，先选Top \(\rho|C|\)，再对剩余样本计算正则化得分并选Top \((1-\rho)|C|\)。

## 3. 实验设计

### 数据集
- CIFAR-10、CIFAR-100、Tiny-ImageNet、ImageNet-1k（规模从10类到1000类递增）。

### 模型
- CIFAR-10/100：ResNet-18（11.2M参数），训练200 epoch。
- Tiny-ImageNet/ImageNet-1k：ResNet-34（21.3M参数），训练100/60 epoch。
- 优化器：SGD，初始学习率0.1，余弦退火，权重衰减依数据集调整。

### 对比方法
- Random、EL2N、GraNd（Paul et al., 2021）、Glister（Killamsetty et al., 2021b）、CCS（Zheng et al., 2023）、Moderate（Xia et al., 2023）、Dyn-Unc（He et al., 2024）、BoundaryCCS（Yang et al., 2024）、D2pruning（Maharana et al., 2024）。

### 评估协议
- **全训练协议**：模型充分训练后选择核心集。
- **早期训练协议**：仅训练R=20 epoch后选择（与MRMC的R一致）。
- 核心集大小：70%、50%、30% 比例（ImageNet-1k额外10%）。
- 评价指标：测试集准确率。大部分实验重复3次取平均。

### 额外实验
- 非核心集损失 vs. 测试准确率的关系可视化。
- 损失减少归因的**稳定性**和**对称性**验证（CIFAR-100上抽取50个样本，计算不同核心集大小下的归因矩阵）。
- 参数敏感性分析：考察初始训练轮数R、正则化子集比例ρ、权衡参数γ对性能的影响。

## 4. 资源与算力

- **文中未明确提及GPU型号和数量**。仅给出训练epoch数（CIFAR-10/100 200 epoch，Tiny-ImageNet 100 epoch，ImageNet-1k 60 epoch）。
- 选择阶段仅需R=20 epoch，代理模型为简单线性层，开销极低。
- 时间成本：在CIFAR-10/100和Tiny-ImageNet上，MRMC在秒级完成选择；在ImageNet-1k上约1分钟；而D2Pruning约6分钟，Boundary因对抗训练需数百秒。
- 结论：方法计算资源需求低，但具体GPU型号未披露。

## 5. 实验数量与充分性

- **实验数量**：共4个数据集，每个数据集3种核心集比例，两种协议，对比近10种基线方法，总计约4×3×2×10=240组实验（含重复）。此外还有消融实验（参数敏感性3个参数各3-4种取值，含两种比例/数据集）、假设验证实验（4种核心集大小下的归因矩阵分析）。
- **充分性**：实验较为全面，覆盖了不同难度、不同规模的数据集，且设置了不同协议（全训练 vs. 早期训练）。但局限性在于：
  - **任务领域单一**：仅限图像分类（CNN模型），未涉及NLP、多模态、更大规模模型（如ViT、LLM）。
  - **假设验证样本量小**：仅用50个样本验证归因的稳定性和对称性，结论的泛化能力存疑。
  - **参数敏感性仅做了部分组合**：没有联合调优所有超参数（如R、ρ、γ同时变化）。
- **公平性**：基线方法均按公开设置复现，但作者提到D2Pruning结果与原论文不一致（可能因训练迭代差异），需注意复现一致性。标签平衡约束未被强制使用，可能影响某些方法的表现。

## 6. 论文的主要结论与发现

- MRMC（及带正则化的MRMC-R）在**早期训练协议**下显著优于多数现有方法，尤其在CIFAR-100、Tiny-ImageNet上表现突出；在CIFAR-10上略逊于CCS但整体最优。
- 在ImageNet-1k上，MRMC在50%和30%比例下优于Random和D2pruning，但MRMC-R因超参数未调优而稍弱。
- 正则化能有效降低非核心集损失并提升准确率，尤其在小核心集比例（30%）时明显；但在复杂任务（CIFAR-100、Tiny-ImageNet）中，单纯降低非核心集损失不一定带来最佳性能，多样性更重要。
- 损失减少归因的**稳定性**随核心集增大而提高（相对误差从27%降至22%）；**对称性**则在训练样本增多时下降（从16%升至24%），表明假设有一定合理性但需进一步改进。
- 参数R对性能影响有限，10-20 epoch即可；ρ越小（0.3）效果越好，γ在2左右较优，但受任务和核心集大小影响。

## 7. 优点

- **理论启发且简洁**：从平方损失最小化出发，推导出直观的MRMC准则，避免了复杂双层优化。
- **高计算效率**：仅需少量初始训练（R=20），选择复杂度近线性，代理模型极轻量。
- **损失减少归因**：首次将样本间贡献归因与核心集选择直接联系，为理解样本交互提供了新视角。
- **内置正则化平衡多样性**：通过代理损失筛选梯度差异大的样本，有效提升子集多样性，且开销可忽略。
- **实验设计较全面**：覆盖多种规模、多种协议、多种基线，参数敏感性分析验证了方法稳健性。

## 8. 不足与局限

- **假设局限性**：初始损失恒定、归因稳定性和对称性假设在极少数样本上验证，且对称性随训练下降，可能不适用于复杂训练过程。若假设不成立，MRMC的理论基础会受影响。
- **超参数依赖性**：正则化部分引入ρ和γ两个新超参数，且最优值随任务和核心集大小变化，无自动调节机制，增加实际使用成本。
- **任务泛化不足**：仅在图像分类（ResNet）上实验，未在NLP、多模态、自监督学习或更大规模模型（如Transformer）上验证，方法通用性存疑。
- **公平性风险**：对比方法未能严格保持相同标签平衡（label balance constraint未被强制执行），可能高估/低估某些方法。此外，D2Pruning复现结果与原论文不一致需谨慎对待。
- **实验统计性**：虽然大多数实验重复3次，但未报告标准差或置信区间，统计显著性不明确。
- **应用限制**：核心集选择后模型训练epoch数固定，未考虑不同核心集大小下最优训练步数的变化（可能导致小核心集欠训练）。

（完）
