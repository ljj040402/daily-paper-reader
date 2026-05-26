---
title: "DeepHalo: A Neural Choice Model with Controllable Context Effects"
title_zh: DeepHalo：具有可控上下文效应的神经选择模型
authors: "Shuhan Zhang, Zhi Wang, Rui Gao, Shuang Li"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=x9XepNPGJ5"
tags: ["query:ai"]
score: 4.0
evidence: 神经选择模型用于人类决策建模，与人工智能对齐相关
tldr: 该论文提出DeepHalo神经选择模型，通过可控上下文效应捕捉人类偏好中的光环效应，在特征化设置下保持可解释性。实验证明该模型能准确预测选择行为，为推荐系统和人类-AI对齐提供了新工具。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-x9xepnpgj5/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 619, \"height\": 541, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-x9xepnpgj5/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 752, \"height\": 622, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-x9xepnpgj5/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1441, \"height\": 626, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-x9xepnpgj5/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1086, \"height\": 291, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-x9xepnpgj5/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1347, \"height\": 621, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-x9xepnpgj5/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1451, \"height\": 222, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-x9xepnpgj5/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 987, \"height\": 511, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-x9xepnpgj5/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 918, \"height\": 281, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-x9xepnpgj5/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 985, \"height\": 315, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-x9xepnpgj5/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1404, \"height\": 376, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-x9xepnpgj5/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1402, \"height\": 373, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-x9xepnpgj5/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 544, \"height\": 413, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-x9xepnpgj5/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1030, \"height\": 348, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-x9xepnpgj5/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1182, \"height\": 456, \"label\": \"Table\"}]"
motivation: 经典模型忽略上下文依赖的偏好，现有特征化模型限制交互结构或缺乏可解释性。
method: 设计可控制上下文效应的神经网络结构，分层建模选择集内选项间的交互。
result: 在多个真实数据集上，DeepHalo预测精度优于现有模型，同时保持可解释性。
conclusion: 该模型有效平衡了上下文效应的捕捉与模型可解释性。
---

## Abstract
Modeling human decision-making is central to applications such as recommendation, preference learning, and human-AI alignment. While many classic models assume context-independent choice behavior, a large body of behavioral research shows that preferences are often influenced by the composition of the choice set itself---a phenomenon known as the context effect or Halo effect. These effects can manifest as pairwise (first-order) or even higher-order interactions among the available alternatives.
Recent models that attempt to capture such effects either focus on the featureless setting or, in the feature-based setting, rely on restrictive interaction structures or entangle interactions across all orders, which limits interpretability. 
In this work, we propose DeepHalo, a neural modeling framework that incorporates features while enabling explicit control over interaction order and principled interpretation of context effects.
Our model enables systematic identification of interaction effects by order and serves as a universal approximator of context-dependent choice functions when specialized to a featureless setting.
Experiments on synthetic and real-world datasets demonstrate strong predictive performance while providing greater transparency into the drivers of choice.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：人类决策行为常常受到选择集构成的上下文效应（又称“光环效应”）影响，例如诱饵效应、折衷效应和相似效应。传统的随机效用模型（如多项Logit）假设选项效用与上下文无关，违反了“无关选项独立性”假设，无法捕捉这些现象。现有捕捉上下文效应的模型要么在没有特征的一热编码设置下工作，要么在基于特征的设置中依赖限制性的交互结构（如仅限一阶交互）或将所有阶交互混杂在一起，导致可解释性差。
- **整体目标**：提出一个既能表达复杂高阶交互（在特征化设置下），又能系统解耦和解释这些效应的神经网络选择模型，实现表达力与透明度的平衡。

## 2. 论文提出的方法论

### 核心思想
- 将效用分解为可解释的、基于特征的组件：基础效用、成对交互和高阶效应，并利用排列等变性质。
- 设计递归神经网络架构，每一层显式增加一个交互阶数，通过残差连接保留低阶效应，从而实现对交互阶数的显式控制。

### 关键技术细节
- **效用分解**：基于Batsell & Polking的包含-排除分解，将效用 \( u_j(S) \) 表示为基效用加上各阶子集T的贡献之和：
  \[ u_j(S) = v_j(\emptyset) + \sum_{j_1} v_j(\{j_1\}) + \sum_{j_1,j_2} v_j(\{j_1,j_2\}) + \cdots + v_j(S\setminus\{j\}) \]
  其中 \( v_j(T) \) 是排列等变的。
- **神经网络参数化**：
  - 使用共享的非线性嵌入函数 \(\chi\) 将每个选项映射到嵌入空间。
  - **第一层（一阶交互）**：聚合上下文的平均嵌入，与每个选项的基嵌入通过头特定非线性变换 \(\phi_{1h}\) 结合，生成 \(z_j^1\)，最终效用 \(\beta^T z_j^1\)。
  - **更高层（高阶交互）**：递归定义 \( \bar{Z}^l = \frac{1}{|S|}\sum_k W^l z_k^{l-1} \) 和 \( z_j^l = z_j^{l-1} + \frac{1}{H}\sum_h \bar{Z}_h^l \cdot \phi_{lh}(z_j^0) \)，其中 \(H\) 为交互头数。
  - 残差连接保证每一层增量式增加交互阶数，第 \(l\) 层捕获最高 \(l\) 阶交互。
- **特征化设置**：利用多项式激活和聚合，可在 \(\lceil \log_2(J-2) \rceil\) 层内捕获所有阶交互（\(J\) 为选项数）。
- **可识别性**：通过定义相对上下文效应 \( \alpha_{jk}(T) = [v_j(T)+v_j(T\cup\{k\})] - [v_k(T)+v_k(T\cup\{j\})] \)，从模型预测中恢复可识别的效应量。

