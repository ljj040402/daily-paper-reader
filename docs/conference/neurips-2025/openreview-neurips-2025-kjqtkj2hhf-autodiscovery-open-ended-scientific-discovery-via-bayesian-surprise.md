---
title: "AutoDiscovery: Open-ended Scientific Discovery via Bayesian Surprise"
title_zh: AutoDiscovery：基于贝叶斯惊奇的开放式科学发现
authors: "Dhruv Agarwal, Bodhisattwa Prasad Majumder, Reece Adamson, Megha Chakravorty, Satvika Reddy Gavireddy, Aditya Parashar, Harshit Surana, Bhavana Dalvi Mishra, Andrew McCallum, Ashish Sabharwal, Peter Clark"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=kJqTkj2HhF"
tags: ["query:ai"]
score: 6.0
evidence: 通过贝叶斯惊奇实现开放式科学发现，人工智能研究
tldr: 现有自主科学发现系统依赖人类指定的研究问题或多样性启发式，难以实现真正的开放式探索。本文提出AutoDiscovery方法，利用贝叶斯惊奇作为驱动，让AI系统自主选择能带来最大信息增益的假设。通过将贝叶斯惊奇与基于大语言模型的假设生成相结合，AutoDiscovery在化学和生物学数据集上发现了比基线更具新颖性和趣味性的假设。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-kjqtkj2hhf/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1439, \"height\": 726, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kjqtkj2hhf/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1447, \"height\": 803, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kjqtkj2hhf/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 714, \"height\": 488, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kjqtkj2hhf/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 795, \"height\": 726, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kjqtkj2hhf/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1563, \"height\": 1160, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kjqtkj2hhf/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1152, \"height\": 568, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kjqtkj2hhf/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1460, \"height\": 818, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kjqtkj2hhf/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1437, \"height\": 418, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-kjqtkj2hhf/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 763, \"height\": 466, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-kjqtkj2hhf/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 745, \"height\": 242, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-kjqtkj2hhf/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1372, \"height\": 261, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-kjqtkj2hhf/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 571, \"height\": 212, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-kjqtkj2hhf/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1067, \"height\": 759, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-kjqtkj2hhf/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1453, \"height\": 584, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-kjqtkj2hhf/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 766, \"height\": 2432, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-kjqtkj2hhf/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1082, \"height\": 166, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-kjqtkj2hhf/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1450, \"height\": 171, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-kjqtkj2hhf/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1442, \"height\": 1192, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-kjqtkj2hhf/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1289, \"height\": 135, \"label\": \"Table\"}]"
motivation: 现有自主科学发现系统缺乏真正开放式探索的能力。
method: 利用贝叶斯惊奇驱动假设选择，结合大语言模型生成新假设。
result: 在化学和生物学数据集上发现更具新颖性和趣味性的假设。
conclusion: 贝叶斯惊奇能有效引导AI系统进行开放式科学发现。
---

## Abstract
The promise of autonomous scientific discovery (ASD) hinges not only on answering questions, but also on knowing which questions to ask. Most recent works in ASD explore the use of large language models (LLMs) in goal-driven settings, relying on human-specified research questions to guide hypothesis generation. However, scientific discovery may be accelerated further by allowing the AI system to drive exploration by its own criteria. The few existing approaches in open-ended ASD select hypotheses based on diversity heuristics or subjective proxies for human interestingness, but the former struggles to meaningfully navigate the typically vast hypothesis space, and the latter suffers from imprecise definitions. This paper presents AutoDiscovery—a method for open-ended ASD that instead drives scientific exploration using Bayesian surprise. Here, we quantify the epistemic shift from the LLM’s prior beliefs about a hypothesis to its posterior beliefs after gathering experimental results. To efficiently explore the space of nested hypotheses, our method employs a Monte Carlo tree search (MCTS) strategy with progressive widening using surprisal as the reward function. We evaluate AutoDiscovery in the setting of data-driven discovery across 21 real-world datasets spanning domains such as biology, economics, finance, and behavioral science. Our results demonstrate that under a fixed budget, AutoDiscovery substantially outperforms competitors by producing 5-29% more discoveries deemed surprising by the LLM. Our human evaluation further reveals that two-thirds of discoveries made by our system are surprising to domain experts as well, suggesting this is an important step towards building open-ended ASD systems.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义

**研究动机与背景**：
- 现有的自主科学发现（ASD）系统大多处于“目标驱动”模式，即需要人类提供具体研究问题，系统仅负责生成假设、设计实验、执行并分析结果。这种模式缺乏真正的“开放式”探索能力——即让AI系统自主决定“接下来该探索哪些问题”。
- 少数开放式ASD工作使用多样性启发式或主观代理指标（如“有趣性”“新颖性”）来引导搜索，但多样性不足以在巨大假设空间中有效导航，而人类主观指标（如“有趣性”）本身定义模糊、评分者间一致性低，不适合作为自动引导信号。
- **核心问题**：如何让ASD系统在没有人类指定目标的情况下，自主、高效地探索假设空间，发现真正新颖且有科学价值的发现？

