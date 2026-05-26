---
title: "SS1: Accelerating Inference with Fast and Expressive Sketch Structured Transform"
title_zh: SS1：快速且富有表达力的Sketch结构化变换加速推理
authors: "Aditya Desai, Kimia Saedi, Apoorv Walia, Jihyeong Lee, Keren Zhou, Anshumali Shrivastava"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=nrgyOGU7ZP"
tags: ["query:ai"]
score: 8.0
evidence: 加速深度学习推理的GPU友好结构化变换
tldr: 本文提出Sketch结构化变换（SS1），一种GPU友好的算子，通过随机但结构化的参数共享减少计算量，在保持表达力的同时加速深度模型推理。解决了非结构化矩阵硬件不匹配与结构化矩阵表达力不足的矛盾。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-nrgyogu7zp/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1239, \"height\": 470, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-nrgyogu7zp/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 519, \"height\": 512, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-nrgyogu7zp/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 673, \"height\": 493, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-nrgyogu7zp/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1292, \"height\": 781, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-nrgyogu7zp/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1419, \"height\": 507, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-nrgyogu7zp/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1419, \"height\": 514, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-nrgyogu7zp/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1308, \"height\": 381, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-nrgyogu7zp/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1450, \"height\": 386, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-nrgyogu7zp/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1444, \"height\": 216, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-nrgyogu7zp/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 789, \"height\": 145, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-nrgyogu7zp/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 777, \"height\": 303, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-nrgyogu7zp/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 816, \"height\": 186, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-nrgyogu7zp/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 641, \"height\": 512, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-nrgyogu7zp/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 727, \"height\": 430, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-nrgyogu7zp/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 640, \"height\": 511, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-nrgyogu7zp/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 725, \"height\": 430, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-nrgyogu7zp/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1439, \"height\": 231, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-nrgyogu7zp/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1066, \"height\": 145, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-nrgyogu7zp/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 962, \"height\": 228, \"label\": \"Table\"}]"
motivation: 学习权重矩阵的变体在效率与表达力间存在权衡。
method: 采用随机但结构化的参数共享方式构建变换算子。
result: 在多种模型上实现了显著的推理加速且精度损失小。
conclusion: 为深度学习推理提供了高效且通用的算子替代方案。
---

## Abstract
Tensor multiplication with learned weight matrices is the fundamental building block in deep learning models. These matrices can often be sparsified, decomposed, quantized, or subjected to random parameter sharing without losing accuracy, suggesting the possibility of more efficient transforms. Although many variants of weight matrices exist, unstructured ones are incompatible with modern hardware, slowing inference and training. On the other hand, structured variants often limit expressivity or fail to deliver the promised latency benefits. We present Sketch Structured Transform (SS1), an expressive and GPU-friendly operator that accelerates inference. SS1 leverages parameter sharing in a random yet structured manner to reduce computation while retraining the rich expressive nature of parameter sharing. We confirm empirically that SS1 offers better quality-efficiency tradeoffs than competing variants. Interestingly SS1 can be combined with Quantization to achieve gains unattainable by either method alone, a finding we justify via theoretical analysis. The analysis may be of independent interest.
Moreover, existing pre-trained models can be projected onto SS1 and finetuned for efficient deployment. Surprisingly, these projected models can perform reasonably well even without finetuning. Our experiments highlight various applications of the SS1:
(a) Training GPT2 and DLRM models from scratch for faster inference. (b) Finetuning projected BERT models for 1.31× faster inference while maintaining GLUE scores. (c) Proof of concept with Llama-3-8b, showing 1.11× faster wall clock inference using projected SS1 layers without finetuning. We open source our code :https://github.com/apd10/Sketch-Structured-Linear/

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

深度学习模型中的张量乘法（Tensor multiplication）是基础运算，但学习到的权重矩阵往往存在冗余，可通过稀疏化、分解、量化、随机参数共享等方式压缩而不显著损失精度。然而，非结构化稀疏与硬件不兼容，导致推理和训练变慢；结构化变体（如结构化稀疏、低秩分解）虽高效，但常牺牲表达力或无法兑现延迟收益。论文旨在设计一种**既GPU友好又富有表达力的结构化变换算子**，在减少计算量的同时保持模型质量，并可与量化等现有技术结合，实现单一方法无法达到的效率提升。

