---
title: "Position: Is machine learning good or bad for the natural sciences?"
title_zh: 立场：机器学习对自然科学是好是坏？
authors: "David W Hogg, Soledad Villar"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=rU8o0QQCy0"
tags: ["query:ai-basics"]
score: 4.0
evidence: 讨论机器学习在科学中的本体论和认识论，与AI概念基础相关
tldr: 这篇立场论文指出机器学习的本体论（只存在数据）和认识论（只要预测好）与自然科学的传统哲学冲突，但也分析了ML在因果推断等场景中的价值。对于AI初学者理解ML的哲学基础有一定启发。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-ru8o0qqcy0/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1683, \"height\": 1675, \"label\": \"Figure\"}]"
motivation: 反思ML在自然科学中的哲学冲突。
method: 分析ML本体论和认识论与自然科学方法的矛盾。
result: 指出冲突并识别有价值应用场景。
conclusion: ML在某些科学场景仍有价值，需谨慎应用。
---

## Abstract
Machine learning (ML) methods are having a huge impact across all of the sciences. However, ML has a strong ontology — in which only the data exist — and a strong epistemology — in which a model is considered good if it performs well on held-out training data. These philosophies are in strong conflict with both standard practices and key philosophies in the natural sciences. Here we identify some locations for ML in the natural sciences at which the ontology and epistemology are valuable. For example, when an expressive machine learning model is used in a causal inference to represent the effects of confounders, such as foregrounds, backgrounds, or instrument calibration parameters, the model capacity and loose philosophy of ML can make the results more trustworthy. We also show that there are contexts in which the introduction of ML introduces strong, unwanted statistical biases. For one, when ML models are used to emulate physical (or first-principles) simulations, they amplify confirmation biases. For another, when expressive regressions are used to label datasets, those labels cannot be used in downstream joint or ensemble analyses without taking on uncontrolled biases. The question in the title is being asked of all of the natural sciences; that is, we are calling on the scientific communities to take a step back and consider the role and value of ML in their fields; the (partial) answers we give here come from the particular perspective of physics.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- 该论文是一篇立场论文（Position Paper），旨在反思机器学习（ML）在自然科学中的应用究竟是“好”还是“坏”。
- 研究动机：ML 方法正在深刻影响所有科学领域，但其固有的本体论（ontology，认为只有数据存在）和认识论（epistemology，认为模型的好坏仅由在留出数据上的表现决定）与自然科学的传统哲学（强调理解潜在结构、因果关系和理论统一性）存在根本冲突。
- 核心问题：面对这种哲学冲突，ML 在自然科学中应该在哪些场景下被积极采用，哪些场景下会引入有害偏差？论文呼吁科学界停下来思考 ML 的角色和价值。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- 论文并未提出新的算法，而是采用哲学分析和案例论证的方法：
  - **定义与对比**：明确 ML（宽泛定义：能力随数据量大幅提升的方法，包括线性回归、高斯过程、神经网络等）和自然科学（狭义定义：以理解自然世界为首要目标的学科）的本体论和认识论。
  - **识别“安全区”与“危险区”**：通过逻辑推理和具体实例，指出 ML 在哪些环节（如实时决策、异常检测、干扰建模）是安全的，在哪些环节（如标签迁移、仿真模拟器替代）会导致严重统计偏差。
  - **因果推断视角**：在因果推断中，使用高容量 ML 模型拟合混杂因子（如前景、背景、仪器校准参数）可以使结论更保守、更稳健，因为模型已经“尽一切可能”解释效应，若仍无法解释则强化了因果主张。
  - **偏差分析**：通过一个**玩具数据示例**（附录A）说明回归标签的种群级偏差：个体级估计偏差可能很小，但当大量回归标签被联合使用时，偏差会被放大且无法通过增大样本量消除。

## 3. 实验设计：使用了哪些数据集 / 场景，它的 benchmark 是什么，对比了哪些方法

