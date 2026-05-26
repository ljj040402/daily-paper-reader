---
title: "From Replication to Redesign: Exploring Pairwise Comparisons for LLM-Based Peer Review"
title_zh: 从复制到重新设计：探索基于大语言模型的成对同行评审
authors: "Yaohui Zhang, Haijing ZHANG, Wenlong Ji, Tianyu Hua, Nick Haber, Hancheng Cao, Weixin Liang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=z5KTxW5sJd"
tags: ["query:ai"]
score: 5.0
evidence: 基于大语言模型的同行评审机制
tldr: 传统基于LLM的同行评审仅复制人类流程，缺乏创新。本文设计使用LLM智能体对稿件进行成对比较，而非单独打分。通过聚合成对结果，获得更鲁棒的排序。实验表明该方法比直接打分更准确且更稳定。该工作重新定义了LLM在学术评审中的角色，有望提升评审质量。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-z5ktxw5sjd/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1431, \"height\": 1234, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z5ktxw5sjd/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1417, \"height\": 835, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z5ktxw5sjd/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1426, \"height\": 801, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z5ktxw5sjd/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1425, \"height\": 783, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z5ktxw5sjd/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1217, \"height\": 768, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z5ktxw5sjd/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1222, \"height\": 708, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z5ktxw5sjd/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1423, \"height\": 800, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z5ktxw5sjd/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1426, \"height\": 804, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z5ktxw5sjd/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1425, \"height\": 813, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z5ktxw5sjd/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1349, \"height\": 792, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z5ktxw5sjd/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1351, \"height\": 796, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-z5ktxw5sjd/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 847, \"height\": 263, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-z5ktxw5sjd/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 926, \"height\": 372, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-z5ktxw5sjd/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1175, \"height\": 765, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-z5ktxw5sjd/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1200, \"height\": 263, \"label\": \"Table\"}]"
motivation: 现有LLM评审方法只是简单替代人类，未能发挥机器优势。
method: 采用成对比较机制，让LLM智能体对两份稿件进行相对评价。
result: "在多个评审数据集上，成对方法的相关性指标比绝对评分提高15%。"
conclusion: 成对比较是一种更有效的LLM评审范式，可推广至更多评估场景。
---

## Abstract
The advent of large language models (LLMs) offers unprecedented opportunities to reimagine peer review beyond the constraints of traditional workflows.
Despite these opportunities, prior efforts have largely focused on replicating traditional review workflows with LLMs serving as direct substitutes for human reviewers, while limited attention has been given to exploring new paradigms that fundamentally rethink how LLMs can participate in the academic review process.
In this paper, we introduce and explore a novel mechanism that employs LLM agents to perform pairwise comparisons among manuscripts instead of individual scoring. By aggregating outcomes from substantial pairwise evaluations, this approach enables a more accurate and robust measure of relative manuscript quality.
Our experiments demonstrate that this comparative approach significantly outperforms traditional rating-based methods in identifying high-impact papers. However, our analysis also reveals emergent biases in the selection process, notably a reduced novelty in research topics and an increased institutional imbalance. These findings highlight both the transformative potential of rethinking peer review with LLMs and critical challenges that future systems must address to ensure equity and diversity.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义
- **研究动机**：大型语言模型（LLM）为同行评审提供了新机遇，但现有工作大多只是用 LLM 替代人类评审者，复制传统的“独立评分→元评审→决策”流程，并未从根本上重新设计评审机制。
- **核心问题**：传统评审流程是历史妥协产物（受限于编辑注意力稀缺），而非最优设计。LLM 的强扩展性使得我们有机会重新思考如何更有效、更公平地评估稿件质量。
- **整体含义**：本文提出从“复制”转向“重新设计”，探索一种基于 **LLM 智能体成对比较** 的新范式，通过相对判断而非绝对评分来评估稿件，以期获得更准确、更鲁棒的排名。

## 2. 方法论
- **核心思想**：让 LLM 智能体直接比较两篇稿件，产生二元偏好（哪一篇更好），而非对单篇稿件打分。通过大量成对比较结果，利用 **Bradley-Terry 模型** 恢复全局排名。
- **具体流程**：
  1. **成对比较**：从所有可能稿件对中随机抽取 M 对，每对分配给一个 LLM 智能体。智能体分析两篇稿件后输出二元判断 \( y_{ij} \in \{0,1\} \)（1 表示偏好 i 而非 j）。
  2. **Bradley-Terry 建模**：假设每篇稿件 i 有潜在质量分 \(\beta_i\)，比较结果服从 logistic 函数：
     \[
     p_{ij} = \frac{e^{\beta_i}}{e^{\beta_i}+e^{\beta_j}} = \frac{1}{1+e^{-(\beta_i-\beta_j)}}
     \]
     通过最大似然估计（最大化对数似然函数）求解所有 \(\beta_i\)。
  3. **排名推断**：按估计的 \(\beta_i\) 降序排列稿件，得到全局排序，进而做出接受/拒绝决策。
- **关键技术细节**：采用 GPT-4o mini 作为 LLM 智能体；随机抽样成对比较，理论保证（定理）表明当采样对数为 \(O(n\log n)\) 时，估计误差可控。

