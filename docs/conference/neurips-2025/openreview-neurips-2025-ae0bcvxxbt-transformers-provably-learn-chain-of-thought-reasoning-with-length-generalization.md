---
title: Transformers Provably Learn Chain-of-Thought Reasoning with Length Generalization
title_zh: Transformer可证明学习具有长度泛化的链式思维推理
authors: "Yu Huang, Zixin Wen, Aarti Singh, Yuejie Chi, Yuxin Chen"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=aE0bCvXXBt"
tags: ["query:ai"]
score: 6.0
evidence: Transformer推理的理论分析
tldr: 该论文针对Transformer在链式思维推理中的长度泛化问题，从理论上证明了状态跟踪任务的代数结构如何决定长度泛化能力。通过提出注意力集中机制，揭示了注意力层的检索鲁棒性与任务结构之间的关系，为理解Transformer推理能力提供了理论基础。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-ae0bcvxxbt/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 593, \"height\": 387, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ae0bcvxxbt/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1362, \"height\": 506, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ae0bcvxxbt/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 590, \"height\": 385, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ae0bcvxxbt/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1335, \"height\": 303, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ae0bcvxxbt/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1416, \"height\": 722, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ae0bcvxxbt/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1325, \"height\": 834, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ae0bcvxxbt/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1325, \"height\": 833, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ae0bcvxxbt/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1193, \"height\": 434, \"label\": \"Figure\"}]"
motivation: 理解Transformer在复杂推理任务中能否外推到更长的推理链，是AI推理的核心问题。
method: 通过梯度下降学习合成状态跟踪任务，形式化注意力集中机制，建立任务结构与泛化的联系。
result: 证明了代数结构决定长度泛化，注意力集中机制解释了检索鲁棒性。
conclusion: 为Transformer的推理长度泛化提供了理论保证，推动可解释AI推理研究。
---

## Abstract
The ability to reason lies at the core of artificial intelligence (AI), and challenging problems usually call for deeper and longer reasoning to tackle. A crucial question about AI reasoning is whether models can extrapolate learned reasoning patterns to solve harder tasks with a longer chain-of-thought (CoT). In this work, we present a theoretical analysis of transformers learning on synthetic state-tracking tasks with gradient descent. Specifically: 1). We prove how the *algebraic structure* of state-tracking problems governs the length generalization of learned reasoning in transformers. In doing so, we formulate the **attention concentration** mechanism, linking the retrieval robustness of the attention layer to the task structure of long-context state tracking problems. 2). Moreover, we prove that a transformer can provably *self-improve* via a *recursive self-training* scheme that progressively extends the range of solvable problem lengths. We show that the model can achieve abilities outside the coverage of the base model in recursive training, different from prior theoretical works on self-improvement.
To our knowledge, we provide the first *optimization guarantee* that constant-depth transformers provably learn $\text{NC}^1$-complete problems with CoT, significantly going beyond prior art confined in $\text{TC}^0$, unless the widely held conjecture $\text{TC}^0 \neq \text{NC}^1$ fails. Finally, we present a broad set of experiments supporting our theoretical results, confirming the length generalization behaviors and the mechanism of attention concentration.

---

## 论文详细总结（自动生成）

好的，这是根据您提供的论文内容生成的结构化中文总结。

### 论文核心问题与整体含义

*   **研究动机与背景：**
    *   链式思维（Chain-of-Thought, CoT）推理是当前大语言模型（LLM）提升复杂推理能力的关键技术。一个核心问题是，模型能否将学到的推理模式**泛化到更长、更复杂的推理链**上，即实现“长度泛化”（Length Generalization）。
    *   尽管实践中模型在长上下文下的性能会下降（即“上下文腐烂”（Context Rot）现象），但理论层面的理解十分有限。此前的研究多集中于Transformer的表达力，而忽视了其**通过梯度下降训练学习推理能力的优化过程**。
    *   本文旨在填补这一理论空白，研究Transformer能否通过训练**学习**到需要序列推理能力（即NC¹复杂度）的任务，以及学习到的能力能否泛化到更长的问题。

### 论文提出的方法论

*   **核心思想：**
    *   论文认为，Transformer在状态跟踪任务中的长度泛化能力受限于任务的**代数结构**。具体而言，对于可迁群作用（如循环群）任务，模型可以学到良好的泛化；对于对称群作用（如置换群）任务，泛化则受到限制。
    *   论文提出了一个关键机制——**注意力集中（Attention Concentration）**，用于解释检索的鲁棒性。该机制表明，当模型需要从长上下文中检索信息时，注意力必须高度集中在相关的几个token上，而忽视其他无关的“干扰”token。

