---
title: "AutoML-Agent: A Multi-Agent LLM Framework for Full-Pipeline AutoML"
title_zh: AutoML-Agent：用于全流程自动机器学习的多智能体大语言模型框架
authors: "Patara Trirat, Wonyong Jeong, Sung Ju Hwang"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=p1UBWkOvZm"
tags: ["query:ai"]
score: 7.0
evidence: ICML 2025自动机器学习论文，使用大语言模型
tldr: 该论文提出AutoML-Agent，一个基于多智能体大语言模型的框架，通过自然语言接口自动化全流程AutoML。现有AutoML系统需要专业知识且耗时，而该方法利用LLM的能力，将多个智能体分别负责数据处理、模型选择和超参数调优，实现了端到端的自动化。实验表明在多个基准上显著降低了用户工作量并保持性能。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-p1ubwkovzm/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 854, \"height\": 516, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-p1ubwkovzm/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1779, \"height\": 792, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-p1ubwkovzm/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 863, \"height\": 227, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-p1ubwkovzm/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1780, \"height\": 981, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-p1ubwkovzm/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 848, \"height\": 263, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-p1ubwkovzm/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1749, \"height\": 468, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-p1ubwkovzm/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 863, \"height\": 279, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-p1ubwkovzm/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1783, \"height\": 578, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-p1ubwkovzm/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 871, \"height\": 486, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-p1ubwkovzm/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1768, \"height\": 1443, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-p1ubwkovzm/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1770, \"height\": 1535, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-p1ubwkovzm/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1783, \"height\": 639, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-p1ubwkovzm/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1787, \"height\": 604, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-p1ubwkovzm/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1787, \"height\": 708, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-p1ubwkovzm/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1785, \"height\": 605, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-p1ubwkovzm/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1780, \"height\": 688, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-p1ubwkovzm/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1782, \"height\": 811, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-p1ubwkovzm/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1777, \"height\": 279, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-p1ubwkovzm/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1784, \"height\": 766, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-p1ubwkovzm/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1786, \"height\": 762, \"label\": \"Table\"}]"
motivation: 现有AutoML系统需要专业知识且耗时，缺乏自然语言交互。
method: 构建多智能体LLM框架，每个智能体负责AutoML流水线的一个环节，通过对话协作。
result: 在多个基准上显著减少人工干预，同时保持或提升模型性能。
conclusion: AutoML-Agent使非专家也能轻松构建高效机器学习模型。
---

## Abstract
Automated machine learning (AutoML) accelerates AI development by automating tasks in the development pipeline, such as optimal model search and hyperparameter tuning. Existing AutoML systems often require technical expertise to set up complex tools, which is in general time-consuming and requires a large amount of human effort. Therefore, recent works have started exploiting large language models (LLM) to lessen such burden and increase the usability of AutoML frameworks via a natural language interface, allowing non-expert users to build their data-driven solutions. These methods, however, are usually designed only for a particular process in the AI development pipeline and do not efficiently use the inherent capacity of the LLMs. This paper proposes *AutoML-Agent*, a novel multi-agent framework tailored for full-pipeline AutoML, i.e., from data retrieval to model deployment. *AutoML-Agent* takes user's task descriptions, facilitates collaboration between specialized LLM agents, and delivers deployment-ready models. Unlike existing work, instead of devising a single plan, we introduce a retrieval-augmented planning strategy to enhance exploration to search for more optimal plans. We also decompose each plan into sub-tasks (e.g., data preprocessing and neural network design) each of which is solved by a specialized agent we build via prompting executing in parallel, making the search process more efficient. Moreover, we propose a multi-stage verification to verify executed results and guide the code generation LLM in implementing successful solutions. Extensive experiments on seven downstream tasks using fourteen datasets show that *AutoML-Agent* achieves a higher success rate in automating the full AutoML process, yielding systems with good performance throughout the diverse domains.

---

## 论文详细总结（自动生成）