**整体含义**：
本文提出一种基于**贝叶斯惊奇（Bayesian Surprise）**的开放式ASD方法AutoDiscovery，利用大语言模型（LLM）自身信念在观察到实验证据前后的变化（即“惊奇程度”）作为引导搜索的奖励信号，结合蒙特卡洛树搜索（MCTS）高效探索假设空间。该方法在21个真实数据集上显著优于现有基线，且三分之二由系统发现的“惊奇”假设也被人类领域专家认为是惊奇的，展示了其作为开放式ASD系统的潜力。

## 2. 论文提出的方法论

### 核心思想
- 利用**贝叶斯惊奇**量化一个假设H给LLM带来的“信念转变”程度：即LLM在观察到实验证据VD(H)之前（先验）和之后（后验）关于该假设为真的信念分布之间的KL散度。
- 只有当信念期望值跨过某个决策阈值（如0.5）时，才视为发生了“惊奇性”（Surprisal），此时才赋予正奖励。
- 使用**蒙特卡洛树搜索（MCTS）**（结合上置信界树UCT和渐进扩宽策略）在高维假设空间中平衡探索与利用，以最大化惊奇性假设的发现数量。

### 关键技术细节
1. **信念启发**：
   - 假设LLM对假设H的信念θH服从Beta分布。通过采样n个布尔响应（“该假设是否为真？”），分别在没有实验证据（先验）和有实验证据（后验）的情况下，用观测到的“真”响应计数k_prior和k_post更新Beta分布参数，得到经验先验P_est(θH)和P_est(θH|VD)。
   - 公式（1）（2）给出具体更新：P_est(θH) = Beta(θH|1+k_prior, 1+n-k_prior)等。
2. **贝叶斯惊奇与惊奇性定义**：
   - 贝叶斯惊奇BS(H,VD) = D_KL(P(θH|VD) ∥ P(θH))。
   - **惊奇性（Surprisal）**指标S(H,VD)定义为：若先验期望和后验期望分别位于决策阈值δ（通常0.5）的两侧，且期望值不同，则S=1，否则为0。同时结合BS的幅度，提出BS_shift（公式4）。
3. **MCTS搜索流程**（Algorithm 1）：
   - **选择**：从根节点开始，使用UCT公式（6）选择子节点，平衡平均惊奇性和探索项。
   - **扩展**：当访问次数未达到渐进扩宽阈值时，从当前节点采样新假设；否则递归选择子节点。
   - **执行**：对新假设执行验证实验VD，并估计其惊奇性S(H,VD)（通过信念启发步骤）。
   - **反向传播**：将惊奇值沿路径回传，更新节点统计。
4. **去重**：基于LLM的层次凝聚聚类（HAC），结合文本嵌入和LLM判断来识别语义等价假设。

## 3. 实验设计

### 数据集/场景
- 使用了 **21个真实世界数据集**，覆盖多个领域：
  - **DiscoveryBench**（5个数据集）：freshwater-fish, nls-bmi, nls-ses, nls-incarceration, requirement-engineering。
  - **BLADE**（15个数据集）：affairs, amtl, boxes, caschools, conversation, crofoot, fertility, fish, hurricane, mortgage, panda_nuts, reading, soccer, teachingratings, toy。
  - **SEA-AD**（1个数据集）：阿尔茨海默病相关多模态细胞图谱元数据。

### 优化目标
- 在固定预算（500次假设验证）下，最大化系统发现的“惊奇性”假设数量（由LLM后验信念判定）。

### 对比方法
所有方法使用相同发现智能体（多智能体框架，基于GPT-4o），对比以下策略：
1. **重复独立采样（Repeated Sampling）**：无上下文，每次独立生成假设。
2. **线性搜索（Last-K Linear）**：只保留最近K=100个父节点作为上下文，顺序生成。
3. **贪心树搜索（Greedy）**：MCTS变种，探索常数C=0，仅利用。
4. **束搜索（Beam Search）**：束宽8，每层保留top-8，生成64个候选后裁剪。
5. **AutoDiscovery（MCTS）**：本文方法，使用UCT平衡探索。

### 额外实验
- 将贝叶斯惊奇替换为其他自动奖励（直接LLM惊奇、LLM有趣性、LLM有用性），比较与人类判断的相关性。
- 使用o4-mini（推理模型）重复主要对比。
- 人工验证实验有效性和实现忠实度。

