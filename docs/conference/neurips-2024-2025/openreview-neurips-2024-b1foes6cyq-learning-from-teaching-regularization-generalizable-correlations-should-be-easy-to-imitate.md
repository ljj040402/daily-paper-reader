---
title: "Learning from Teaching Regularization: Generalizable Correlations Should be Easy to Imitate"
title_zh: 从教学正则化中学习：可泛化相关性应易于模仿
authors: "Can Jin, Tong Che, Hongwu Peng, Yiyuan Li, Dimitris N. Metaxas, Marco Pavone"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=B1FOes6cyq"
tags: ["query:ai"]
score: 8.0
evidence: 受教学启发的深度神经网络正则化技术
tldr: 本文提出“从教学中学习”（LoT）正则化方法，假设可泛化的相关性易于模仿。通过辅助学生模型训练主模型，并反馈以增强可泛化相关性。在计算机视觉和自然语言处理等领域验证了其有效性，提升了泛化能力。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-b1foes6cyq/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1398, \"height\": 403, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-b1foes6cyq/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1437, \"height\": 295, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-b1foes6cyq/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 616, \"height\": 457, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-b1foes6cyq/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1361, \"height\": 371, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-b1foes6cyq/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1424, \"height\": 366, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-b1foes6cyq/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1381, \"height\": 234, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-b1foes6cyq/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 732, \"height\": 332, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-b1foes6cyq/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1451, \"height\": 615, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-b1foes6cyq/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1234, \"height\": 229, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-b1foes6cyq/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1380, \"height\": 344, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-b1foes6cyq/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1383, \"height\": 409, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-b1foes6cyq/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1164, \"height\": 301, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-b1foes6cyq/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 776, \"height\": 336, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-b1foes6cyq/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 632, \"height\": 385, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-b1foes6cyq/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1446, \"height\": 192, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-b1foes6cyq/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1448, \"height\": 264, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-b1foes6cyq/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1445, \"height\": 175, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-b1foes6cyq/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1158, \"height\": 219, \"label\": \"Table\"}]"
motivation: 神经网络泛化能力仍是挑战，需新正则化方法。
method: LoT利用学生模型辅助主模型捕捉易模仿且可泛化的相关性。
result: 在多个领域（包括NLP和CV）的实验中提升了模型泛化性能。
conclusion: LoT是一种有效的正则化技术，可增强深度学习模型的泛化能力。
---

## Abstract
Generalization remains a central challenge in machine learning. In this work, we propose *Learning from Teaching* (**LoT**), a novel regularization technique for deep neural networks to enhance generalization. Inspired by the human ability to capture concise and abstract patterns, we hypothesize that generalizable correlations are expected to be easier to imitate. LoT operationalizes this concept to improve the generalization of the main model with auxiliary student learners. The student learners are trained by the main model and, in turn, provide feedback to help the main model capture more generalizable and imitable correlations. Our experimental results across several domains, including Computer Vision, Natural Language Processing, and methodologies like Reinforcement Learning, demonstrate that the introduction of LoT brings significant benefits compared to training models on the original dataset. The results suggest the effectiveness and efficiency of LoT in identifying generalizable information at the right scales while discarding spurious data correlations, thus making LoT a valuable addition to current machine learning. Code is available at https://github.com/jincan333/LoT.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：深度学习模型的泛化能力仍然是重大挑战。模型可能学习到数据中的虚假相关性（spurious correlations）而非真正的泛化相关性（generalizable correlations），导致过拟合。
- **研究动机**：受认知科学启发，人类倾向于捕捉简洁、抽象的模式，从而形成易于理解和传播的简单相关性。作者假设：**可泛化的相关性应更易于被其他学习器模仿**（imitable）。基于此，设计一种正则化方法，通过衡量主模型（教师）被学生模型模仿的难易程度，来引导教师学习更易模仿、更泛化的表示。
- **整体含义**：提出一种名为 **Learning from Teaching (LoT)** 的正则化技术，将“可模仿性”作为优化目标，联合训练教师和学生模型，通过学生反馈提升教师泛化能力。

