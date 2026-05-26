---
title: "HashAttention: Semantic Sparsity for Faster Inference"
title_zh: HashAttention：基于语义稀疏性的快速推理方法
authors: "Aditya Desai, Shuo Yang, Alejandro Cuadron, Matei Zaharia, Joseph E. Gonzalez, Ion Stoica"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=Em2oaXd8Dc"
tags: ["query:ai"]
score: 7.0
evidence: ICML 2025关于AI系统高效注意力机制的论文
tldr: 该论文将注意力中关键令牌识别转化为最大内积搜索问题，提出HashAttention方法。通过将查询和键映射到哈希空间，实现GPU友好的稀疏注意力计算。实验表明在不损失质量的情况下显著加速长上下文推理，为大型语言模型高效部署提供了实用方案。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-em2oaxd8dc/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 826, \"height\": 513, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-em2oaxd8dc/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1363, \"height\": 587, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-em2oaxd8dc/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1780, \"height\": 412, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-em2oaxd8dc/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 805, \"height\": 509, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-em2oaxd8dc/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1420, \"height\": 569, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-em2oaxd8dc/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 681, \"height\": 369, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-em2oaxd8dc/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 682, \"height\": 396, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-em2oaxd8dc/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 679, \"height\": 371, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-em2oaxd8dc/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1773, \"height\": 701, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-em2oaxd8dc/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1758, \"height\": 199, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-em2oaxd8dc/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1604, \"height\": 246, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-em2oaxd8dc/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1768, \"height\": 194, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-em2oaxd8dc/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 897, \"height\": 124, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-em2oaxd8dc/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1181, \"height\": 501, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-em2oaxd8dc/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1298, \"height\": 460, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-em2oaxd8dc/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1801, \"height\": 461, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-em2oaxd8dc/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 918, \"height\": 195, \"label\": \"Table\"}]"
motivation: 长上下文注意力计算成为AI系统瓶颈，现有稀疏方法牺牲质量或资源。
method: 将关键令牌识别视为推荐问题，使用哈希方法实现快速最大内积搜索。
result: 在不损失质量的情况下显著加速注意力计算。
conclusion: HashAttention为长上下文AI模型提供了高效且无损的加速方法。
---

## Abstract
Leveraging long contexts is crucial for advanced AI systems, but attention computation poses a scalability challenge. While scaled dot-product attention (SDPA) exhibits token sparsity, i.e. only a few pivotal tokens significantly contribute to output, exploiting this sparsity remains challenging. Existing methods either suffer from quality degradation or require substantial additional resources. We show that identifying pivotal tokens is a Maximum Inner Product Search (MIPS) problem. However, existing MIPS solutions are not well-suited for SDPA, as they are not GPU-friendly and often underperform due to the separated query and key distributions. This paper introduces HashAttention, framing pivotal token identification as a recommendation problem. Given a query, HashAttention encodes keys and queries in Hamming space, capturing the required semantic similarity, using learned mapping functions. HashAttention efficiently identifies pivotal tokens for a given query using bitwise operations and computes attention using only these tokens, improving the overall attention efficiency. Trained on generic data, HashAttention reduces tokens used by up to $16\times$ with minimal quality loss, requiring only 32 bits of auxiliary memory per token. Sparsity can be further improved to $32\times$ through task-specific fine-tuning. 
On A100 GPU, at $32\times$ sparsity, incorporating HashAttention reduces attention latency by up to $4.3\times$ in GPT-FAST and $2.54\times$ in FlashDecode, and achieves up to $3.12\times$ higher throughput for GPT-FAST.

---

## 论文详细总结（自动生成）

