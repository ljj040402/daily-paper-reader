---
title: "SHARP-Distill: A 68× Faster Recommender System with Hypergraph Neural Networks and Language Models"
title_zh: SHARP-Distill：基于超图神经网络和语言模型的68倍加速推荐系统
authors: "Saman Forouzandeh, Parham Moradi, Mahdi Jalili"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=3hYrORJndz"
tags: ["query:ai"]
score: 6.0
evidence: ICML 2025 AI研究论文，结合超图神经网络和语言模型
tldr: 该论文提出SHARP-Distill，一种基于知识蒸馏的推荐系统加速框架，结合超图神经网络和语言模型。教师模型利用超图捕获高阶交互关系，并通过预训练语言模型提取评论文本语义。通过对比学习保持结构一致性。实验表明在保持推荐质量的同时实现68倍推理加速，为高效推荐系统提供了新思路。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-3hyrorjndz/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1561, \"height\": 908, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-3hyrorjndz/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 794, \"height\": 426, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-3hyrorjndz/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 793, \"height\": 428, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-3hyrorjndz/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 808, \"height\": 397, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-3hyrorjndz/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 812, \"height\": 396, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-3hyrorjndz/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 855, \"height\": 428, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-3hyrorjndz/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1433, \"height\": 749, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-3hyrorjndz/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1468, \"height\": 771, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-3hyrorjndz/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1653, \"height\": 822, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-3hyrorjndz/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 858, \"height\": 438, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-3hyrorjndz/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 869, \"height\": 521, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-3hyrorjndz/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 748, \"height\": 392, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-3hyrorjndz/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 859, \"height\": 425, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-3hyrorjndz/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 791, \"height\": 384, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-3hyrorjndz/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 784, \"height\": 384, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-3hyrorjndz/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 789, \"height\": 384, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-3hyrorjndz/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 790, \"height\": 382, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-3hyrorjndz/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 850, \"height\": 421, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-3hyrorjndz/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 846, \"height\": 419, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-3hyrorjndz/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1405, \"height\": 628, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-3hyrorjndz/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1399, \"height\": 681, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-3hyrorjndz/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1398, \"height\": 680, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-3hyrorjndz/fig-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 1394, \"height\": 680, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-3hyrorjndz/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1783, \"height\": 765, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3hyrorjndz/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1772, \"height\": 449, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3hyrorjndz/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1443, \"height\": 464, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3hyrorjndz/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 883, \"height\": 500, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3hyrorjndz/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1628, \"height\": 371, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3hyrorjndz/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1321, \"height\": 311, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3hyrorjndz/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1775, \"height\": 340, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3hyrorjndz/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1458, \"height\": 489, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3hyrorjndz/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 986, \"height\": 237, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3hyrorjndz/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1076, \"height\": 664, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3hyrorjndz/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1803, \"height\": 433, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3hyrorjndz/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1168, \"height\": 439, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3hyrorjndz/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1720, \"height\": 267, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3hyrorjndz/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1360, \"height\": 441, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3hyrorjndz/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1340, \"height\": 354, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3hyrorjndz/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1330, \"height\": 388, \"label\": \"Table\"}]"
motivation: 现有推荐系统推理速度慢，需要同时捕捉高阶交互和文本语义。
method: 提出教师-学生蒸馏框架，教师使用超图神经网络和语言模型生成嵌入，结合对比学习约束。
result: 在保持推荐质量的同时，推理速度提升68倍。
conclusion: SHARP-Distill实现了高效且高质量的推荐，验证了超图与语言模型结合的有效性。
---

## Abstract
This paper proposes SHARP-Distill (\textbf{S}peedy \textbf{H}ypergraph \textbf{A}nd \textbf{R}eview-based \textbf{P}ersonalised \textbf{Distill}ation), a novel knowledge distillation approach based on the teacher-student framework that combines Hypergraph Neural Networks (HGNNs) with language models to enhance recommendation quality while significantly improving inference time. The teacher model leverages HGNNs to generate user and item embeddings from interaction data, capturing high-order and group relationships, and employing a pre-trained language model to extract rich semantic features from textual reviews. We utilize a contrastive learning mechanism to ensure structural consistency between various representations. The student includes a shallow and lightweight GCN called CompactGCN designed to inherit high-order relationships while reducing computational complexity. Extensive experiments on real-world datasets demonstrate that SHARP-Distill achieves up to 68× faster inference time compared to HGNN and 40× faster than LightGCN while maintaining competitive recommendation accuracy.