- 论文并未进行传统意义上的大规模实验，而是：
  - **主要论证**：基于已有文献和科学实践案例（如 Hubble 宇宙膨胀发现、Kepler 行星轨道、AlphaFold、LHC ATLAS 实验、Planck 宇宙微波背景、Rubin LSST 等）。
  - **玩具示例（Appendix A）**：人工生成一个模拟天文光谱数据，包含引导半径 r、年龄 η、高维特征 x 和标签 y。构建了一个三层多层感知器（MLP，隐层大小64/32/16），使用 4096 训练样本、2048 验证样本、10^5 测试样本。
  - **基准（Benchmark）**：验证集上回归估计的个体偏差很小（斜率1、截距0），但测试集上按 r 分箱的平均标签估计出现强烈偏差（30σ 水平与真实关系不符）。
  - **对比**：训练集上的平均关系（无偏但精度低） vs. 测试集上回归标签的平均关系（有偏但精度很高）。解释了为何训练集结果比使用 ML 转移标签后的测试集结果更可靠。

## 4. 资源与算力：如果文中有提到，请总结使用了多少算力（GPU 型号、数量、训练时长等）。若未明确说明，也请指出这一点。

- 论文**未提及任何具体的硬件资源、GPU 型号、训练时长或算力消耗**。玩具示例使用 scikit-learn 实现，属于轻量级计算，未给出性能细节。

## 5. 实验数量与充分性：大概做了多少组实验（如不同数据集、消融实验等），这些实验是否充分、是否客观、公平。

- 论文并未进行多组对照实验或消融实验，仅提供了一个玩具示例（Appendix A）来证明标签迁移导致的种群级偏差。
- 充分性评价：作为一篇立场论文，其主要贡献在于逻辑论证和哲学反思，而非实验验证。玩具示例足以说明核心论点，但实验覆盖范围有限（只有一个人工数据集、一个 MLP 架构）。
- 客观性和公平性：论文作者自称“既是 ML 怀疑者又是 ML 实践者”，立场相对平衡，但未进行系统性基准测试，因此不能被视为充分的实验验证。

## 6. 论文的主要结论与发现

- **主要结论**：ML 在自然科学中“既有益也有害”，答案取决于使用场景。
- **具体发现**：
  1. **有害之处**：
     - **标签迁移偏差**：回归模型产生的标签用于种群级联合分析时，会放大个体级偏差，且无法通过增大样本量或使用验证集消除。
     - **仿真模拟器替代引入确认偏差**：ML 模拟器（emulators）在昂贵的第一性原理模拟不可复现时，会系统性偏向支持已有预期（确认偏差），因为异常结果比预期结果更值得被质疑和重复验证，但重复验证成本高昂且设计不充分。
  2. **有益之处**：
     - 实时操作（如 LHC 触发、LSST 事件分类）。
     - 异常检测（发现稀有天体或设备故障）。
     - 干扰模型（前景、背景、仪器校准）等因果推断场景，高容量 ML 使结论更保守可靠。
- **呼吁**：科学界应认真审视 ML 的角色，不应盲目应用。

## 7. 优点：方法或实验设计上有哪些亮点

- **哲学框架清晰**：首次系统性地将 ML 的本体论/认识论与自然科学的传统哲学进行对比，为跨学科讨论提供了理论工具。
- **偏差机理揭示深刻**：通过简单玩具示例，直观展示了回归标签种群级偏差的严重性（30σ 水平），并指出该偏差与分布偏移无关，即使同分布也会出现。
- **提出安全使用指南**：明确了哪些场景可以安全使用 ML（如干扰建模），哪些应避免（如用回归标签做种群推断）。
- **视角独特**：从物理科学（特别是天体物理）实践出发，结合因果推断观点，认为高容量 ML 在混杂因子建模中具有保守性优势。

## 8. 不足与局限：包括实验覆盖、偏差风险、应用限制等

- **实验覆盖不足**：仅有一个玩具数据示例，未在真实科学数据集上验证（如天文谱线、粒子物理数据分析），也未测试不同 ML 架构（如神经网络、随机森林、高斯过程）对偏差影响的差异。
- **缺乏量化分析**：对确认偏差的论述停留在逻辑层面，没有量化模拟器引入偏差的程度，也没有提出具体的校正方法。
- **定义争议**：论文采用宽泛 ML 定义，可能引起部分研究者异议（例如线性回归是否属于 ML）。
- **应用限制**：结论主要基于物理科学（尤其是宇宙学和粒子物理），对生物学、化学等领域的适用性需要进一步检验。论文承认“答案来自物理学视角”。
- **未讨论的维度**：未涉及深度学习可解释性（可解释 ML）是否可能缓解某些问题；未讨论联邦学习、隐私保护等新兴范式的影响。

（完）