# HashAttention: 基于语义稀疏性的快速推理方法 —— 详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **背景**：现代大型语言模型（LLMs）需要处理长上下文（如长文档、多轮对话），但其中核心的缩放点积注意力（SDPA）的计算复杂度随上下文长度线性增长，成为瓶颈。例如，Llama-3.1-8B 模型在 512K 上下文时 KV 缓存达 64 GB，导致解码极慢。
- **关键观察**：SDPA 天然存在“令牌稀疏性”——只有少数关键令牌（pivotal tokens）对输出贡献显著。若能高效识别这些关键令牌，则可大幅降低计算量。
- **现有方法局限**：
  - 固定稀疏模式（如 StreamingLLM）忽略动态性，质量下降。
  - KV 缓存丢弃策略（如 H2O、ScissorHands）无法恢复被丢弃的令牌，多轮对话等场景失效。
  - 动态稀疏方法（如 Double Sparsity、Quest、InfLLM）基于启发式或部分计算，召回率低或需要大量辅助内存。
- **核心问题**：如何在不牺牲模型质量和仅使用极少辅助内存的前提下，在 GPU 上高效、准确地识别关键令牌？

## 2. 方法论：核心思想、关键技术细节

### 2.1 整体框架

- 将稀疏注意力视为“推荐系统”问题：Key-Value 对为“物品”，查询为“用户”，目标是选出与查询最相关的物品。
- 证明识别关键令牌等价于**最大内积搜索（MIPS）**问题（Lemma 4.2），进而可约化为**余弦相似度搜索**。

### 2.2 HashAttention 核心技术

- **学习哈希映射**：为每个注意力头学习两个独立的映射函数：
  - `φ_kv: R^d → {0,1}^b` （对键/值，实验中仅使用键）
  - `φ_q: R^d → {0,1}^b` （对查询）
  - 采用小 MLP（如 128x128-128x128-128x32）配合 tanh 激活（训练时替代 sign 以保持可微）将输入映射到 b 位汉明空间。
- **位打包与高效计算**：
  - 训练时将键的位签名（如 32 位整数）预计算并缓存（仅需每令牌每头 32 位辅助内存）。
  - 解码时，将查询也映射为位签名，通过按位异或（XOR）和 bitcount 计算汉明距离，快速找到最相近的令牌。
  - 使用 vLLM 的页面注意力框架（页大小=1），无需物理搬移令牌，利用索引直接选择性计算注意力。

### 2.3 训练策略

- **目标**：使哈希签名逼近“隔离令牌贡献得分”（Lemma 4.1：贡献 ∝ 注意力分数 × 值向量范数）。
- **损失函数**：二值交叉熵（BCE），类权重根据上下文长度动态调整（公式：`class1-weight = α + β / context_length`）。
- **训练数据**：通用数据（OpenWebText 拼接成长序列）预训练；任务特定微调（HashAttention*）可进一步提升。
- **训练方式**：在 LLM 推理模式下，按块处理，每块后对所有注意力头独立一步训练。

## 3. 实验设计

### 3.1 数据集与基准

- **质量评估**：
  - **LongBench**（多任务双语，包括多文档 QA、摘要、合成任务等）
  - **RULER@16K**（长上下文检索与推理）
  - 中文子集（评估跨语言泛化）
- **效率评估**：
  - **GPT-FAST**（PyTorch 轻量推理框架）
  - **FlashDecode**（基于 FlashAttention 的序列并行版本）

### 3.2 对比方法

- 固定稀疏：StreamingLLM
- 丢弃策略：H2O
- 动态稀疏：InfLLM、Double Sparsity（DS）、Quest
- 理想上界：Oracle（精确 top-k，使用全部 token 注意力分数）

所有方法均保持前 128 个 token 和最近 128 个 token 为固定 sink + 局部上下文，公平对比。辅助内存统一控制在 32 bits/token/head（PTPA），除非特别说明。

## 4. 资源与算力

- **GPU 型号**：A100（文中明确提及用于效率实验）
- **训练细节**：论文未报告训练 HashAttention 的具体 GPU 数量和训练时长，仅提及“在通用数据上训练，使用 Adam 优化器”。因此算力开销未量化，但指出对于每个模型（如 Llama-3.1-8B）需要训练一次，类似于 Double Sparsity 的校准过程。
- **推理算力需求**：3 层 MLP 映射，计算量较小，但尚未给出完整的 FLOPs 分析。