---

## 论文详细总结（自动生成）

# 论文详细中文总结：SHARP-Distill

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：现有基于图神经网络（GNN）的推荐系统虽然能建模用户-物品间的复杂交互，但存在两大痛点：一是依赖稀疏的用户-物品交互矩阵，导致交互捕捉困难；二是深度GNN层在推理时计算开销巨大，尤其是超图神经网络（HGNN）虽能捕获高阶关系，但推理时间过长（如数毫秒级），难以满足实时推荐需求。此外，结合预训练语言模型（如DeBERTa）从用户评论文本中提取语义特征可以缓解数据稀疏问题，但多模态融合缺乏有效的对齐机制。
- **核心问题**：如何设计一种知识蒸馏方法，将复杂HGNN教师模型的高阶结构知识高效迁移到轻量级学生模型，同时保持推荐准确率并大幅提升推理速度；如何对齐异构嵌入（结构嵌入与文本嵌入）且不损失各自特性；如何同时利用复杂网络的结构信息和位置信息。
- **整体含义**：提出SHARP-Distill框架，通过教师-学生蒸馏，结合超图神经网络和预训练语言模型，在保持推荐质量前提下实现**68倍推理加速**（vs. HGNN）和**40倍加速**（vs. LightGCN），使高效推荐系统实用化。

## 2. 提出的方法论

### 核心思想
基于教师-学生知识蒸馏框架，教师模型包含两个HGNN（分别处理用户和物品）和一个预训练语言模型DeBERTa，利用对比学习对齐多模态表示；学生模型设计了一个轻量级单层GCN（CompactGCN），通过软标签蒸馏、嵌入插值和对比学习（融合结构相似度和位置相似度）继承教师的高阶关系和拓扑知识。

### 关键技术细节
- **教师模型**：
  - 构建用户和物品的超图关联矩阵，使用超图拉普拉斯进行消息传播（公式3），得到用户和物品的嵌入 \( \mathbf{Z}^U_t, \mathbf{Z}^I_t \)。
  - DeBERTa提取评论文本嵌入 \( \mathbf{Z}^U_R, \mathbf{Z}^I_R \)。
  - 跨模态对比学习（公式4）对齐HGNN嵌入与DeBERTa嵌入；域内对比学习（公式5）增强结构一致性。
  - 融合后的嵌入送入MLP预测评分，监督损失为MSE，教师总损失结合监督损失和对比损失（公式10）。
  - 教师预测经温度缩放生成软标签（公式11-12），采用温度退火策略。
- **学生模型（CompactGCN）**：
  - 单层图卷积（公式14）：\(\mathbf{Z}_s = \hat{\mathbf{A}}_s \mathbf{X} \mathbf{W}_s\)，其中 \(\hat{\mathbf{A}}_s\) 是归一化邻接矩阵。
  - 嵌入插值（公式13）：融合学生和教师嵌入，参数γ控制平衡，早期依赖教师，后期转向自主表示。
  - 软标签蒸馏监督损失（公式15-16），结合硬标签和软标签（KL散度）。
  - **创新对比学习蒸馏**：不仅利用软标签，还引入基于超图的位置编码（公式17）定义节点拓扑位置，然后定义综合相似度（公式18）：结合嵌入余弦相似度和位置余弦相似度，参数α平衡两者。学生对比损失（公式19-20）对齐教师和学生表示。
  - 学生总损失 = 监督损失 + 对比损失（公式21）。

### 算法流程
分三个阶段：1）训练教师模型（HGNN+DeBERTa+对比学习）；2）训练学生模型（CompactGCN+位置编码对比蒸馏）；3）用学生模型进行推理。

## 3. 实验设计

### 数据集
- **五个真实数据集**：Yelp Tips、Amazon CDs、Amazon Cellphones、Amazon Beauty、Amazon Sports。
- 数据规模：用户数7,598~71,258，物品数6,208~65,443，评论数85,472~1,243,755。包含用户-物品交互和评论文本。

### 对比方法
- **超图方法**：LightGCN、HCCF、HGAtt、GCGM（图对比框架）。
- **大语言模型方法**：SAID（语义嵌入学习）、POD（提示蒸馏）。
- **知识蒸馏方法**：KRD（量化顶点知识蒸馏）、LightHGNN（HGNN-to-MLP）。
- 还额外对比了推荐系统专用蒸馏方法：UnKD（无偏蒸馏）和Graph-less。

