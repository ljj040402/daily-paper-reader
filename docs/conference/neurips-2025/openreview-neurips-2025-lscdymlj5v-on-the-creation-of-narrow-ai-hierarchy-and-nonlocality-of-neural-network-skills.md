---
title: "On the creation of narrow AI: hierarchy and nonlocality of neural network skills"
title_zh: 论窄AI的创建：神经网络技能的层次性与非局域性
authors: "Eric J Michaud, Asher Parker-Sartori, Max Tegmark"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=lscdYmLJ5v"
tags: ["query:ai"]
score: 6.0
evidence: 窄AI创建与神经网络技能层次
tldr: 该论文研究创建强而窄的AI系统时的两个挑战：一是为了学习某些窄技能，有时必须在广泛数据分布上训练（层次性）；二是技能表示的非局域性。这些发现对AI专业化和安全性有重要启示。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-lscdymlj5v/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1436, \"height\": 508, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lscdymlj5v/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 404, \"height\": 440, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lscdymlj5v/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1439, \"height\": 822, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lscdymlj5v/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1359, \"height\": 969, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lscdymlj5v/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1438, \"height\": 507, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lscdymlj5v/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1426, \"height\": 634, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lscdymlj5v/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 587, \"height\": 431, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lscdymlj5v/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1407, \"height\": 817, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lscdymlj5v/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1428, \"height\": 705, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lscdymlj5v/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1432, \"height\": 439, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lscdymlj5v/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1429, \"height\": 1362, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lscdymlj5v/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1386, \"height\": 696, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lscdymlj5v/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1320, \"height\": 571, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lscdymlj5v/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1421, \"height\": 512, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-lscdymlj5v/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1233, \"height\": 428, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lscdymlj5v/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 835, \"height\": 454, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lscdymlj5v/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 583, \"height\": 331, \"label\": \"Table\"}]"
motivation: 创建窄AI对于效率和安全性有重要价值，但神经网络基本学习特性带来挑战。
method: 通过合成任务实验，研究窄技能训练的数据分布要求和技能表示结构。
result: 发现某些窄技能无法通过仅训练窄分布数据习得，且技能表示存在非局域性。
conclusion: 窄AI的创建需考虑学习路径中的层次性和表示非局域性，对模型设计提出新要求。
---

## Abstract
We study the problem of creating strong, yet narrow, AI systems. While recent AI progress has been driven by the training of large general-purpose foundation models, the creation of smaller models specialized for narrow domains could be valuable for both efficiency and safety. In this work, we explore two challenges involved in creating such systems, having to do with basic properties of how neural networks learn and structure their representations. The first challenge regards when it is possible to train narrow models from scratch. Through experiments on a synthetic task, we find that it is sometimes necessary to train networks on a wide distribution of data to learn certain narrow skills within that distribution. This effect arises when skills depend on each other hierarchically, and training on a broad distribution introduces a curriculum which substantially accelerates learning. The second challenge regards how to transfer particular skills from large general models into small specialized models. We find that model skills are often not perfectly localized to a particular set of prunable components. However, we find that methods based on pruning can still outperform distillation. We investigate the use of a regularization objective to align desired skills with prunable components while unlearning unnecessary skills.

---

## 论文详细总结（自动生成）

# 论文总结：On the creation of narrow AI: hierarchy and nonlocality of neural network skills

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：当前最强的AI系统通常是通用型基础模型（如LLM），但通用性在效率和安全性上存在缺陷。例如，编程助手不需要具备医学知识，通用模型可能带来危险能力（如CBRN风险）、难以机械可解释性、难以验证。创建强而窄的AI系统（即仅在某领域表现优异的小模型）可在效率和安全性上获益。
- **核心问题**：探究创建窄AI时面临的两个基本挑战——（1）什么时候需要先在广泛数据上训练才能学会某些窄技能？（2）如何将大模型中的特定技能转移到小模型中，同时去除不需要的技能？这涉及神经网络学习中的层次性（hierarchy）和表示非局域性（nonlocality）。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：通过合成任务分析层次性对学习的影响；通过剪枝、正则化、蒸馏等方法研究技能转移。
- **关键技术细节**：
  - **合成任务CMSP**（Compositional Multitask Sparse Parity）：扩展了稀疏奇偶任务，输入包含控制位和任务位，多个控制位可同时为1，标签为所有激活控制位对应任务位的奇偶。原子样本（单控制位）和复合样本（多控制位）构成层次结构。
  - **剪枝方法**：按组（如神经元）计算消融分数（ablation score）：\( s_g = \mathbb{E}[\mathcal{L}(f(x;\theta),y) - \mathcal{L}(f(x;\theta^*_g),y)] \)。大规模模型使用一阶近似（attribution score）：\( \hat{s}_g = \sum_{i\in g} \frac{\partial \mathcal{L}}{\partial \theta_i} (-\theta_i) \)。
  - **正则化方法**：使用组套索（group lasso）惩罚：\( R(\theta) = \sum_{g\in G} \sqrt{\sum_{i\in g} \theta_i^2} \)，鼓励整组权重变为零，促进可剪枝性。
  - **蒸馏方法**：标准KL散度蒸馏（Hinton et al. 2015）。
  - **剪枝+恢复训练**：先剪枝，再在目标任务数据上少量训练恢复性能。

