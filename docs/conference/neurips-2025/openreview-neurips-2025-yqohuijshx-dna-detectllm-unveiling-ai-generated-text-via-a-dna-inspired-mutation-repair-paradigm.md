---
title: "DNA-DetectLLM: Unveiling AI-Generated Text via a DNA-Inspired Mutation-Repair Paradigm"
title_zh: DNA-DetectLLM：通过DNA启发的突变-修复范式揭示AI生成文本
authors: "Xiaowei Zhu, Yubing Ren, Fang Fang, Qingfeng Tan, Shi Wang, Yanan Cao"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=yQoHUijSHx"
tags: ["query:ai"]
score: 5.0
evidence: DNA启发的AI文本检测
tldr: 该论文提出DNA-DetectLLM，从DNA视角出发，利用修复过程直接捕捉人类与AI文本的内在差异。该方法在特征分布重叠严重的情况下仍然有效，增强了检测的准确性和可解释性。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-yqohuijshx/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1446, \"height\": 559, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-yqohuijshx/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1434, \"height\": 464, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-yqohuijshx/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1447, \"height\": 305, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-yqohuijshx/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1446, \"height\": 1030, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-yqohuijshx/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1432, \"height\": 387, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-yqohuijshx/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 704, \"height\": 479, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-yqohuijshx/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 687, \"height\": 504, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-yqohuijshx/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1440, \"height\": 617, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-yqohuijshx/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1437, \"height\": 431, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-yqohuijshx/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1448, \"height\": 632, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-yqohuijshx/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1443, \"height\": 494, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-yqohuijshx/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1249, \"height\": 337, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-yqohuijshx/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1080, \"height\": 532, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-yqohuijshx/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1079, \"height\": 529, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-yqohuijshx/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1079, \"height\": 528, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-yqohuijshx/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1439, \"height\": 339, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-yqohuijshx/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1388, \"height\": 257, \"label\": \"Table\"}]"
motivation: LLM使人类与AI文本特征重叠，传统检测方法准确性下降，急需新方法。
method: 借鉴DNA修复机制，设计基于修复的检测过程，直接捕捉两类文本的差异特征。
result: 在多种挑战性数据集上提高了检测准确率和可解释性。
conclusion: DNA启发的范式为AI文本检测提供了新颖而有效的手段。
---

## Abstract
The rapid advancement of large language models (LLMs) has blurred the line between AI-generated and human-written text. This progress brings societal risks such as misinformation, authorship ambiguity, and intellectual property concerns, highlighting the urgent need for reliable AI-generated text detection methods. However, recent advances in generative language modeling have resulted in significant overlap between the feature distributions of human-written and AI-generated text, blurring classification boundaries and making accurate detection increasingly challenging. To address the above challenges, we propose a DNA-inspired perspective, leveraging a repair-based process to directly and interpretably capture the intrinsic differences between human-written and AI-generated text. Building on this perspective, we introduce **DNA-DetectLLM**, a zero-shot detection method for distinguishing AI-generated and human-written text. The method constructs an ideal AI-generated sequence for each input, iteratively repairs non-optimal tokens, and quantifies the cumulative repair effort as an interpretable detection signal. Empirical evaluations demonstrate that our method achieves state-of-the-art detection performance and exhibits strong robustness against various adversarial attacks and input lengths. Specifically, DNA-DetectLLM achieves relative improvements of **5.55\%** in AUROC and **2.08\%** in F1 score across multiple public benchmark datasets. Code and data are available at https://github.com/Xiaoweizhu57/DNA-DetectLLM.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：大语言模型（LLM）的快速发展使得AI生成文本与人类撰写文本的特征分布高度重叠，传统检测方法（基于训练或无需训练）依赖特征空间中的清晰分类边界，但边界越来越模糊，导致检测准确性显著下降。
- **社会风险**：AI生成文本可能加剧虚假信息传播、作者身份混淆、知识产权侵犯等问题，迫切需要可靠且可解释的检测方法。
- **动机**：现有方法（训练型容易过拟合分布内特征，训练型依赖统计假设）在分布重叠区域表现不佳。作者受DNA复制中的突变-修复机制启发，提出一种新的视角：将理想AI生成文本视为“模板链”，人类文本视为发生突变的链，通过修复难度来区分两者。

## 2. 方法论

### 核心思想
- **DNA类比**：理想AI序列（每个位置取最大概率token）类比DNA模板链，人类文本中的token偏离理想选择视为突变。通过模拟修复过程，测量修复难度，从而捕捉两类文本的生成本质差异。
- **零样本检测**：无需训练数据，仅依赖参考语言模型计算条件概率。

### 关键技术细节
1. **获取理想AI序列** $\hat{s}$：对输入序列 $s$，利用参考模型 $M_1$，在每个位置 $i$ 选取条件概率最大的token：  
   $\hat{x}_i = \arg\max_{\tilde{x} \in V} P_{M_1}(\tilde{x} | x_{<i})$。
2. **突变修复机制**：逐token比较输入序列 $s$ 与理想序列 $\hat{s}$，若 $x_i \neq \hat{x}_i$，则将该token修复为 $\hat{x}_i$。迭代执行直到序列完全对齐。
3. **修复分数** $R(s)$：定义为修复过程中条件分数的平均值：  
   $R(s) = \frac{1}{T+1} \sum_{t=0}^{T} \sigma(s_t | s)$，其中 $\sigma(st|s) = \frac{\log PPL_{M_1}(st|s)}{\log X-PPL_{M_1, M_2}(s)}$。
   - 通过理论推导（随机修复的期望），简化为：$R(s) = \frac{1}{2} (\sigma(s) + \sigma(\hat{s}|s))$，避免迭代计算，大幅提升效率。
