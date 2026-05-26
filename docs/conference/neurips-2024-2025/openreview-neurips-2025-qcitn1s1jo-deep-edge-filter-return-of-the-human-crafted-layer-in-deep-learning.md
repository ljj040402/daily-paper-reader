---
title: "Deep Edge Filter: Return of the Human-Crafted Layer in Deep Learning"
title_zh: 深度边缘滤波器：深度学习中人造层的回归
authors: "Dongkwan Lee, Junhoo Lee, Nojun Kwak"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=QcItn1s1jO"
tags: ["query:ai-basics"]
score: 4.0
evidence: 提出深度边缘滤波器改进泛化，涉及深度学习基础技术
tldr: 论文提出深度边缘滤波器，通过高通滤波分离深度特征中语义与领域偏置，提升模型泛化能力。在图像、文本、3D、音频等多种模态上均获得一致性能提升。该方法即插即用，不改变架构。为深度学习泛化提供了一种有效且简洁的改进手段。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-qcitn1s1jo/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 284, \"height\": 464, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qcitn1s1jo/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1156, \"height\": 792, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qcitn1s1jo/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1297, \"height\": 412, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qcitn1s1jo/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1406, \"height\": 417, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qcitn1s1jo/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1407, \"height\": 416, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qcitn1s1jo/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1432, \"height\": 354, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qcitn1s1jo/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1430, \"height\": 352, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-qcitn1s1jo/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 603, \"height\": 184, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-qcitn1s1jo/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1452, \"height\": 293, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-qcitn1s1jo/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1159, \"height\": 161, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-qcitn1s1jo/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1446, \"height\": 392, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-qcitn1s1jo/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 970, \"height\": 390, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-qcitn1s1jo/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 932, \"height\": 282, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-qcitn1s1jo/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1449, \"height\": 399, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-qcitn1s1jo/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1446, \"height\": 398, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-qcitn1s1jo/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1443, \"height\": 162, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-qcitn1s1jo/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 791, \"height\": 221, \"label\": \"Table\"}]"
motivation: 深度网络编码的语义信息与领域偏置分别存在不同频率成分中。
method: 对深度特征做高通滤波，减去低通成分，保留语义信息。
result: 在视觉、文本、3D、音频等多个领域均提升泛化性能。
conclusion: 高通滤波是一种轻量且有效的泛化增强技术。
---

