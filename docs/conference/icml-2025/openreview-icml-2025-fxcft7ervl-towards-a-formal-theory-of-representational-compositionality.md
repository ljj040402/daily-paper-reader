---
title: Towards a Formal Theory of Representational Compositionality
title_zh: 迈向表示组合性的形式化理论
authors: "Eric Elmoznino, Thomas Jiralerspong, Yoshua Bengio, Guillaume Lajoie"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=fXCfT7ErvL"
tags: ["query:ai"]
score: 8.0
evidence: ICML 2025 AI基础理论研究，定义了表示组合性
tldr: 该论文提出了一个基于算法信息理论的表示组合性形式定义，该定义简单、定量且直观：组合性表示既表达丰富又可描述为部分的简单函数。通过在真实和合成数据集上的验证，该定义有效衡量了表示的组合程度，为理解神经网络泛化和智能提供了理论基础。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-fxcft7ervl/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1767, \"height\": 594, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fxcft7ervl/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1764, \"height\": 676, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fxcft7ervl/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 574, \"height\": 406, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fxcft7ervl/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 813, \"height\": 431, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fxcft7ervl/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1504, \"height\": 427, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fxcft7ervl/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1607, \"height\": 921, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fxcft7ervl/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 785, \"height\": 317, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fxcft7ervl/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1756, \"height\": 471, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-fxcft7ervl/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1414, \"height\": 325, \"label\": \"Table\"}]"
motivation: 组合性被认为是智能的基础，但缺乏形式化定义。
method: 基于算法信息理论定义表示组合性，要求表示既表达丰富又可由部分的简单函数描述。
result: 在真实和合成数据上验证了定义的合理性和有效性。
conclusion: 该形式化定义有助于量化和理解神经网络的组合泛化能力。
---

## Abstract
Compositionality is believed to be fundamental to intelligence. In humans, it underlies the structure of thought and language. In AI, it enables a powerful form of out-of-distribution generalization, in which a model systematically adapts to novel combinations of known concepts. However, while we have strong intuitions about what compositionality is, we lack satisfying formal definitions for it. Here, we propose such a definition called representational compositionality that is conceptually simple, quantitative, and grounded in algorithmic information theory. Intuitively, representational compositionality states that a compositional representation is both expressive and describable as a simple function of parts. We validate our definition on both real and synthetic data, and show how it unifies disparate intuitions from across the literature in both AI and cognitive science. We hope that our definition can inspire the design of novel, theoretically-driven models that better capture the mechanisms of compositional thought. We make our code available at https://github.com/EricElmoznino/complexity_compositionality.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：组合性（compositionality）被认为是人类智能和人工智能（AI）的关键特征，它能支撑强大的**分布外泛化**能力，使模型能够系统性地适应已知概念的新组合。然而，学界对组合性缺乏令人满意的形式化定义——现有的定义（如“复杂表达式的意义由其结构及成分意义决定”）存在模糊、二元化、无法定量测量等缺陷。
- **研究动机**：论文旨在提出一个**概念简单、可定量计算、基于算法信息论**的组合性形式定义，从而统一文献中（AI与认知科学）关于组合性的各种直觉，为设计更具组合性机制的模型提供理论基础。

### 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程（用文字说明即可）
- **核心思想**：组合性表示应同时满足：**表达力强**（表示能够编码丰富的信息）和**可描述为成分的简单函数**（即通过压缩的角度来看，表示的最短程序由一个生成句子 \(W\) 的简单语言 \(p_w\) 和一个从句子映射到高维向量表示的简单语义函数 \(f\) 组成）。
- **关键技术细节**：
  - 将表示 \(Z \in \mathbb{R}^{N \times D}\) 的**Kolmogorov复杂度**分解为四个部分：
    \[
    K(Z) = \min_{p_w, W, f} \left[ K(p_w) + K(W | p_w) + K(f) + K(Z | W, f) \right]
    \]
    - \(K(p_w)\)：描述语言（句子先验分布）的复杂度；
    - \(K(W | p_w)\)：在语言下描述句子的复杂度（与负对数似然相关）；
    - \(K(f)\)：描述语义映射函数（离散句子→连续向量）的复杂度；
    - \(K(Z | W, f)\)：重建误差的复杂度（连续部分无法被离散句子完美刻画的部分）。
  - **组合性定义**：
    \[
    C(Z) = \frac{K(Z)}{K(Z|W)} = \frac{K(Z)}{K(f) + K(Z|W, f)}
    \]
    即：表示的表达力（分子）相对于它作为部分简单函数可被压缩的程度（分母）的比值。比值越高，表示越具组合性。
  - 对于给定外部语言系统的场景，定义**语言系统组合性** \(C_L(Z)\)，此时 \(W^L\) 固定，仅优化 \(f^L\)。
