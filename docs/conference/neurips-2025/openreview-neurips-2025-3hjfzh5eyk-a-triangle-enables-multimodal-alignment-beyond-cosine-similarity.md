---
title: A TRIANGLE Enables Multimodal Alignment Beyond Cosine Similarity
title_zh: TRIANGLE：实现超越余弦相似度的多模态对齐
authors: "Giordano Cicchetti, Eleonora Grassucci, Danilo Comminiello"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=3Hjfzh5Eyk"
tags: ["query:ai"]
score: 4.0
evidence: 多模态对齐的新相似度度量
tldr: 该论文提出TRIANGLE（三模态神经几何学习），一种新型相似度度量，用于多模态对齐，超越余弦相似度的局限。该方法能提供模态是否有效对齐的指标，避免因对齐不足导致下游任务性能下降。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-3hjfzh5eyk/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1385, \"height\": 339, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3hjfzh5eyk/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1370, \"height\": 461, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3hjfzh5eyk/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1301, \"height\": 369, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3hjfzh5eyk/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 718, \"height\": 578, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3hjfzh5eyk/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 864, \"height\": 474, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3hjfzh5eyk/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1303, \"height\": 476, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3hjfzh5eyk/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1360, \"height\": 648, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-3hjfzh5eyk/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1452, \"height\": 760, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3hjfzh5eyk/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1023, \"height\": 542, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3hjfzh5eyk/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 877, \"height\": 320, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3hjfzh5eyk/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 728, \"height\": 395, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3hjfzh5eyk/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1446, \"height\": 145, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3hjfzh5eyk/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1231, \"height\": 300, \"label\": \"Table\"}]"
motivation: 现有多模态模型缺乏对齐有效性指标，可能导致模态未对齐。
method: 设计基于神经几何学习的相似度度量，提供对齐指示。
result: 有效检测并对齐多模态表示。
conclusion: 推动多模态学习的可靠对齐。
---

## Abstract
Multimodal learning plays a pivotal role in advancing artificial intelligence systems by incorporating information from multiple modalities to build a more comprehensive representation. Despite its importance, current state-of-the-art models still suffer from severe limitations that prevent the successful development of a fully multimodal model. Such methods do not provide indicators that all the involved modalities are effectively aligned. As a result, a set of modalities may not be aligned, undermining the effectiveness of the model in downstream tasks where multiple modalities should provide additional information that the model fails to exploit. 
In this paper, we present TRIANGLE: TRI-modAl Neural Geometric LEarning, the novel proposed similarity measure that is directly computed in the higher-dimensional space spanned by the modality embeddings. TRIANGLE improves the joint alignment of three modalities via a triangle‑area similarity, avoiding additional fusion layers.
When incorporated in contrastive losses replacing cosine similarity, TRIANGLE significantly boosts the performance of multimodal modeling, while yielding interpretable alignment rationales. Extensive evaluation in three-modal tasks such as video-text and audio-text retrieval or audio-video classification, demonstrates that TRIANGLE achieves state-of-the-art results across different datasets improving the performance of cosine-based methods up to 9 points of Recall@1.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **背景**：多模态学习旨在融合来自不同感官通道的信息（如视觉、听觉、文本）以构建更全面的表示。CLIP等模型通过对比学习对齐图像-文本对，后续工作（如CLAP、ImageBind、LanguageBind）尝试扩展到三个或更多模态，但核心对齐方式仍依赖**成对余弦相似度**。
- **核心问题**：现有方法存在以下缺陷：
  - 通常选择一个模态作为锚点，将其他模态与锚点逐一对齐，但**无法保证非锚点模态之间的对齐**（例如视频与语言对齐、音频与语言对齐，但视频与音频可能未对齐）。
  - 缺乏几何指标来指示所有模态是否真正相互对齐，导致模型在多模态数据中无法有效利用第三个模态的关键信息（如视频中音频信息对区分相似画面至关重要）。
  - 许多方法通过额外融合层或辅助损失来缓解，但增加了复杂性，且仍无法提供可解释的对齐度量。
- **动机**：设计一种**直接在高维空间中联合对齐三个模态**的相似度量，既能提升对齐效果，又能提供可解释性，且无需额外融合层。

## 2. 方法论

### 2.1 核心思想

