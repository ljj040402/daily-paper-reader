---
title: "Beyond Random: Automatic Inner-loop Optimization in Dataset Distillation"
title_zh: 超越随机：数据集蒸馏中的自动内循环优化
authors: "Muquan Li, Hang Gou, Dongyang Zhang, Shuang Liang, Xiurui Xie, Deqiang Ouyang, Ke Qin"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=dbZo5cLlV9"
tags: ["query:ai-basics"]
score: 4.0
evidence: 深度学习数据集蒸馏
tldr: 针对数据集蒸馏中内循环优化随机截断的问题，提出自动截断反向传播（AT-BPTT）。该方法根据梯度行为动态调整截断位置和窗口大小，适应不同训练阶段的学习动态，提升数据集蒸馏效率。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-dbzo5cllv9/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1432, \"height\": 622, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dbzo5cllv9/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 621, \"height\": 461, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dbzo5cllv9/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1458, \"height\": 508, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dbzo5cllv9/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 614, \"height\": 362, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dbzo5cllv9/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 671, \"height\": 518, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dbzo5cllv9/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 669, \"height\": 516, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dbzo5cllv9/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1430, \"height\": 622, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dbzo5cllv9/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1444, \"height\": 1436, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-dbzo5cllv9/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1446, \"height\": 783, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dbzo5cllv9/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 769, \"height\": 215, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dbzo5cllv9/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 669, \"height\": 216, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dbzo5cllv9/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1293, \"height\": 914, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dbzo5cllv9/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 945, \"height\": 341, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dbzo5cllv9/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1448, \"height\": 200, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dbzo5cllv9/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1323, \"height\": 363, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dbzo5cllv9/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1022, \"height\": 249, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dbzo5cllv9/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 982, \"height\": 428, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dbzo5cllv9/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1068, \"height\": 336, \"label\": \"Table\"}]"
motivation: 现有内循环优化方法采用随机截断，缺乏灵活性且效果不佳。
method: 观察神经网络训练不同阶段动态，提出AT-BPTT自动调整截断。
result: 通过动态适应梯度行为，提升蒸馏质量。
conclusion: AT-BPTT为数据集蒸馏提供了有效的自动优化策略。
---

## Abstract
The growing demand for efficient deep learning has positioned dataset distillation as a pivotal technique for compressing training dataset while preserving model performance. However, existing inner-loop optimization methods for dataset distillation typically rely on random truncation strategies, which lack flexibility and often yield suboptimal results. In this work, we observe that neural networks exhibit distinct learning dynamics across different training stages—early, middle, and late—making random truncation ineffective. To address this limitation, we propose Automatic Truncated Backpropagation Through Time (AT-BPTT), a novel framework that dynamically adapts both truncation positions and window sizes according to intrinsic gradient behavior. AT-BPTT introduces three key components: (1) a probabilistic mechanism for stage-aware timestep selection, (2) an adaptive window sizing strategy based on gradient variation, and (3) a low-rank Hessian approximation to reduce computational overhead. Extensive experiments on CIFAR-10, CIFAR-100, Tiny-ImageNet, and ImageNet-1K show that AT-BPTT achieves state-of-the-art performance, improving accuracy by an average of 6.16\% over baseline methods. Moreover, our approach accelerates inner-loop optimization by 3.9 × while saving 63\% memory cost.

---

## 论文详细总结（自动生成）

### 论文核心问题与整体含义（研究动机和背景）

- **研究背景**：深度学习对大规模数据集和计算资源高度依赖，数据集蒸馏（Dataset Distillation）旨在从原始数据中合成紧凑的代理数据集，在保持模型性能的同时显著降低存储和计算开销。该问题通常表述为双层优化（bilevel optimization），包含内循环（在合成数据上模拟训练）和外循环（优化合成数据）。
- **核心问题**：现有内循环优化方法（如BPTT、T-BPTT、RaT-BPTT）采用固定或随机截断策略，忽略了神经网络在不同训练阶段（早期、中期、晚期）截然不同的学习动态（早期学习简单模式，晚期精细调整复杂特征），导致截断位置和窗口大小缺乏灵活性，性能次优。
- **整体含义**：本文提出自动截断反向传播（AT-BPTT）框架，通过动态感知训练阶段并自适应调整截断策略，显著提升数据集蒸馏的性能与效率，为内循环优化提供了新的理论依据和实用方案。

