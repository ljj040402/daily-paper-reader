---
title: "MLE-STAR: Machine Learning Engineering Agent via Search and Targeted Refinement"
title_zh: MLE-STAR：通过搜索与目标细化的机器学习工程智能体
authors: "Jaehyun Nam, Jinsung Yoon, Jiefeng Chen, Jinwoo Shin, Sercan O Arik, Tomas Pfister"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=vS1M06Px6u"
tags: ["query:ai"]
score: 7.0
evidence: 基于搜索和细化的机器学习工程智能体
tldr: 本文提出MLE-STAR，一种基于大语言模型的机器学习工程智能体。通过搜索引擎获取外部知识形成初始方案，再通过迭代细化深入探索特定组件（如特征工程），克服了现有方法依赖固有知识或粗粒度探索的局限。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-vs1m06px6u/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1131, \"height\": 226, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vs1m06px6u/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1435, \"height\": 942, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vs1m06px6u/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1430, \"height\": 301, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vs1m06px6u/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 669, \"height\": 494, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vs1m06px6u/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 710, \"height\": 549, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vs1m06px6u/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 661, \"height\": 516, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vs1m06px6u/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 711, \"height\": 547, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vs1m06px6u/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 548, \"height\": 470, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-vs1m06px6u/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1442, \"height\": 649, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-vs1m06px6u/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 735, \"height\": 239, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-vs1m06px6u/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 679, \"height\": 238, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-vs1m06px6u/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1443, \"height\": 427, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-vs1m06px6u/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1305, \"height\": 238, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-vs1m06px6u/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1443, \"height\": 240, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-vs1m06px6u/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 479, \"height\": 167, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-vs1m06px6u/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 557, \"height\": 171, \"label\": \"Table\"}]"
motivation: 现有LLM驱动的MLE智能体依赖内在知识和粗探索，效果受限。
method: 结合搜索检索有效模型，并迭代细化代码组件。
result: 在多个ML任务上优于现有MLE智能体。
conclusion: 为自动化机器学习工程提供了更有效的智能体范式。
---

## Abstract
Agents based on large language models (LLMs) for machine learning engineering (MLE) can automatically implement ML models via code generation. However, existing approaches to build such agents often rely heavily on inherent LLM knowledge and employ coarse exploration strategies that modify the entire code structure at once. This limits their ability to select effective task-specific models and perform deep exploration within specific components, such as experimenting extensively with feature engineering options. To overcome these, we propose MLE-STAR, a novel approach to build MLE agents. MLE-STAR first leverages external knowledge by using a search engine to retrieve effective models from the web, forming an initial solution, then iteratively refines it by exploring various strategies targeting specific ML components. This exploration is guided by ablation studies analyzing the impact of individual code blocks. Furthermore, we introduce a novel ensembling method using an effective strategy suggested by MLE-STAR. Our experimental results show that MLE-STAR achieves medals in 64% of the Kaggle competitions on the MLE-bench, significantly outperforming the best alternative.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **研究动机**：现有基于大语言模型（LLM）的机器学习工程（MLE）智能体在自动生成ML模型代码时，严重依赖LLM的内在知识，且采用粗粒度的探索策略（一次性修改整个代码结构）。这导致两个问题：① 容易偏向常见但可能过时的方法（如对表格数据总是使用scikit-learn），忽略任务特定的最新模型；② 缺乏对某个具体组件（如特征工程）进行深度迭代探索的能力，过早地切换优化目标（如模型选择或超参数调参）。
- **整体含义**：本文提出MLE-STAR，一种通过**搜索引擎获取外部知识**（检索有效模型）并结合**目标性代码块细化**（通过消融研究定位关键组件并进行深度迭代优化）的MLE智能体，旨在克服上述局限，提升自动化ML工程的效果。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程
- **核心思想**：  
  MLE-STAR分为三阶段：  
  1. **初始化**：利用搜索引擎（如Google Search）检索任务相关的有效模型及其示例代码，生成多个候选脚本，通过评估和合并得到初始解。  
  2. **迭代细化**：通过外循环（outer loop）和内循环（inner loop）结合的方式，逐步改进解。外循环中，通过消融研究分析每个ML组件的影响，选出影响力最大的代码块作为目标；内循环中，针对该代码块，由LLM提出多种细化方案并评估，保留最优方案。  
  3. **集成（Ensemble）**：对多个并行运行得到的解，由LLM自主提出集成策略（如加权平均、投票等），并迭代优化集成方案，最终输出集成后的解。
