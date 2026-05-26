---
title: Nonparametric Classification on Low Dimensional Manifolds using Overparameterized Convolutional Residual Networks
title_zh: 基于过参数化卷积残差网络的低维流形非参数分类
authors: "Zixuan Zhang, Kaiqi Zhang, Minshuo Chen, Yuma Takeda, Mengdi Wang, Tuo Zhao, Yu-Xiang Wang"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=guzWIg7ody"
tags: ["query:ai"]
score: 8.0
evidence: 深度学习理论：过参数化卷积残差网络的非参数分类
tldr: 本文研究过参数化卷积残差网络（ConvResNeXts）的非参数分类性能，证明权重衰减隐式施加稀疏性，使网络适应低维流形上的光滑目标函数，达到最优分类速率，解释了过参数化网络的成功。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-guzwig7ody/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1176, \"height\": 421, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-guzwig7ody/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 689, \"height\": 663, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-guzwig7ody/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 771, \"height\": 606, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-guzwig7ody/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 625, \"height\": 472, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-guzwig7ody/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 626, \"height\": 471, \"label\": \"Figure\"}]"
motivation: 过参数化卷积网络虽实践成功但理论解释不足，需探究其泛化机制。
method: 从非参数分类角度，分析无限宽度ConvResNeXts的权重衰减效应。
result: 证明网络能自适应函数光滑性和低维结构，达到最优分类速率。
conclusion: 为过参数化深度网络的泛化提供了理论依据。
---

## Abstract
Convolutional residual neural networks (ConvResNets), though overparametersized, can achieve remarkable prediction performance in practice, which cannot be well explained by conventional wisdom. To bridge this gap, we study the performance of ConvResNeXts trained with weight decay, which cover ConvResNets as a special case, from the perspective of nonparametric classification. Our analysis allows for infinitely many building blocks in ConvResNeXts, and shows that weight decay implicitly enforces sparsity on these blocks. Specifically, we consider a smooth target function supported on a low-dimensional manifold, then prove that ConvResNeXts can adapt to the function smoothness and low-dimensional structures and efficiently learn the function without suffering from the curse of dimensionality. Our findings partially justify the advantage of overparameterized ConvResNeXts over conventional machine learning models.

---

## 论文详细总结（自动生成）

### 论文核心问题与整体含义（研究动机和背景）

- **问题**：过参数化卷积网络（如ConvResNets）在实际中表现出色，但传统学习理论（要求模型大小不超过样本量）无法解释其泛化能力。理论界长期存在“过参数化为何不导致过拟合”的疑问。
- **背景**：现有工作（如Zhang & Wang 2023）分析了过参数化前馈网络的局部自适应性，但局限于并行FNN结构且受维数灾难影响；而实际广泛使用的ConvResNeXt（包含残差连接、并行瓶颈和卷积核）缺乏相应理论。同时，传统核方法（包括神经正切核NTK）在Besov空间上只能达到次优速率。
- **整体含义**：本文证明，在权重衰减正则化下，宽度可无限大的ConvResNeXt隐式施加稀疏性，能够适应低维流形上的光滑目标函数并达到近乎最优的分类速率，从而部分解释了过参数化深度网络的成功。

### 论文提出的方法论

- **核心思想**：
  - 使用权重衰减（Frobenius范数约束）训练ConvResNeXt，隐式地将网络的有效参数限制在少量“大块”上，其余块对输出贡献可忽略，从而控制模型复杂度。
  - 假设目标函数属于低维流形上的Besov空间，利用流形的局部坐标和B样条分解，再用神经网络逐块逼近。
  - 通过Dudley链（Dudley's chaining）界定量子网络的覆盖数，进而得到本地高斯复杂度的临界半径，推导泛化界。