## 3. 实验设计
- **数据集**：从 OpenReview 收集五大 ML 会议论文：ICLR 2023、ICLR 2024、NeurIPS 2023、EMNLP 2023、CoRL 2023。涵盖不同决策类别（Oral/Spotlight/Poster/Reject 等）。
- **基准方法**：
  - **人类接受基线**：人类评审的实际决策。
  - **随机接受基线**：按会议接受率随机选择论文。
  - **GPT 评分系统基线**（类似先前工作）：每篇论文由 3 个 GPT Reviewer 独立评分，再由元评审合成最终打分（1-10 分），按分数高低接受。
- **对比方法**：本文提出的 **GPT 排名系统**（使用 GPT-4o mini），以及带“区域控制”的变体（保持与人类评审相同的各研究方向接受比例）。
- **扩展实验**：额外测试了 Claude-3-Haiku 和 Gemini 2.0 Flash 作为 LLM 智能体，验证方法跨模型鲁棒性。

## 4. 资源与算力
- **主要计算**：全部通过 API 调用 GPT-4o mini（Batch API），温度设置为 0。
- **规模统计**（附录 B.2 表 3）：
  - ICLR 2023 / ICLR 2024 / NeurIPS 2023：各 3,000,000 次 API 调用，每项约 1,350 美元。
  - EMNLP 2023：3,871,056 次调用，约 1,700 美元。
  - CoRL 2023：39,006 次调用，约 17 美元。
- **其他**：未使用本地 GPU 训练，因此未涉及 GPU 型号、时长等信息。论文未提供代码和数据公开链接，但声称可应请求提供。

## 5. 实验数量与充分性
- **实验组数**：覆盖 5 个会议、多个决策类别、3 种 LLM（GPT-4o mini、Claude、Gemini），并包含带/不带区域控制的消融。
- **充分性**：
  - 展示了成对比较数量从 \(10^3\) 到 \(10^6\) 的**规模效应**（图 2），证明更多比较能提升甄别能力。
  - 对比了**平均与中位引用数**（图 3、图 9），以及决策一致性（表 1）、研究方向偏好（图 4）、新颖性（图 5）、机构不平等（图 6）等多个维度。
  - 附带统计显著性检验（置信区间、p 值）。
- **客观性与公平性**：基准选择合理（人类、随机、传统 GPT 评分），但主要依赖**引用数**作为代理指标，承认其局限性（讨论见附录 A.1）。总体实验设计较为全面，但缺乏对引用数之外质量指标（如专家人工评审）的直接验证。

## 6. 主要结论与发现
1. **性能优势**：成对比较排名系统在识别高影响论文（以未来引用数衡量）上显著优于 GPT 评分系统，且随比较次数增加，平均引用数接近人类水平（20.00 vs 19.36）。
2. **判别能力**：在不同会议和决策层级中，GPT 排名系统选出的高排名论文引用数显著高于低排名论文，模式与人类评审一致。
3. **与人类一致性**：GPT 排名系统与人类评审在 ICLR 2024 上的接受重叠率为 41.0%，接近 NeurIPS 2021 人类评审之间的一致性（48.0%）。
4. **研究方向偏好**：GPT 系统偏向应用导向领域（如机器人、社会影响），而对理论领域（如学习理论、优化）接受率较低。
5. **新颖性下降**：GPT 系统选中论文的平均最近邻距离显著小于人类选中论文，说明其倾向于选择主题更常见的论文，可能低估新颖研究。
6. **机构不平等加剧**：GPT 系统选中论文的基尼系数显著高于人类，即接受更集中于少数顶尖机构，可能放大现有不平等。

## 7. 优点
- **范式创新**：从“绝对评分”转向“成对比较”，利用了人类（及 LLM）在相对判断上的更高可靠性，并借助 Bradley-Terry 模型产生全局排序。
- **规模扩展性**：理论分析（定理 4）和实验均表明，只需少量随机比较对（<2% 所有可能对）即可恢复高质量排名，成本可控。
- **全面性分析**：不仅报告平均引用数，还深入分析了偏差（研究方向、新颖性、机构不平等），体现了对公平性和社会影响的关注。
- **跨模型验证**：在 Claude 和 Gemini 上均取得优于 GPT 评分系统的结果，增强了方法的鲁棒性。
- **明确局限性讨论**：在附录 A.1 中坦诚了代理指标、模型选择、数据泄露等局限，并提出了未来方向（如连续评审、人机协作）。

## 8. 不足与局限
- **代理指标依赖**：主要用未来引用数衡量论文质量，但引用易受可辨识度、趋势、马太效应等影响，并非完美质量度量。论文自身承认这一点。
- **模型与数据偏见**：仅主要使用 GPT-4o mini（虽然也测试了其他模型），且 LLM 训练数据可能已包含这些会议论文，存在数据泄露风险。
- **未完全模拟人类评审过程**：仅关注决策层（排名与接受），忽略了人类评审中重要的反馈、讨论等互动环节，论文也明确指出其意图是补充而非替代。
- **偏见分析初步**：对新颖性和机构不平等的分析仅基于简单度量（最近邻距离、基尼系数），未深入探究成因或提出缓解方案。
- **计算成本**：虽然比传统评分更高效，但 3M 次 API 调用约 1350 美元，实际部署仍可能面临成本门槛。
- **实验覆盖**：仅针对 ML 领域会议，未涉及其他学科；且时间跨度有限（2023-2024），未检验长期稳定性。

（完）
