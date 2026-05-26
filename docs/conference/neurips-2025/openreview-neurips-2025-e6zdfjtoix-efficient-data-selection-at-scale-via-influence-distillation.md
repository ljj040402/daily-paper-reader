---
title: Efficient Data Selection at Scale via Influence Distillation
title_zh: 通过影响蒸馏实现大规模高效数据选择
authors: "Mahdi Nikdan, Vincent Cohen-Addad, Dan Alistarh, Vahab Mirrokni"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=E6ZdfjtoiX"
tags: ["query:ai"]
score: 5.0
evidence: 大语言模型训练数据选择
tldr: 现代大语言模型训练中数据选择至关重要。本文提出影响蒸馏框架，利用二阶信息对训练样本最优加权，并针对梯度下降和Adam优化器推导闭式解。通过里程碑近似实现可扩展计算。实验表明在目标领域微调中，该方法用更少数据达到更优性能，显著降低数据成本。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-e6zdfjtoix/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 715, \"height\": 360, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e6zdfjtoix/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1443, \"height\": 393, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e6zdfjtoix/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1439, \"height\": 509, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e6zdfjtoix/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1352, \"height\": 1417, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e6zdfjtoix/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1138, \"height\": 573, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e6zdfjtoix/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1361, \"height\": 558, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e6zdfjtoix/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1370, \"height\": 337, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e6zdfjtoix/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1047, \"height\": 432, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-e6zdfjtoix/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1389, \"height\": 1554, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-e6zdfjtoix/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1440, \"height\": 578, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-e6zdfjtoix/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1392, \"height\": 166, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-e6zdfjtoix/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1371, \"height\": 153, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-e6zdfjtoix/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1386, \"height\": 130, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-e6zdfjtoix/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1194, \"height\": 218, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-e6zdfjtoix/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1120, \"height\": 176, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-e6zdfjtoix/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1173, \"height\": 335, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-e6zdfjtoix/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 558, \"height\": 293, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-e6zdfjtoix/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 993, \"height\": 137, \"label\": \"Table\"}]"
motivation: 现有数据选择方法缺乏理论指导，难以高效选择关键训练样本。
method: 基于影响函数蒸馏每个样本对目标分布的影响，推导最优权重。
result: "在多个LLM微调任务上，仅用10%数据即达到或超过全数据训练性能。"
conclusion: 提供了理论驱动的数据选择方案，大幅提升微调效率。
---

## Abstract
Effective data selection is critical for efficient training of modern Large Language Models (LLMs). This paper introduces Influence Distillation, a novel, mathematically-justified framework for data selection that employs second-order information to optimally weight training samples. By distilling each sample's influence on a target distribution, our method assigns model-specific weights that are used to select training data for LLM fine-tuning, guiding it toward strong performance on the target domain. We derive these optimal weights for both Gradient Descent and Adam optimizers. To ensure scalability and reduce computational cost, we propose a $\textit{landmark-based approximation}$: influence is precisely computed for a small subset of "landmark" samples and then efficiently propagated to all other samples to determine their weights. We validate Influence Distillation by applying it to instruction tuning on the Tulu V2 dataset, targeting a range of tasks including GSM8k, SQuAD, and MMLU, across several models from the Llama and Qwen families. Experiments show that Influence Distillation matches or outperforms state-of-the-art performance while achieving up to $3.5\times$ faster selection.

---

## 论文详细总结（自动生成）

# 论文中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

大语言模型（LLM）的训练和微调需要大量计算资源和精心筛选的数据集。现有数据选择方法存在以下问题：  
- 多采用启发式方法（如基于困惑度的过滤），缺乏数学理论支撑；  
- 依赖模型无关的静态特征，无法充分捕捉训练样本与目标分布之间的关系；  
- 部分方法（如 LESS）需要计算所有样本的梯度，计算成本极高（约 8400 TeraFLOPs），难以大规模实用。  

因此，本文提出一个**有数学理论依据、高效且可扩展的数据选择框架——影响蒸馏（Influence Distillation）**，旨在直接针对特定目标分布优化训练样本的权重，从而用更少的数据实现更好或相当的性能。

## 2. 论文提出的方法论

### 核心思想
通过二阶泰勒展开近似训练样本对目标分布损失的影响，为每个训练样本分配最优权重。该方法可直接用于梯度下降和 Adam 优化器。

### 关键技术细节
- **基本目标**：寻找样本权重 \( w \) 使得在源数据集 \( S \) 上加权训练后的模型在目标数据集 \( T \) 上损失最小。
- **二阶近似**：对一步梯度下降后的损失进行展开，得到关于 \( w \) 的二次目标函数：
  \[
  f(w; \theta) = -p^T w + \frac{\eta}{2} w^T Q w
  \]
  其中 \( p = G_S(\theta) g_T(\theta) \)，\( Q = \frac{1}{|S|} G_S(\theta) H_T(\theta) G_S^T(\theta) \)。
- **鲁棒权重**：为避免负权重、过拟合和数值不稳定，添加非负约束、归一化约束和 L2 正则化：
  \[
  \min_w f(w) + \frac{\lambda}{2}\|w\|^2,\quad s.t. \ w \ge 0,\ w^T \mathbf{1} = |S|
  \]
  \(\lambda\) 通过二分搜索调节，使恰好 \( k \) 个样本获得非零权重，以实现目标稀疏度。