- **高维空间中的三角形**：三个模态的归一化嵌入向量（位于单位超球面）在高维空间中确定一个三角形，该三角形的**面积**直接反映三个嵌入的相似度：面积越小，向量越接近，即模态对齐越好；面积越大，向量越分散。
- **三角形面积公式**（无需降维）：
  - 设三个模态嵌入为 x、y、z，定义 u = x - y，v = x - z，则面积为：
    \[ A = \frac{1}{2} \sqrt{\langle u, u\rangle \langle v, v\rangle - \langle u, v\rangle^2} \]
    该公式仅依赖于点积，可在任意维度计算。

### 2.2 关键技术细节

- **对比损失替换**：将传统对比损失中的余弦相似度替换为**负的三角形面积**（因为面积越小越好，用 -A 作为相似度）。
  - 文本到视频-音频检索损失（LD2T）和视频-音频到文本检索损失（LT2D）：
    \[ L = -\frac{1}{B} \sum_{i=1}^B \log \frac{\exp(-A(t_i, v_i, a_i)/\tau)}{\sum_{j=1}^B \exp(-A(t_j, v_i, a_i)/\tau)} \]
    及对称形式。
- **下游任务正则化**：为防止三角形面积在所有向量共线时失效（此时面积为零但可能对齐不良），加入**对应两个主要模态的余弦相似度正则项**：
    \[ A_{\text{reg}} = \frac{1}{2} \sqrt{\langle u, u\rangle\langle v, v\rangle - \langle u, v\rangle^2} - \alpha \cos\theta_{xy} \]
    其中 θ_{xy} 是下游任务中最相关的两个模态（如视频-文本检索中的视频与文本）的夹角。
- **附加损失**：Data Text Matching (DTM) 损失，用于进一步强化文本与视频-音频的匹配。
- **总损失**：\[ L_{\text{TOT}} = \frac{1}{2}(L_{D2T} + L_{T2D}) + \lambda L_{\text{DTM}} \]

### 2.3 算法流程（文字说明）

1. 使用三个编码器（视频、音频、文本）分别提取嵌入向量，并归一化到单位超球面。
2. 对于每个样本的三元组，计算三角形面积。
3. 在对比损失中用负面积代替余弦相似度，对比批次内正负样本对。
4. 可选地加上余弦正则项（针对主要任务模态）。
5. 总损失包含对比损失和DTM损失，联合优化编码器参数。

## 3. 实验设计

### 3.1 数据集与场景

| 数据集 | 模态 | 任务 | 规模 |
|--------|------|------|------|
| MSR-VTT | 视频+音频+文本 | 零样本视频检索 (T2V / V2T) | 9000训练/1000测试 |
| DiDeMo | 同上 | 零样本视频检索 | 1003测试 |
| ActivityNet | 同上 | 零样本视频检索 | 4917测试 |
| VATEX | 同上 | 零样本视频检索 | 431测试（子集） |
| AudioCaps | 音频+文本 | 零样本音频检索 (T2A) | 700测试 |
| VGGSound (5K子集) | 音频+视频+文本 | 零样本音频-视频分类 | 5000测试 |
| MNIST+AudioMNIST | 图像+音频+文本 | 可控环境下检索（vanilla实验） | 数字0-9 |

### 3.2 Benchmark 与对比方法

- **对比基线**：
  - 双模态方法：CLIP、CLIP4Clip、UMT、ImageBind、LanguageBind、InternVideo2、VideoPrism、GRAM、VAST等。
  - 三模态方法：VALOR、VAST、GRAM、Symile等（其中VAST使用相同骨干网络与预训练数据，是最直接基线）。
- **评估指标**：Recall@1、Recall@10（零样本设定）。

### 3.3 实验设置

- **骨干网络**：文本-BERT-B，音频-BEATs，视频-EVAClip-ViT-G（总参数1.3B），继承自VAST。
- **预训练**：在VAST27M数据子集（150k样本）上微调10k steps，每100步在MSR-VTT验证最佳checkpoint。
- **从头训练**：在MSR-VTT训练集上从头训练4个epoch，编码器无预训练知识。
- **消融实验**：对正则化权重α、DTM损失权重λ、有无DTM、不同损失函数（余弦、Symile、GRAM、TRIANGLE）进行对比。
- **额外验证**：在Touch-Vision-Language数据集上测试不同模态组合。

## 4. 资源与算力

- **论文明确提到**：
  - 预训练和从头训练均使用 **4 × A100 GPU**。
  - 预训练：10k steps，batch size 256，学习率1e-4线性衰减。
  - 从头训练：4 epochs，batch size 64，学习率1e-4。
- **计算耗时对比**：计算三角形面积（3个2048维向量）仅需0.0016秒，余弦相似度需0.0001秒（batch=256，RTX4080），开销可忽略。

