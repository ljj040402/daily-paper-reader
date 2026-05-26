---
title: Learning Interestingness in Automated Mathematical Theory Formation
title_zh: 自动化数学理论发现中的趣味性学习
authors: "George Tsoukalas, Rahul Saha, Amitayush Thakur, Sabrina Reguyal, Swarat Chaudhuri"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=RespmwOoCH"
tags: ["query:ai"]
score: 6.0
evidence: 强化学习用于自动数学理论发现，人工智能研究
tldr: 自动发现新数学理论是人工智能的重大挑战，现有方法难以有效评估数学对象的趣味性。本文首先提出Fermat环境，将概念发现和定理证明建模为强化学习问题；然后基于大语言模型的进化算法，自动合成非平凡的趣味性度量。在初等数论和有限域领域，该方法显著优于基线，推动了开放数学发现的前沿。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-respmwooch/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 694, \"height\": 336, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-respmwooch/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1063, \"height\": 705, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-respmwooch/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1395, \"height\": 485, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-respmwooch/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 742, \"height\": 662, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-respmwooch/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1173, \"height\": 1100, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-respmwooch/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1271, \"height\": 1254, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-respmwooch/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 618, \"height\": 2405, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-respmwooch/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1444, \"height\": 67, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-respmwooch/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1451, \"height\": 67, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-respmwooch/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1455, \"height\": 287, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-respmwooch/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1550, \"height\": 2361, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-respmwooch/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 974, \"height\": 497, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-respmwooch/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1466, \"height\": 154, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-respmwooch/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1094, \"height\": 535, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-respmwooch/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1355, \"height\": 296, \"label\": \"Table\"}]"
motivation: 自动数学理论发现需要有效评估新概念的趣味性，但现有方法定义模糊。
method: 构建Fermat强化学习环境，并利用大语言模型进化算法自动合成趣味性度量。
result: 在初等数论和有限域发现中显著优于基线。
conclusion: 结合强化学习与大语言模型能有效自动化数学理论发现中的趣味性评估。
---

## Abstract
We take two key steps in automating the open-ended discovery of new mathematical theories, a grand challenge in artificial intelligence. First, we introduce Fermat, a reinforcement learning (RL) environment that models concept discovery and theorem-proving using a set of symbolic actions, opening up a range of RL problems relevant to theory discovery. Second, we explore a specific problem through Fermat: automatically scoring the interestingness of mathematical objects. We investigate evolutionary algorithms for synthesizing nontrivial interestingness measures. In particular, we introduce an LLM-based evolutionary algorithm that features function abstraction, leading to notable improvements in discovering elementary number theory and finite fields over hard-coded baselines. We open-source the \fermat environment at github.com/trishullab/Fermat.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：自动数学理论发现是人工智能领域的长期挑战。当前AI系统主要擅长解决预定义问题（如定理证明、程序搜索），但数学家通过开放式的过程——定义新概念、研究性质、提出猜想、证明或反驳——来发展理论。这个过程的关键瓶颈是如何引导搜索，因为可能的定义和猜想空间组合爆炸，多数路径导向平凡或无趣的数学对象。人类数学家依靠一种细腻的“趣味性”（interestingness）直觉来判断科学潜力。论文旨在将这种直觉自动化，实现开放式数学理论发现。

- **研究背景**：已有工作如HR系统使用硬编码的启发式规则，但缺乏对趣味性的学习能力；AlphaProof等现代方法侧重于问题求解而非理论构建。本文试图填补这一空白，提供一个强化学习（RL）框架，并学习可编程的趣味性度量。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：
  1. 将数学理论发现形式化为马尔可夫决策过程（MDP），构建FERMAT环境。
  2. 趣味性（interestingness）作为内在奖励函数，引导策略搜索。引入EvoAbstract算法，通过LLM驱动的进化搜索和抽象学习自动合成趣味性度量。

- **关键技术细节**：
  - **FERMAT环境**：
    - 状态：知识图（节点为数学实体：定义、猜想、定理；边为依赖关系）。
    - 动作：定义生成动作（如Compose, Exists, Specialize等8种）、猜想生成动作（Implication, Equivalence等4种）、证明动作（prove/disprove，后端使用Z3 SMT求解器）。
    - 转移函数：符号化的确定性更新。
    - 外部奖励：仅当发现预定义的地面真值（ground truth）数学实体时给予+1。
    - 趣味性函数I(m, S)作为内在奖励，输入新实体和当前状态，输出标量分数。

  - **EvoAbstract算法**：
    - 采用LLM（GPT-4o-mini）驱动的进化搜索。
    - 使用岛屿模型（k=4个并行种群）保持多样性。
    - 核心创新：**抽象学习**。定期让LLM分析高分程序，提取可复用子程序（abstraction），存入每个岛屿的抽象库中，后续进化LLM被条件化为参考这些抽象。
    - 流程：进化步骤（LLM基于模板和父程序生成新候选）→ 抽象步骤（LLM生成新抽象）→ 策略评估步骤（在FERMAT中执行回合获得累积外部奖励作为适应度）。

  - **策略模板**：根据趣味性分数采样候选定义，枚举可能动作，模拟若干动作并选择最高分的执行。

