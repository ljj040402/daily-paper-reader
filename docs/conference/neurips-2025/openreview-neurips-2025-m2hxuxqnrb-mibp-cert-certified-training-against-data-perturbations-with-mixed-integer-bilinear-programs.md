---
title: "MIBP-Cert: Certified Training against Data Perturbations with Mixed-Integer Bilinear Programs"
title_zh: MIBP-Cert：基于混合整数双线性规划的数据扰动认证训练
authors: "Tobias Lorenz, Marta Kwiatkowska, Mario Fritz"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=M2HxuxqNrb"
tags: ["query:ai"]
score: 5.0
evidence: AI鲁棒性与认证
tldr: 该论文提出MIBP-Cert方法，通过混合整数双线性规划计算确定性的鲁棒性边界，为训练阶段的数据扰动提供可证明的保证。该方法能预测所有可能输出，确保模型在面对复杂攻击时的可靠性。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-m2hxuxqnrb/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 710, \"height\": 654, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-m2hxuxqnrb/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1394, \"height\": 355, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-m2hxuxqnrb/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1024, \"height\": 224, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-m2hxuxqnrb/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1446, \"height\": 234, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-m2hxuxqnrb/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1316, \"height\": 266, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-m2hxuxqnrb/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 542, \"height\": 183, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-m2hxuxqnrb/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 816, \"height\": 262, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-m2hxuxqnrb/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 818, \"height\": 301, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-m2hxuxqnrb/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1122, \"height\": 281, \"label\": \"Table\"}]"
motivation: 现有经验性防御无法应对不断变化的攻击，需要可证明的鲁棒训练方法来保证模型在扰动数据下的安全性。
method: 提出基于混合整数双线性规划（MIBP）的认证方法，计算可达参数集，从而得到确定性的鲁棒边界。
result: 该方法能处理复杂威胁模型，提供可证明的鲁棒性保证。
conclusion: MIBP-Cert为AI系统在训练阶段的数据鲁棒性提供了首个可证明的解决方案。
---

## Abstract
Data errors, corruptions, and poisoning attacks during training pose a major threat to the reliability of modern AI systems. While extensive effort has gone into empirical mitigations, the evolving nature of attacks and the complexity of data require a more principled, provable approach to robustly learn on such data—and to understand how perturbations influence the final model. Hence, we introduce MIBP-Cert, a novel certification method based on mixed-integer bilinear programming (MIBP) that computes sound, deterministic bounds to provide provable robustness even under complex threat models. By computing the set of parameters reachable through perturbed or manipulated data, we can predict all possible outcomes and guarantee robustness. To make solving this optimization problem tractable, we propose a novel relaxation scheme that bounds each training step without sacrificing soundness. We demonstrate the applicability of our approach to continuous and discrete data, as well as different threat models—including complex ones that were previously out of reach.

---

## 论文详细总结（自动生成）

### 论文总结：MIBP-Cert：基于混合整数双线性规划的数据扰动认证训练

---

#### 1. 核心问题与整体含义
- **研究动机**：训练阶段的数据扰动（如错误、污染、投毒攻击）严重威胁AI系统的可靠性。现有经验性防御方法（如数据过滤、鲁棒训练）无法提供形式化保证，攻击者可绕过。政府机构已将其列为核心威胁。
- **整体含义**：需要一种可证明的、确定性的鲁棒学习方法，能够在复杂威胁模型下保障模型输出的安全性。本文提出 **MIBP-Cert**，通过混合整数双线性规划（MIBP）计算可达参数集的确定性边界，从而对训练阶段的各类扰动提供可证明的鲁棒性。

#### 2. 方法论
- **核心思想**：将认证训练转化为参数空间中的精确优化问题。每个训练步骤构建一个MIBP，编码输入扰动、前向传播、损失函数、反向传播和参数更新。为避免将整个训练链式编码（计算上不可行），在每个参数更新后对参数空间进行松弛，保持声学性。
- **关键技术细节**：
  - **形式化威胁模型**：用约束集合C(D, D′)描述允许的数据扰动，可包含ℓ∞界、稀疏性、单调性、类别条件等复杂约束。
  - **参数界递归计算**：θ_i ≤ A_i(D′, θ′) ≤ θ_i，其中θ′ ∈ [θ_{i-1}, θ_{i-1}]。
  - **MIBP构建**：每个训练迭代构建2m个优化问题（m为参数数量），分别最小化和最大化每个参数。约束包括：输入约束（例如ℓ∞）、参数约束（上一轮界）、层约束（线性层为双线性，ReLU用Big-M或SOS编码为分段线性）、损失约束（铰链损失可精确编码）、梯度约束（链式法则产生双线性）、参数更新约束（θ_i^{new} = θ_i - λ ∂J/∂θ）。
  - **求解器**：使用Gurobi原生支持双线和分段线性约束。
  - **预测认证**：用最终参数界编码前向传播，检查是否存在某个类别logit在所有可能参数下均大于其他logit。
