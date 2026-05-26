---
title: "Exploration from a Primal-Dual Lens: Value-Incentivized Actor-Critic Methods for Sample-Efficient Online RL"
title_zh: 从原始-对偶视角看探索：基于价值激励的演员-评论家方法实现样本高效在线强化学习
authors: "Tong Yang, Bo Dai, Lin Xiao, Yuejie Chi"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=A5Y8Uh5Szl"
tags: ["query:ai"]
score: 6.0
evidence: 在线强化学习中的探索-利用平衡方法
tldr: 该论文从原始-对偶优化的角度重新解释了强化学习中的乐观探索原则，提出了一种价值激励的演员-评论家方法，在理论上保证了在线RL的样本效率。通过将乐观正则化转化为优化问题，有效平衡了探索与利用。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-a5y8uh5szl/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1341, \"height\": 445, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-a5y8uh5szl/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1346, \"height\": 448, \"label\": \"Figure\"}]"
motivation: 在线强化学习中探索与利用的权衡缺乏高效且具有理论保证的实用方案。
method: 利用原始-对偶优化解释乐观探索，设计价值激励的演员-评论家算法。
result: 理论上保证了样本效率，实验验证了方法的有效性。
conclusion: 为RL中的探索提供了新视角和实用算法。
---

## Abstract
Online reinforcement learning (RL) with complex function approximations such as transformers and deep neural networks plays a significant role in the modern practice of artificial intelligence. Despite its popularity and importance, balancing the fundamental trade-off between exploration and exploitation remains a long-standing challenge; in particular, we are still in lack of efficient and practical schemes that are backed by theoretical performance guarantees. Motivated by recent developments in exploration via optimistic regularization, this paper provides an interpretation of the principle of optimism through the lens of primal-dual optimization. From this fresh perspective, we set forth a new value-incentivized actor-critic (VAC) method, which optimizes a single easy-to-optimize objective integrating exploration and exploitation --- it promotes state-action and policy estimates that are both consistent with collected data transitions and result in higher value functions. Theoretically, the proposed VAC method has near-optimal regret guarantees under linear Markov decision processes (MDPs) in both finite-horizon and infinite-horizon settings, which can be extended to the general function approximation setting under appropriate assumptions.

---

## 论文详细总结（自动生成）

# 论文中文详细总结

## 1. 核心问题与整体含义（研究动机和背景）
- **研究动机**：在线强化学习（Online RL）中，平衡探索与利用的权衡是一个长期挑战。现有方法如 $\epsilon$-greedy 随机探索效率低下，而理论上有保障的乐观方法（如基于置信集、Thompson 采样）往往计算复杂，难以与通用函数近似器（如深度神经网络、Transformer）结合。作者指出，虽然 MEX（Maximize to Explore）框架统一了估计、规划与探索，但其目标函数具有双层优化结构（bilevel optimization），实际优化困难。
- **核心贡献**：本文从原始-对偶（primal-dual）优化的视角重新审视乐观探索原则，提出了一种**价值激励的演员-评论家方法（VAC）**，通过单个易于优化的目标函数同时进行探索与利用，避免了双层优化。理论上在**线性MDP**下达到 $\tilde{O}(dH^2\sqrt{T})$ 的接近最优的遗憾界，并可推广到无限折扣与一般函数近似场景。

## 2. 方法论：核心思想、关键技术细节、算法流程（文字说明）
- **核心思想**：将价值最大化问题视为带有**Bellman一致性方程**约束的优化问题，构造正则化拉格朗日函数，通过重参数化技巧将对偶变量转化为 $\lambda(s,a) = (Q_f(s,a) - g(s,a))/\beta$，从而得到一个**非双层**的单目标函数。该目标由两部分组成：一是鼓励高价值的项 $V^\pi_f(\rho)$，二是惩罚Bellman误差的正则项 $\alpha L_t(f,\pi)$。正则项定义为历史数据上实际误差与最优拟合误差之差，类似MEX但使用策略相关的动作采样。
- **算法流程（VAC for finite-horizon MDP，Algorithm 1）**：
  1. 输入正则化系数 $\alpha>0$，初始化空数据集 $D_{0,h}$。
  2. 对每个 episode $t=1,\dots,T$：
     - **联合优化**：求解 $(f_t,\pi_t) = \arg\sup_{f\in\mathcal{Q},\pi\in\mathcal{P}} \{ V^\pi_f(\rho) - \alpha L_t(f,\pi) \}$，其中 $L_t(f,\pi)$ 由 $\sum_{h=1}^H \left[ \sum_{\xi_h\in D_{t-1,h}} \mathbb{E}_{a'\sim\pi_{h+1}}[(\cdot)^2] - \inf_{g\in\mathcal{Q}_h} \sum_{\xi_h} \mathbb{E}_{a'\sim\pi_{h+1}}[(\cdot)^2] \right]$ 给出。
     - **数据收集**：用 $\pi_t$ 运行一个episode，得到轨迹并加入数据集。
  3. 实践中可采用**演员-评论家**风格：固定策略 $\pi_{t-1}$ 优化评论家 $f_t$，再固定 $f_t$ 通过策略梯度更新策略。
