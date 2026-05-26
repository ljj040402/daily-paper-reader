---
title: Plasticity as the Mirror of Empowerment
title_zh: 可塑性：作为赋能的镜像
authors: "David Abel, Michael Bowling, Andre Barreto, Will Dabney, Shi Dong, Steven Stenberg Hansen, Anna Harutyunyan, Khimya Khetarpal, Clare Lyle, Razvan Pascanu, Georgios Piliouras, Doina Precup, Jonathan Richens, Mark Rowland, Tom Schaul, Satinder Singh"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=eOZFqyE9Ok"
tags: ["query:ai"]
score: 7.0
evidence: AI智能体理论：可塑性与赋能
tldr: 该论文提出“可塑性”作为衡量智能体受过去观测影响程度的概念，使用新的信息论量“广义有向信息”进行定义，并揭示了其与“赋能”的基本联系。这项工作为理解智能体如何被环境塑造提供了理论基础，对人工智能和认知科学具有基础意义。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-eozfqye9ok/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1414, \"height\": 392, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eozfqye9ok/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1253, \"height\": 352, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eozfqye9ok/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1011, \"height\": 483, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eozfqye9ok/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1349, \"height\": 464, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-eozfqye9ok/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1466, \"height\": 1720, \"label\": \"Table\"}]"
motivation: 现有理论侧重于智能体影响未来的能力（赋能），但忽略了其受过去影响的程度（可塑性），本文旨在确立这一概念。
method: 通过提出一系列期望性质，定义了一个名为“广义有向信息”的信息论量来量化可塑性。
result: 证明了该新量严格推广了有向信息，并建立了可塑性与赋能之间的深层联系。
conclusion: 可塑性是智能体的基础维度，与赋能互补，为统一智能体理论提供了新视角。
---

## Abstract
Agents are minimally entities that are influenced by their past observations and act to influence future observations. This latter capacity is captured by empowerment, which has served as a vital framing concept across artificial intelligence and cognitive science. This former capacity, however, is equally foundational: In what ways, and to what extent, can an agent be influenced by what it observes? In this paper, we ground this concept in a universal agent-centric measure that we refer to as plasticity, and reveal a fundamental connection to empowerment. Following a set of desiderata on a suitable definition, we define plasticity using a new information-theoretic quantity we call the generalized directed information. We show that this new quantity strictly generalizes the directed information introduced by Massey (1990) while preserving all of its desirable properties. Under this definition, we find that plasticity is well thought of as the mirror of empowerment: The two concepts are defined using the same measure, with only the direction of influence reversed. Our main result establishes a tension between the plasticity and empowerment of an agent, suggesting that agent design needs to be mindful of both characteristics. We explore the implications of these findings, and suggest that plasticity, empowerment, and their relationship are essential to understanding agency.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：如何从信息论角度统一刻画智能体的两种基础能力——**被环境塑造的能力（可塑性，Plasticity）** 和**塑造未来的能力（赋能，Empowerment）**，并揭示二者之间存在的内在张力。
- **研究背景**：赋能（Klyubin et al., 2005）已被广泛用于解释内在动机、技能发现、社会影响等；可塑性在神经科学、生物学和机器学习中均有重要地位（如突触可塑性、稳定性-可塑性困境、持续学习中的塑性丧失）。然而，这两个概念此前缺乏统一的数学框架和相互关系的深度分析。
- **整体含义**：本文通过引入新的信息论量——**广义有向信息（Generalized Directed Information, GDI）**，给出了可塑性的普适定义，并证明可塑性与赋能互为“镜像”，且二者之和存在严格上界，从而揭示了智能体设计必须权衡这两种能力。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：利用信息论中的有向信息（Directed Information）的对称性，将智能体受观测影响的程度（可塑性）与智能体影响观测的能力（赋能）统一在同一个数学表述中，仅方向相反。
- **关键技术细节**：
    - **广义有向信息（GDI）**：定义为  
      \[
      I(X_{a:b} \rightarrow Y_{c:d}) = \sum_{i=\max(a,c)}^{d} I(X_{a:\min(b,i)}; Y_i \mid X_{1:a-1}, Y_{1:i-1})
      \]  
      它严格推广了 Massey (1990) 的有向信息，允许任意长度的子序列，并保留了非负性、时间一致性、区间可分解性以及守恒律等性质。
    - **可塑性（Plasticity）定义**：  
      \[
      P_{a:b}^{c:d}(\lambda, \mathcal{E}) = \max_{e \in \mathcal{E}} I(O_{a:b} \rightarrow A_{c:d})
      \]  
      即观测序列对动作序列的有向信息在环境集上的最大值。
    - **赋能（Empowerment）定义**：  
      \[
      E_{a:b}^{c:d}(\Lambda, e) = \max_{\lambda \in \Lambda} I(A_{a:b} \rightarrow O_{c:d})
      \]  
      同样是GDI的特例。
