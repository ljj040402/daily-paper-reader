---
title: Why Do We Need Weight Decay in Modern Deep Learning?
title_zh: 为什么现代深度学习需要权重衰减？
authors: "Francesco D'Angelo, Maksym Andriushchenko, Aditya Varre, Nicolas Flammarion"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=YrAxxscKM2"
tags: ["query:ai-basics"]
score: 6.0
evidence: 分析权重衰减在深度学习训练中的作用
tldr: 本文研究了权重衰减在现代深度学习中的关键作用，发现对于视觉任务，权重衰减通过损失稳定机制增强SGD的隐式正则化；对于大语言模型，它平衡了训练动态。该工作揭示了权重衰减并非简单的正则化，而是优化策略的一部分，为理解和调整训练过程提供了新视角。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-yraxxsckm2/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 426, \"height\": 427, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yraxxsckm2/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1411, \"height\": 391, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yraxxsckm2/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1048, \"height\": 527, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yraxxsckm2/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1408, \"height\": 387, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yraxxsckm2/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1415, \"height\": 394, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yraxxsckm2/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 513, \"height\": 386, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yraxxsckm2/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1319, \"height\": 331, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yraxxsckm2/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 516, \"height\": 387, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yraxxsckm2/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 602, \"height\": 560, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yraxxsckm2/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1419, \"height\": 405, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yraxxsckm2/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1412, \"height\": 416, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yraxxsckm2/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1418, \"height\": 414, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yraxxsckm2/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 588, \"height\": 588, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yraxxsckm2/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1419, \"height\": 396, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yraxxsckm2/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1412, \"height\": 995, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yraxxsckm2/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1311, \"height\": 1519, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yraxxsckm2/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1309, \"height\": 1519, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yraxxsckm2/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1308, \"height\": 1520, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yraxxsckm2/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1187, \"height\": 555, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yraxxsckm2/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 710, \"height\": 530, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yraxxsckm2/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 711, \"height\": 530, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yraxxsckm2/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 711, \"height\": 542, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yraxxsckm2/fig-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 1472, \"height\": 404, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yraxxsckm2/fig-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 575, \"height\": 423, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yraxxsckm2/fig-025.webp\", \"caption\": \"\", \"page\": 0, \"index\": 25, \"width\": 1305, \"height\": 476, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-yraxxsckm2/fig-026.webp\", \"caption\": \"\", \"page\": 0, \"index\": 26, \"width\": 1306, \"height\": 493, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-yraxxsckm2/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1433, \"height\": 285, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-yraxxsckm2/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1423, \"height\": 359, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-yraxxsckm2/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1418, \"height\": 387, \"label\": \"Table\"}]"
motivation: 经典理论认为权重衰减是正则化，但现代深度学习中其作用尚不明确，需要理清。
method: 通过理论分析和实验，分别探究多遍SGD下的视觉任务和近一遍训练的LLM中权重衰减的影响。
result: 权重衰减在视觉任务中通过损失稳定机制增强隐式正则化，在LLM中平衡训练动态。
conclusion: 权重衰减在现代深度学习中的作用已不是传统正则化，而是优化动态的重要调节器。
---

## Abstract
Weight decay is a broadly used technique for training state-of-the-art deep networks from image classification to large language models. Despite its widespread usage and being extensively studied in the classical literature, its role remains poorly understood for deep learning. In this work, we highlight that the role of weight decay in modern deep learning is different from its regularization effect studied in classical learning theory. For deep networks on vision tasks trained with multipass SGD, we show how weight decay modifies the optimization dynamics enhancing the ever-present implicit regularization of SGD via the *loss stabilization mechanism*. In contrast, for large language models trained with nearly one-epoch training, we describe how weight decay balances the *bias-variance tradeoff* in stochastic optimization leading to lower training loss and improved training stability. 
Overall, we present a unifying perspective from ResNets on vision tasks to LLMs: weight decay is never useful as an explicit regularizer but instead changes the training dynamics in a desirable way.

---

## 论文详细总结（自动生成）

好的，以下是基于您提供的论文内容生成的结构化中文总结。

### 1. 论文的核心问题与整体含义（研究动机和背景）

*   **研究动机**：权重衰减（Weight Decay）是现代深度学习（从图像分类到大型语言模型）中广泛使用的技术。尽管其在经典学习理论中被视为一种显式的正则化方法，但它在现代深度学习中的实际作用却鲜为人知，且存在争议。例如，在过参数化情况下，即使使用权重衰减，网络仍然可以完全记忆数据，这质疑了其作为容量约束的解释。
*   **核心问题**：论文旨在揭示权重衰减在现代深度学习训练中的真实机制，而非简单归因于传统的正则化效应。具体地，它试图解释在两个典型的训练范式（多轮训练的“过训练”范式和接近单轮训练的“欠训练”范式）中，权重衰减为何有效。
* **整体含义**：论文提出一个统一的视角：权重衰减在现代深度学习中几乎从未作为显式正则化器发挥作用，而是通过改变优化动态来产生积极效果。在过训练中，它增强隐式正则化；在欠训练中，它优化训练损失和提升稳定性。

