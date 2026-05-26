---
title: Iterative Self-Incentivization Empowers Large Language Models as Agentic Searchers
title_zh: 迭代自我激励赋能大语言模型成为智能搜索体
authors: "Zhengliang Shi, Lingyong Yan, Dawei Yin, Suzan Verberne, Maarten de Rijke, Zhaochun Ren"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=s9NkfkUuEr"
tags: ["query:ai"]
score: 6.0
evidence: 大语言模型智能搜索框架，与人工智能研究论文相关
tldr: 现有大语言模型在复杂多跳查询中难以准确获取知识，且常受无关检索内容干扰。本文提出ExSearch框架，让大语言模型通过自我激励机制在推理过程中主动决定检索内容、触发外部检索器并提取细粒度证据，以支持逐步推理。该方法采用广义期望算法实现自我激励，实验表明其显著提升了多跳问答的准确性，为智能检索提供了新范式。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-s9nkfkuuer/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1423, \"height\": 537, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-s9nkfkuuer/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1438, \"height\": 378, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-s9nkfkuuer/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1417, \"height\": 709, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-s9nkfkuuer/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1427, \"height\": 341, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-s9nkfkuuer/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 797, \"height\": 398, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-s9nkfkuuer/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 732, \"height\": 405, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-s9nkfkuuer/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1447, \"height\": 697, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-s9nkfkuuer/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1430, \"height\": 342, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-s9nkfkuuer/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1448, \"height\": 692, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-s9nkfkuuer/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1452, \"height\": 1286, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-s9nkfkuuer/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1451, \"height\": 1286, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-s9nkfkuuer/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1453, \"height\": 535, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-s9nkfkuuer/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1453, \"height\": 1224, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-s9nkfkuuer/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 734, \"height\": 359, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-s9nkfkuuer/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 714, \"height\": 358, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-s9nkfkuuer/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1469, \"height\": 536, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-s9nkfkuuer/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1368, \"height\": 296, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-s9nkfkuuer/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1452, \"height\": 1469, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-s9nkfkuuer/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1407, \"height\": 388, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-s9nkfkuuer/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1451, \"height\": 565, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-s9nkfkuuer/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1153, \"height\": 135, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-s9nkfkuuer/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1451, \"height\": 314, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-s9nkfkuuer/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1477, \"height\": 2327, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-s9nkfkuuer/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1464, \"height\": 515, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-s9nkfkuuer/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1464, \"height\": 727, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-s9nkfkuuer/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1450, \"height\": 620, \"label\": \"Table\"}]"
motivation: 解决大语言模型在复杂多跳查询中难以准确获取知识且受无关内容干扰的问题。
method: 提出ExSearch框架，通过自我激励过程让大语言模型在推理中主动决策检索内容并提取证据。
result: 实验证明有效提升了多跳问答的准确性。
conclusion: 自我激励机制能显著增强大语言模型作为智能搜索体的能力。
---

## Abstract
Large language models (LLMs) have been widely integrated into information retrieval to advance traditional techniques. However, effectively enabling LLMs to seek accurate knowledge in complex tasks remains a challenge due to the complexity of multi-hop queries as well as the irrelevant retrieved content. To address these limitations, we propose ExSearch, an agentic search framework, where the LLM learns to retrieve useful information as the reasoning unfolds through a self-incentivized process. At each step, the LLM decides what to retrieve (thinking), triggers an external retriever (search), and extracts fine-grained evidence (recording) to support next-step reasoning.  To enable LLM with this capability, we adopts a Generalized Expectation-Maximization algorithm. In the E-step, the LLM generates multiple search trajectories and assigns an importance weight to each; the M-step trains the LLM on them with a re-weighted loss function. This creates a self-incentivized loop, where the LLM iteratively learns from its own generated data, progressively improving itself for search. We further theoretically analyze this training process, establishing convergence guarantees. Extensive experiments on four knowledge-intensive benchmarks show that ExSearchS substantially outperforms baselines, e.g., +7.8% improvement on exact match score. Motivated by these promising results, we introduce ExSearch-Zoo, an extension that extends our method to broader scenarios, to facilitate future work.

