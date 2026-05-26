---
title: Nonparametric Modern Hopfield Models
title_zh: 非参数现代霍普菲尔德模型
authors: "Jerry Yao-Chieh Hu, Bo-Yu Chen, Dennis Wu, Feng Ruan, Han Liu"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=xkV3uCQtJm"
tags: ["query:ai"]
score: 7.0
evidence: 提出稀疏结构的现代Hopfield模型，与Transformer注意力相关
tldr: 该论文为非参数现代Hopfield模型提供了新的解释框架，将记忆存储和检索视为非参数回归问题。在此基础上提出了稀疏结构的现代Hopfield模型，实现了次二次复杂度，并保留了与Transformer注意力的理论联系。实验表明新模型在理论上具有良好性质，为高效关联记忆模型开辟了新方向。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-xkv3ucqtjm/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1778, \"height\": 408, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xkv3ucqtjm/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1755, \"height\": 1168, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xkv3ucqtjm/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1064, \"height\": 534, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xkv3ucqtjm/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1765, \"height\": 1183, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xkv3ucqtjm/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1057, \"height\": 523, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xkv3ucqtjm/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1762, \"height\": 603, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xkv3ucqtjm/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1758, \"height\": 603, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-xkv3ucqtjm/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1767, \"height\": 1652, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xkv3ucqtjm/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 523, \"height\": 535, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xkv3ucqtjm/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 938, \"height\": 278, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xkv3ucqtjm/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 647, \"height\": 407, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xkv3ucqtjm/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1199, \"height\": 424, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xkv3ucqtjm/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1767, \"height\": 884, \"label\": \"Table\"}]"
motivation: 传统现代Hopfield模型计算复杂，缺乏高效的稀疏变体，且与Transformer注意力的理论联系尚不充分。
method: 将记忆存储与检索解释为非参数回归问题，引入稀疏性约束，构建稀疏结构的现代Hopfield模型。
result: 新模型在保持理论性质的同时将复杂度降至次二次，并在多个任务上验证了有效性。
conclusion: 非参数视角为设计高效现代Hopfield模型提供了统一框架，且有助于理解Transformer注意力机制。
---

## Abstract
We present a nonparametric interpretation for deep learning compatible modern Hopfield models and utilize this new perspective to debut efficient variants. 
Our key contribution stems from interpreting the memory storage and retrieval processes in modern Hopfield models as a nonparametric regression problem subject to a set of query-memory pairs.
Interestingly,
our framework not only recovers the known results from the original dense modern Hopfield model but also fills the void in the literature regarding efficient modern Hopfield models, by introducing *sparse-structured* modern Hopfield models with sub-quadratic complexity.
We establish that this sparse model inherits the appealing theoretical properties of its dense analogue --- connection with transformer attention,  fixed point convergence and exponential memory capacity.
Additionally, we showcase the versatility of our framework by constructing a family of modern Hopfield models as extensions, including linear, random masked, top-$K$ and positive random feature modern Hopfield models.
Empirically, we validate our framework in both synthetic and realistic settings for memory retrieval and learning tasks.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义

现代 Hopfield 模型是一类与 Transformer 注意力机制兼容的联想记忆模型，具有指数级存储容量、单步检索和单调能量下降等优良性质。然而，现有模型存在三大缺陷：

- **（P1）效率不足**：稠密模型和已有稀疏变体（Hu et al., 2023）仍为 O(n²) 复杂度，难以扩展至大规模基础模型；
- **（P2）缺乏对稀疏性的严格分析**：先前工作仅给出定性论证，未刻画稀疏性对检索误差、分离条件和容量的定量影响；
- **（P3）注意力与 Hopfield 模型的连接不完整**：仅桥接了一部分注意力变体（如 softmax），未能系统连接多种高效注意力机制（线性、随机特征、滑动窗口等）。

本文提出一个**非参数框架**，将记忆存储与检索建模为带软间隔的支持向量回归（SVR）问题，从而统一地推导出一族现代 Hopfield 模型。该框架不仅恢复稠密模型的结果，还自然引出**稀疏结构现代 Hopfield 模型**，实现**次二次复杂度**，并保持与注意力机制的联系、固定点收敛、指数级存储容量等优良理论性质。

