---
title: Probabilistic Reasoning with LLMs for Privacy Risk Estimation
title_zh: 基于大语言模型的概率推理用于隐私风险评估
authors: "Jonathan Zheng, Alan Ritter, Sauvik Das, Wei Xu"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=HMVQ00vabY"
tags: ["query:ai"]
score: 6.0
evidence: 利用大语言模型进行概率推理以评估隐私风险，属于人工智能研究
tldr: 大语言模型在数值推理任务上存在不足，尤其是涉及不确定性的隐私风险评估。本文提出BRANCH方法，利用贝叶斯网络分解个人信息联合概率分布，分别估计各因子在总体中的概率，从而计算文本的k-隐私值。实验表明，BRANCH在真实数据集上能准确估计隐私风险，为文本隐私保护提供了新工具。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-hmvq00vaby/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1414, \"height\": 663, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-hmvq00vaby/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1420, \"height\": 906, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-hmvq00vaby/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1442, \"height\": 511, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-hmvq00vaby/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1324, \"height\": 421, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-hmvq00vaby/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1447, \"height\": 483, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-hmvq00vaby/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1443, \"height\": 540, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-hmvq00vaby/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1381, \"height\": 582, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-hmvq00vaby/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1414, \"height\": 663, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-hmvq00vaby/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1421, \"height\": 550, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-hmvq00vaby/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1411, \"height\": 172, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-hmvq00vaby/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 871, \"height\": 358, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-hmvq00vaby/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 654, \"height\": 1277, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-hmvq00vaby/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 651, \"height\": 372, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-hmvq00vaby/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 649, \"height\": 1053, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-hmvq00vaby/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 871, \"height\": 737, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-hmvq00vaby/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1419, \"height\": 313, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-hmvq00vaby/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1428, \"height\": 216, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-hmvq00vaby/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 935, \"height\": 754, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-hmvq00vaby/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 546, \"height\": 333, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-hmvq00vaby/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1164, \"height\": 387, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-hmvq00vaby/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1008, \"height\": 193, \"label\": \"Table\"}]"
motivation: 大语言模型在处理不确定数值推理任务时存在局限，尤其是隐私风险评估。
method: 提出BRANCH方法，通过贝叶斯网络分解概率分布来估计文本的k-隐私值。
result: 在真实数据集上准确估计隐私风险。
conclusion: 概率因子分解能有效提升大语言模型在隐私风险评估中的数值推理能力。
---

## Abstract
Probabilistic reasoning is a key aspect of both human and artificial intelligence that allows for handling uncertainty and ambiguity in decision-making. In this paper, we introduce a new numerical reasoning task under uncertainty for large language models, focusing on estimating the privacy risk of user-generated documents containing privacy-sensitive information. We propose BRANCH, a new LLM methodology that estimates the $k$-privacy value of a text—the size of the population matching the given information. BRANCH factorizes a joint probability distribution of personal information as random variables.  The probability of each factor in a population is estimated separately using a Bayesian network and combined to compute the final $k$-value. Our experiments show that this method successfully estimates the $k$-value 73% of the time, a 13% increase compared to o3-mini with chain-of-thought reasoning. We also find that LLM uncertainty is a good indicator for accuracy, as high variance predictions are 37.47% less accurate on average.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：大语言模型（LLM）在数学和逻辑推理方面表现日益增强，但处理不确定性下的数值推理任务仍存在挑战。隐私风险评估是一个典型的不确定数值推理任务：需要估计在全世界有多少人同时具备用户文档中披露的多项个人属性（如年龄、性别、职业、健康状况等），从而帮助用户理解在线披露个人信息时的隐私风险大小。
- **背景**：传统的隐私研究主要关注数据集所有者如何通过k-anonymity等属性保护记录，而本研究将焦点转向数据贡献者（如Reddit用户），提供无需访问完整数据库即可计算的、可解释的风险估计。论文提出新的任务——隐私风险评估，并设计了BRANCH方法，利用贝叶斯网络分解联合概率分布，将每个属性作为随机变量，分别估计其在总体中的概率，再组合得到最终k值。

## 2. 论文提出的方法论

- **核心思想**：将用户文档中披露的个人属性表示为随机变量，通过贝叶斯网络结构建模它们的联合概率分布，从而估计匹配这些属性的总人数k。
- **关键技术细节**：
  - **贝叶斯网络结构生成**：LLM根据因果性和统计可用性对披露属性进行排序，并确定条件依赖关系，构建有向无环图（DAG）。
  - **查询生成与子查询分解**：将每个条件概率转换为文本查询（如“Townsbridge居民中从事Tech工作的百分比”），必要时分解为更易估计的子查询（如按年龄范围或离散情况）。
  - **答案估计与验证**：LLM利用其内部知识或检索增强生成（RAG）估计每个查询的答案，并对低置信度查询进行简化后重新估计。
  - **概率重组**：根据贝叶斯网络结构将各查询答案组合成数学公式，由Python解释器计算最终k值。
- **公式**：k = n × P(X1, X2, ..., Xj)，其中n为全球人口，P为联合概率，通过链式法则分解为条件概率的乘积。

## 3. 实验设计

- **数据集**：
  - 180个Reddit帖子（130个真实+50个合成）和40个真实用户-LLM对话（ShareGPT），总共220个文档，标注了gold标准k值。
  - 每个帖子由两名内部标注者识别披露类别、构建贝叶斯网络、计算k值，每篇帖子至少标注两次，确保一致性。
  - 另外收集了100个已知真实人口数量的兴趣组（来自人口普查和公立大学记录），用于验证标注方法的质量（平均百分比误差22.24%）。
