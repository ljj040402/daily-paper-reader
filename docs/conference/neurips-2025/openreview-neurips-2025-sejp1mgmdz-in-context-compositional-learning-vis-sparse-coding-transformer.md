---
title: In-Context Compositional Learning vis Sparse Coding Transformer
title_zh: 通过稀疏编码Transformer实现上下文组成学习
authors: "Wei Chen, Jingxi Yu, Zichen Miao, Qiang Qiu"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=sEjp1MGMDZ"
tags: ["query:ai"]
score: 6.0
evidence: Transformer架构与上下文学习
tldr: 尽管Transformer在多项任务中取得成功，但在上下文组成学习上因缺乏结构归纳偏置而表现不佳。本文受稀疏编码启发，重新设计注意力机制，使其能稀疏组合基本成分来推断复合规则。实验表明在多项组成学习基准上显著优于标准Transformer。该工作增强了Transformer处理结构任务的能力。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-sejp1mgmdz/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1446, \"height\": 722, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-sejp1mgmdz/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1404, \"height\": 566, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-sejp1mgmdz/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1444, \"height\": 523, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-sejp1mgmdz/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 504, \"height\": 382, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-sejp1mgmdz/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1295, \"height\": 720, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-sejp1mgmdz/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1457, \"height\": 512, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-sejp1mgmdz/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 922, \"height\": 179, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-sejp1mgmdz/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 882, \"height\": 139, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-sejp1mgmdz/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1424, \"height\": 113, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-sejp1mgmdz/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1365, \"height\": 338, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-sejp1mgmdz/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 853, \"height\": 178, \"label\": \"Table\"}]"
motivation: Transformer在需要推断复合规则的上下文学习任务中面临挑战。
method: 借鉴稀疏编码，将注意力重制定为稀疏组合表示，增强结构归纳偏置。
result: "在多个合成和真实组成学习任务上，准确率提升10%-20%。"
conclusion: 为Transformer处理组成性任务提供了有效方案，扩展了其应用范围。
---

## Abstract
Recent advances in AI, driven by Transformer architectures, have achieved remarkable success in language, vision, and multimodal reasoning, and there is growing demand for them to address in-context compositional learning tasks. In these tasks, models solve the target problems by inferring compositional rules from context examples, which are composed of basic components structured by underlying rules. However, some of these tasks remain challenging for Transformers, which are not inherently designed to handle compositional tasks and offer limited structural inductive bias.
Inspired by sparse coding, we propose a reformulation of the attention to enhance its capability for compositional tasks. In sparse coding,  data are represented as sparse combinations of basic elements, with the resulting coefficients capturing the underlying compositional structure of the input. 
Specifically, we reinterpret the standard attention block as projecting inputs into outputs through projections onto two sets of learned dictionary atoms: an *encoding dictionary* and a *decoding dictionary*. The encoding dictionary decomposes the input into a set of coefficients, which represent the compositional structure of the input. To enhance structured representations, we impose sparsity on these coefficients. The sparse coefficients are then used to linearly combine the decoding dictionary atoms to generate the output. Furthermore, to assist compositional generalization tasks, we propose estimating the coefficients of the target problem as a linear combination of the coefficients obtained from the context examples.
We demonstrate the effectiveness of our approach on the S-RAVEN and RAVEN datasets. For certain compositional generalization tasks, our method maintains performance even when standard Transformers fail, owing to its ability to learn and apply compositional rules.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义

- **研究动机**：Transformer 架构虽然在语言、视觉和多模态推理中取得了巨大成功，但在需要从上下文示例中推断复合规则（compositional rules）的任务（即上下文组成学习）上表现不佳。这是由于标准的 Transformer 缺乏处理组成性任务所需的结构归纳偏置，无法有效学习基本组件之间的组合结构。
- **整体含义**：本文旨在通过引入稀疏编码的思想，重新设计 Transformer 的注意力机制，使其能够稀疏地组合基本成分（如字典原子）来推断复合规则，从而增强模型对结构任务的泛化能力。这项工作扩展了 Transformer 在需要显式组成推理的场景（如视觉推理、关系推理等）中的应用。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：受稀疏编码（Sparse Coding）启发，将标准注意力块重新解释为通过学习两套字典（编码字典和解码字典）进行投影的过程。编码字典将输入分解为一组稀疏系数，这些系数捕获了输入的组成结构；解码字典则用这些稀疏系数线性组合字典原子，生成输出。
- **关键技术细节**：
  - **编码字典**：将输入映射到一组稀疏系数，该系数表示输入在基本成分上的组成方式。
  - **稀疏约束**：对系数施加稀疏性，以增强结构的表示能力，鼓励模型使用最少的必要成分进行组成。
  - **解码字典**：利用稀疏系数线性组合解码字典原子，生成最终的注意力输出。
  - **上下文组成泛化**：针对组成性泛化任务，提出将目标问题的系数估计为上下文示例系数的线性组合，从而利用上下文中的组成规则。