## 5. 实验数量与充分性

### 5.1 实验数量
- **主要实验**：6个标准数据集×2个子任务（T2V/V2T或T2A/分类），共约10+组主要结果（Table 1、Table 2）。
- **可控环境实验**：MNIST+AudioMNIST上的vanilla对比（图4）。
- **从头训练实验**：MSR-VTT从头训练对比（Table 3）。
- **消融实验**：正则化权重α（图7）、DTM损失权重λ（Table 6）、有无DTM（Table 3）、不同损失函数（Table 3）。
- **额外模态实验**：Touch-Vision-Language数据集（Table 5）。
- **定性分析**：三个VGGSound示例的Top-5检索结果。

### 5.2 实验充分性与客观性
- **充分性**：覆盖了主流多模态检索和分类任务，包含了零样本、从头训练、可控环境等多种场景。消融实验比较全面。统计显著性检验（p<0.001或p<0.05）也被报告。
- **公平性**：
  - 与VAST对比时使用完全相同骨干网络和预训练数据（仅修改损失函数），确保公平。
  - 与GRAM、Symile等比在相同设置下对比。
  - 数据集分割、指标等遵循标准惯例。
- **潜在局限**：预训练数据只用了VAST27M的子集（150k），未在全量数据上验证；VGGSound因YouTube政策只用了5k子集；未在更大规模模型（如>1.3B）上测试。

## 6. 主要结论与发现

1. **TRIANGLE在零样本视频检索上全面超越SOTA**：在MSR-VTT、DiDeMo、ActivityNet、VATEX上，T2V和V2T的R@1均最高，相比VAST最高提升**8.8个点**（V2T on MSR-VTT）。
2. **在零样本音频检索和分类上也达到SOTA**：AudioCaps上R@1达32.2（+0.1 vs VAST），VGGSound上R@1达44.8（+5.2 vs VAST）。
3. **从头训练中TRIANGLE优于余弦、Symile、GRAM**：同样编码器下，TRIANGLE的R@1显著更高（39.4 vs VAST 36.5，GRAM 38.9）。
4. **三角形面积可解释**：训练过程中正配对面积下降，R@1上升（图6），表明面积度量与对齐质量一致。
5. **正则化α有效**：适量余弦正则（α=1）能进一步提升T2V任务，但对V2T影响较小（图7）。
6. **TRIANGLE适用于不同模态组合**：在Touch-Vision-Language数据上也超越原方法（TVL）。

## 7. 优点

- **创新性**：首次提出使用**高维空间三角形面积**作为三模态对齐的相似度量，替代传统的成对余弦相似度，从根本上解决了多模态对齐中缺失非锚点对齐信息的问题。
- **可解释性**：面积直接度量三个嵌入的聚拢程度，训练中面积减小对应性能提升，提供了直观的几何解释。
- **简洁高效**：无需额外融合层、无需锚点选择，计算开销极小（仅为余弦相似度的16倍，但绝对时间可忽略）。
- **实验全面且公平**：对比方法覆盖主流SOTA，且与最相关基线（VAST）保持码架构和预训练数据一致，统计检验显著。
- **泛化能力**：在多个数据集、多个任务（检索/分类）上一致提升，且在从头训练和可控制实验中验证了鲁棒性。

## 8. 不足与局限

- **仅针对三个模态**：论文方法目前严格针对三个模态（三角形），虽然讨论了扩展到n模态（多边形分解）的思路，但**未提供具体实现或实验验证**。对于实际中可能出现的四个及以上模态，需额外工作。
- **预训练规模有限**：预训练仅使用VAST27M的150k子集（而非全量），可能未充分发挥能力。全量预训练的效果未报告。
- **数据集覆盖有限**：VGGSound仅用5k子集；ActivityNet和VATEX测试集较小；未在如HowTo100M等更大规模视频数据集上验证。
- **对余弦正则化敏感**：最优α需在验证集上调整（α=0或1），不同任务可能不同，增加了调参成本。
- **未讨论负样本的影响**：损失函数中负样本区域的计算方式仍与余弦相似度对比学习类似，但未分析负样本区域特性（如负样本是否也形成大区域）。
- **应用限制**：仅针对检索和分类任务，未在生成任务（如视频描述生成、QA）上验证。
- **资源信息较简略**：虽然提供了GPU数量和step数，但未给出具体训练耗时（小时数）、显存占用等，可能影响可复现性。

---

（完）