## 5. 实验数量与充分性

论文进行了多组实验，整体较为充分：

| 实验类型 | 内容 | 充分性评价 |
|---------|------|-----------|
| **Head-to-head 对比**（Table 1） | LongBench 每类选 1 子集，175 样本，固定 budget=512，比较 8 种方法 | 覆盖主要类别，样本量适中，但未全覆盖所有子集。 |
| **Pareto 曲线**（Figure 3） | 4 个 LongBench 子集 + 6 个 RULER 子集，变稀疏度对比 DS、Quest | 给出不同稀疏度下的质量-效率折中，有说服力。 |
| **全基准测试**（Table 2, 3） | 16× 稀疏下完整 LongBench 和 RULER 性能 | 覆盖全部 16 个任务，结果稳定。 |
| **微基准测试**（Figure 5） | 不同上下文长度下 top-32 召回率 | 直接验证方法有效性。 |
| **效率实验**（Figure 4） | GPT-FAST 和 FlashDecode 中延迟和吞吐量对比 | 结合两个主流框架，结果可靠。 |
| **消融实验**（Section 5.3） | 位宽、LSH vs 学习哈希、余弦相似度变化、SCORE 延迟对比等 | 多维度分析，全面且有针对性。 |

**公平性**：所有基线使用相同 sink+local 策略、相同 token budget，并尽可能优化其超参数。但注意 Double Sparsity 的效率实验“排除量化/反量化的时间”，可能高估其性能。

## 6. 主要结论与发现

1. **质量保持**：HashAttention 在 16× 稀疏下，LongBench 平均分下降 <1 分（48.78→48.00），RULER 下降约 1.13；32× 稀疏下通过任务微调可接近全模型。
2. **效率提升**：32× 稀疏时，GPT-FAST 注意力延迟下降 4.3×，FlashDecode 下降 2.54×，端到端吞吐提升最高 3.12×。
3. **辅助内存优势**：仅需 32 bits/token/head，比同类方法（DS 需 64-128 bits）更节省。
4. **令牌级别稀疏可行**：尽管传统认为块稀疏更高效，HashAttention 结合页面注意力（page size=1）实现高效聚集。
5. **训练无关泛化**：通用数据训练的 HashAttention 可推广到中文、代码等任务；任务微调可进一步压缩。

## 7. 优点：方法与实验亮点

- **理论扎实**：将稀疏注意力与 MIPS 问题严格连接，并通过不对称变换（Lemma 4.2）给出可解释的哈希方向。
- **GPU 友好**：位运算与页面注意力设计高效利用 GPU 缓存行，避免 CPU 卸载（对比 RetrievalAttention）。
- **训练数据效率**：仅需通用数据预训练即可获得核心能力，微调成本低。
- **实验设计全面**：性能、效率、消融多维度覆盖，且对比基线最新（2024 年）。
- **结果开放**：代码开源，便于复现与集成。

## 8. 不足与局限

- **需要预训练**：尽管训练一次，但相比于完全无需训练的方法（如 StreamingLLM）仍有一定迁移成本，且在不同模型上需重新训练。
- **分布外敏感性**：训练基于英文数据，中文任务上性能下降较多（约 2.66 分），跨语言泛化能力不足。
- **极长上下文未评估**：论文仅测试到 32K 上下文（LongBench）和 16K（RULER），未涉及 128K/1M 场景（如 RULER@128K 或 Needle-in-Haystack），而 KV 缓存 offload 到 CPU 时的表现未知。
- **效率实验粒度**：SCORE 阶段 MLP 计算在小上下文下占主导，实际收益体现在 8K+；且只报告了 batch=1 的结果，缺少多 batch 吞吐分析。
- **辅助内存隐含假设**：32 bits/token/head 对 8B 模型（32 heads）相当于每 token 额外 128 字节，对于极端长上下文仍可能内存压力增大。
- **消融中 LSH 对比不完整**：仅对比了 LSH 作为哈希函数，但未与 MagicPig 等完整系统比较端到端质量 vs 效率。

（完）