### 评估指标
- **准确性**：Precision@10、Recall@10、NDCG@10、F1@10（部分）、Hit Ratio（HR@10,20,50）。
- **效率**：推理时间（ms）。
- **代表对齐**：Centered Kernel Alignment (CKA) 度量学生与教师表示相似度。

## 4. 资源与算力

- 论文未明确说明使用的GPU型号、数量或具体训练时长（但附录表5给出了训练时间：教师模型在Amazon CDs上4.2小时，学生模型0.3小时；Yelp上教师3.5小时，学生0.3小时）。总体算力消耗中等，学生模型仅0.5M参数，远小于教师的145M参数。
- **不足之处**：未报告GPU型号（如V100/A100）、是否单卡或多卡、batch size等详细信息，难以复现具体算力成本。

## 5. 实验数量与充分性

- **实验丰富**：在5个数据集上进行了主实验结果（表1，11项指标），HR对比（表2），推理时间与精度权衡（图4），推理时间缩放实验（表3，4种节点规模），消融实验（去除DeBERTa、去除对比学习、仅软标签、仅结构CL、仅位置CL等），超参数敏感性（温度、损失权重、学习率、嵌入维度），层数配置影响，训练数据比例影响，训练轮次影响，各类对比学习组合分析，CKA对齐分析，以及与其他蒸馏方法的全面对比（附录表7）。
- **充分性评估**：实验设计较全面，覆盖了准确性、效率、可扩展性、组件贡献、超参数鲁棒性。但未在更大规模（千万级）数据集上测试，也未涉及工业场景的在线A/B测试。对比方法涵盖主流类型，但缺少近年来更先进的LLM+推荐组合（如LLM-RecSys）的直接对比。

## 6. 主要结论与发现

- SHARP-Distill在5个数据集的11/15个准确率指标上取得最佳，尤其在Sports数据集上提升显著（P@10达4.27%，远高于次优3.56%）。
- 推理速度：学生模型在完整CDs数据集上仅9.77ms，相比HGNN（668ms）加速68×，比LightGCN（395ms）加速40×；在Yelp上类似。
- 消融实验：去除DeBERTa导致P@10下降约18.8%；去除对比学习下降29.4%；仅用软标签蒸馏效果远不如结合结构/位置CL。
- CKA分析：SHARP-Distill学生与教师表示对齐分数平均0.85，高于仅用HGNN（0.71）或DeBERTa（0.76），证明多模态融合有效。
- 知识蒸馏保留教师94.1%的性能，同时显著降低计算成本。

## 7. 优点

1. **方法创新**：首次将超图结构知识（位置编码）与对比学习结合用于知识蒸馏，超越传统软标签蒸馏，有效传递高阶拓扑信息。
2. **轻量高效**：CompactGCN仅0.5M参数，推理复杂度O(|E|d)，实现60+倍推理加速，同时保持或超越SOTA准确率。
3. **多模态融合**：教师模型融合HGNN和DeBERTa，并通过跨模态对比学习对齐，充分利用交互结构和评论文本。
4. **实验全面**：包括准确性、效率、可扩展性、详细消融、超参数分析，且从多个维度验证框架的有效性。
5. **实用价值**：为资源受限环境部署高质量推荐系统提供了可行方案，有助于降低能耗和计算成本。

## 8. 不足与局限

1. **实验规模有限**：最大数据集约130万条交互，未在超大规模（如亿级）或流式场景验证可扩展性。
2. **硬件信息不透明**：未报告GPU型号、数量、训练batch size，影响可复现性。
3. **对比方法时效性**：对比的LLM方法（SAID, POD）为2023-2024年，但对2024下半年以后更先进的LLM+推荐方法未纳入。
4. **冷启动问题**：论文未专门分析冷启动场景下（如新用户/新物品）的推荐效果，而评论文本可能有助于冷启动但未量化。
5. **隐私风险**：使用用户评论文本提取语义特征，可能涉及隐私问题，论文仅在“社会影响”部分简提，未提出具体缓解措施。
6. **潜在偏差**：训练数据来自Amazon和Yelp，可能引入平台偏差或用户行为偏差；未做公平性分析（性别、地域等）。

（完）