### 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程
- **核心思想**：将教师模型（主模型）与一个或多个学生模型联合训练。学生模型学习模仿教师的预测分布，教师则通过学生反馈的“可模仿性”度量（如KL散度）进行正则化，从而迫使教师学习更简单、更通用的相关关系。
- **关键技术细节**：
  - 训练教师模型：损失函数为常规任务损失 + LoT正则项 \( R(\theta) = \frac{\alpha}{|\mathcal{D}_s|} \sum_{x \in \mathcal{D}_s} \sum_{i=1}^K \lambda_i \mu_{t,s_i}(x) \)，其中 \(\mu\) 为KL散度，\(\alpha\) 为正则系数。
  - 训练学生模型：学生仅通过模仿教师（最小化KL散度）学习，无需标签，可用无标签数据集 \(\mathcal{D}_s\)。
  - 教师和学生交替更新：每步先更新教师，再多次更新学生（由超参数 \(N\) 控制）。
- **算法流程（文字描述）**：
  1. 初始化教师网络 \(T_\theta\) 和学生网络 \(S_\phi\)。
  2. 循环：
     - 从标注数据 \(\mathcal{D}_t\) 采样 batch，从无标注数据 \(\mathcal{D}_s\) 采样 batch。
     - 计算教师损失：任务损失 + LoT正则项（基于学生当前输出）。
     - 更新教师参数。
     - 重复 \(N\) 次：从 \(\mathcal{D}_s\) 采样，计算学生模仿损失（教师固定），更新学生参数。
  3. 直到收敛。
- **关键区别**：不同于知识蒸馏（预先训练好教师然后蒸馏到学生），LoT 是同步训练教师和学生，且教师利用学生反馈进行正则化。

### 3. 实验设计：使用了哪些数据集/场景，基准方法，对比了哪些方法
- **实验场景**：
  - **强化学习（RL）**：4个Atari游戏（BeamRider, Breakout, UpNDown, Gravitar），使用PPO算法。对比 Teacher-only（无LoT）。
  - **无监督语言预训练**：PTB和WikiText-103数据集，使用LSTM、AWD-LSTM、Transformer-XL架构。对比 Teacher-only，总训练步数相同。
  - **有监督微调（LLM）**：GSM8K和MATH数学推理数据集，使用LLaMA-1 7B和LLaMA-2 7B。对比 In-Context Learning (ICL) 和标准 SFT。
  - **图像分类**：CIFAR-100和ImageNet-1K，使用ResNet、MobileNetV2、ViT、Swin等不同大小和架构的教师-学生组合。对比 Teacher-only（设置相同总训练步数）。
- **基准方法**：主要对比 Teacher-only（即不使用LoT正则项）。另外在消融实验中对比了 Born-Again Networks (BAN) 及更细的蒸馏方法（DKD, ReviewKD）。
- **消融实验**：研究正则化系数 \(\alpha\)、学生步数比例 \(N\)、不同度量（KL vs L2）、学生模型大小等的影响。

### 4. 资源与算力（若文中有说明）
- **论文附录 Table 12 详细列出了计算资源**：
  - **Atari（BeamRider）**：1块 NVIDIA A6000 48GB GPU，CPU 16核，训练时间约10小时（LoT与baseline相当）。
  - **PTB (LSTM)**：1块 A100 40GB GPU，CPU 1核，LoT 0.3小时 vs Teacher-only 0.6小时（LoT更快）。
  - **WikiText-103 (Transformer-XL-L)**：4块 A100 40GB GPU，CPU 4核，LoT 67.7小时 vs 85.6小时。
  - **GSM8K (LLaMA-2 7B)**：8块 A100 40GB GPU，CPU 8核，LoT 6.7小时 vs 8.1小时。
  - **CIFAR-100 (ResNet-50)**：1块 A100 40GB GPU，CPU 1核，LoT 0.5小时 vs 0.7小时。
  - **ImageNet-1K (ViT-L/16)**：4块 A100 40GB GPU，CPU 4核，LoT 18.7小时 vs 28.9小时。
- **结论**：LoT 在相同总训练步数下训练时间通常少于 Teacher-only（由于收敛更快），GPU内存占用增加12%~55%。

