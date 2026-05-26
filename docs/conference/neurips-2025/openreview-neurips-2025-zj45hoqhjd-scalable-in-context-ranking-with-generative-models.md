---
title: Scalable In-context Ranking with Generative Models
title_zh: 基于生成模型的可扩展上下文排序
authors: "Nilesh Gupta, Chong You, Srinadh Bhojanapalli, Sanjiv Kumar, Inderjit S Dhillon, Felix X. Yu"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=zj45hoQhjD"
tags: ["query:ai"]
score: 5.0
evidence: 上下文排序在信息检索中的应用
tldr: 上下文排序范式利用LLM直接对候选文档排序，但计算成本随上下文增长。本文发现微调后的LLM注意力具有文档间稀疏和查询文档块结构，据此设计高效注意力加速方法。在不牺牲精度的情况下，大幅降低推理开销。该工作使得ICR可应用于更大规模的检索场景。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-zj45hoqhjd/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1439, \"height\": 506, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zj45hoqhjd/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1363, \"height\": 491, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zj45hoqhjd/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1451, \"height\": 714, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zj45hoqhjd/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 579, \"height\": 330, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zj45hoqhjd/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 656, \"height\": 353, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zj45hoqhjd/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1155, \"height\": 364, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zj45hoqhjd/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 644, \"height\": 431, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-zj45hoqhjd/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1441, \"height\": 276, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zj45hoqhjd/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1433, \"height\": 467, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zj45hoqhjd/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 583, \"height\": 291, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zj45hoqhjd/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 583, \"height\": 232, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zj45hoqhjd/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 724, \"height\": 237, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zj45hoqhjd/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 727, \"height\": 246, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zj45hoqhjd/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 722, \"height\": 232, \"label\": \"Table\"}]"
motivation: 上下文排序有效但计算量随候选列表二次增长，难以扩展。
method: 识别注意力中的块稀疏和查询-文档块结构，设计稀疏注意力计算方法。
result: 在多个IR基准上，速度提升10倍以上，同时保持甚至提升排序精度。
conclusion: 揭示了ICR中注意力结构的可优化性，促进了该范式的实际应用。
---

## Abstract
In-context Ranking (ICR) is an emerging paradigm for Information Retrieval (IR), which leverages contextual understanding of LLMs by directly incorporating the task description, candidate documents, and the query into the model's input prompt and tasking the LLM to identify relevant document(s). While it is effective, efficiency is a significant challenge in this paradigm, especially as the candidate list grows due to quadratic/super-linear scaling of attention operation with context length. To this end, this paper first identifies inherent and exploitable structures in the attention of LLMs finetuned for ICR: (1) inter-document block sparsity: attention is dense within each document block but sparse across different documents in the context; and (2) query-document block relevance: the attention scores from certain query tokens to a document block in middle layers strongly correlate with that document's actual relevance. Motivated by these observations, we introduce BlockRank (Blockwise In-context Ranking), a novel method that adapts the attention operation in an LLM by (a) architecturally enforcing the observed inter-document block sparsity, reducing attention complexity from quadratic to linear without loss in performance, and (b) optimizing query-document block relevance for true relevant documents during fine-tuning using an auxiliary contrastive training objective, improving retrieval in attention. Experiments on BEIR, MSMarco and NQ with Mistral-7B demonstrate that BlockRank Mistral matches or outperforms existing SOTA listwise rankers and controlled fine-tuned baseline while being significantly more efficient at inference (4.7x for 100 MSMarco documents in context) and scaling gracefully to long-context shortlists, around 500 documents in-context (approximately 100K context length) within a second, presenting a scalable and effective solution for ICR.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：In-context Ranking (ICR) 利用 LLM 直接在输入提示中处理查询和候选文档列表进行排序，但效率严重受限于注意力机制的二次复杂度——随着候选文档数量增长，推理成本急剧上升。
- **研究背景**：现有方法通常将 LLM 视为黑盒，未充分利用 ICR 任务的结构（提示由共享指令、多个独立文档和查询组成），导致计算冗余。
- **整体含义**：本文通过揭示 LLM 微调后注意力中存在的固有结构（块稀疏性、查询-文档相关性），设计出 **BlockRank** 方法，在不牺牲排序质量的前提下将注意力复杂度从二次降至线性，使 ICR 在长上下文场景下变得可扩展，推动该范式向实际应用迈进。