- **关键技术细节**：  
  - 候选模型检索：`{T_model_i, T_code_i}_i^M = A_retriever(T_task)`，然后对每个模型生成脚本并评估，按得分排序，依次合并（`s0 ← A_merger(s0, s^(k))`），直到评分不再提升。  
  - 消融研究提取目标代码块：`at = A_abl(st, {T_abl^i}^{t-1}_{i=0})`，执行后得到结果`rt`，并总结为`T_abl^t`。提取器`A_extractor`根据`T_abl^t`和已细化过的代码块历史，选择最具影响力的代码块`ct`，同时生成初始细化计划`p0`。  
  - 代码块细化内循环：对于计划`pk`，编码器生成`s_kt`，评估后记录。`pk = A_planner(ct, {(pj, h(s_jt))}_{j=0}^{k-1})`。遍历K个计划后，选取最优作为`st+1`。  
  - 集成方法：从L个候选解中，由`A_ens_planner`提出首个计划`e0`，经评估后，迭代R轮（`er = A_ens_planner({sl}_L, {(ej, h(s_j_ens))}_{j=0}^{r-1})`），最终选择表现最好的集成结果。  
  - 附加模块：调试代理（A_debugger）、数据泄漏检查器（A_leakage）、数据使用检查器（A_data），分别用于修复执行错误、防止训练集泄露测试集信息、确保使用所有提供的数据源。
- **公式/算法流程**（文字说明）：  
  输入：任务描述`T_task`、数据集`D`。  
  1. 通过搜索检索M个模型，生成候选脚本并评估，合并得到初始解`s0`。  
  2. 外循环T轮：  
     a. 生成消融研究脚本`at`，执行并总结。  
     b. 提取目标代码块`ct`及初始计划`p0`。  
     c. 内循环K轮：  
        - 根据计划生成细化代码块，替换后评估。  
        - 更新计划（根据历史尝试）。  
     d. 选择最优细化方案，更新`st`。  
  3. 集成阶段：并行生成L个最终解（重复步骤1-2），然后迭代R轮探索集成策略，输出最终集成解。

## 3. 实验设计：数据集/场景、benchmark、对比方法
- **数据集/场景**：使用 **MLE-bench Lite** 中的22个Kaggle竞赛，涵盖分类、回归、图像去噪、文本、音频等多种模态和任务类型。
- **Benchmark**：主要基于MLE-bench（由22个Kaggle竞赛组成），评估指标包括提交率、有效提交率、高于中位数率、获得铜/银/金牌率、任何奖牌率等。同时，额外使用4个表格分类任务（与DS-Agent对比）。
- **对比方法**：  
  - 主要基线：**AIDE**（最先进的MLE智能体，使用多种LLM如Gemini-2.0-Flash、o1-preview、GPT-4o、Llama-3.1-405B、Claude-3.5-Sonnet）。  
  - 其他基线：MLAB、OpenHands（均使用GPT-4o）。  
  - 特定对比：DS-Agent（需人工构建案例库，仅在4个表格任务上对比）；AutoGluon（经典AutoML方法，见附录）。

## 4. 资源与算力
- **未明确说明具体GPU型号和数量**。论文提到设置最大24小时时间限制以公平比较，并在附录F（计算分析）中提及计算成本。使用Gemini-2.0-Flash时，每个ML挑战的成本约$0.24。未说明训练/推理使用的具体硬件细节。

