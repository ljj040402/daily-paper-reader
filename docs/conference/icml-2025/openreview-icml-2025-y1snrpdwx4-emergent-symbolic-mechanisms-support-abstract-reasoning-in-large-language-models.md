---
title: Emergent Symbolic Mechanisms Support Abstract Reasoning in Large Language Models
title_zh: 涌现符号机制支撑大语言模型的抽象推理
authors: "Yukang Yang, Declan Iain Campbell, Kaixuan Huang, Mengdi Wang, Jonathan D. Cohen, Taylor Whittington Webb"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=y1SnRPDWx4"
tags: ["query:ai"]
score: 8.0
evidence: ICML 2025关于大语言模型推理机制的论文
tldr: 该论文揭示了大型语言模型中支持抽象推理的涌现符号机制。通过分析内部计算，识别出三个串行过程：早期层的符号抽象头将输入转换为抽象变量，中间层的符号归纳头进行序列归纳，后期层的检索头完成检索。这些机制共同实现了强大的抽象推理能力，为理解LLM的推理黑箱提供了重要见解。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-y1snrpdwx4/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1326, \"height\": 697, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y1snrpdwx4/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1641, \"height\": 1019, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y1snrpdwx4/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1658, \"height\": 918, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y1snrpdwx4/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1680, \"height\": 1006, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y1snrpdwx4/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1424, \"height\": 1587, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y1snrpdwx4/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1421, \"height\": 1587, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y1snrpdwx4/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1420, \"height\": 1585, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y1snrpdwx4/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1677, \"height\": 584, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y1snrpdwx4/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1170, \"height\": 618, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y1snrpdwx4/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1178, \"height\": 1238, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y1snrpdwx4/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1726, \"height\": 871, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y1snrpdwx4/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1728, \"height\": 872, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y1snrpdwx4/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1471, \"height\": 959, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y1snrpdwx4/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1471, \"height\": 965, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y1snrpdwx4/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1678, \"height\": 503, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y1snrpdwx4/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1288, \"height\": 618, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y1snrpdwx4/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1463, \"height\": 706, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y1snrpdwx4/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1738, \"height\": 2172, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y1snrpdwx4/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1170, \"height\": 2177, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y1snrpdwx4/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1738, \"height\": 1619, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y1snrpdwx4/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1735, \"height\": 2173, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y1snrpdwx4/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1741, \"height\": 1076, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y1snrpdwx4/fig-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 1824, \"height\": 560, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y1snrpdwx4/fig-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 1751, \"height\": 1074, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y1snrpdwx4/fig-025.webp\", \"caption\": \"\", \"page\": 0, \"index\": 25, \"width\": 1287, \"height\": 571, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-y1snrpdwx4/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1421, \"height\": 169, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-y1snrpdwx4/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1252, \"height\": 292, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-y1snrpdwx4/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 979, \"height\": 164, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-y1snrpdwx4/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 810, \"height\": 746, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-y1snrpdwx4/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 621, \"height\": 216, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-y1snrpdwx4/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 796, \"height\": 202, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-y1snrpdwx4/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 894, \"height\": 115, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-y1snrpdwx4/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 885, \"height\": 166, \"label\": \"Table\"}]"
motivation: LLM的推理能力机制尚不明确，存在争议。
method: 通过机制分析识别出符号抽象、归纳和检索三阶段计算。
result: 发现并验证了内部符号化推理过程。
conclusion: 揭示了LLM抽象推理的结构化内部机制。
---

## Abstract
Many recent studies have found evidence for emergent reasoning capabilities in large language models (LLMs), but debate persists concerning the robustness of these capabilities, and the extent to which they depend on structured reasoning mechanisms. To shed light on these issues, we study the internal mechanisms that support abstract reasoning in LLMs. We identify an emergent symbolic architecture that implements abstract reasoning via a series of three computations. In early layers, *symbol abstraction heads* convert input tokens to abstract variables based on the relations between those tokens. In intermediate layers, *symbolic induction heads* perform sequence induction over these abstract variables. Finally, in later layers, *retrieval heads* predict the next token by retrieving the value associated with the predicted abstract variable. These results point toward a resolution of the longstanding debate between symbolic and neural network approaches, suggesting that emergent reasoning in neural networks depends on the emergence of symbolic mechanisms.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：大语言模型（LLMs）是否真正具备结构化的抽象推理能力，还是仅仅通过统计近似模仿训练数据？其内部机制是什么？
- **背景**：学界对LLM推理能力存在激烈争论（如“随机鹦鹉”与真正推理的争议）。传统符号主义认为需要内置符号处理机制，而联结主义认为神经网络可自行学习。本文试图通过分析内部计算机制来回答这一问题。
- **整体含义**：发现LLM内部涌现出一套三阶段符号架构，实现抽象推理。这调和了符号主义与神经网络的长期争论，表明神经网络中的推理依赖于涌现的符号机制。

## 2. 论文提出的方法论：核心思想、关键技术细节
- **核心思想**：将抽象推理分解为三个串行的神经机制：
  1. **符号抽象头（Symbol Abstraction Heads）**：在早期层，将输入令牌转换为抽象变量（符号），基于令牌间关系（如相同/不同），值嵌入仅表示位置，不包含令牌身份。
  2. **符号归纳头（Symbolic Induction Heads）**：在中间层，对抽象变量序列进行归纳，预测下一个抽象变量（类似归纳头但作用于符号而非字面令牌）。
  3. **检索头（Retrieval Heads）**：在后期层，根据预测的抽象变量检索对应的具体令牌值，实现间接引用（指针）。
