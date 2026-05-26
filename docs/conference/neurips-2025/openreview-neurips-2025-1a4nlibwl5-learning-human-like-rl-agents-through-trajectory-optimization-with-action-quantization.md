---
title: Learning Human-Like RL Agents Through Trajectory Optimization With Action Quantization
title_zh: 通过轨迹优化与动作量化学习类人强化学习智能体
authors: "Jian-Ting Guo, Yu-Cheng Chen, Ping-Chun Hsieh, Kuo-Hao Ho, Po-Wei Huang, Ti-Rong Wu, I-Chen Wu"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=1A4Nlibwl5"
tags: ["query:ai"]
score: 6.0
evidence: 强化学习算法
tldr: 针对强化学习智能体行为不自然的问题，本文提出通过轨迹优化与动作量化来学习类人行为。方法将类人性建模为轨迹优化目标，并采用滚动视野控制来高效求解。实验表明该方法能生成更接近人类的行为序列，提升了可解释性和可信度。这一工作为设计类人智能体提供了新思路。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-1a4nlibwl5/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1383, \"height\": 352, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1a4nlibwl5/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 916, \"height\": 724, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1a4nlibwl5/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1368, \"height\": 423, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1a4nlibwl5/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1431, \"height\": 519, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1a4nlibwl5/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1233, \"height\": 533, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1a4nlibwl5/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1262, \"height\": 976, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1a4nlibwl5/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1282, \"height\": 994, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1a4nlibwl5/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1283, \"height\": 992, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1a4nlibwl5/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1281, \"height\": 994, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1a4nlibwl5/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1435, \"height\": 375, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1a4nlibwl5/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1291, \"height\": 589, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1a4nlibwl5/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 936, \"height\": 1188, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1a4nlibwl5/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1089, \"height\": 623, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1a4nlibwl5/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1089, \"height\": 872, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-1a4nlibwl5/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1298, \"height\": 828, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-1a4nlibwl5/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1301, \"height\": 785, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-1a4nlibwl5/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 634, \"height\": 379, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-1a4nlibwl5/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1442, \"height\": 412, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-1a4nlibwl5/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1002, \"height\": 189, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-1a4nlibwl5/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1365, \"height\": 927, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-1a4nlibwl5/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1285, \"height\": 283, \"label\": \"Table\"}]"
motivation: 现有强化学习智能体虽性能超人类，但行为不自然，缺乏可解释性和可信度。
method: 将类人性作为轨迹优化目标，结合动作量化和滚动视野控制来近似求解。
result: 生成的智能体行为在人类相似度指标上明显优于传统强化学习方法。
conclusion: 所提方法有效提升了强化学习智能体的人类似性，为类人AI设计提供了可行框架。
---

## Abstract
Human-like agents have long been one of the goals in pursuing artificial intelligence.
Although reinforcement learning (RL) has achieved superhuman performance in many domains, relatively little attention has been focused on designing human-like RL agents.
As a result, many reward-driven RL agents often exhibit unnatural behaviors compared to humans, raising concerns for both interpretability and trustworthiness.
To achieve human-like behavior in RL, this paper first formulates human-likeness as trajectory optimization, where the objective is to find an action sequence that closely aligns with human behavior while also maximizing rewards, and adapts the classic receding-horizon control to human-like learning as a tractable and efficient implementation.
To achieve this, we introduce Macro Action Quantization (MAQ), a human-like RL framework that distills human demonstrations into macro actions via Vector-Quantized VAE.
Experiments on D4RL Adroit benchmarks show that MAQ significantly improves human-likeness, increasing trajectory similarity scores, and achieving the highest human-likeness rankings among all RL agents in the human evaluation study.
Our results also demonstrate that MAQ can be easily integrated into various off-the-shelf RL algorithms, opening a promising direction for learning human-like RL agents. 
Our code is available at https://rlg.iis.sinica.edu.tw/papers/MAQ.

---

## 论文详细总结（自动生成）

## 论文详细中文总结

### 1. 核心问题与整体含义（研究动机和背景）