4. **检测决策**：$R(s) > \tau$ 判定为人类文本，否则为AI文本（$\tau$ 为校准阈值）。

### 算法流程（文字说明）
- 输入文本 $s$ → 用参考模型获得理想序列 $\hat{s}$ → 计算初始条件分数 $\sigma(s)$ 和最终条件分数 $\sigma(\hat{s}|s)$ → 计算简化修复分数 $R(s)$ → 与阈值比较得到检测结果。

## 3. 实验设计

### 数据集
- **主要评估数据**：从三个来源收集4,800个人类文本：XSum（新闻摘要）、WritingPrompts（故事生成）、Arxiv（学术写作）。对每个文本，使用GPT-4 Turbo、Gemini-2.0 Flash、Claude-3.7 Sonnet生成对应的AI文本（每个LLM生成1,600个）。
- **公共基准**：从M4、DetectRL（含Multi-LLM和Multi-Domain两个子集）、RealDet各采样2,000个平衡样本。

### Benchmark与对比方法
- **训练型方法**：OpenAI-D、Biscope、R-Detect（均在HC3数据集上训练，与测试集不重叠）。
- **训练-free方法**：Entropy、Likelihood、LogRank、DetectGPT、Fast-DetectGPT、Binoculars、Lastde++。
- **额外对比**（附录）：Revise-Detect、GECScore、DNA-GPT、IMBD、GPTZero，以及在PubMedQA数据集上的测试。

### 指标
- AUROC、F1分数（均报告最优阈值下的结果，并在表格4中给出固定阈值下的F1）。

## 4. 资源与算力

- **硬件**：单个NVIDIA A100 GPU（80GB显存）。
- **训练细节**：训练型方法在HC3数据集（4,000样本）上训练，未报告具体训练时长或迭代次数。
- **推理效率**：所有方法在单GPU上测试，DNA-DetectLLM处理单样本约0.78秒（与其他训练-free方法相近）。
- **说明**：作者在附录A中指出，由于内存限制，未能在更大批大小下评估大规模实时监控性能，因此效率结果基于相对比较。

## 5. 实验数量与充分性

### 实验组数
- **主实验**：表1涵盖9个设置（3个数据集 × 3个LLM），表2涵盖4个基准设置（M4、DetectRL两个子集、RealDet），共13个场景。
- **鲁棒性实验**：图4展示针对4种攻击（插入、删除、替换、释义）× 3个LLM的AUROC曲线，共12种攻击场景。图5展示不同长度（5种长度）× 3个LLM。
- **消融实验**：表1中4种修复顺序对比；图6中4种LLM组合对比；附录表10额外消融。共约20+子实验。
- **效率实验**：图7比较11种方法单样本时间。

### 充分性与公平性
- **充分性**：覆盖多种文本类型、多种生成模型、多种攻击、多种长度，实验设计系统全面。
- **公平性**：训练型方法严格使用不相交的数据集；训练-free方法统一参考模型（Falcon-7B）和观察模型（Falcon-7B）；所有方法在同一硬件环境下评估。
- **不足**：未报告多次运行的统计误差（如标准差或置信区间）；未进行超参数敏感性分析。

## 6. 主要结论与发现

1. **性能领先**：DNA-DetectLLM在所有设置下达到SOTA，平均AUROC 98.30%（相对提升0.93%），在公共基准上AUROC平均提升5.55%、F1提升2.08%。
2. **强鲁棒性**：对token编辑攻击（插入/删除/替换）和释义攻击均表现最佳，尤其低假阳性率下优势显著。
3. **短文本优势**：在40 tokens短文本上，AUROC超出第二名3%以上，优于其他方法。
4. **修复顺序不敏感**：通过简化公式（取起始和结束分数的均值）避免了迭代计算，性能保持不变，效率提升20倍。
5. **模型无关性**：不同LLM组合（Falcon、Llama、Mistral）下仍显著超越基线，说明方法不依赖特定模型。

## 7. 优点

- **新视角可解释**：DNA突变-修复机制直观可解释，直接量化生成差异而非隐式特征。
- **零样本、通用性强**：无需标注数据，跨领域、跨模型均表现稳定，泛化性好。
- **鲁棒性突出**：对多种对抗攻击和短文本均保持高检测性能。
- **计算高效**：简化后的修复分数计算仅需两次前向传播，单样本0.78秒，适合实时检测。
- **理论完备**：推导了修复分数的期望收敛公式，简化了算法流程。
- **实验全面**：涵盖多种数据集、生成模型、攻击类型、长度，验证了方法的可靠性和实用性。

## 8. 不足与局限

- **实验统计学不足**：未报告多次重复实验的误差线或置信区间，无法评估结果的波动性。
- **资源限制**（附录A）：单批次大小下评估效率，未探索大规模并发场景下的实际吞吐量。
- **对抗攻击覆盖有限**：仅测试了token级编辑和DIPPER释义攻击，未考虑更复杂的对抗策略（如句子级改写、混合生成、适应检测器的攻击）。
- **语言与领域局限**：仅在英语文本上验证，对其他语言或多模态内容（代码、表格等）的适用性未知。
- **理想序列假设偏差**：理想AI序列由greedy解码得到，但实际AI生成常用采样（temperature>0），可能导致理想序列与真实生成分布有出入。
- **阈值依赖**：检测依赖校准阈值，实际部署时需在干净验证集上调整，可能在分布漂移时失效。
- **伦理风险**（附录B）：作者强调检测结果不能作为直接证据，存在误判风险，可能造成不当指控。

（完）
