---
title: "Curated LLM: Synergy of LLMs and Data Curation for tabular augmentation in low-data regimes"
title_zh: Curated LLM：大语言模型与数据整理协同实现低数据表格增强
authors: "Nabeel Seedat, Nicolas Huynh, Boris van Breugel, Mihaela van der Schaar"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=9cG1oRnqNd"
tags: ["query:ai"]
score: 6.0
evidence: 利用大语言模型在低数据表格场景中进行数据增强
tldr: 该论文针对低数据场景下的表格数据增强问题，提出CLLM方法，利用大语言模型的先验知识生成合成数据。实验证明，与传统的生成模型相比，CLLM能够生成更多样化的数据，显著提升下游机器学习任务的性能。论文还讨论了如何筛选高质量生成数据，避免噪声影响。这一方法为数据稀缺领域提供了有效的解决方案。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-9cg1ornqnd/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1488, \"height\": 554, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-9cg1ornqnd/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 850, \"height\": 277, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-9cg1ornqnd/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 473, \"height\": 304, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-9cg1ornqnd/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 493, \"height\": 374, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-9cg1ornqnd/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 838, \"height\": 318, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-9cg1ornqnd/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 854, \"height\": 277, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-9cg1ornqnd/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 987, \"height\": 553, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-9cg1ornqnd/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1269, \"height\": 571, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-9cg1ornqnd/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1344, \"height\": 524, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-9cg1ornqnd/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1325, \"height\": 389, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-9cg1ornqnd/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 905, \"height\": 1247, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-9cg1ornqnd/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 812, \"height\": 283, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-9cg1ornqnd/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 855, \"height\": 128, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-9cg1ornqnd/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1756, \"height\": 1285, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-9cg1ornqnd/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 842, \"height\": 594, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-9cg1ornqnd/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1286, \"height\": 415, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-9cg1ornqnd/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 633, \"height\": 292, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-9cg1ornqnd/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1527, \"height\": 1656, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-9cg1ornqnd/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1241, \"height\": 286, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-9cg1ornqnd/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1327, \"height\": 824, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-9cg1ornqnd/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1338, \"height\": 827, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-9cg1ornqnd/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1338, \"height\": 833, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-9cg1ornqnd/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1338, \"height\": 827, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-9cg1ornqnd/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1683, \"height\": 724, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-9cg1ornqnd/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1120, \"height\": 379, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-9cg1ornqnd/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1051, \"height\": 1283, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-9cg1ornqnd/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 684, \"height\": 1323, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-9cg1ornqnd/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 982, \"height\": 290, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-9cg1ornqnd/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1255, \"height\": 240, \"label\": \"Table\"}]"
motivation: 传统表格数据生成器在低数据场景下难以生成足够多样有效的增强数据。
method: 利用大语言模型的先验知识生成合成表格数据，并结合质量控制机制剔除无效样本。
result: 在多个低数据表格数据集上，CLLM生成的增强数据显著提高下游ML模型性能。
conclusion: 利用LLM进行数据增强是低数据场景下有效且实用的方法。
---

## Abstract
Machine Learning (ML) in low-data settings remains an underappreciated yet crucial problem. Hence, data augmentation methods to increase the sample size of datasets needed for ML are key to unlocking the transformative potential of ML in data-deprived regions and domains. Unfortunately, the limited training set constrains traditional tabular synthetic data generators in their ability to generate a large and diverse augmented dataset needed for ML tasks. To address this challenge, we introduce $\texttt{CLLM}$, which leverages the prior knowledge of Large Language Models (LLMs) for data augmentation in the low-data regime. However, not all the data generated by LLMs will improve downstream utility, as for any generative model. Consequently, we introduce a principled curation mechanism, leveraging learning dynamics, coupled with confidence and uncertainty metrics, to obtain a high-quality dataset. Empirically, on multiple real-world datasets, we demonstrate the superior performance of $\texttt{CLLM}$ in the low-data regime compared to conventional generators. Additionally, we provide insights into the LLM generation and curation mechanism, shedding light on the features that enable them to output high-quality augmented datasets.

---

## 论文详细总结（自动生成）

# 论文总结：Curated LLM: Synergy of LLMs and Data Curation for tabular augmentation in low-data regimes

