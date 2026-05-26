---
title: A Bayesian Model Selection Criterion for Selecting Pretraining Checkpoints
title_zh: 一种用于选择预训练检查点的贝叶斯模型选择准则
authors: "Michael Munn, Susan Wei"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=fEjktWQ5Am"
tags: ["query:ai"]
score: 6.0
evidence: 预训练检查点选择
tldr: 该论文提出一种贝叶斯模型选择准则——下游自由能，用于选择最适合下游任务适配的预训练检查点。该准则通过度量检查点附近有利参数的集中程度量化适应性。在多种基础模型上的实验表明，下游自由能可以有效预测并选择出更优的预训练检查点，从而提高微调效率。这一方法对于理解和优化预训练-微调范式具有实际指导意义。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-fejktwq5am/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 653, \"height\": 1002, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fejktwq5am/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1775, \"height\": 930, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fejktwq5am/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1775, \"height\": 936, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-fejktwq5am/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 848, \"height\": 239, \"label\": \"Table\"}]"
motivation: 预训练检查点的选择对下游任务性能影响大，但缺乏有效的选择标准。
method: 定义下游自由能作为贝叶斯准则，通过参数空间浓度评估检查点适应性。
result: 该方法在多个基础模型和任务上成功选择了更优的检查点，提升了微调效果。
conclusion: 下游自由能是一种有效的预训练检查点选择准则，可指导模型部署与迁移学习。
---

## Abstract
Recent advances in artificial intelligence have been fueled by the development of foundation models such as BERT, GPT, T5, and Vision
Transformers. These models are first pretrained on vast and diverse datasets and then adapted to specific downstream tasks, often with significantly less data. However, the mechanisms behind the success of this ubiquitous pretrain-then-adapt paradigm remain underexplored, particularly the characteristics of pretraining checkpoints that enhance downstream adaptation. We introduce a Bayesian model selection criterion, called the downstream free energy, which quantifies a checkpoint’s adaptability by measuring the concentration of nearby favorable parameters for a downstream task. We demonstrate that this Bayesian model selection criterion can be effectively implemented without access to the downstream data or prior knowledge of the downstream task. Furthermore, we provide empirical evidence that the criterion reliably correlates with improved fine-tuning performance, offering a principled approach to predicting model adaptability.

---

## 论文详细总结（自动生成）

# 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：在“预训练-微调”范式中，如何选择最优的预训练检查点（checkpoint），使其在下游任务上具有最佳的适应能力。现有方法多依赖经验启发式（如跟踪预训练损失），缺乏理论支撑。
- **研究动机**：预训练模型（如BERT、GPT、T5、Vision Transformers）在大规模数据上训练后，需要针对特定下游任务进行微调。然而，预训练过程中不同检查点的适应性差异显著，选择不当会导致微调性能下降。现有理论（如神经坍缩、几何复杂度）虽提供了一些解释，但尚未形成统一的、可实际部署的准则。
- **整体含义**：该论文旨在从贝叶斯模型选择的角度，引入“下游自由能”作为量化检查点适应性的准则，并证明其可通过仅使用预训练数据计算的“预训练自由能”进行有效代理，从而为检查点选择提供理论基础和实用方法。

# 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程（用文字说明即可）

- **核心思想**：一个好的预训练检查点应在其参数空间附近存在大量对下游任务表现良好的参数（即低下游损失参数的高浓度）。该浓度可通过“下游自由能”（负对数局部边际似然）衡量：下游自由能越低，表示该检查点附近有利参数越集中，适应性越强。
- **关键技术细节**：
    1. **下游自由能定义**：对于预训练检查点 \(w^* = (v^*, \theta^*)\)，定义其γ-邻域 \(B_\gamma(w^*)\) 内的局部边际似然：
       \[
       \bar{Z}_1(B_\gamma(w^*)) = \int_{B_\gamma(w^*)} \exp\{-m K_1(w)\} \phi(w) dw
       \]
       其中 \(K_1(w)\) 是下游测试损失，\(m\) 是下游样本量。下游自由能 \(\bar{F}_1 = -\log \bar{Z}_1\)。
    2. **渐近展开**：\(\bar{F}_1(B_\gamma(w^*)) = m K_1(w_1^*) + \lambda_1(w^*) \log m + O(\log \log m)\)，其中 \(\lambda_1\) 是局部学习系数（复杂度度量）。这意味着选择低下游自由能的检查点等价于平衡“拟合度”和“复杂度”。
    3. **预训练自由能作为代理**：定义预训练自由能 \(F_0(B_\gamma(w^*); \beta) = -\log Z_0\)，其中 \(Z_0\) 基于预训练数据。关键命题（Proposition 5.1）在分布漂移有界条件下，证明下游自由能受预训练自由能控制：
       \[
       K_1(w_1^*) + \frac{\lambda_1 \log m}{m} \leq M K_0(w^*) + D + \frac{\lambda_0 \log m}{m}
       \]
       因此最小化预训练自由能可有效代理最小化下游自由能。
    4. **估计方法**：使用局部化广泛适用贝叶斯信息准则（WBIC），通过随机梯度Langevin动力学（SGLD）在检查点邻域内采样，计算期望预训练损失和复杂度项，从而得到预训练自由能的渐近无偏估计。
- **算法流程**：训练过程中定期计算每个检查点的预训练WBIC，选择WBIC最低的检查点进行后续微调。

# 3. 实验设计：使用了哪些数据集 / 场景，它的 benchmark 是什么，对比了哪些方法

