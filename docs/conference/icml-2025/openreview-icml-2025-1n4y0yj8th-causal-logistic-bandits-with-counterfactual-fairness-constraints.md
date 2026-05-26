---
title: Causal Logistic Bandits with Counterfactual Fairness Constraints
title_zh: 带有反事实公平约束的因果逻辑赌博机
authors: "Jiajun Chen, Jin Tian, Christopher John Quinn"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=1N4Y0Yj8th"
tags: ["query:ai"]
score: 6.0
evidence: ICML 2025关于顺序决策中AI公平性的论文
tldr: 该论文研究因果逻辑赌博机中的公平决策问题，提出结合反事实公平约束的算法。利用原始-对偶优化处理未知的非线性约束，理论证明亚线性遗憾上界。在合成数据上验证了算法在保证公平的同时有效学习策略，为公平AI决策提供了新框架。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-1n4y0yj8th/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 567, \"height\": 491, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-1n4y0yj8th/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1747, \"height\": 495, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-1n4y0yj8th/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1359, \"height\": 543, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-1n4y0yj8th/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1772, \"height\": 501, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-1n4y0yj8th/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1768, \"height\": 500, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-1n4y0yj8th/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1802, \"height\": 596, \"label\": \"Table\"}]"
motivation: 顺序决策中公平性定义和约束学习不足。
method: 将反事实公平约束纳入因果逻辑赌博机，采用原始-对偶方法在线学习未知约束。
result: 获得亚线性遗憾保证，并在实验中保持公平性。
conclusion: 为公平AI决策提供了可理论保证的在线学习算法。
---

## Abstract
Artificial intelligence will play a significant role in decision making in numerous aspects of society. Numerous fairness criteria have been proposed in the machine learning community, but there remains limited investigation into fairness as defined through specified attributes  in a sequential decision-making framework.  In this paper, we focus on causal logistic bandit problems where the learner seeks to make fair decisions, under a notion of fairness that accounts for counterfactual reasoning.  We propose and analyze an algorithm by leveraging primal-dual optimization for constrained causal logistic bandits where the non-linear constraints are a priori unknown and must be learned in time.  We obtain sub-linear regret guarantees with leading term similar to that for  unconstrained logistic bandits (Lee et al., 2024)  while guaranteeing sub-linear constraint violations.   We show how to achieve zero cumulative constraint violations with a small increase in the regret bound.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：人工智能在顺序决策（如招聘、推荐系统）中日益重要，但现有公平性研究多关注一步奖励或基于经验风险的“功德公平”，较少考虑基于**指定属性**（如性别、种族）的**反事实公平**。本文希望在线决策过程中，不仅最大化累积奖励，还要确保决策的反事实公平——即如果指定属性取不同值，结果不会显著改变。
- **研究背景**：将问题建模为**带约束的因果逻辑赌博机**：每个时间步，学习器观察到包含敏感属性、混杂特征、中间特征的上下文，选择一个决策，获得二元奖励；奖励由逻辑回归模型生成，其中参数未知；反事实公平约束定义为实际决策下期望奖励与反事实干预下期望奖励之差的绝对值不超过阈值τ。该约束是参数θ*的非线性函数，且未知，必须在学习过程中估计。
- **整体含义**：这是首次在逻辑赌博机中处理未知的非线性反事实公平约束，并给出亚线性遗憾和亚线性约束违反保证的算法，弥补了先前工作（如Huang et al. 2022b）需要已知安全决策子集的不足。

## 2. 方法论

### 核心思想
- 采用**原始-对偶优化**框架，同时优化累积奖励和约束违反。每个时间步，利用置信集（基于改进的对数似然损失）估计参数θ*，用乐观估计选择动作，并通过惩罚项（ϕₜ乘以约束违反）调整决策。
- 通过**遗憾-置信集转换**（regret-to-confidence-set conversion）构造凸置信集，得到更紧的半径，从而改进遗憾界。
- 引入**截断参数ρ**和**Slater约束规范条件**（存在一个随机策略使平均约束违反严格小于0），证明算法可以实现亚线性遗憾（与无约束逻辑赌博机Lee et al. 2024相近）和亚线性累积约束违反。进一步，通过引入用户选择的紧度参数ϵ，可以牺牲少量遗憾换取零累积约束违反。