## 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：在低数据场景（样本量 n < 100）下，传统的表格数据增强方法（如 GAN、VAE、Normalizing Flows、SMOTE 等）因训练数据过少而无法生成足够多样且准确的合成样本，导致下游机器学习模型性能不佳。
- **研究动机**：数据稀缺严重阻碍了 ML 在医疗、金融、低收入国家等领域的应用。现有方法受限于小样本的分布，难以覆盖真实数据流形。
- **整体含义**：本文提出利用大型语言模型（LLMs）的广泛先验知识来生成表格数据，并结合数据策展（curation）机制筛选高质量样本，从而在低数据场景下实现有效的数据增强，提升下游模型性能。

## 2. 方法论

### 2.1 核心思想
- 采用**冻结（frozen）的 LLM**（如 GPT-4、GPT-3.5）通过上下文学习（in-context learning）生成合成表格数据，避免微调的高成本与过拟合风险。
- 设计**数据策展机制**，基于学习动力学（learning dynamics）计算每个合成样本的**置信度（confidence）**和**偶然不确定性（aleatoric uncertainty）**，剔除低质量、可能导致误导的样本。

### 2.2 关键技术细节
- **生成阶段**：
  - 构建提示（prompt），包含三部分：
    1. **背景信息**：数据集的任务描述和特征含义。
    2. **上下文示例**：将小训练集 D<sub>train</sub> 序列化为示例。
    3. **指令**：要求 LLM 利用先验知识生成多样且符合特征-标签关系的新样本。
  - 生成合成数据集 D<sub>syn</sub>（通常 1000 个样本）。
- **策展阶段**：
  - 基于 D<sub>train</sub> 训练一个分类器（如 XGBoost），记录其在多个训练检查点（checkpoints）上的预测。
  - 对 D<sub>syn</sub> 中每个样本 (x, y)，计算：
    - **平均置信度**：平均预测概率。
    - **偶然不确定性**：预测概率的方差。
  - 若样本的置信度低于阈值 τ<sub>conf</sub> 且偶然不确定性低于阈值 τ<sub>al</sub>，则视为“低质量”并丢弃。
  - 保留的样本构成策展数据集 D<sub>curated</sub>，用于训练下游分类器。

### 2.3 公式与算法流程（文本说明）
1. 输入：小训练集 D<sub>train</sub>，LLM，提示模板。
2. 生成：调用 LLM 生成大规模合成集 D<sub>syn</sub>。
3. 训练策展模型：在 D<sub>train</sub> 上训练一个分类器（例如 100 轮迭代的 XGBoost），记录 E 个检查点。
4. 计算指标：对每个 (x, y) ∈ D<sub>syn</sub>，计算平均置信度和偶然不确定性。
5. 过滤：根据阈值 τ<sub>conf</sub> 和 τ<sub>al</sub> 决定保留或丢弃。
6. 输出：策展后的数据集 D<sub>curated</sub>，再训练下游模型。

## 3. 实验设计

### 3.1 数据集与场景
- **7 个真实数据集**：
  - 4 个**私有医疗数据集**（需授权访问，因此不太可能出现在 LLM 训练语料中）：Covid-19、CUTRACT、MAGGIC、SEER。
  - 3 个**公开数据集**：Adult（金融）、Compas（刑事司法）、Drug（医疗）。
- 每个数据集按样本量分为 n = 20, 40, 100, 200 的低数据场景。
- 评估方式：Train-on-Synthetic-Test-on-Real（TSTR），即在合成数据上训练，在真实测试集上测试，指标为 AUC。

### 3.2 Benchmark 与对比方法
- **基线方法**：
  - 传统生成模型：CTGAN、TVAE、Normalizing Flows、TabDDPM。
  - 传统数据增强：SMOTE。
  - 微调 LLM 的生成方法：GReaT。
  - 额外对比：TabPFN（小表格分类的少样本学习方法）。
- **CLLM 变体**：使用 GPT-4、GPT-3.5 以及开源模型（Mistral-7b、LLAMA-13b/70b、Mixtral-8x7b）作为生成骨干，并分别测试策展与未策展版本。

