---
title: Large-Scale Contextual Market Equilibrium Computation through Deep Learning
title_zh: 基于深度学习的大规模上下文市场均衡计算
authors: "Yunxuan Ma, Yide Bian, Hao Xu, Weitao Yang, Jingshu Zhao, Zhijian Duan, Feng Wang, Xiaotie Deng"
date: 2024-05-15
pdf: "https://openreview.net/pdf?id=JWF1dN4TOd"
tags: ["query:ai"]
score: 5.0
evidence: 基于深度学习的大规模市场均衡计算方法
tldr: 本文研究大规模买家场景下的市场均衡计算，提出MarketFCNet深度学习方法。通过神经网络参数化买家与商品的分配，基于上下文特征近似均衡，突破了传统方法的小规模局限。
source: NeurIPS-2024-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-jwf1dn4tod/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1307, \"height\": 646, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-jwf1dn4tod/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1452, \"height\": 284, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-jwf1dn4tod/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 472, \"height\": 520, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-jwf1dn4tod/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 466, \"height\": 508, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-jwf1dn4tod/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 920, \"height\": 325, \"label\": \"Table\"}]"
motivation: 现有市场均衡计算难以处理大规模买家群体。
method: 使用神经网络基于上下文参数化分配，近似均衡。
result: 在大规模上下文市场模拟中有效逼近均衡。
conclusion: 为经济市场均衡计算提供了可扩展的深度学习方案。
---

## Abstract
Market equilibrium is one of the most fundamental solution concepts in economics and social optimization analysis.
Existing works on market equilibrium computation primarily focus on settings with a relatively small number of buyers.
Motivated by this, our paper investigates the computation of market equilibrium in scenarios with a large-scale buyer population, where buyers and goods are represented by their contexts.
Building on this realistic and generalized contextual market model, we introduce MarketFCNet, a deep learning-based method for approximating market equilibrium.
We start by parameterizing the allocation of each good to each buyer using a neural network, which depends solely on the context of the buyer and the good.
Next, we propose an efficient method to estimate the loss function of the training algorithm unbiasedly, enabling us to optimize the network parameters through gradient descent.
To evaluate the approximated solution, we introduce a metric called Nash Gap, which quantifies the deviation of the given allocation and price pair from the market equilibrium.
Experimental results indicate that MarketFCNet delivers competitive performance and significantly lower running times compared to existing methods as the market scale expands, demonstrating the potential of deep learning-based methods to accelerate the approximation of large-scale contextual market equilibrium.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义

- **研究动机**：市场均衡是经济学和社会优化中的基础概念，广泛应用于公平分配、广告拍卖等领域。传统计算方法主要针对小规模买家（如400左右），但在现实场景（如就业市场、在线购物市场）中买家数量可达数百万甚至无限，此时描述复杂度为 \(O(nm)\)，每一步优化都需要 \(O(nm)\) 的代价，传统方法无法扩展。
- **核心问题**：如何在大规模买家群体下高效地近似计算市场均衡？论文提出利用上下文模型（contextual model）将买家和商品用低维向量表示，将描述复杂度降低到 \(O(n+m)\)，并在此基础上设计深度学习方法来近似均衡。
- **整体含义**：本文开创性地将深度学习引入大型上下文市场均衡计算，证明了深度学习方法在扩展性和运行时间上的优势，为处理现实大规模市场提供了新思路。

## 2. 论文提出的方法论

- **核心思想**：将市场均衡的分配函数参数化为一个神经网络（MarketFCNet），该网络仅依赖于买家上下文和商品上下文，输出分配量 \(x_\theta(b_i, g_j)\)。通过优化一个基于EG凸规划的无偏估计目标函数来训练网络，并利用增广拉格朗日乘子法（ALMM）处理市场清仓约束。
- **关键技术细节**：
  - 使用全连接网络（5层，每层宽度256）作为分配网络，输入为买家表示和商品表示拼接后的向量。
  - 将EG凸规划的目标函数重写为期望形式：\(\max_{x_\theta} \mathbb{E}_b [B(b) \log u(b; x_\theta(b, g))]\)，约束为 \(\mathbb{E}_b[x_\theta(b, g_j)] = Y(g_j)/n\)。
  - 采用增广拉格朗日函数 \(L_\rho(x_\theta; \lambda)\) 处理等式约束，包括原始目标、拉格朗日乘子项和二次惩罚项。
  - 通过蒙特卡洛采样从买家分布中抽取独立批次（batch size \(M\)），构造无偏估计器计算梯度和乘子更新量。对二次项使用双重采样（两个独立批次的乘积）以保持无偏性。
  - 网络参数通过梯度下降优化，价格乘子 \(\lambda_j\) 按 \(\lambda_j \leftarrow \lambda_j + \beta_t \cdot \rho \cdot (\frac{1}{M}\sum_i x_\theta(b_i, g_j) - 1)\) 更新。
- **算法流程**：每个epoch内，先采样M个买家，计算无偏损失估计，反向传播更新网络参数；然后计算市场清仓偏差，更新价格乘子。交替进行直到收敛或达到预设epoch数。

## 3. 实验设计