### 5. 实验数量与充分性
- **实验数量**：覆盖4个领域的多种任务：RL（4个游戏）、语言预训练（2个数据集×3种架构）、LLM微调（2个模型×2个数据集）、图像分类（2个数据集×多种CNN/Transformer组合）。总计超过20种不同设置。
- **消融实验**：包括 \(\alpha\) 和 \(N\) 的调参、度量选择（KL vs L2）、与多种蒸馏方法比较（BAN、DKD、ReviewKD）、不同学生模型大小的效果、以及额外OOD评估（ImageNet-R/Sketch）。
- **充分性评估**：实验设计较为全面，考虑了不同规模模型（小到MobileNetV2，大到LLaMA 7B）、不同架构（CNN、LSTM、Transformer）、不同学习范式（监督、无监督、RL）。结果均重复多次并报告标准差，统计可靠性较高。对比方法（Teacher-only、ICL、SFT、BAN等）设置公平（总步数相同）。因此实验充分且客观。

### 6. 论文的主要结论与发现
- **核心发现**：实验证实假设——可泛化的相关性更易模仿（学生能从学到泛化知识的教师那里获得更低KL损失且更快收敛）。
- **LoT 显著提升泛化性能**：
  - RL：平均回报提升44%（在4个Atari游戏中）。
  - 语言模型：PTB上LSTM PPL从82.75降至71.72；WikiText-103上Transformer-XL-L PPL从18.50降至16.47。
  - LLM微调：LLaMA-2 7B在GSM8K上准确率从39.81%升至41.87%；MATH从5.79%升至6.28%。
  - 图像分类：CIFAR-100上ResNet-18从81.14%升至83.13%（学生ResNet-50）；ImageNet-1K上ViT-B/16从83.97%升至84.80%（学生ViT-L/16）。
- **鲁棒性**：LoT在OOD评估（ImageNet-R, ImageNet-Sketch）上也优于Teacher-only。
- **效率与兼容性**：LoT在相同总计算量下训练更快，且可与现有正则化（weight decay, dropout）兼容。

### 7. 优点：方法或实验设计上的亮点
- **创新性**：将认知科学中的“易模仿性”概念引入深度学习正则化，提出了一种全新的师生协同训练范式，不同于传统知识蒸馏。
- **通用性**：适用于监督、无监督、强化学习，架构不限于CNN/LSTM/Transformer，小模型到大模型均可。
- **计算效率**：尽管增加了学生模型开销，但由于收敛更快，总训练时间反而减少（尤其在LLM和大视觉模型上）。
- **灵活性**：可自由选择学生模型大小和架构（不同大小或同架构），且学生可以更小以降低资源需求。
- **公平比较**：所有对比均保持总训练步数一致，且报告多次平均和标准差，结果可靠。
- **消融全面**：对关键超参数 \(\alpha\) 和 \(N\) 进行了系统分析，并对比了多种蒸馏变体，体现了方法的稳健性。

### 8. 不足与局限：包括实验覆盖、偏差风险、应用限制等
- **计算资源要求**：虽然总训练时间减少，但需要同时训练教师和学生，GPU内存占用增加12%~55%。对于资源受限场景可能仍需权衡。
- **超参数敏感性**：\(\alpha\) 和 \(N\) 需要调优，且最优值随任务变化（例如RL中 \(\alpha=0.1\) 或0.5）。文中未提供自动搜索方法。
- **实验覆盖的局限性**：
  - 仅测试了Atari 4个游戏，未涉及更复杂的RL环境（如DM Control或MuJoCo）。
  - LLM微调仅使用了数学推理任务（GSM8K/MATH），未涵盖其他通用知识或对话任务。
  - 图像分类仅使用了CIFAR-100和ImageNet，未测试细粒度分类或小样本学习。
- **理论分析不足**：论文未提供严格的数学证明为什么“易模仿性”等价于泛化，仅通过实验验证假设。
- **偏差风险**：在RL中，学生从教师收集的replay buffer中学习，可能引入数据分布偏移；文中未深入分析。
- **学生模型的选择**：虽然不同架构组合有效，但文中未系统研究如何选择最优学生（例如是否需同质初始化、是否需要不同随机种子等）。
- **社会影响**：文中提到LoT可能放大已有偏见或有害内容，但未提供具体缓解措施。

（完）