---

### 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：利用梯度幅值和梯度变化幅度作为量化指标，自动确定每个训练阶段（早期/中期/晚期）的最优截断位置和窗口大小，并结合低秩Hessian近似降低计算成本，同时引入补丁语义保留（PSP）模块处理高分辨率图像。
- **关键技术细节**：
  1. **动态截断位置（Dynamic Truncation Position, DTP）**：  
     - 基于每个时间步的梯度L2范数，通过温度控制的softmax计算各时间步被选为截断点的概率。  
     - 早期阶段：优先选择梯度幅值大的时间步（倾向于简单模式）。  
     - 中期阶段：随机均匀选择。  
     - 晚期阶段：优先选择梯度幅值小的时间步（倾向精细调整）。  
     - 概率公式如下（Early Stage为例）：  
       $$P_{\text{trunc}}(t) = \frac{\exp(\|\nabla_\theta \mathcal{L}_t\|_2 / \tau)}{\sum_{i=1}^T \exp(\|\nabla_\theta \mathcal{L}_i\|_2 / \tau)}$$
  2. **自适应窗口大小（Adaptive Window Size, AWS）**：  
     - 基于梯度变化幅度（当前步与上一步梯度L2范数之差的绝对值）计算窗口权重$\eta(t)$。  
     - 窗口大小在基窗口$W$的基础上线性调整：$W^*(t) = W - d + 2d \cdot \eta(t)$，其中$d$控制调整范围。  
     - 梯度变化大的时间步获得更大窗口以保留关键信息。
  3. **阈值引导的阶段转换（Threshold-guided Stage Transition）**：  
     - 使用精度变化$\Delta A_t = A_t - A_{t-1}$和两个计数器$C_{\text{early-middle}}, C_{\text{middle-late}}$。  
     - 当连续出现一定次数$\Delta A_t < M$时进入中期；当连续出现一定次数$\Delta A_t < N$时进入晚期。
  4. **低秩Hessian近似（Low-Rank Hessian Approximation, LRHA）**：  
     - 利用Hessian矩阵的低秩特性，通过随机SVD和Hessian-vector乘积（HVP）近似$\widetilde{H}_j$。  
     - 将原始复杂度从$O(p^2)$降至$O(p k_j + k_j^3)$，内存从$O(p^2)$降至$O(2p k_j + k_j^2)$。
  5. **补丁语义保留（Patch-wise Semantic Preservation, PSP）**：  
     - 将高分辨率图像分割为$n \times n$非重叠补丁（$n=4$），每个补丁独立蒸馏。  
     - 通过原型质心对齐损失$\mathcal{L}_{\text{align}}$保证语义一致性，最终损失为$\mathcal{L}_{\text{total}} = \mathcal{L}_{\text{AT-BPTT}} + \lambda \mathcal{L}_{\text{align}}$。
- **算法流程**（文字描述）：
  1. 初始化计数器$C_1, C_2$，总时间步$T$。
  2. 对每个时间步$t$：
     - 应用PSP分割图像。
     - 计算精度变化并更新计数器。
     - 根据计数器是否达到阈值切换阶段（Early→Middle→Late）。
     - 基于当前阶段根据梯度幅值计算截断概率$P_{\text{trunc}}(t)$。
     - 基于梯度变化幅度计算自适应窗口$W^*(t)$。
     - 使用LRHA计算Hessian近似并得到元梯度$\nabla_S \mathcal{L}_{\text{meta}}$。
     - 更新模型参数和蒸馏数据集$S$。

---

### 实验设计

- **数据集与场景**：
  - 低分辨率：CIFAR-10（32×32, 10类）、CIFAR-100（32×32, 100类）、Tiny-ImageNet（64×64, 200类）。
  - 高分辨率：ImageNet-1K（224×224, 1000类）。
  - IPC设置：CIFAR-10/100使用1、10、50；Tiny-ImageNet和ImageNet-1K使用1、10。