- **实验场景**：使用合成数据，所有买家与商品由随机向量表示（标准正态分布为默认，也测试均匀分布和指数分布）。效用函数采用CES家族（包括线性、Cobb-Douglas、Leontief特例），参数 \(\alpha\) 设为0.5（默认），并测试1, 0.5, 0, -1。
- **Benchmark与对比方法**：
  - **Naïve**：最简单的基准，所有分配设为1，价格按总预算/总供给设置。
  - **EG**：直接对EG凸规划进行梯度上升，使用软加层保证非负，拉格朗日乘子处理约束。
  - **EG-m**：EG的动量版本（动量系数0.9）。
- **评估指标**：Nash Gap（NG）、VoA（分配违反度）、VoP（价格违反度）以及GPU运行时间。NG是衡量均衡偏离度的主要指标，VoA和VoP衡量约束满足度。
- **实验设置**：买家数量 \(n = 2^{18}, 2^{20}, 2^{22}\)，商品数量 \(m = 5, 10, 20\)。特征维度 \(d=5\)。MarketFCNet训练30个epoch，每个epoch内100次内迭代；EG/EG-m也训练30个epoch，但内迭代次数根据n调整（n>1000时1000次，否则100次），并带早停（NG<1e-3）。

## 4. 资源与算力

- 论文附录C.2明确指出：**所有实验在单张NVIDIA RTX 4090显卡上运行，使用16个CPU或1个GPU**。
- 未明确说明每次实验的总训练时长，但给出了各算法在特定设置下的运行时间（如表1：MarketFCNet训练43.6秒+测试0.096秒）。不同实验配置下的运行时间均有报告（图2、图3）。
- 注意：论文未说明是否使用了多卡并行或整个项目总计算量。

## 5. 实验数量与充分性

- **实验组数**：论文进行了多维度实验：
  - 表1：基本对比实验（n=1,048,576, m=10）。
  - 图2：不同上下文分布（正态、均匀、指数）和不同CES参数α（1, 0.5, 0, -1）下的NG和时间，每组包含MarketFCNet、EG、EG-m三条曲线。
  - 图3：不同市场大小（n=2^18,2^20,2^22; m=5,10,20）共9种组合下的NG和时间。
- **充分性与客观性**：
  - 覆盖了多种效用类型、多种上下文分布、多种市场大小，场景较为全面。
  - 但是，**每组实验似乎只运行了一次，未报告多次重复的统计量（如均值、标准差）**，缺乏误差棒或置信区间。作者在回答栏中承认“未提供误差棒，但因差异显著，认为单次足够”。这在一定程度上削弱了实验的严谨性和可复现性。
  - 对比方法为目前主流的一阶优化方法（EG及动量版本），且进行了超参数调优（学习率、步长等），对比相对公平。

## 6. 论文的主要结论与发现

- MarketFCNet在大规模买家市场（n 达百万级以上）中能够获得与EG/EG-m相近的Nash Gap，但**运行时间显著更低**（表1：FC总耗时约43.7秒，EG耗时197秒，EG-m耗时100秒）。
- 随着市场规模的扩大（n增大、m增大），EG和EG-m的Nash Gap和运行时间均增加，而MarketFCNet的Nash Gap和运行时间几乎保持不变，展现出**良好的可扩展性**。
- 不同上下文分布和不同CES参数下，MarketFCNet均能保持稳定性能，表明其具有**鲁棒性**。
- 提出的Nash Gap度量能够有效量化近似均衡的偏离程度，且满足非负性和零值唯一对应于均衡等良好性质。

## 7. 优点

- **问题创新**：首次提出使用深度学习计算大规模上下文市场均衡，突破了传统方法仅适用于小买家的局限。
- **方法新颖**：利用神经网络参数化分配函数，通过无偏采样实现与买家数量无关的优化复杂度（O(m)），具有理论上的可扩展性。
- **度量贡献**：提出Nash Gap，给出了经济解释，并与欧氏距离、社会剩余等直观度量建立了联系（Proposition 5.6）。
- **实验设计全面**：考虑了多种效用函数、多种分布、多种市场规模，验证了方法的鲁棒性。
- **经济解释清晰**：使用增广拉格朗日法自然得到价格，与均衡的经济学含义一致。

## 8. 不足与局限

- **理论收敛保证缺失**：论文未提供MarketFCNet训练过程收敛到均衡的理论证明（仅经验验证）。
- **实验统计严谨性不足**：未提供多次重复实验的统计量，无法判断结果是否稳定。
- **仅考虑合成数据**：所有实验基于随机生成的上下文，未在真实市场数据上验证，实际泛化能力未知。
- **适用范围有限**：论文仅针对买家数量大的情况，假定商品数量较小（m=5/10/20）。当商品数量也巨大时，方法的复杂度仍可能受限于O(m)项。作者在结论中也承认这是未来工作。
- **未公开代码**：论文称代码需进一步整理后才开源，影响可复现性。
- **假设较强**：假设买家预算和估值是确定的，未考虑随机或不确定情况；仅覆盖CES效用函数族（尽管较广），对非CES效用未验证。
- **Nash Gap需满足约束**：对于不满足市场清仓和价格约束的(x,p)，需先投影再计算NG，且VoA和VoP可能非零，增加评估复杂性。

（完）
