---
title: Improved Algorithm for Deep Active Learning under Imbalance via Optimal Separation
title_zh: 基于最优分离的深度主动学习不平衡改进算法
authors: "Shyam Nuggehalli, Jifan Zhang, Lalit K Jain, Robert D Nowak"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=rm2WHra1fB"
tags: ["query:ai"]
score: 7.0
evidence: 针对类别不平衡的主动学习算法，基于最优分离
tldr: 该论文针对类别不平衡场景下的深度主动学习问题，提出DIRECT算法。通过识别类别分离边界并选择最不确定的样本来标注，将问题转化为一维主动学习，从而有效处理批量标注和标签噪声。实验表明，在多个不平衡数据集上，DIRECT在减少标注成本的同时显著提升了少数类的性能。这是首个全面研究主动学习结合类别不平衡的工作。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-rm2whra1fb/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1696, \"height\": 418, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rm2whra1fb/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 853, \"height\": 300, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rm2whra1fb/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 854, \"height\": 239, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rm2whra1fb/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 717, \"height\": 449, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rm2whra1fb/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1701, \"height\": 1003, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rm2whra1fb/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1706, \"height\": 415, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rm2whra1fb/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1713, \"height\": 453, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rm2whra1fb/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1741, \"height\": 844, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rm2whra1fb/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1712, \"height\": 625, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rm2whra1fb/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1715, \"height\": 627, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rm2whra1fb/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1708, \"height\": 629, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rm2whra1fb/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1708, \"height\": 631, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rm2whra1fb/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1714, \"height\": 625, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rm2whra1fb/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1711, \"height\": 627, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rm2whra1fb/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1711, \"height\": 631, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rm2whra1fb/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1722, \"height\": 635, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rm2whra1fb/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1696, \"height\": 1398, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rm2whra1fb/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1710, \"height\": 627, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rm2whra1fb/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1714, \"height\": 631, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rm2whra1fb/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1710, \"height\": 626, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rm2whra1fb/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1710, \"height\": 628, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rm2whra1fb/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1709, \"height\": 627, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rm2whra1fb/fig-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 1710, \"height\": 625, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rm2whra1fb/fig-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 1711, \"height\": 628, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rm2whra1fb/fig-025.webp\", \"caption\": \"\", \"page\": 0, \"index\": 25, \"width\": 1714, \"height\": 631, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rm2whra1fb/fig-026.webp\", \"caption\": \"\", \"page\": 0, \"index\": 26, \"width\": 848, \"height\": 614, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rm2whra1fb/fig-027.webp\", \"caption\": \"\", \"page\": 0, \"index\": 27, \"width\": 1699, \"height\": 695, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rm2whra1fb/fig-028.webp\", \"caption\": \"\", \"page\": 0, \"index\": 28, \"width\": 820, \"height\": 609, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-rm2whra1fb/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 882, \"height\": 1383, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-rm2whra1fb/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 743, \"height\": 509, \"label\": \"Table\"}]"
motivation: 现有主动学习方法在处理类别不平衡时效果不佳，且难以应对批量标注和标签噪声。
method: 通过识别类别分离边界和选择最不确定样本，将问题转化为一维主动学习。
result: 在多个不平衡数据集上，DIRECT显著提升了少数类的性能并降低了标注成本。
conclusion: DIRECT为不平衡主动学习提供了高效且理论支持的解决方案。
---

## Abstract
Class imbalance severely impacts machine learning performance on minority classes in real-world applications. While various solutions exist, active learning offers a fundamental fix by strategically collecting balanced, informative labeled examples from abundant unlabeled data. We introduce DIRECT, an algorithm that identifies class separation boundaries and selects the most uncertain nearby examples for annotation. By reducing the problem to one-dimensional active learning, DIRECT leverages established theory to handle batch labeling and label noise -- another common challenge in data annotation that particularly affects active learning methods.
Our work presents the first comprehensive study of active learning under both class imbalance and label noise. Extensive experiments on imbalanced datasets show DIRECT reduces annotation costs by over 60\% compared to state-of-the-art active learning methods and over 80\% versus random sampling, while maintaining robustness to label noise.

---

## 论文详细总结（自动生成）

# 论文总结：Improved Algorithm for Deep Active Learning under Imbalance via Optimal Separation

## 1. 核心问题与研究动机