### 关键技术细节
1. **模型结构**：使用扩展的标准公平模型（SFM）因果图。奖励Y与特征Z满足 logistic 关系：E[Y|Z] = g(f(Z)ᵀθ*)，其中g是sigmoid函数。反事实公平约束|Δ_d(X_t)| ≤ τ，其中Δ_d(X_t) = g(f(Z_d)ᵀθ*) - g(f(Z'_d)ᵀθ*)，Z'_d是替换敏感属性后的特征。
2. **置信集**：基于最大似然估计构造。采用Lee et al. (2024)改进的损失差置信集：C_t(α) = {θ: L_t(θ)-L_t(ˆθ_t) ≤ β_t(α)²}，其中β_t(α) = √(10n log(St/2n+e)+2((e-2)+S)log(1/α))。该置信集保证了θ*以高概率落入。
3. **算法流程（CCLB Algorithm 1）**：
   - 每轮t，观察上下文X_t。
   - 更新MLE估计ˆθ_t，构建置信集C_t(α)。
   - 选择乐观参数˜θ_t = argmax_{θ∈C_t} max_{d∈D} g(f(Z_d)ᵀθ)。
   - 选取动作d_t = argmax_{d∈D} [g(f(Z_d)ᵀ˜θ_t) - ϕ_t(|Δ̂_d(X_t)| - τ)]，其中ϕ_t是当前对偶变量，Δ̂_d是用˜θ_t计算的估计约束违反。
   - 更新对偶变量：ϕ_{t+1} = Proj_{[0,ρ]}[ϕ_t + (1/η)(|Δ̂_{d_t}(X_t)| - τ)]，其中η=√T/ρ。
4. **理论保证**：
   - 遗憾界：R⁺(T) = Õ(ρ n S √T + ρ n² S² κ_Z + ρ √T)。
   - 约束违反界：V(T) = Õ(n S √T + n² S² κ_Z + √T)。
   - 通过引入紧度参数ϵ，可达到零累积违反（Proposition 4），代价是遗憾增加O(ρ√T (1+ϵ)²)。

## 3. 实验设计

### 数据集/场景
- 使用**合成数据集**，基于修改的Plecko & Bareinboim (2024)中的结构因果模型生成。变量包括：敏感属性A（二元）、混淆特征W、中间特征M、20个候选决策D₁,…,D₂₀、二元奖励Y。每个时间步生成20个特征向量及其反事实对应向量。通过拒绝采样确保至少12个动作是可行的。

### Benchmark与对比方法
- **GLM-UCB** (Filippi et al., 2010)：无约束广义线性赌博机。
- **OFULog+** (Lee et al., 2024)：无约束逻辑赌博机（当前最先进）。
- **CCLB**（本文方法）：带反事实公平约束的因果逻辑赌博机（τ=0.2）。
- **ϵ-CCLB**（本文方法）：使用用户选定紧度参数ϵ（实验中取0.14）的变体（τ=0.2）。

### 评价指标
- 累积遗憾 (cumulative regret)
- 累积约束违反 (cumulative constraint violations)
- 惩罚累积遗憾 (penalized cumulative regret)：当动作违反约束时，其奖励计为0。

## 4. 资源与算力

论文中**未明确说明**使用的GPU型号、数量、训练时长等计算资源。实验仅在合成数据上运行，可推测算力需求较低。

## 5. 实验数量与充分性

- 进行了**一个主要实验**（Figure 2），比较四种方法在合成数据上的表现，展示了累积遗憾、累积约束违反和惩罚累积遗憾随回合数（T从1000到10000）的变化。
- 附录H中提供了**附加实验**：对ϵ-CCLB算法在不同ϵ值下的效果（Figure 4），以及对CCLB算法在不同公平阈值τ下的效果（Figure 5）。
- **充分性分析**：
  - 实验覆盖了所提方法的主要变体（CCLB和ϵ-CCLB）与两种强基线对比。
  - 但**仅使用单一合成数据集**，缺乏真实世界或多数据集验证，实验维度有限。
  - 未展示不同特征维度n、参数范数S、问题依赖常数κ_Z等关键参数变化对性能的影响。
  - 未与同样考虑反事实公平的Huang et al. (2022b)方法直接比较（因其代码未公开），但这种比较对全面评估有帮助。
  - 总体而言，实验设计**初步验证了方法的有效性**，但不足以全面证明其在不同场景下的鲁棒性。

## 6. 主要结论与发现

- 提出**CCLB算法**，首次在逻辑赌博机中处理未知的非线性反事实公平约束。
- 理论分析表明：CCLB的累积遗憾界与无约束逻辑赌博机（Lee et al. 2024）的领先项相同，同时获得亚线性约束违反。
- 通过引入紧度参数ϵ，可进一步实现**零累积约束违反**，仅以小幅遗憾增加为代价。
- 合成数据实验显示：CCLB和ϵ-CCLB在惩罚累积遗憾上显著优于无约束基线（GLM-UCB、OFULog+），表明在奖励与公平之间取得了有效权衡；ϵ-CCLB的约束违反增长近乎零。
- 随着公平阈值τ增大（更多动作可接受），累积约束违反下降；随着紧度参数ϵ增大，累积约束违反减少但遗憾增加。

## 7. 优点

- **理论创新**：首次将反事实公平约束纳入逻辑赌博机框架，给出严格遗憾与违反界，且领先项接近无约束情形。
- **方法论亮点**：采用原始-对偶优化与置信集技术，避免了需要预先知道安全动作的强假设（如Huang et al. 2022b），更适用于现实场景。
- **灵活性**：用户可通过参数ϵ在遗憾与约束违反之间进行可调节的权衡，甚至达到零违反。
- **实验设计**：将惩罚累积遗憾作为综合指标，直观展示了公平-效率权衡。

## 8. 不足与局限

- **实验局限**：
  - 仅使用**合成数据**，未在真实世界数据集（如招聘、推荐系统的实际数据）上验证。
  - 未与其他因果公平赌博机方法（如Huang et al. 2022b）直接比较（代码未公开）。
  - 实验参数范围有限（如仅测试一个τ和ϵ组合），敏感性分析不足。
- **算法局限**：
  - 假设因果图已知且变量可观测（未考虑未观测混杂）。
  - 要求特征映射f已知，且参数θ*在紧致集Θ内。
  - 要求Slater约束规范条件（存在严格可行的随机策略），这在某些应用中可能难以验证。
  - 计算复杂度每轮O(t)，与现有无约束逻辑赌博机相当，但未针对大规模决策集或高维特征进行优化。
- **应用限制**：
  - 反事实公平约束依赖于“如果敏感属性取不同值”的干预，需要因果图正确指定，且可能涉及无法观测的反事实。
  - 阈值τ的选择具有主观性，实验未探讨τ对公平与效率权衡的敏感度。
  - 方法主要针对二值奖励和逻辑模型，扩展到其他广义线性模型或多值奖励需要进一步研究。

（完）
