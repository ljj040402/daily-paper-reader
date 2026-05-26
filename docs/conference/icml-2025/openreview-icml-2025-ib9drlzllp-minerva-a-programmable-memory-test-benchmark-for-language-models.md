---
title: "Minerva: A Programmable Memory Test Benchmark for Language Models"
title_zh: Minerva：语言模型可编程记忆测试基准
authors: "Menglin Xia, Victor Rühle, Saravan Rajmohan, Reza Shokri"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=ib9drlZllP"
tags: ["query:ai"]
score: 6.0
evidence: ICML 2025关于评估大语言模型记忆能力的论文
tldr: 该论文提出Minerva，一个可编程的LLM记忆测试基准自动生成框架。针对现有静态基准易过拟合且缺乏可解释性的问题，Minerva自动生成涵盖多种原子记忆任务的测试集，超越传统的needle-in-haystack测试。实验揭示了不同LLM在记忆能力上的具体缺陷，为模型改进提供了方向。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-ib9drlzllp/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 711, \"height\": 662, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ib9drlzllp/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 774, \"height\": 496, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ib9drlzllp/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 839, \"height\": 414, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ib9drlzllp/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 840, \"height\": 415, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ib9drlzllp/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 760, \"height\": 579, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ib9drlzllp/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 853, \"height\": 444, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-ib9drlzllp/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1650, \"height\": 2046, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ib9drlzllp/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 859, \"height\": 357, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ib9drlzllp/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 697, \"height\": 389, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ib9drlzllp/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1600, \"height\": 489, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ib9drlzllp/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 613, \"height\": 426, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ib9drlzllp/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 819, \"height\": 427, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ib9drlzllp/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 694, \"height\": 213, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ib9drlzllp/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 754, \"height\": 193, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ib9drlzllp/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 731, \"height\": 215, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ib9drlzllp/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 732, \"height\": 196, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ib9drlzllp/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1644, \"height\": 2120, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ib9drlzllp/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1644, \"height\": 2149, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ib9drlzllp/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1642, \"height\": 2026, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ib9drlzllp/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1646, \"height\": 1869, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ib9drlzllp/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1627, \"height\": 141, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ib9drlzllp/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1621, \"height\": 536, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ib9drlzllp/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1641, \"height\": 773, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ib9drlzllp/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1777, \"height\": 431, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ib9drlzllp/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1782, \"height\": 2538, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ib9drlzllp/table-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1781, \"height\": 464, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ib9drlzllp/table-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1764, \"height\": 539, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ib9drlzllp/table-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 893, \"height\": 233, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ib9drlzllp/table-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 908, \"height\": 233, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ib9drlzllp/table-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 906, \"height\": 235, \"label\": \"Table\"}]"
motivation: 现有LLM记忆基准静态、易过拟合且缺乏可操作见解。
method: 自动生成多样化原子记忆测试任务，评估模型上下文利用能力。
result: 揭示了不同LLM在记忆任务上的具体短板。
conclusion: Minerva为LLM记忆评估提供了更全面和诊断性的工具。
---

## Abstract
How effectively can LLM-based AI assistants utilize their memory (context) to perform various tasks? Traditional data benchmarks, which are often manually crafted, suffer from several limitations: they are static, susceptible to overfitting, difficult to interpret, and lack actionable insights--failing to pinpoint the specific capabilities a model lacks when it does not pass a test. In this paper, we present a framework for automatically generating a comprehensive set of tests to evaluate models' abilities to use their memory effectively. Our framework extends the range of capability tests beyond the commonly explored (passkey, key-value, needle in the haystack) search, a dominant focus in the literature. Specifically, we evaluate models on atomic tasks such as searching, recalling, editing, matching, comparing information in context memory, performing basic operations when inputs are structured into distinct blocks, and maintaining state while operating on memory, simulating real-world data. Additionally, we design composite tests to investigate the models' ability to perform more complex, integrated tasks. Our benchmark enables an interpretable, detailed assessment of memory capabilities of LLMs.

---

## 论文详细总结（自动生成）

# Minerva：语言模型可编程记忆测试基准 —— 详细总结

## 1. 核心问题与整体含义（研究动机与背景）

- **问题**：大语言模型（LLM）在作为 AI 助理时，需要有效利用其输入上下文（记忆）来执行各种任务。然而，现有的数据基准（如静态 QA 数据集）存在多个缺陷：静态性、易过拟合、缺乏可解释性、无法定位模型在哪些具体能力上失败。
- **背景**：已有的自动测试（如 Needle-in-a-Haystack、Key-Value 检索）过于集中于简单搜索能力，忽略了更复杂的记忆利用能力，例如编辑、匹配、比较、状态跟踪、跨块处理等。
- **核心含义**：需要一种可编程、可随机生成、可诊断的基准，能够系统地、原子地评估 LLM 在记忆利用上的各项子能力，并为模型改进提供可操作的见解。

