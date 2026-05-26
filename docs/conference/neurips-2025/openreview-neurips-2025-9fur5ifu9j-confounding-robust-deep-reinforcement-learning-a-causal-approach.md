---
title: "Confounding Robust Deep Reinforcement Learning: A Causal Approach"
title_zh: 混杂鲁棒的深度强化学习：一种因果方法
authors: "Mingxuan Li, Junzhe Zhang, Elias Bareinboim"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=9fUr5iFU9j"
tags: ["query:ai"]
score: 7.0
evidence: 基于因果方法的鲁棒深度强化学习，核心人工智能主题
tldr: 离线强化学习常因数据中存在未观测混杂因素而得到有偏策略，在高维领域尤为严重。本文在深度Q网络基础上，提出一种对混杂偏差鲁棒的深度强化学习算法，通过寻找与观测数据相容的最坏环境下的安全策略来对抗偏差。在12个存在混杂的Atari游戏上，该方法显著优于现有基线。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-9fur5ifu9j/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 629, \"height\": 293, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-9fur5ifu9j/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1422, \"height\": 421, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-9fur5ifu9j/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 277, \"height\": 399, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-9fur5ifu9j/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 783, \"height\": 423, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-9fur5ifu9j/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 784, \"height\": 391, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-9fur5ifu9j/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 786, \"height\": 368, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-9fur5ifu9j/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 805, \"height\": 274, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-9fur5ifu9j/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1450, \"height\": 1357, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-9fur5ifu9j/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1452, \"height\": 1823, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-9fur5ifu9j/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1454, \"height\": 1360, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-9fur5ifu9j/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1463, \"height\": 482, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-9fur5ifu9j/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1456, \"height\": 519, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-9fur5ifu9j/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1445, \"height\": 541, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-9fur5ifu9j/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1446, \"height\": 598, \"label\": \"Table\"}]"
motivation: 离线强化学习数据中未观测混杂因素会导致学习到的策略有偏。
method: 基于深度Q网络提出鲁棒算法，寻找最坏环境下的安全策略以对抗混杂偏差。
result: 在混杂Atari游戏上显著优于现有方法。
conclusion: 因果视角的鲁棒优化能有效提升离线强化学习对混杂偏差的抵抗力。
---

## Abstract
A key task in Artificial Intelligence is learning effective policies for controlling agents in unknown environments to optimize performance measures. Off-policy learning methods, like Q-learning, allow learners to make optimal decisions based on past experiences. This paper studies off-policy learning from biased data in complex and high-dimensional domains where \emph{unobserved confounding} cannot be ruled out a priori. Building on the well-celebrated Deep Q-Network (DQN), we propose a novel deep reinforcement learning algorithm robust to confounding biases in observed data. Specifically, our algorithm attempts to find a safe policy for the worst-case environment compatible with the observations. We apply our method to twelve confounded Atari games, and find that it consistently dominates the standard DQN in all games where the observed input to the behavioral and target policies mismatch and unobserved confounders exist.

---

## 论文详细总结（自动生成）

# 论文总结：Confounding Robust Deep Reinforcement Learning: A Causal Approach

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：在离线强化学习（off-policy RL）中，当数据由不同行为策略收集时，常常存在**未观测混杂因素（unobserved confounders）**，导致标准 Q-learning 等算法学到有偏策略。这一问题在高维复杂环境（如 Atari 游戏）中尤为突出。
- **研究动机**：传统 MDP 框架隐含地假设“无未观测混杂”（NUC），但实际场景中该假设脆弱。例如，学习者的观测受限（如部分屏幕被遮挡），而行为策略依赖完整信息（包括被遮挡部分），就会产生混杂偏差。
- **整体含义**：该工作尝试将因果推断中的**部分识别（partial identification）**方法引入深度强化学习，提出对混杂偏差鲁棒的离线策略学习算法，为安全、可靠的 AI 决策系统奠定基础。

