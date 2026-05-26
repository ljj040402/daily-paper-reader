---
title: Bayesian Inference for Correlated Human Experts and Classifiers
title_zh: 相关人类专家和分类器的贝叶斯推断
authors: "Markelle Kelly, Alex James Boyd, Sam Showalter, Mark Steyvers, Padhraic Smyth"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=sw2pUzbTf1"
tags: ["query:ai"]
score: 6.0
evidence: ICML 2025关于结合人类专家的机器学习论文
tldr: 该论文提出一个通用贝叶斯框架，对相关的人类专家和分类器进行联合建模。通过共享潜在表示捕捉专家相关性，利用仿真推断决定是否需要额外专家查询，并推断未观察到的专家标签。在医疗分类和CIFAR-10H等任务上，显著降低了查询成本同时保持预测精度。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-sw2puzbtf1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 680, \"height\": 2151, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-sw2puzbtf1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 690, \"height\": 505, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-sw2puzbtf1/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 690, \"height\": 524, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-sw2puzbtf1/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 639, \"height\": 524, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-sw2puzbtf1/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 868, \"height\": 988, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-sw2puzbtf1/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 870, \"height\": 602, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-sw2puzbtf1/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 825, \"height\": 221, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-sw2puzbtf1/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 836, \"height\": 174, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-sw2puzbtf1/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 346, \"height\": 337, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-sw2puzbtf1/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 970, \"height\": 254, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-sw2puzbtf1/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 798, \"height\": 252, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-sw2puzbtf1/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 794, \"height\": 254, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-sw2puzbtf1/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 817, \"height\": 253, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-sw2puzbtf1/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 811, \"height\": 253, \"label\": \"Table\"}]"
motivation: 在结合模型和人类专家时，如何高效查询专家并处理相关性。
method: 构建贝叶斯模型，通过联合潜在表示建模专家相关性，使用仿真推断。
result: 在医疗和视觉任务上减少专家查询次数，保持预测性能。
conclusion: 该框架有效降低了人机协作中的标注成本。
---

## Abstract
Applications of machine learning often involve making predictions based on both model outputs and the opinions of human experts. In this context, we investigate the problem of querying experts for class label predictions, using as few human queries as possible, and leveraging the class probability estimates of pre-trained classifiers. We develop a general Bayesian framework for this problem, modeling expert correlation via a joint latent representation, enabling simulation-based inference about the utility of additional expert queries, as well as inference of posterior distributions over unobserved expert labels. We apply our approach to two real-world medical classification problems, as well as to CIFAR-10H and ImageNet-16H, demonstrating substantial reductions relative to baselines in the cost of querying human experts while maintaining high prediction accuracy.

---

## 论文详细总结（自动生成）

# 论文中文总结

## 1. 核心问题与整体含义（研究动机和背景）

在许多现实应用中，机器学习系统需要与人类专家协作，例如放射科医生对X光片进行分类。理想情况下，每次输入都查询所有专家并聚合其投票（如多数表决）作为“真实标签”，但这样做成本过高。因此，本文研究如何利用预训练分类器的输出，在仅查询少量专家的情况下，准确预测一组专家对每个样本的集体标签（如多数共识）。核心目标是**最小化查询人类专家的成本，同时保持对专家共识的预测精度**。该问题不同于传统的人机互补或学习去委派，而是将专家投票本身作为预测目标，而非某个独立的真实标签。

## 2. 方法论

### 核心思想
构建一个层次贝叶斯模型，将人类专家和分类器视为“智能体”，通过一个联合潜在表示（logit空间）捕捉它们之间的相关性。利用已观测的专家投票和分类器概率，推断未观测专家的投票，并基于信息增益决定下一步查询哪个专家。

### 关键技术细节
- **模型结构（图1）**：每个样本 \(x\) 下，每个专家 \(i\) 的投票 \(y_i\) 服从以潜在概率 \(\theta_i\) 为参数的多项分布。\(\theta_i\) 经过 logistic 正态变换得到 logits \(z_i\)。所有智能体的 \(z_i\) 联合服从多元正态分布 \(N(\mu, \Sigma)\)，其中 \(\mu\) 和 \(\Sigma\) 有先验（正态、半正态 + LKJ 相关矩阵）。引入温度参数 \(\tau\) 调整 softmax 的尖锐程度。
- **条件模拟（算法1）**：给定观测到的模型 logits \(z_M\) 和部分专家投票 \(y_O\)，从后验中采样 \(\mu, \Sigma, \tau\)，进而采样未观测专家的 logits 和投票，加权计算共识标签的后验分布。
- **主动查询策略（算法2）**：对剩余每个未查询专家，假设其可能的投票结果，计算该假设下共识后验的期望熵，选择使期望熵最小的专家进行下一轮查询。当模型估计的共识预测误差低于阈值 \(e\) 时停止查询。
- **在线学习**：模型在样本序列上逐个处理，每若干样本后重新进行 MCMC 采样更新后验参数，实现探索与利用的平衡。

## 3. 实验设计