- **算法流程**（文字说明）：
  1. 假设表示存在最简程序：先使用离散符号句子 \(W\) 描述表示，再通过简单语义函数 \(f\) 将句子映射回连续表示，并用残差编码补偿误差。
  2. 通过优化一个**离散自编码器**（包含编码器、自回归先验 \(p_w\)、解码器 \(f\)）来近似最小化上述复杂度之和；训练损失为负对数似然：\(\sum_{z \in Z} [-\log p_w(e(z)) - \log \mathcal{N}(z; f(e(z)))]\)。
  3. 使用**序贯编码（prequential coding）** 来估计模型复杂度 \(K(p_w)\) 和 \(K(f)\)，其核心是逐步增加训练数据、记录每步模型对下一个数据点的预测误差（负对数似然），最终总编码长度之渐近等于 \(K(D, \theta)\)，进而分离出模型复杂度。
  4. 组合性 \(C(Z)\) 或 \(C_L(Z)\) 即可基于这些估计值计算。

### 3. 实验设计：使用了哪些数据集 / 场景，它的 benchmark 是什么，对比了哪些方法
- **合成数据实验**（验证 \(C(Z)\) 性质）：
  - **查找表（Lookup table）**：按不同句子长度、词汇量大小、表示维度和解纠缠因子生成表示；精确计算所有复杂度项。
  - **上下文无关文法**：生成具有层级结构的表示，改变文法宽度和深度。
  - **基准对比**：与**拓扑相似性（topological similarity）** 作对比（即句子空间与表示空间中成对距离的 Pearson 相关）。
- **真实数据实验**（验证 \(C_L(Z)\)）：
  - **涌现语言**：多智能体参考游戏中智能体沟通的语言系统（Li & Bowling, 2019；Ren et al., 2020）。比较**有无迭代学习（iterated learning）** 两种条件。对象为64种符号物体，句子长度2、词汇量8。
  - **自然语言**：从COCO图像描述数据集获取英语句子（414,010条），用多语言模型翻译为法语、西班牙语、德语、日语；用多语言句子嵌入模型（Reimers & Gurevych, 2020）编码为向量表示 \(Z\) 作为意义的代理。比较各语言的相对组合性。
- **未见有其他对比方法**（仅与拓扑相似性对比；未与现有其他组合性度量如线性语义等作系统比较）。

### 4. 资源与算力：如果文中有提到，请总结使用了多少算力（GPU 型号、数量、训练时长等）。若未明确说明，也请指出这一点。
- **文中未明确说明**使用的 GPU 型号、数量或训练时长。所有实验（涌现语言、自然语言）均使用标准深度学习框架，但具体硬件细节缺失。序贯编码需要迭代训练模型（每次增加数据块），但未报告实际耗时。

### 5. 实验数量与充分性：大概做了多少组实验（如不同数据集、消融实验等），这些实验是否充分、是否客观、公平
- **实验数量**：
  - 合成数据：查找表实验包括对句子长度、词汇量、表示维度、解纠缠因子的各自扫描，每种设置10个随机种子；文法实验扫描宽度和深度，同样10个种子。合计约几十组。
  - 涌现语言：有无迭代学习各5个种子，共10组。
  - 自然语言：5种语言，3个种子，共15组。
