---
title: "AI-Researcher: Autonomous Scientific Innovation"
title_zh: AI-Researcher：自主科学创新
authors: "Jiabin Tang, Lianghao Xia, Zhonghang Li, Chao Huang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=kQWyOYUAC4"
tags: ["query:ai"]
score: 6.0
evidence: 自主人工智能研究系统
tldr: 本文提出AI-Researcher，一个完全自主的科研系统，通过大语言模型智能体协调文献综述、假设生成、算法实现到论文撰写的全流程。并构建了Scientist-Bench基准来评估。该系统能独立完成多项研究任务，显著加速科学发现。这项工作展示了AI在自主科研中的巨大潜力。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-kqwyoyuac4/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1400, \"height\": 646, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kqwyoyuac4/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1447, \"height\": 342, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kqwyoyuac4/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 907, \"height\": 414, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kqwyoyuac4/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 679, \"height\": 402, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kqwyoyuac4/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 706, \"height\": 404, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kqwyoyuac4/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 710, \"height\": 410, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kqwyoyuac4/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 488, \"height\": 494, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kqwyoyuac4/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1368, \"height\": 897, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kqwyoyuac4/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 459, \"height\": 490, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-kqwyoyuac4/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 455, \"height\": 492, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-kqwyoyuac4/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1398, \"height\": 532, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-kqwyoyuac4/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1398, \"height\": 533, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-kqwyoyuac4/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1425, \"height\": 294, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-kqwyoyuac4/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1509, \"height\": 1533, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-kqwyoyuac4/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1509, \"height\": 1744, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-kqwyoyuac4/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1413, \"height\": 252, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-kqwyoyuac4/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1225, \"height\": 319, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-kqwyoyuac4/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1425, \"height\": 586, \"label\": \"Table\"}]"
motivation: 现有AI辅助科研通常需要大量人工干预，缺乏全流程自动化。
method: 构建多智能体框架，利用LLM推理能力自动执行科研管线的各个阶段。
result: 在Scientist-Bench上，系统能从头产出可发表的论文，部分结果达到顶级水平。
conclusion: 首次展示了AI全自主科研的可行性，为加速科学发现奠定了基础。
---

## Abstract
The powerful reasoning capabilities of Large Language Models (LLMs) in mathematics and coding, combined with their ability to automate complex tasks through agentic frameworks, present unprecedented opportunities for accelerating scientific innovation. In this paper, we introduce AI-Researcher, a fully autonomous research system that transforms how AI-driven scientific discovery is conducted and evaluated. Our framework seamlessly orchestrates the complete research pipeline--from literature review and hypothesis generation to algorithm implementation and publication-ready manuscript preparation--with minimal human intervention. To rigorously assess autonomous research capabilities, we develop Scientist-Bench, a comprehensive benchmark comprising state-of-the-art papers across diverse AI research domains, featuring both guided innovation and open-ended exploration tasks. Through extensive experiments, we demonstrate that AI-Researcher achieves remarkable implementation success rates and produces research papers that approach human-level quality. This work establishes new foundations for autonomous scientific innovation that can complement human researchers by systematically exploring solution spaces beyond cognitive limitations.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：现有AI辅助科研通常需要大量人工干预，缺乏全流程自动化。尽管大语言模型（LLM）在数学推理和编码方面表现出色，但将其从孤立能力转化为能够自主进行原创科学发现的完整系统仍是未解决的挑战。人类认知限制和巨大的解空间阻碍了科学突破。
- **整体含义**：本文旨在构建一个完全自主的科研系统（AI-Researcher），使其能够自主完成从文献综述、假设生成、算法实现到论文撰写的完整科研流程，从而加速科学发现，探索超越人类认知边界的解空间。同时，为评估自主科研能力，构建了首个标准化基准Scientist-Bench。

### 2. 论文提出的方法论：核心思想、关键技术细节
- **核心思想**：采用多智能体架构，将科研流程分解为三个阶段，通过结构化知识交换和递归细化机制，实现从概念到最终学术贡献的端到端自动化。
- **关键技术细节**：
  - **阶段一：文献综述与想法生成**
    - **Knowledge Acquisition Agent**：基于用户提供的10-15篇参考论文，自动从GitHub、arXiv等数据库搜集高质量代码仓库和相关文献。
    - **Resource Analyst Agent**：将复杂研究概念分解为原子组件，通过Paper Analyst和Code Analyst子代理，提取数学公式和对应代码实现，建立精确映射，减少幻觉风险。
    - **Idea Generator**：发散-收敛机制，先生成5个不同研究方向，再根据科学新颖性、技术合理性和变革潜力进行收敛评估，选择最佳方向。
  - **阶段二：新算法设计、实现与验证**
    - **Code Agent**：在受控工作空间（Docker容器）中，基于实现计划生成可执行代码，强调代码独立性和忠实翻译。
    - **Advisor Agent**：提供专家级反馈，比较代码与原子研究概念，生成具体改进建议，形成迭代优化循环（类似导师-学生合作）。
    - **渐进式实验循环**：先在小数据上验证可行性，再扩展到完整实验，失败多次则标记为“不可行”。
  - **阶段三：自动科学文档撰写**
    - **Documentation Agent**：通过三阶段层次化生成（结构大纲→模板引导内容展开→清单核查与修订）克服LLM长文本连贯性挑战，生成符合出版标准的论文。
- **安全环境**：所有过程在Docker容器中运行，提供安全隔离和一致的实验环境。

