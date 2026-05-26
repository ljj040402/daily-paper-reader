---
title: "AcuRank: Uncertainty-Aware Adaptive Computation for Listwise Reranking"
title_zh: AcuRank：面向列表式重排序的不确定性感知自适应计算
authors: "Soyoung Yoon, Gyuwan Kim, GYU-HWUNG CHO, seung-won hwang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=H918WyPf0s"
tags: ["query:ai"]
score: 6.0
evidence: 基于大语言模型的自适应重排序，贡献于自然语言处理技术
tldr: 现有列表式重排序方法对所有查询使用固定计算预算，忽视了查询难度和文档分布差异，导致效率低下。本文提出AcuRank，基于贝叶斯TrueSkill模型对文档相关性进行不确定性估计，并动态调整计算量与目标，直到置信度达标。在多个检索数据集上，AcuRank在保持精度的同时显著降低了计算成本。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-h918wypf0s/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1440, \"height\": 355, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-h918wypf0s/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 969, \"height\": 549, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-h918wypf0s/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 394, \"height\": 513, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-h918wypf0s/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1447, \"height\": 729, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h918wypf0s/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1447, \"height\": 308, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h918wypf0s/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1376, \"height\": 907, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h918wypf0s/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1003, \"height\": 260, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h918wypf0s/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1447, \"height\": 196, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h918wypf0s/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1444, \"height\": 238, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h918wypf0s/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1456, \"height\": 837, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h918wypf0s/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1376, \"height\": 657, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h918wypf0s/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1451, \"height\": 416, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h918wypf0s/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1452, \"height\": 376, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h918wypf0s/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1022, \"height\": 222, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h918wypf0s/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1455, \"height\": 866, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h918wypf0s/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 804, \"height\": 185, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h918wypf0s/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1444, \"height\": 254, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h918wypf0s/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1178, \"height\": 577, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h918wypf0s/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1002, \"height\": 392, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h918wypf0s/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 853, \"height\": 255, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h918wypf0s/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1441, \"height\": 357, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h918wypf0s/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1456, \"height\": 1433, \"label\": \"Table\"}]"
motivation: 固定计算预算的重排序方法忽略了查询难度差异，导致效率低下。
method: 提出AcuRank框架，利用贝叶斯TrueSkill模型迭代估计不确定性，动态调整计算。
result: 在多个检索数据集上以更低计算成本保持或提升重排序精度。
conclusion: 不确定性感知的自适应计算能有效优化列表式重排序的效率与效果。
---

## Abstract
Listwise reranking with large language models (LLMs) enhances top-ranked results in retrieval-based applications.
Due to the limit in context size and high inference cost of long context, reranking is typically performed over a fixed size of small subsets, with the final ranking aggregated from these partial results.
This fixed computation disregards query difficulty and document distribution, leading to inefficiencies. 
We propose AcuRank, an adaptive reranking framework that dynamically adjusts both the amount and target of computation based on uncertainty estimates over document relevance. 
Using a Bayesian TrueSkill model, we iteratively refine relevance estimates until reaching sufficient confidence levels, and our explicit modeling of ranking uncertainty enables principled control over reranking behavior and avoids unnecessary updates to confident predictions.
Results on the TREC-DL and BEIR benchmarks show that our method consistently achieves a superior accuracy–efficiency trade-off and scales better with compute than fixed-computation baselines.
These results highlight the effectiveness and generalizability of our method across diverse retrieval tasks and LLM-based reranking models.

---

## 论文详细总结（自动生成）

以下是基于给定论文《AcuRank: Uncertainty-Aware Adaptive Computation for Listwise Reranking》的详细中文总结。

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：现有基于大语言模型（LLM）的列表式重排序方法（Listwise Reranking）对所有查询使用固定的计算预算（如固定数量的重排序调用），忽视了不同查询的难度差异和文档的分布特性。这导致了计算资源的浪费（简单查询过度计算，复杂查询计算不足），无法在精度与效率之间取得最优平衡。
- **研究背景**：信息检索系统通常先使用快速检索（如BM25）选出候选文档，再通过重排序提升顶部的精度。列表式重排序利用LLM一次性比较一组文档，能捕捉跨文档关系，效果优于点式和成对方法。但由于LLM输入长度限制，通常只能对小批量文档进行排序，整体排序需通过多次调用完成。传统方法如滑动窗口（Sliding Windows）和锦标赛式排序（TourRank）采用固定策略，缺乏自适应性。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：提出AcuRank框架，基于不确定性感知的自适应计算。它利用贝叶斯TrueSkill模型对每个文档的相关性进行概率建模（均值和方差），在每次迭代中识别不确定性高的文档（即被判定为可能在top-k边界附近的文档），仅对这些文档进行重排序，然后更新其相关性估计，重复直至收敛或达到预算。
- **关键技术细节**：
  - **TrueSkill模型**：每个文档的相关性表示为高斯分布 \( x_i \sim N(\mu_i, \sigma_i^2 + \beta^2) \)，其中 \(\mu_i\) 为估计相关性，\(\sigma_i\) 为认知不确定性（随证据积累下降），\(\beta\) 为固定观测噪声。
  - **不确定性量化**：计算文档出现在top-k的概率 \( s_i = P(x_i > t(k)) \)，其中阈值 \(t(k)\) 通过二分搜索使预期超过阈值的文档数等于k。选择 \( \epsilon < s_i < 1-\epsilon \) 的文档作为不确定候选集。
  - **迭代流程**：初始化（基于第一阶段检索分数设定 \(\mu_i\) 和 \(\sigma_i = \mu_i/3\)）→ 选择不确定性候选并分组（每组大小m）→ 调用LLM重排序 → 通过TrueSkill更新相关性（根据重排序结果调整\(\mu_i\)和\(\sigma_i\)）→ 重复直至不确定文档数小于阈值或预算耗尽。
  - **停止准则**：默认使用不确定文档数低于阈值（如10）或达到计算预算；也可用top-k稳定性。