- **关键技术细节**：
  - **架构定义（公式5）**：ConvResNeXt由N个残差块组成，每块包含M个并行瓶颈（深度L、卷积核大小K、通道数w），每个瓶颈为卷积+ReLU的序列，最后经全连接层输出。
  - **权重约束（公式7）**：残差块所有参数Frobenius范数和≤B_res，输出层范数≤B_out，输出值限制在[0,1]。
  - **近似误差定理（Theorem 3.2）**：存在一个满足约束的ConvResNeXt，其与目标Besov函数的无穷范数误差为O(P^{-α/d} + exp(-C L'))，其中P正比于块数MN。
  - **估计误差定理（Theorem 3.3）**：在有限样本下，经验风险最小化估计的期望风险与最优风险之差接近minimax最优速率Õ(n^{-α/d / (2α/d+1)})，且速率只依赖于流形内在维度d。
  - **覆盖数引理（Lemma 4.1）**：过参数化ConvResNeXt的log覆盖数由B_res、B_out、L、K等界定的一个幂次项给出，证明时通过将残差块分为“小块”和“大块”，移除小块对输出的扰动可控制在δ/2以内。

### 实验设计

- **数据集/场景**：合成数据。生成一维流形嵌入三维空间（螺旋线函数），加上随机旋转和无关特征（维度D可调），标签由一维参数t的Besov函数加噪声得到。
- **基准方法**：核岭回归（RBF核）、XGBoost、决策树、Lasso回归、高斯过程（Matern核）。同时对比另一过参数化模型PNN（并行前馈网络）。
- **对比指标**：均方误差（MSE）。

### 资源与算力

- 论文未明确说明使用的GPU型号、数量或训练时长，只提到实验可在笔记本电脑上复现。因此，资源信息不透明。

### 实验数量与充分性

- **实验数量**：共三组实验（三个图）：
  1. MSE随有效自由度变化（Figure 3）。
  2. MSE随环境维度D变化（Figure 4）。
  3. MSE随样本量n变化（log-log图，Figure 5）。
- **充分性与公平性**：
  - 每个实验结果均包含误差棒（误差条），但未说明重复次数。
  - 基线方法超参数被自动调整或使用默认值；ConvResNeXt超参数固定（w=8, L=6, K=6, M=2, N=2等）。
  - 实验覆盖了不同维度、样本量和复杂度权衡，验证了理论的主要结论（如速率不受D影响、与核方法的速度差异），但缺乏真实数据集验证和消融研究（如改变L、M、N等对性能的影响）。
  - 整体实验设计客观，但样本量较少，充分性一般。

### 主要结论与发现

- **适应低维结构**：ConvResNeXt的学习速率仅依赖于流形内在维度d，不受环境维度D影响，避免了维数灾难。
- **过参数化无害**：只要权重衰减约束总范数，模型复杂度不随块数MN增加而爆炸，泛化界依然成立，且MN只需达到某个下界即可。
- **权重衰减导致稀疏性**：在过参数化下，只有少数“大块”对输出有显著贡献，其余块近乎可忽略，有效模型复杂度受限。
- **深度提升性能**：随着瓶颈深度L增加，估计速率趋近于minimax最优率（L→∞时达n^{-α/d / (2α/d+1)}），而NTK等核方法只能达到次优速率。
- **结构与灵活性**：残差连接和并行瓶颈无需特定排列，MN保持乘积即可，为架构设计提供了理论依据。

### 优点（亮点）

- **理论完整**：同时给出近似误差和估计误差的上界，且下界证明（附录E）确认了接近minimax最优。
- **首次为ConvResNeXt提供理论**：覆盖带残差、卷积、并行瓶颈的复杂架构，不同于以往仅研究简单前馈网络。
- **新颖的覆盖数分析**：通过将残差块按范数大小分类，证明过参数化并不增加覆盖数，技术比Zhang & Wang (2023)的单半径方法更紧。
- **实验支持理论**：合成数据实验验证了维数不敏感性和与核方法的速率差异。

### 不足与局限

- **实验不充分**：仅使用合成数据，未在真实图像/文本等深度网络擅长的任务上验证；缺少对超参数（L, M, N, K）的消融实验和统计显著性检验。
- **理论假设较强**：要求流形光滑、Besov函数满足α-d/p>1（保证B样条收敛），且损失函数为逻辑损失，未推广到其他分类损失。
- **忽略优化**：论文仅分析风险最小化器（ERM）的统计性质，未给出实际优化算法（如SGD）的收敛保证；作者已提及这是有意为之，但限制了结论对训练过程的解释。
- **覆盖数引理局限性**：证明假设L>2，且需要B_res为带量级常数（O(1)），未讨论B_res过大时的退化情况。
- **实验资源不明确**：未报告GPU使用情况，可重复性打折扣。

（完）
