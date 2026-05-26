---
title: "LoRANN: Low-Rank Matrix Factorization for Approximate Nearest Neighbor Search"
title_zh: LoRANN：基于低秩矩阵分解的近似最近邻搜索
authors: "Elias Jääsaari, Ville Hyvönen, Teemu Roos"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=wyYsCI3K7U"
tags: ["query:ai"]
score: 6.0
evidence: 用于机器学习流水线的近似最近邻搜索方法
tldr: 本文提出LoRANN，一种基于低秩矩阵分解的近似最近邻搜索方法。将内积近似视为多输出回归问题，采用降秩回归监督学习，在保持精度的同时显著提升查询速度，适用于RAG和向量数据库等场景。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-wyysci3k7u/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1441, \"height\": 477, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-wyysci3k7u/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1406, \"height\": 475, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-wyysci3k7u/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1405, \"height\": 476, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-wyysci3k7u/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1405, \"height\": 473, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-wyysci3k7u/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1404, \"height\": 473, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-wyysci3k7u/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1408, \"height\": 479, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-wyysci3k7u/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1413, \"height\": 1871, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-wyysci3k7u/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1413, \"height\": 1867, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-wyysci3k7u/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1412, \"height\": 1899, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-wyysci3k7u/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1415, \"height\": 1879, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-wyysci3k7u/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1382, \"height\": 907, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-wyysci3k7u/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1358, \"height\": 891, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-wyysci3k7u/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1415, \"height\": 1877, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-wyysci3k7u/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1416, \"height\": 1881, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-wyysci3k7u/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1414, \"height\": 1877, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-wyysci3k7u/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1413, \"height\": 935, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-wyysci3k7u/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1414, \"height\": 942, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-wyysci3k7u/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1449, \"height\": 771, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-wyysci3k7u/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1429, \"height\": 735, \"label\": \"Table\"}]"
motivation: 聚类近似最近邻算法查询速度慢于图方法，需效率提升。
method: 将内积近似看作多输出回归，用降秩回归求解。
result: 查询速度快于基于产品量化的聚类方法，且精度相当。
conclusion: 为大规模应用提供了高效的ANN搜索方案。
---

## Abstract
Approximate nearest neighbor (ANN) search is a key component in many modern machine learning pipelines; recent use cases include retrieval-augmented generation (RAG) and vector databases. Clustering-based ANN algorithms, that use score computation methods based on product quantization (PQ), are often used in industrial-scale applications due to their scalability and suitability for distributed and disk-based implementations. However, they have slower query times than the leading graph-based ANN algorithms. In this work, we propose a new supervised score computation method based on the observation that inner product approximation is a multivariate (multi-output) regression problem that can be solved efficiently by reduced-rank regression. Our experiments show that on modern high-dimensional data sets, the proposed reduced-rank regression (RRR) method is superior to PQ in both query latency and memory usage. We also introduce LoRANN, a clustering-based ANN library that leverages the proposed score computation method. LoRANN is competitive with the leading graph-based algorithms and outperforms the state-of-the-art GPU ANN methods on high-dimensional data sets.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **研究动机**：近似最近邻搜索（ANN）是检索增强生成（RAG）、向量数据库等现代机器学习流水线的关键组件。基于聚类的ANN算法（如使用乘积量化PQ）在工业规模化应用中具有可扩展性和分布式、磁盘友好等优势，但查询速度显著慢于领先的基于图的ANN算法（如HNSW、NGT）。
- **整体含义**：本文旨在通过一种新的监督式得分计算方法——降秩回归（Reduced-Rank Regression, RRR）来提升聚类ANN算法的查询效率，使其在速度上能与图方法竞争，同时保持聚类方法低内存、快速构建索引的优势。最终提出了LoRANN库，提供了CPU和GPU实现。

## 2. 论文提出的方法论
### 核心思想
- 将查询点与簇内点的内积近似视为一个多输出回归问题，其精确解为普通最小二乘（OLS）估计。通过降秩回归对参数矩阵施加秩约束，得到低秩近似解，从而大幅降低计算复杂度。

### 关键技术细节
- **问题建模**：对于簇 \( l \)，输出矩阵 \( Y = XC^T \)（\( X \) 为路由到该簇的训练查询，\( C \) 为簇内语料点），最小化 Frobenius 范数损失，约束 \( \text{rank}(\beta) \le r \)。
- **RRR解**：\( \hat{\beta}_{\text{RRR}} = C^T V_r V_r^T = A B \)，其中 \( V_r \) 是 \( Y \) 的前 \( r \) 个右奇异向量，\( A = C^T V_r \in \mathbb{R}^{d \times r} \)，\( B = V_r^T \in \mathbb{R}^{r \times m_l} \)。预测时计算 \( \hat{y} = (x^T A) B \)，复杂度 \( \Theta(r(d + m_l)) \)。
- **8-bit量化**：对 \( A, B \) 和查询 \( x \) 进行absmax量化，并用AVX-512 VNNI指令集高效计算8-bit向量矩阵乘法，进一步降低延迟和内存。
- **降维**：训练时用PCA投影到 \( s \) 维子空间（\( s < d \)），模型输入为 \( \tilde{x} = W_s^T x \)，输出仍为原始内积，可减少第一个矩阵乘的成本。
- **GPU实现**：将查询和簇模型组织为张量，利用JAX/XLA编译为高效批量矩阵乘法，使用16位浮点（FP16）而非8-bit整数（因GPU对8-bit支持有限）。