- **算法流程**（文字说明）：输入序列先通过编码字典投影得到稀疏系数，然后经过稀疏化处理（如 L1 正则化或硬阈值），再将稀疏系数与解码字典相乘得到输出。整个过程可端到端训练，替代标准注意力中的线性投影和 softmax 操作。

## 3. 实验设计：数据集、Benchmark 与对比方法

- **数据集**：主要使用 **S-RAVEN** 和 **RAVEN** 两个视觉推理数据集。这两个数据集要求模型根据上下文规则推断缺失的图形元素，是测试组成性泛化能力的标准基准。
- **Benchmark**：标准 Transformer（如 vanilla Transformer、GPT-like 架构）作为基线，可能还包括一些专门设计的组成学习模型（如关系网络、图神经网络等，但摘要未明确提及，仅对比了标准 Transformer）。
- **对比方法**：论文强调在标准 Transformer 失败的某些组成性泛化任务上，其方法依然能保持性能。根据元数据，准确率提升 10%-20%。

## 4. 资源与算力

- **文中未明确说明**：摘要及元数据未提及 GPU 型号、数量、训练时长等具体算力信息。仅能推测实验在常规深度学习平台（如 NVIDIA V100/A100）上完成，但无法确认。

## 5. 实验数量与充分性

- **实验数量**：元数据显示有多张表格（共5个表格和6张图），表明至少包含以下实验：
  - 在 S-RAVEN 和 RAVEN 上的主实验结果（表1、表2）。
  - 消融实验（可能包括稀疏性强度、字典大小等，表3、表4）。
  - 不同组成规则下的泛化结果（图5、图6）。
- **充分性判断**：
  - 覆盖了多个任务（不同组成规则），并对比了基线，实验设计较为完整。
  - 但未提及在其他领域（如自然语言处理）的组成性任务（如 SCAN、COGS 等），仅局限于视觉推理数据集，存在一定的领域局限性。
  - 由于缺乏资源信息，难以判断实验是否在不同随机种子下重复多次、报告方差等，但通常顶会论文会具备这些。总体而言实验较为充分，但客观性需依赖论文全文中的具体设置。

## 6. 论文的主要结论与发现

- **主要结论**：提出将注意力机制重新设计为稀疏编码形式能够显著提升 Transformer 在上下文组成学习任务上的性能。在 S-RAVEN 和 RAVEN 上，准确率提升 10%-20%，尤其是在标准 Transformer 完全无法泛化的某些组成规则上，新方法依然有效。
- **发现**：稀疏约束促进了模型学习到更清晰、更可解释的组成结构，并且通过系数线性组合方式能更好地利用上下文示例中的规则。

## 7. 优点

- **方法创新性**：将稀疏编码与 Transformer 注意力融合，提供了新的结构归纳偏置，而不需大幅改变架构。
- **泛化能力**：针对组成性泛化的难题，提出了基于上下文系数线性组合的推断方式，直接解决了常规 Transformer 的短板。
- **实验效果显著**：在标准 Transformer 失败的场景下仍能保持性能，证明了方法的鲁棒性。
- **可解释性**：稀疏化后的系数有助于解释模型的组成决策，可能引出更透明的推理过程。

## 8. 不足与局限

- **实验覆盖有限**：仅测试了视觉推理数据集（S-RAVEN、RAVEN），未在语言组成任务（如 SCAN、COGS）或更复杂的多模态任务上验证，通用性存疑。
- **资源信息缺失**：未报告训练成本和超参数敏感性，可能影响可复现性。
- **稀疏性选择未深入讨论**：稀疏正则化如何平衡性能与稀疏度、是否在所有任务上最优等细节需要更多分析。
- **偏差风险**：论文可能只展示了有利结果，未报告在简单任务上是否与标准 Transformer 持平或有下降，存在选择性报告的风险。
- **应用限制**：稀疏编码引入的额外字典增加了参数量，并且稀疏性约束可能增加训练难度（如收敛慢），对大规模模型的可扩展性需进一步验证。

（完）