### 3. 实验设计：数据集、Benchmark、对比方法
- **数据集/场景**：
  - **Scientist-Bench**：22篇来自顶级会议的高质量论文，涵盖扩散模型（4篇）、向量量化（6篇）、图神经网络（7篇）、推荐系统（5篇）。
  - 两个挑战级别：
    - **Level-1（导向创新）**：提供明确的研究指令（从目标论文提取的核心思想），测试执行能力。
    - **Level-2（开放探索）**：仅提供参考文献和数据集，不给出具体指令，测试独立创新能力（选取5篇论文保证领域多样性）。
- **对比方法**：
  - 与**人类撰写论文**（ground truth）进行成对比较。
  - 不同LLM骨干对比：Claude-3.5、Claude-3.7、GPT-4o、o1-mini、o3-mini。
  - 不同模型家族对比：Claude系列 vs 4o系列。
- **评估指标**：
  - **代码实现质量**：Completeness（是否成功生成可执行代码，93.8%成功率）和Correctness（多智能体评审打分，5分量表）。
  - **科学论文质量**：成对比较，7点量表（-3到+3），由多个LLM评审代理（GPT-4o、o1-mini、o3-mini、Claude-3.5、Claude-3.7）独立评估，并计算与人类论文的可比率（评分≥-1.0视为可比）。
  - **评审代理验证**：使用32对ICLR提交论文（已接受/拒绝）测试评审代理与人类专家判断的一致性。

### 4. 资源与算力
- **未明确说明具体算力**：论文提到所有进程在Docker容器中运行，使用预配置的ML框架，但未提供GPU型号、数量、训练时长等详细信息。仅提及实验依赖于API调用（如Claude、GPT），具体计算资源未披露。

### 5. 实验数量与充分性
- **实验数量**：
  - 在Scientist-Bench的22篇论文上评估Level-1任务（全部22篇）和Level-2任务（5篇代表性论文）。
  - 每种配置使用5种LLM评审代理，每个评审进行16次独立评估（温度=1.0）。
  - 消融研究：使用7篇代表性论文比较不同LLM骨干（Claude-3.5 vs GPT-4o）作为研究代理的影响。
  - 评审代理验证：32对ICLR论文，5种评审模型（Gemini-2.0-flash, GPT-4o, o3-mini, Claude-3.5, Claude-3.7）。
- **充分性**：
  - **优点**：多维度评估（代码完整性、正确性、科学质量），跨领域、跨难度级别对比，使用多个LLM评审减少单一模型偏差。评审代理经过人类判断验证。
  - **局限性**：LLM评审本身可能存在偏差（不同模型对同一论文判断差异大，如推荐系统领域GPT-4o和o1-mini认为全部可比，o3-mini认为全不可比）。实验未涉及实际人工评审交叉验证。计算资源限制导致部分领域（如扩散模型）性能未能充分发挥。

### 6. 论文的主要结论与发现
- **代码实现能力**：Claude系列模型实现完整率达93.8%，正确率平均2.65/5。Claude系列显著优于GPT-4o系列（完整率87.5% vs 50%）。
- **科学论文质量**：AI生成的论文在13.64%~81.82%的情况下被认为质量与人类论文可比（因评审代理而异）。开放探索任务（Level-2）表现优于导向任务（Level-1），说明自主系统更擅长利用内部知识综合而非执行明确指令。
- **领域差异**：不同领域表现有差异，但更受评审代理偏好影响而非领域本身。推荐系统领域可比率最高，扩散模型和GNN次之。
- **LLM骨干影响**：Claude-3.5作为研究代理骨干时优于GPT-4o，产出论文更接近人类水平。
- **评审代理验证**：AI评审代理与ICLR专家决策一致性高达81%~90%，验证了其有效性。

### 7. 优点
- **端到端全自动化**：首次实现从文献调研到论文撰写的完整科研流程自主执行，只需极少人工干预。
- **多智能体协作架构**：通过Resource Analyst减少幻觉，通过迭代细化机制提高实现成功率，通过层次化文档生成克服长文本连贯性问题。
- **构建标准化基准**：Scientist-Bench为未来自主科研评估提供了可复用的平台，涵盖多种领域和难度级别。
- **实验设计严谨**：采用双重评估（代码质量+科学质量）、多LLM评审、随机交换顺序避免位置偏差、评审代理与人类判断对齐验证。
- **核心洞见**：自主系统在开放探索任务中表现优于导向任务，挑战了“AI更擅长严格指令执行”的常识。

### 8. 不足与局限
- **LLM评审偏差**：不同LLM评审代理对同一论文评价差异显著，仅依赖LLM评审可能不可靠，缺乏人工专家直接参与。
- **计算资源限制**：对于计算密集领域（如扩散模型），性能受限于可用算力，可能低估了系统的真实能力。未报告具体硬件配置。
- **伦理与安全考虑不足**：论文未系统处理自主科研可能引发的偏见、不安全建议、责任归属等伦理问题。
- **LLM骨干多样性有限**：主要依赖Claude和GPT系列闭源模型，未评估开源模型（如DeepSeek、Llama）的适用性。
- **基准规模有限**：仅22篇论文，领域覆盖（扩散、VQ、GNN、推荐）虽广但数量偏少，可能不足以泛化到更多科研领域。
- **代码正确性评分中等**：平均2.65/5，表明仍有较大提升空间，特别是复杂算法实现质量需改进。
- **潜在幻觉风险**：尽管Resource Analyst设计用于减少幻觉，但生成论文中仍可能存在不准确引用或逻辑漏洞。

（完）