- **Benchmark**：基线方法包括Few-Shot Prompting、Chain-of-Thought (CoT)、Program-of-Thought (PoT)等，使用GPT-4o、LLaMA-3.1-Instruct 8B/70B、GPT-4o-mini、o1-preview、DeepSeek-R1、o3-mini等不同模型。
- **评价指标**：Spearman秩相关ρ、Log Error（|log2(ˆk) - log2(k*)|）、Range%指标（预测值在gold standard的a倍范围内，a=5为主要报告值，也测试了a=2,10）。
- **对比方法**：包括多种模型和提示策略，以及BRANCH的多种变体（不同基座模型、全连接/全独立贝叶斯网络、去除子查询模块等），以及检索增强生成（RAG）系统（Google Search API + PerplexityAI产品）的对比。

## 4. 资源与算力

- 论文明确说明：使用4块A40 GPU进行LoRA微调，训练最多6小时每轮（10个epoch，总batch size=16）。
- 推理时使用采样解码，温度0.7；对于不确定性分析，重复运行5次。
- API调用成本：对于GPT-4o，每个文档的BRANCH pipeline平均调用约8-32次LLM，成本约$0.04-$0.24（取决于披露数量）。
- 未报告总训练时间或总计算量，但上述细节已提供。

## 5. 实验数量与充分性

- **实验数量**：包含了多组实验：
  - 主实验：对比10种以上方法（不同模型、提示策略）在三个指标上的性能，覆盖Reddit和ShareGPT两个域。
  - 消融实验：测试不同贝叶斯网络结构（全连接、全独立）、去除子查询模块、简化模块等。
  - 组件分析：单独评估LLM估计单个属性概率的准确性（平均百分比误差）和贝叶斯网络排序的一致性（Kendall's τ）。
  - 不确定性分析：通过多次采样评估预测方差与准确性的关系。
  - 检索增强生成对比：测试多种RAG系统（Google检索+不同数量的片段、PerplexityAI多种版本）。
  - 预测区间实验：构造k的预测区间并评估召回率和精确率。
- **充分性与公平性**：
  - 实验覆盖了多个基座模型（开源和闭源）、多种提示策略、不同输入复杂度（披露数量）。
  - 使用统计显著性检验（paired bootstrap test）比较BRANCH与对应CoT基线。
  - 消融实验控制变量，逐步验证核心组件的贡献。
  - 数据集经过双重标注和验证，确保gold标准质量。
  - 总体实验设计较全面，但未在真实用户场景中部署验证，属于实验室条件下的评估。

## 6. 论文的主要结论与发现

- BRANCH方法（o3-mini + GPT-4o）在隐私风险评估任务上显著优于所有基线，在72.61%的情况下预测k值在gold标准的一个数量级范围内（a=5），Log Error降至1.99，Spearman ρ达0.873，比最佳CoT基线（o3-mini CoT）的59.13%范围准确率高出13%以上。
- 对于包含4个及以上披露的复杂帖子，BRANCH优势更明显（范围准确率74.22% vs CoT的55.47%），说明贝叶斯网络分解能有效处理多属性交互。
- Chain-of-Thought的主要错误类型包括：条件依赖缺失（25.64%）、缺乏子查询（20.51%）、无法处理PII（15.38%）；而BRANCH的错误主要来自概率估计或属性选择（38.47%的CoT错误也源于此）。
- LLM预测的不确定性（方差）是准确性的良好指标：高方差预测的准确率低37.47%，可用于过滤不可靠结果。
- BRANCH在ShareGPT域（用户-LLM对话）上表现优于Reddit域，表明对含有严重隐私风险的文本具有更好的鲁棒性。
- 检索增强生成（RAG）系统未能显著超越BRANCH，因为生成的查询过于特定，71.30%的查询在前10个检索文档中找不到证据。

## 7. 优点

- **任务新颖且实用**：将隐私风险评估转化为可解释的数值推理任务，面向最终用户，具有实际应用价值（类似密码强度计）。
- **方法创新**：利用LLM构建贝叶斯网络进行概率分解，无需外部数据库，仅依赖LLM内部知识或检索，适合无完备数据库的场景。
- **全面的实验验证**：涵盖多种模型、提示策略、消融、不确定性分析、RAG对比，并使用统计显著性检验，结论可靠。
- **组件分析**：分别评估了概率估计能力和贝叶斯网络结构建模能力，揭示了BRANCH的优势来源。
- **开源数据集（部分）**：合成数据可公开，真实数据可申请，促进后续研究。

## 8. 不足与局限

- **数据集规模有限**：仅220个文档，且披露数量集中在3-6个，未测试更多披露的情况，可能限制泛化性。
- **域局限性**：主要基于Reddit和ShareGPT，未验证在Amazon评论、求职论坛等其他平台上的表现。
- **计算成本高**：BRANCH多步pipeline需要多次LLM调用，推理成本较高；虽然论文讨论了缓解方案，但未实际验证。
- **标注偏差与ground truth**：gold标准由人类标注，尽管验证了低误差，但完美ground truth在实际中难以获得，尤其对于罕见属性组合。
- **未进行用户研究**：模型未在真实用户场景中测试，用户如何理解和使用k值、是否改变行为尚不清楚。
- **潜在偏见风险**：未系统评估LLM内部人口统计知识对特定群体（如种族、性别、地域）的可能偏差，可能影响某些群体的隐私风险评估公平性。
- **威胁模型单一**：假设敌手知晓所有披露上下文，未考虑不同等级的敌手知识范围。

（完）
