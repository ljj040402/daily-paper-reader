---
title: Structural Entropy Guided Agent for Detecting and Repairing Knowledge Deficiencies in LLMs
title_zh: 结构熵引导的LLM知识缺陷检测与修复智能体
authors: "Yifan Wei, Xiaoyan Yu, Tengfei Pan, Angsheng Li, Li Du"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=hTGqC1h8Ig"
tags: ["query:ai"]
score: 4.0
evidence: 通过结构熵增强LLM知识，与人工智能研究相关
tldr: 该论文提出SENATOR框架，利用结构熵度量知识图谱路径的不确定性，引导合成数据生成以修复大模型的领域知识缺陷。实验证明该方法在医学和科学问答上显著提升LLM的事实准确性，避免冗余样本。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-htgqc1h8ig/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1434, \"height\": 676, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-htgqc1h8ig/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1437, \"height\": 652, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-htgqc1h8ig/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 595, \"height\": 465, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-htgqc1h8ig/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1449, \"height\": 372, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-htgqc1h8ig/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1429, \"height\": 509, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-htgqc1h8ig/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1414, \"height\": 923, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-htgqc1h8ig/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1436, \"height\": 675, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-htgqc1h8ig/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1412, \"height\": 974, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-htgqc1h8ig/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 598, \"height\": 363, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-htgqc1h8ig/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1384, \"height\": 627, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-htgqc1h8ig/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1382, \"height\": 675, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-htgqc1h8ig/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1409, \"height\": 1066, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-htgqc1h8ig/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1443, \"height\": 156, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-htgqc1h8ig/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1081, \"height\": 298, \"label\": \"Table\"}]"
motivation: 大模型在知识密集型领域事实精度不足，现有合成数据方法生成冗余样本。
method: 基于结构熵指标量化知识图谱路径不确定性，选择性地生成填补知识漏洞的合成数据。
result: 在多个知识密集型基准上，SENATOR提升了LLM的准确率，且生成数据效率更高。
conclusion: 结构熵有效指导了LLM知识增强过程。
---

## Abstract
Large language models (LLMs) have achieved unprecedented performance by leveraging vast pretraining corpora, yet their performance remains suboptimal in knowledge-intensive domains such as medicine and scientific research, where high factual precision is required.
While synthetic data provides a promising avenue for augmenting domain knowledge, 
existing methods frequently generate redundant samples that do not align with the model’s true knowledge gaps. 
To overcome this limitation, 
we propose a novel Structural Entropy-guided Knowledge Navigator (SENATOR) framework that addresses the intrinsic knowledge deficiencies of LLMs. 
Our approach employs the Structure Entropy (SE) metric to quantify uncertainty along knowledge graph paths and leverages Monte Carlo Tree Search (MCTS) to selectively explore regions where the model lacks domain-specific knowledge. 
Guided by these insights, the framework generates targeted synthetic data for supervised fine-tuning, enabling continuous self-improvement. 
Experimental results on LLaMA-3 and Qwen2 across multiple domain-specific benchmarks show that SENATOR effectively detects and repairs knowledge deficiencies, achieving notable performance improvements.

---

## 论文详细总结（自动生成）

好的，这是根据您提供的论文内容生成的结构化、深入、客观的中文总结。

## 论文精华解析：SENATOR：结构熵引导的LLM知识缺陷检测与修复框架

### 1. 核心问题与整体含义

*   **研究动机：** 大型语言模型在通用任务上表现出色，但在医学、科学研究等**知识密集型领域**，其事实精度往往不足。主要原因在于高质量领域语料难以获取。
*   **问题根源：** 当前流行的数据合成方法（用于生成领域数据以微调模型）效率低下。它们生成的样本通常是**冗余的**，包含了模型已经掌握的知识，未能有效填补模型真正的**知识盲区（知识缺陷）**。
*   **核心挑战：** 最关键的挑战在于**如何高效、精准地检测出LLM的知识缺陷**。由于模型的知识是隐式编码在参数中的，很难明确区分模型“知道”和“不知道”什么。
*   **论文目标：** 提出一个名为SENATOR的框架，旨在通过一个**“探测-修复”的闭环**，主动发现并修复LLM在特定领域的知识缺陷，从而高效地提升模型在该领域的表现。

### 2. 方法论

*   **核心思想：** 利用知识图谱作为知识空间，引入**结构熵（Structural Entropy, SE）** 作为度量模型不确定性的指标。通过**蒙特卡洛树搜索（MCTS）** 智能地遍历知识图谱，找到那些模型**不确定性最高（即知识缺陷最严重）** 的路径，然后在这些路径上定向合成数据，用于微调模型，填补知识漏洞。

