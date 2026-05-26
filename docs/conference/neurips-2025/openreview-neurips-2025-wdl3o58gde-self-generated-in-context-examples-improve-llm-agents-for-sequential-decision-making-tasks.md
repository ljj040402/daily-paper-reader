---
title: Self-Generated In-Context Examples Improve LLM Agents for Sequential Decision-Making Tasks
title_zh: 自生成上下文示例提升LLM智能体序列决策能力
authors: "Vishnu Sarukkai, Zhiqiang Xie, Kayvon Fatahalian"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=WdL3O58gde"
tags: ["query:ai"]
score: 6.0
evidence: LLM智能体决策
tldr: "该论文提出一种无需人工干预的方法：LLM智能体通过自动收集自身成功轨迹作为上下文示例来改进。在ALFWorld、Wordcraft和InterCode-SQL三个基准上分别获得16%、9%和4%的性能提升，优于手动示例工程。"
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-wdl3o58gde/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 515, \"height\": 383, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wdl3o58gde/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1439, \"height\": 390, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wdl3o58gde/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1439, \"height\": 392, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wdl3o58gde/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1438, \"height\": 396, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wdl3o58gde/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 931, \"height\": 420, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wdl3o58gde/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 924, \"height\": 456, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wdl3o58gde/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 465, \"height\": 451, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-wdl3o58gde/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1453, \"height\": 667, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wdl3o58gde/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1321, \"height\": 796, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wdl3o58gde/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1453, \"height\": 291, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wdl3o58gde/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1171, \"height\": 368, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wdl3o58gde/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1453, \"height\": 977, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wdl3o58gde/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1275, \"height\": 214, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wdl3o58gde/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1565, \"height\": 213, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wdl3o58gde/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1447, \"height\": 173, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wdl3o58gde/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1170, \"height\": 215, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wdl3o58gde/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1181, \"height\": 214, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wdl3o58gde/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1315, \"height\": 409, \"label\": \"Table\"}]"
motivation: LLM智能体提升通常需要大量任务特定知识和人工示例，本文旨在实现自动从自身经验中学习。
method: 构建并不断精炼一个包含成功轨迹的数据库，作为未来任务的上下文示例。
result: 即使简单累积成功轨迹，也在三个基准上显著提升性能，超过手动示例工程的效果。
conclusion: 自生成示例为LLM智能体提供了一种可扩展的自动改进途径。
---

## Abstract
Improving Large Language Model (LLM) agents for sequential decision-making tasks typically requires extensive task-specific knowledge engineering—custom prompts, curated examples, and specialized observation/action spaces. We investigate a different approach where agents automatically improve by learning from their own successful experiences without human intervention. Our method constructs and refines a database of self-generated trajectories that serve as in-context examples for future tasks. Even naive accumulation of successful trajectories yields substantial performance gains across three diverse benchmarks: ALFWorld (73\% to 89\%), Wordcraft (55\% to 64\%), and InterCode-SQL (75\% to 79\%). These improvements exceed those achieved by upgrading from gpt-4o-mini to gpt-4o and match the performance of allowing multiple attempts per task. We further enhance this approach with two innovations: database-level curation using population-based training to propagate high-performing example collections, and exemplar-level curation that selectively retains trajectories based on their empirical utility as in-context examples. With these enhancements, our method achieves 93\% success on ALFWorld—surpassing approaches that use more powerful LLMs and hand-crafted components. Our trajectory bootstrapping technique demonstrates that agents can autonomously improve through experience, offering a scalable alternative to labor-intensive knowledge engineering.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机与背景）

- **问题**：提升LLM智能体在序列决策任务上的性能通常需要大量人工知识工程——定制提示、人工编排的上下文示例、专门的观察/动作空间设计。这种依赖人工扩展的方式成本高且不可持续。
- **动机**：探索一种替代路径——让LLM智能体**自主地从自身成功经验中学习**，通过积累和优化自生成的轨迹数据库，实现无需人工干预的自动性能提升。
- **整体含义**：自生成的上下文示例可以成为可扩展的替代方案，其效果甚至超越使用更强LLM或手工组件的复杂方法。

## 2. 方法论

### 核心思想
采用ReAct风格智能体（Alg. 1），结合动态检索机制，在每个决策点根据当前状态检索最相关的过往轨迹片段作为上下文示例。核心创新在于**如何构建和精炼存储这些轨迹的数据库**，使其包含高质量、高价值的示例。

