---
title: Improving Generalization and Convergence by Enhancing Implicit Regularization
title_zh: 通过增强隐式正则化改进泛化与收敛
authors: "Mingze Wang, Jinbo Wang, Haotian He, Zilin Wang, Guanhua Huang, Feiyu Xiong, Zhiyu li, Weinan E, Lei Wu"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=cjM2bhLOiC"
tags: ["query:ai-basics"]
score: 5.0
evidence: 深度学习泛化改进
tldr: 提出隐式正则化增强（IRE）框架，通过解耦平坦和尖锐方向动态，加速寻找平坦解，提升深度学习的泛化和收敛。IRE可集成到通用优化器中，在图像分类任务上持续提升性能。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-cjm2bhloic/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1420, \"height\": 331, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-cjm2bhloic/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1426, \"height\": 359, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-cjm2bhloic/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 514, \"height\": 296, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-cjm2bhloic/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1494, \"height\": 291, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-cjm2bhloic/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 460, \"height\": 271, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-cjm2bhloic/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1134, \"height\": 423, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-cjm2bhloic/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1100, \"height\": 249, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-cjm2bhloic/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 647, \"height\": 213, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-cjm2bhloic/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 646, \"height\": 214, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-cjm2bhloic/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 801, \"height\": 180, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-cjm2bhloic/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 394, \"height\": 151, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-cjm2bhloic/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 619, \"height\": 198, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-cjm2bhloic/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 962, \"height\": 241, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-cjm2bhloic/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1098, \"height\": 252, \"label\": \"Table\"}]"
motivation: 深度学习训练中寻求平坦解可提升泛化，但现有方法效率低。
method: IRE解耦平坦和尖锐方向动态，增强平坦方向锐度降低。
result: 在CIFAR-10/100和ImageNet上提升ResNet和ViT性能。
conclusion: IRE是有效且实用的隐式正则化增强框架。
---

## Abstract
In this work, we propose an Implicit Regularization Enhancement (IRE) framework to accelerate the discovery of flat solutions in deep learning, thereby improving generalization and convergence. 
Specifically, IRE decouples the dynamics of flat and sharp directions, which boosts the sharpness reduction along flat directions while maintaining the training stability in sharp directions. We show that IRE can be practically incorporated with *generic base optimizers* without introducing significant computational overload. Experiments show that IRE consistently improves the generalization performance for image classification tasks across a variety of benchmark datasets (CIFAR-10/100, ImageNet) and models (ResNets and ViTs). 
Surprisingly, IRE also  achieves a $2\times$ *speed-up* compared to AdamW in the pre-training of Llama models (of sizes ranging from 60M to 229M) on datasets including Wikitext-103, Minipile, and Openwebtext. Moreover, we provide theoretical guarantees, showing that IRE can substantially accelerate the convergence towards flat minima in Sharpness-aware Minimization (SAM).

---

## 论文详细总结（自动生成）

好的，这是根据您提供的论文内容生成的中文总结。

# 论文《通过增强隐式正则化改进泛化与收敛》详细总结

## 1. 核心问题与研究动机

*   **问题背景**：深度学习中，优化器（如SGD）存在一种“隐式正则化”效应，倾向于找到并收敛到“平坦”的最小值，这些平坦解通常具有更好的泛化能力。
*   **核心挑战**：
    *   **过程缓慢**：这种隐式锐度降低过程非常缓慢，尤其是在训练的后期阶段。为了获得平坦解，实践中通常需要采用较大的学习率并延长训练时间，但大学习率受限于训练稳定性。
    *   **计算成本**：显式的锐度感知最小化（SAM）方法虽然能有效促进平坦性，但其每次迭代的计算成本是基础优化器的两倍。
*   **论文目标**：提出一种高效、通用的框架，既能加速隐式正则化过程以获得更好的泛化和收敛，又不会带来过高的计算负担。

## 2. 方法论：隐式正则化增强（IRE）

*   **核心思想**：受隐式锐度降低沿“平坦方向”动态缓慢的启发，IRE框架的核心思想是**解耦优化器在平坦方向和尖锐方向上的动态**。具体来说，IRE只增强沿平坦方向上的更新步长（即放大平坦方向上的梯度），同时保持沿尖锐方向上的动态不变，从而在加速锐度降低的同时，维持训练稳定性。

*   **关键技术细节与算法流程**：
    1.  **通用框架**：IRE可以集成到任意的“基础优化器”（如GD, SGD, Adam, SAM）中。对于基础优化器的标准更新 `θ_{t+1} = θ_t - η * g_t`，IRE的修改版本为：
        `θ_{t+1} = θ_t - η * (g_t + κ * P_t * g_t)`
        其中 `κ` 是增强强度，`P_t` 是将梯度投影到平坦方向的投影算子。
    2.  **投影算子的轻量化估计**：为避免计算昂贵的完整Hessian矩阵，IRE通过**对角的Fisher信息矩阵**来近似Hessian。具体地，它使用一种计算高效的估计器 `h_t = B * ∇L_B(θ) ⊙ ∇L_B(θ)`，其中 `B` 为batch大小。然后根据对角Hessian的绝对值大小来识别平坦方向，生成一个掩码向量 `n_t`。
    3.  **算法流程**：
        *   **输入**：基础优化器，学习率 `η`，IRE超参数 `κ`（增强强度），`γ`（用于选择平坦坐标的比例），`K`（更新掩码的频率）。
        *   **每K步**：
            1.  使用轻量级估计器计算对角Hessian `h_t`。
            2.  根据 `γ` 筛选出`|h_t|`最小的**top-`γ`**（通常>0.5）个坐标作为“平坦方向”。
            3.  更新掩码 `n_t`（对平坦方向置1，其余置0）。
        *   **每步更新**：最终的更新量为 `θ_{t+1} = θ_t - η * (g_t + κ * n_t ⊙ g_t)`。