- **充分性与客观性**：
  - 合成数据实验能够精确计算理论值，验证了定义与直觉的一致性（如句子越长组合性越高、词汇量过大或过小组合性降低、解缠程度越低组合性越高等）。这些结果充分说明了定义的合理性。
  - 涌现语言实验复现了前人结果，且将绝对数值解释为“无迭代学习时组合性为1（极端任意映射）”，提供了拓扑相似性无法提供的解释力。
  - 自然语言实验表明各语言组合性相近（日语略高），而拓扑相似性得出反常结果（日语奇异大负值），显示新定义更符合语言学直觉。
  - 不足：未进行更广泛的模型/任务验证（例如不同架构的深层神经网络表示）；未对估计方法作系统消融；自然语言实验中未估计分子 \(K(Z)\)，假设所有语言表达力相等，该假设可能不完全成立。

### 6. 论文的主要结论与发现
- **主要结论**：提出了一种基于算法信息论的组合性形式定义——**表示组合性**（\(C(Z)\)），它统一了认知科学和AI中关于组合性的多种直觉（如系统性、结构保持性、模块性、等变性等）。
- **关键发现**：
  - 组合性可视为**表达力**与**可压缩性**之间的博弈，这与认知科学中文化进化理论（Kirby）一致。
  - 在合成数据中，定义量化结果与所有测试的直觉变量高度一致（句子长度、词汇量、维度、解缠、文法宽度/深度）。
  - 在涌现语言中，迭代学习确实提高了组合性；新定义提供了**绝对可解释数量**（无迭代学习时为1），优于仅能提供相对排序的拓扑相似性。
  - 在自然语言中，不同语言的组合性大致相等，与“所有语言同等复杂”的语言学观点吻合；而拓扑相似性给出违反直觉的对比。

### 7. 优点：方法或实验设计上有哪些亮点
- **理论创新**：首次将组合性与Kolmogorov复杂度和压缩联系起来，提供了一个既定量又直观的定义，不需要预设符号或外部标注的“部分”，而是通过压缩最优性自发确定组成元素。
- **统一性**：能够涵盖并解释多种先前的直觉（系统性、模块性、结构保持、等变性、解缠），将它们视为组合性在不同形式下的体现。
- **可操作框架**：给出了利用离散自编码器和序贯编码估计 \(C(Z)\) 的实用路线图（尽管 \(C(Z)\) 的完全实现留作未来工作，但对固定语言系统 \(C_L(Z)\) 已可直接使用）。
- **实验设计巧妙**：合成数据生成方式允许精确计算真值复杂度，从而验证定义；真实实验（涌现语言、自然语言）展示了定义在实践中的有用性和解释力，特别是与拓扑相似性对比凸显了优势。

### 8. 不足与局限：包括实验覆盖、偏差风险、应用限制等
- **计算复杂性**：\(C(Z)\) 的估计需要在表示空间上训练离散自编码器并执行序贯编码，这在大型真实表示（例如全连接层激活、大脑记录）上仍面临稳定性和效率挑战，论文仅给出了路线图而未实现完整的 \(C(Z)\) 估计。
- **估计偏差**：估计方法（离散自编码器+序贯编码）对模型架构、超参数、数据量敏感，可能存在较大波动；线性假设更强的现有方法（如线性语义）可能更稳定。
- **实验覆盖有限**：
  - 未测试在深度神经网络（如Transformer、CNN）中间表示的组合性，也未直接验证与组合泛化的关联（论文仅作为未来工作假设）。
  - 自然语言实验中，翻译质量、句子嵌入的质量对结果有潜在影响，且未控制词汇差异和语域。
  - 未与除拓扑相似性外的其他组合性度量（如线性重建误差、函数复杂度正则化方法）进行系统对比。
- **连续部分的情况**：定义局限于离散部分，未考虑可能的连续部分组合性，这可能忽略一些连续的表示结构。
- **理论假设**：程序形式假设（图1）可能不适用于某些没有符号结构的表示，导致估计的复杂度可能过高，但论文认为这恰能检测非组合性。
- **未讨论可解释性**：虽然定义可能在理论上支持组合泛化，但实际应用中的可解释性和因果解释仍待探讨。

（完）