- **关键公式与定理**：
    - **守恒律**（Theorem 3.5）：  
      \[
      I(X_{a:b}; Y_{c:d} \mid X_{1:a-1}, Y_{1:c-1}) = I(X_{a:b} \rightarrow Y_{c:d}) + I(Y_{c:d} \rightarrow X_{a:b})
      \]  
    - **可塑性与赋能之间的张力**（Theorem 4.8）：  
      \[
      E_{a:b}^{c:d}(\lambda, e) + P_{c:d}^{a:b}(\lambda, e) \leq m,
      \]  
      其中 \( m = \min\{(b-a+1)\log|O|, (d-c+1)\log|A|\} \)，且该上界是紧的。

## 3. 实验设计：使用的数据集/场景、benchmark、对比方法

- **实验场景**：使用**二臂伯努利赌臂问题（Two-armed Bernoulli Bandit）**，智能体采用**表格Q学习（Tabular Q-learning）**。
- **实验内容**：
    - **实验1**：改变探索参数 \(\epsilon\)（从0到1），估计可塑性在时间区间 \([1:3] \to [2:5]\) 上的值。
    - **实验2**：改变初始Q值（从-1到1的乐观/悲观），同时估计可塑性和赋能，并观察二者之和是否不超过上界。
- **对比方法**：没有与其他方法对比，主要是验证理论结果（可塑性随\(\epsilon\)变化、赋能随初始Q值变化、和的上界成立）。

## 4. 资源与算力

- **文中说明**：实验在**单个CPU**上运行，未提及GPU型号、数量或具体训练时长。
- **备注**：由于实验规模极小（二臂赌博机 + 表格Q学习），算力需求很低。

## 5. 实验数量与充分性

- **实验数量**：共两组实验（\(\epsilon\)扫描和初始Q值扫描），每组给出均值与置信区间。
- **充分性评估**：
    - **优点**：实验直观地验证了理论预测（可塑性随随机性增加而下降；乐观/悲观影响赋能和可塑性；二者之和不超过上界）。
    - **不足**：实验仅作“接地”的简单验证，未涉及复杂环境、深度神经网络、持续学习或稳定性-可塑性困境等更贴近实际应用的场景。因此，**实验数量较少，覆盖面有限**，不能充分证明理论在实际复杂系统中的适用性。

## 6. 论文的主要结论与发现

1. **可塑性是赋能的信息论镜像**（Proposition 4.6）：交换观测和动作的角色，可塑性与赋能的定义完全对偶。
2. **可塑性与赋能存在基本张力**（Theorem 4.8）：在同一时间区间上，二者之和受限于界面大小和区间长度的对数，不能同时最大化。
3. **非零可塑性的充要条件**（Lemma 4.2）：存在某个时刻，观测可以降低动作的不确定性。
4. **可塑性的直观性质**（Theorem 4.3）：非负性、确定性智能体也可具有正可塑性、环境集单调性，以及常量/开环/仅依赖于历史长度的智能体可塑性为零。
5. **GDI的独立性价值**：GDI作为信息论新工具，可用于更广泛的反馈系统分析。

## 7. 优点

- **理论贡献扎实**：给出了可塑性的第一个信息论精确定义，并建立了与赋能之间的深层联系，为智能体理论提供了统一视角。
- **数学严密**：提出的GDI满足所有期望的守恒律、上界和分解性质，证明完整。
- **对设计具有指导意义**：揭示了可塑性与赋能之间的权衡，提示在实际智能体设计中需要平衡二者（例如，过度优化赋能可能损害可塑性，反之亦然）。
- **讨论丰富**：论文讨论了塑性定义的多种变体（基于策略、内部状态等），以及目标导向、因果干预、多智能体等扩展方向，展现了该框架的泛化潜力。

## 8. 不足与局限

- **实验验证薄弱**：仅有两个简单赌博机实验，未涉及高维状态、深度网络、持续学习等实际场景，难以评估理论在实际系统中的预测力。
- **假设限制**：GDI基于有限离散随机变量和固定时间区间，向连续状态/动作空间、无限时间水平或部分可观测马尔可夫过程的推广需进一步研究。
- **可操作性不足**：论文未提供高效的GDI估算器（虽然有提及Jiao等人(2013)的通用估计思路但未实现），限制了实际应用。
- **潜在偏差风险**：实验仅使用了Q学习一种算法，不同算法（如策略梯度、深度Q网络）对可塑性/赋能的影响可能不同，未做对比。
- **应用边界**：文中强调“张力”在相同区间上存在，但若区间错开（如先高塑性后高赋能），则张力可能消失。实际设计中如何调度这两个阶段未深入讨论。

（完）
