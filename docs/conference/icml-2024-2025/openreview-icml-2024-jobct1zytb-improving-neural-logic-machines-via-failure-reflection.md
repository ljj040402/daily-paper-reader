---
title: Improving Neural Logic Machines via Failure Reflection
title_zh: 通过失败反思改进神经逻辑机
authors: "Zhiming Li, Yushi Cao, YAN ZHENG, Xu Liu, Bozhi Wu, Tianlin Li, Xiufeng Xu, Junzhe Jiang, Yon Shin Teo, Shang-Wei Lin, Yang Liu"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=JObct1zyTb"
tags: ["query:ai"]
score: 7.0
evidence: 通过失败反思改进神经逻辑机的推理能力
tldr: 该论文针对神经逻辑机（NLM）在推理任务中重复犯相同错误的问题，提出失败反思引导正则化器（FRGR）。FRGR在训练过程中动态识别模型反复出现的错误类型，并施加惩罚，从而避免陷入次优。在多个推理数据集上，FRGR显著提升了NLMs的准确率和泛化能力。这一框架可作为通用插件应用于其他神经符号模型。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-jobct1zytb/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 864, \"height\": 372, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-jobct1zytb/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 772, \"height\": 576, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-jobct1zytb/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 442, \"height\": 600, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-jobct1zytb/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 811, \"height\": 488, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-jobct1zytb/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 805, \"height\": 404, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-jobct1zytb/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1779, \"height\": 711, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-jobct1zytb/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1740, \"height\": 849, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-jobct1zytb/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1767, \"height\": 858, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-jobct1zytb/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1776, \"height\": 811, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-jobct1zytb/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1778, \"height\": 1135, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-jobct1zytb/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1739, \"height\": 846, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-jobct1zytb/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1771, \"height\": 681, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-jobct1zytb/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1772, \"height\": 678, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-jobct1zytb/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1539, \"height\": 653, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-jobct1zytb/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1762, \"height\": 326, \"label\": \"Table\"}]"
motivation: 神经逻辑机在训练中常重复相同错误，导致性能次优。
method: 动态识别模型重复错误并施加正则化惩罚，引导模型避免相同错误。
result: 在多个推理任务上提升了神经逻辑机的准确率和泛化性。
conclusion: 失败反思正则化为神经符号学习提供了一种有效的错误纠正机制。
---

## Abstract
Reasoning is a fundamental ability towards artificial general intelligence (AGI). Fueled by the success of deep learning, the neural logic machines models (NLMs) have introduced novel neural-symbolic structures and demonstrate great performance and generalization on reasoning and decision-making tasks. However, the original training approaches of the NLMs are still far from perfect, the models would repeat similar mistakes during the training process which leads to sub-optimal performance. To mitigate this issue, we present a novel framework named Failure Reflection Guided Regularizer (FRGR). FRGR first dynamically identifies and summarizes the root cause if the model repeats similar mistakes during training. Then it penalizes the model if it makes similar mistakes in future training iterations. In this way, the model is expected to avoid repeating errors of similar root causes and converge faster to a better-performed optimum. Experimental results on multiple relational reasoning and decision-making tasks demonstrate the effectiveness of FRGR in improving performance, generalization, training efficiency, and data efficiency.

---

## 论文详细总结（自动生成）

# 中文论文详细总结

## 1. 核心问题与整体含义（研究动机和背景）

神经逻辑机（Neural Logic Machines, NLMs）是一类结合神经网络与符号逻辑的模型，在关系推理和决策任务上展现出良好的性能与泛化能力。然而，现有NLMs的训练方法存在严重缺陷：模型在训练过程中会反复犯相似的错误，导致损失函数振荡在次优局部最优，难以跳脱。作者观察到，NLM和DLM（可微分逻辑机）在IsUncle等推理任务中，训练损失曲线长时间振荡后才下降，或一直困于局部最优点。根本原因是模型在反复使用具有相同根因的错误子程序（subprogram），而原始训练方法无法识别并阻止这种行为。为此，作者提出**失败反思引导的正则化器（FRGR）**，旨在动态识别错误重复的根因并施加惩罚，使模型更快跳出振荡，收敛到更优解。

## 2. 方法论

### 2.1 核心思想
FRGR在训练过程中动态地：  
- **根因挖掘**：当模型重复犯相似错误时，提取当前模型的程序表示（通过程序提取器），存入历史队列，并使用频繁项集挖掘（Apriori算法）找出频繁共现的神经元集合，作为根因子程序。  
- **重复正则化**：计算当前程序表示与根因子程序的交集，对交集中对应的网络权重施加L1正则化惩罚，阻止模型继续使用这些错误子程序。