- **关键技术细节**：
  - 与MEX不同，VAC的目标函数中 $L_t(f,\pi)$ 依赖于当前策略 $\pi$，而不是需要计算 $Q_f$ 下的最优值函数 $\max_a Q_f$，从而避免了双层优化。
  - 理论分析假设**线性MDP**（特征 $\phi(s,a)$ 已知），Q函数线性 $\langle \theta,\phi(s,a)\rangle$，策略为对率线性softmax策略。通过Freedman不等式、覆盖数论证和线性模型中的椭球引理推导遗憾上界。

## 3. 实验设计：数据集/场景、基准方法、对比方法
- **实验场景**：两个连续控制任务 from **MuJoCo**：**Ant-v4** 和 **Walker2d-v4**。
- **基准方法**：**Soft Actor-Critic (SAC)** 实现自 Stable-Baselines3 库。
- **对比方法**：**VAC**（本文方法）与 **SAC**（基线）对比。VAC仅在SAC的评论家损失函数中添加了价值激励项 $-\frac{1}{|B|}\alpha \sum_{s\in B} \frac{1}{N}\sum_i Q_{\theta_j}(s,a_i)$（用蒙特卡洛近似 $V^\pi_f(s)$），演员更新保持与SAC相同。

## 4. 资源与算力
- 文中**未明确说明**使用的GPU型号、数量、训练时长等硬件资源。仅描述每个任务训练1e6迭代，使用3个随机种子，但未提及具体计算平台。不过由于是MuJoCo连续控制任务，通常可在单GPU（如NVIDIA RTX 3090/4090）上数小时内完成。

## 5. 实验数量与充分性
- **实验数量**：每个任务做3个随机种子，共2个任务，即总计6次独立运行。
- **充分性评价**：
  - **充分方面**：展示了平均回报与最佳回报曲线，并附标准差（shaded area），说明稳定性。与SAC直接对比，消融了价值激励项的作用。
  - **不足方面**：
    - 仅对比了SAC一个基线，缺乏与其他探索方法（如 $\epsilon$-greedy SAC、噪声网络、MEX实现等）的比较。
    - 任务数量少（仅两个），未在高维或复杂环境（如Humanoid、Atari等）验证。
    - 未提供消融实验（如不同 $\alpha$ 取值的影响、$N=1$ vs 更大样本的效果）。
    - 未报告计算成本（时间、收敛速度）或超参数敏感性。

## 6. 主要结论与发现
- VAC在Ant-v4和Walker2d-v4上均优于纯SAC，**样本效率更高**（在相同训练步数下获得更高累计回报）。
- VAC的正则化项在早期探索阶段提供额外激励，使策略更快发现高奖励区域。
- 理论证明在**线性MDP**下VAC具有 $\tilde{O}(dH^2\sqrt{T})$ 的接近最优遗憾，验证了算法的理论有效性。

## 7. 优点
1. **理论‑实践桥梁**：从原始-对偶优化角度重新解释了乐观探索，使得算法自然兼容梯度优化，避免了之前MEX中的双层优化困难。
2. **简单易实现**：仅需在标准演员-评论家框架的评论家损失上添加一个价值激励项，无需修改演员更新，与现有深度学习工具链兼容。
3. **理论保证强**：在线性MDP下达到近最优遗憾，且可推广到无限折扣和一般函数近似（低GEC假设）。
4. **实验提升一致**：在两个MuJoCo任务上均显示出对SAC的稳定改进，标准差较小。

## 8. 不足与局限
1. **实验规模有限**：仅两个连续控制任务，缺乏对离散动作空间或视觉环境的验证，也未与其他先进探索方法（如RND、ICM、MEX）比较。
2. **消融分析不足**：未系统研究超参数 $\alpha$ 的敏感性、蒙特卡洛样本数 $N$ 的影响、以及不同网络架构下的表现。
3. **线性MDP假设较强**：理论上依赖线性特征和Bellman完备性，实际应用中特征可能非线性，理论保障的泛化性有待验证。
4. **计算资源未报告**：未提供训练时间、GPU型号等，不利于复现和效率评估。
5. **风险偏差**：仅与单个基线SAC对比，可能存在选择偏差（SAC默认参数可能不是最优）；且作者团队与Meta/Fundamental AI Research有关，可能倾向于展示正面结果。

（完）