*   **关键技术细节与算法流程：**
    *   **任务设定**：使用合成的`LEGO`状态跟踪任务。该任务的核心是预测变量在经历一系列群作用（如C6循环群或S5对称群）后的最终状态。
    *   **模型架构**：采用简化的**单层、无位置编码（NoPE）** 的解码器Transformer。模型由一个软注意力层和一个前馈网络（FFN）组成。
    *   **训练方案**：
        1.  **阶段一（Stage 1）**：固定注意力参数，仅训练FFN，使其学会执行单步的群操作（如 `g(y) -> y'`）。
        2.  **阶段二（Stage 2）**：固定训练好的FFN，仅训练注意力参数`Q`，使其学会如何从上下文中检索正确的信息（如找到正确的动作`g`和当前状态`y`）。
    *   **核心机制（图3）**：预测下一个状态`y_{ℓ+1}`需要两步：
        1.  **检索**：注意力层从上下文中找到正确的动作（来自谓词子句`Z_pred,ℓ+1`）和当前状态（来自答案子句`Z_ans,ℓ`）。
        2.  **应用**：FFN层执行`Y_{ℓ+1} = g_{ℓ+1}(Y_ℓ)`这个组合操作。
    *   **递归自训练（Recursive Self-Training）**：当直接泛化失败（如对称群任务）时，论文提出了一种课程学习算法。核心是：用当前模型为更长序列的中间步骤自动生成“标签”，然后在这些“自标签”数据上重新训练模型。通过不断重复“自我提升”的循环，模型可以逐步解决更长的推理问题。

### 实验设计

*   **数据集与场景：**
    *   使用合成数据集`LEGO`，具体包含**两个任务族**：
        *   **可迁群作用**：以**循环群C6**为代表。在这种结构中，从一个状态到另一个状态，只存在唯一的动作，干扰较少。
        *   **对称群作用**：以**对称群S5**为代表。在这种结构中，多个不同的动作可以将一个状态映射到同一个目标状态，因此存在大量潜在的“干扰”子句。
*   **评估指标**：主要测量模型在不同问题长度下的**最终答案正确率**（自回归生成，非教师强制）。
*   **对比方法**：论文主要是理论分析，并与自身的理论预测进行对比。实验部分对比了C6和S5两种任务下的长度泛化表现，以及有无递归自训练的效果。

### 资源与算力

*   论文明确指出，其实验是**小规模的、合成的**，可以在单个GPU上复现。文中并未提供具体的GPU型号、数量和训练时长等信息，这与其理论研究的定位相符。

### 实验数量与充分性

*   **实验数量**：实验设置清晰，主要包括：
    *   主实验（图1）：对比C6和S5任务的直接泛化能力（a），以及S5任务上递归自训练的效果（b）。
    *   注意力可视化（图2-6）：通过热力图和线条图，直观展示了C6和S5任务下注意力模式的差异，以及在更长上下文中的衰减情况。
*   **充分性与客观性**：
    *   实验设计很好地支持了论文的理论核心论点，清晰地展示了两种代数结构在泛化能力上的分离。
    *   递归自训练的消融实验也验证了其在困难任务上的有效性。
    *   实验是客观的，通过大量的随机采样取平均值来报告结果，并分析了注意力模式来揭示其内在机制。
    *   这些实验充分地验证了理论模型的关键预测。

### 论文的主要结论与发现

1.  **代数结构决定长度泛化**：对于可迁群作用（如C6），模型可以直接泛化到远长于训练长度的任务（从L=5到L=160）。而对于对称群作用（如S5），直接泛化能力有限。
2.  **注意力集中机制是核心**：成功的长度泛化依赖于模型学习到高度集中的注意力模式，使其能够精准地从上下文中检索所需信息。在可迁群任务中，这种模式更鲁棒。
3.  **递归自训练可引导出更长推理能力**：当直接泛化失败时，通过递归地使用模型自身的生成结果进行训练，可以“自举”出解决更长问题的能力。这为模型自我提升提供了理论保证。
4.  **超越理论界限**：论文首次从优化角度证明，常数深度的Transformer可以学习到`NC¹`完全问题（对称群任务），这超过了此前认为的`TC⁰`的理论上限（除非 `TC⁰ ≠ NC¹` 的猜想成立）。

### 优点

*   **理论深度与严谨性**：论文提供了严谨的理论证明（Optimization Guarantee），前所未有地揭示了Transformer学习链式思维推理的优化过程和泛化机制。
*   **机制的可解释性**：提出的“注意力集中”机制直观且可解释，为理解模型为何在长上下文中失败（上下文腐烂）提供了一个清晰的理论视角。
*   **理论与实践结合**：理论预测与实验结果高度吻合，实验设计精巧，能够清晰验证理论观点。
*   **问题设定巧妙**：采用`LEGO`任务和不同代数结构的群作用，简洁而有力地抓住了核心矛盾，避免了真实语言模型中的噪声干扰，便于进行纯理论分析。

### 不足与局限

*   **模型极度简化**：理论分析完全基于一个经过大量简化的Transformer模型（单层、NoPE、块稀疏注意力）。这些结论在更复杂的多层、多头注意力模型和真实世界任务上的适用性，仍有待验证。
*   **数据设定理想化**：`LEGO`任务是一个完全理想化的合成任务，其数据的生成分布和token表示（正交嵌入）都与真实语言数据相去甚远。
*   **泛化能力依赖于共现变量**：论文指出，注意力集中之所以能实现，是因为查询子句和需要检索的子句中共享同一个变量（例如`x_ℓ`）。这种强共现信号在真实语言中可能并不总是存在。
*   **应用限制**：论文的方法和结论主要服务于理论理解，距离直接应用于改进现行大语言模型的长度泛化能力还有一定距离。

（完）
