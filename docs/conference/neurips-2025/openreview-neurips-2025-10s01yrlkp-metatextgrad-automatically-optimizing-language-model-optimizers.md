---
title: "metaTextGrad: Automatically optimizing language model optimizers"
title_zh: metaTextGrad：自动优化语言模型优化器
authors: "Guowei Xu, Mert Yuksekgonul, Carlos Guestrin, James Zou"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=10s01YrlKp"
tags: ["query:ai"]
score: 5.0
evidence: 优化语言模型优化器
tldr: 现有基于大语言模型的优化器依赖人工设计且通用性不足。本文提出metaTextGrad，通过元优化循环自动优化优化器本身。该方法针对特定任务自适应调整优化策略，在多个下游任务上显著提升性能。这一工作朝着自动化AI系统优化迈出了重要一步。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-10s01yrlkp/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1437, \"height\": 479, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-10s01yrlkp/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1420, \"height\": 750, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-10s01yrlkp/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1459, \"height\": 752, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-10s01yrlkp/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 708, \"height\": 221, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-10s01yrlkp/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 720, \"height\": 474, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-10s01yrlkp/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1438, \"height\": 182, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-10s01yrlkp/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 714, \"height\": 222, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-10s01yrlkp/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 706, \"height\": 475, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-10s01yrlkp/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1460, \"height\": 754, \"label\": \"Table\"}]"
motivation: LLM优化器通常由人类手工设计，缺乏自动化和任务特化。
method: 设计元优化框架，将优化器参数作为可学习变量，通过反馈循环自动调整。
result: 在提示调优、演示选择等任务上优于手工优化器和通用基线。
conclusion: 证明了优化器自动优化的可行性，提升了AI系统的自适应能力。
---

## Abstract
Large language models (LLMs) are increasingly used in learning algorithms, evaluations, and optimization tasks. Recent studies have shown that using LLM-based optimizers to automatically optimize model prompts, demonstrations, predictions themselves, or other components can significantly enhance the performance of AI systems, as demonstrated by frameworks such as DSPy and TextGrad. However, optimizers built on language models themselves are usually designed by humans with manual design choices; optimizers themselves are not optimized. Moreover, these optimizers are general purpose by design, to be useful to a broad audience, and are not tailored for specific tasks. To address these challenges, we propose metaTextGrad, which focuses on designing a meta-optimizer to further enhance existing optimizers and align them to be good optimizers for a given task. Our approach consists of two key components: a meta prompt optimizer and a meta structure optimizer. The combination of these two significantly improves performance across multiple benchmarks, achieving an average absolute performance improvement of up to 6% compared to the best baseline.

---

## 论文详细总结（自动生成）

# metaTextGrad: 自动优化语言模型优化器 — 详细中文总结

## 一、核心问题与整体含义（研究动机与背景）

- **现有 LLM 优化器的局限**：DSPy、TextGrad 等优化器虽能自动优化程序提示、演示等，但其本身由人类手动设计，是固定的通用优化器，缺乏针对特定任务的自动调优能力。
- **核心问题**：如何让优化器本身被优化，使其更好地适配特定下游任务，而无需人工反复调整？
- **整体含义**：本文提出元优化（meta-optimization）思想，通过一个“元优化器”自动改进现有 LLM 优化器的提示和组合结构，从而提升优化效果。这是从“优化程序”到“优化优化器”的一次跃迁，推进了 AI 系统的自动化程度。

## 二、方法论：核心思想、关键技术细节与算法流程

### 核心思想
- 假定所有 LLM 调用为黑盒（仅可获取输入输出），任务只需少量训练数据和一个评估指标。
- 元优化器以现有优化器为初始化，通过外循环优化优化器的参数（提示/结构），内循环评估优化后的程序性能，最终输出更优的优化器。

### 两大组件
1. **元提示优化器 (Meta Prompt Optimizer)**  
   - 针对每个输入优化器，基于当前任务示例分析其特点，迭代地改进优化器自身的提示文本，使其更关注任务关键点（如括号匹配中的 LIFO 顺序）。
   - 工作流程：初始化 → 采样任务示例 → LLM 生成改进提示 → 内循环测试 → 更新最佳优化器。

2. **元结构优化器 (Meta Structure Optimizer)**  
   - 自动决定不同优化器的组合与执行顺序，形成复合优化器。
   - 工作流程：初始化各优化器性能 → 列出参考优化器（含已优化的）→ LLM 生成新的混合优化器 → 评估 → 更新最佳。

### 整体流程 (metaTextGrad)
- 先对每个候选优化器独立进行提示优化 → 然后进行结构优化，组合形成最终优化器。
- 算法伪代码：Algorithm 1（内循环：优化程序）、Algorithm 2（外循环：优化优化器）。

### 理论动机 (Theorem 1)
- 基于 Hoeffding 不等式，证明经过元学习对齐后的优化器在测试集上的性能高概率接近最优，而未对齐的优化器无此保证。

## 三、实验设计：数据集、基准与对比方法

