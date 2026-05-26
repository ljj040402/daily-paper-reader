---
title: "Active Measurement: Efficient Estimation at Scale"
title_zh: 主动测量：大规模高效估计
authors: "Max Hamilton, Jinlin Lai, Wenlong Zhao, Subhransu Maji, Daniel Sheldon"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=nFc38gSYze"
tags: ["query:ai"]
score: 5.0
evidence: AI用于科学测量
tldr: 该论文提出主动测量框架，将AI模型与人类标注相结合：AI预测后通过重要性采样选择样本由人工验证，不断更新模型并得到无偏估计。即使AI模型不完美也能提供精确估计，极大减少人力。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-nfc38gsyze/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1375, \"height\": 476, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nfc38gsyze/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 385, \"height\": 278, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nfc38gsyze/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1452, \"height\": 830, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nfc38gsyze/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 636, \"height\": 289, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nfc38gsyze/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 782, \"height\": 300, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nfc38gsyze/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 632, \"height\": 273, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nfc38gsyze/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 753, \"height\": 256, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nfc38gsyze/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 991, \"height\": 632, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nfc38gsyze/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1262, \"height\": 414, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nfc38gsyze/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1430, \"height\": 486, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nfc38gsyze/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1122, \"height\": 451, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nfc38gsyze/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1449, \"height\": 345, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nfc38gsyze/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1346, \"height\": 464, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nfc38gsyze/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1463, \"height\": 1953, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nfc38gsyze/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1105, \"height\": 2251, \"label\": \"Figure\"}]"
motivation: 当前AI科学发现工作流缺乏精度和统计保证，需要人类在环的高效方法。
method: 使用AI预测测量值，然后通过重要性采样选择样本进行人工标注，不断改进AI模型并更新无偏估计。
result: 推导了新颖估计器和权重方案，实验表明在AI模型准确时只需极少人工，不准确时也能保证估计质量。
conclusion: 主动测量为AI驱动的科学测量提供了兼具效率和统计严谨性的通用框架。
---

## Abstract
AI has the potential to transform scientific discovery by analyzing vast datasets with little human effort. However, current workflows often do not provide the accuracy or statistical guarantees that are needed. We introduce \emph{active measurement}, a human-in-the-loop AI framework for scientific measurement. An AI model is used to predict measurements for individual units, which are then sampled for human labeling using importance sampling. With each new set of human labels, the AI model is improved and an unbiased Monte Carlo estimate of the total measurement is refined. Active measurement can provide precise estimates even with an imperfect AI model, and requires little human effort when the AI model is very accurate. We derive novel estimators, weighting schemes, and confidence intervals, and show that active measurement reduces estimation error compared to alternatives in several measurement tasks.

---

## 论文详细总结（自动生成）

# 论文中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **核心问题**：当前AI在科学发现中分析海量数据时，缺乏必要的精度和统计保证。传统工作流要么完全依赖AI模型（可能偏差大、错误率高），要么要求大量人工标注来验证模型，效率低且难以获得可靠的科学测量结果。
- **整体含义**：论文提出了一种**人机协作的主动测量框架**，通过迭代地利用AI预测引导人工标注，并利用标注结果同时改进AI模型和更新无偏蒙特卡洛估计，从而在有限人工代价下实现高精度、有统计保证的科学测量。

## 2. 论文提出的方法论
- **核心思想**：将AI模型预测作为重要性采样（Importance Sampling）的提议分布，选择性地对未标注单元进行人工标注；新标注的单元用于：（1）更新无偏的总量估计；（2）改进AI模型（微调探测器）以优化后续提议分布。整个过程迭代进行，直到误差足够低。
- **关键技术细节**：
  - **基本估计器**：  
    \[
    \hat{F}_t = F(D_t) + \frac{f(s_t)}{q_t(s_t)},\quad s_t \sim q_t
    \]  
    其中 \(D_t\) 是已标注单元集合，\(q_t\) 是以AI预测值为比例的提议分布，该估计器无偏。
  - **权重方案**：提出组合权重（COMB） \(\alpha_\tau^{\text{COMB}} = w_\tau/\sqrt{\tau}\)（其中 \(w_\tau=1/((N-\tau)(N-\tau+1))\)），兼顾早期模型适应和后期样本空间缩减；还引入基于估计条件方差的逆方差加权（INV），进一步提升效率。
  - **方差估计与置信区间**：利用后续样本重要性采样估计每个阶段的条件方差，并借助鞅中心极限定理构建置信区间，可在线流式计算（O(t)复杂度）。