## 2. 方法论：核心思想、关键技术细节、算法流程

### 2.1 核心思想

- **Sketch Structured Transform (SS1)** 属于随机参数共享（RPS）方法，但与传统RPS（仅减少内存，不影响FLOPs）不同，SS1通过**在单个神经元内部进行参数绑定**来减少计算量。
- 核心技巧：将神经元的权重向量 \(w \in \mathbb{R}^K\) 通过随机映射从压缩向量 \(z \in \mathbb{R}^{K/c}\) 恢复（\(c\)为压缩因子）。输出计算 \(y = x^\top w = (x^\top S)z\)，其中\(S\)为稀疏草图矩阵，\(x^\top S\)仅涉及加法和减法，乘加次数从\(K\)降至\(K/c\)。

### 2.2 关键技术：K-coalescing 与 N-coalescing

- **K-coalescing**：限制哈希函数使得同一超级组（supergroup）内的块（chunk）共享权重，且块内权重连续存储，从而实现缓存友好的块状计算。
- **N-coalescing**：沿输出维度（N）分组，同一列块的神经元共享相同的哈希函数，便于GPU上的块矩阵乘法。

### 2.3 算法流程（文字描述）

- 输入：数据矩阵 \(X \in \mathbb{R}^{M \times K}\)，压缩权重矩阵 \(Z \in \mathbb{R}^{(K//c) \times N}\)，压缩因子 \(c\)，分块参数 \(B_M, B_K, B_N\)，哈希函数 \(h\) 和符号函数 \(g\)。
- 输出：\(Y = \text{SS1}(X, Z)\)。
- 步骤：
  1. 对输出维度分块（大小为\(B_N\)），对输入维度分块（大小为\(B_K\)）。
  2. 对于每个输出块，迭代K维度的超级块（大小为\(c B_K\)）：
     - 利用哈希函数将\(c\)个输入块聚合（旋转并对齐）为草图输入（大小为\(B_K\)）。
     - 将草图输入与对应的压缩权重块进行矩阵乘法，累加到输出块。
- 该实现通过预加载、向量化加载、自动调优等优化，确保GPU高效运行。

### 2.4 预训练模型投影

- 给定预训练的全权重矩阵\(W\)，通过求解线性回归\(z^* = \arg\min_z \|w - Sz\|\)得到每神经元的最优压缩向量\(z\)（\(S^\top S\)为对角矩阵，可解析求解）。整个投影可按块高效实现。

### 2.5 与标准RPS结合

- SS1减少计算量，标准RPS减少参数量，两者可独立控制，进一步压缩参数内存。

## 3. 实验设计

### 3.1 数据集与任务场景

| 场景 | 模型 | 数据集/基准 | 评价指标 |
|------|------|-------------|----------|
| NLP语言建模 | GPT2 (Small/Medium/Large) | Wikitext-103 | 困惑度 (PPL)、损失、延迟 |
| 视觉分类 | MLPMixer (S/M/L) | CIFAR-10, CIFAR-100 | 准确率、延迟 |
| 自然语言理解 | BERT (Base/Large) | GLUE基准（9项任务） | GLUE得分、延迟 |
| 大规模语言模型 | Llama-3-8B | MMLU, Winogrande | 准确率、延迟 |
| 推荐系统 | DLRM MLPerf Benchmark | 100GB嵌入表 + 10MB MLP | 质量（AUC）、成分耗时 |

### 3.2 对比方法

- Monarch：SOTA结构化稀疏变换（不同块数 nb=2,4,8）
- LowRank：低秩分解变换（约2x,4x,8x压缩）
- 标准全连接层（Original）
- 部分实验还对比了ROAST（标准RPS方法）、小模型（SmallModel）、量化（Post-training quantization）

### 3.3 实验内容

- **端到端质量-延迟权衡**：在GPT2和MLPMixer上，固定参数预算下比较SS1 vs. Monarch vs. LowRank。
- **核函数延迟**：单独测试不同形状下各算子的延迟。
- **量化联合实验**：对SS1模型和原模型施加8位后训练量化，比较量化前后质量。
- **预训练模型投影+微调**：将BERT投影到SS1后微调，评估GLUE分数及加速比。
- **无需微调的投影**：Llama-3-8B直接投影SS1部分层，评估MMLU/Winogrande得分。
- **CPU工作负载**：分析DLRM MLPerf各组件耗时，展示SS1可减少MLP计算约2倍。

### 3.4 资源与算力

- GPT2训练：4块V100-32GB GPU，每个配置约13小时（Small模型）。
- BERT微调：RTX-8000 Quadro，最大任务QQP约7-8小时。
- Llama-3-8B评估：1块A100-40GB，约1小时。
- MLPMixer训练：1块RTX Quadro 8000，约2小时每配置。
- 未提及所有实验的总GPU时数，但算力说明较充分。

## 4. 实验数量与充分性

- **总实验组数**：涵盖4个领域（NLP、视觉、理解、推荐），共约10+个不同模型/压缩比例组合，每个组合多次运行（如GPT2不同尺寸、不同压缩倍数；BERT两种尺寸；LLaMA两个任务；DLRM一个基准）。
- **消融实验**：
  - 对SS1的超参数\(B_K\)进行理论分析，证明其为纯延迟参数，不影响学习质量。
  - 与标准RPS对比（ROAST），显示SS1在延迟上的优势。
  - 量化+SS1联合实验，证实质量保持。
- **客观性与公平性**：
  - 所有对比方法使用相同训练超参数（来自Monarch论文的推荐值）。
  - 对Monarch进行了学习率调优（附录C），确认调优后SS1仍占优。
  - 报告统计显著性：GPT2 PPL标准差约0.2，BERT GLUE报告多次运行均值和标准差。
  - 但部分结果（如DLRM）仅报告单次运行值（0.8032），未提供置信区间。

## 5. 主要结论与发现

1. **SS1提供更好的质量-效率权衡**：在相同参数预算下，SS1在GPT2和MLPMixer上均优于Monarch和LowRank；端到端推理吞吐提升可达1.30×（GPT2）和1.31×（BERT）。
2. **可与量化高效结合**：量化对SS1模型的影响与对全模型相当，且理论分析表明联合压缩的方差低于单一方法。
3. **预训练模型投影可行**：BERT投影至SS1后微调，GLUE分数几乎不变（下降<2.6分），推理加速1.31×。Llama-3-8B投影后无需微调，MMLU仅下降约3.8分，延迟提升1.11×。
4. **CPU工作负载潜力**：DLRM的Top MLP耗时占据71.3%，SS1可将其参数减半且保持AUC不变。

## 6. 优点

- **创新性**：首次在RPS框架内同时实现参数减少和计算减少，并通过K/N-coalescing解决GPU效率问题。
- **理论贡献**：给出了量化与SS1联合的方差上界分析，以及\(B_K\)对学习质量无影响的证明。
- **实用性**：支持预训练模型直接投影（无需微调即可使用），降低了部署成本。
- **广泛的实验验证**：覆盖NLP、视觉、推荐、大型语言模型等多个场景，与SOTA结构方法（Monarch）和经典方法（LowRank）充分对比。
- **代码开源**：提供完整实现和Kernel优化（Triton），便于复现。

## 7. 不足与局限

- **理论分析的局限性**：关于量化+SS1联合的方差分析以及参数\(B_K\)的讨论均基于线性模型和标准降维设置，在深度非线性模型中的适用性未经验证。
- **反向传播未加速**：SS1仅减少前向计算量，反向传播计算量与全模型相同，因此训练加速不明显，主要针对推理。
- **压缩效率上限**：实验显示超过8×压缩后延迟增益边际递减，且模型质量下降明显。
- **部分实验覆盖不足**：
  - 量化联合实验仅测试了质量，未实现量化后的SS1核函数，无法测量联合延迟。
  - DLRM实验仅展示质量，未实现CPU核函数，延迟收益为推测。
  - 未与块稀疏（Block Sparse）方法对比（因FP16下PyTorch实现不稳定）。
- **超参数敏感性**：\(B_N\)影响神经元间相关性，实验中需谨慎选择以保证质量，论文未提供自动选择策略。

（完）