- **数据集**：
    - CIFAR-FS（CIFAR-100的少量样本划分）：64类用于预训练，20类用于下游测试，并构建5-shot 5类任务评估小样本场景。
    - mini-ImageNet：同样划分为元训练和元测试集，用于验证泛化性。
- **场景**：
    - 全元测试集微调（full meta-test fine-tuning）：使用下游数据集的全部训练样本进行微调。
    - 少样本微调（few-shot fine-tuning）：5-shot 5类任务的多次平均准确率。
- **基准与对比方法**：
    - 对比的预训练指标：几何复杂度（Geometric Complexity）、神经坍缩（Neural Collapse）、预训练自由能（Free Energy）。
    - 对比方式：计算各指标与下游微调准确率的皮尔逊相关系数。
    - baseline：预训练训练损失（图2第一列显示其失效，因训练后期损失值趋于一致）。

# 4. 资源与算力：如果文中有提到，请总结使用了多少算力（GPU 型号、数量、训练时长等）。若未明确说明，也请指出这一点

- 论文中**未明确说明**所使用的GPU型号、数量及具体训练时长。仅在方法部分提到使用SGLD计算WBIC时，设置了步长、链长等超参数（如步长2e-7，链长3000或1000次迭代，batch size 2048或1024），但未提供硬件配置和总耗时。因此无法量化算力消耗。

# 5. 实验数量与充分性：大概做了多少组实验（如不同数据集、消融实验等），这些实验是否充分、是否客观、公平

- **实验组数**：
    - 主要实验（图2）：在CIFAR-FS上分别对学习率（5个值）、批大小（6个值）、动量（5个值）进行超参数扫描，每个配置使用5个随机种子，共计约85个检查点。
    - 补充实验（图3）：在mini-ImageNet上类似扫描，学习率3个值、批大小6个值、动量4个值。
    - 相关性分析（表1）：基于CIFAR-FS上所有85个检查点，计算三种指标与两种微调准确率的皮尔逊相关系数。
    - 消融实验：未单独设计消融实验，但通过改变超参数观察WBIC与性能的单调关系，间接验证了方法机制。
- **充分性与公平性**：
    - **优点**：覆盖了多个数据集（CIFAR-FS、mini-ImageNet）、多种架构（ResNet-18、VGG-16）、多种超参数和两种微调场景（全量、少样本），实验范围较广。使用5个随机种子保证统计稳定性。
    - **不足**：未对比除超参数扫描以外的其他检查点选择策略（如基于验证集损失、sharpness-aware选择等）；未在更大尺度的模型（如GPT、ViT）上验证，仅使用了小型模型（ResNet-18, VGG-16）。因此泛化性可能受限。

# 6. 论文的主要结论与发现

- **主要发现**：
    - 预训练自由能（由WBIC估计）与下游微调准确率呈强负相关：低预训练自由能对应高微调性能（图1、2、3）。
    - 相较于几何复杂度和神经坍缩，预训练自由能具有显著更高的相关性（皮尔逊系数：全量微调-0.820 vs -0.767/-0.632；少样本微调-0.890 vs -0.443/-0.1875）。
    - 预训练中的隐式偏置（大学习率、小批大小、高动量）通过降低预训练自由能，进而提升下游适应性。预训练训练损失在后期无法区分这些偏置的影响，而预训练自由能则提供有效信号。
- **理论贡献**：建立了预训练自由能控制下游自由能的渐近关系（Proposition 5.1），并为检查点选择提供了贝叶斯理论基础。

# 7. 优点：方法或实验设计上有哪些亮点

- **理论创新**：首次将贝叶斯模型选择中的自由能概念应用于迁移学习中的检查点选择，提供了严谨的数学框架（渐近展开、分布漂移有界条件下的控制关系）。
- **实用性强**：预训练自由能可完全基于预训练数据计算，无需下游任务先验知识，符合实际部署场景。
- **实验验证充分**：通过控制超参数（学习率、批大小、动量）来影响预训练自由能，并验证其与下游性能的单调关系，实验设计具有因果推断意义。表格1中的相关性对比客观展示了优于现有指标。
- **方法可操作**：提供了WBIC的实用计算方案（SGLD采样），并给出超参数推荐（步长、链长、温度等）。

# 8. 不足与局限：包括实验覆盖、偏差风险、应用限制等

- **实验覆盖有限**：仅测试了CIFAR-FS和mini-ImageNet两个图像分类数据集，且模型为ResNet-18和VGG-16，未涉及更大规模的模型（如BERT、GPT、ViT）或其他模态（文本、语音）。结果泛化性需进一步验证。
- **理论基础不完整**：作者承认目前只在下游适配采用贝叶斯方式（后验预测）时，才建立了自由能与下游泛化误差的严格联系。但实际微调常使用SGD等确定性优化，该联系依赖贝叶斯假设，可能不完全成立。
- **计算成本**：计算预训练WBIC需要使用SGLD采样，对于具有数十亿参数的大模型可能不切实际（作者也指出是未来挑战）。虽然提出可通过识别影响自由能的“杠杆”来间接优化，但实验仍依赖直接计算。
- **分布漂移假设**：Proposition 5.1要求 \(M = \max \frac{r_1}{r_0} < \infty\)。当预训练与下游分布差异极大（如类别支持不重叠）时，该界可能无意义（M无穷大）。作者虽提出通过使预训练数据更丰富来缓解，但未提供定量处理策略。
- **超参数敏感性**：WBIC计算涉及SGLD步长、链长、温度等超参数，文中给出了固定值，但未分析这些超参数对结果稳定性的影响。

（完）