### 关键技术细节
- **Traj-Bootstrap基础方法**：从少量人工轨迹开始，智能体尝试训练任务，仅将成功轨迹（s=1）存入数据库。形成正反馈循环：成功示例帮助解决新任务，产生更多成功示例。
- **+DB-Curation（数据库级筛选）**：针对Traj-Bootstrap性能波动问题，引入群体化训练（Alg. 2）。维护N个并行数据库实例，定期评估各实例在最近任务上的表现，用最佳数据库替换最差数据库，传播高质量的整体集合。
- **+Exemplar-Curation（示例级筛选）**：认识到即使低性能数据库也可能包含高质量轨迹，提出基于**检索加权质量指标Q(τ)** 筛选单个轨迹：
  \[
  Q(\tau) = \frac{\sum_{i \in R(\tau)} o_i \cdot f_i(\tau)}{\sum_{i \in R(\tau)} f_i(\tau)}
  \]
  其中R(τ)是检索到轨迹τ的任务集，o_i是任务i结果，f_i(τ)是检索频率。根据该指标为每个任务选择最佳成功轨迹，构建复合数据库。
- **组合方法**：+DB+Exemplar-Curation同时应用两种筛选。

### 算法流程（文字说明）
1. 初始化数据库D（含少量人工示例）。
2. 智能体按Alg. 1执行训练任务：先规划，再逐步推理-动作，每一步检索最相似的轨迹片段。
3. 若成功，将轨迹加入数据库（仅Traj-Bootstrap）。
4. 对于+DB-Curation，每隔一定任务数（按2的幂次增长）评估各数据库性能，淘汰最差并复制最佳。
5. 对于+Exemplar-Curation，训练结束后计算所有轨迹的Q值，为每个训练任务保留Q值最高的轨迹存入最终数据库。

### 关键区别
- 训练阶段需额外算力（N倍并行），但推理阶段成本与基线相同，不增加测试时计算。
- 方法无需任务特定提示、观测空间或动作空间设计，仅依赖自生成轨迹。

## 3. 实验设计

### 数据集/场景与Benchmark
| Benchmark | 描述 | 任务数（训练/测试） | 最大步数 |
|-----------|------|-------------------|----------|
| **ALFWorld** | 文本环境，导航与物体操作（6类任务） | 3500/134 | 30步 |
| **InterCode-SQL** | 交互式SQL查询生成 | 800/234 | 10步 |
| **Wordcraft** | 组合元素创造新元素（简化版Little Alchemy） | 4000/500 | 4步 |

- 三个Benchmark覆盖不同推理挑战，且均采用**稀疏奖励**（仅最终成功/失败），训练集与测试集严格分离。

### 对比方法
| 方法类别 | 具体方法 | 说明 |
|----------|----------|------|
| **基线** | Fixed-DB | 固定人工示例，不增长数据库 |
| **自改进基础** | Traj-Bootstrap | 简单累积成功轨迹 |
| **数据库级筛选** | +DB-Curation | 群体训练算法 |
| **示例级筛选** | +Exemplar-Curation | 基于Q值选择轨迹 |
| **组合** | +DB+Exemplar-Curation | 两者结合 |
| **外部对比** | Autoguide | 层次化规则学习（gpt-3.5+gpt-4） |
| **外部对比** | AutoManual | 手工观测/动作空间（gpt-4o-mini/gpt-4） |
| **测试时扩展** | Fixed-DB@k | 多次尝试（k=2~5） |
| **模型升级** | Fixed-DB with gpt-4o | 改用更强LLM |
| **微调** | ReAct-Finetune | 在自收集数据上微调GPT-4o-mini |
| **跨模型** | Mixtral 8x7B | 使用GPT-4o-mini收集的数据库测试泛化 |

- 所有方法均使用**GPT-4o-mini**作为默认基础模型（温度0.1），实验重复5次随机种子报告平均值和标准差。

## 4. 资源与算力

- **GPU**：1块NVIDIA A5000（24GB显存）用于嵌入计算（all-MiniLM-L6-v2）。
- **RAM**：64GB。
- **API调用**：主要算力消耗在OpenAI API调用。约需200万次（ALFWorld）、20万次（InterCode-SQL）、50万次（Wordcraft）。
- **总API成本**：约3,000美元。
- **数据库构建成本（最坏情况）**：
  - ALFWorld：17,500次episode（5个并行数据库×3,500），约595美元。
  - InterCode-SQL：4,000次episode（5×800），约64美元。
  - Wordcraft：20,000次episode（5×4,000），约120美元。
- **推理成本**：每个任务ALFWorld约0.034美元，InterCode-SQL约0.016美元，Wordcraft约0.006美元。
- **算力细节**：论文明确说明GPU型号、内存、成本，但未提供训练时长（如天数）。非GPU密集型，主要依赖API。

## 5. 实验数量与充分性

