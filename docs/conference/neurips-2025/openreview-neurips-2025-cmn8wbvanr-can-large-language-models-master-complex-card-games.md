---
title: Can Large Language Models Master Complex Card Games?
title_zh: 大语言模型能否掌握复杂纸牌游戏？
authors: "Wei Wang, Fuqing Bie, Junzhe Chen, Dan Zhang, Shiyu Huang, Evgeny Kharlamov, Jie Tang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=cmN8Wbvanr"
tags: ["query:ai-classic"]
score: 6.0
evidence: 使用AlphaGo等经典AI游戏基准评估LLM
tldr: 针对LLM能否在复杂游戏中达到AlphaGo等经典AI水平的问题，本文在8种纸牌游戏中系统评估LLM，发现微调能提升表现但通用能力稳定，为AI在游戏领域的进展提供新视角。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-cmn8wbvanr/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 727, \"height\": 508, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cmn8wbvanr/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1445, \"height\": 413, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cmn8wbvanr/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1449, \"height\": 532, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cmn8wbvanr/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 644, \"height\": 471, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cmn8wbvanr/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 700, \"height\": 481, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cmn8wbvanr/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 697, \"height\": 487, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cmn8wbvanr/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 698, \"height\": 467, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-cmn8wbvanr/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1450, \"height\": 297, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-cmn8wbvanr/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1451, \"height\": 681, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-cmn8wbvanr/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 656, \"height\": 146, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-cmn8wbvanr/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1428, \"height\": 456, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-cmn8wbvanr/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1424, \"height\": 458, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-cmn8wbvanr/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1423, \"height\": 460, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-cmn8wbvanr/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1450, \"height\": 232, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-cmn8wbvanr/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1451, \"height\": 245, \"label\": \"Table\"}]"
motivation: 评估LLM在复杂游戏中的能力，与经典AI基准对比。
method: 在8种纸牌游戏中微调LLM并评估性能与泛化。
result: 微调可提升游戏表现，但通用能力保持稳定。
conclusion: LLM在复杂游戏中展现潜力，但仍需改进。
---

## Abstract
Complex games have long been an important benchmark for testing the progress of artificial intelligence algorithms. AlphaGo, AlphaZero, and MuZero have defeated top human players in Go and Chess, garnering widespread societal attention towards artificial intelligence. Concurrently, large language models (LLMs) have exhibited remarkable capabilities across various tasks, raising the question of whether LLMs can achieve similar success in complex games. In this paper, we explore the potential of LLMs in mastering complex card games. We systematically assess the learning capabilities of LLMs across eight diverse card games, evaluating the impact of fine-tuning on high-quality gameplay data, and examining the models' ability to retain general capabilities while mastering these games. Our findings indicate that: (1) LLMs can approach the performance of strong game AIs through supervised fine-tuning on high-quality data, (2) LLMs can achieve a certain level of proficiency in multiple complex card games simultaneously, with performance augmentation for games with similar rules and conflicts for dissimilar ones, and (3) LLMs experience a decline in general capabilities when mastering complex games, but this decline can be mitigated by integrating a certain amount of general instruction data. The evaluation results demonstrate strong learning ability and versatility of LLMs. The code is available at 
https://github.com/THUDM/LLM4CardGame

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：大型语言模型（LLM）能否在复杂纸牌游戏中达到类似 AlphaGo、AlphaZero 等经典强化学习 AI 的顶尖水平？即 LLM 是否具备在高度复杂、不完全信息的博弈环境中「掌握」游戏的能力。
- **研究背景**：以往对 LLM 在游戏中的评估多采用提示（prompt）方式，不涉及微调，因此只能测量模型已有的知识迁移能力，而无法评估其学习能力；此外，已有微调评估的任务复杂度不足。本文旨在填补这一空白，系统评估 LLM 通过监督微调在多个高复杂度纸牌游戏上的学习能力，并检验其同时学习多游戏、保持通用能力的能力。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：利用现有强游戏 AI 或人类专家数据生成高质量玩法轨迹，以监督微调（SFT）方式训练 LLM，使其从这些轨迹中学习游戏策略，从而避免让模型从零开始探索环境的高计算成本。
- **关键技术细节**：
  - **游戏选择**：8 款纸牌游戏：斗地主、掼蛋、日本麻将、Uno、Gin Rummy、Leduc Hold'em、Limit Texas Hold'em、No-limit Texas Hold'em。这些游戏在信息集数量、平均信息集大小和动作空间上具有不同复杂度。
  - **数据生成**：使用**教师模型**（如 DouZero、DanZero、DQN 模型、Tenhou 人类专家数据）与对手模型对弈，仅保留**胜方**的观测-动作对，并过滤掉合法动作数仅为1的样本，确保数据高质量。
  - **微调方案**：设计每款游戏的提示模板，将观测-动作对转化为指令格式；采用 LoRA 微调（rank=8, alpha=16），学习率 1e-4，余弦调度，1 epoch，batch size 128。
  - **评估指标**：斗地主/掼蛋用胜率，其余用奖励分数（reward score）；麻将按平均排名转换得分（第1名3分，第2名2分，第3名1分，第4名0分）。

### 3. 实验设计：数据集 / 场景、benchmark、对比方法

- **数据集**：每款游戏生成过滤后的样本。斗地主、掼蛋、麻将从各自数据中抽样1000k条训练；Uno、Gin Rummy、Leduc、Limit、No-limit 各抽样400k条。
- **Benchmark**：
  - 游戏性能：与各自的强 AI 教师模型或规则模型/随机模型对弈（如斗地主 vs. DouZero，掼蛋 vs. DanZero，麻将 vs. Mortal AI）。
  - 通用能力：MMLU-Pro（知识问答）、Math-500（数学）、HumanEval（代码），此外还补充了 GQPA-Diamond、AIME2024、LiveCodeBench、IFEval。