## 2. 方法论

### 核心思想
- 将检索动力学 \( T(x) \) 视为一个学习问题：给定带噪声的记忆‑查询对数据集 \( \mathcal{D} = \{(\xi_\mu + \delta\xi_\mu,\; \xi_\mu)\}_{\mu=1}^M \)，学习一个函数 \( f_{W,\Phi}(x)=W\Phi(x) \) 使其满足“每个记忆周围半径为 \( R \) 的球是广义固定点”的定义。
- 采用软间隔 SVR（支持向量回归）形式化该学习问题，通过拉格朗日对偶得到权重 \( w_i^* = \sum_{\mu=1}^M (\alpha_\mu[i] - \tilde{\alpha}_\mu[i])\Phi(\xi_\mu+\delta\xi_\mu) \)。
- 进而获得一般形式的检索动力学：\( x^{\text{new}}[i] = \langle w_i^*, \Phi(x)\rangle \)。

### 关键技术细节
1. **稠密模型（恢复）**：选择 \(\Phi\) 为指数核的泰勒展开（无限维特征），解出 \( T_{\text{Dense}}(x) = \Xi \cdot \text{Softmax}(\beta\Xi_\delta^\top x) \)。
2. **稀疏结构模型（核心贡献）**：引入支撑集掩码 \( \mathcal{M} \subseteq [M] \)（大小为 \( k \)），仅对 \( \mu \in \mathcal{M} \) 保留约束，解出：
   \[
   T_{\text{Sparse}}(x) = \sum_{\mu\in\mathcal{M}} \bigl[\text{Softmax}(\beta\Xi_{\mathcal{M}}^\top x)\bigr]_\mu\, \xi_\mu.
   \]
3. **高效变种**：
   - **随机掩码**（BigBird 式）：\( O(kL) \)；
   - **滑动窗口**（Longformer 式）：\( O(L\sqrt{L}) \)；
   - **Top‑K**：选择内积最大的 K 个记忆，仍为 \( O(M^2) \)（但可用于高效实现）。
4. **理论分析**：
   - 依赖稀疏度的检索误差界（Theorem 4.1）：\( \|T_{\text{Sparse}}(x)-\xi_\mu\| \le m(M+k-2)\exp(-\beta\Delta_\mu) \)；
   - 对比稠密模型更紧的误差（Corollary 4.1.1）；
   - 无需能量函数即可证得固定点收敛（Corollary 4.1.3）；
   - 扩展的容量下界（Proposition 4.1）：\( M_{\text{Sparse}} \ge \sqrt{p}\, C^{\frac{d-1}{4}} \)，呈指数于模式维度 \( d \)。

5. **扩展模型**（附录E）：线性、多头、正随机特征（Performer 式）现代 Hopfield 模型均可通过选择不同的核映射 \(\Phi\) 纳入统一框架。

## 3. 实验设计

### 使用的数据集/场景
- **记忆检索任务**（Appendix G.1）：MNIST（稀疏）和 CIFAR-10（稠密），测试半掩图像恢复和不同噪声水平下的恢复误差。
- **多实例学习（MIL）** ：
  - 合成 MNIST 袋（Appendix G.2）：不同袋大小（5~100），预测袋中是否包含负信号；
  - 真实数据集（Appendix G.3）：Elephant、Fox、Tiger（图像标注）和 UCSB 乳腺癌分类。
- **时间序列预测**（Appendix G.4）：ETTh1、ETTm1、ECL、WTH、Traffic 五个数据集，四种预测长度（96/192/336/720）。
- **计算效率**（Appendix G.5）：测量不同输入长度下的每批处理时间和 FLOPs。

### Benchmark 与对比方法
- **基线**：Dense Hopfield (Ramsauer et al., 2020)、Sparse Hopfield (Hu et al., 2023)。
- **本文变体**：Top‑K (20%/50%/80%)、Random Masked、Window、Linear、Random Feature (PRF) Hopfield。
- **指标**：MIL 用 AUC；时间序列用 MSE/MAE；记忆检索用平方误差。

### 实验公平性
- 均采用相同网络结构（embedding + Hopfield pooling + FC）和优化器（AdamW）控制变量。
- 超参数搜索空间（学习率、隐层维度、头数等）统一。
- 多次重复（5~10 次）报告均值和标准差。