## 3. 实验设计

*   **视觉任务（Image Classification）**：
    *   **数据集**：CIFAR-10, CIFAR-100, ImageNet。
    *   **模型**：ResNet-56, WideResNet (WRN-16-8, WRN-28-10), Vision Transformers (ViT-T, ViT-S)。
    *   **基准优化器 (Base Optimizer)**：SGD, AdamW, SAM。
    *   **对比方法**：将IRE与三个基准优化器结合（SGD-IRE, AdmIRE, SAM-IRE），并与原始基准优化器进行对比。

*   **语言模型预训练 (LLM Pre-training)**：
    *   **数据集**：Wikitext-2, Wikitext-103, Minipile, Openwebtext。
    *   **模型**：2层Transformer (8M), Llama (60M, 119M, 229M)。
    *   **基准优化器**：AdamW。
    *   **对比方法**：AdamW 与 AdmIRE (Adam+IRE)。

*   **验证实验 (Section 4.1.1)**：
    *   专门设计实验验证IRE能加速锐度降低。使用SAM-IRE训练WRN-16-8在CIFAR-10上，观察不同`κ`和`γ`下锐度的变化。

## 4. 资源与算力

*   **实验平台**：
    *   CIFAR-10/100实验：单块A800 GPU。
    *   ImageNet实验：4块A800 GPU。
    *   LLM预训练实验 (Wikitext-103, Minipile, Openwebtext)：4块H800 GPU。
*   **计算效率**：
    *   通过设置 `K=10`（每10步更新一次投影），IRE的平均额外计算开销仅为**约10%**。论文中报告了AdamW与AdmIRE在单个A800上的平均每步耗时分别为0.165s和0.185s，验证了其低开销。

## 5. 实验数量与充分性

*   **实验数量**：非常充分，涵盖了计算机视觉和自然语言处理两大领域，涉及从小型数据集（CIFAR）到大型数据集（ImageNet, Openwebtext），以及从小型模型（ResNet-56）到大型语言模型（Llama-229M）的多种场景。
*   **消融实验**：对IRE的核心超参数 `κ`（增强强度）和 `γ`（平坦比例）进行了消融研究，验证了其鲁棒性。
*   **公平性**：
    *   在所有对比中，IRE都是直接集成到当前最优的基础优化器（SGD, AdamW, SAM）中，并与其原始版本进行公平比较。
    *   在LLM预训练中，AdmIRE和AdamW使用了相同的最佳学习率，确保对比是基于相同的主干。
    *   论文报告了随机种子的结果（见表8），并使用了标准的训练配置（如数据增强、标签平滑等），确保了对比的客观性。

## 6. 主要结论与发现

1.  **持续改进视觉任务泛化**：IRE在CIFAR-10/100和ImageNet上，对于ResNets和ViTs，均能**一致提升**SGD、AdamW、SAM的测试准确率。
2.  **显著加速LLM预训练**：在预训练不同规模（60M-229M）的Llama模型时，**AdmIRE实现了约2.1倍的加速**，即用一半的训练步数即可达到与AdamW相同的验证损失。
3.  **加速锐度降低的理论保证**：论文提供了理论证明，表明IRE可以将标准SAM在最小化Hessian迹上的收敛速度提升 `Θ(1/ρ)` 倍（`ρ`为SAM的超参数）。
4.  **与SAM正交性**：IRE的机制与SAM近似正交，将其与SAM结合（SAM-IRE）可以进一步带来性能提升。
5.  **有效性归因**：在LLM预训练中，AdmIRE不仅训练更快，所找到的解也比AdamW在相同损失下更平坦（具有更小的Hessian迹）。

## 7. 优点

*   **设计精巧**：IRE的核心思路（加速平坦方向而不扰动尖锐方向）非常简洁、直观且有效，深刻洞察了隐式正则化的过程。
*   **通用性与兼容性强**：它是一个“即插即用”的框架，可以无缝集成到各种主流优化器中，无需修改优化器的核心逻辑。
*   **极致的计算效率**：通过使用轻量对角Hessian估计和延迟更新策略（`K=10`），IRE的计算开销非常低（约10%），远低于SAM的100%额外开销。
*   **理论与实验双验证**：论文不仅通过大量实验证明了IRE的有效性，还从理论上论证了其在SAM上的加速能力，深化了对其机理的理解。
*   **发现意外的加速效果**：除了提升泛化，IRE还能在LLM预训练中实现显著的加速，这表明其价值可能超越了最初的动机，这一发现本身很重要。

## 8. 不足与局限

*   **理论解释的局限性**：论文主要从理论上解释了IRE加速SAM锐度降低的原因，但对于IRE（特别是在优化路径上）为何能显著加速LLM预训练中的损失收敛，论文承认这需要未来的研究来进一步解释。
*   **大规模应用的验证**：虽然Llama 229M的预训练实验证明有效，但更大的模型（如7B、13B及以上）和更长的训练任务尚未被探索。论文将其列为未来工作。
*   **下游任务性能**：论文仅分析了预训练阶段的损失和锐度，并假设更平坦的解可能带来更好的下游任务性能，但并未对下游任务表现进行直接测评。这是一个重要的后续验证步骤。
*   **超参数敏感性**：虽然论文进行了消融实验，但`κ`和 `γ`的选取仍需要针对特定任务进行调整。论文中大多数任务通过网格搜索选择超参数，但在实际应用中，这可能是一个潜在的调优成本点。
*   **偏差风险**：IRE通过仅放大平坦方向的梯度，可能会引入一种新的偏差，即过度偏好参数空间中某些特定的平坦区域，这可能在某些情况下并非最优，尽管实验尚未发现负面影响。

（完）