- **算法流程**（伪代码见Algorithm 1和2）：  
  1. 初始化已标注集 \(D_1\) 和提议分布 \(q_1\)；  
  2. 每步 \(t\)：从 \(q_t\) 采样一个单元 \(s_t\)，获取真值 \(f(s_t)\)；  
  3. 用公式(2)形成无偏估计 \(\hat{F}_t\)；  
  4. 将所有历史估计加权组合为 \(\hat{F}_{1:t}\)；  
  5. 用Algorithm 2估计方差，构建置信区间；  
  6. 将 \(s_t\) 加入 \(D_{t+1}\)，微调AI模型更新提议分布 \(q_{t+1}\)。

## 3. 实验设计
- **数据集/场景**：
  - **高分辨率鸟群图像计数**：两张图像（“sky”和“reeds”），分别含925和1426个图块，真值由人工标注点获得。
  - **雷达鸟群计数**：11个美国大湖区雷达站的数据，每年6-10月共5年，每个站点约765天，地面真值由专家筛选的鸟巢检测结果提供。
  - **额外数据集**：疟疾感染细胞计数（1364张图像）、卫星图像受损建筑计数（113张图像），用于展示领域泛化性。
- **基准方法**：
  - 简单蒙特卡洛（MC/MC+WOR）
  - DISCount（DIS，即固定提议分布，无放回版本DIS+WOR）
  - DIS+无放回（DIS+WOR）
  - DIS+自适应重要性采样（DIS+AIS）
  - 原始检测器预测（Raw Detector）
  - 预测驱动推断（PPI）风格估计器 \(\hat{H}_t\)
  - 主动测试（Active testing）
- **对比方法**：主要与上述基线比较分数误差和置信区间覆盖率。

## 4. 资源与算力
- **明确说明**：
  - 鸟群图像检测器：Faster R-CNN（ResNet-50），在单块A16 GPU上微调400迭代，学习率0.001，每次约20分钟，共8次微调，总计约3小时单图。
  - 雷达检测器：Faster R-CNN（ResNet-101），微调学习率10⁻⁴，3000迭代，每次约2小时/GPU，共4次微调，总计约8小时/站。
- **说明**：论文明确报告了使用的GPU型号和训练时长，计算资源合理但未详细说明总实验开销。

## 5. 实验数量与充分性
- **实验组数**：
  - 鸟群图像：10,000次重复（固定检查点方案），1,000次端到端验证（图A4）。
  - 雷达数据：5,000次重复，覆盖11个站。
  - 额外数据集：各1,000次端到端试验。
  - 权重方案对比、置信区间覆盖分析、与额外基线对比等多个消融实验。
- **充分性与客观性**：实验数量充分，覆盖多种任务（计数、物体检测）和不同难度（简单到极难），统计重复次数高，结果稳定。固定检查点方案与端到端方案趋势一致，验证了近似有效性。但未包含所有可能的超参数搜索或全量消融，部分结论依赖理论最优性。

## 6. 论文的主要结论与发现
- 主动测量在几乎所有实验中都显著优于原始检测器预测和DISCount等基线，尤其在检测器性能较差时（如雷达任务）提升更为明显。
- 组合权重（COMB）在权衡模型适应和样本空间缩减方面优于单一权重方案（SQRT或LURE）；逆方差权重（INV）在适中γ下可进一步降低误差。
- 置信区间覆盖率随着标注数量增加趋近于名义水平（0.95），宽度与误差成比例；提出的条件方差估计器提供良好的不确定性量化。
- 检测器微调（AIS）和无放回采样（WOR）各自贡献显著，且两者结合效果最佳。

## 7. 优点
- **方法论创新**：将自适应重要性采样与无放回采样、交互式模型微调融合，首次提出组合权重并理论证明其最坏情况最优性（因子9/8）。
- **统计严谨**：推导了无偏估计器、一致方差估计、鞅中心极限定理支持的置信区间，提供理论保证。
- **实验全面**：在多种科学测量任务（鸟类计数、雷达生态、医学细胞、灾害评估）上验证，均显示优势，结果具有泛化性。
- **实用性强**：提供了流式算法降低方差计算复杂度，适合在线部署；固定检查点方法大幅降低计算开销，便于大规模重复实验。

## 8. 不足与局限
- **应用限制**：对于某些高精度要求场景，可能仍需大量标注；未探讨系统偏差（如探测器系统性低估）的鲁棒性。
- **实验覆盖**：主要基于特定检测器（Faster R-CNN），未在多种模型架构（如Transformer、few-shot）上充分测试；雷达任务仅覆盖11个站点，未涵盖所有地理区域。
- **偏差风险**：逆方差加权可能引入轻微偏置；早期估计器方差大，权重方案依赖估计准确性；置信区间在少数站点覆盖率低于0.95（如KIWX、KTYX）。
- **算力要求**：微调深度检测网络需要GPU，对于资源受限场景可能不适用；未探讨轻量级模型或在线更新的可行性。
- **未讨论**：跨图块空间相关性（如高斯过程建模）、半监督/自监督辅助适应性提升等未来方向。

（完）