- **问题**：现有深度强化学习（RL）智能体虽然能在许多任务中达到超人类水平，但其行为往往与人类动作模式差异显著，表现为抖动、旋转、不自然的抓取等，导致可解释性和可信度下降。
- **背景**：类人智能体是AI的长期目标（如图灵测试），但在RL领域尚未得到充分研究。已有工作要么依赖手工设计的约束（如惩罚非自然动作），要么通过模仿学习直接复制人类行为，但前者需要大量手工工程，后者性能受限于演示质量，难以兼顾类人性和任务成功率。
- **突破口**：论文首次将类人性正式定义为**轨迹优化问题**——寻找既最大化回报、又最接近人类行为序列的动作序列，并采用滚动时域控制（Receding-Horizon Control）实现高效求解。

### 2. 方法论：核心思想、关键技术细节

- **核心思想**：将人类演示中的动作模式蒸馏为“宏观动作”（macro actions，即连续动作序列），并将原始RL的原始动作空间替换为这些宏观动作的离散码本。智能体在离散码本上选择索引，从而强制其行为限定在人类行为流形内。
- **关键技术**：
  1. **条件VQ-VAE（Conditional Vector-Quantized VAE）**：以当前状态 \( s_t \) 为条件，输入长度为 \( H \) 的宏动作 \( m_t = (a_t, a_{t+1}, ..., a_{t+H-1}) \)，训练编码器-解码器结构，学习一个包含 \( K \) 个离散嵌入向量的码本。每个嵌入对应一个典型的人类行为片段。
  2. **训练损失**：包含重构损失（\( \|m - \hat{m}\|^2 \)）、代码本损失（\( \|\text{sg}[e] - e_k\|^2 \)）和承诺损失（\( \|e - \text{sg}[e_k]\|^2 \)），\( \beta \) 控制承诺损失权重。
  3. **在线RL集成**：原始RL算法（如IQL、SAC、RLPD）的动作为输出码本索引 \( k \)，策略 \( \pi_\theta \) 输出 \( K \) 个logits。选择索引后，从码本取出对应嵌入 \( e_k \)，与状态 \( s_t \) 一起输入解码器，重建宏动作 \( \hat{m}_t \) 并执行。环境返回累积奖励 \( R(s_t, m_t) = \sum_{i=t}^{t+H-1} \gamma^{i-t} r(s_i, a_i) \)。
  4. **滚动时域控制**：在每个决策步 \( t \)，优化长度为 \( H \) 的宏动作序列（即通过码本选择），执行整个宏动作后，在下一个状态 \( s_{t+H} \) 重新规划（commit-and-replan）。这等价于在人类行为流形上做短视优化，兼顾类人性和在线适应性。

- **算法流程**：① 从人类演示中提取宏动作 → ② 训练条件VQ-VAE，获得码本 → ③ 将任意RL算法的动作空间改为码本索引，重写累积奖励为宏动作上的累计奖励 → ④ 训练RL策略。

### 3. 实验设计

- **数据集与场景**：D4RL中的Adroit任务（四个连续控制任务）：
  - **Door**：开门；**Hammer**：钉钉子；**Pen**：旋转笔；**Relocate**：搬运球。
  - 每个任务提供25条人类演示轨迹，按9:1分割为训练集和测试集。
- **对比方法**：
  - 基线：BC（行为克隆）、IQL（隐式Q学习）、SAC（软演员-评论家）、RLPD（高效在线RL+离线数据）。
  - 增强版：MAQ+IQL、MAQ+SAC、MAQ+RLPD（分别将MAQ集成到对应算法中）。
- **评价指标**：
  - **轨迹相似性**：动态时间规整（DTW，包括状态DTW_s和动作DTW_a）、Wasserstein距离（WD_s, WD_a）。均归一化为[0,1]（1表示最像人类）。
  - **任务成功率**（Success）。
  - **人类评估**：19名评估者进行图灵测试（二选一，判断哪个更像人类）和类人性排名测试（多对比较）。
- **消融实验**：
  - 宏动作长度 \( H=1,...,9 \)。
  - 码本大小 \( K=8,16,32 \)。
  - 演示质量（随机子集、最低回报子集）。
  - 环境步数限制（Hammer任务增加最大步数至450）。

### 4. 资源与算力

