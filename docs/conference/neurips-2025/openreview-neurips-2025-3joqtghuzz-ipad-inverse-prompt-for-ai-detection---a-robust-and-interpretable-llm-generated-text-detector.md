---
title: "IPAD: Inverse Prompt for AI Detection - A Robust and Interpretable LLM-Generated Text Detector"
title_zh: IPAD：逆提示用于AI检测——一个鲁棒且可解释的LLM生成文本检测器
authors: "Zheng CHEN, Yushi Feng, Jisheng Dang, Changyang He, Yue Deng, Hongxi Pu, Haoxuan Li, Bo Li"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=3JoQTGhUzz"
tags: ["query:ai"]
score: 5.0
evidence: LLM生成文本检测
tldr: 该论文提出IPAD框架，通过提示反向器识别可能生成文本的提示，并结合两个判别器进行检测。相比现有方法，IPAD在分布外数据和攻击数据上更具鲁棒性，并提供可解释证据。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-3joqtghuzz/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1454, \"height\": 687, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3joqtghuzz/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1425, \"height\": 779, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3joqtghuzz/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1438, \"height\": 740, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-3joqtghuzz/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1306, \"height\": 346, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3joqtghuzz/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1161, \"height\": 354, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3joqtghuzz/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1300, \"height\": 298, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3joqtghuzz/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1166, \"height\": 337, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3joqtghuzz/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1157, \"height\": 246, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3joqtghuzz/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1169, \"height\": 241, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3joqtghuzz/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1434, \"height\": 442, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3joqtghuzz/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1450, \"height\": 186, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3joqtghuzz/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1443, \"height\": 208, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3joqtghuzz/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1666, \"height\": 1757, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3joqtghuzz/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1670, \"height\": 1702, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3joqtghuzz/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1670, \"height\": 1129, \"label\": \"Table\"}]"
motivation: 现有LLM文本检测器鲁棒性差且缺乏可解释性，无法应对真实场景。
method: 提出包含提示反向器和两个判别器的框架，通过对提示进行逆向推理来判断文本来源。
result: 在多种攻击和分布外数据上表现鲁棒，并提供可解释的判别依据。
conclusion: IPAD为AI生成文本检测提供了更可靠且可解释的解决方案。
---

## Abstract
Large Language Models (LLMs) have attained human-level fluency in text generation, which complicates the distinguishing between human-written and LLM generated texts. This increases the risk of misuse and highlights the need for reliable detectors. Yet, existing detectors exhibit poor robustness on out-of-distribution (OOD) data and attacked data, which is critical for real-world scenarios. Also, they struggle to provide interpretable evidence to support their decisions, thus undermining reliability. In light of these challenges, we propose IPAD (Inverse Prompt for AI Detection), a novel framework consisting of a Prompt Inverter that identifies predicted prompts that could have generated the input text, and two Distinguishers that examine the probability that the input texts align with the predicted prompts. Empirical evaluations demonstrate that IPAD outperforms the strongest baselines by 9.05% (Average Recall) on in-distribution data, 12.93% (AUROC) on out-of-distribution (OOD) data, and 5.48% (AUROC) on attacked data. IPAD also performs robust on structured datasets. Furthermore, an interpretability assessment is conducted to illustrate that IPAD enhances the AI detection trustworthiness by allowing users to directly examine the decision-making evidence, which provides interpretable support for its state-of-the-art detection results.

---

## 论文详细总结（自动生成）

## 论文总结：IPAD：逆提示用于AI检测——一个鲁棒且可解释的LLM生成文本检测器

### 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：大语言模型（LLM）已达到人类水平的文本生成流畅度，使得区分人类手写文本（HWT）和LLM生成文本（LGT）变得困难，存在误用风险（学术欺诈、虚假信息等）。现有检测器在分布外（OOD）数据和受到攻击的数据上鲁棒性差，且缺乏可解释的证据支持其决策，导致用户难以信任。
- **整体含义**：IPAD旨在提供一种鲁棒且可解释的检测框架，通过逆向推理出可能生成输入文本的提示（prompt），并基于此进行一致性检验，从而提升检测性能和可解释性。

### 2. 方法论：核心思想、关键技术细节、流程

- **核心思想**：IPAD通过“提示反向器”（Prompt Inverter）从输入文本中重构最可能的提示，然后通过两个判别器评估文本与提示的一致性，最后融合得分做出判断。
- **关键技术细节**：
  - **Prompt Inverter（finv）**：基于Phi-3-medium-128k-instruct模型微调，输入文本T，输出预测的提示P。
  - **Prompt-Text Consistency Verifier (PTCV，fPTCV)**：微调模型，判断文本T是否可能由LLM通过提示P生成，输出概率p_PTCV。
  - **Regeneration Comparator (RC，fRC)**：用预测的提示P通过gpt-3.5-turbo重新生成文本T'，然后微调模型判断T和T'是否由相似提示生成，输出概率p_RC。