## 3. 实验设计

- **CMSP合成任务**：
  - 数据集：二进制字符串，n=64（或18等），k=4（或3），m=4或6。控制位编码子任务。训练网络为ReLU MLP（1-2隐藏层，宽度128-1024）。
  - Benchmark：比较不同训练分布下的学习曲线（含原子任务+复合任务 vs 仅复合任务）。
  - 方法对比：剪枝（基于消融分数）、组套索正则化+剪枝。

- **MNIST实验**：
  - 任务：仅识别偶数数字（窄任务）。
  - 模型：2隐藏层MLP（宽度1200）。
  - 对比方法：从头训练、蒸馏（教师为同一大模型）、组套索正则化剪枝、基于attribution的剪枝+恢复训练。
  - 指标：达到97%准确率所需的神经元数和数据量。

- **LLM实验**：
  - 任务：Python代码文档的下一个token预测（GitHub Code Dataset）。
  - 模型：Llama-3.2-1B作为初始大模型；另训练不同规模的小模型从头开始或蒸馏。
  - 对比方法：从头训练、蒸馏（教师为Llama-3.1-8B）、剪枝（神经元和残差流维度）+恢复训练、随机剪枝。
  - 评估：交叉熵损失及下游任务（counterfact、ARC-Easy、WMDP-Bio、WMDP-Cyber）的准确性，用于检测是否成功遗忘（unlearning）。
  - 剪枝配置：神经元稀疏度30%、63%、80%，残差流稀疏度50%、50%、90%等组合。

## 4. 资源与算力

- 论文在附录C中总结了算力估算：
  - CMSP训练：约13-160 GPU小时（多种节点）。
  - CMSP剪枝实验：约2-50 GPU小时。
  - MNIST实验：约18 GPU小时。
  - LLM实验：总时间<1600 A100 GPU小时，但全部尝试可能超过5000小时。
  - 使用GPU类型：A100-80GB节点，单GPU每任务。未明确具体数量和型号分布。

## 5. 实验数量与充分性

- 实验数量较多：
  - CMSP：40个随机种子重复，不同宽度（64-1024）和深度。
  - MNIST：54个配置点，每个平均10次运行。
  - LLM：9种规模从头训练、9种蒸馏、3种组套索λ（70k步）、多种剪枝稀疏度组合。
- 消融实验：比较随机剪枝 vs 基于attribution剪枝；比较有无正则化。
- 公平性：所有方法均在同一基准下比较（准确率阈值为97%或损失阈值1.7 nats），但作者承认超参数未最优缩放，比较可能存在偏差。
- 充分性：对合成任务进行了详细随机种子重复，对MNIST和LLM也有多次运行，统计上合理。然而CMSP为玩具任务，结论外推需谨慎。

## 6. 论文的主要结论与发现

- **发现1（层次性-curriculum效应）**：在CMSP任务中，若仅训练复合任务，网络几乎无法学会；若混合训练原子任务，复合任务学习效率大幅提升。表明有些窄技能必须通过广泛数据分布引入的课程才能有效学习。
- **发现2（表示非局域性）**：未正则化的网络中，不同子任务的电路高度纠缠，按某一任务剪枝后另一任务仍可恢复，即技能不局域于可剪除单元。
- **发现3（正则化改善可剪枝性）**：组套索正则化可使网络权重稀疏化，将技能对齐到可剪枝组件，从而更有效剪枝和遗忘。
- **发现4（剪枝优于蒸馏）**：在MNIST和LLM实验中，剪枝+恢复训练在参数-数据前沿上Pareto优于蒸馏和从头训练。
- **发现5（随机剪枝同样有效）**：在LLM中，随机剪枝经过恢复训练后性能与基于attribution剪枝相近，表明技能表示高度分布，无明确“Python神经元”局域化。
- **发现6（遗忘效果）**：剪枝（包括随机）可有效遗忘非目标任务，但基于attribution的剪枝在低稀疏度下遗忘效果较差。

## 7. 优点

- **问题新颖**：系统研究窄AI创建中的学习层次性和表示非局域性，连接了课程学习、剪枝、遗忘等方向。
- **方法简单有效**：使用组套索正则化改善可剪枝性，方法简洁；剪枝+恢复训练实用性强。
- **多层级实验**：从合成任务到标准图像分类（MNIST）再到实际LLM，验证结论的泛化性。
- **开源代码**：提供代码仓库增强可复现性。

## 8. 不足与局限

- **合成任务的局限性**：CMSP为人为构造的强层次性任务，真实数据中类似效应是否存在尚不明确。
- **剪枝方法简单**：使用贪心剪枝和一阶attribution近似，更先进策略可能更好。
- **LLM实验超参数未优化**：从头训练和蒸馏可能因学习率、批次大小等未调优而表现不佳，影响比较公平性。
- **非局域性分析不深入**：仅显示相关性，未机械可解释地分析特征分布。
- **遗忘评估有限**：仅测试少数基准，且未检查知识彻底删除（如通过对抗性攻击）。
- **硬件资源报告不够细化**：仅有总时间估算，未提供每实验的具体GPU型号和数量。

（完）
