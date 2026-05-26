---
title: "KARMA: Leveraging Multi-Agent LLMs for Automated Knowledge Graph Enrichment"
title_zh: KARMA：利用多智能体大语言模型自动化知识图谱增强
authors: "Yuxing Lu, Wei Wu, Xukai Zhao, Rui Peng, Jinzhuo Wang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=k0wyi4cOGy"
tags: ["query:ai"]
score: 6.0
evidence: 多智能体大语言模型用于知识图谱增强，人工智能研究
tldr: 知识图谱的维护依赖人工，难以跟上科学文献增长。本文提出KARMA框架，利用九个协作的大语言模型智能体自动完成实体发现、关系抽取、模式对齐和冲突消解，迭代解析文档并整合到现有图中。在1200篇PubMed文章上的实验表明，KARMA显著提升了知识图谱的覆盖率和更新效率。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-k0wyi4cogy/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1164, \"height\": 291, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-k0wyi4cogy/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1447, \"height\": 839, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-k0wyi4cogy/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1177, \"height\": 445, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-k0wyi4cogy/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1389, \"height\": 469, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-k0wyi4cogy/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1391, \"height\": 471, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-k0wyi4cogy/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1389, \"height\": 469, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-k0wyi4cogy/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1465, \"height\": 731, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-k0wyi4cogy/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1453, \"height\": 682, \"label\": \"Table\"}]"
motivation: 手动维护知识图谱难以应对科学文献的快速增长。
method: 开发多智能体大语言模型框架，自动化实体发现、关系抽取、模式对齐和冲突消解。
result: 在PubMed文献上验证了知识图谱覆盖率和更新效率的提升。
conclusion: 多智能体协作能有效自动化知识图谱的增强过程。
---

## Abstract
Maintaining comprehensive and up-to-date knowledge graphs (KGs) is critical for modern AI systems, but manual curation struggles to scale with the rapid growth of scientific literature. This paper presents KARMA, a novel framework employing multi-agent large language models (LLMs) to automate KG enrichment through structured analysis of unstructured text. Our approach employs nine collaborative agents, spanning entity discovery, relation extraction, schema alignment, and conflict resolution that iteratively parse documents, verify extracted knowledge, and integrate it into existing graph structures while adhering to domain-specific schema. Experiments on 1,200 PubMed articles from three different domains demonstrate the effectiveness of KARMA in knowledge graph enrichment, with the identification of up to 38,230 new entities while achieving 83.1\% LLM-verified correctness and reducing conflict edges by 18.6\% through multi-layer assessments.

---

## 论文详细总结（自动生成）