## 2. 方法论：核心思想、关键技术细节、算法流程

### 核心思想
- 将 LLM 的记忆利用能力拆解为一系列 **原子测试**（atomic tests），每个测试只评估一种基本能力（如搜索、回忆、编辑、匹配、计数、集合操作、状态跟踪）。
- 同时设计 **复合测试**（composite tests），组合多种原子能力来模拟真实场景（如跨数据块处理、多智能体状态跟踪）。
- 所有测试通过 **可编程脚本** 自动生成随机化的测试案例，支持调整超参数（如上下文长度、查询深度、操作步数等）来控制难度。

### 关键技术细节
- **原子测试类型**（共 6 大类）：
  - **Search**：字符串搜索（单词/子序列）、键值搜索、批量搜索。
  - **Recall and Edit**：完整快照、全局替换、位置覆盖、函数更新（如对每个数字加 3）。
  - **Match and Compare**：位置比较、找重复、计数、关联检查。
  - **Spot the Differences**：两列表比较、找不同组、序列补全。
  - **Compute on Sets and Lists**：组归属、组关联、交替组关联、迭代（返回每个列表最后一个元素）。
  - **Stateful Processing**：数量状态跟踪（加减运算）、集合状态跟踪（添加/移除物品）。
- **复合测试类型**：
  - **Processing Data Blocks**：交替标记的列表块，要求对指定标签的列表进行检索和编辑。
  - **Composite-State Tracking (Theory of Mind)**：多智能体同时进行添加/移除/交换操作，最终报告每个智能体的状态。
- **生成流程**：使用参数化模板，上下文词汇从英语词典均匀采样，指令部分包含占位符。测试案例数、指标、超参数均在附录中明确（见表10）。

### 算法/流程说明（非公式）
1. 对于每个测试类别，定义模板和可调超参数（如上下文长度、目标位置、操作步数）。
2. 随机生成上下文（如单词列表、键值对、操作序列）。
3. 生成对应的指令（如“在上下文中，单词 xxx 是否出现？”）。
4. 将上下文和指令拼接为模型输入，收集模型输出。
5. 使用精确匹配（Exact Match）、ROUGE-L、Jaccard 相似度等指标自动打分。
6. 支持批量运行，可重复生成不同随机种子下的测试集。

## 3. 实验设计

### 数据集/场景
- **自建测试集**：固定快照包含 **1110 个随机生成样本**，覆盖所有原子和复合测试类别（具体分布见附录 B）。
- **上下文长度**：多数测试固定为 **4k tokens**（Stateful Processing 任务约 1.5k tokens）。
- **评估指标**：二进制任务用 Exact Match；序列重叠用 ROUGE-L；集合重叠用 Jaccard 相似度。

### Benchmark
- 提出的 **Minerva 基准** 本身是唯一的测试框架，没有使用现有基准（如 LongBench、RULER）进行直接对比，但通过与已有测试（NIAH、Key-Value 等）的比较来说明其更全面的覆盖范围。

### 对比的方法（模型）
- **闭源模型**：GPT-4-turbo、GPT-4o、GPT-4o-mini、Cohere-command-rplus。
- **开源模型**：Mistral-7b-instruct-v02、Phi-3-small-128k-instruct (7B)、LLaMA-3.1-8b-instruct、Gemma-2-9b、Phi-3-medium-128k-instruct (14B)。
- 推理设置：max output tokens = 4096，temperature = 0，top_p = 1。

### 对比策略
- 不与其他基准直接比较（因为 Minerva 是全新测试框架），而是通过在不同能力类别上的性能差异来揭示模型短板。
- 进行了多项消融研究：gibberish 上下文（去除语义）、上下文长度变化、提示措辞变化、操作步数变化。

## 4. 资源与算力

- **文中未明确说明使用的 GPU 型号、数量或训练时长**。论文主要关注推理评估（而非训练），因此算力需求未作专门阐述。但可以推断推理测试可在普通 GPU（如 A100 或 V100）上完成，对开源模型推理需要一定的计算资源。

## 5. 实验数量与充分性

### 实验数量
- 全文呈现 **1110 个测试样本** 的评估结果，其中：
  - 搜索类：200 个
  - 回忆与编辑：105 个
  - 匹配与比较：175 个
  - 找差异：260 个
  - 集合与列表计算：210 个
  - 状态跟踪：50 个
  - 复合测试：110 个
- 每组测试覆盖多种超参数（如查询深度、序列长度、操作步数），每个参数组合至少 5 个样本。
- 额外进行了 **上下文长度消融**（500~32K）、**提示措辞消融**（2 种变体）、**gibberish 消融**（将语义词替换为乱码）、**操作步数消融**（50~1600 步）。