# AutoML-Agent 论文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **问题**：现有自动机器学习（AutoML）系统虽能自动化模型搜索、超参数调优等流程，但仍需要用户具备编程和机器学习专业知识来配置复杂工具，费时费力，阻碍了非专业用户的使用。
- **现有LLM方法的局限**：近期利用大语言模型（LLM）的AutoML工作仅覆盖AI开发流水线的某一特定环节（如特征工程、超参数优化）或特定任务（如自然语言处理、计算机视觉），未实现端到端全流程自动化，且未充分利用LLM的推理与规划能力。
- **意义**：提出AutoML-Agent，旨在通过自然语言接口，让非专家用户从数据检索到模型部署全流程自动化，同时提高搜索效率和实现准确度。

## 2. 论文提出的方法论
- **核心思想**：构建一个多智能体LLM框架，包含多个角色化智能体（Agent Manager, Prompt Agent, Data Agent, Model Agent, Operation Agent），分工协作完成全流程AutoML。用户仅需提供任务描述，框架输出可部署模型。
- **关键技术细节**：
  - **检索增强规划（RAP）**：利用外部知识（网页搜索、论文摘要、Kaggle等）生成多个端到端规划方案，增强探索能力。
  - **角色特定的规划分解**：将全局规划分解为面向Data Agent和Model Agent的子任务，使智能体能聚焦自身职责。
  - **基于提示的执行（Promping-based Execution）**：智能体通过模拟执行（不实际训练）生成预期结果，如Data Agent进行伪数据分析，Model Agent进行模型搜索和超参数优化，避免开销。
  - **多阶段验证**：包括请求验证（检查用户指令清晰性）、执行验证（检查模拟结果是否符合需求）、实现验证（检查生成代码是否能运行并满足约束），若失败则进入修订循环。
  - **指令数据生成与提示解析**：使用EvolInstruct自动生成约2300条指令-响应对，微调Prompt Agent（Mixtral-8x7B）以将用户输入解析为标准化JSON（含User、Problem、Dataset、Model等字段）。
- **算法流程**（算法1）：
  1. 初始化阶段：请求验证 → 解析指令。
  2. 规划阶段：RAP生成P个规划（默认P=3）。
  3. 执行阶段：对每个规划，Data Agent和Model Agent并行执行分解后的子任务 → 组合结果。
  4. 验证与实现：执行验证通过后，选择最优规划，由Operation Agent编写Python代码，并通过实现验证，最终输出可部署模型。

## 3. 实验设计
- **任务与数据集**：覆盖5种数据模态（图像、文本、表格、时序、图），7个下游任务（图像分类、文本分类、表格分类/回归/聚类、时序预测、节点分类），共14个数据集（Butterfly, Shopee, Ecomm, Entail, Banana, Software, Crab, Crop, Smoker, Student, Weather, Electricity, Cora, Citeseer）。
- **评估指标**：
  - **SR（成功率）**：代码是否可执行、部署，约束自由和约束感知两种评分等级。
  - **NPS（归一化性能分数）**：对任务指标（准确率、F1、RMSLE等）进行转换，范围[0,1]。
  - **CS（综合分数）**：CS = 0.5×SR + 0.5×NPS。
- **对比方法**：
  - 人工设计模型（Human Models）
  - 传统AutoML（AutoGluon-TS/Tabular/Multimodal）
  - 通用LLM（GPT-3.5, GPT-4零样本）
  - LLM-based框架：DS-Agent, SELA（MCTS-based），Agent K
- **设置**：包含约束自由（无额外限制）和约束感知（带有精确度、延迟、训练时间等约束）两种场景。

