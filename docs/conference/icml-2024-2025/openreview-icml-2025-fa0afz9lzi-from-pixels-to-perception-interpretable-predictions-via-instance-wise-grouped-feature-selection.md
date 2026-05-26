---
title: "From Pixels to Perception: Interpretable Predictions via Instance-wise Grouped Feature Selection"
title_zh: 从像素到感知：基于实例分组特征选择的可解释预测
authors: "Moritz Vandenhirtz, Julia E Vogt"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=Fa0aFZ9LZi"
tags: ["query:ai"]
score: 7.0
evidence: 通过实例级分组特征选择实现可解释机器学习
tldr: 该论文提出了一种本质可解释的分类方法，通过对输入图像进行实例级的分组特征选择来产生人类可理解的解释。不同于像素级操作，方法在语义有意义的区域上进行掩码学习，并动态确定每个实例所需的稀疏程度。在半合成和自然图像数据集上的实验表明，该方法生成的解释更符合人类感知，同时保持了分类性能。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-fa0afz9lzi/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 721, \"height\": 242, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fa0afz9lzi/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1587, \"height\": 650, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fa0afz9lzi/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 828, \"height\": 116, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fa0afz9lzi/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1705, \"height\": 550, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fa0afz9lzi/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 836, \"height\": 504, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fa0afz9lzi/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1635, \"height\": 933, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fa0afz9lzi/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1703, \"height\": 545, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fa0afz9lzi/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1709, \"height\": 1023, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fa0afz9lzi/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1607, \"height\": 284, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fa0afz9lzi/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1756, \"height\": 1678, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fa0afz9lzi/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1747, \"height\": 1670, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fa0afz9lzi/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1748, \"height\": 1617, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fa0afz9lzi/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1744, \"height\": 1617, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fa0afz9lzi/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1748, \"height\": 1498, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fa0afz9lzi/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1744, \"height\": 2041, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-fa0afz9lzi/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 865, \"height\": 1718, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fa0afz9lzi/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 850, \"height\": 810, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fa0afz9lzi/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1177, \"height\": 895, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fa0afz9lzi/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1057, \"height\": 1223, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fa0afz9lzi/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1086, \"height\": 293, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fa0afz9lzi/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 981, \"height\": 291, \"label\": \"Table\"}]"
motivation: 现有可解释方法通常依赖像素级操作，解释结果不够语义化。
method: 在语义像素区域上进行实例级掩码学习，动态确定稀疏度以实现可解释分类。
result: 生成的解释在人类感知上更合理，且分类性能无损。
conclusion: 基于分组特征选择的方法为可解释AI提供了更符合人类认知的途径。
---

## Abstract
Understanding the decision-making process of machine learning models provides valuable insights into the task, the data, and the reasons behind a model's failures. In this work, we propose a method that performs inherently interpretable predictions through the instance-wise sparsification of input images. To align the sparsification with human perception, we learn the masking in the space of semantically meaningful pixel regions rather than on pixel-level. Additionally, we introduce an explicit way to dynamically determine the required level of sparsity for each instance. We show empirically on semi-synthetic and natural image datasets that our inherently interpretable classifier produces more meaningful, human-understandable predictions than state-of-the-art benchmarks.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：现有实例级特征选择（Instance-wise Feature Selection）方法主要是在像素级进行掩码，导致出现大量无意义的解（如均匀间隔掩码可保留高精度但缺乏可解释性）。作者认为，为了实现人类可理解的预测，特征稀疏化应在**感知上有意义的语义区域**上进行，而非单个像素。
- **研究动机**：人类感知对象是作为结构单元（部分）而非独立像素。因此，本文提出一种本质可解释的分类方法，通过学习在**语义区域**上的二进制掩码，并动态调整每个实例所需的稀疏度，使解释既忠实于模型又符合人类感知。

## 2. 论文提出的方法论：核心思想、关键技术细节与流程

