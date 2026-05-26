---
title: "EAReranker: Efficient Embedding Adequacy Assessment for Retrieval Augmented Generation"
title_zh: EAReranker：面向检索增强生成的高效嵌入充分性评估
authors: "Dongyang Zeng, Yaping Liu, Wei Zhang, Shuo Zhang, Xinwang Liu, Binxing Fang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=mzxGGzeLCL"
tags: ["query:ai"]
score: 5.0
evidence: 检索增强生成
tldr: 针对RAG系统中文档充分性评估计算量大且依赖明文的问题，本文提出EAReranker，一种基于嵌入的充分性评估框架。该框架无需访问原始文本，通过综合指标量化文档效用。实验表明在保持高效的同时显著提高了生成质量。该工作为敏感场景下的RAG优化提供了新方案。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-mzxggzelcl/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1450, \"height\": 484, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mzxggzelcl/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1310, \"height\": 402, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mzxggzelcl/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1307, \"height\": 314, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-mzxggzelcl/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1420, \"height\": 510, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mzxggzelcl/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1406, \"height\": 502, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mzxggzelcl/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1442, \"height\": 556, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mzxggzelcl/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1438, \"height\": 579, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mzxggzelcl/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 710, \"height\": 227, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mzxggzelcl/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 706, \"height\": 226, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mzxggzelcl/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 709, \"height\": 359, \"label\": \"Table\"}]"
motivation: 传统重排序方法计算开销大、依赖明文，对文档价值评估不足。
method: 提出基于嵌入的充分性评估框架，量化文档对RAG系统的效用，无需原文。
result: 在多个知识密集型任务上，生成质量优于现有重排序方法，计算效率高。
conclusion: 该方法在保护隐私的同时提升了RAG生成质量，适用于敏感场景。
---

## Abstract
With the increasing adoption of Retrieval-Augmented Generation (RAG) systems for knowledge-intensive tasks, ensuring the adequacy of retrieved documents has become critically important for generation quality. Traditional reranking approaches face three significant challenges: substantial computational overhead that scales with document length, dependency on plain text that limits application in sensitive scenarios, and insufficient assessment of document value beyond simple relevance metrics.  We propose EAReranker, an efficient embedding-based adequacy assessment framework that evaluates document utility for RAG systems without requiring access to original text content. The framework quantifies document adequacy through a comprehensive scoring methodology considering verifiability, coverage, completeness and structural aspects, providing interpretable adequacy classifications for downstream applications. EAReranker employs a Decoder-Only Transformer architecture that introduces embedding dimension expansion method and bin-aware weighted loss, designed specifically to predict adequacy directly from embedding vectors. Our comprehensive evaluation across four public benchmarks demonstrates that EAReranker achieves competitive performance with state-of-the-art plaintext rerankers while maintaining constant memory usage ($\sim$550MB) regardless of input length and processing 2-3x faster than traditional approaches. The semantic bin adequacy prediction accuracy of 92.85\% LACC@10 and 86.12\% LACC@25 demonstrates its capability to effectively filter out inadequate documents that could potentially mislead or adversely impact RAG system performance, thereby ensuring only high-utility information serves as generation context. These results establish EAReranker as an efficient and practical solution for enhancing RAG system performance through improved context selection while addressing the computational and privacy challenges of existing methods.

---

## 论文详细总结（自动生成）

## 1. 核心问题与整体含义
- **研究动机**：检索增强生成（RAG）系统在知识密集型任务中日益普及，但传统重排序方法存在三大瓶颈：计算开销随文档长度线性增长、依赖原始文本（限制敏感场景应用）、仅评估“相关性”而忽略文档对生成任务的“充分性”（如事实可靠性、覆盖完整性等）。
- **整体目标**：提出一种无需访问原始文本、仅基于嵌入向量的文档充分性评估框架（EAReranker），在保持竞争力的同时显著降低计算成本，并增强隐私保护与可解释性。

## 2. 方法论
- **核心思想**：从传统 `f(查询文本, 文档文本)→相关分数` 转变为 `M(查询嵌入, 文档嵌入)→充分性分数`，直接利用预训练嵌入模型输出的固定维度向量进行预测。
- **关键技术细节**：
  - **嵌入维度扩展**：通过独立的投影层将单个嵌入向量扩展为序列表示（含可学习的 CLS/SEP 令牌），以挖掘压缩向量中的细粒度语义。
  - **Decoder-Only Transformer**：处理扩展后的嵌入序列，输出 CLS 令牌经三层 MLP 预测充分性分数。
  - **箱感知加权损失函数**：强调语义边界附近的预测准确性，权重根据预测值与箱边界的偏差动态调整。
  - **标注流程**（算法1）：
    1. 使用多个 LLM 对查询-文档对评分（0-1区间）；
    2. 检查前4个评分一致性（容忍度0.2），若不满足则逐步添加更多模型并枚举所有4元组合，直至找到自洽子集；
    3. 对箱内分数进行二次校准：结合重排序器分数归一化后加权，增强箱内区分度。
