---
title: "Gompertz Linear Units: Leveraging Asymmetry for Enhanced Learning Dynamics"
title_zh: Gompertz线性单元：利用不对称性增强学习动态
authors: "Indrashis Das, Mahmoud Safari, Steven Adriaensen, Frank Hutter"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=d8yAQOSLwv"
tags: ["query:ai-basics"]
score: 4.0
evidence: 深度学习基础组件：激活函数
tldr: 论文针对深度学习中激活函数的重要性，提出了一种新型自门控激活函数Gompertz线性单元（GoLU）。GoLU利用右偏不对称性，相比ReLU及其变体，在多个图像分类任务上表现出更优的训练动态和性能。该工作为深度学习基础组件的改进提供了新思路。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-d8yaqoslwv/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1466, \"height\": 506, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-d8yaqoslwv/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1494, \"height\": 555, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-d8yaqoslwv/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 938, \"height\": 396, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-d8yaqoslwv/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1447, \"height\": 379, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-d8yaqoslwv/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1408, \"height\": 321, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-d8yaqoslwv/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1448, \"height\": 382, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-d8yaqoslwv/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 875, \"height\": 105, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-d8yaqoslwv/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 139, \"height\": 100, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-d8yaqoslwv/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1306, \"height\": 680, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-d8yaqoslwv/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1307, \"height\": 333, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-d8yaqoslwv/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 858, \"height\": 501, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-d8yaqoslwv/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 697, \"height\": 434, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-d8yaqoslwv/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 707, \"height\": 444, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-d8yaqoslwv/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 713, \"height\": 431, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-d8yaqoslwv/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 723, \"height\": 450, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-d8yaqoslwv/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 709, \"height\": 446, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-d8yaqoslwv/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 906, \"height\": 543, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-d8yaqoslwv/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 713, \"height\": 446, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-d8yaqoslwv/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1426, \"height\": 536, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-d8yaqoslwv/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1426, \"height\": 536, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-d8yaqoslwv/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1428, \"height\": 533, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-d8yaqoslwv/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1428, \"height\": 538, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-d8yaqoslwv/fig-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 1425, \"height\": 536, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-d8yaqoslwv/fig-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 1427, \"height\": 532, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-d8yaqoslwv/fig-025.webp\", \"caption\": \"\", \"page\": 0, \"index\": 25, \"width\": 1435, \"height\": 536, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-d8yaqoslwv/fig-026.webp\", \"caption\": \"\", \"page\": 0, \"index\": 26, \"width\": 1434, \"height\": 536, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-d8yaqoslwv/fig-027.webp\", \"caption\": \"\", \"page\": 0, \"index\": 27, \"width\": 1429, \"height\": 536, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-d8yaqoslwv/fig-028.webp\", \"caption\": \"\", \"page\": 0, \"index\": 28, \"width\": 855, \"height\": 546, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-d8yaqoslwv/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 675, \"height\": 359, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-d8yaqoslwv/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 963, \"height\": 299, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-d8yaqoslwv/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1460, \"height\": 426, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-d8yaqoslwv/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 944, \"height\": 301, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-d8yaqoslwv/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 796, \"height\": 298, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-d8yaqoslwv/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 528, \"height\": 296, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-d8yaqoslwv/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 795, \"height\": 299, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-d8yaqoslwv/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 542, \"height\": 297, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-d8yaqoslwv/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1247, \"height\": 831, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-d8yaqoslwv/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 437, \"height\": 371, \"label\": \"Table\"}]"
motivation: 现有激活函数如ReLU存在神经元死亡问题，自门控激活函数虽好但仍有改进空间。
method: 提出GoLU激活函数，定义为x乘以Gompertz函数，利用函数的右偏不对称特性。
result: 在多个基准数据集上，GoLU相比GELU、Swish等实现了更快的收敛和更高的准确率。
conclusion: GoLU是一种有效的激活函数，能够改善深度神经网络的训练效率和性能。
---

## Abstract
Activation functions are fundamental elements of deep learning architectures as they significantly influence training dynamics. ReLU, while widely used, is prone to the dying neuron problem, which has been mitigated by variants such as LeakyReLU, PReLU, and ELU that better handle negative neuron outputs. Recently, self-gated activations like GELU and Swish have emerged as state-of-the-art alternatives, leveraging their smoothness to ensure stable gradient flow and prevent neuron inactivity. In this work, we introduce the Gompertz Linear Unit (GoLU), a novel self-gated activation function defined as $\mathrm{GoLU}(x) = x \\, \mathrm{Gompertz}(x)$, where $\mathrm{Gompertz}(x) = e^{-e^{-x}}$. The GoLU activation leverages the right-skewed asymmetry in the Gompertz function to reduce variance in the latent space more effectively compared to GELU and Swish, while preserving robust gradient flow. Extensive experiments across diverse tasks, including Image Classification, Language Modeling, Semantic Segmentation, Object Detection, Instance Segmentation, and Diffusion, highlight GoLU's superior performance relative to state-of-the-art activation functions, establishing GoLU as a robust alternative to existing activation functions.