### 2.2 关键细节
- **程序提取器**：对于NLM，取每个逻辑模块（MLP）中与输出神经元连接的最大权重对应的输入神经元索引，组成程序表示；对于DLM，类似地取模糊逻辑模块中的最大连接。
- **历史程序队列**：大小为m的队列，存储模型在犯错的训练步中提取的程序表示。
- **根因挖掘**：每m轮执行一次Apriori算法，找出支持度超过阈值的频繁项集，作为根因。
- **正则化损失**：\( \mathcal{L}_{\text{ReReg}} = \sum \|\phi_j\|_1 \)，其中 \(\phi\) 为当前程序与根因交集对应的权重参数。
- **总损失**：原始分类损失 + β * L_ReReg。

### 2.3 算法流程
1. 训练当前模型，若输出错误，提取程序表示并入队。
2. 当历史队列大小达到阈值，运行Apriori更新根因。
3. 用分类损失和重复正则化损失共同更新模型参数。

## 3. 实验设计

### 3.1 数据集/场景
- **关系推理**：家族树推理（5个子任务：HasFather, HasSister, IsGrandparent, IsUncle, IsMGUncle）和一般图推理（4个子任务：1-OutDegree, 2-OutDegree, 4-Connectivity, 6-Connectivity）。
- **强化学习**：Sorting, Path, BlocksWorld。

### 3.2 基准与对比方法
- **基线模型**：原始NLM（Neural Logic Machines）和原始DLM（Differentiable Logic Machines）。
- **对比设置**：分别在数据丰富（大数据量训练）和数据稀缺（1/500训练数据）两种场景下比较。

### 3.3 评估指标
- **性能**：在测试集上的成功率（success rate）。
- **泛化**：在不同规模测试集上的成功率（如家族树从20人扩展到100人，图从10节点扩展到20节点）。
- **训练效率**：达到最优验证集成功率所需的训练轮数（#Epochs）。
- **毕业率**：多次种子实验中训练集达到100%成功的比例。

## 4. 资源与算力
论文在附录C中说明：
- **硬件**：Ubuntu 18.05服务器，48核Intel Xeon Silver 4214 CPU，4块NVIDIA Quadro RTX 8000 GPU，252GB RAM。
- **训练时长**：未明确给出具体时间，但报告了各任务所需的epoch数（例如IsUncle任务NLM需143.7轮，加入FRGR后降至78.4轮）。
- **超参数**：使用Adam优化器，学习率0.005，批量大小4，正则化系数β=0.1，历史队列大小τ=100。

## 5. 实验数量与充分性
- **主要实验**：在9个关系推理子任务和3个强化学习任务上，分别测试NLM和DLM两种基线，每个任务在数据丰富和数据稀缺两种设置下进行评估，共计约\( 2 \text{ (模型)} \times (9+3) \text{ (任务)} \times 2 \text{ (设置)} = 48 \)组核心对比结果。
- **消融/分析实验**：  
  - 动机验证：通过分析训练过程中一元原子比率（UAR）和损失曲线，证明模型重复错误及FRGR的缓解效果。  
  - 超参数分析：对β（0.1, 0.05, 0.01, 0.005, 0.001）和τ（50, 100, 150, 200）进行调参实验。  
  - 行为分析：可视化重复正则化损失与分类损失的相关性。
- **充分性判断**：实验覆盖了从简单到复杂的多种推理任务，对比了两种主流NLM架构，并考虑了数据稀缺场景，实验设计较为充分。论文使用官方代码和设置，对比公平。但RL任务中DLM的复现问题导致仅报告NLM结果，是一个小缺憾。

## 6. 主要结论与发现
- FRGR显著提升了NLMs在大多数任务上的性能、泛化能力和训练效率。  
- 在数据稀缺场景下，FRGR同样能有效提升模型表现，表明其具有数据效率优势。  
- 动机验证表明，原始NLMs在训练中会长期使用错误子程序（如一元原子占比高），FRGR能显著降低这种错误重复，帮助模型跳出局部最优。  
- 超参数实验表明，FRGR对β和τ具有一定稳健性，但β不宜过低。

## 7. 优点
- **创新性**：首次提出利用错误根因进行正则化来优化神经符号模型训练，思路新颖。  
- **通用性**：FRGR可灵活应用于NLM和DLM两种架构，且可扩展到其他神经符号模型。  
- **实验全面**：覆盖多种推理任务、两种数据设置，并包含消融和动机分析，论证充分。  
- **透明性**：公开代码，易于复现。

## 8. 不足与局限
- **简单任务负作用**：对于非常简单的任务（如HasFather, 1-OutDegree），FRGR可能略微增加训练轮数，因为额外正则化可能减慢收敛。  
- **效率依赖**：根因挖掘需定期运行Apriori频繁项集挖掘，当模型规模或历史队列较大时可能带来计算开销，论文未详细分析时间开销。  
- **局限性**：目前仅验证了在NLMs上的有效性，未测试其他类型的神经符号模型（如∂ILP）或深度学习模型。  
- **RL任务复现问题**：DLM在RL任务上的结果无法复现，因此只在NLM上进行了RL实验，削弱了对比的完整性。  
- **偏差风险**：根因挖掘依赖于程序提取器的近似表示，可能无法捕获所有错误模式，存在信息损失风险。

（完）