- **公式说明**：嵌入扩展公式为 `e'_q,i = W_{q,i} e_q + b_{q,i}` 等；损失函数为 `L = (1/N) Σ w_i (s_true - s_pred)^2`，其中权重 `w_i` 基于预测与箱边界的距离计算。

## 3. 实验设计
- **数据集**：
  - 训练/测试：自行构建的100万查询-文档对（80%训练，20%测试），基于 bge-m3-data 并补充多个公开来源（FEVER、NFCorpus、TriviaQA 等）。
  - 基准评估：FEVER（事实验证）、NFCorpus（医学检索）、DuRetrieval（中文问答）、T2Ranking（中文排序）。
- **对比方法**：
  - 词法模型：BM25。
  - 嵌入相似度：Cosine 相似度（使用 gte-base、bge-m3、jina-v3、KaLM 四种嵌入器）。
  - 明文重排序器：gte-reranker-base、bge-reranker-v2-m3、jina-reranker-v2、lb-reranker-v1.0。
- **评估指标**：
  - 排名性能：NDCG@10、MRR。
  - 充分性分类：ACC25（预测误差≤0.25的比例）、LACC@25 和 LACC@10（二分类准确率，阈值0.25/0.10）。

## 4. 资源与算力
- 论文附录B.1明确说明：使用单张 NVIDIA RTX 4090（24GB VRAM），搭配 Intel Xeon Gold 6348 CPU，训练耗时约20小时（50 epoch，batch size 256，学习率1e-5）。
- 推理阶段 EAReranker 内存占用恒定约550MB，不受输入长度影响；明文重排序器最高消耗8441MB（lb-reranker-v1.0 处理128K长度时）。

## 5. 实验数量与充分性
- **实验组数**：
  - 排名性能对比（表3）：覆盖4个数据集×4种嵌入器×4种基线（BM25、4种余弦、4种明文重排序器，共约13组对比，加上 EAReranker 的4种嵌入配置）。
  - 充分性分类（表4）：4种嵌入器下的 ACC25/LACC@25/LACC@10。
  - 消融实验（表5）：移除维度扩展、箱感知损失、校准方法等3个关键组件，在 bge-m3 上验证。
  - 计算效率对比（表6）：与4种明文重排序器对比VRAM和推理时间。
  - 案例研究（表2）：展示传统分数与充分性分数的差异。
- **充分性与公平性**：
  - 实验覆盖多语言（英文+中文）、多领域（医学、事实验证、通用问答）场景。
  - 所有基线均使用官方实现或推荐配置，EAReranker 报告了标准差（附录B.6表10，5次不同随机种子）。
  - 消融实验明确量化各贡献度，验证了设计合理性。

## 6. 主要结论与发现
- EAReranker 在排名性能上接近最优明文重排序器：NDCG@10 差距仅0.54%~1.30%（表3）。
- 充分性分类准确率高：LACC@10 达92.85%（bge-m3 嵌入），能有效过滤低质量文档。
- 计算效率显著优于明文模型：推理速度2-3倍提升，内存占用恒定且远低于变长明文模型。
- 消融表明三个核心组件（维度扩展、箱感知损失、分数校准）均不可或缺，分别贡献3.70%、2.67%、1.33%的ACC25提升。

## 7. 优点
- **方法创新**：首次提出“充分性”多维度定义（可验证性、需求覆盖、证据完整性、结构适宜性），并设计语义箱标注系统，将定性概念转化为可训练的量化标签。
- **隐私/安全友好**：全程无需访问原始文本，仅利用嵌入向量，适合数据治理敏感的领域。
- **轻量高效**：4层 Decoder 架构，推理成本与文档长度解耦，便于部署在资源受限环境。
- **实验设计严谨**：采用多模型交叉验证标注，减少单模型偏差；在多个公开基准和不同嵌入器上评估，对比充分。

## 8. 不足与局限
- **标注偏差风险**：多模型 LLM 评分虽经一致性校验，但模型本身可能存在系统性偏好，尤其对边界样本（如“边际相关”与“弱相关”的区分）未必可靠。
- **经验依赖**：语义箱分割和维度整合（如四个维度的权重）基于启发式规则，缺乏理论最优性保证。
- **实验覆盖有限**：
  - 仅评估英文和中文数据集，缺乏对其他语言（如阿拉伯语、印地语）的泛化测试。
  - 未涉及极长文档（>128K tokens）或特定专业领域（如法律、生物医学）的深度评估。
  - 训练数据规模（100万对）相对较大，但标注依赖 LLM，质量可控性不足。
- **可扩展性未知**：当前仅使用单卡训练，扩展至更大模型或更高维度嵌入（如4096维）的性能、内存开销未报告。
- **潜在应用限制**：方案完全依赖外部嵌入模型的质量；若嵌入模型对某些语义特征不敏感（如反讽、隐含前提），可能影响充分性判断。

（完）