---

## 论文详细总结（自动生成）

# 论文《Gompertz Linear Units: Leveraging Asymmetry for Enhanced Learning Dynamics》中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **背景**：激活函数是深度学习架构的基础组件，直接影响训练动态。早期 Sigmoid、Tanh 存在梯度消失问题；ReLU 缓解了梯度消失但引入了“神经元死亡”问题。后续 LeakyReLU、PReLU、ELU 等改进 ReLU 负半轴处理。近年来，自门控激活函数（如 GELU、Swish、Mish）因其平滑性和稳定梯度流动成为 SOTA，但仍有改进空间。
- **核心问题**：现有自门控激活函数（基于对称或左偏分布）在方差控制、权重分布多样性、损失景观平滑性方面尚未达到最优。
- **整体含义**：本文提出一种全新的自门控激活函数 **GoLU**（Gompertz Linear Unit），利用 Gumbel 分布 CDF（即 Gompertz 函数）的**右偏不对称性**，在降低隐空间方差的同时保持梯度流动，从而提升模型性能。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：用 Gompertz 函数作为门控机制，其右偏不对称性使得门控值在整个输入范围内均小于对称门控（如 Sigmoid 和 Gaussian CDF），从而压缩激活输出幅度、降低方差。
- **定义**：
  - $\mathrm{GoLU}(x) = x \cdot \mathrm{Gompertz}(x)$
  - $\mathrm{Gompertz}(x) = e^{-e^{-x}}$，即标准 Gumbel 分布 (0,1) 的 CDF。
- **关键性质**：
  - 平滑、非单调、无限可微（与 Swish、GELU 类似）。
  - 在原点处斜率较小（$\mathrm{GoLU}'(0) = e^{-1} \approx 0.37$），低于 Sigmoid 和 Gaussian CDF 的 0.5，导致输出方差降低。
  - 负半轴衰减为双指数（超快），正半轴与 Sigmoid 指数级收敛。
- **对训练动态的影响**：
  - **方差降低**：通过泰勒展开近似，$\mathrm{Var}[f(x)] \approx f'(\mu)^2 \sigma^2$，小斜率带来低方差。实验证实 GoLU 输出分布更尖峰（图 3、表 1）。
  - **平滑损失景观**：低方差使梯度更一致，损失函数对参数扰动更不敏感（图 5 展示更平滑的 2D 损失景观）。
  - **权重分布更分散**：GoLU 训练的模型权重在峰值附近更宽泛，表明网络捕捉更多样化特征（图 6）。
- **实现**：开发了自定义 CUDA 核函数，使得训练/推理速度与其他激活函数相当（表 9）。

## 3. 实验设计：数据集、场景、Benchmark、对比方法

- **任务范围**：涵盖图像分类、语言建模、语义分割、目标检测、实例分割、去噪扩散模型、机器翻译、学习曲线外推（共 8 类任务）。
- **数据集**：
  - 图像分类：ImageNet-1k、CIFAR-10
  - 语言建模：TinyStories、OpenWebText（GPT2-S）、WMT14 En-De（机器翻译）
  - 语义分割：MS-COCO（PASCAL-VOC 标签）
  - 目标检测/实例分割：MS-COCO
  - 扩散模型：CelebA
  - 其他：学习曲线外推使用合成数据
- **对比方法**：ReLU、LeakyReLU、ELU、GELU、Swish、Mish（共 6 个基线）。
- **架构**：ResNet 系列（18/34/50/20/32/44/56/110）、WideResNet-50-2、DenseNet-121/40、EfficientNet-B0、TinyViT、ViT-B/32、ViT-B/16（Vision）；GPT2（babyGPT 和 GPT2-S）（语言）；DeepLabV3、Faster R-CNN、RetinaNet、Mask R-CNN（检测/分割）；DDPM（扩散）；Transformer-Big（机器翻译）；LC-PFN（学习曲线）。
- **Benchmark**：所有实验遵循各架构的标准训练设置（优化器、学习率、正则化等），仅替换激活函数为唯一变量，进行 3 次随机种子运行取平均值和标准误差。

## 4. 资源与算力