### 3. 实验设计：数据集、基准、对比方法

- **数据集**：TREC Deep Learning (DL19-DL23, DL-Hard) 和 BEIR (TREC-COVID, NFCorpus, Signal-1M, News, Robust04, Touché, DBPedia, SciFact) 共14个数据集，涵盖多种领域。
- **基准（Benchmark）**：使用NDCG@10作为评估指标，效率指标为每查询LLM调用次数（以及窗口大小、输入长度、延迟、FLOPs等）。
- **对比方法**：
  - 基线：Sliding Windows (SW-1, SW-2, SW-3)，TourRank (1/2/5/10轮)，TrueSkill-Static（仅基于\(\mu_i\)选择，不含不确定性）。
  - AcuRank变体：AcuRank-9（固定预算9次调用），AcuRank（默认），AcuRank-H/HH（高精度变体，更严格阈值）。
- **检索器和重排序器**：默认BM25作为第一阶段检索（top-100或top-1000），重排序器使用RankZephyr-7B；额外测试使用SPLADE++ED、Contriever作为检索器，RankGPT (gpt-4.1-mini) 和 RankVicuna-7B、Llama-3.3-70B-Instruct作为重排序器。

### 4. 资源与算力

- **硬件**：单个 NVIDIA A6000 GPU（48GB VRAM）。实验在此环境下完成。
- **软件**：基于transformers库，使用贪心解码，最大输入长度4096 tokens。LLM推理未使用vLLM等加速后端。
- **时间**：文中未给出完整训练时间（因为主要是推理），但报告了延迟数据（例如DL19上AcuRank-9约58秒，全AcuRank约106秒），TrueSkill更新开销仅占0.1%。

### 5. 实验数量与充分性

- **实验数量**：大量实验，包括：
  - 主实验：在14个数据集上比较AcuRank与多个基线（SW-1/2/3, TourRank-1/2/5/10等），表1、表3、表7-8等。
  - 不同检索器/重排序器实验：SPLADE++ED、Contriever、RankGPT、RankVicuna、Llama-3.3-70B。
  - 消融实验：初始化方式、分组策略、停止准则（表4）、阈值敏感性（表13）、方差初始化（表5）等。
  - 自适应行为分析：查询困难度与调用次数的相关性（WIG指标）、硬/软查询分解（表15）。
  - 可扩展性实验：改变候选集大小n=50～1000，排名稳定性测试（表17-18）。
- **充分性**：实验设计全面，覆盖多种场景，对比公平（匹配计算预算），消融验证各组件贡献，结果具有统计显著性（提供Spearman相关p值）。结论合理且支持充分。

### 6. 论文的主要结论与发现

- **主要结论**：AcuRank在所有测试场景下均优于固定计算基线，在相同或更少的LLM调用次数下取得更高的NDCG@10。它实现了更优的精度-效率权衡。
- **关键发现**：
  - 自适应计算将更多资源分配给困难查询（与WIG负相关，p<10⁻⁸），而简单查询消耗较少。
  - 不确定性建模（TrueSkill）是关键：TrueSkill-Static（仅用均值）性能低于AcuRank，证明排名不确定性引导选择至关重要。
  - AcuRank在大候选集下缩放更好（子线性增长），且排名稳定性更强。
  - 高计算预算变体（AcuRank-H/HH）可继续提升精度，不会过早饱和，支持anytime预测。

### 7. 优点

- **方法创新**：将贝叶斯TrueSkill模型引入列表式重排序，实现不确定性驱动的自适应计算，不同于传统固定策略。
- **理论基础**：概率相关性建模使不确定性量化具有数学严谨性，且TrueSkill更新高效（闭式解）。
- **灵活部署**：提供多种变体（AcuRank-9/AcuRank/AcuRank-H等），适应不同预算需求。
- **实验广泛**：在14个数据集上验证，覆盖多种检索器和LLM模型，消融和鲁棒性分析充分。
- **效率显著**：在同等精度下大幅减少LLM调用次数（如top-1000场景下AcuRank调用68次 vs SW-1 94次，但NDCG更高）。
- **可扩展性**：对更大候选集（如1000）缩放优于滑动窗口。

### 8. 不足与局限

- **开源资源**：仅给出代码链接，但未发布模型或大规模预训练，实验可重复性依赖于公开数据。
- **超参数选择**：全局固定\(\epsilon\)、\(\tau\)等可能不适用于所有领域；文中承认需手动调整，未提供自动化适配方案。
- **并行化潜力未充分利用**：虽然支持组间并行，但论文主要评估串行调用次数，未深入分析并行加速带来的实际延迟优势。
- **未覆盖推理密集型检索**：文中提及未来方向，但未在当前工作中探索推理式重排序（如ReasonRank等）。
- **对第一阶段检索质量的依赖**：初始化使用检索分数，若检索质量差可能影响不确定性估计。
- **仅评估NDCG@10**：未评估其他指标（如MRR、MAP等），但NDCG@10是标准指标。

（完）
