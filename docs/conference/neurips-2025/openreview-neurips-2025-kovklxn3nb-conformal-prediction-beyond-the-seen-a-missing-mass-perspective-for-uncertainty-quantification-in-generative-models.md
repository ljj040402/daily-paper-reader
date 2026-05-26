---
title: "Conformal Prediction Beyond the Seen: A Missing Mass Perspective for Uncertainty Quantification in Generative Models"
title_zh: 超越可见的共形预测：生成模型不确定性量化的缺失质量视角
authors: "Sima Noorani, Shayan Kiyani, George J. Pappas, Hamed Hassani"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=KoVKLxn3Nb"
tags: ["query:ai"]
score: 6.0
evidence: 生成模型的共形预测，人工智能中的不确定性量化
tldr: 经典共形预测方法依赖几何距离或softmax分数，难以直接应用于生成模型。本文研究仅通过查询黑盒生成模型构建预测集的设定，引入覆盖率、测试时查询预算与信息量之间的新权衡。提出基于缺失质量视角的共形预测方法，在保持覆盖率的同时最小化查询次数，为生成式AI的安全部署提供原理性框架。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-kovklxn3nb/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1442, \"height\": 1064, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kovklxn3nb/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1165, \"height\": 1704, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kovklxn3nb/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1436, \"height\": 941, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-kovklxn3nb/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1449, \"height\": 345, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-kovklxn3nb/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 951, \"height\": 454, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-kovklxn3nb/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 900, \"height\": 1670, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-kovklxn3nb/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1257, \"height\": 639, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-kovklxn3nb/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 834, \"height\": 339, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-kovklxn3nb/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 938, \"height\": 420, \"label\": \"Table\"}]"
motivation: 现有共形预测方法依赖结构化输出，难以直接用于生成模型的不确定性量化。
method: 提出仅通过查询黑盒生成模型构建预测集的共形预测方法，引入缺失质量视角。
result: 在保持覆盖率的同时显著减少查询次数。
conclusion: 缺失质量视角能有效扩展共形预测到生成模型，促进安全部署。
---

## Abstract
Uncertainty quantification (UQ) is essential for safe deployment of generative AI models such as large language models (LLMs), especially in high-stakes applications. Conformal prediction (CP) offers a principled uncertainty quantification framework, but classical methods focus on regression and classification, relying on geometric distances or softmax scores--tools that presuppose structured outputs. We depart from this paradigm by studying CP in a query-only setting, where prediction sets must be constructed solely from finite queries to a black-box generative model, introducing a new trade-off between coverage, test-time query budget, and informativeness. We introduce **Conformal Prediction with Query Oracle** (CPQ), a framework characterizing the optimal interplay between these objectives. Our finite-sample algorithm is built on two core principles: one governs the optimal query policy, and the other defines the optimal mapping from queried samples to prediction sets. Remarkably, both are rooted in the classical **missing mass problem** in statistics. Specifically, the optimal query policy depends on the rate of decay--or the derivative--of the missing mass, for which we develop a novel estimator. Meanwhile, the optimal mapping hinges on the missing mass itself, which we estimate using Good-Turing estimators. We then turn our focus to implementing our method for language models, particularly in open-ended LLM tasks involving question answering, multi-step reasoning, and structured information extraction, where outputs are vast, variable, and often under-specified. Fine-grained experiments on three real-world open-ended tasks and two LLMs, show CPQ's applicability to **any black-box LLM** and highlight: (1) individual contribution of each principle to CPQ’s performance, and (2) CPQ's ability to yield significantly more informative prediction sets than existing conformal methods for language uncertainty quantification.

---

## 论文详细总结（自动生成）

# 论文中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **目标**：为生成模型（如大语言模型LLM）提供不确定性量化（UQ），确保安全部署。
- **传统局限**：经典共形预测（CP）依赖结构化输出空间（如回归的距离、分类的softmax分数），但生成模型的输出空间巨大、非结构化，且通常仅通过采样接口（query oracle）访问，不暴露完整概率分布。
- **关键挑战**：需要仅通过有限次查询（采样）构建预测集，同时满足三方面权衡：**覆盖率**（预测集包含真实标签的概率）、**测试时查询预算**（每样本采样次数）、**信息量**（预测集应尽可能小，避免依赖后备标签“EE”——表示“一切其他未观测标签”）。
- **新颖视角**：将问题视为**缺失质量（missing mass）**问题——即当前未观测到的正确标签的概率——来指导查询策略和预测集构造。

## 2. 方法论：核心思想、技术细节与算法流程
- **核心思想**：将CP扩展至仅能查询黑盒生成模型的设定，通过两个算法原则实现最优权衡：
  1. **最优查询策略（Principle 1）**：对于每个输入x，持续采样直到缺失质量的导数（即每多一个额外样本的边际收益）低于阈值β\*。导数由新提出的估计器 $\hat{\Delta}(x,t) = -\frac{2N_2}{t^2}$ 给出，其中 $N_2$ 是出现恰好两次的标签数。
  2. **最优预测集构造（Principle 2）**：基于Good-Turing估计器对缺失质量本身的估计 $\hat{\theta}(x,t) = N_1/t$，定义非一致性得分 $\hat{S}(x,y)$，对观测标签取 $1 - \hat{\omega}(y|x)$，对后备标签EE取 $2 - \hat{\theta}(x,t)$。然后通过分位数阈值化构建预测集。