```markdown
### 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：知识图谱（KG）的维护对于现代AI系统至关重要，但手动审核难以跟上科学文献的指数级增长（每年超过700万篇文章）。传统NLP方法处理领域特定术语和上下文依赖关系能力有限；现有LLM方法存在幻觉、模式不一致和计算成本高等问题。
- **整体含义**：本文提出**KARMA**框架，利用多智能体大语言模型自动化知识图谱增强，通过结构化分析非结构化文本，实现从文献到图谱的端到端更新，提升可扩展性和准确性。

### 2. 方法论：核心思想、关键技术细节

- **核心思想**：将知识图谱增强任务分解为多个专门的子任务，由九个协作的LLM智能体分阶段处理，包括文档摄入、文本分段、摘要生成、实体提取、关系提取、模式对齐、冲突解决和最终评估，最终将验证后的三元组整合到现有知识图谱中。
- **关键技术细节**：
  - **摄入智能体 (IA)**：标准化文档格式并提取元数据。
  - **读取智能体 (RA)**：将文本分割为相关片段，并根据领域特定阈值δ过滤不相关片段（式3）。
  - **摘要智能体 (SA)**：将每个片段浓缩为保留关键实体的短摘要（式4），减少下游计算开销。
  - **实体提取智能体 (EEA)**：基于LLM进行命名实体识别，并通过词典/本体过滤（式5）；随后将实体提及映射到规范表示，通过嵌入空间中最小距离匹配（式6）。
  - **关系提取智能体 (REA)**：对每对实体进行关系分类，输出多标签概率分布（式7），并设定阈值θr提取三元组（式8）。
  - **模式对齐智能体 (SAA)**：对新实体或关系进行类型分类，映射到KG现有模式，否则标记为候选新增（式9）。
  - **冲突解决智能体 (CRA)**：检测新三元组与现有KG的逻辑矛盾（式10），通过LLM辩论决定采纳、丢弃或人工审核（式11）。
  - **评估智能体 (EA)**：对每个三元组聚合置信度、清晰度和相关性三个分数（式12-14），通过加权逻辑函数计算，最终根据平均分阈值Θ决定是否整合（式15）。
- **算法流程**：文档 → IA → RA（分段+过滤）→ SA（摘要）→ EEA（实体提取+归一化）→ REA（关系提取）→ SAA（模式对齐）→ CRA（冲突解决）→ EA（评估）→ 整合至KG。

### 3. 实验设计：数据集、基准、对比方法

- **数据集**：从PubMed收集三个领域的科学文献：**基因组学**（720篇）、**蛋白质组学**（360篇）、**代谢组学**（120篇），共1200篇文章。
- **基准**：与**单智能体方法**（一个LLM直接提取所有三元组）进行对比。
- **对比方法**：使用三种LLM作为骨干：**GLM-4**（9B参数，开源）、**GPT-4o**（专有，多模态）、**DeepSeek-v3**（37B激活参数MoE，开源）。每个智能体共享相同的LLM骨干。评估全部基于DeepSeek-v3作为判官。
- **评估指标**：
  - **核心指标**：平均置信度 (M_Con↑)、平均清晰度 (M_Cla↑)、平均相关性 (M_Rel↑)。
  - **图统计**：覆盖增益 (ΔCov↑，新实体数)、连接增益 (ΔCon↑，节点度增加)。
  - **质量指标**：冲突比 (R_CR↓，被冲突解决移除的边比例)、LLM正确性 (R_LC↑)、QA一致性 (C_QA↑，基于图谱的问答正确率)、人类评估 (R_HE↑，两位专家打分，0-1尺度)。

### 4. 资源与算力

- **未明确说明**：论文未提及所使用的GPU型号、数量或训练时间。所有实验通过调用LLM的API完成（包括GLM-4、GPT-4o、DeepSeek-v3），仅在图3中给出了prompt tokens、completion tokens和处理时间的统计分布，反映了计算开销但无硬件细节。

### 5. 实验数量与充分性

- **主要实验**：在三个领域上，每个领域测试三种LLM骨干+单智能体基线，共4×3=12组实验，报告所有指标（表1），并附有示例三元组（附录C）。
- **消融实验**：系统性地去除摘要智能体、冲突解决智能体和评估智能体，在三个领域上各做一组（共9组），评估对质量指标的影响（表2）。
- **充分性评价**：实验覆盖了不同规模的领域（720篇、360篇、120篇），消融实验验证了各组件的贡献。但仅测试了三种LLM，且所有LLM评估使用同一个判官模型（DeepSeek-v3），可能存在偏见。人类评估仅有两位专家，样本量有限。总体设计较为充分，但客观性上仍有提升空间。

### 6. 主要结论与发现

- KARMA能显著扩展知识图谱：在基因组学中，DeepSeek-v3识别**38,230**个新实体，覆盖增益是单智能体的8.7倍；在三个领域中，LLM验证的正确性最高达**83.1%**，冲突边减少**18.6%**。
- **不同骨干表现分化**：DeepSeek-v3在覆盖增益上领先（比GPT-4o高3.9倍）；GPT-4o在正确性上最优（基因组学88.0%）；GLM-4在代谢组学清晰度和蛋白质组学QA一致性上表现突出。
- **多智能体架构优于单智能体**：在所有领域，单智能体的LLM正确性和人类评估得分均低于任何完整多智能体配置。
- **消融实验重要性排序**：移除冲突解决智能体导致正确性下降最多（基因组学从83.1%降至79.0%）；移除摘要智能体导致QA一致性大幅下降（基因组学从0.612降至0.472）。所有组件均不可或缺。

### 7. 优点

- **方法创新**：多智能体协作将复杂任务解耦，引入交叉验证和辩论机制减少幻觉，提升可靠性和一致性。
- **模块化设计**：易于扩展新领域、新本体或智能体，具有较强适应性。
- **领域自适应提示**：每个智能体使用专门提示，适应不同科学领域的术语和关系。
- **评估全面性**：采用多维指标（核心、图结构、质量），包括LLM验证、QA测试和人类评估，从不同角度衡量效果。

### 8. 不足与局限

- **评估依赖LLM**：主要质量指标（R_LC、C_QA）和冲突解决的判官均为LLM（DeepSeek-v3），可能引入自身偏见，缺乏大规模人类专家直接验证。**论文自身承认**这一局限。
- **领域差异未完全解决**：代谢组学性能相对较低（QA一致性比基因组学低12.4%），表明对稀疏关系处理能力不足。
- **实验覆盖有限**：仅测试三种LLM，未包括更广泛的开源模型（如LLaMA系列）。且所有实验基于PubMed生物医学领域，通用性和跨领域泛化能力未验证。
- **计算成本**：虽提供token和时间数据，但未给出完整GPU算力需求，实际部署成本不透明。
- **未见代码/数据开源**：论文称代码已存于补充材料，但当前未提供，复现存在困难。

（完）
```
