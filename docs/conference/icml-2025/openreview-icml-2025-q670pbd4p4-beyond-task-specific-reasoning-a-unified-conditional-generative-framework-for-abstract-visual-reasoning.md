---
title: "Beyond Task-Specific Reasoning: A Unified Conditional Generative Framework for Abstract Visual Reasoning"
title_zh: 超越任务特定推理：抽象视觉推理的统一条件生成框架
authors: "Fan Shi, Bin Li, Xiangyang Xue"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=q670PBd4p4"
tags: ["query:ai"]
score: 6.0
evidence: 抽象视觉推理
tldr: 该论文针对抽象视觉推理任务提出统一条件生成求解器（UCGS），解决了现有深度求解器需要为每个任务单独设计架构和参数的问题。UCGS通过条件生成机制，在多个AVR基准上达到或超越任务专属方法的表现。这一统一框架降低了求解新任务的计算成本，推动了类人抽象推理能力的发展。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-q670pbd4p4/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1675, \"height\": 496, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q670pbd4p4/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1743, \"height\": 951, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q670pbd4p4/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1769, \"height\": 987, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q670pbd4p4/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1520, \"height\": 1377, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q670pbd4p4/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1608, \"height\": 2149, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q670pbd4p4/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1584, \"height\": 2063, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q670pbd4p4/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1582, \"height\": 2073, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-q670pbd4p4/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1646, \"height\": 637, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-q670pbd4p4/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 806, \"height\": 371, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-q670pbd4p4/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 955, \"height\": 397, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-q670pbd4p4/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1326, \"height\": 395, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-q670pbd4p4/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1684, \"height\": 397, \"label\": \"Table\"}]"
motivation: 现有抽象视觉推理求解器为每个任务单独设计，缺乏通用性且重训练成本高。
method: 提出统一条件生成求解器，通过条件生成范式将多个任务映射到同一空间。
result: 在多个抽象视觉推理基准上，UCGS取得了与任务特定方法相当甚至更优的结果。
conclusion: 统一条件生成是一种有效的通用抽象推理方法，有望推动通用人工智能基础研究。
---

## Abstract
Abstract visual reasoning (AVR) enables humans to quickly discover and generalize abstract rules to new scenarios. Designing intelligent systems with human-like AVR abilities has been a long-standing topic in the artificial intelligence community. Deep AVR solvers have recently achieved remarkable success in various AVR tasks. However, they usually use task-specific designs or parameters in different tasks. In such a paradigm, solving new tasks often means retraining the model, and sometimes retuning the model architectures, which increases the cost of solving AVR problems. In contrast to task-specific approaches, this paper proposes a novel Unified Conditional Generative Solver (UCGS), aiming to address multiple AVR tasks in a unified framework. First, we prove that some well-known AVR tasks can be reformulated as the problem of estimating the predictability of target images in problem panels. Then, we illustrate that, under the proposed framework, training one conditional generative model can solve various AVR tasks. The experiments show that with a single round of multi-task training, UCGS demonstrates abstract reasoning ability across various AVR tasks. Especially, UCGS exhibits the ability of zero-shot reasoning, enabling it to perform abstract reasoning on problems from unseen AVR tasks in the testing phase.

---

## 论文详细总结（自动生成）

以下是根据论文内容生成的详细中文总结：

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：现有抽象视觉推理（AVR）求解器通常为每个任务单独设计模型架构和超参数，导致求解新任务时需要重新训练甚至调整网络结构，增加了应用成本。缺乏一个统一的、可泛化的推理框架。
- **研究动机**：人类能够快速发现并泛化抽象规则到新场景，而现有深度学习模型难以做到。论文希望设计一个统一的框架，使单一模型能够处理多种AVR任务，并具备零样本推理能力。
- **背景**：AVR任务（如Raven渐进矩阵RPM、视觉类比问题VAP、找出不同类O3、合成视觉推理任务SVRT）在问题结构、答案形式（生成式与选择式）上差异很大。已有工作尝试用条件生成模型解决单个任务，但尚未统一。

## 2. 论文提出的方法论

### 核心思想
将多个AVR任务重新形式化为对问题面板中目标图像“可预测性”的估计问题。通过训练一个单一的条件生成模型来估计这种可预测性，再根据任务类型通过简单的、无训练的判决函数得到最终答案。

### 关键技术细节
- **数学基础**：定义问题面板的联合概率p(Ip)和条件概率p(x|I<sub>¬i</sub>)。对于RPM，正确选项x<sup>*</sup> = argmax p(x|I<sub>¬N</sub>)；对于O3，异常图像索引 i<sup>*</sup> = argmin p(Ip<sub>i</sub>|I<sub>¬i</sub>)；对于SVRT，查询图像属于 p(x|I<sub>l</sub>) 更大的面板。
- **模型架构（UCGS-T）**：
  - **图像编码器与解码器**：使用CNN将图像映射到离散码本（VQVAE风格），得到量化后的patch表示。
  - **Patch编码器**：对每个图像的patch加入位置编码，通过Transformer解码器提取K个视觉概念（通过class tokens聚合）。
  - **概念编码器**：将上下文图像的概念分组（按概念维度），分别用共享的Transformer解码器处理，预测目标图像的概念。
  - **Patch解码器**：自回归地生成目标图像的patch序列，每一步基于已生成的patch和预测的目标概念，从码本中采样离散编码。
- **训练损失**：包含patch预测损失（负对数似然）和图像重建损失（VQVAE损失），总损失 L<sub>total</sub> = L<sub>pred</sub> + λL<sub>recon</sub>。图像编码解码器先预训练，再冻结，训练其余模块。