## 5. 实验数量与充分性
- **实验数量**：  
  - 主实验：22个Kaggle竞赛，每种方法重复3种子（MLE-STAR Gemini-2.5-Pro和Gemini-2.0-Flash；AIDE各LLM有不同种子数，如o1-preview用16种子，GPT-4o用36种子）。  
  - 与DS-Agent对比：4个表格任务，5种子。  
  - 消融实验：  
    - 集成策略对比（包括None、Best-of-N、平均集成、本文方法）。  
    - 组件消融（有无目标细化/搜索工具）。  
    - 高级推理模型（Gemini-2.5-Pro vs Gemini-2.0-Flash）。  
    - Claude-Sonnet-4验证通用性（4个任务，3种子）。  
    - 集成轮数敏感性分析（4个任务）。  
  - 另有人工干预实验、数据泄漏检查器/数据使用检查器效果示例。  
  - 总体实验覆盖了多个模态、多个模型、多个种子，**较为充分**。
- **公平性**：  
  - 与AIDE对比时，均使用相同或类似的LLM版本（如Gemini-2.0-Flash）。  
  - 时间限制相同（24小时）。  
  - 论文指出DS-Agent需人工构建案例库，无法直接在所有任务比较，但选择了其原始任务进行公平对比。  
  - 使用Dolos检测抄袭，确保解决方案新颖性。

## 6. 论文的主要结论与发现
- MLE-STAR在MLE-bench Lite上**显著优于所有基线**：  
  - 使用Gemini-2.5-Pro时，任何奖牌率达到**63.6%**（其中金牌36.4%），而最佳基线AIDE（o1-preview）仅36.6%。  
  - 即使使用便宜的Gemini-2.0-Flash，MLE-STAR也达到43.9%奖牌率，远高于AIDE（Gemini-2.0-Flash）的25.8%。  
- 各组件均有效：搜索工具和针对性细化均能提升性能；集成策略优于简单选择最优或平均集成。  
- MLE-STAR能自动选择更先进的模型（如EfficientNet、ViT），而AIDE偏好过时的ResNet。  
- 数据泄漏检查器和数据使用检查器能有效修正LLM生成的代码错误，防止性能坍塌。

## 7. 优点：方法或实验设计上的亮点
- **方法创新**：  
  - 引入搜索引擎作为外部知识源，打破LLM内在知识局限，使模型选择更符合任务最新进展。  
  - 通过消融研究精准定位影响最大的代码块，进行深度细化，避免盲目全局修改。  
  - 自动探索集成策略，而非固定规则，能发现更有效的组合方式。  
  - 附加模块（调试、泄漏检查、数据使用检查）提高了鲁棒性。
- **实验设计亮点**：  
  - 使用标准化的MLE-bench基准，包含多模态任务，评估全面。  
  - 与多种最新基线（AIDE、MLAB、OpenHands、DS-Agent）对比，并控制LLM类型。  
  - 多组消融实验验证各组件贡献。  
  - 分析模型使用分布、错误案例、渐进改进轨迹，展示实际行为。  
  - 进行了抄袭检测，保证解决方案原创性。

## 8. 不足与局限
- **成本较高**：由于需要多次LLM调用（搜索、多个候选、内外循环、集成），计算成本高于简单基线（如AIDE）。论文提到使用Gemini-2.0-Flash时每个挑战约$0.24，但更高级模型或更多轮次可能更贵。
- **实验覆盖**：虽然包含22个Kaggle竞赛，但仍有限，可能无法完全代表各种真实ML任务。部分实验仅使用4个任务做敏感性分析。
- **对LLM性能依赖**：MLE-STAR的性能高度依赖于底层LLM的推理和编码能力；当LLM较弱时，搜索和细化效果可能受限。论文显示了用更强模型（Gemini-2.5-Pro）效果更好，但也意味着成本更高。
- **潜在过拟合风险**：由于Kaggle竞赛可能已存在于LLM训练数据中（尽管论文通过了抄袭检测和LLM作为裁判的新颖性评估），仍不能完全排除污染影响。
- **集成策略探索**：集成轮数固定（R=5），未充分探讨不同轮数对效果的权衡。
- **应用限制**：需要联网搜索（可能在某些环境受限）；对于高度新颖或非公开领域的任务，搜索可能无效。此外，数据泄漏检查器等模块可能无法覆盖所有形式的泄漏。

（完）