## 4. 资源与算力

论文中**未明确说明**所使用的GPU型号、数量及训练时长。实验依赖OpenAI API（GPT-4o和o4-mini），所有计算均在云端进行，未提供本地算力细节。作者提到平均每个节点（假设）耗时约75秒，最长600秒，但未给出总计算资源估计。

## 5. 实验数量与充分性

- **主要对比实验**：在21个数据集上，每个数据集运行5种方法（重复采样、线性、贪心、束搜索、MCTS），每种方法预算500次验证。图2展示了累积惊奇发现数（均值、误差带）、搜索效率斜率、各数据集细分结果。
- **人工评估**：
  - 对4个数据集、4种自动奖励的1,620个假设，由3位STEM硕士/博士标注者进行人类惊奇性、有趣性、有用性评分。
  - 内部验证：对175个节点标注实验有效性和实现忠实度；对120对假设标注去重有效性。
- **消融/替代奖励实验**：比较贝叶斯惊奇 vs. LLM惊奇/有趣性/有用性作为MCTS奖励，在人类评分上的表现。
- **推理模型实验**：使用o4-mini重复主要对比（图8）。
- **结论**：实验规模较大（21个数据集、多种基线、人工验证），覆盖多个领域，对比方法全面，统计结果有误差带，总体客观充分。但未进行跨模型（如不同LLM型号）或不同预算设置的广泛消融。

## 6. 论文的主要结论与发现

1. **AutoDiscovery（MCTS）在惊奇性发现数量上显著优于所有基线**：在21个数据集中平均产生比第二名（贪心/束搜索）多5-29%的惊奇性假设。图2(a)显示MCTS累积曲线超越其他方法，且搜索效率下降最慢（图2(b)）。
2. **贝叶斯惊奇与人类惊奇高度相关**：人工评估表明，AutoDiscovery发现的假设中67%被领域专家评为“惊奇”，远超其他自动奖励（直接LLM惊奇仅11%，有趣性15%，有用性21%）。表2显示贝叶斯惊奇在所有熟悉度层次上均优于其他指标。
3. **有趣性和有用性指标缺乏清晰语义**：所有自动奖励在人类有趣性/有用性评分上表现相似（约0.73-0.80），说明这些概念过于主观，不适合作为自动引导信号。
4. **信念转变方向因领域而异**：图3显示大多数惊奇性假设是从“支持”转向“不支持”（证伪），且证伪的KL散度通常更大，暗示LLM可能更容易被证伪证据说服。
5. **发现智能体框架高度可靠**：实验有效性98.6%，实现忠实度98.0%，去重准确率90.8%，均具有良好的标注者间一致性。

## 7. 优点

1. **理论驱动的自动化指标**：贝叶斯惊奇建立了严格的信念转变量化框架，避免了主观代理指标的模糊性，并与人类惊奇性高度一致。
2. **高效的搜索策略**：MCTS结合渐进扩宽和UCT，平衡探索与利用，在有限预算下显著优于线性/贪心/束搜索。
3. **广泛的实证验证**：在21个真实世界数据集（跨4个领域）上验证，并有大规模人工标注支持，结果可靠。
4. **框架通用性**：方法不局限于特定数据类型或模型，可推广至文献驱动或其他科学发现场景。
5. **可解释性**：通过信念分布和惊奇分数，可以追溯哪些假设令LLM“惊讶”及转变方向，增加了系统透明性。

## 8. 不足与局限

1. **依赖LLM代理的可靠性**：代理框架可能出现代码执行错误、环境损坏、上下文窗口溢出等问题（附录有示例）。尽管验证了高有效性，但失败案例仍可能引入虚假发现。
2. **LLM惊奇≠人类惊奇**：67%的一致性虽高，但仍有33%的假阳性。LLM的“惊讶”可能源于模型偏差或训练数据中的错误关联，而非科学意义上的新颖性。
3. **未充分覆盖所有科学领域**：仅包含数据驱动的定量分析（无湿实验），且数据集来自有限来源（DiscoveryBench、BLADE、SEA-AD），可能无法代表所有科学领域。
4. **计算成本未量化**：未报告总API调用成本或本地算力需求，可能限制了方法在资源受限环境中的可复现性。
5. **单一模型实验**：主要使用GPT-4o，仅补充o4-mini，但未测试其他LLM（如Llama、Claude）以验证泛化性。
6. **去重依赖LLM判断**：HAC去重虽然准确率90.8%，但仍有约9%的误判，可能无意中合并了非等价假设或遗漏了重复假设。
7. **假设空间限定**：假设被定义为“上下文+变量+关系”的三元组，可能无法涵盖所有科学假设类型（如机制性、因果性更复杂的陈述）。

（完）