- **问题背景**：实际应用中的深度模型常面临严重的**类别不平衡**（minority class 样本极少）和**标签噪声**（标注错误）两大挑战。主动学习通过策略性地从未标注数据中选取信息量大的样本，有望从根本上改善不平衡问题，但现有主动学习方法在极端不平衡和噪声共存的场景下效果很差。
- **现有方法局限**：
  - 传统不确定性采样（如 margin 采样）倾向于在决策边界附近采样，但由于少数类样本本身稀少，边界附近多数为多数类，导致标注仍不平衡。
  - 最新算法 GALAXY 通过图二分法识别所有“切割点”（cut），但会因模型训练不足或标签噪声引入大量虚假切割，浪费标注预算，且仅支持顺序标注（batch size = 1），无法并行。
  - 尚无工作系统研究 **类别不平衡 + 标签噪声** 这一现实场景下的深度主动学习。

## 2. 方法论：DIRECT 算法

### 2.1 核心思想
- 将**多类不平衡分类**问题分解为 **K 个一维的 agnostic active learning 问题**（each class vs. rest）。
- 对于每个类 k，利用当前神经网络的 margin 得分对未标注样本排序，将问题转化为寻找最优分离阈值 \( j^\star \)，该阈值能在两侧最好地分离少数类与多数类。
- 然后专注于标注靠近该阈值的样本——这些样本既**类别平衡**又**具有不确定性**。
- 利用**版本空间缩减（VReduce）** 框架（源自 agnostic active learning 理论），在存在标签噪声时仍能鲁棒地逼近最优阈值，并且支持批量并行标注（batch size 可调）。

### 2.2 关键技术细节
- **1D 约简**：对每个类 k，定义假设集 \( \mathcal{H} = \{ h_0, \dots, h_N \} \)，其中 \( h_j \) 将排序后前 j 个样本判为类 k，其余判为非 k。最优阈值 \( j^\star \) 等价于最小化经验零一损失的假设，即 \( j^\star = \arg\min_j L(h_j) \)，且与“最大化两侧类别标签差异”等价（见 Lemma A.1）。
- **VReduce 算法**（Algorithm 1）：
  1. 维护版本空间区间 [I, J]：所有已标注样本在 I 左侧均为类 k，在 J 右侧均为非 k。
  2. 迭代地在该区间内均匀采样未标注样本（每次批量大小 \( B_{\text{parallel}} \)），更新标签。
  3. 根据经验损失估计收缩区间：计算每个候选间隔内左右两侧的累计错误，选择使最大错误最小的候选间隔，并以因子 c 缩小版本空间。
  4. 理论保证：基于 ACED 框架，误识别阈值的概率随预算指数衰减。
- **DIRECT 算法**（Algorithm 2）：
  - 每轮分为两阶段：
    1. **识别阶段**：对每个类 k，调用 VReduce 标注 \( B_{\text{train}}/(2K) \) 个样本。
    2. **标注阶段**：基于当前版本空间估计各阈值 \( \hat{j}_k \)，再为每个类标注靠近阈值的 \( B_{\text{train}}/(2K) \) 个样本（剩余预算）。
  - 并行性：通过参数 \( B_{\text{parallel}} \) 指定单次请求的并行标注数，算法自然支持批量。

### 2.3 与 GALAXY 的理论对比
- 论文证明：在标签噪声率为 η 时，GALAXY 以至少 \( 1 - \exp(-b \log(1/(1-\eta))/2) \) 的概率找到至少一个额外切割点（Theorem B.1），即浪费大量预算；而 DIRECT 基于 agnostic active learning 理论，误识别概率随预算指数衰减，从而聚焦于真正的最优阈值。

## 3. 实验设计

### 3.1 数据集与场景
- **ResNet-18 实验**：使用 CIFAR-10、CIFAR-100、SVHN、PathMNIST 构建的极不平衡版本（如两/三/十类，不平衡比 0.0049~0.2546），还使用了标准的 CIFAR-10LT、CIFAR-100LT。
- **LabelBench 实验**（大规模预训练模型 + 半监督）：使用 FMoW（62 类）、iWildCam（14 类）、ImageNet-LT、iNaturalist（不平衡比低至 \( 4.57\times10^{-5} \)）。
- **噪声设置**：引入 0%、10%、15%、20% 的均匀随机标签噪声（i.i.d. flip）。

### 3.2 对比基线
- **ResNet-18**：Random、BADGE、BASe、BAIT、Cluster Margin、Confidence Sampling、Margin Sampling、Most Likely Positive、SIMILAR、GALAXY、DIRECT（Bparallel = 1 或 5）。
- **LabelBench**：Random、BADGE、Margin Sampling、CORESET、GALAXY、DIRECT（Bparallel = 20）。
- **训练细节**：所有方法均使用重加权交叉熵损失（逆频率）补偿不平衡，噪声实验额外使用 10% 标签平滑。ResNet-18 采用 Adam 优化器，LabelBench 采用 CLIP ViT-B32 微调 + FlexMatch 半监督（但噪声下改用纯监督训练）。