---

## 论文详细总结（自动生成）

# 论文结构化总结

## 1. 核心问题与整体含义（研究动机与背景）

- **核心问题**：大语言模型（LLMs）在复杂多跳查询（multi-hop queries）中难以准确获取知识，且常受检索返回的无关内容干扰。现有方法通常将信息检索流水线（如查询分解、文档重排、知识提取）级联起来，并独立训练各阶段，但端到端监督对齐不足。
- **整体含义**：本文旨在让LLM能够像智能搜索体（agentic searcher）一样，主动在推理过程中动态决策检索什么、如何检索，并自我激励地提升检索-推理能力，从而更准确地在知识密集型任务中寻求知识。

## 2. 方法论

### 核心思想
- 提出 **ExSearch** 框架，将LLM建模为一个具备细粒度推理与搜索能力的智能体，通过 **自我激励** 过程学习如何搜索和推理。
- 将搜索轨迹（search trajectory）视为隐变量，采用 **广义期望最大化（GEM）算法** 进行训练。

### 关键技术细节
- **三个核心动作**：
  - **thinking**：基于当前搜索轨迹生成子查询（sub-query）。
  - **search**：触发外部检索器（如ColBERTv2.0）获取top-K文档。
  - **recording**：从检索文档中提取细粒度证据以支持下一步推理。
- **搜索轨迹建模**：形式化为序列 \( z = \{(x_i, d_i, e_i) \mid i \in [|z|]\} \)，联合似然为 \( p(z|x;\theta) = \prod_i p(x_i|x,z_{<i};\theta) \cdot p(e_i|x_i,R(x_i);\theta) \)。
- **学习目标**：最大化边际对数似然 \( \log p(y|x;\theta) \)，引入变分ELBO。
- **E-step（轨迹探索）**：由当前LLM采样多条候选轨迹，并为每条轨迹计算重要性权重 \( w(z) \propto p(y|x,z;\theta_t) \)，即该轨迹支持正确答案的似然。
- **M-step（重加权轨迹学习）**：用加权损失函数 \( w(z) \log p(y,z|x;\theta) \) 更新LLM参数，包含两项：学习推理（LR）和学习回答（LA）。
- **训练算法**：伪代码见Algorithm 1，迭代进行E-step和M-step，直到收敛。
- **理论分析**：证明了训练目标非递减且上界有界，使用单调收敛定理保证收敛。

## 3. 实验设计

### 数据集与场景
- **四个知识密集型基准**：Natural Questions (NQ)、HotpotQA、MuSiQue、2WikiMultihopQA。
- **评价指标**：KILT框架下的F1、Exact Match (EM)、Accuracy (Acc)。

### 对比方法
- **无检索直接推理**：DeepSeek-R1、GPT-4o、GPT-3.5、Qwen2.5、Llama-3.3-70B、Mistral-8x7B、QwQ-32B等。
- **高级RAG**：RankRAG、ChatQA、Recomp、RetRobust、InstructRAG、RAG-DDR等。
- **迭代RAG**：GenGround、DSPy、SearChain、Iter-RetGen、Verify-and-Edit、Gen-Ret-Gen、Search-o1、Search-R1、Self-RAG等。

### 实现细节
- 检索器：ColBERTv2.0，使用2018年12月的Wikipedia段落语料库。
- 冷启动：使用1000个伪示例对LLM进行微调，使其具备基本的think-search-record模式。
- 训练超参数：学习率2×10⁻⁶，DeepSpeed ZeRO 3，batch size根据模型大小调整（3B/7B/8B：4，24B：2），序列长度8192 tokens，5个训练迭代，梯度累积16步。

## 4. 资源与算力