- **关键技术细节**：
  - **因果中介分析（Causal Mediation Analysis, CMA）**：通过将某一上下文中的激活值替换到另一上下文，测量对输出的因果影响，从而定位特定头。
  - **双分离设计**：创建两类上下文对——抽象变量变化但令牌不变（用于定位符号抽象/归纳头），令牌变化但抽象变量不变（用于定位检索头）。
  - **注意力模式分析**：验证各头的注意力是否指向理论预测的位置。
  - **表征相似性分析（RSA）**：比较头输出的相似性矩阵与理论预测的抽象变量/令牌相似性矩阵。
  - **消融实验**：逐步消除各头并观察模型性能下降。
- **公式/算法**：CMA得分计算公式见Algorithm 1，通过比较原始上下文和修补后上下文的logits差来量化因果影响。

## 3. 实验设计：数据集、Benchmark、对比方法
- **数据集/场景**：
  - **代数规则归纳**（Identity Rules）：ABA或ABB模式，使用随机采样令牌，确保无统计关联。
  - **字母串类比**（Letter String Analogies）：继承者（successor）或前驱（predecessor）关系，如 [i j k] → [i j l]。
  - **语言类比**（Verbal Analogies）：同义词或反义词关系，如 “lazy : idle” vs “energetic : idle”。
- **Benchmark**：基于准确率（如Llama-3.1 70B在2-shot规则归纳任务上达到95%）。
- **对比方法**：
  - 与标准归纳头（prefix matching score）对比，发现弱相关（r=0.11）。
  - 与函数向量（Function Vectors）对比，发现符号归纳头与函数向量高度相关（r=0.86）。
  - 控制消融（替换为同层最低得分头）和随机消融基线。
- **模型家族**：GPT-2 (4个尺寸)、Gemma-2 (3个)、Qwen2.5 (4个)、Llama-3.1 (2个)，共计13个模型。

## 4. 资源与算力
- **明确说明**：
  - Llama-3.1 70B和Qwen2.5 72B实验使用**2块NVIDIA 80G H100 GPU**。
  - 其他较小模型使用**1块H100 GPU**。
  - 所有模型权重以bfloat16格式加载。
- **未说明**：训练时长，因为论文仅分析预训练模型，不涉及训练过程。

## 5. 实验数量与充分性
- **实验组数量**：
  - 三大任务（规则归纳、字母串类比、语言类比）均在Llama-3.1 70B上验证。
  - 规则归纳任务扩展至13个模型，包含不同尺寸和家族。
  - 因果中介分析覆盖所有注意力头（每个模型数百至数千个头）。
  - 消融实验逐步消除前h个头（h从1到H）。
  - 表征相似性分析使用40个令牌集。
  - 解码分析（线性探针）从200训练+100验证+200测试中评估泛化。
  - 错误分析比较正确和错误试次。
- **充分性与客观性**：
  - **充分**：多任务、多模型、多种分析方法（因果、注意、表征、消融、解码）交叉验证，结论一致。
  - **客观**：使用统计显著性检验（置换检验，family-wise error rate p<0.05），并设控制组和随机基线。
  - **公平**：对比了标准归纳头和函数向量，揭示了关系与差异；GPT-2系列表现差且未发现符号抽象头，说明机制与性能对应。

## 6. 论文的主要结论与发现
- **主要结论**：LLM内部涌现出三阶段符号架构，支持抽象推理。
  1. 符号抽象头在早期层将令牌转换为抽象变量。
  2. 符号归纳头在中间层对变量序列进行归纳。
  3. 检索头在后期层根据变量检索令牌值。
- **关键发现**：
  - 机制在三个不同任务上均存在，表明通用性。
  - 符号归纳头与函数向量高度一致，但不同于标准归纳头。
  - 符号抽象头实现类似“抽象器”（abstractor）架构。
  - 模型规模越大、训练数据越多，符号机制越显著。
  - 解码分析显示变量表示具有不变性（跨令牌集泛化准确率>98%）。
  - 错误分析显示正确试次中变量表示更纯净。

## 7. 优点：方法或实验设计上的亮点
- **方法创新**：提出并验证了LLM内部符号处理的完整三阶段机制，是首篇将符号抽象头、符号归纳头、检索头整合为统一架构的工作。
- **实验设计亮点**：
  - 双分离因果设计，巧妙区分变量与令牌。
  - 跨任务（规则、字母、语言）和跨模型（13个模型）验证，增强泛化性。
  - 结合多种分析工具（CMA、注意力图、RSA、消融、解码、错误分析），提供收敛证据。
  - 对比标准归纳头和函数向量，厘清了概念关系。
  - 公开代码和数据集，可复现。

## 8. 不足与局限
- **实验覆盖**：
  - 主要基于2-shot和10-shot设置，未探索更多shot数的影响。
  - 仅测试了同/不同、后继/前驱、同义/反义等简单关系，未涉及更复杂的推理（如数学推理、规划）。
  - GPT-2系列表现差，可能由于模型过小或训练数据不足，但未分析原因。
- **偏差风险**：
  - 因果中介分析假定可分离的线性干预，实际可能存在非线性交互。
  - 注意力分析仅基于正确试次，未系统分析错误试次的注意力模式。
  - 语言类比任务中，同义词/反义词的得分相关性低，表明存在任务特定专业化，但未深入探讨。
- **应用限制**：
  - 机制在更大模型（如GPT-4、Claude）上是否成立未知。
  - 目前的发现基于英文令牌，多语言泛化未测试。
  - 未讨论如何利用该机制改进LLM推理（如促进抽象或处理OOD）。

（完）