## 4. 资源与算力

- **硬件**：NVIDIA GEFORCE RTX 2080 Ti + Intel Xeon Silver 4214 @ 2.20GHz。
- **软件**：PyTorch 1.8.0，使用 RayTune 进行超参搜索。
- **未明确说明**：总 GPU 时数、训练 epoch 数（仅说 150 epoch for MNIST MIL, 50 epoch for 真实 MIL, 50 epoch for 时间序列）及具体单次训练时长。

## 5. 实验数量与充分性

- 共设置 **5 大类场景**：记忆检索（2 个数据集 × 多种噪声/掩码比例）、合成 MIL（1 个数据集 × 多种袋大小）、真实 MIL（4 个数据集 × 8 种方法）、时间序列（5 个数据集 × 4 种预测长度 × 8 种方法）、效率测试（不同输入长度）。
- **消融/组件分析**：通过变化 Top‑K 比例、随机掩码比例、窗口大小等，验证稀疏度影响。
- **充分性**：涵盖了理论验证（记忆检索误差）、下游任务性能（MIL、时间序列）和实际效率（耗时、FLOPs）。实验设置合理，多次重复，结果稳定。
- **客观性**：作者承认存在“准确率‑效率权衡”（accuracy-efficiency tradeoff），并指出随机掩码模型在目标记忆被掩去时性能差，符合理论预期。

## 6. 论文的主要结论与发现

1. **非参数框架有效恢复并扩展了现代 Hopfield 模型**：新框架以 SVR 形式统一了多种变体，包括稠密、稀疏、线性、多头、随机特征等。
2. **稀疏结构模型具有理论优势**：更紧的检索误差界、更强的噪声鲁棒性、指数级容量，且无需能量函数即可保证固定点收敛。
3. **高效变体实现次二次复杂度**：在保持理论性质的同时，线性、随机特征、滑动窗口等模型在实验中显着降低计算时间和 FLOPs。
4. **实验验证了理论与实用性能**：在多种任务上，Top‑K 和 Sparse 模型在检索精度与下游任务上接近或超越稠密模型；线性/PRF 模型在效率提升同时性能损失可控。
5. **连接注意力机制**：框架提供了 Bridge between Hopfield models and various efficient attention mechanisms（BigBird, Longformer, Performer, 线性注意力等）。

## 7. 优点

- **理论深度与统一性**：首次将 Hopfield 模型严格视为非参数回归问题，用 SVR 的对偶形式导出检索动力学，使得不同核映射对应不同注意力变体。
- **填补效率空白**：针对 Hu et al. (2023) 的稀疏模型仅加速检索、未降低整体复杂度的问题，本文直接通过掩码和核函数降低复杂度至次二次。
- **完备的理论分析**：给出了稀疏依赖的检索误差界、固定点收敛证明（无需能量函数）、以及指数级容量下界，且这些结果在 \( k=M \) 时退化至稠密情形，保持了自洽性。
- **实验全面覆盖**：从合成数据到真实世界任务，从记忆检索到监督学习与时间序列，并额外测量效率，验证了方法的普适性和实际可行性。
- **开源代码**：便于复现与后续研究。

## 8. 不足与局限

- **依赖假设**：理论分析假设模式是良好分离的（well-separation condition），且目标记忆必须在支撑集 \( \mathcal{M} \) 中。对于随机掩码模型，若目标被掩去则检索失败（正如实验所示）。
- **可扩展性验证有限**：仅测试了中等规模的数据（MNIST、小时间序列），未在大规模语言模型或视觉 Transformer 上验证。
- **未讨论所有变体的理论保证**：线性、多头等扩展模型的固定点收敛和容量未严格证明（仅在附录中给出描述）。
- **计算效率依赖实现**：随机掩码模型在 PyTorch 稀疏矩阵操作（beta 阶段）下并未获得实际加速（FLOPs 统计可能不准），作者也指出这一点。
- **未做严格消融**：例如，未单独验证不同核函数对性能的独立贡献。
- **未公开完整训练时长**：总计算开销（GPU 小时数）未报告，不利于复现和比较。

（完）