### 算法流程（文字描述）
1. 对每个选择集，将特征矩阵填充到固定大小 \(J\)，并应用二值掩码处理空位。
2. 通过共享嵌入网络 \(\chi\) 获取每个选项的基嵌入 \(z_j^0\)。
3. 对层 \(l=1..L\)：
   - 计算上下文的加权聚合 \(\bar{Z}^l\)（使用参数 \(W^l\)）。
   - 对于每个选项 \(j\)，通过残差连接和头特定调制更新表示 \(z_j^l\)。
4. 最终效用 \( u_j = \beta^T z_j^L \)，通过 softmax 得到选择概率。

## 3. 实验设计

### 使用的数据集/场景
- **无特征数据集**：
  - 假设饮料市场份额数据（4种产品），用于可视化相对光环效应。
  - 合成数据：20个选项，固定选择集大小15，均匀采样选择概率向量，生成124万样本。
  - 真实数据：Hotel（5家酒店，最多11个备选项，1845训练/465测试），SFOwork（6种出行模式，5029观测），SFOshop（8种模式，3157观测），均按8:1:1划分。
- **有特征数据集**：
  - LPMC（伦敦出行调查，81086观测，8个选项特征+17个共享特征，4种模式）。
  - Expedia（酒店选择，275609交易，最多38家酒店，35个选项特征+56个共享特征）。

### 基准方法
- 无特征设置：多项Logit（MNL）、MLP、上下文MNL（CMNL）、混合MNL、FATE、TCNet等。
- 有特征设置：MNL、MLP、TasteNet、RUMnet、ResLogit、DLCL、FateNet、TCNet。

### 对比的指标
- 负对数似然（NLL）、部分实验中还报告了训练RMSE和准确率。

## 4. 资源与算力

- 论文中明确提到：所有无特征实验（包括假设数据和合成数据）在单个 Google Colab T4 GPU 上进行，使用 Adam 优化器。
- 有特征实验同样在单个 Google Colab T4 GPU 上进行。
- **未明确**说明具体训练时长、GPU 数量（仅单卡）、内存消耗等详细算力信息。

## 5. 实验数量与充分性

- **实验组数**：进行了多组实验，涵盖无特征（假设、合成、3个真实数据集）和有特征（2个真实数据集）共至少10个实验配置。
- **充分性**：
  - 在无特征设置中，展示了模型深度与表达力的关系（固定参数预算下深度对比）。
  - 在有特征设置中，与7种以上基线对比，报告了多次运行的平均值和标准差（5次重复，见附录表7、8）。
  - 进行了数据效率实验（SFOshop上从10%~100%子采样）和训练时间比较。
  - **消融实验**：对比了DeepHalo（二阶约束）与MLP+Trunc（后验截断到k阶），验证显式控制交互阶数的有效性。
- **公平性**：所有模型使用相同的数据划分，超参数通过验证集调整，参数预算相近（如附录表4）。结果报告了均值和标准差，基本客观。

## 6. 论文的主要结论与发现

- DeepHalo 在所有无特征和有特征数据集上取得了最低或接近最优的 NLL，优于现有上下文依赖模型。
- 显式控制交互阶数（如二阶）在真实数据上几乎达到与全阶模型相同的效果，表明人类选择行为主要受低阶交互驱动。
- 深度（层数）是捕获高阶交互的关键因素：在固定参数预算下，增加深度显著降低训练RMSE，而仅增加宽度效果有限。
- 模型可解释性：通过恢复相对光环效应热图，清晰展示了如“百事优于可口”等偏好，验证了模型能忠实反映已知行为规则。
- 在数据稀疏时，DeepHalo 仍能保持较好的泛化性能。

## 7. 优点

- **方法论**：提出一种具备可控交互阶数的神经选择模型，兼具深度学习的表达力和基于分解的可解释性。
- **结构设计**：残差递归结构使得每一层明确对应一个交互阶数，易于理解和调试。
- **理论贡献**：证明了所提架构在无特征设置下可作为上下文依赖选择函数的通用逼近器，并给出多项式激活下所需层数上界。
- **实验覆盖**：涵盖多种场景（假设、合成、真实），且与多个基线公平比较，结果具有说服力。
- **开源**：提供了代码仓库，便于复现。

## 8. 不足与局限

- **计算效率**：随着层数增加，模型训练时间明显长于某些简单基线（如MLP,FATE），在附录表10中训练时间约202秒，高于多数对比方法。大规模应用可能需要更多优化。
- **可解释性**：虽然交互阶数可控，但每层的具体内部表示（如 \(z_j^l\)）仍然是非线性的，完全理解具体如何组合特征仍不直观。
- **实验“公平性”的细微局限**：在无特征实验中，合成数据直接采样概率向量，未从显式高维光环效应生成，可能与真实机制有差异；但作者论证任何选择数据均可由光环效应表示。
- **应用限制**：当前设计针对静态选择集（固定最大大小 \(J\)），对于动态变长序列未做专门处理；对极大选项集（如电商成千上万产品）的可扩展性未评估。
- **缺乏用户异质性**：模型输出是总体选择概率，未建模个体差异（除非通过多“头”隐式部分捕捉）。
- **未讨论负的社会影响**：尽管论文提及透明决策支持系统，但未讨论模型可能被用于操纵用户（如利用光环效应）的风险。

（完）
