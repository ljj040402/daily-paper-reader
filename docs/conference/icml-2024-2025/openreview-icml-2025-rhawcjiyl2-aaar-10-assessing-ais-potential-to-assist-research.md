---
title: "AAAR-1.0: Assessing AI’s Potential to Assist Research"
title_zh: AAAR-1.0：评估人工智能辅助研究的潜力
authors: "Renze Lou, Hanzi Xu, Sijia Wang, Jiangshu Du, Ryo Kamoi, Xiaoxin Lu, Jian Xie, Yuxuan Sun, Yusen Zhang, Jihyun Janice Ahn, Hongchao Fang, Zhuoyang Zou, Wenchao Ma, Xi Li, Kai Zhang, Congying Xia, Lifu Huang, Wenpeng Yin"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=RHAWcjIyl2"
tags: ["query:ai"]
score: 6.0
evidence: 评估大语言模型在研究任务上的基准，涉及AI能力
tldr: 该论文提出AAAR-1.0基准数据集，用于评估大语言模型在三大研究任务：方程推理、实验设计和论文审阅上的表现。实验结果显示，当前最强模型在专业研究任务上仍有明显不足，尤其在复杂推理和领域知识应用方面。该基准为未来AI辅助研究工具的发展提供了重要参考。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-rhawcjiyl2/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 831, \"height\": 677, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rhawcjiyl2/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1699, \"height\": 756, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rhawcjiyl2/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1131, \"height\": 1095, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rhawcjiyl2/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1201, \"height\": 902, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rhawcjiyl2/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 851, \"height\": 622, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rhawcjiyl2/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 862, \"height\": 1164, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rhawcjiyl2/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1776, \"height\": 382, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rhawcjiyl2/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1767, \"height\": 850, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rhawcjiyl2/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1771, \"height\": 758, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rhawcjiyl2/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1775, \"height\": 600, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rhawcjiyl2/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1776, \"height\": 731, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rhawcjiyl2/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1113, \"height\": 916, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-rhawcjiyl2/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 852, \"height\": 545, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-rhawcjiyl2/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1754, \"height\": 654, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-rhawcjiyl2/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 857, \"height\": 295, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-rhawcjiyl2/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 853, \"height\": 442, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-rhawcjiyl2/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 589, \"height\": 347, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-rhawcjiyl2/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1766, \"height\": 807, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-rhawcjiyl2/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1057, \"height\": 808, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-rhawcjiyl2/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1045, \"height\": 985, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-rhawcjiyl2/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 939, \"height\": 1144, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-rhawcjiyl2/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1519, \"height\": 442, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-rhawcjiyl2/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1757, \"height\": 275, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-rhawcjiyl2/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1725, \"height\": 2242, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-rhawcjiyl2/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1472, \"height\": 358, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-rhawcjiyl2/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1241, \"height\": 535, \"label\": \"Table\"}]"
motivation: 缺乏系统评估大语言模型在研究任务上能力的基准。
method: 构建包含方程推理、实验设计和论文审阅三大任务的基准数据集。
result: 评估发现当前最强模型在专业研究任务上表现有限，揭示了许多局限。
conclusion: AAAR-1.0为AI辅助研究的能力评估和提升提供了标准化测试平台。
---

## Abstract
Numerous studies have assessed the proficiency of AI systems, particularly large language models (LLMs), in facilitating everyday tasks such as email writing, question answering, and creative content generation. However, researchers face unique challenges and opportunities in leveraging LLMs for their own work, such as brainstorming research ideas, designing experiments, and writing or reviewing papers. In this study, we introduce AAAR-1.0, a benchmark dataset designed to evaluate LLM performance in three fundamental, expertise-intensive research tasks: (i) EquationInference, assessing the correctness of equations based on the contextual information in paper submissions; (ii) ExperimentDesign, designing experiments to validate research ideas and solutions; and (iii) PaperWeakness, identifying weaknesses in paper submissions. AAAR-1.0 differs from prior benchmarks in two key ways: first, it is explicitly research-oriented, with tasks requiring deep domain expertise; second, it is researcher-oriented, mirroring the primary activities that researchers engage in on a daily basis. An evaluation of both open-source and proprietary LLMs reveals their potential as well as limitations in conducting sophisticated research tasks. We will release the AAAR-1.0 and keep iterating it to new versions.

---

## 论文详细总结（自动生成）