### 2. 论文提出的方法论：核心思想与关键技术细节

论文的核心思想是将深度学习训练分为两个截然不同的阶段（过训练和欠训练），并分别解释了权重衰减在这两个阶段的不同作用机制。

#### 过训练阶段（Over-training regime，如CNN视觉任务）

*   **核心思想**：权重衰减通过一种**损失稳定机制**来维持SGD（随机梯度下降）的非零噪声，从而激活并增强SGD的隐式正则化效应。
*   **关键技术细节**：
    1.  **损失稳定**：对于指数尾部损失函数（如交叉熵），不使用权重衰减时，权重范数会无限增长，损失趋近于零。使用权重衰减会抑制权重的增长，导致训练损失稳定在一个非零的水平。
    2.  **维持SGD噪声**：由于损失稳定在非零水平，SGD梯度的协方差（噪声）不会消失。论文证明，SGD噪声的尺度（由 `ση,λ` 表示）与训练损失和超参数 `ηλ`（学习率×权重衰减系数）的乘积单调相关。
    3.  **隐式正则化**：论文提出一个猜想（Conjecture 1），即SGD的动力学过程逼近于最小化一个正则化损失函数 `Lλ(w) + ησ²₍η,λ₎||J(w)||²_F`，其中 `||J(w)||_F` 是网络雅可比矩阵的范数。
    4.  **核心机制**：权重衰减通过稳定损失，维持了SGD噪声的强度，而正是这个噪声驱动了隐式正则化，惩罚了雅可比矩阵的范数，从而提升了泛化能力。这与经典理论中权重衰减作为显式L2惩罚不同。
    5.  **有效学习率（ELR）的解释**：在欠训练部分，论文指出对于AdamW优化器，权重衰减会诱导出一个有效学习率 `η_eff ∝ η/||w||₂`。匹配这个有效学习率可以复现权重衰减带来的训练损失改进。

### 3. 实验设计：数据集、场景与对比方法

论文在两个主要的深度学习场景中设计了实验：

#### 过训练实验（Section 2）

*   **数据集/场景**：
    *   主要实验：ResNet18 on CIFAR-10 和 Tiny-ImageNet。
    *   额外实验（附录C）：VGG on CIFAR-10, ResNet-32 on CIFAR-10, ResNet-34 on CIFAR-100, 以及尺度不变的ResNet架构。
*   **基准（Benchmark）**：测试误差（Test Error）。
*   **对比方法**：
    *   对比有无权重衰减（WD=0 vs WD>0）。
    *   对比大小学习率（Large LR vs Small LR）。
    *   对比EMA（指数移动平均）和微调（Fine-tuning）的效果。
    *   对比不同的 `η`（学习率）和 `λ`（权重衰减系数）组合，绘制热力图。

#### 欠训练实验（Section 3）

*   **数据集/场景**：
    *   主要实验：GPT-2-124M 模型在 OpenWebText 数据集上训练。
*   **基准（Benchmark）**：训练损失（Training Loss）。
*   **对比方法**：
    *   对比有无权重衰减的AdamW。
    *   对比不同权重衰减系数（λ=0.0, 0.1, 0.3）。
    *   **关键对比**：对比原始的AdamW（有WD）与一个修改后的Adam（无WD，但使用匹配的有效学习率 `η_eff = η_t / ||w||₂`）。这用于验证“有效学习率”假说。
    *   对比bf16和float32精度训练。
    *   对比AdamW和SGD with momentum。
    *   对比解耦权重衰减（AdamW）和简单的L2正则化。

### 4. 资源与算力

论文在附录中提供了算力细节：

*   **过训练实验 (CIFAR-10/100)**：每个实验在 Nvidia A100 GPU 上大约需要 2 GPU 小时。
*   **过训练实验 (Tiny-ImageNet)**：每个实验在 Nvidia A100 GPU 上大约需要 5 GPU 小时。
*   **欠训练实验 (GPT-2-124M)**：每个训练运行（50,000次迭代）在单张 Nvidia A100 GPU 上大约需要 12 小时。
*   **总体说明**：论文强调由于计算资源有限（given our limited computational resources），未进行真正意义上的大规模实验（e.g., 像GPT-3那样）。