- **Adam 优化器适配**：通过固定动量估计，推导出对应的 \( p_{\text{Adam}} \) 和 \( Q_{\text{Adam}} \)。
- **一阶近似**：实验发现二阶项在实际学习率下可忽略，因此采用一阶近似，避免计算 Hessian。
- **梯度投影**：使用随机 Hadamard 变换将梯度投影到低维空间（如 131072 维），降低存储和计算成本。
- **里程碑近似（Landmark-based Approximation）**：  
  为避免计算所有样本的梯度，选取少量“里程碑”样本精确计算其影响，然后通过**JVP 嵌入**将影响传播到其他样本。JVP 嵌入通过雅可比向量积（Jacobian-vector product）从模型中间层提取，仅需部分前向计算。
- **理论保证**：若梯度近似无偏且均方误差有界，则权重误差与正则化强度、维度有关（定理 4.1）。

## 3. 实验设计

- **训练数据集**：Tulu V2（约 5.8M 样本），随机采样 200k 作为候选池，从中选择 10k 子集。
- **目标数据集**：MMLU、GSM8k、BBH、TyDIQA、Codex、SQuAD。每个目标集提供 8–500 个示例作为“目标分布”。
- **模型**：Llama2-7B、Llama3.2-3B、Qwen2.5-1.5B、Qwen2.5-3B。
- **对比方法**：
  - 均匀随机选择（Uniform）
  - Mid-PPL（基于困惑度选择中间样本）
  - RDS+（基于模型嵌入的相似性）
  - 全数据集训练（Full）
  - LESS（需要全梯度计算，仅对比一次）
- **超参数**：AdamW 优化器，学习率 2e-5，训练 2 个 epoch，序列长度 2048，梯度累积 128，单卡 H100。
- **评估指标**：各任务准确率及平均提升。

## 4. 资源与算力

- 所有实验在**单张 H100 GPU** 上完成。
- **选择成本估算**：  
  - Influence Distillation（一阶 + 里程碑）：约 872 TeraFLOPs（Llama2-7B）。  
  - LESS：约 8400 TeraFLOPs（高 10 倍）。  
  - RDS+ 和 Mid-PPL：约 2800 TeraFLOPs。  
  - 注：论文未明确给出完整训练（选后微调）的总算力，但给出了选择阶段的 FLOPs。
- 论文提及**不纳入预热成本**，认为随池增大预热成本可忽略。

## 5. 实验数量与充分性

- **主要实验**（表 1）：4 个模型 × 6 任务 × 3 个随机种子，共 72 次独立实验。  
- **泛化实验**：  
  - 不同池大小（50k–200k）和选择样本数（2500–20000）的帕累托前沿（图 1，图 3 右）。  
  - 不同里程碑数量（512–16384）的影响（图 3 左）。  
  - 与 LESS 的对比（一次）。  
  - 嵌入函数对比（表 3）、权重是否用于训练（表 4）。  
  - 目标集大小消融（表 8）、里程碑选择方法（表 9）、权重跨任务迁移（表 6、7）、JVP 嵌入跨模型迁移（表 10）。  
  - 训练过程准确率变化（表 5）。  
- **充分性评价**：实验覆盖全面，包含主要基准、消融、可迁移性分析，重复 3 次种子，报告标准差。客观性较好。

## 6. 论文的主要结论与发现

- **Influence Distillation 在多数模型和任务上匹配或超越 SOTA 方法（RDS+、Mid-PPL、LESS），同时选择速度提升 2.9–3.5×。**
- 仅用 10k 样本（占全数据 5%），即可达到或超过全数据训练性能（如 Llama2-7B 上平均提升 +2.30 vs 全数据 +2.30）。
- 一阶近似足够有效，二阶项可忽略。
- JVP 嵌入比其他嵌入（RDS+、NV-Embed-v2、GTR-base）梯度恢复更好，且跨模型可迁移。
- 权重不直接用于训练时性能更稳定，可以仅用于选择样本。

## 7. 优点

- **理论扎实**：从二阶泰勒展开出发，推导出最优权重的闭式解，并解决了鲁棒性问题。
- **高效可扩展**：里程碑近似 + JVP 嵌入 + 梯度投影，大幅降低计算和存储开销。
- **实用性强**：可直接用于 LLM 微调，支持 Adam，适配不同模型和任务。
- **实验充分**：在多个模型、多个任务、多种设置下验证，结果稳定。
- **帕累托最优**：在计算成本与性能之间取得良好平衡。

## 8. 不足与局限

- **需要目标分布**：方法要求预先定义一个小型目标数据集，不适用于无目标分布的一般预训练场景（论文提到可作为未来方向）。
- **预训练适应性未验证**：方法针对微调设计，能否推广到预训练（梯度变化大、需要多阶段选择）尚不明确。
- **预热成本不纳入计算**：虽然认为可忽略，但实际预热仍需要少量计算。
- **二次项近似假设**：实际中若学习率较大或模型高度非线性，二阶项可能不可忽略，但论文实验表明可以忽略。
- **里程碑选择方式**：目前使用随机选择，虽比复杂方法简单，但可能未充分利用信息。

（完）
