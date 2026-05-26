---
title: Learning Linear Attention in Polynomial Time
title_zh: 在多项式时间内学习线性注意力
authors: "Morris Yau, Ekin Akyürek, Jiayuan Mao, Joshua B. Tenenbaum, Stefanie Jegelka, Jacob Andreas"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=QN0E0KX2LM"
tags: ["query:ai-classic"]
score: 4.0
evidence: Transformer可学习性的基础理论结果
tldr: 针对Transformer的可学习性开放问题，本文首次证明了单层线性注意力Transformer的多项式时间可学习性，通过将其转化为核学习，并提出了多项式时间验证一致性的算法，为深度学习理论奠定基础。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-qn0e0kx2lm/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 878, \"height\": 1167, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qn0e0kx2lm/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 586, \"height\": 382, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qn0e0kx2lm/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 577, \"height\": 442, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qn0e0kx2lm/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 732, \"height\": 505, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qn0e0kx2lm/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1439, \"height\": 349, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-qn0e0kx2lm/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 947, \"height\": 342, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-qn0e0kx2lm/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 944, \"height\": 341, \"label\": \"Table\"}]"
motivation: Transformer的可学习性尚属开放问题。
method: 将线性注意力学习转化为RKHS中的核预测器学习。
result: 首次给出多项式时间PAC可学习结果。
conclusion: 为理解Transformer的学习能力提供理论支撑。
---

## Abstract
Previous research has explored the expressivity of Transformer models in simulating Boolean circuits or Turing machines. However, the efficient learnability of Transformers from data has remained an open question.  Our study addresses this gap by providing the first polynomial-time learnability results (specifically strong, agnostic PAC learning) for single-layer Transformers with linear attention.  We show that learning the optimal multi head linear attention can be recast as finding the optimal kernel predictor in a suitably defined RKHS.  Moving to generalization, we construct an algorithm that, given a dataset, checks in polynomial time whether the set of best fit multi head linear attention networks on this data all perform an identical computation--a powerful notion for out of distribution generalization.  We empirically validate our theoretical findings on several canonical tasks: learning random linear attention networks, key--value associations, and learning to execute finite automata. Our findings bridge a critical gap between theoretical expressivity and learnability of Transformer models.

---

## 论文详细总结（自动生成）

# 论文《Learning Linear Attention in Polynomial Time》中文总结

## 1. 核心问题与整体含义

- **研究动机**：Transformer 在模拟布尔电路和图灵机方面已被证明具有强大的表达能力，但其从数据中**高效可学习性（efficient learnability）** 长期是开放问题。
- **核心问题**：是否存在多项式时间和样本的算法，能够学习单层线性注意力网络的全局最优参数，并保证泛化？
- **整体贡献**：本文首次给出了单层**多头线性注意力（MHLA）** 的强 Agnostic PAC 可学习性证明，并提出了一个可在多项式时间内验证的条件（**可识别性证书**），该条件确保所有经验风险最小化器实现相同的函数，从而实现分布外泛化。

## 2. 方法论

### 核心思想
- 将多头线性注意力（MHLA）的学习重新表述为在合适的再生核希尔伯特空间（RKHS）中寻找最优核预测器。
- 通过构造一个三次多项式特征映射 \(\mathcal{X}(Z)\)，将非凸损失转化为关于矩阵 \(W\) 的线性回归问题。其中 \(W = \sum_h \text{flatten}(V_h) \text{flatten}(Q_h)^T\)。
- 在全秩空间 \(\mathbb{R}^{d^2 \times d^2}\) 中优化 \(W\)（通过普通最小二乘），再通过 SVD 分解得到不超过 \(d^2\) 个注意力头，从而恢复原参数。

### 关键技术细节
1. **特征映射**：对每个输入 \(Z \in \mathbb{R}^{d \times n}\)，构造 \(X(Z) \in \mathbb{R}^{d \times d^2}\)，其元素为 \(\langle z_{j:}, z_{k:} \rangle z_{\ell n}\)。
2. **损失重写**：MHLA 的损失可写为：
   \[
   L(\Theta) = \frac{1}{N} \sum_{i,a} \left( \langle T_\Theta, X_{i,a} \rangle - y_{i,a} \right)^2,
   \]
   其中 \(T_\Theta = \sum_h \text{flatten}(V_h) \text{flatten}(Q_h)^T\)。
3. **松弛与求解**：将 \(T_\Theta\) 替换为无约束矩阵 \(W \in \mathbb{R}^{d^2 \times d^2}\)，通过线性回归求得 \(\hat{W}\)，再对其做 SVD 得到 \(\hat{V}_h, \hat{Q}_h\)。
4. **可识别性证书**：定义数据协方差矩阵 \(\Lambda_D = \mathbb{E}[H(Z) H(Z)^\top]\)（\(H\) 为包含 \(X(Z)\) 及其变体的特征向量）。若 \(\lambda_{\min}(\Lambda_D) > 0\)，则所有经验风险最小化器在任意输入上输出相同（定理 A.3）。
5. **应用**：证明 MHLA 可表达有界计算历史的通用图灵机（UTM），在可识别数据上学习后能外推到任意 TMs 和输入。