### 3.3 评估指标
- **平衡准确率（Balanced Accuracy）**：所有类别的平均召回率，对不平衡更鲁棒。
- 同时报告了标注的少数类样本数量。

## 4. 资源与算力

- 论文未提供详细的 GPU 型号、数量或精确训练时长。仅提及：
  - ResNet-18 实验每轮在 NVIDIA 3090 Ti GPU 上运行，单次试验（trial）不超过 **2 小时**。
  - LabelBench 实验单次试验约 **12 小时**。
  - 所有实验均在有限的 GPU 资源下完成（无大规模分布式训练说明）。

## 5. 实验数量与充分性

- **实验规模**：覆盖 **12 种数据集设置**（包括不同类别数、不同不平衡度）、**4 种标签噪声水平**（0%/10%/15%/20%）、**两种模型架构**（ResNet-18 和 CLIP ViT-B32）。
- **重复次数**：每个设置至少 **4 次随机试验**，结果报告均值和标准误差（以阴影表示），具备统计可靠性。
- **消融分析**：对比了不同并行批大小（Bparallel = 1 vs 5 vs 20）；展示了不同噪声水平下的性能退化趋势；定性分析了各类别准确率分布（ImageNet-LT 按类频率分组）。
- **公平性**：所有方法共享相同的训练设置（优化器、数据增强、标签平滑等），且训练超参数经过统一调整。但论文未提及是否对基线方法做了特别的超参数调优（如 learning rate、batch size 等），仅说明使用了标准做法。

## 6. 主要结论与发现

1. **DIRECT 显著优于所有基线**：在无噪声和存在噪声的场景下，DIRECT 均达到最高的平衡准确率。相比最佳基线，可节省 **超过 60% 的标注成本**；相比随机采样，节省 **超过 80%**。
2. **对标签噪声鲁棒**：在 10%~20% 噪声下，DIRECT 依然大幅优于 GALAXY 和其他方法，而 GALAXY 甚至可能劣于随机采样（图 1b）。
3. **支持批量并行标注**：Bparallel 从 1 增加到 5 或 20 时，DIRECT 的性能下降很小，而 GALAXY 仅支持同步（Bparallel=1）。
4. **平衡性和信息性之间的权衡**：尽管 “Most Likely Positive” 和 “SIMILAR” 标注了更多少数类样本，但准确率不如 DIRECT，表明单纯增加少数类样本量并非最优，还需要选择信息量大的样本。
5. **理论优势**：DIRECT 继承了 agnostic active learning 的指数级误识别上界，避免了 GALAXY 因标签噪声产生额外切割点的问题。

## 7. 优点

- **问题新颖**：首次系统研究 “类别不平衡 + 标签噪声” 这一实际常见组合场景。
- **理论联系实践**：巧妙地将深度主动学习问题约简到一维 agnostic 分类，从理论文献中吸取鲁棒算法并适配到深度模型，兼具理论保障和实证效果。
- **并行性**：突破了 GALAXY 的同步限制，适应实际多标注员场景，且性能损失小。
- **实验全面**：涵盖多种不平衡度、噪声水平、模型架构，并做了定性分析，结果可信度高。
- **开源实现**：代码集成在 LabelBench 框架中，便于复现和进一步研究。

## 8. 不足与局限

- **模型与数据范围**：仅测试了计算机视觉任务（CIFAR, SVHN, PathMNIST, FMoW, iWildcam 等），未涉及 NLP 或表格数据等模态，泛化性未验证。
- **噪声模型**：仅假设均匀随机噪声（i.i.d. flip），未考虑异方差噪声（不同样本区域噪声不同）或 annotator 依赖，虽提到与 Khosla et al. (2022) 的不同，但未对比。
- **超参数敏感性**：未系统分析 VReduce 中的收缩因子 c、预算分配比例（识别 vs 标注各半）等对结果的影响；未报告基线的超参数调优细节，可能存在不公平比较风险。
- **计算开销**：虽然指出时间复杂度低于 BADGE 和 GALAXY，但未提供实际运行时间对比表；大模型（CLIP）实验单次 12 小时，对于更大规模场景可能仍较高。
- **理论边界**：虽然给出了 GALAXY 的额外切割概率上界，但未提供 DIRECT 的有限样本误差下界或收敛率（仅引用了 ACED 的指数界，未在文中重新表述）。
- **应用限制**：需要每轮训练神经网络以更新 margin 分数，对于极快速迭代的场景（如实时标注）可能不适用；未讨论冷启动阶段（初始极少量标注）的效果。

（完）