- **公式**：核心优化目标为 \( I^* = \arg\max_I \mathbb{E}_{\tau \sim \pi_I}[\sum \gamma^t R_E(S_t, a_t)] \)，其中\(R_E\)为外部奖励。

## 3. 实验设计

- **场景与数据集**：
  - 初等数论（Number Theory）：180个地面真值实体（概念、猜想、定理），源自从入门数论教材[2]。
  - 有限域F₂₇：67个地面真值实体。
  - 三种初始知识图配置：
    - **succ_zero_eq**：仅零、后继、相等。
    - **arithmetic_base**：包含零、一、二、加法、乘法、除法、≤、相等。
    - **ff_27**：零、一、F₂₇的生成元。

- **基准（Baseline）**：
  - **随机策略**：均匀随机选择动作。
  - **HR Measures**：实现HR系统中5种硬编码趣味性度量（新颖性、简洁性、生产力、适用性、可理解性）及其等权组合。
  - **One-shot LLM**：直接采样64个GPT-4o程序并评估。
  - **FunSearch**：去掉抽象学习版本的EvoAbstract（相当于FunSearch算法），相同超参数。
  - **EvoAbstract**：完整方法。

## 4. 资源与算力

- **硬件**：64个Intel Xeon Platinum 8352Y CPU + 64个AMD EPYC 7413 24C CPU。未使用GPU（LLM推理通过API调用）。
- **时间**：
  - 单个趣味性度量评估（64个工作并行）约120秒。
  - 每次FunSearch/EvoAbstract运行（64代，每代评估多个程序）约18小时。
  - GPT-4o基线共6小时。
- **模型**：GPT-4o-mini（用于进化变异和抽象），GPT-4o（用于one-shot评估）。
- **算力说明**：文中未明确提及GPU型号/数量，因为LLM调用通过API，计算主要依赖CPU集群。

## 5. 实验数量与充分性

- **实验组数**：
  - EvoAbstract与FunSearch各运行4次独立重复（不同随机种子），报告平均值和标准差。
  - 每种基线（随机、HR Measures、GPT-4o）在三种初始配置上各评估64次（通过64次回合）。
  - 消融实验：FunSearch vs. EvoAbstract（有无抽象学习）。
  - 共3种初始配置 × 多种方法，形成了较全面的对比。

- **充分性与公平性**：
  - 所有方法使用相同环境、相同评估协议（64回合，每次60秒超时）。
  - EvoAbstract与FunSearch超参数相同，差异仅在于抽象学习。
  - 统计报告了均值和标准差，但未进行假设检验（如t检验），可视为合理充分。
  - 局限性：仅4次重复，可能受随机性影响；但结果趋势清晰，FunSearch和EvoAbstract显著优于其他基线。

## 6. 主要结论与发现

- EvoAbstract和FunSearch学到的趣味性度量显著优于所有硬编码HR度量和随机策略。在arithmetic_base上，EvoAbstract平均发现23.98个地面真值实体（FunSearch 22.41），远超随机(4.44)和最佳HR(Comprehensibility 8.55)。
- 抽象学习带来适度提升，尤其在arithmetic_base上，但方差较大；在其他两个任务中，EvoAbstract早期更快但后期可能因“抽象锁定”而性能不如FunSearch。
- GPT-4o one-shot表现仅略优于随机，表明直接生成有效趣味性度量困难，进化搜索不可或缺。
- 定性分析显示，EvoAbstract发现的趣味性度量包含许多可解释的子程序（如适用性变体、规则多样性分数、节点类型调整等），模块化程度高于FunSearch。
- 在生成理论方面，FERMAT成功发现了加法、乘法、整除、幂、质数等基本概念，但在复杂猜想（如偶数哥德巴赫猜想、有限域特征3）的发现上仍困难。

## 7. 优点

- **环境设计**：FERMAT将理论发现正式化为MDP，提供了可扩展的基准；DSL支持嵌套定义，Z3后端可验证猜想。
- **方法论创新**：EvoAbstract的抽象学习机制使趣味性度量模块化、可解释，且能复用成功模式，优于纯进化搜索。
- **实验结果强**：在三个不同起点上均大幅超越所有基线，展示进化行为不仅可行且必要。
- **开放资源**：开源FERMAT环境，便于后续研究。

## 8. 不足与局限

- **探索限制**：策略模板为了管理组合爆炸，仅暴露部分动作空间，可能错过有价值的长序列。
- **瓶颈实体**：如“质数”概念发现后，知识图急剧膨胀，导致后续计算成本高，有效动作被淹没。
- **冗余与对称**：未利用实体间的等价关系减少冗余，Z3检测等价计算成本高。
- **猜想发现弱**：成功发现的定义较多，但猜想（尤其是需要多层推理的）较少被正确发现，这可能是由于合理指定猜想的路径有限。
- **评估局限性**：仅依赖预定义地面真值集（人类已知概念），未测试完全新颖的发现；4次重复可能不足以完全刻画变异性。
- **计算资源**：实验依赖CPU集群和LLM API，对大规模进化可能昂贵；未探索更大预算下的性能。

（完）