## 3. 实验设计
### 数据集与场景
- 使用了 **16 个标准及高维嵌入数据集**，涵盖维度 128 ~ 1536，包括：
  - 传统基准：fashion-mnist、gist、glove、mnist、sift
  - 现代高维嵌入：ag-news (DistilBERT/MiniLM)、arxiv (InstructXL/OpenAI Ada)、wiki (GTE-small/OpenAI Ada)、wolt (clip-ViT)、yandex T2I (OOD 场景)
- 评估指标：recall@100 vs Queries Per Second (QPS)。遵循 ANN-benchmarks 设置。

### 对比方法
- **基线聚类方法**：Faiss-IVF-PQ（4-bit PQ 快速扫描）、ScaNN（各向异性量化）
- **图方法**：HNSW、GLASS、QSG-NGT、PyNNDescent
- **树方法**：MRPT
- **GPU方法**：Faiss IVF/IVF-PQ、RAFT IVF/IVF-PQ、RAFT CAGRA

## 4. 资源与算力
- **CPU实验**：AWS r6i.4xlarge 实例（Intel Xeon 8375C Ice Lake，禁用超线程），单核运行。
- **GPU实验**：AWS g5.2xlarge（NVIDIA A10G，24 GB VRAM）；此外还有 Apple M2 Pro SoC（mac2-m2pro.metal实例）。
- **索引构建时间**：在表2中给出，但文中未明确报告总训练GPU时长或总能耗。实验重复5次取最低延迟，未提供完整的算力消耗统计。

## 5. 实验数量与充分性
- **实验组数**：
  - 固定聚类对比（§7.1.1）：8个数据集，两种簇数设置。
  - 内存占用对比（§7.1.2）：8个数据集，多种码率（b ≈ 16/32/64/128）。
  - 消融实验（§7.2.1）：在大部分数据集上分别测试IVF、+RRR、+DR（降维）、+8-bit量化。
  - CPU端到端（§7.2.2）：16个数据集，对比多个算法。
  - GPU端到端（§7.2.3）：9个高维+若干低维数据集。
  - OOD实验（§5）：基于Yandex T2I数据集的特殊设置。
  - 秩参数影响实验（附录E.2）：改变r=16/32/64。
- **充分性与公平性**：
  - 实验相当充分，覆盖了多种维度、规模、距离度量（欧氏、内积、余弦）。
  - 使用ANN-benchmarks标准框架，对比方法是当前最先进的并公开可用。
  - 在 §7.1.1 和 §7.1.2 中保证了聚类固定或内存水平相同，比较公平。
  - 消融实验有效验证了各模块贡献。
  - 存在缺少统计误差棒的问题（ANN领域惯例），但多次重复并取最优延迟，可接受。

## 6. 主要结论与发现
1. **RRR显著优于PQ**：在固定聚类和相同内存预算下，RRR在所有数据集上均比PQ获得更高的QPS（相同召回率），部分数据集上RRR@b≈16甚至超过PQ@b≈128（8倍内存）。
2. **LoRANN在CPU端**：在大多数数据集上，LoRANN在召回率90%以下优于或等于领先图方法GLASS，在召回率高时图方法略优。LoRANN全面超过其他聚类方法（Faiss-IVF-PQ、ScaNN）。
3. **GPU端**：LoRANN在高维（d>300）数据集上优于CAGRA等其它GPU方法，在低维上不如CAGRA。
4. **OOD适应性**：使用真实查询分布进行训练可大幅提升性能，且训练集更大时效果更好。
5. **索引构建时间**：LoRANN一般快于图方法（尤其QSG-NGT、HNSW），但慢于Faiss-IVF-PQ。

## 7. 优点
- **方法创新**：将内积近似重新解释为回归问题，并采用降秩回归这一成熟统计工具，简化了产品量化（PQ）的复杂优化。
- **高效实现**：结合8-bit量化和AVX-512指令，取得了极低延迟和低内存占用。
- **OOD鲁棒性**：由于是有监督回归，自然适应查询分布变化，实验验证了这一点。
- **简单且易于移植**：GPU实现仅需将计算表示为矩阵乘法，易于用JAX/PyTorch等框架部署，并支持Apple Silicon。
- **实验全面**：对比了多个主流ANN库，包含传统和现代高维数据集，消融实验充分验证了各组件。
- **开源**：提供了LoRANN库及实验代码，可复现。

## 8. 不足与局限
- **高召回率局限**：在召回率>90%时，需要探索大量簇，速度不如图方法（如GLASS）。这是聚类方法的固有特性，本文并未完全解决。
- **低维数据不适用**：当维度d较小时（如<100），秩r必须相应增大使得r/d比例过高，降秩回归的计算优势消失。
- **仅支持内积相关度量**：对于非内积相似度（如Jaccard、Hellinger），需另行扩展回归公式。
- **索引构建时间优化不足**：当前实现未完全并行化，部分数据集（如ann-t2i）索引构建时间较长（916s），有改进空间。
- **实验算力披露不完整**：未报告总GPU运行时长、能耗等，可复现性受限于环境依赖；
- **统计显著性缺失**：未提供误差棒或置信区间，虽然符合领域惯例，但削弱了不同方法之间差异的严谨性。

（完）