## 3. 实验设计

### 数据集与场景
- **合成线性注意力数据**：从单层线性注意力网络生成（\(V \in \mathbb{R}^{1 \times d}, Q \in \mathbb{R}^{d \times d}\)，输入高斯，输出自回归）。
- **关联记忆（Associative Memory）任务**：构造键-值-查询数据，分别从高斯分布（可识别）和随机酉矩阵（不可识别）生成，并按不同比例混合。
- **DFA 执行历史任务**（附录）：学习给定 DFA 转移表和输入词的执行历史。

### 对比方法
- **多头线性注意力**：不同头数 \(m = 1,2,4,8,16\)。
- **多层线性注意力**：不同层数 \(n = 1,2,4\)（单头）。
- **完整 Transformer**：包含 softmax 注意力、MLP、层归一化。
- **凸算法**（本文 Algorithm 1）。

### 评估指标
- 均方误差（MSE） vs 训练轮数；参数在 p 特征空间中的距离；下一 token 预测准确率（DFA）。

## 4. 资源与算力

- **文中未明确说明**：未提及所使用的 GPU 型号、数量、总训练时长或具体计算资源。仅列出了优化器（AdamW）、学习率（0.01/0.001/0.00025）、批大小（32/64）、轮数（500/100）等超参数。实验规模较小（维度 \(d \le 4\)，样本数达 \(2^{14}\)），对算力需求不高。

## 5. 实验数量与充分性

- **实验组数**：主要呈现 3 组：
  1. 对比多头/多层/全 Transformer 在不同维度、数据集大小下的 MSE 曲线（图 1、图 3）。
  2. 关联记忆任务中证书值 vs 参数距离（图 2a），以及可识别/不可识别数据下 SGD 学习参数的距离（图 2b）。
  3. 附录中 DFA 执行的数据需求与状态数、词长、字母表大小的关系（图 4）。
- **消融**：头数、层数、数据维度、数据集大小、可识别性混合比例。
- **充分性评价**：对理论预测（多头优化优势、证书与泛化关联）验证充分；但缺少真实语言或视觉基准测试，且仅在低维度（\(d=2,4\)）上展示，统计上取 3 次运行的标准误，较为有限。因此实验充分但范围受限于合成场景。

## 6. 主要结论与发现

1. **多项式时间可学习性**：首次证明单层线性注意力可在多项式时间内实现强 Agnostic PAC 学习，算法 1 返回的参数保证全局最优（误差 \(\epsilon\)）且样本复杂度 \(\tilde{O}(d^4/\epsilon)\)。
2. **可识别性证书有效**：当数据协方差矩阵满秩时，所有经验风险最小化器输出完全一致，这可由多项式时间算法验证。
3. **多头优于多层的优化特性**：实验中增加头数（特别是 \(d^2\) 头）显著加速收敛并逼近凸算法性能，而增加层数收益递减甚至有害。
4. **证书与泛化正相关**：最小特征值越大，学习到的参数与真实参数在等价特征空间中的距离越小；不可识别数据下 SGD 无法学到正确函数。
5. **UTM 学习的可行性**：在可识别数据下，学习到的 MHLA 可正确模拟任意有界计算历史的图灵机。

## 7. 优点

- **开创性理论结果**：首次为线性注意力提供完整的多项式时间 PAC 可学习性证明，填补了表达能力与可学习性之间的空白。
- **技术巧妙简洁**：通过特征映射将非凸问题转化为线性回归，并利用 SVD 恢复低秩结构，无需复杂优化技巧。
- **提供实用证书**：可识别性条件不仅理论优美，且能通过协方差矩阵最小特征值高效检查，直接关联泛化。
- **实验与理论吻合**：多头优化优势、证书值指导泛化等结论均得到验证。

## 8. 不足与局限

- **模型限制**：仅针对单层线性注意力（无 softmax），与现代 LLM 使用的多层 softmax 注意力+MLP+归一化差距较大，扩展性未证实。
- **实验覆盖有限**：所有实验均在合成数据上进行，未在真实语言/视觉任务中验证，结论的实际适用性有待检验。
- **可识别性条件的实际可达性**：满秩条件在高维数据下可能难以满足，且证书计算涉及 \(O(d^4)\) 复杂度，对大规模维度不友好。
- **缺少组件影响分析**：未讨论位置编码、残差连接、非线性激活等关键组件对可学习性的影响。
- **算力资源未披露**：实验复现所需的具体计算环境未提供，降低了可复现性。
- **泛化保证的严格性**：分布外泛化（UTM 学习）依赖于可识别性假设，在非理想数据下保证可能退化。

（完）