- **对比方法**：
  - **API 模型**：GPT-4o-mini, GPT-4o, GLM-4-air, GLM-4-plus, DeepSeek-V3, DeepSeek-R1。
  - **基座模型**：Qwen2.5-7B-Instruct, Llama3.1-8B-Instruct, GLM4-9B-Chat（不微调）。
  - **微调模型**：分别对每款游戏单独微调，以及在所有游戏混合数据集上微调的混合模型（mix）。
- **消融**：模型类型（3种）、模型参数量（Qwen2.5: 0.5B/1.5B/3B/7B/14B）、单游戏 vs. 多游戏混合、加入通用数据微调后的恢复效果。

### 4. 资源与算力

- **训练平台**：8 张 H100 GPU 的服务器（具体型号：H800？文中说 H800，但原文写 H100？原文PDF第4页：“We conduct experiments on a server with 8 H100 GPUs.” 第21页附录又说 “8 H800 GPUs” —— 存在不一致，但可表述为 H100/H800 系列）。
- **训练时长**（以1百万样本为例）：
  - 斗地主：Qwen2.5-7B 11h, Llama3.1-8B 12h, GLM4-9B 14h。
  - 掼蛋：Qwen2.5-7B 21h, Llama3.1-8B 25h, GLM4-9B 29h。
- **对比**：DouZero 需 4 块 1080 Ti 训练30天；DanZero 需 GeForce RTX 3070 训练30天。但公平比较不可行。

### 5. 实验数量与充分性

- **实验数量**：
  - 单游戏微调：每个游戏至少1组（不同模型类型、不同参数量）。提供每个游戏随数据量变化的曲线（每隔400步保存 checkpoint）。
  - 多游戏混合微调：在混合数据集上训练3种模型，评估所有8款游戏。
  - 游戏间影响：将每款游戏单独微调的模型在其余7款上评估，分析知识迁移与冲突（共8×7=56组条件，实际以表格形式展示8款模型×8款游戏）。
  - 通用能力：在3个基准上评估基座、混合游戏微调、混合+通用数据微调三个状态。还补充了4个额外基准。
  - 消融实验：模型类型（3种）、参数量（5种）、是否加入通用数据。
- **充分性**：实验覆盖了多种游戏类型、多种模型架构、多个尺寸、多种数据混合策略，并同时评估游戏性能与通用能力，覆盖面较广。但缺失对更大参数规模（如70B）和更多训练轮次的探索；教师模型数据质量依赖公开资源，可能存在偏差；未做重复实验以统计误差（文中解释为计算代价高）。

### 6. 论文的主要结论与发现

1. **LLM 可掌握复杂纸牌游戏**：通过监督微调高质量数据，LLM 能逼近强游戏 AI（如 DouZero、DanZero、Mortal）的性能，尤其在斗地主、掼蛋、麻将三个高复杂度游戏中表现突出。
2. **多游戏同时学习能力**：模型在混合数据微调后，可同时在所有8款游戏中取得较好成绩，远超 API 基座模型。规则相似的游戏（如斗地主与掼蛋，三种德州扑克之间）存在正向知识迁移；规则差异大的游戏间则出现性能冲突。
3. **通用能力下降与恢复**：游戏微调后，在 MMLU-Pro、Math-500、HumanEval 等通用基准上出现明显下降。通过少量通用数据（知识、数学、代码各20k + 游戏8k）继续微调，可部分恢复通用能力，且游戏性能几乎不变。
4. **模型规模与类型影响**：参数量从 0.5B 增至 7B 时游戏性能提升，但 14B 因角色间不平衡反而不如 7B；不同模型类型（Qwen、Llama、GLM）在平衡角色学习上存在差异，GLM 在 Farmer 角色上表现弱，导致平均胜率低。
5. **LLM 最大优势是通用性**：无需为每款游戏设计专用网络结构，同一种架构即可适应多游戏。

### 7. 优点

- **系统性**：首次在多达8款复杂纸牌游戏上全面评估 LLM 的学习能力，而不是仅提示评估。
- **高质量数据**：利用强 AI 生成并过滤数据，避免从零探索的高成本。
- **多维度分析**：涵盖单游戏、多游戏混合、通用能力恢复、游戏间迁移/冲突、模型类型与尺寸影响。
- **公平对比**：与多个主流 API 模型（GPT-4o、DeepSeek 等）和基座模型对比，设置合理。
- **实用价值**：验证了 LLM 可作为通用博弈学习器的潜力，并展示了如何通过混合微调保持通用能力，对实际部署有指导意义。

### 8. 不足与局限

- **实验覆盖**：未包含更大型模型（如70B）或更多训练轮次；未报告误差棒或多次重复实验（计算代价高）。
- **教师模型依赖**：数据质量受限于公开的教师 AI（如 DouZero、DanZero）的水平，且人类专家数据（麻将）可能存在偏差。
- **角色不平衡**：数据筛选策略（仅保留胜方）导致某些角色（斗地主农民）的训练数据含低质量样本，影响模型平衡。
- **推理时间**：LLM 参数量大（7B-9B），游戏内推理速度远慢于专用游戏 AI，限制了实时应用。
- **通用能力恢复有限**：微调通用数据后，模型在指令遵循（IFEval）等基准上未见恢复甚至下降。
- **公平性**：与强化学习 AI 的训练计算资源对比不直接，无法得出 LLM 数据/计算效率优势的明确结论。

（完）