- **算法流程**（文字说明）：
  - 训练：初始化参数界与初始值相同。对每个epoch，清空MIBP模型，添加参数界约束，对每个训练样本添加输入、层、损失、梯度和参数更新约束。最后对每个参数分别最小化和最大化，得到新的参数界。
  - 预测：用参数界构建MIBP，对每个测试样本检查每个类别logit的最小差值是否非负；若存在，则输出该类别，否则放弃预测。

#### 3. 实验设计
- **数据集**：
  - **TwoMoons**（合成二分类，100训练/200验证/200测试），噪声0.1，二维连续特征。
  - **UCI Iris**（3类，150样本，4连续特征）及二类子集；**Breast Cancer Wisconsin**（二类，30连续特征，369训练/100验证/100测试）。
  - **NPHA**（National Poll on Healthy Aging，714样本，14分类特征，3类目标），用于复杂离散扰动。
- **威胁模型**：
  - ℓ∞-norm扰动（连续特征）。
  - 离散特征复杂约束：缺失值（指定特征可任意取值）、心理健康的乐观报告偏差（值只能不变或变糟一级）。
- **对比方法**：FullCert [20]（区间界传播）、Sosnin et al. [28]（区间+线性界）。比较了认证准确率及标准差。
- **指标**：认证准确率（certified accuracy，即测试样本中被证明预测正确的比例）。

#### 4. 资源与算力
- **硬件**：CPU集群（AMD Rome 7742，128核@2.25GHz），每个任务最多32核。未使用GPU（Gurobi不支持GPU）。
- **训练时长**：TwoMoons上每epoch约19-156秒（取决于扰动大小），而基线方法仅0.01-0.04秒。更复杂模型（如6层5宽）时22秒/epoch。总实验规模较小，论文未报告总GPU时或总能耗。

#### 5. 实验数量与充分性
- **主要实验**：TwoMoons上三个ϵ(0.0001,0.001,0.01)各10个随机种子（表2）；UCI Iris和Breast Cancer三个ϵ（表3a-c）；NPHA三个复杂场景（表4）。此外有架构消融（层数与宽度，表6-7）、运行时分析（表5、表8）。
- **充分性**：实验覆盖了连续和离散数据、简单和复杂威胁模型、不同扰动大小，与两个最先进确定性方法对比，并报告了均值和标准差。但未在更大模型（如深层CNN、大图像数据集）或更多基线（如随机平滑方法）上测试，也未涉及多分类超3类的场景（除Iris全类外）。整体较为充分，但规模有限。

#### 6. 主要结论与发现
- MIBP-Cert在认证准确率上显著优于FullCert和Sosnin等，尤其是大扰动区域（ϵ=0.01时TwoMoons认证准确率81.4% vs 69-71.5%；Iris 2类ϵ=0.3时40% vs 20%）。
- 训练更稳定：标准差更小，未出现发散现象（约4% vs 11%）。
- 能处理此前方法无法处理的复杂威胁模型（离散特征、缺失值、报告偏差），提供了实用的鲁棒性诊断。
- 运行时虽慢但可接受，实际分支数远低于最坏指数情况。

#### 7. 优点
- **形式上突破**：首次将训练时认证形式化为MIBP，避免粗放凸松弛（如区间界）导致的发散和界膨胀问题，理论收敛性得到保证。
- **表达力强**：支持线性、双线性、整数、分段线性等任意混合约束，可建模现实中的结构化/条件扰动（如仅允许某些特征变化）。
- **确定性保证**：提供声学、确定性界（非概率性），可给出明确的“保证正确”或“放弃”结果。
- **实验扎实**：在多个数据集、多种扰动、多个基线对比下展示了优势，并进行了消融和复杂度分析。

#### 8. 不足与局限
- **可扩展性**：MIBP是NP难问题，当前实现仅适用于小模型（数百参数）、小数据集（百个样本）。论文未在深度卷积网络或大规模数据集上验证。
- **计算成本高**：相比区间界方法慢3-4个数量级，依赖商业求解器Gurobi，可能限制实际部署。
- **激活函数限制**：对非分段线性激活（如sigmoid/tanh）需采用分段线性松弛，引入近似，虽然可调整紧度但增加了复杂度。
- **实验覆盖有限**：未包含更丰富的基线（如随机平滑方法Bagging、BagFlip），也未对多分类（>3类）进行大规模测试，且仅在CPU上运行。
- **偏差与风险**：论文声明非恶意意图，但若被用于攻击者评估防御边界，可能带来负作用。此外，认证依赖于威胁模型假设，若实际攻击超出假设，则保证失效。

（完）