- **算法流程（文字说明）**：
  1. 输入文本T，调用finv得到预测提示P。
  2. 使用fLLM（gpt-3.5-turbo）根据P生成重写文本T'。
  3. 计算fPTCV的得分p_PTCV（softmax归一化）。
  4. 计算fRC的得分p_RC。
  5. 加权融合：ŝ = w·p_PTCV + (1-w)·p_RC，其中w=0.45，阈值τ=0.54（通过网格搜索在验证集上确定）。
  6. 若ŝ > τ，预测为LGT，否则为HWT。
  7. 返回预测标签和解释证据E（包含P、p_PTCV、p_RC、ŝ）。
- **训练细节**：全部使用Phi-3-medium-128k-instruct作为基座，采用LoRA微调，基于LLaMA-Factory框架。Prompt Inverter、PTCV、RC分别微调。

### 3. 实验设计

- **数据集与场景**：
  - **分布内数据**：基于OUTFOX数据集（essay问题、学生文章、LLM生成文章），评估标准分、DIPPER攻击、OUTFOX攻击。
  - **分布外（OOD）数据**：四个基准数据集（arXiv摘要、XSum新闻、WritingPrompts故事、Yelp评论），以及三种攻击（Prompt Attack、Paraphrase Attack、Perturbation Attack）。
  - **结构化提示数据**：LongWriter、Code-Feedback、Math数据集，用于评估结构化和长提示情况。
  - **可解释性评估**：用户研究，10名参与者比较IPAD与三个商用检测器（Scribbr、QuillBot、GPTZero）。
- **Benchmark与对比方法**：
  - 分布内：RoBERTa（base/large）、HC3、OUTFOX。
  - OOD：DetectLLM (LRR/NPR)、Binoculars、Fast-DetectGPT、RoBERTa-base。
  - 结构化：同上对比。
  - 提示反向器比较：与DPIC、PE（prompt extraction）对比。
  - 判别器：与Sentence-Bert、Bart-large-cnn、直接ChatGPT提示对比。
- **评估指标**：AUROC、HumanRec、MachineRec、AvgRec。

### 4. 资源与算力

- 论文明确说明：使用6张A800 GPU，训练时间：Prompt Inverter 20小时，PTCV 7小时，RC 9小时。推理可在单个Nvidia V100 GPU上运行（最小要求），且调用三次Phi-3模型（轻量级）和一次GPT-3.5-turbo API。

### 5. 实验数量与充分性

- **实验组数**：涉及多个数据集（分布内、OOD四种、结构化三种、攻击三种）、多种对比方法、消融实验（仅输入、仅提示、PTCV/RC单独、完整IPAD）、提示反向器对比、判别器对比、DPIC对比（15个数据集）、可解释性用户研究。总计至少十几组实验，每组通常有多个子场景。
- **充分性与公平性**：实验覆盖了分布内、分布外、攻击、结构化等多种场景，消融实验证明了各模块必要性。对比方法均使用公开基准或论文报告结果，且IPAD代码开源。实验设计较为客观、全面。但部分对比（如DPIC）由于未开源代码，依赖论文报告结果，可能存在细微偏差；用户研究样本量较小（10人），统计显著性有限。

### 6. 主要结论与发现

- IPAD在分布内数据上比最强基线平均提升9.05% AvgRec；在OOD数据上提升12.93% AUROC；在攻击数据上提升5.48% AUROC。
- 对结构化数据（LongWriter、Code-Feedback、Math）也表现鲁棒，MachineRec平均95.27%。
- 消融实验证明三个模块均不可或缺。
- 提示反向器在提示相似性指标（BartScore、Sentence-Bert、BLEU、ROUGE-1）上优于DPIC和PE。
- 判别器（PTCV+RC）优于简单相似度方法或直接提示ChatGPT。
- 可解释性评估表明IPAD提高了用户信任和透明度。

### 7. 优点

- **创新性**：首次将提示反向推理与双一致性检验结合，引入逻辑推理式任务（“能否生成？”）而非简单分类，提升了鲁棒性和可解释性。
- **鲁棒性**：在多种攻击和OOD场景下显著优于现有方法。
- **可解释性**：提供预测提示、重写文本、模块得分等证据，用户可验证决策。
- **实用性**：使用轻量级开源模型Phi-3，计算成本可接受（单V100即可推理）。
- **实验全面**：涵盖多领域、多攻击、多对比，消融验证充分。

### 8. 不足与局限

- **提示反向器局限性**：对于包含显式上下文学习示例的提示，反向器可能无法完整重构，因优先语义对齐而非精确句法复制。
- **计算成本**：相比轻量检测器（如RoBERTa），IPAD需要三次Phi-3调用和一次GPT-3.5 API，算力更高（但相比DPIC等LLM方法更轻量）。
- **用户研究规模小**：仅10人评估，统计效力有限，且未覆盖不同背景用户。
- **依赖外部LLM**：重写步骤依赖gpt-3.5-turbo，若API不可用或修改可能影响性能。
- **未评估实时性**：推理延迟未详细报告，可能不适用于实时检测场景。
- **局限性声明**：论文结尾明确指出了上述两点局限性。

（完）