## 4. 资源与算力
- **硬件**：Ubuntu 22.04 LTS服务器，配备8块NVIDIA A100 GPU（CUDA 12.4），Intel(R) Xeon(R) Platinum 8275CL CPU @ 3.00GHz。
- **模型**：除Prompt Agent使用Mixtral-8x7B（微调）外，所有智能体及LLM baseline均使用GPT-4 (gpt-4o-2024-05-13)。
- **时间与成本**：单次运行平均耗时约525秒（约束自由）和512秒（约束感知），成本约0.27–0.32美元（GPT-4o调用费用）。规划阶段（检索与规划）占主要时间（约187秒）。
- **微调**：使用LoRA在约2300条指令数据上训练Prompt Agent，计算资源未详细说明。

## 5. 实验数量与充分性
- **实验数量**：
  - 主实验：14个数据集 × 2种设置 × 5次独立运行，共140组实验（每个方法在每个设置下生成28个模型）。
  - 消融实验：3种变体（仅RAP, RAP+分解, 完整框架）在5个代表性任务上的比较。
  - 超参数研究：调整规划数量P=1,3,5。
  - 提示敏感性：5种系统提示变体测试。
  - 噪声鲁棒性：两种注入噪声场景。
  - 与SELA对比：6个表格数据集（难度不同）。
  - 与Agent K对比：8个Kaggle竞赛（覆盖无牌到金牌）。
- **充分性与客观性**：
  - 实验覆盖任务多样、数据集来源丰富（Kaggle、UCI、HuggingFace、研究数据集等）。
  - 使用多次独立运行并报告标准差，统计可靠性较好。
  - 对比方法包括传统AutoML、通用LLM及针对性baselines，较为全面。
  - 但部分baseline（如AutoGluon）仅适用于特定模态（图数据未包含），对比不完全公平；DS-Agent原为建模阶段设计，本文扩展了其部署阶段，但可能未完全公平。

## 6. 论文的主要结论与发现
- AutoML-Agent在约束自由和约束感知设置下均大幅优于所有baselines：平均SR=100%（约束自由），87.1%（约束感知）；平均CS=0.902（约束自由），0.841（约束感知）。
- 检索增强规划有效提升了搜索多样性，多阶段验证确保代码可运行并满足约束。
- 与训练型方法（SELA）相比，AutoML-Agent搜索速度快约8倍（249秒 vs 2037秒），性能相近或略优（平均CS 0.612 vs 0.599）。
- 通用LLM（GPT-4）在简单表格任务上尚可，但在复杂任务上易失败，证实了专门框架的必要性。
- 噪声鲁棒性实验表明，内置纠错和验证机制可有效缓解外部知识噪声影响。

## 7. 优点
- **全流程自动化**：从数据检索到模型部署一站式解决，用户仅需自然语言描述。
- **高效搜索**：采用检索增强规划+提示执行，避免实际训练，大幅降低计算开销，且能利用最新知识。
- **模块化与可扩展**：多智能体角色分离，易于替换或新增模块（如支持新任务需添加对应智能体）。
- **准确性保障**：多阶段验证（请求、执行、实现）与反馈循环，减少LLM幻觉和代码错误。
- **实验全面且可重复**：公开代码，实验设计覆盖多模态、多约束，统计严谨。

## 8. 不足与局限
- **骨架代码依赖**：对于全新任务，若缺少预设的流水线骨架脚本，代码生成可能产生幻觉。
- **强LLM骨干依赖**：当前版本依赖GPT-4，使用小模型（如GPT-3.5）时性能急剧下降，未来需增强与弱模型的兼容性。
- **任务覆盖局限**：未覆盖强化学习、推荐系统等特殊领域，扩展需额外开发智能体。
- **安全与隐私风险**：集成外部API（检索、LLM调用）可能泄露用户数据；LLM生成代码存在潜在恶意输出风险（如生成对抗性内容），建议在隔离环境（如Docker）中运行。
- **噪声鲁棒性分析**：仅测试了两种简单注入场景，实际中噪声可能更复杂。
- **基线公平性**：DS-Agent设计用于建模阶段而非全流程，本文扩展其部署阶段但未完全对齐；AutoGluon在全流程中不支持图数据；Human Models来自第三方基准，与本文环境不完全一致。

（完）