## 3. 实验设计

### 数据集
- **ID任务（训练集+测试集）**：RAVEN（7种配置，42K训练/14K验证/14K测试）和PGM（1.4M训练/5K验证/200K测试，使用neutral regime）。
- **ID-ZS任务（仅测试，零样本）**：基于RAVEN构建的O3-ID（5张图像）、VAP-ID（6张图像）、SVRT-ID（8张图像），共享训练集的视觉概念和抽象规则，但任务形式不同。
- **OOD-ZS任务（仅测试，零样本且包含未见概念/规则）**：G1-set（O3任务，1K样本）、VAP（200K样本）、SVRT（253样本）。

### Benchmark与评价指标
- 使用**选择准确率（selection accuracy）**，对生成式求解器，若生成结果与候选集中正确答案最接近则视为正确。
- 对比方法：
  - **消融基线**：三种骨干（patch-based、object-centric [OCL]、monolithic [Mono]）分别搭配两种条件生成求解器（ANP、Transformer [TF]），共6种。
  - **任务特定求解器**：PrAE、NVSA、GCA、ALANS、RAISE（训练时不使用规则/属性标注）。
  - **多模态大模型**：GPT-4o（使用任务特定提示）。

### 实验设置
- 所有UCGS-T和消融基线均在多任务设置下训练：使用RAVEN所有7种配置和PGM的neutral regime，测试时在ID-ZS和OOD-ZS任务上零样本评估。
- 任务特定求解器分别在各数据集上单独训练和测试。

## 4. 资源与算力

- **计算资源**：所有模型在单张24GB NVIDIA GeForce RTX 4090 GPU上训练，使用PyTorch实现。
- **训练时长**：文中未明确给出具体训练时长或迭代次数。仅提到图像编码解码器先预训练（learning rate 4×10<sup>-4</sup>, batch size 64），再冻结；剩余部分训练（learning rate 3×10<sup>-4</sup>, batch size 128）。监控验证集准确率，保存最佳检查点。

## 5. 实验数量与充分性

- **实验数量**：涵盖4大AVR任务类型，涉及3类评估设置（ID、ID-ZS、OOD-ZS），共8个数据集/子数据集。对比了3类方法（消融基线6种、任务特定求解器5种、GPT-4o）。
- **充分性评估**：
  - 充分：在多个难度级别（ID → ID-ZS → OOD-ZS）上评估了泛化能力，包括零样本和跨任务迁移。
  - 客观公平：与消融基线在同一多任务训练设置下比较；与任务特定求解器比较时确保不使用额外标注；与GPT-4o比较时使用相同子集。
  - 还提供了定性生成结果可视化（图3, 6, 7），直观展示生成质量。
  - 消融实验覆盖骨干（Patch/OCL/Mono）和条件生成器（ANP/TF）的组合，验证了各组件的有效性。
- **潜在不足**：未与最先进的selective solvers（如使用规则监督的模型）在同等条件下比较；未在真实场景AVR数据上测试。

## 6. 论文的主要结论与发现

- UCGS框架能够将多种AVR任务统一为条件生成问题，仅需一次多任务训练即可求解。
- 实例化模型UCGS-T在ID任务（RAVEN 64.6%, PGM 38.1%）上显著优于所有消融基线和多数任务特定求解器。
- 在ID-ZS任务上，UCGS-T表现最佳（O3-ID 33.6%, VAP-ID 35.8%, SVRT-ID 84.6%），证明其能够将已学推理能力迁移到新任务形式。
- 在OOD-ZS任务上（G1-set, VAP, SVRT）所有方法性能大幅下降，但UCGS-T仍略优于基线，说明具备一定的跨分布泛化能力。
- 与GPT-4o相比，UCGS-T在ID和ID-ZS任务上大幅领先，但在OOD-ZS任务上稍逊，可能归因于GPT-4o更强大的先验知识。
- 生成可视化显示UCGS-T能产生符合规则且清晰的目标图像，而基线常出现错误概念或伪影。

## 7. 优点

- **统一性**：首次提出一个框架同时处理生成式与选择式AVR任务，避免任务特定设计。
- **零样本推理**：支持在训练未见过的任务形式上进行推理，无需重新训练。
- **模块化设计**：图像编码/解码、patch编码、概念编码、patch解码可解释性强，便于分析和改进。
- **离散表示**：使用VQVAE将图像压缩为离散码本，有利于抽象概念的学习和泛化。
- **概念级推理**：通过概念分组独立处理每个视觉概念，能捕捉全局抽象规则。
- **实验全面**：包含消融实验、多任务泛化、与任务特定求解器及大型MLLM的比较，结果可信。

## 8. 不足与局限

- **性能差距**：UCGS-T的准确率仍低于最先进的选择式求解器（如使用规则监督的模型），提升空间大。
- **未涉及真实场景**：实验仅在合成AVR数据集上验证，真实世界场景中更复杂的视觉概念和抽象规则可能难以处理。
- **图像tokenizer限制**：当前VQVAE编码器解码器对复杂图像的重建精度可能不足，需要更强大的模型（如扩散模型）。
- **OOD泛化有限**：在OOD-ZS任务上准确率仅略高于随机猜测，说明面对全新视觉概念和规则时泛化能力较弱。
- **实验设置局限**：仅使用单GPU训练，未报告训练时间，可能影响可复现性；未公开代码和预训练模型（论文未说明，但作为ICML论文可能已开源）。
- **对比方法的选择**：未与近期基于大语言模型的视觉推理方法（如Visual Prompting）进行充分比较；与GPT-4o的对比中，提示设计可能未达到最优。

（完）