- **硬件**：一台机器配备Intel E5-2678 CPU和4×NVIDIA GeForce GTX 1080 Ti GPU。
- **训练时间**：
  - VQVAE：<5分钟。
  - MAQ+IQL：约9 GPU小时（训练步数2M，因包含离线+在线阶段）；IQL基线约8 GPU小时。
  - MAQ+SAC、MAQ+RLPD：各约1 GPU小时（8个并行环境）；对应基线SAC约1小时，RLPD约1小时。
- **推理时间**（表5）：MAQ+RLPD的单步推理时间约0.81 ms，虽比原始RLPD（0.28 ms）长，但执行宏动作(9步)只需一次前向，总推理成本可能更低。论文指出MAQ在某些情况下可降低总推理时间。

### 5. 实验数量与充分性

- **数量**：
  - 主实验：4个任务 × 7个方法 × 3个随机种子 = 84组实验。
  - 消融实验：宏动作长度（9种）× 码本大小（3种）× 3个MAQ变体，共81组；演示质量消融（4种子集 × 4任务 = 16组）；环境步数消融（2×1组）。
  - 人类评估：19名评估者，每人Turing Test问题28个（7个智能体×4任务），排名测试约17对，共约×19人次。
- **充分性**：实验涵盖了主要对比、多种超参搜索和鲁棒性测试，定量指标与人类主观评价结合，设计较为严谨。但**仅在一个基准（Adroit）上测试**，未扩展到其他领域（如游戏、机器人导航），通用性有待证实。此外，人类评估样本量较小（19人），可能引入个体偏差。

### 6. 主要结论与发现

1. **类人性显著提升**：MAQ在所有四个任务上极大提高了轨迹相似性分数（DTW和WD）。例如，在Door任务中，MAQ+IQL的DTW_s从0.43提升至0.84，MAQ+SAC从-0.39提升至0.80，MAQ+RLPD从-0.06提升至0.76。
2. **任务成功率保持或改善**：MAQ在多数任务上未明显牺牲成功率，部分任务（如Door）成功率甚至大幅提升（从0.16到0.93）。Hammer任务中MAQ+RLPD成功率低于RLPD（0.56 vs 1.0），但通过增加最大步数可提升至0.72。
3. **人类评估一致**：图灵测试中MAQ+RLPD平均胜率39%，高于所有基线（最高24%）；类人性排名中MAQ+RLPD以71%胜率仅次于人类（74%），表明评估者难以区分MAQ智能体与人类。
4. **宏动作长度影响**：更长的宏动作（H=9）带来更高的相似度和成功率，说明时序扩展有利于类人规划。
5. **可即插即用**：MAQ能无缝集成到IQL、SAC、RLPD等多种算法中，无需修改算法核心。

### 7. 优点

- **创新性**：首次将类人性形式化为轨迹优化问题，并利用VQVAE将连续动作空间离散化为结构化宏动作码本，是一种优雅的类人约束实现。
- **通用性**：不依赖特定RL算法，任何策略都可方便地替换动作空间，适用范围广。
- **实验全面**：包含定量指标、人类主观评估、多维度消融（长度、码本大小、演示质量、环境设置），结果具有说服力。
- **可解释性**：通过人类评估中的文字反馈，揭示了MAQ为何被认为更像人类（如握持稳定、多次敲击等具体行为特征），增强了方法可信度。
- **性能平衡**：在保持甚至提升成功率的同时显著增强类人性，克服了模仿学习牺牲性能的缺陷。

### 8. 不足与局限

- **演示依赖**：方法完全依赖人类演示的质量和数量。若演示数量少或质量差，MAQ效果可能受限。论文虽做了子集消融，但未对比零演示情况。
- **领域狭窄**：仅在Adroit控制任务上验证，未在游戏（如Atari、StarCraft）或导航任务上测试，通用性存疑。
- **计算开销**：MAQ的VQVAE训练和在线RL中解码器前向有一定额外开销，尤其在H较大时，码本搜索可能成为瓶颈。
- **成功率折损**：在Hammer任务上，MAQ+RLPD若使用默认步数限制，成功率远低于RLPD。虽然可通过延长步数缓解，但环境设定限制可能导致不公平对比。
- **人类评估样本量**：19名评估者可能不足，且未详细说明评估者背景和随机化细节，存在偏差风险。
- **代码未开源**：论文仅承诺接收后开源，可复现性暂未完全保障。

（完）
