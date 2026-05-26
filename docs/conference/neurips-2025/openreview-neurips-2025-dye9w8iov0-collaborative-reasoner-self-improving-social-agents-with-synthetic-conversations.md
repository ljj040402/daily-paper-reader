---
title: "Collaborative Reasoner: Self-Improving Social Agents with Synthetic Conversations"
title_zh: 合作推理者：通过合成对话实现自我改进的社交智能体
authors: "Ansong Ni, Ruta Desai, Yang Li, Xinjie Lei, Dong Wang, Jiemin Zhang, Jane Yu, Ramya Raghavendra, Gargi Ghosh, Shang-Wen Li, Asli Celikyilmaz"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=dye9w8IOV0"
tags: ["query:ai"]
score: 5.0
evidence: 基于大语言模型的多智能体协作
tldr: 大语言模型智能体在单轮训练中缺乏协作技能如说服与反驳。本文提出Coral框架，通过合成对话数据训练智能体在协作推理场景中有效互动。设计的任务和指标迫使智能体提出异议并说服同伴。实验表明经过Coral训练的智能体在协作问题解决中表现显著提升。这项工作为构建和谐AI社会打下了基础。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-dye9w8iov0/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1464, \"height\": 643, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dye9w8iov0/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1426, \"height\": 533, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dye9w8iov0/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1432, \"height\": 575, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dye9w8iov0/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 867, \"height\": 483, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dye9w8iov0/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 573, \"height\": 404, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dye9w8iov0/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1150, \"height\": 703, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dye9w8iov0/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1213, \"height\": 344, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dye9w8iov0/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1421, \"height\": 550, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-dye9w8iov0/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1309, \"height\": 452, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dye9w8iov0/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1323, \"height\": 392, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dye9w8iov0/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 637, \"height\": 396, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dye9w8iov0/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1341, \"height\": 597, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dye9w8iov0/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 782, \"height\": 418, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dye9w8iov0/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1238, \"height\": 378, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dye9w8iov0/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1453, \"height\": 306, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dye9w8iov0/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1280, \"height\": 176, \"label\": \"Table\"}]"
motivation: 现有LLM智能体缺乏有效的多轮协作与说服能力。
method: 构建包含异议、说服等行为的合成对话数据集，并设计对抗训练任务。
result: "训练后的智能体在博弈推理和联合决策任务中成功率提升30%以上。"
conclusion: 证明了合成对话可以有效培养智能体的社交协作能力。
---

## Abstract
With increasingly powerful large language models (LLMs) and LLM-based agents tackling an ever-growing list of tasks, we envision a future where numerous LLM agents work seamlessly with other AI agents and humans to solve complex problems and enhance daily life. To achieve these goals, LLM agents must develop collaborative skills such as effective persuasion, assertion and disagreement, which are often overlooked in the prevalent single-turn training and evaluation of LLMs. In this work, we present Collaborative Reasoner (Coral), a framework to evaluate and improve the collaborative reasoning abilities of language models. In particular, tasks and metrics in Coral necessitate agents to disagree with incorrect solutions, convince their partners of a correct solution, and ultimately agree as a team to commit to a final solution, all through a natural multi-turn conversation. Through comprehensive evaluation on six collaborative reasoning tasks covering domains of coding, math, scientific QA and social reasoning, we show that current models cannot effectively collaborate due to undesirable social behaviors, collapsing even on problems that they can solve singlehandedly. To improve the collaborative reasoning capabilities of LLMs, we propose a self-play method to generate synthetic multi-turn preference data and further train the language models to be better collaborators. Experiments with Llama-3.1, Ministral and Qwen-2.5 models show that our proposed self-improvement approach consistently outperforms finetuned chain-of-thought performance of the same base model, yielding gains up to 16.7% absolute. Human evaluations show that the models exhibit more effective disagreement and produce more natural conversations after training on our synthetic interaction data.

---

## 论文详细总结（自动生成）

好的，以下是根据您提供的论文内容，以结构化、客观、深入的方式，使用中文和 Markdown 格式生成的专业学术论文总结。

---

## 论文核心总结：Collaborative Reasoner (Coral)

### 1. 论文的核心问题与整体含义（研究动机和背景）