*   **关键技术细节：**
    1.  **知识缺陷检测：**
        *   **三元组不确定性度量：** 给定一个知识图谱三元组 `<subject, relation, object>`，使用**自信息（Self-Information）** 来度量模型对该事实的确定性。公式为：`I(u, ρ, v) = -log₂ P(v | u, ρ)`，其中 `P(v | u, ρ)` 是模型在给定主语和关系后，预测出正确宾语的概率。概率越低，自信息越大，表示模型对这个“事实”越不确定。
        *   **知识路径不确定性度量：** 基于单个三元组的自信息，进一步计算**图结构熵（1维结构熵）** 来综合评估一条路径的不确定性。公式为：`H₁(G) = - Σ (dᵤ / vol(G)) * log₂(dᵤ / vol(G))`，其中 `dᵤ` 是节点 `u` 的加权度（其所有关联边自信息之和），`vol(G)` 是整个子图的加权度。结构熵越高，说明该路径上的知识结构越复杂，模型表现的越不自信。
        *   **MCTS探索：** 框架定义一个LLM智能体，以知识图谱节点作为状态（entity），关系边作为动作（relation），进行MCTS搜索。
            *   **选择（Selection）：** 使用**PUCT算法**平衡探索与利用，选择最有潜力暴露知识缺陷的节点进行扩展。
            *   **扩展（Expansion）：** 当达到一个叶子节点时，将其所有相邻实体作为新节点加入搜索树。
            *   **模拟（Simulation）：** 从新节点开始，用随机策略进行模拟，直到达到预设深度，并计算该路径的**结构熵**作为**奖励值**。
            *   **反向传播（Backpropagation）：** 将模拟得到的奖励值回传，更新路径上所有父节点的价值（Q值）和访问次数（N值）。
        *   通过多次迭代MCTS，框架能够找到结构熵最大的路径，即模型知识缺陷最严重的关键路径。

    2.  **知识合成与修复：**
        *   将MCTS探索出的**最高结构熵路径**作为上下文，通过设计好的**提示模板（prompt）**，引导LLM生成与这条路径相关的**问答对（QA pairs）**。例如，模板会要求模型基于路径中的事实生成问题并给出基于路径中实体的答案。
        *   生成的数据会经过一个**多层质量评估机制**，包含**格式一致性、逻辑连贯性、幻觉避免**等规则，过滤掉低质量样本。
        *   使用过滤后的高质量合成数据，对模型进行**监督微调**，修复其知识缺陷。

*   **算法流程（文字描述）：**
    1.  初始化知识图谱、LLM和MCTS搜索树。
    2.  **知识缺陷发现阶段（MCTS循环）：**
        a.  从种子实体（如常见疾病）开始。
        b.  在搜索树中进行多轮MCTS。每一轮包括：选择当前最有潜力的节点、扩展新节点、模拟至路径末端并计算结构熵作为奖励、反向传播更新节点统计信息。
        c.  多次迭代后，提取结构熵最高的若干条知识路径。
    3.  **知识修复阶段:**
        a.  对于提取出的高不确定性路径，使用特定提示模板引导LLM生成QA对。
        b.  使用多级规则（格式、逻辑、幻觉检查）过滤合成数据。
        c.  将高质量的合成数据与常规的指令微调数据混合，对LLM进行两阶段微调：先进行知识注入，再进行领域指令对齐。

### 3. 实验设计

*   **场景：** 知识密集型的**医学领域**。
*   **数据集：**
    *   **知识图谱：** **SPOKE知识图谱**，包含超过4200万个节点和1.6亿条边，覆盖广泛的生物医学知识。
    *   **基准测试（Benchmarks）：** **MedQA**（USMLE）、**MedMCQA**（AIIMS）、**PubMedQA**、**GPQA**（研究生级别，特别是其中的遗传学和分子生物学子集）、**MMLU**的医学子集。
    *   **指令微调数据（DI）：** 来自PMC-LLaMA工作的包含51.4万样本的医学指令数据集。
*   **对比方法：**
    *   通用LLM基座：**Llama-3-8B**、**Qwen2-7B**、**Baichuan2**、**Llama-2**。
    *   特定医学LLM：**Med-Alpaca**、**HuatuoGPT-II**、**PMC-LLaMA**。以及在附录中补充的**BioMistral-7B**、**Meditron-7B**、**Llama-3-UltraMedical**。
*   **评估协议：** 主要采用**零样本（Zero-shot）** 设置进行评估。

### 4. 资源与算力

*   论文在附录D部分明确描述了算力使用情况：
    *   **模型微调（SFT）：** 使用 **8 张 NVIDIA A100-40G GPU**。以Qwen2-7B模型为例，持续约 **30小时** 完成3个epoch的训练。
    *   **推理实验：** 使用 **1-2 张 NVIDIA A100-40G GPU** 进行合成数据生成和模型评估。报告提及使用了vllm加速库。

### 5. 实验数量与充分性