# 论文详细总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：现有研究大多评估大语言模型（LLMs）在日常生活任务（如邮件撰写、问答、创意生成）中的能力，但缺乏对**专业研究任务**的系统评估。研究者面临独特的挑战——需要深度领域知识和推理能力，如构思研究想法、设计实验、撰写和评审论文。因此，需要一个标准化基准来衡量LLMs在**专家级研究任务**上的表现。
- **整体含义**：提出AAAR-1.0基准，专注于三个高难度、高专业性的研究子任务，以揭示当前LLMs在辅助科研方面的真实能力与局限，为未来AI辅助研究工具的发展提供参考。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：构建一个面向研究者的、要求深度领域知识的基准，包含三个独立、清晰的评估任务，每个任务具有明确的输入输出，避免复杂任务链带来的模糊性。
- **任务一：方程推理（EQINFER）**
  - **目标**：给定论文上下文，判断提供的方程是否正确（二分类）。
  - **数据构建**：
    1. 从ACL Anthology（2019-2023）爬取1,762篇论文的LaTeX源码，清洗后随机提取最多3个方程/篇，得到3,877个人工正例方程。
    2. 使用GPT-4基于论文上下文为每个正例生成3个负例方程（高温度采样）。
    3. GPT-4过滤负例中与上下文不匹配（未定义的符号）的样本。
    4. 人工专家（5位资深博士生）检查正负例是否确实不同、语法是否正确，共保留1,049组（每组1正3负）。
- **任务二：实验设计（EXPDESIGN）**
  - **目标**：给定论文实验前的上下文（含图表），生成实验计划及对应动机解释。
  - **数据构建**：
    1. 从arXiv收集≥10k篇论文（cs.AI, cs.CL, cs.CV，2018-2023），仅限知名会议论文。
    2. 邀请10位资深专家（至少4年AI研究经验、有顶级会议发表、常担任审稿人）阅读论文，定位关键实验并简述“做什么”和“为什么”。
    3. 经多轮同行讨论（另一位专家审阅）直至意见一致，最终得到100个实例。
    4. 使用GPT-4删除可能泄露实验内容的句子（约9.8%）。
    5. 输入为实验前文本+图表；输出为专家标注的实验列表与动机列表。
- **任务三：论文弱点识别（WEAKNESS）**
  - **目标**：根据整篇论文内容，指出论文中的弱点。
  - **数据构建**：
    1. 从ICLR 2023 OpenReview爬取3,779篇匿名投稿，均匀采样500篇接收+500篇拒稿，覆盖全部13个track，共1,000篇（最终保留993篇）。
    2. 使用GPT-4从每位审稿人原始评语中提取所有弱点，保持原文不变，并保留重复项（因重复强调表示重要）。
    3. 输入：PDF经VILA解析的文本 + PDFFigures-2.0提取的图表；输出：多位审稿人的弱点列表。
- **评估指标**：
  - **EQINFER**：F1分数。
  - **EXPDESIGN**：实验设计用En-Precision/En-Recall（基于LLM-as-judge判断预测实验是否被真实实验蕴含）；动机解释用S-Match（SentenceBERT语义相似度）+ ROUGE。
  - **WEAKNESS**：S-Precision/S-Recall（基于语义相似度与多位审稿人弱点比较）+ ITF-IDF（衡量弱点多样性，结合信息量和特异性）。

## 3. 实验设计

- **数据集与场景**：
  - EQINFER：1,049正例 + 3,147负例（来自869篇论文）。
  - EXPDESIGN：100个实例（100篇论文）。
  - WEAKNESS：993篇论文（每篇多位审稿人弱点列表）。
- **基准与对比方法**：
  - 基线：简单全正例预测（EQINFER 40% F1）；直接复制输入作为解释（EXPDESIGN）；人类审稿人（WEAKNESS ITF-IDF对比）。
  - 对比模型：开源LLM（OLMo-7B, Mistral-7B, Mixtral-8x22B-MoE, Llama 3.1-70B, Qwen 2.5-72B等）及闭源LLM（Gemini 1.5 Pro, Claude 3.5 Sonnet, GPT-4o, o1-preview, o3-mini）。另有AI-SCI agent框架（WEAKNESS）。
- **消融实验**：
  - 上下文长度缩放（EQINFER从100到1500词；EXPDESIGN从0.1k到10k tokens；WEAKNESS对比split-combine与no-split及不同窗口大小）。
  - 多模态输入（在EXPDESIGN和WEAKNESS中测试加图表是否提升性能）。
  - EXPDESIGN中测试“逐个解释”vs.“整体列表解释”。
  - WEAKNESS中对比split-combine与直接输入全文。

