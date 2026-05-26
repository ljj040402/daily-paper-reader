---
title: A Causal Model of Theory-of-Mind in AI Agents
title_zh: AI智能体中心理理论的因果模型
authors: "Jack Foxabbott, Rohan Subramani, James Fox, Francis Rhys Ward"
date: 2024-05-15
pdf: "https://openreview.net/pdf?id=ASA2jdKtf3"
tags: ["query:ai"]
score: 8.0
evidence: AI智能体心理理论的因果模型
tldr: 本文在AI智能体交互中引入心理理论，扩展多智能体影响图（MAID）为不完全信息MAID（II-MAID），显式建模信念与意图推理。与动态博弈理论建立联系，为智能体社会交互提供形式化基础。
source: NeurIPS-2024-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-asa2jdktf3/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1176, \"height\": 332, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-asa2jdktf3/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1621, \"height\": 602, \"label\": \"Figure\"}]"
motivation: 智能体交互需要推理他人信念与意图，现有模型不足。
method: 扩展多智能体影响图，加入不完全信息表示。
result: II-MAID与不完全信息动态博弈有强理论联系。
conclusion: 为AI智能体社会推理提供了因果建模框架。
---

## Abstract
Agency is a vital concept for understanding and predicting the behaviour of future AI systems. There has been much focus on the goal-directed nature of agency, i.e., the fact that AI agents may capably pursue goals. However, the dynamics of agency become significantly more complex when autonomous agents interact with other agents and humans, necessitating engagement in theory-of-mind, the ability to reason about the beliefs and intentions of others. In this paper, we extend the framework of multi-agent influence diagrams (MAIDs) to explicitly capture this complex form of reasoning. We also show that our extended framework, MAIDs with incomplete information (II-MAIDs), has a strong theoretical connection to dynamic games with incomplete information with no common prior over types. We prove the existence of important equilibria concepts in these frameworks, and illustrate the applicability of II-MAIDs using an example from the AI safety literature.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：现有AI智能体建模主要关注单智能体的目标导向行为，忽略了多智能体交互中必要的**心理理论**（Theory-of-Mind, ToM），即推理他人信念与意图的能力。传统多智能体影响图（MAID）假设所有智能体共享相同且正确的世界信念，无法捕捉智能体间不一致、错误的信念以及高阶信念（如“我认为你认为…”）。
- **研究背景**：AI安全领域需要形式化工具描述智能体之间的欺骗、误解等复杂社会推理。因果关系在信念、意图建模中具有重要作用，但现有因果博弈模型（MAID/因果游戏）缺乏对**不完全信息**（incomplete information）的支持，即智能体可能对游戏结构、他人信念存在不确定性，且没有共同先验假设。

### 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程
- **核心思想**：将MAID推广为**不完全信息MAID（II-MAID）**，显式建模每个智能体（包括外部建模者）的主观信念层次，允许不同智能体拥有不一致、甚至错误的世界模型。
- **关键技术细节**：
  - **定义II-MAID**：一个元组 \( \mathcal{S} = (N, S^*, \mathcal{S}) \)，其中 \( N \) 是智能体集合，\( \mathcal{S} \) 是主观MAID的集合，\( S^* \) 是客观真实模型。每个主观MAID \( S = (M_S, (P_S^i)_{i \in N}) \) 包含一个MAID \( M_S \) 和智能体 \( i \) 在该主观模型下的先验 \( P_S^i \) 分布。
  - **相干性条件**：智能体 \( i \) 知道自己的先验 \( P_{S^*}^i \)，因此只能分配概率给那些具有相同先验的主观MAID。
  - **信息集与策略**：定义II-MAID的信息集为所有主观MAID中不可区分的（观测值, 动作集）对。策略（policy）需要为每个可能的信息集指定一个混合动作，即使某些情况在智能体主观先验下概率为0。
  - **与不完全信息扩展式博弈（II-EFG）的等价性**：通过构造 `maid2efgII` 和 `efg2maidII` 变换，证明II-MAID与II-EFG在**中期阶段**（interim stage）等价，策略和期望效用一一对应。
  - **均衡存在性**：在完美回忆、有限状态和有限动作假设下，证明II-MAID存在**纳什均衡**（通过Kakutani不动点定理）。

### 3. 实验设计：使用了哪些数据集 / 场景，它的 benchmark 是什么，对比了哪些方法
- **本文为纯理论工作，未设计实验。** 论文仅通过一个**概念性示例**（AI安全中的诚实评估与危险能力评估博弈）来阐释II-MAID的建模能力，但并未进行数值模拟或与基线方法的对比。

### 4. 资源与算力：如果文中有提到，请总结使用了多少算力（GPU 型号、数量、训练时长等）。若未明确说明，也请指出这一点
- **未提及任何计算资源或算力消耗**。论文全部为理论分析，无实验运行，因此无需GPU等算力。

### 5. 实验数量与充分性：大概做了多少组实验（如不同数据集、消融实验等），这些实验是否充分、是否客观、公平
- **无实验。** 因此不存在实验充分性、客观性或公平性的讨论。论文的贡献在于形式化框架和理论等价性证明，属于数学推理类工作，不依赖实验验证。

### 6. 论文的主要结论与发现
- **主要结论**：
  - 提出的II-MAID框架能够显式建模智能体间**不一致的高阶信念**，比传统MAID更贴近真实多智能体交互。
  - II-MAID与**动态不完全信息博弈（II-EFG）** 在中期阶段等价，从而继承了后者的均衡存在性定理（纳什均衡）。
  - 然而，论文指出纳什均衡在II-MAID中并不一定合理：因为智能体可能基于错误信念行动，即使事假上看是相互最优，实际却无法被智能体理性辨识。
  - 未来需要开发更合适的解概念（如基于信念层次的最佳反应）。

### 7. 优点：方法或实验设计上有哪些亮点
- **理论贡献突出**：将心理理论的形式化与因果图结合，提供了一个紧凑且可扩展的表示框架。
- **严格的理论基础**：建立了与动态不完全信息博弈的等价性，为后续研究提供了坚实桥梁。
- **打破共同先验假设**：允许智能体持有不一致、错误的信念，这在现实场景（如AI欺骗、误解）中至关重要。
- **应用导向**：特别关注AI安全场景，示例展示了如何用II-MAID建模智能体之间的错误信念和欺骗。

### 8. 不足与局限：包括实验覆盖、偏差风险、应用限制等
- **缺乏实验验证**：纯理论工作未进行任何模拟或实证，框架的实际可行性和计算效率未知。
- **缺少实用解概念**：纳什均衡存在但不合理，论文未提出能反映智能体真实行为的解概念（如“信念最佳响应”），限制了框架的直接应用。
- **假设限制**：框架要求完美回忆、有限状态/动作空间，实际大规模场景下可能不成立。
- **复杂性**：信念层次可能无限深，虽定义中允许，但显式表示和管理高阶信念在实践中可能指数增长。

（完）