### 5. 实验数量与充分性

*   **实验数量**：论文进行了大量实验，包括：
    *   3个以上的不同视觉架构（ResNet18/34, VGG）和数据集。
    *   对超参数（η, λ）进行广泛的网格扫描，绘制了热力图。
    *   设计了过训练和欠训练两种完全不同的场景。
    *   在欠训练中进行了多个消融实验（不同精度、不同优化器、是否耦合、匹配ELR）。
    *   在附录中验证了关键近似（如“解耦近似”）。
*   **充分性、客观性和公平性**：
    *   **充分**：实验覆盖了论文的核心声明，并提供了足够的证据支持其猜想。
    *   **客观**：使用了标准的数据集（CIFAR, Tiny-ImageNet, OpenWebText）和模型（ResNet, GPT-2），对比了合理的基线（有无WD, 不同LR）。
    *   **公平**：最重要的公平性实验是在欠训练部分匹配有效学习率（ELR），这直接证明了其核心假设。实验设计严谨，控制了变量。论文也承认了其局限性（如未做大规模实验）。

### 6. 论文的主要结论与发现

1.  **权重衰减在现代深度学习中的角色已转变**：它不再是一个简单的显式正则化器，而是优化动态的关键调节器。
2.  **过训练时期（如ResNet）**：权重衰减通过与**大学习率**结合，稳定了损失函数，进而维持了SGD的噪声强度。这个噪声触发了对**雅可比矩阵范数**的隐式正则化，从而提升泛化能力。其有效性由**乘积 `ηλ`**（学习率×权重衰减系数）控制。
3.  **欠训练时期（如GPT-2）**：对于单轮训练的大语言模型，权重衰减没有正则化效果（泛化差距为零）。它的主要好处是：
    *   **优化训练损失**：通过诱导一个更高的**有效学习率（ELR）**，更好地平衡了随机优化中的偏差-方差权衡，从而在训练后期获得更低的损失。
    *   **提升训练稳定性**：在**bf16低精度训练**中，权重衰减可以防止损失发散，是稳定训练的关键。
4.  **统一视角**：无论是哪种训练范式，权重衰减都不是因为其显式的L2惩罚而有效，而是因为它以有益的方式改变了训练动态。

### 7. 优点

1.  **统一的理论视角**：该工作成功地将权重衰减在两种截然不同的训练范式（过训练和欠训练）中的作用用统一的思想（改变动态而非显式正则化）联系起来，提供了更深刻的理解。
2.  **揭示了新的机制**：
    *   在过训练中，提出了“损失稳定机制”，并将其与SGD噪声的维持和隐式正则化联系起来，这超越了仅适用于尺度不变网络的“有效学习率”理论。
    *   在欠训练中，清晰地解释了权重衰减如何通过有效学习率影响偏差-方差权衡，并首次强调了其在低精度训练中的稳定性作用。
3.  **关键实验验证**：在欠训练中通过**匹配有效学习率**来复现训练曲线，是一个非常优雅且有力的实验，直接证明了其核心假设。
4.  **实用见解**：为实践者提供了如何选择和调整权重衰减（结合学习率）以优化训练的指导。

### 8. 不足与局限

1.  **计算资源限制**：论文明确指出，由于计算资源有限，未能在真正大规模（如GPT-3级别）的模型上进行实验，其结论的普适性有待在大规模场景下进一步验证。
2.  **缺乏严格理论证明**：论文承认没有提出新的严格理论结果（we do not prove new theoretical results）。其核心贡献是对实验现象的清晰描述和解释性猜想（Conjecture 1 & 3），而非严谨的数学证明。隐式正则化的猜想依赖于高斯近似和解耦近似，这些假设的严格有效性在更复杂的情况下可能受到挑战。
3.  **实验覆盖的局限性**：
    *   过训练部分的猜想主要在小到中规模视觉任务（CIFAR, Tiny-ImageNet）上验证，未在ImageNet等大规模数据集上进行大规模验证。
    *   欠训练部分的解释主要基于GPT-2系列模型，其在其他架构（如Transformer-XL）上的表现未知。
    *   混合精度训练的稳定性问题仅在GPT-2上进行了展示，其普适性有待考察。
4.  **优化器依赖**：欠训练中对有效学习率的推导主要基于sign SGD，并用于解释AdamW，但论文也展示了SGD with momentum的类似现象，其统一的解释框架仍有待完善。
5.  **偏差/公平性分析缺失**：论文聚焦于训练动态和泛化性能，未讨论权重衰减（或由此导致的不同训练动态）对模型公平性、鲁棒性等社会影响方面的潜在偏差。

（完）