### 数据集与场景
- **BBH Word Sorting** (排序任务)  
- **BBH Dyck Languages** (括号匹配)  
- **MMLU Abstract Algebra** (抽象代数选择题)  
- **GPQA Diamond** (研究生级问答)  

每个数据集划分训练/验证/测试（如 50/100/100，10/50/40 等）。

### 基线方法
- 零样本 CoT、少样本 CoT、Self-consistency、Best-of-N  
- **DSPy 优化器**：MIPROv2  
- **TextGrad 优化器**：TGD、ADAS-TG  
- 所有基线均与 metaTextGrad 在相同设置下比较。

### 额外实验
- **跨模型迁移**：将 GPT-4o-mini 上优化的优化器迁移到 Claude 3 Haiku。
- **跨数据集迁移**：在 GPQA 上训练的优化器直接在 Abstract Algebra 上测试。
- **消融分析**：分别评估元提示优化、元结构优化、两者结合的效果。
- **开源模型验证**：使用 Qwen3-8B + Qwen3-235B-A22B 作为程序/优化器/元优化器。
- **困难基准**：ARC-AGI 抽象推理任务。

## 四、资源与算力

- **未明确指定 GPU 型号、数量或训练时长**，主要依赖调用商业 API。
- 采用分层模型策略：程序级 → GPT-4o-mini，优化器级 → GPT-4o，元优化器级 → o1，以平衡成本与效果。
- Token 消耗分析 (表2，Abstract Algebra)：
  - 程序级：~400k tokens
  - 优化器级：~100k tokens  
  - 元优化器级：~2.5k tokens
- 成本对比 (表3，Dyck Languages)：metaTextGrad (GPT-4o-mini) 成本 0.44 美元，性能 0.37，而 GPT-4o 零样本 CoT 成本 0.52 美元，性能仅 0.18。

## 五、实验数量与充分性

- **主要实验**：4 个标准基准 × 5 个随机种子，结果取平均。
- **消融实验**：6 种配置（零样本 CoT、TGD、ADAS-TG、TGD+元提示、ADAS-TG+元提示、元结构、metaTextGrad），验证各组件贡献。
- **迁移性实验**：跨模型 1 组、跨数据集 1 组。
- **开源模型验证**：1 组（Dyck Languages）。
- **困难基准**：1 组（ARC-AGI）。
- **总实验量**：约 10 组以上独立实验，覆盖多场景、多模型、多组件分析。
- **充分性评价**：实验设计全面客观，对比了多种最新基线，消融和迁移实验验证了方法的鲁棒性和泛化性，公平地使用了相同评估指标和种子数。

## 六、主要结论与发现

1. **性能显著提升**：在 4 个基准上，metaTextGrad 平均绝对性能比最佳基线高 6%，最高达 11%。
2. **任务对齐增强**：优化后的优化器更注重任务特有细节（如 Dyck 语言的 LIFO 堆栈验证），生成的程序也更针对性地包含专用模块（如类型分析器、嵌套分析器）。
3. **高效性**：元优化后的优化器往往只需 1-2 步内循环即可大幅提升，而普通优化器需要更多步骤。
4. **跨模型与跨数据集迁移**：在 GPT-4o-mini 上训练的优化器可直接迁移至 Claude 3 Haiku 并保持优势；在 GPQA 上训练的优化器也能提高 Abstract Algebra 性能。
5. **各组件均有贡献**：元提示优化器和元结构优化器均能单独带来提升，且不同任务的最佳组件不同。

## 七、优点

- **创新性**：首次提出“优化优化器本身”的元优化框架，突破了手工设计优化器的局限。
- **理论支撑**：提供概率泛化界 (Theorem 1)，为元优化必要性提供了理论依据。
- **实用性**：采用分层模型策略，有效控制成本；支持黑盒调用，兼容商业 API。
- **全面实验**：涵盖标准基准、迁移、消融、开源模型、困难基准，验证了方法鲁棒性和通用性。
- **可解释性**：优化后的优化器提示和程序结构更贴近任务特性，便于理解改进来源。

## 八、不足与局限

1. **基础模型能力瓶颈**：当底层 LLM 缺乏任务相关知识时（如数学竞赛 AIME 2024），元优化本身无法创造新能力。
2. **元优化器对模型要求高**：当前元优化器需要 o1 或 Claude-3.5 Sonnet 等强模型，较弱模型（如 Gemini 1.5 Pro）表现不佳，限制了可访问性。
3. **成本与复杂性**：尽管分层设计控制了成本，但整体优化流程仍涉及多次 API 调用，对于大规模任务可能时间较长。
4. **实验范围有限**：主要基于 GPT 系列和 Claude；更多模型族（如 Llama、Mistral）的泛化性尚未充分验证。
5. **潜在滥用风险**：元优化可被用于生成更具说服力的有害文本或操纵性系统，需谨慎部署。
6. **超参数依赖**：内循环迭代次数、外循环迭代次数等超参数对性能有影响，文中未做系统敏感度分析。

（完）