- **明确说明**：所有实验在 NVIDIA A100 GPU 上运行，总计算量约 **112K GPU 小时**；TinyViT 在 NVIDIA H100 GPU 上额外消耗 **455 GPU 小时**；机器翻译使用单张 NVIDIA L40S GPU，约 1750 GPU 小时。总计约 114K+ GPU 小时。
- 文中未详细列出每项任务的具体 GPU 数量，但提供了总体估算。

## 5. 实验数量与充分性

- **实验数量**：共包含 8 大类任务，每类任务下多个架构/数据集组合。图像分类（ImageNet 上 9 种架构，CIFAR-10 上 8 种架构）、语言建模（2 个模型 × 2 数据集）、语义分割、目标检测、实例分割、扩散模型、机器翻译（1 个模型）、学习曲线（1 个模型）。总计超过 **20 个不同的模型-数据集组合**，每个组合 3 个随机种子。
- **消融实验**：对语义分割、实例分割、扩散模型、图像分类的**学习率**进行了消融（附录 D），发现默认学习率并非最优，而在微调后的最优学习率下 GoLU 均超越基线。此外，还构造了 **Flipped Mish**（附录 B）验证右偏不对称性的作用。
- **充分性与公平性**：实验覆盖了计算机视觉、自然语言处理、生成模型等多个领域，采用开源代码、标准训练脚本，控制变量（仅替换激活函数）。结果以均值±标准误差报告，并进行了**临界差异分析**（附录 E）统计算法排名。总体公平、充分。

## 6. 论文的主要结论与发现

1. **GoLU 在大多数任务上优于所有基线激活函数**，尤其在图像分类（ImageNet 上 ResNet-50 提升至 76.63%，ViT-B/16 提升至 80.72%）、语言建模（GPT2-S 困惑度降至 17.30）、语义分割（最优学习率下 mIoU 65.98）、目标检测（Box mAP 最高）和扩散模型（最优学习率下 loss 最低）中表现突出。
2. **方差降低、权重分布更广、损失景观更平滑**是 GoLU 的三个关键特性，且三者协同提升泛化。
3. **右偏不对称性**是 GoLU 性能提升的重要因素（通过 Flipped Mish 实验间接验证）。
4. **学习率调优**对充分释放 GoLU 优势至关重要：在默认学习率下 GoLU 可能略逊，但在最优学习率下全面领先。

## 7. 优点

- **创新性**：首次将 Gompertz 函数（Gumbel CDF）作为激活函数门控，引入右偏不对称性这一新颖视角。
- **理论支持**：通过泰勒展开定量解释方差降低；提供显式的斜率与方差关系。
- **全面实验**：覆盖 8 大任务、20+ 架构、多个数据集，结果统计严谨（3 种子 + 标准误差 + 临界差异分析）。
- **学习率敏感性分析**：不仅报告默认设置，还进行学习率消融，揭示最优工况，体现科学严谨性。
- **计算效率**：自定义 CUDA 核使 GoLU 的训练/推理速度几乎不逊于现有激活函数（平均相对速度 1.01×/1.00×）。
- **可解释性**：可视化损失景观、激活分布、权重分布，直观展示 GoLU 的作用机制。
- **开放代码**：提供完整可复现的 GitHub 仓库（https://github.com/automl/GoLU）。

## 8. 不足与局限

- **局限性承认**：论文明确在附录 K 指出，所宣称的效果（方差降低、权重分布等）并非保证在任何场景下成立，而是基于实证观察的普遍趋势；高性能不能唯一归因于不对称性，而是多种性质的相互作用。
- **学习率依赖性**：默认学习率下 GoLU 可能不是最优（如语义分割、实例分割），需要调参才能充分体现优势，增加了用户的使用门槛。
- **部分任务表现不突出**：在 EfficientNet-B0（图像分类）、DDPM 默认学习率下、学习曲线外推（LC-PFN，排名第6）中，GoLU 优势微弱或甚至低于部分基线。在 LC-PFN 中，不同激活函数差异很小，GoLU 并非最佳。
- **缺乏大规模 Transformer 验证**：虽然测试了 ViT-B 和 GPT2-S（124M），但未在更大的模型（如 GPT3 规模、LLaMA 等）上进行实验，规模外推能力未知。
- **对称性问题**：论文强调不对称性的重要性，但未系统研究不对称程度与性能之间的定量关系（如通过改变分布偏度进行消融）。
- **计算资源报告**：仅提供了总 GPU 小时数，未细化每项任务配置（如使用的 GPU 数量、每个运行的具体时长），可复现性略有欠缺。

（完）