*   **实验数量：** 论文进行了较为充分的实验，主要包括：
    *   **主实验（Main Results）：** 在4个主要基准测试上对比了数十个不同规模和领域的模型（通用LLM和医学LLM）。
    *   **消融实验（Ablation）：** 对比了“仅SFT指令数据”和“指令数据+合成数据”的效果，验证了合成数据的必要性。
    *   **数据分布分析：** 使用UMAP和KDE可视化方法，对比了原始预训练数据和SENATOR合成数据的分布，证明合成数据扩展了知识覆盖。
    *   **数据规模分析：** 探讨了合成数据量对模型性能的影响。
    *   **交叉验证（Swap Setting）：** 交换不同模型生成的合成数据来微调另一个模型，验证了合成数据的通用性。
    *   **人工评估：** 对生成的501个QA样本进行了人工质量检查，统计了各类错误的比例。
    *   **超参数：** 在附录中提供了模型训练的详细超参数。
*   **充分性与公平性：**
    *   **充分：** 实验覆盖了多个标准医学基准，并在多种主流模型上验证了有效性。对实验结果进行了量化（∆提升百分比）和定性（分布图）分析。实验设置（零样本）被清晰定义。
    *   **客观/公平：** 对比了包括当时最先进的医学领域模型在内的多个基线。然而，对比中未包含当时可能更新的模型（如GPT-4）等，这是一个常见的局限性。所有实验均使用固定的随机种子运行3次以确保一致性。总体而言，实验设计是严谨和相对公平的。

### 6. 主要结论与发现

1.  **有效性：** SENATOR框架能够**有效检测并修复LLM的知识缺陷**。相比于仅使用通用指令微调，加入SENATOR生成的合成数据后，Llama-3和Qwen2在多个医学基准上均获得显著提升，平均提升约10%-12%。
2.  **效率：** SENATOR通过**定向填补知识盲区**，避免了冗余数据的生成，是一种更高效的知识增强方法。仅需少量（如26k-128k条）合成数据就能带来可观提升，远超同等数量的随机数据或通用指令数据。
3.  **分布覆盖：** 通过可视化分析，SENATOR生成的合成数据能够**有效扩展**原始预训练数据的知识覆盖范围，并且其密度分布与模型预测性能具有一定的负相关性，即模型表现越差的领域，合成的数据越多。
4.  **通用性与模型特异性：** 不同模型（如Llama-3和Qwen2）的知识缺陷有**部分重叠**（可能源于预训练语料的相似性），因此一个模型生成的合成数据也能部分帮助另一个模型。但同时存在**模型特异性**的知识缺陷，说明SENATOR能够针对性地发现单个模型的弱点。
5.  **规模效应：** 随着合成数据量的增加，模型性能呈现**持续提升**的趋势，表明该方法具有良好的可扩展性。

### 7. 优点

1.  **创新性：** 将**结构熵**引入到LLM知识缺陷的度量中，相较于传统的自信息或概率置信度，能更好地捕捉图谱中的**拓扑结构和元素间的依赖关系**，提供更全面的不确定性评估。
2.  **高效性：** 通过MCTS引导探索，能**避免枚举所有知识路径的计算爆炸**，高效地定位到最关键的知识缺陷区域，实现“好钢用在刀刃上”的数据合成。
3.  **通用性与可解释性：** 框架不依赖于特定的模型架构（在Llama和Qwen上均有效），并且MCTS探索出的高熵路径本身就提供了一个指向知识缺陷的、可解释的**“线索”**。
4.  **数据质量保障：** 建立了包括格式、逻辑、幻觉检查在内的**多层质量控制机制**，有效过滤了生成的低质量数据，维护了训练数据的可靠性。
5.  **结构完整：** 论文逻辑清晰，问题定义明确，方法设计环环相扣，实验设计覆盖了有效性和可靠性验证的多个方面。

### 8. 不足与局限

1.  **依赖外部知识图谱：** 框架高度依赖**高质量、结构化的领域知识图谱**（如SPOKE）。在没有现成图谱或图谱不完整的领域，本方法难以直接应用。
2.  **合成数据质量瓶颈：** 人工评估显示，虽然幻觉问题被有效缓解，但仍有近**38% 的合成数据存在质量问题**（主要是格式和逻辑错误）。尽管有过滤机制，但数据生成的质量仍有较大提升空间，这直接影响了模型微调效果的上限。
3.  **实验覆盖范围有限：** 实验主要局限在**医学领域**。虽然在GPQA（跨学科）和MMLU上也有涉及，但整体结论的泛化性（如扩展到法律、工程、金融等其他知识密集型领域）尚未得到充分验证。
4.  **计算资源消耗较大：** 尽管数据效率高，但整个框架的运行成本不低：
    *   **MCTS探索阶段**需要多次调用LLM进行推理。
    *   微调使用了8张A100 GPU。对于资源有限的团队，这可能构成障碍。
5.  **探索策略可优化：** 论文提到，在MCTS探索中未考虑**实体类型**等因素，导致生成的合成数据在主题分布上可能不均衡（如图9所示，不同医学子领域的性能提升有波动）。引入更精细的约束可能进一步提升效率。

（完）