### 实验数量
- **主要比较**：3个Benchmark × 7~8种方法（Fixed-DB, Traj-Bootstrap, +DB-Curation, +Exemplar-Curation, +DB+Exemplar-Curation, 以及外部对比如Autoguide, AutoManual, Fixed-DB@k） → 约25~30个实验条件，每个5次随机种子，总计上百次运行。
- **消融实验**：
  - 数据库大小对性能的影响（图2，3个Benchmark）。
  - 最佳vs最差示例的比较（图4）。
  - 初始人工示例的价值（附录I，Wordcraft）。
  - 跨模型迁移（附录G，Mixtral 8x7B）。
  - 微调（附录F）。
  - 成功预测分析（附录H，AUROC）。
- **充分性**：
  - 覆盖多样化任务（导航、SQL、组合推理）。
  - 对比了多种基线：无自改进、多次尝试、更强LLM、手工方法、层次方法。
  - 报告了标准差，统计意义明确。
  - 进行了跨模型泛化测试，验证了方法的通用性。
  - 进行了消融分离两种筛选机制的效果。
- **公平性**：所有方法使用相同底层LLM和agent架构（除特别说明），检索参数一致。与Autoguide、AutoManual对比时虽LLM不同（论文承认），但结果仍具有参考价值。

## 6. 主要结论与发现

1. **简单累积成功轨迹即可大幅提升性能**：Traj-Bootstrap在ALFWorld上从73%提升至89%（+16%），Wordcraft从55%提升至64%（+9%），InterCode-SQL从75%提升至79%（+4%）。提升效果相当于允许2~3次尝试的基线。
2. **数据库级与示例级筛选可进一步增强**：组合方法在ALFWorld达93%，InterCode-SQL达82%。
3. **超越手工方法**：在ALFWorld上，+DB+Exemplar-Curation（93%）超越AutoManual（91%，使用GPT-4-turbo和手工观测/动作空间）。
4. **成本效益显著**：一次性构建数据库后，推理成本低于升级LLM或多次尝试，在规模化场景下可大幅节省成本。
5. **跨模型泛化**：用GPT-4o-mini收集的数据库使Mixtral 8x7B在ALFWorld上从27%提升至55%（+28%），证明捕获了任务结构而非模型特定伪影。
6. **可预测成功率**：自收集数据可用于训练分类器预测新任务成功概率，AUROC随数据库增大而提升（InterCode-SQL达0.77，Wordcraft达0.71），且校准良好。
7. **可用于微调**：自收集数据微调的ReAct-Finetune在ALFWorld和Wordcraft上优于上下文方法，但在InterCode-SQL上略逊。
8. **初始人工示例的作用**：Wordcraft上无初始示例时，即使收集4000条轨迹也无法达到有5条人工示例的性能，表明初始示例对引导方向至关重要。

## 7. 优点

- **自动化程度高**：完全无需人工提示工程、观测/动作空间设计，仅需少量初始示例。
- **方法简单有效**：核心idea（累积成功轨迹）简单，但效果显著，且两个筛选机制逻辑清晰、计算高效。
- **通用性强**：适用于多个不同领域的序列决策任务，且可跨模型迁移。
- **实验充分**：不仅对比基线，还对比了多种常见扩展策略（多次尝试、模型升级、手工方法、微调），并包含消融和跨模型验证。
- **实际可行性**：提供了详细成本分析，证明在规模化场景下极具经济性。
- **附带诊断能力**：成功预测分类器可作为实用工具，帮助识别困难任务。
- **与强化学习联系**：质量指标Q(τ)类似于价值函数，DB-Curation类似于群体训练（PBT），在概念上连接了ICL和RL。

## 8. 不足与局限

- **需要少量人工示例**：虽然方法自动化，但仍需少量初始轨迹（ALFWorld 18条，InterCode-SQL 10条，Wordcraft 4条），且论文发现无初始示例时性能难以追赶。
- **性能单调性不保证**：随着数据库增大，成功率并非单调递增，有时添加新轨迹会引入噪声导致下降。
- **对模型上下文学习能力依赖**：方法效果依赖于LLM自身从示例中学习的能力，若模型较弱（如Mixtral基线低），可能改善幅度有限。
- **未处理失败轨迹**：目前仅使用成功轨迹，未利用失败轨迹中的信息（如探索失败原因）。论文提到“Credit Attribution”问题，但未深入解决。
- **训练阶段算力开销**：5个并行数据库导致训练成本约5倍，对于任务数量极大的场景可能开销较高。但论文论证了训练是一次性投入，后续推理成本低。
- **benchmark范围有限**：三个benchmark均为文本交互式，未涉及视觉或多模态任务。论文指出排除了QA任务以避免检索器混淆，但未来需扩展至更广领域。
- **未详细探讨检索质量的影响**：虽然使用了动态检索，但未深入分析检索失败（如找不到相关示例）对性能的影响。
- **潜在风险**：智能体可能学习“奖励黑客”行为（未直接衡量），需要人工或LLM裁判审计自生成示例。

（完）