### 2. 论文提出的方法论
- **核心思想**：强制利用 ICR 任务的结构化稀疏注意力 + 显式优化内部注意力信号以实现高效推理。
- **关键技术细节**：
  - **块状结构化注意力**：
    - 将提示分割为指令段、文档段、查询段。
    - 文档 token 仅关注本段 + 指令段；查询 token 关注全提示；指令 token 内部因果注意力。
    - 采用 **置换不变位置嵌入**：文档段共享相同的局部位置编码（始于指令末尾），查询段使用大偏移量（如8192），消除绝对位置偏差。
  - **辅助注意力损失 (Laux)**：
    - 选择中间层（如第20层）的“信号载体”查询 token（如“:”、“['”），计算其对各文档的注意力得分。
    - 使用 InfoNCE 对比损失，鼓励相关文档得分高于无关文档。
    - 总损失：Ltotal = L_NTP + λ Laux，λ=0.1。
  - **基于注意力的高效推理**：
    - 仅需部分前向传播到中间层，从信号 token 的注意力得分中直接获取相关文档 ID，无需自回归解码。
- **公式/算法流程**（文字说明）：
  1. 对输入进行分段、分块（固定长度 Lchunk）。
  2. 逐层执行上述结构化注意力：文档块与指令块并行计算，查询块最后聚合。
  3. 训练时：同时计算标准 NTP 损失（在最终隐藏层）和中间层 Laux。
  4. 推理时：前向传播至层 l*，计算信号 token 在文档 token 上的注意力得分，取最高分的文档 ID 为输出。

### 3. 实验设计
- **数据集与场景**：
  - **零样本泛化**：BEIR 基准的11个数据集（Climate-FEVER, DB-Pedia, FEVER, FiQA, HotpotQA, MSMarco, NF-Corpus, NQ, Sci-docs, Sci-fact, Trec-COVID），使用 Contriever 检索的前100候选。
  - **域内控制实验**：MSMarco 段落排名和 Natural Questions (NQ)，候选列表由 sentence transformer 检索（大小从10到500可变）。
- **Benchmark**：对比方法包括：
  - 传统模型：BM25, GTR, ColBERTv2, Sentence-Transformers
  - 跨编码器：monoBERT, monoT5
  - 现有列表式重排序器：RankVicuna, RankZephyr, FIRST
  - 基准微调 LLM：Full-FT Mistral-7B（完整因果注意力 + NTP 损失）
  - 零样本 LLM：Mistral-7B-Instruct, Gemini-2.0-flash
- **评估指标**：nDCG@10 (BEIR)、Precision@1、MRR@10、推理延迟 (wall-clock time per query)。

### 4. 资源与算力
- **训练与推理硬件**：Google Cloud TPUs，具体为8 chip v6e 配置。
- **训练细节**：Adafactor 优化器，学习率 3×10⁻⁷，全局 batch size 32，训练 1 epoch（线性预热+余弦衰减）。
- **未明确说明**：训练时长（小时数）、总计算量（TFLOPS-days）或具体 TPU 型号未在文中提供。

### 5. 实验数量与充分性
- **实验组数**：约 4-5 组主要实验（BEIR 零样本、MSMarco/NQ 域内、标度性分析、消融实验、跨数据集泛化）。
- **消融实验**：训练损失（NTP vs aux）、推理方法（解码 vs 注意力）、位置嵌入、查询前缀、中间层选择等。
- **充分性**：覆盖了主要检索基准和多种基线，并验证了方法的可扩展性。但论文提到未提供误差条或统计显著性检验，因此结论的稳定性需进一步确认。总体而言，实验设计客观、公平，对比方法选择合理，但缺少多次运行的可信度声明。

### 6. 论文的主要结论与发现
- BlockRank (Mistral-7B) 在 BEIR 11个数据集上平均 nDCG@10 达 54.8，超过 FIRST（54.3）、RankZephyr（53.7）等 SOTA 列表式排序器。
- 在 MSMarco 域内测试中，BlockRank 的 P@1（29.1）和 MRR@10（42.0）均高于 Full-FT Mistral（28.7/38.4）。
- **效率优势显著**：当候选文档 N=100 时，推理加速 4.7 倍；N=500 时仍可在 1.15 秒内完成，而 Full-FT 的 P@1 已严重下降。
- 基于注意力的推理（利用中间层注意力得分）优于自动回归解码，尤其在 MRR@10 上表现更佳。

### 7. 优点
- **方法创新性强**：首次系统分析 ICR 中 LLM 注意力的结构特性，并设计出任务驱动的稀疏注意力 + 辅助对比损失，实现了高效率与高质量的统一。
- **实践价值高**：BlockRank 使 LLM 作为重排序器能在实际部署中处理数百候选文档，延迟毫秒级，具备强可扩展性。
- **实验全面**：涵盖了零样本泛化和域内控制两种典型场景，验证了模型在不同检索首步模型下的鲁棒性。
- **开源代码**：提供 GitHub 仓库（BlockRank），促进可复现性。

### 8. 不足与局限
- **架构局限性**：当前分析及方法仅基于 Mistral-7B 模型，在其他架构（如 Llama, Gemma）上的适用性未知。
- **跨任务泛化仍有限**：尽管 BEIR 上表现优秀，但跨数据集测试（如 MSMarco→NQ 仅 62.0 P@1）显示迁移能力较弱，需更多研究提升可迁移性。
- **实验细节缺失**：未报告多次运行的均值和方差，也未提供统计显著性检验，削弱了结果的可靠性。
- **计算资源披露不足**：未给出具体训练时长或总计算成本，不利于重复成本和能效对比。
- **潜在偏差风险**：注意力信号“信号载体” token 的选择（“:”、“['”）依赖于特定提示模板，若提示结构变化可能失效。

（完）