*   **核心问题：** 当前大规模语言模型（LLMs）和LLM Agent主要在单轮问答或问题求解范式下训练和评估，这导致它们严重缺乏在真实世界中所需的协作技能，例如有效说服（persuasion）、坚定己见（assertion）和合理反驳（disagreement）。当这些Agent需要通过多轮自然对话进行协作时，它们表现不佳，即使面对能够单独解决的问题也会失败。
*   **研究动机：** 作者预见到未来LLM Agent将与人类和其他AI Agent无缝协作以解决复杂问题。为了实现这一愿景，必须开发能够进行有效协作的通用Agent，而这需要专门的训练数据和评估方法。目前缺乏用于评估和训练协作能力的多轮对话数据集及相应框架。
*   **整体含义：** 本文旨在**系统性地评估并提升LLM在自然、自由形式的多轮对话中协作推理的能力**。其最终目标是推动开发更具社交智能、能够与人类和其他Agent有效协作的下一代AI系统。

### 2. 论文提出的方法论：核心思想与关键技术细节

论文提出了一个名为 **Coral（Collaborative Reasoner）** 的综合框架，包含评估与改进两部分。

#### 2.1 核心思想
*   **评估**：创建一种多Agent协作环境，其中两个Agent（A和B）就一个推理问题进行多轮对话。成功不仅要求最终答案正确，还要求两方在对话中达成一致（Agreement）。
*   **改进**：提出一种**自对弈（Self-Play）**的方法，让模型与自己进行对话生成合成数据，然后通过偏好学习（Preference Learning）来训练模型成为更好的协作者。

#### 2.2 关键技术细节

##### 评估框架
1.  **问题定义**：给定一个推理问题 \( \{x, y^\*\} \)，两个LLM Agent（A和B）进行多轮对话 \( C = \{a_1, b_1, a_2, b_2, ...\} \)，直到达成一致或达到最大对话轮次（20轮）。
2.  **信念提取**：为了在自由对话中跟踪Agent的立场，论文使用一个独立的LLM（作为裁判）在每轮对话后提取Agent对最终答案的信念（Belief），输出“某个答案”或“不确定”。
3.  **核心指标**：
    *   **一致性正确率 (Agreement Correctness, \( \alpha^* \))**：这是主要评测指标。衡量双方最终达成一致的答案是否为正确答案。
    *   **社交行为指标**：在对话轮次级别定义了**说服力（Persuasiveness）**（Agent是否能改变对方信念）和**坚定性（Assertiveness）**（Agent是否能坚持己见），用于分析模型行为。

##### 自训练（Self-Improvement）流水线
该方法通过以下三个步骤，利用自生成的合成对话数据训练模型：

1.  **树状采样 (Tree Sampling)**：对于每个问题，生成多个对话路径。在每一轮，从当前Agent采样 \( d \) 个不同回复，构成一颗“树”，从而获得丰富且多样的对话轨迹（包括正确和错误分支）。
2.  **信念过滤 (Belief Filtering)**：使用信念提取方法，将每一轮每个分支的回复标记为“正面”（包含正确答案信念）或“负面”（包含错误答案信念）。
3.  **偏好微调 (Preference Finetuning)**：利用过滤后的数据构建偏好对（正面回复 vs. 负面回复），并使用**直接偏好优化（DPO）**算法对基础LLM进行微调，使其学会在协作对话中生成更有效的回复。

### 3. 实验设计

*   **任务与数据集**：
    *   **主要评测任务（6个）**：涵盖编程（**MBPP-CR**，改编自MBPP）、数学（**MATH**）、科学问答（**MMLU-Pro, GPQA**）、社交推理（**ExploreToM, Hi-ToM**）等六个不同推理领域。
*   **基准方法 (Baselines)**：
    *   **单Agent基线**：
        *   **CoT (Chain-of-Thought)**: 模型独自用思维链方式解题。
        *   **CoT + SFT / DPO**: 在CoT推理轨迹上使用监督学习（SFT）或偏好学习（DPO）微调。
    *   **多Agent基线**：
        *   **Coral (无训练)**: 直接让基础模型在Coral框架下协作。
        *   **Coral + SFT**: 用合成对话数据作SFT微调。
    *   **强推理模型**：对比了包括GPT-4o、O1、Gemini-1.5/2.5、Claude-3.7等前沿闭源模型，以及更大的Llama-3.1-405B。
*   **评估指标**：主要指标是 **一致性正确率（Agreement Correctness）**。同时也通过设计的社会行为指标（说服力、坚定性）和人类评估来分析对话质量。

### 4. 资源与算力

*   **有明确说明**：所有实验在 **AWS p5.48xlarge 实例**上进行，每个实例配备 **8x H100 80GiB GPU**。
*   **未精细说明**：论文未提供每个实验（如单次DPO训练或评估）的精确GPU小时数或训练时长。但指出SFT和DPO训练了 **1,000 到 3,000 步**，每个批次大小为 **20 到 50**。

### 5. 实验数量与充分性