### 充分性与客观性评价
- **充分性**：测试覆盖了 6 大类原子能力 + 2 类复合能力，比以往仅关注搜索的基准更全面。消融实验验证了语义不是主要干扰（gibberish 实验），并展示了长度和提示变化的影响，说明结果稳健。
- **客观性**：使用固定随机种子快照，保证可复现；评估指标明确（Exact Match、ROUGE-L、Jaccard）。模型推理设置统一（temperature=0），最小化随机性。
- **潜在不足**：所有测试仅基于 4k tokens（除状态跟踪外），尽管作者声称 4k 已能暴露问题，但更长上下文（如 128k）下模型表现未知。复合测试数量较少（仅 110 个样本），可能统计显著性不足。

## 6. 主要结论与发现

1. **搜索能力并不代表全面记忆利用能力**：模型在简单搜索任务上表现良好（如字符串搜索、键值搜索），但在其他原子能力（如计数、编辑、集合操作、状态跟踪）上表现急剧下降，即使上下文仅 4k tokens。
2. **状态跟踪是当前模型最大短板**：GPT-4（o）在整数状态跟踪上尚可，其他模型几乎为零；集合状态跟踪表现稍好但仍有较大差距。操作步数增加后，所有模型性能迅速退化。
3. **复合测试挑战巨大**：即使最强模型（GPT-4-turbo、GPT-4o）在复合测试（数据处理块、心理理论）上得分低于 0.4，说明组合多种能力使任务难度远超单个原子测试。
4. **不同模型存在不同错误模式**：例如在子序列搜索中，GPT-4o 倾向假阳性，Phi-3-medium 倾向假阴性，暗示不同搜索策略。
5. **模型大小不是唯一因素**：8B 的 LLaMA-3.1 在“找不同组”任务上超越 GPT-4o，表明架构或训练数据差异也有重要影响。
6. **语义干扰不大**：gibberish 替换后性能几乎不变，说明模型主要依赖位置和匹配模式而非语义理解。
7. **参数提示变化影响有限**：轻微措辞变化对多数任务无显著影响，但更大幅度的指令改变（如“检查关联”任务）可能引起差异。

## 7. 优点

- **可编程性与动态性**：所有测试由脚本自动生成，支持随机化，可灵活调整难度（上下文长度、符号数量等），避免静态基准的过拟合问题。
- **原子化诊断**：将记忆利用分解为可解释的微小能力，精准定位模型失败的具体原因（如无法计数、无法维护状态）。
- **复合测试设计**：模拟真实多步交互场景（如多智能体信息交换），揭示了更复杂的局限性。
- **开源与可扩展**：代码和数据将公开，支持社区添加新测试类别。
- **消融实验扎实**：验证了语义、上下文长度、提示措辞等因素的影响，增强了结论的可靠性。
- **跨模型分析细致**：覆盖多个主流开源与闭源模型，并区分了错误类型（假阳性 vs 假阴性）。

## 8. 不足与局限

- **上下文长度范围有限**：主实验只测了 4k tokens（状态跟踪 1.5k），虽然作者强调短上下文已暴露问题，但实际应用中 LLM 常需处理 32k~128k 甚至更长上下文，该基准无法评估长上下文下的记忆能力衰减情况（附录中仅对少数任务展示了更长长度下的趋势，但不全面）。
- **测试样本量较小**：每个超参数组合仅 5~10 个样本，部分测试（如复合测试）仅有 50~60 个样本，可能导致统计波动；评估指标单一（仅 Exact Match/ROUGE-L/Jaccard），未使用更丰富的语义相似度度量。
- **未覆盖复杂推理能力**：作者刻意排除数学推理、逻辑推理等能力，但实际应用中记忆利用常与推理交织，单独评估可能低估模型真实表现。
- **潜在 prompt 敏感性**：虽然提示变化影响有限，但仅测试了 2 种变体，更广泛的 prompt 工程可能改变结果；且所有测试使用简洁直白指令，未探索链式思考（CoT）或其他增强方法。
- **数据集局限性**：上下文全部由随机英语单词构成，缺乏自然语言语义结构（如对话、故事、表格），与现实应用场景有差距；虽然 gibberish 实验排除语义干扰，但也意味着测试未涉及语义理解带来的挑战。
- **计算资源未说明**：没有报告推理成本或环境，不利于其他研究者复现。
- **静态快照风险**：虽然测试可随机生成，但论文中所有结果基于同一固定快照（1110 个样本），若该快照存在偏向（例如某类测试样本过少），结论可能不稳健（作者未提供多快照交叉验证结果）。
- **缺乏与现有基准的公平对比**：未在 Minerva 与 I NeedleBench、RULER 等基准上同时评估模型，因此无法说明 Minerva 比它们更能揭示模型差异；只通过定性对比凸显新颖性。

（完）