## Abstract
We introduce the Deep Edge Filter, a novel approach that applies high-pass filtering to deep neural network features to improve model generalizability. Our method is motivated by our hypothesis that neural networks encode task-relevant semantic information in high-frequency components while storing domain-specific biases in low-frequency components of deep features. By subtracting low-pass filtered outputs from original features, our approach isolates generalizable representations while preserving architectural integrity. Experimental results across diverse domains such as Vision, Text, 3D, and Audio demonstrate consistent performance improvements regardless of model architecture and data modality. Analysis reveals that our method induces feature sparsification and effectively isolates high-frequency components, providing empirical validation of our core hypothesis. The code is available at \url{https://github.com/dongkwani/DeepEdgeFilter}.

---

## 论文详细总结（自动生成）

# 论文总结：Deep Edge Filter: Return of the Human-Crafted Layer in Deep Learning

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：现代深度神经网络虽然能力强大，但极易受到扰动和领域偏移的影响，例如对抗攻击、从白天到夜晚的环境变化等。传统基于边缘检测的预处理方法（在输入图像上应用高通滤波）虽然能提供鲁棒性，但会丢失细粒度细节，且局限于图像模态，难以扩展到文本、3D、音频等数据。
- **关键假设**：论文假设**深度特征中，任务相关的语义信息主要编码在高频分量，而领域特定的偏置（如光照、纹理、背景等）主要编码在低频分量**。因此，对深度特征施加高通滤波（即边缘滤波器）可以分离出更具泛化能力的表征。
- **整体含义**：提出一种轻量、即插即用的滤波器模块，可直接应用于网络中间层的特征，帮助模型在多个模态下提升对分布外数据的泛化性能，而无需改变模型架构或增加大量计算。

## 2. 论文提出的方法论

- **核心思想**：定义一个**深度边缘滤波器** \( F_{\text{edge}}(h) = h - \text{LPF}(h) \)，其中 \( h \) 是网络某层的特征，LPF 是低通滤波器（默认均值滤波器）。该操作相当于高通滤波，保留高频语义、抑制低频领域偏置。
- **关键技术细节**：
  - **滤波器类型**：默认使用均值滤波器；消融中也测试了中值和高斯滤波。
  - **维度适配**：对于CNN架构（如WRN、ResNet），使用2D滤波器，在空间维度 (H, W) 上逐通道滤波；对于Transformer/MLP架构（如ViT、BERT、NeRF的MLP），使用1D滤波器，在序列长度维度上滤波。
  - **梯度阻断**：LPF部分在训练中**梯度被截断**（detach），即滤波器本身不参与学习，只对特征进行固定预处理，模型仅基于高通部分进行训练。
  - **放置位置**：通常只在一个层（而非多个层）插入滤波器，避免信息丢失。默认放置位置例如WRN的block1之后、ViT的block11之后等。
- **无额外可学习参数**：滤波器本身不引入可学习参数，几乎不增加计算量。

## 3. 实验设计

- **模态与任务**：
  - **视觉**：测试时适应（Test-Time Adaptation, TTA）任务，在CIFAR-10C、CIFAR-100C、ImageNet200-C基准上评估，使用NORM和TENT算法。模型包括WRN-28-10、ResNet18、ViT-B/32。
  - **文本**：GLUE子任务（SST-2情感分析、QQP语义等价、QNLI推理），使用标准BERT架构（12层Transformer）。
  - **3D**：少样本NeRF任务（8视图输入），在Blender数据集（chair、drums、ficus、lego、mic、ship）上评估PSNR、SSIM、LPIPS、MAE。
  - **音频**：UrbanSound8K声音分类，CNN架构（三层卷积）。
- **对比方法**：
  - 各任务均对比**无滤波器（vanilla）模型**。
  - 消融实验对比不同滤波器类型（均值、中值、高斯）以及直接应用低通滤波（LPF）。
  - 额外实验将边缘滤波器替换为**同等计算量的可训练卷积层**，以排除计算量增加带来的性能提升。
- **扩展示例**：在ViT-L/14 OpenCLIP基础模型上进行跨领域小样本分类（PACS、DomainNet）。

## 4. 资源与算力

- 论文明确指出：**所有实验均在单张 A6000 GPU 上完成**。未提供具体训练时长，但提到视觉任务训练50 epoch（CIFAR）、5 epoch（ImageNet200）；语言任务40 epoch；3D任务500像素epoch；音频任务20 epoch。

## 5. 实验数量与充分性

- **实验数量**：覆盖4个模态、多个任务，包含大量子实验。例如CIFAR-10C/100C各有15种corruption类型详细结果，消融实验包括位置、核大小、滤波器类型、替换为Conv层、统计显著性（5次独立运行）等。在基础模型OpenCLIP上还做了跨领域验证。
- **充分性与公平性**：
  - 对比了多种架构（CNN、Transformer）、多种领域适应方法（NORM/TENT），并控制标准偏差（给出baseline均值和标准差）。
  - 消融研究系统探讨了滤波器位置和核大小的影响。
  - 专门设计了等计算量对比（替换为可训练卷积），证明性能提升并非由计算量增加导致。
  - 总体实验设计较为充分、客观，但作者承认受限于算力未能在更大规模模型（如LLM）上验证，且仅报告了基线标准差而未报告Edge Filter结果的标准差。

## 6. 论文的主要结论与发现

1. **边缘滤波器普遍有效**：在视觉、文本、3D、音频模态上均观察到性能提升（例如CIFAR-10C TTA提升最高8.5%p；SST-2提升1.49%p；NeRF平均PSNR +0.44、LPIPS降低14%；UrbanSound8K提升4.3%点）。
2. **验证频率假设**：直接应用低通滤波会显著降低性能（表5），而高通（边缘）滤波提升性能，支持“低频含领域偏置、高频含语义”的假设。
3. **特征稀疏化**：滤波后特征激活密度显著下降（图3a/b），符合稀疏编码视角。
4. **频率分析支持**：特征的FFT幅度在低频区显著降低（图3c），验证了高通滤波的正确执行。
5. **即插即用、架构无关**：CNN和Transformer均能受益，且仅需在单层插入，几乎不增加参数。

## 7. 优点

- **简洁有效**：方法简单（特征减去其低通版本），无需修改网络结构或训练方式，易于复现和集成。
- **模态通用**：从图像到文本、3D、音频，验证了跨领域有效性，扩展性强。
- **轻量高效**：不引入可学习参数，计算开销极小（单次卷积滤波），适合实际部署。
- **理论支撑**：从稀疏编码和领域自适应文献提供了理论动机，并通过FFT和激活密度分析提供实证。
- **实验系统**：包含多种架构、任务、消融、统计显著性及扩展实验，结论可靠。

## 8. 不足与局限

- **需重新训练**：滤波器在训练时需嵌入模型并从头训练，无法直接应用于已有预训练模型（但后续OpenCLIP实验暗示在预训练模型上微调也可能有效）。
- **对某些场景反效果**：如在NeRF的ficus场景性能下降（因为其本身纹理丰富，进一步高通可能丢失信息）；高斯滤波器用于ViT时性能下降（未优化参数）。
- **统计报告不完整**：仅报告了基线性能的均值和标准差（5次运行），未给出边缘滤波器结果的标准差，难以直接判断改善是否显著超过噪声。
- **大模型验证不足**：受限于计算资源，未在LLM或更大规模视觉模型上广泛验证（仅在OpenCLIP ViT-L上做了小样本跨域测试）。
- **超参数敏感**：滤波器位置、核大小、类型对性能有影响（见消融热图），但作者未给出自动选择准则，需手动调优。
- **低通滤波的假设可能过于简化**：在某些任务中，低频成分也可能包含部分语义（如场景全局结构），简单地移除可能不利。

（完）