- **核心思想**：将输入图像过分割（superpixel）为感知原子区域 \( \Omega = \{R_1, \ldots, R_D\} \)，然后学习一个实例级二进制掩码 \( m \in \{0,1\}^D \)，使得只有被选中的区域保留。掩码在区域级别聚合，利用Gumbel-Softmax实现可微采样。模型由两部分组成：选择器（Selector）和分类器（Classifier），共享一个预训练骨干。
- **关键技术细节**：
  - **区域提议**：使用SLIC超像素算法（FastSLIC）快速生成感知区域。论文也证明其他算法（Watershed）不影响性能。
  - **掩码学习**：选择器在像素级预测重要性参数，然后在每个区域内平均，得到区域选择概率 \( p_{m_j} \)。通过Gumbel-Softmax二值化。
  - **稀疏性损失**：定义期望选中的像素比例 \( \bar{p} = \frac{1}{HW}\sum_j p_{m_j} |R_j| \)。损失函数为：
    \[
    L_m = \begin{cases} -\log(1-\bar{p}) & \text{if } \bar{p} > \tau \\ 0 & \text{otherwise} \end{cases}
    \]
    其中 \( \tau \) 为像素级稀疏阈值（训练时从 \(U[0.05,1]\) 随机采样）。该损失只在超过阈值时惩罚，实现显式稀疏控制。
  - **动态阈值**：推理时，逐步增加 \( \tau \) 直到分类器对预测类的置信度达到 \( \delta \)（如0.8~0.99），公式：
    \[
    \tau = \inf\{\tau' \mid \max_c \hat{p}(y_c|x_m) \ge \delta\}
    \]
  - **部分关系建模**：将选择概率参数化为对数正态分布（logit-normal），协方差矩阵由区域嵌入的点积构成（保证半正定）。训练时增加协方差稀疏正则化 \( \lambda_2 \|\Sigma\|_1 \)。
  - **最终损失**：
    \[
    -\log p(y|x_m) - \lambda_1 \mathbf{1}[\bar{p} > \tau] \log(1-\bar{p}) + \lambda_2 \|\Sigma\|_1
    \]

- **流程示意**：输入图像 → 超像素分割 → 选择器预测区域概率 → 采样二值掩码 → 掩码后图像 → 分类器输出。推理时动态调整阈值。

## 3. 实验设计

- **数据集**：
  - 自然图像：CIFAR-10（10类）、ImageNet（1000类）、ImageNet-9（9类，有物体分割标注）、COCO-10（10类，从MS COCO选取，有分割标注）。
  - 半合成：BAM Object 和 BAM Scene（物体插入场景，有干净背景，无捷径特征）。
- **基准方法**：
  - 黑盒（Blackbox）：直接使用原图分类。
  - Blackbox Pixel：等间距像素级掩码（展示无信息掩码仍可保留性能）。
  - DiET、REAL-X、RB-AEM、B-cos、COMET（连续值掩码）、COMET⁻¹（反选掩码）。
- **评价指标**：
  - 性能：分类准确率。
  - 定位：掩码与真实分割的重叠率 \( |m \cap m^*| / |m| \)。
  - 忠实性：插入/删除 fidelity（衡量掩码对预测的重要性）。
- **实现细节**：
  - 选择器：预训练 LR-ASPP MobileNetV3；分类器：预训练 ViT-Tiny。
  - 训练：Adam，lr=1e-4，ImageNet 20 epoch，其他 100 epoch，batch size=64。
  - 超像素：FastSLIC，m=20，100个区域。

## 4. 资源与算力

- **未明确说明**：论文未提及具体的GPU型号、数量或训练总时长。仅提到使用预训练骨干网络（MobileNetV3、ViT-Tiny）并在ImageNet上训练20 epoch、其他数据集100 epoch。因此缺乏可复现的算力细节。但考虑到模型规模不大（ViT-Tiny），推测算力需求适中。

## 5. 实验数量与充分性

- **实验组数**：
  - 主要性能对比：在4个自然图像数据集 + 2个半合成数据集上，每个方法重复10个随机种子，报告均值标准差。
  - 定位实验：在3个有分割标注的数据集（COCO-10, ImageNet-9, BAM）上进行。
  - 忠实性实验：插入/删除 fidelity 图（多个数据集）。
  - 消融实验：
    - 固定阈值 vs 动态阈值（2种设置）。
    - 不同置信度阈值 \(\delta\) 的探索（4个级别）。
    - 不同超像素算法（SLIC vs Watershed）。
    - 与InfoMask的额外对比。
- **充分性与客观性**：
  - 实验覆盖了从简单（CIFAR-10）到复杂（ImageNet）的数据集，以及半合成控制场景。
  - 所有对比方法均在同一骨干和设置下重新训练或微调，公平性较好。
  - 重复10次随机种子降低了偶然性。
  - 定位指标虽然简单，但结合可视化提供了定性佐证。
  - 缺点：部分数据集（如BAM）结果仅在附录中展示，正文仅汇总表。整体实验设计合理，但缺乏更大规模或迁移实验（如ImageNet的完整1000类定位评估未做，因为缺少分割标注）。

## 6. 论文的主要结论与发现

- **性能保持**：P2P在移除高达80%像素的情况下，准确率接近黑盒模型（如CIFAR-10 94.45% vs 95.79%；COCO-10 89.53% vs 89.36%）。
- **定位优越**：在COCO-10和ImageNet-9上，P2P的定位指标显著优于所有基线（分别为47%和69%，第二名COMET为36%和64%）。
- **忠实性**：插入/删除 fidelity 曲线显示P2P的解释最陡峭，即最重要的像素确实驱动预测，而COMET因连续值掩码导致暗像素仍贡献信息，忠实性较低。
- **动态阈值有效**：动态阈值允许不同实例使用不同稀疏度，比固定阈值既能提高性能又能保持定位质量。
- **可视化可解释性强**：掩码聚焦于物体对象，而非随机像素，更符合人类感知。

## 7. 优点

- **语义区域分组**：将掩码提升到超像素水平，避免像素级无意义解，使解释更直观。
- **动态阈值**：根据预测置信度自动调整稀疏度，克服了固定稀疏度不适应难易样本的问题。
- **部分关系建模**：通过协方差矩阵捕捉区域间关系，可为解释提供额外信息（如区域相似性色彩可视化）。
- **忠实性保障**：二值掩码确保了模型只利用选中区域，避免了连续掩码的信息泄漏。
- **与现有方法兼容**：可采用任何超像素算法，且无需真实分割标签。

## 8. 不足与局限

- **超像素依赖**：结果可能受超像素算法的参数（如区域数量、紧凑度）影响，尽管论文做了小规模消融，但对于不同任务可能需要调整。
- **计算开销**：需要运行超像素算法（FastSLIC），且在推理时动态搜索阈值，对实时应用可能增加延迟。
- **实验覆盖有限**：未在更大规模（完整ImageNet定位）或更复杂任务（如语义分割、目标检测）上验证；未与最新结构（如Transformer-based选择器）对比。
- **忠实性度量争议**：插入/删除 fidelity 可能受分布漂移影响，论文通过重新训练分类器缓解，但未与ROAR等更严格标准对比。
- **可解释性深度**：虽然掩码指向物体区域，但未解释区域之间的组合关系（如“猫头+猫身=猫”），仅停留在区域挑选。
- **缺少泛化性分析**：未探讨对对抗样本或分布外数据的鲁棒性。

（完）