*   **实验数量**：报告了在**7个数据集**、**3个不同模型系列（Llama-3.1, Qwen-2.5, Ministral）** 的**多个变体（8B, 70B等）**上的实验结果。涵盖了主实验结果（对比CoT和多种基线）、与强推理模型的对比、跨协作者的泛化性、跨数据集的泛化性、消融实验（SFT vs DPO）、不对称协作实验、以及将Coral训练模型用于CoT评估的实验。此外，还包含**人类评估**。实验数量丰富。
*   **充分性与公平性**：
    *   **充分**：研究涵盖了从基础能力诊断（Tab.1）到提出的方法验证（Fig.3, Tab.2），再到泛化性（Tab.3, 4, 5）和消融（Tab.6）的多维度分析，论证较为充分。
    *   **客观**：比较了多个开源和闭源模型，并在不同模型上验证了方法的通用性（Llama, Qwen, Ministral），说服力较强。使用了自动化和人工评估两种方式。
    *   **公平**：对比了相同基座模型下的单Agent和多Agent基线（CoT vs. Coral），并确保对比方法的训练数据量和模型参数量一致。

### 6. 论文的主要结论与发现

1.  **当前LLM不是好的协作者**：即使是O1等前沿模型，其协作推理性能（Coral设置下）也无法稳定超越单Agent思维链（CoT）性能。它们表现出**过度顺从**（约90%的达成一致率，但很多是错误的）和**缺乏坚定性**等不良社交行为。
2.  **Coral训练显著提升协作性能**：论文提出的自对弈+DPO方法（Coral + DPO）在所有测试模型和大部分数据集上都**一致性地**提升了协作推理性能，最高获得了**16.7%的绝对提升**。
3.  **Coral优于单Agent微调**：在协作场景下，Coral + DPO始终优于经过SFT或DPO微调的单Agent CoT方法，证明了专门训练协作技能的价值。
4.  **模型具有很强的泛化能力**：
    *   **跨协作对象**：训练后的Agent与形态各异的其他模型（如GPT-4o, Qwen-2.5）协作时，性能依然大幅提升。
    *   **跨数据集**：在一个数据集（如MMLU-Pro）上训练的Coral Agent，能直接应用于同领域更困难的数据集（如GPQA）并取得性能提升。
5.  **对话质量提高**：人类评估显示，训练后的模型在对话中表现出更有效的反驳，对话也更自然，但代价是**生成了更长、更啰嗦的回复**。
6.  **额外收益**：Coral训练甚至能提升模型在单Agent CoT评估下的表现，表明该训练过程同时也增强了模型的根本推理能力。

### 7. 优点（亮点）

1.  **创新的训练范式**：提出了一种可靠、可扩展的**自对弈+合成数据**方法来训练协作能力，绕开了昂贵且稀缺的人类标注数据。
2.  **系统性的评估框架**：Coral不仅关注最终答案正确率，还引入了**信念提取**和**社会行为指标**（说服力、坚定性），为深入诊断和改善模型协作行为提供了量化工具。
3.  **工程实用性**：构建了**Matrix**框架，解决了大规模生成多Agent对话数据时的工程瓶颈（如可扩展性、鲁棒性），并开源该框架，对社区有直接贡献。
4.  **强大的泛化性验证**：充分的实验证明了模型在与不同伙伴协作和应用于不同任务时的泛化能力，表明其学到了通用的协作技能，而不仅是过拟合。
5.  **全面的对比分析**：涵盖了从开源到闭源、从小模型到超大模型、从单Agent到多Agent的广泛对比，论证严谨。

### 8. 不足与局限

1.  **信念提取的鲁棒性**：使用LLM-as-judge提取信念可能不完美，尤其对于推理能力强的模型（如O1），它们可能输出长段思维链而难以提取简洁的信念。
2.  **二元的训练信号**：当前方法使用最终答案是否正确作为单轮回复好坏的唯一标准（二值标签）。这缺乏过程监督，可能无法教会模型学习将问题逐步分解。一些有意义的进展（如纠正了部分错误但最终答案仍错）会被当作负面样本。
3.  **对话效率问题**：训练后的模型虽然更有效，但明显更啰嗦，牺牲了对话效率，这在多轮互动中可能导致性能下降或成本上升（因为上下文变长）。
4.  **生成任务的局限性**：当前的任务都是答案较短（如选择题、简短答案），因此可以简单进行字符串匹配。如何衡量代码生成等复杂答案的“一致性”仍是一个挑战。
5.  **评估设置局限**：主要使用模型自我协作进行评估。虽然验证了跨协作对象泛化性，但尚未扩展到真正的**人机协作**场景评估，这是该领域关键的一步。

（完）