- 论文未明确说明使用的GPU型号、数量、总训练时长，仅提及使用DeepSpeed ZeRO 3进行高效分布式优化。
- 冷启动数据收集：使用GPT-4o生成1000个伪示例，总成本约$20（输入$12.73 + 输出$7.30），平均每个示例$0.02。
- 实验型号包括：Qwen-2.5-3B/7B、Llama-3.2-3B/3.1-8B、Mistral-7B/24B，均可在HuggingFace上获取。

## 5. 实验数量与充分性

- **实验组丰富**：
  - 总体对比（Table 1）：涵盖三大类共约20种基线方法，在四个数据集上报告F1、EM、Acc。
  - 检索性能对比（Table 2）：Recall@3/5与多种重排序基线对比。
  - 消融实验（Table 3）：移除thinking、search、recording、权重w(z)四个组件，在两个数据集上验证。
  - 训练收敛分析（Figure 3, 7）：展示5个迭代的训练集/验证集性能变化。
  - 冷启动数据量分析（Figure 4, 8-10）：K=0到1000的多种设置。
  - 扩展场景（ExSearch-Zoo）：不同骨干模型（Table 9）、扩展重排序动作（Figure 5, 11）。
  - 人类评估（Table 8）：100个随机样本，由3名评估者判断，Kappa=0.771。
  - 案例分析（附录F.3）：提供成功和失败实例。
- **充分性与客观性**：覆盖主流的RAG和推理基线，消融设计完整，但未提供统计显著性检验（如误差棒），论文对此有说明“No”但认为结果稳定。

## 6. 主要结论与发现

- ExSearch在四个数据集上显著超越所有强基线，平均F1提升显著，例如在HotpotQA上达到62.59 F1（7B模型），远优于RankRAG-70B的55.40和Search-o1-32B的53.31。
- 自我激励的EM训练过程稳定收敛，通常2-3次迭代即可达到最佳验证性能。
- 三个核心动作（thinking、search、recording）和重要性权重w(z)均不可或缺，消融实验表明移除任一组件会导致性能大幅下降。
- 冷启动数据有助于提升性能，但100个示例即可取得较好权衡；零示例也能优于许多基线。
- 方法在不同模型家族和尺度（3B-24B）上均有效，呈现缩放定律模式。
- 可扩展性：加入文档重排动作后性能进一步提升，验证了框架的灵活性。

## 7. 优点

- **方法创新性强**：首次将搜索轨迹视为隐变量，使用广义EM算法实现端到端的自我改进训练，而非独立的子任务优化。
- **理论保证**：提供了收敛性证明（非递减 + 上界有界），并结合KL散度分析优化间隙。
- **实验全面**：包含大量基线、多维消融、冷启动分析、人类评估、案例研究，覆盖主流基准。
- **可扩展性**：提出ExSearch-Zoo，支持不同骨干模型和扩展动作（如重排），便于后续研究。
- **开源友好**：代码已公开。
- **清晰的可解释性**：think-search-record模式提供透明的推理轨迹，便于诊断。

## 8. 不足与局限

- **实验覆盖**：
  - 仅限文本输入/输出，未涉及多模态场景。
  - 所有实验基于固定规则指标（EM、F1），未评估长文本生成或开放式任务。
- **计算资源细节不足**：未明确报告GPU型号、数量、总训练耗时，影响复现可比性。
- **统计显著性缺失**：实验未报告误差棒或显著性检验（论文self-reported为“No”）。
- **方法局限**：
  - 固定每步都进行检索，即使对于简单问题也造成冗余，缺乏自适应判定何时检索。
  - 存在“欠检索”（3.5%案例）和“过检索”（7.5%案例）问题，停止准则仍需改进。
- **冷启动依赖**：虽然零示例也有效，但1000示例在性能上更优，仍需代价约$20的数据生成。
- **潜在偏差**：训练和评估基于Wiki语料，可能在其他领域泛化性未知。
- **应用限制**：增强的事实准确性可能被用于生成更具说服力的虚假信息，需配套安全机制。

（完）