- **算法流程（Algorithm 1: CPQ）**：
  - **查询模块**：对每个输入x，从LLM采样，每步更新导数估计，直到 $\hat{\Delta}(x, T(x)) \leq \beta\*$，得到采样标签集 $Z(x)$。
  - **校准模块**：利用独立校准集 $D_{\text{cal2}}$ 计算每个样本的非一致性得分，取 $(1-\alpha)$ 分位数 $q\*$。
  - **测试阶段**：对测试输入，用同一查询策略采样，然后预测集 $C(x) = \{ y \in Z(x) \cup \{EE\} : \hat{S}(x,y) \leq q\* \}$。
- **覆盖保证**：定理4.1证明方法具有分布自由的有限样本覆盖率保证 $P(Y_{\text{test}} \in C(X_{\text{test}})) \geq 1-\alpha$。

## 3. 实验设计：数据集、场景、基准与对比方法
- **数据集与场景**（均为开放式生成，移除多选题结构，使用精确匹配评估）：
  - **BBH Geometric Shapes**（250 prompts）：视觉推理，LLaMA-3 8B-Instruct生成。
  - **GSM8K**（300 prompts）：多步算术推理，Mixtral-8x7B-Instruct生成。
  - **BBH Date Understanding**（250 prompts）：时间推理，LLaMA-3 8B-Instruct生成。
  - **SimpleQA**（高幻觉率场景）：GPT-4o生成，验证鲁棒性。
- **基准方法**：
  - **CLM** (Conformal Language Modeling, 2024)
  - **SCOPE-Gen** (2025)
  - 消融变体：Vanilla（固定查询+简单校准）、Principle 1（自适应查询+简单校准）、Principle 1+2（完整CPQ）。
- **评估指标**：经验覆盖率（Empirical Coverage）、EE分数（EE fraction，预测集包含后备标签的比例，越低越好）、平均集大小（Average set size）。
- **预处理**：使用LLaMA-3-8B-Instruct进行语义等价聚类，将生成聚为语义簇。聚类方法不影响最终结论（附录C.5中有消融）。

## 4. 资源与算力
- 文中未明确提及具体的GPU型号、数量或训练时长。说明实验主要依赖API访问LLM，无需本地GPU资源。估计总运行时间约3-5小时（主要为LLM查询时间），算法本身运行时间仅几分钟。

## 5. 实验数量与充分性
- **实验规模**：覆盖3个主要数据集 + 1个额外高幻觉率数据集（SimpleQA），2种不同LLM。
- **消融实验**：系统比较Vanilla、Principle 1、Principle 1+2三个变体，在不同覆盖水平（1-α从0.5到0.95）和不同预算水平（B=20/40等）下进行。
- **与基线对比**：在多个覆盖水平上公平比较CLM和SCOPE-Gen（控制相同平均查询预算），结果表格详实。
- **鲁棒性实验**：高幻觉率场景（SimpleQA on GPT-4o）结果一致。
- **聚类方法消融**：比较四种聚类方法（LLaMA、RoBERTa、Word2Vec、MiniLM），证明方法对聚类细节不敏感。
- **公平性**：控制预算、重复50次随机分割、报告标准差，对比方法扩展输出空间以包含EE标签，避免偏袒。
- **结论**：实验设计充分、客观、公平。

## 6. 主要结论与发现
- CPQ在所有数据集和覆盖水平上均能维持接近名义覆盖率的经验覆盖，同时显著降低EE分数（即减少依赖后备标签，提供更信息量的预测集）。
- 每个算法原则均贡献独立改进，完整CPQ（Principle 1+2）最优。
- 与CLM和SCOPE-Gen相比，CPQ在相同预算下EE分数降低数倍（例如GSM8K上从70%降至16%），且经验覆盖更紧。
- 缺失质量的导数估计量 $\hat{\Delta} = -2N_2/t^2$ 在合成数据和真实数据上均表现良好，优于朴素有限差分基线。
- CPQ可应用于任何黑盒LLM，不依赖logits或概率输出。

## 7. 优点：方法与实验设计亮点
- **理论新颖性**：首次将缺失质量概念系统引入共形预测，并推导出最优查询策略和最优预测集构造的两个原则，具有独立理论价值。
- **算法实用性**：算法仅需黑盒采样，无需模型内部信息，适用于任意生成模型（LLM、扩散模型等）。
- **覆盖保证**：证明有限样本分布自由的覆盖率，符合CP传统。
- **实验全面性**：消融实验、基线对比、不同预算/覆盖/数据集/模型/聚类方法的全面评估，并额外验证高幻觉率鲁棒性。
- **开源**：提供代码。

## 8. 不足与局限
- **低查询预算下的估计挑战**：极少量采样（t很小）时，缺失质量及其导数的Good-Turing估计方差较大，可能影响稳定性。
- **聚类依赖**：虽然在消融中表现鲁棒，但语义聚类质量仍可能影响后续估计；论文未探索长文本或高度领域专用生成的聚类挑战。
- **假设π ≈ p**：理论推导假设查询分布等于真实分布，但实验中使用黑盒LLM（分布可能偏离），尽管经验上仍有效，未给出理论边界。
- **仅覆盖有限空间**：预测集限制在采样集∪{EE}，当采样数极少时，EE频繁出现导致信息量低；论文依赖惩罚项平衡，但用户需手动设定λ（未敏感性分析）。
- **未与其他非CP方法比较**：如基于熵或一致性的不确定性方法，仅比较了CP类方法。
- **计算成本**：虽然算法本身快，但依赖多次LLM查询（每个测试点可能多次），在计算受限时可能不适用。

（完）