- **基准（Benchmark）**：遵循标准协议，使用ConvNet（CIFAR用Conv-3，Tiny-ImageNet/ImageNet用Conv-4/Conv-5）。
- **对比方法**：
  - 外循环优化：DSA, CAFE, MTT, TESLA, DATM, ATT, MCT, NCFM等。
  - 内循环优化：BPTT, FRePO, RCIG, RaT-BPTT, Teddy等。
- **额外对比**：扩散模型方法（D4M, D2M）、宽网络场景（KIP, RFAD等）、语言任务（SST-2, MNLI-m, AGNews）以及ImageNet子集（ImageNette等）。

---

### 资源与算力

- 实验使用 **NVIDIA A800 GPU**（未明确说明具体数量）。
- 典型训练时长（以CIFAR-10 IPC=10为例）：RaT-BPTT需21.6小时，AT-BPTT（LRHA版）仅需5.5小时，加速约**3.9×**。
- 内存节省：相比RaT-BPTT降低**63%**（从16.7G降至6.94G）。
- 其他数据集和IPC的设置下，训练时间和内存消耗在文中图4和表5中有详细展示。

---

### 实验数量与充分性

- **实验数量**：超过10组主要对比实验（4个标准数据集×多种IPC），15+消融实验（组件、超参数、窗口大小d），以及在宽网络、语言任务、高分辨率子集上的泛化实验。
- **充分性**：
  - 所有主要结果均报告5次实验的平均值和标准差，统计可靠。
  - 消融实验覆盖了三个核心组件（DTP, AWS, PSP）和关键超参数（M,N,X,Y,d），验证了各自贡献。
  - 对比方法覆盖面广（12种以上SOTA），包括内循环和外循环方法。
  - 在多种分辨率、多种模型架构上验证，结论具有普遍性。
- **客观公平性**：与基线方法在同一框架（RaT-BPTT实施细节）下进行控制变量实验，无选择性报告。

---

### 论文的主要结论与发现

1. **神经网络的阶段性学习动态**：早期倾向于大梯度简单模式，晚期关注小梯度精细调整，中期对截断策略不敏感。随机截断无法匹配这种动态。
2. **AT-BPTT显著优于现有内循环方法**：在CIFAR-10/100、Tiny-ImageNet、ImageNet-1K上平均提升6.16%准确率（相对于RaT-BPTT），并达到新的SOTA。
3. **计算效率巨大提升**：通过LRHA和自适应窗口，实现3.9×加速和63%内存节省，同时保持或提升精度。
4. **组件协同效应**：DTP和AWS结合产生超可加性改进（2.8%提升，高于单独贡献之和）；PSP对高分辨率任务尤为关键（ImageNet-1K上提升17.6%）。
5. **阈值设计指导意义**：阶段转换超参数（M=1.5, X=5%总epoch等）可平衡阶段持续时间，避免过早或延迟切换。

---

### 优点

- **创新性方法**：首次将训练阶段动态与截断策略显式关联，利用内在梯度信号而非随机性。
- **高效实用**：低秩Hessian近似大幅降低二阶优化的计算瓶颈，窗口自适应进一步节省资源。
- **全面实验**：覆盖多个数据集、IPC、模型架构，以及泛化到语言任务和宽网络，验证方法鲁棒性。
- **开源承诺**：论文声明将开源代码，促进可重复性。
- **理论动机清晰**：通过假设验证实验（图1）直观展示不同阶段截断偏好，方法设计有据可依。

---

### 不足与局限

- **算力依赖未完全消除**：虽加速明显，但内循环展开仍需较多计算，在更大模型（如Vision Transformer）上未验证。
- **架构局限**：基础网络仅使用简易ConvNet（3~5层），未在更深或复杂架构上测试，可能限制实际场景适用性。
- **超参数敏感**：阶段转换阈值（M,N,X,Y）和窗口范围d需手动调整，不同数据集可能需要重新搜索。
- **高分辨率处理仍有限**：ImageNet-1K上IPC=10仅30.6%准确率，与全数据集（33.8%）差距较大，蒸馏能力仍有提升空间。
- **未涉及其他任务**：仅测试图像分类和简单文本分类，未在检测、分割等任务上验证，通用性待证。
- **与部分外循环方法对比**：虽然性能领先，但某些外循环方法（如DATM、NCFM）在某些设置下也接近，没有绝对碾压，且外循环方法通常计算更简单。

---

（完）