### 数据集与场景
使用了四个真实或模拟数据集：
- **ChestX-Ray**（真实，二分类，5位放射科专家，810张X光片）
- **Chaoyang**（真实，四分类，3位病理学家，2139张结肠镜图像）
- **CIFAR-10H**（模拟专家，三分类，3位合成专家，来自CIFAR-10测试集）
- **ImageNet-16H**（模拟专家，三分类，3位合成专家，含不同噪声水平）

这些数据集在专家数量、类别数、专家间差异、难度上各不相同，覆盖了不同场景。

### 对比方法（Baselines）
1. **INFEXP + ε-greedy querying**：基于 Showalter et al. (2024) 的 INFEXP 方法，但增加了 ε-greedy 选择专家（根据历史准确率），用于选择查询哪个专家。
2. **Confusion matrices + calibration**：扩展自 Kerrigan et al. (2021) 的混淆矩阵+校准方法，为每个专家学习混淆矩阵，并用算法2选择查询专家。

两种 baseline 均被调整为预测专家共识，并以与本文一致的方式定义误差。

### 评估指标
- **误差 vs. 平均查询次数曲线**：通过改变误差阈值 \(e\) 生成不同查询成本下的错误率。
- **额外指标**：校准误差（ECE）、探索-利用行为、对聚合函数（任意专家投票为1 / 全票一致）的支持。

## 4. 资源与算力

论文中在 Appendix D 提到：“Experiments were run on an NVIDIA GeForce 2080ti GPU over the course of several days.” 未说明 GPU 数量（可能是单卡），训练总时长约为数天。MCMC 采样使用了 3 条链，每条 1500 次 warm-up + 2000 次 posterior 样本。

## 5. 实验数量与充分性

- **核心实验**：在四个数据集上，每个方法生成误差-成本曲线，每个曲线由 12 次不同随机顺序的 250 样本运行平均得到（对于 ChestX-Ray 和 Chaoyang，由于样本数较少，通过 shuffling 创建 12 组不同顺序的 250 样本集）。因此共 12 runs × 4 数据集 = 48 次运行。
- **消融与扩展**：
  - 校准分析（ECE 表格，表1），4个数据集 × 3个阈值 = 12 个值。
  - 探索-利用分析（表2，前50 vs 后50 样本查询数）。
  - 分布转移实验（ImageNet-16H 噪声变化，48 个重复运行，图4）。
  - 替代聚合函数实验（ChestX-Ray 上检验 “至少一个专家预测为1” 和 “全部一致” 两种函数，图5）。
- 未进行传统意义上的消融实验（如移除温度参数、不同先验等），但提供了对模型行为的深入分析。

**充分性评价**：实验覆盖了多种类型的数据集（真实医疗、模拟视觉）、多个 baseline、多个额外分析，结果具有统计依据（12 次重复）。未进行大规模超参数搜索或更全面的消融，但对于一篇方法论文而言已较充分。比较公平：baseline 均按照原文描述适配到本任务，且使用了同样的查询选择算法（算法2）进行对比。

## 6. 主要结论与发现

1. 本文方法在**所有四个数据集上均能达到 0% 误差**，且所需的平均专家查询次数低于两种 baseline。
2. 在医疗数据集（ChestX-Ray、Chaoyang）上，本文方法以更少查询达到完美共识预测；在 CIFAR-10H 和 ImageNet-16H 上同样表现优异。
3. 模型的不确定性估计校良好（ECE 通常低于 1%），使得通过误差阈值直接控制实际误差成为可行策略。
4. 模型自然地平衡了探索与利用：初期查询较多，后期减少；在分布发生转移时能迅速增加查询以维持 0% 误差。
5. 该方法支持任意聚合函数（如“任意专家投阳性”、“全体一致”），并展示了不同的成本-误差曲线。

## 7. 优点

- **框架通用性强**：可处理多个专家、多个分类器、任意聚合函数，且专家可识别、可相关。
- **主动查询策略**：基于信息增益选择最有益的专家，而非随机或固定顺序，有效减少查询。
- **在线适应能力**：通过后验更新和滑动窗口，能应对数据分布变化。
- **校准良好**：使得预先设置误差阈值具有实际控制意义。
- **实验设计合理**：覆盖真实和模拟数据，对比方法经过适配，重复次数足够。

## 8. 不足与局限

- **计算开销**：MCMC 采样在每轮更新时需要大量迭代（1500 warm-up + 2000 posterior），虽然更新频率降低，但在实时场景中可能仍不够高效。
- **类别和智能体数量扩展性**：协方差矩阵大小随 \(K \times (M+H)\) 增长，对更多类别或更多专家（例如数十个）可能难以直接应用。论文明确指出需要低秩近似或结构化先验作为未来工作。
- **实验仅限图像分类**：未在文本、表格等其他模态上验证，结论的通用性有待检验。
- **baseline 局限性**：两个 baseline 中，混淆矩阵方法从未达到 0% 误差，INFEXP 在模拟数据集上也未达到 0%，可能并非最强竞争对手；但论文没有提供更多最新方法。
- **未对查询成本变化建模**：假设所有专家查询成本相同，而真实场景中不同专家可能有不同成本。
- **依赖“专家共识即为目标”**：如果专家本身存在系统性偏见或错误，预测其共识可能传播偏见。论文在 Impact Statement 中也提到了这一点。

（完）