## 2. 论文提出的方法论：核心思想、关键技术细节、算法流程
- **核心思想**：构建一个与观测数据相容的**最坏情况环境（worst-case environment）**，并学习在该环境下性能有保障的保守策略（pessimistic policy），从而获得对真实最优值函数的下界。
- **关键技术细节**：
  - 定义**混杂马尔可夫决策过程（CMDP）**，其中行为策略依赖于未观测混杂变量 U。
  - 推导**因果贝尔曼最优方程（Causal Bellman Optimality Equation）**（Proposition 3.1），给出最优值函数的下界：
    \[
    \underline{Q}^*(s,x) = P(x|s)\Big[\tilde{R}(s,x)+\gamma\sum_{s'}\tilde{T}(s,x,s')\max_{x'}\underline{Q}^*(s',x')\Big] + P(\neg x|s)\Big[a+\gamma\min_{s'}\max_{x'}\underline{Q}^*(s',x')\Big]
    \]
    其中 \(\tilde{T},\tilde{R}\) 为从观测数据中估计的名义转移和奖励函数，\(a\) 为奖励下界。
  - 该下界通过迭代更新，利用神经网络（Q-network）近似，从而训练出鲁棒的策略。
- **算法流程**：
  - 初始化经验回放缓冲区 D 和 Q-network 参数。
  - 在每轮 episode 中，观察行为策略的样本 \((s_t,x_t,y_t,s_{t+1})\)，存入 D。
  - 从 D 中采样 minibatch，对每个动作 x 构造目标值 \(w_i(x)\)：
    - 若 \(x=x_i\)：使用标准 Q-learning 目标 \(y_i+\gamma\max_{x'}Q^*(s_{i+1},x';\theta)\)。
    - 若 \(x\neq x_i\)：使用悲观目标 \(a+\gamma\min_{s'}\max_{x'}Q^*(s',x';\theta)\)。
  - 执行梯度下降最小化损失 \(\sum_x (w_i(x)-Q^*(s_i,x;\theta))^2\)。
  - 定期更新目标网络。
- **名称**：Causal Deep Q-Learning (Causal-DQN)，如 Algorithm 1 所示。

## 3. 实验设计：数据集/场景、benchmark、对比方法
- **场景**：12 个流行的 Atari 游戏（Amidar, Asterix, Boxing, Breakout, ChopperCommand, Gopher, KungFuMaster, MsPacman, Pong, Qbert, RoadRunner, Seaquest）。
- **混杂设计**：对游戏画面进行遮挡（mask），使学习者无法观察到行为策略赖以决策的关键信息（如对手位置、得分、雷达等），从而引入未观测混杂。
- **Benchmark**：以行为策略（demonstrator）的表现为参考，计算归一化平均回报和 IQM。
- **对比方法**：
  - **Conf. DQN**：使用混杂演示数据的标准 CNN-DQN。
  - **Conf. LSTM-DQN**：使用混杂演示数据的 LSTM-DQN。
  - **Interv. DQN**：在遮挡观测上直接进行在线交互训练的 DQN（不使用演示数据）。
  - 行为策略（demonstrator）本身作为上界。
  - 随机策略作为下界。
- **实验设置**：1M 环境步，20 个并行环境，batch size 512，replay buffer 100K，学习率 5e-4。

## 4. 资源与算力
- **计算资源**：使用 H100 GPU 进行训练。
- **训练时长**：每个游戏每个种子约 2 小时（使用 diamond 演示者），约 8 小时（使用 sebulba 演示者）。
- **内存**：小于 2 GB RAM。
- **总计算量**：12 个游戏 × 5 个种子 × 2 种演示者配置，总训练时长估计在数百 GPU 小时量级。

## 5. 实验数量与充分性
- **实验数量**：
  - 主实验：12 个 Atari 游戏，每个游戏 5 个随机种子，训练 1M 步。
  - 每个种子在训练过程中每 100K 步评估 10 个 episode，绘制学习曲线。
  - 包含两种演示者（diamond 和 sebulba）的对比。
  - 提供了归一化平均、中位数、IQM 及置信区间（bootstrap）。
- **充分性评估**：
  - **正面**：覆盖 12 个游戏，多样性较高；使用标准化评估协议（Agarwal et al. 2021）；报告了方差（标准差或置信区间）；进行了广泛的超参数调优。
  - **不足**：仅训练 1M 步（文章指出 Interv. DQN 在更长时间后可逐渐学习，但实验中未展示）；仅使用 DQN 作为基算法，未与更先进的非因果稳健 RL 方法（如 Robust FQI）或最新深度 RL（Rainbow, BBF）对比；未做消融实验分离各个组件（如上下界选择、min s' 的近似方式）。

## 6. 论文的主要结论与发现
- **主要发现**：Causal-DQN 在全部 12 个混杂 Atari 游戏中一致优于所有基线，且在 7/12 个游戏中甚至**超过了使用完整观测和更复杂架构的演示者**。
- **策略行为**：学习到的策略更加保守（如 Pong 中只关注球和自身球拍，Boxing 中采用“rope-a-dope”防守策略），避免依赖混杂特征。
- **样本效率**：Causal-DQN 能在约 1M 步内收敛，而在线 DQN（Interv. DQN）需要约 3M 步才开始学习，体现出 3 倍的样本效率提升。
- **归一化性能**：Causal-DQN 的归一化平均回报 1.04，归一化 IQM 1.02，接近甚至超过演示者水平（1.00）。

## 7. 优点：方法或实验设计上的亮点
- **方法创新**：
  - 将部分识别理论引入深度强化学习，推导出可实现的因果贝尔曼最优方程闭式解，无需求解复杂不确定性集。
  - 算法简单（仅在标准 DQN 基础上修改 target 构造），但效果显著，易于集成到其他深度 RL 方法。
- **实验亮点**：
  - 设计了具有实际意义的混杂场景（遮挡），并通过 saliency map 验证了混杂存在。
  - 使用了两种不同演示者（diamond 和 sebulba），验证方法对演示者质量的鲁棒性。
  - 全面报告了归一化指标和置信区间，遵循 NeurIPS 评估建议。

## 8. 不足与局限
- **实验覆盖**：
  - 仅测试离散动作的 DQN，未扩展到连续控制、policy gradient 方法或多智能体。
  - 未在更大规模或现实世界任务（如机器人、医疗、RLHF）中验证。
- **方法局限**：
  - 下界推导假设单个时间步的 Q 值，未覆盖多步 returns 或 eligibility traces。
  - 当演示者策略在遮挡区域没有支持（即所有有效行为都在遮挡区域中），Causal-DQN 无法学习（如 Boxing 右半场被遮挡但演示者始终在右半场活动）。
  - 面对随机性较大的演示者（如分布策略），确定性 DQN 学习效果下降。
- **偏差风险**：
  - 下界估计依赖 min s' 的近似（实际中通过随机采样估计），可能引入额外误差。
  - 假设奖励下界 a 已知，在真实应用中可能不准确。
- **未明确说明**：
  - 代码未公开（仅提及将提供）。
  - 没有与现有“鲁棒强化学习”（如 Robust MDP）方法对比。

（完）