## 4. 资源与算力

- **文中明确说明**：
  - 所有开源LLM推理使用**8张NVIDIA A100 GPU**，框架为VLLM，CUDA 12.1，PyTorch 2.4.0。
  - 闭源LLM通过API调用（LiteLLM统一）。
  - 未提及具体训练时长（仅评估无需训练）。
  - 备注：每个模型运行3次取中位数结果。

## 5. 实验数量与充分性

- **实验数量**：
  - 主实验：在全部三个任务上测试了多个LLM，每个任务均有详细表格。
  - 消融实验：EQINFER上下文长度缩放（不同长度）；EXPDESIGN上下文长度、多模态、解释方式、人类评估；WEAKNESS split-combine vs no-split、多模态。
  - 人类评估：EXPDESIGN上对新颖实验的必要性（三级）由3位专家评估，对解释的可接受性由5位专家评估；WEAKNESS引用人类审稿人作为参考。
- **充分性与客观性**：
  - **优点**：多元模型覆盖开源/闭源，多维度消融，人工评估验证自动指标相关性（如EXPDESIGN S-Match与人类排名相关系数为1）。
  - **不足**：EXPDESIGN仅100个实例，样本量偏小，可能受限特定领域（AI相关）；WEAKNESS数据源自ICLR 2023，可能偏向NLP/ML领域；评估依赖LLM打分（如En-Precision）存在潜在偏差；未进行跨学科验证。

## 6. 主要结论与发现

- **EQINFER**：最强模型o3-mini仅47.98% F1，略高于随机基线40%，且所有LLM普遍高召回低精确率，表明验证方程能力极弱。
- **EXPDESIGN**：LLM设计的实验有创意（多样性高），但大量实验不必要、不可行或偏离原目标。闭源模型略优于开源，但En-F1仅~30%。解释生成中S-Match与ROUGE负相关，开源模型倾向于抄袭输入而非理解动机。更多上下文提升效果有限（超过8k无增益）。
- **WEAKNESS**：LLM发现的弱点通常泛泛而谈、缺乏深度和特异性。闭源模型S-Recall较高（因生成更多条），但ITF-IDF多样性远低于人类（人类7.69 vs 最强LLM约5.95）。高级提示技术（如self-reflection）未能超越简单方法。split-combine优于直接输入全文。
- **多模态输入**：在EXPDESIGN和WEAKNESS中，加入图表未带来显著提升，甚至略降，表明当前多模态LLM不擅长利用科学图表信息。
- **总体**：当前LLM在专业研究任务上远未达到人类水平，仅能提供初稿辅助，不可替代学者。

## 7. 优点

- **任务设计**：选取三个典型的、需要深度领域知识和推理的研究子任务，具有代表性和实用性。
- **数据质量**：由资深AI研究者进行人工标注（多位专家、多轮讨论、严格审核），确保正负例准确、实验动机合理、弱点提取忠实于原始评论。
- **评估指标创新**：提出适应开放生成任务的自动指标（En-Precision/Recall、S-Match、ITF-IDF），并验证了与人工评价的一致性（Spearman相关系数=1）。
- **全面消融**：覆盖上下文长度、多模态、输入处理方式等影响因素，提供了深入的性能分析。
- **开源/闭源模型对比**：公平比较并揭示不同规模、不同授权模式模型的能力差异。

## 8. 不足与局限

- **样本量有限**：EXPDESIGN仅100实例，可能不足以反映多样化的研究场景；WEAKNESS虽近1000但仅来自单一会议（ICLR 2023），领域偏向NLP/ML。
- **领域泛化性**：数据全部来自AI会议（ACL, CVPR, ICLR等），结论未必适用于其他科学领域（如物理、生物、医学）。
- **评估依赖LLM**：En-Precision/Recall使用GPT-4o作为评判器，可能引入另一LLM的偏见，且成本高。
- **多模态处理不足**：图表信息未有效利用，反映当前多模态模型在科学图像理解上的局限。
- **任务覆盖面**：仅关注三个独立子任务，未涵盖完整研究流程（如代码实现、结果分析、论文写作等），也无法评估LLM在闭环研究中的表现。
- **伦理声明限制**：作者明确表示不主张AI替代人类研究，主要评估其辅助潜力，但未深入讨论滥用风险（如生成虚假论文）。
- **重复性**：部分模型（如Claude, o1）仅API可用，无法本地复现；论文未提供全部提示模板（仅附录中部分）。

（完）