### 3.3 实验充分性与公平性
- **重复次数**：每个配置重复 10 个不同随机种子（不同 D<sub>train</sub>/D<sub>test</sub> 划分）。
- **下游模型**：使用 4 种不同分类器（XGBoost、Random Forest、Logistic Regression、Decision Tree），取平均 AUC 作为最终性能。
- **消融实验**：
  - 验证 LLM 上下文信息的重要性（有/无特征描述提示）。
  - 验证策展机制的有效性（所有方法都增加策展对比）。
  - 验证 LLM 对少数群体的影响。
  - 验证开源 LLM 和低资源语言下的鲁棒性。
  - 验证阈值敏感性。
- **公平性分析**：设置了合成偏置数据，证明策展可缓解偏置。
- **总体实验数量**：约 7 数据集 × 4 样本量 × 10 种子 × 10+ 方法 = 超过 2800 次独立实验（包含消融），非常充分。

## 4. 资源与算力

- **文中未明确说明**所使用的 GPU 型号、数量或训练时长。
- 仅提及使用 Azure OpenAI 服务调用 GPT-4/GPT-3.5（无需本地微调），以及对于开源 LLM（Mistral-7b、LLAMA-13b/70b、Mixtral）可能运行在本地。但具体硬件资源细节（如 GPU 型号、数量、训练总时长）未给出。

## 5. 主要结论与发现

1. **CLLM + GPT-4 + 策展取得最佳性能**：在几乎所有低数据设置（n=20,40,100,200）中，CLLM 的 AUC 排名第一，甚至接近或超过在完整真实数据（Doracle）上训练的表现。
2. **策展机制普遍提升所有生成模型**：无论是 LLM 还是传统生成器，策展后性能均有提升，说明丢弃低质量样本是数据增强的关键环节。
3. **LLM 能够外推到训练数据未覆盖的区域**：t-SNE 可视化显示 GPT-4 生成的样本覆盖了真实流形中 D<sub>train</sub> 缺失的部分，而传统方法（如 TVAE）仅限于 D<sub>train</sub> 附近。
4. **少数群体获益最大**：在 COVID-19 数据集中，训练样本最少的亚组（如 Amarela 群体、40 岁以下群体）性能提升最大。
5. **上下文提示至关重要**：省略特征描述会导致生成质量大幅下降（精度和效用均降低）。
6. **“硬度”代理信号**：丢弃样本比例与下游 AUC 呈强负线性关系，可提前预警低质量合成数据集。
7. **开源 LLM 也可受益**：即使使用较小的开源模型（Mistral-7b、LLAMA-13b），策展后性能仍能提升。

## 6. 优点

- **方法创新**：首次系统性地将 LLM 的上下文学习能力与基于学习动力的数据策展相结合，用于低数据表格增强。
- **实用性强**：无需微调 LLM、无需外部数据集，计算成本低，适合资源受限场景（如低收入国家）。
- **灵活性**：可适配任何下游模型（树模型、线性模型等），不绑定特定分类器。
- **实验全面**：覆盖 7 个真实数据集、多种样本量、多种基线、多种 LLM 骨干，并包含丰富的消融实验和公平性分析。
- **可解释性**：通过分析策展丢弃样本的特征（如近邻标签一致性、与真实分布的对齐），揭示了策展机制的工作原理。

## 7. 不足与局限

- **依赖 LLM 质量**：最终性能受限于所选择 LLM 的先验知识和生成能力。更小的开源模型（如 Mistral-7b）生成的未策展数据质量较低，虽然策展后提升，但仍弱于 GPT-4。
- **潜在偏差风险**：LLM 可能从训练语料中引入社会偏置或错误知识。虽然策展能部分缓解，但论文未彻底解决偏置问题，仅在小规模合成实验中展示。
- **低资源语言表现下降**：将特征名称翻译为斯瓦希里语和豪萨语后，CLLM 性能降低（但仍优于部分基线）。
- **阈值依赖**：策展需要设定两个阈值（τ<sub>conf</sub> 和 τ<sub>al</sub>），虽然作者提供了默认值并通过敏感性实验验证其鲁棒性，但在实际应用中可能需要根据数据特点调整。
- **计算成本未量化**：论文未报告调用 LLM API 的总费用或本地推理的硬件需求，实际使用中可能产生大量 API 调用费用。
- **仅有分类任务验证**：实验仅针对二分类任务，未涉及多分类或回归问题。
- **提示工程未深度优化**：作者承认提示设计和 LLM 调优有进一步改进空间，但超出本文范围。

（完）
