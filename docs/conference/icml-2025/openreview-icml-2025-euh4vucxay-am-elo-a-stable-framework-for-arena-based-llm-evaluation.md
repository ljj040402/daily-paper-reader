---
title: "am-ELO: A Stable Framework for Arena-based LLM Evaluation"
title_zh: am-ELO：基于竞技场的大语言模型评估稳定框架
authors: "Zirui Liu, Jiatong Li, Yan Zhuang, Qi Liu, Shuanghong Shen, Jie Ouyang, Mingyue Cheng, Shijin Wang"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=EUH4VUCXay"
tags: ["query:ai"]
score: 6.0
evidence: ICML 2025关于大语言模型评估方法的论文
tldr: 该论文提出am-ELO，一种稳定的竞技场式LLM评估框架。针对传统ELO系统的排名不一致问题，采用最大似然估计替代迭代更新，并证明其一致性和稳定性。进一步通过融入标注者能力差异，提升了评估的鲁棒性。在多个LLM对战数据上展示了更可靠的排名结果。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-euh4vucxay/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 840, \"height\": 561, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-euh4vucxay/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 848, \"height\": 514, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-euh4vucxay/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1754, \"height\": 744, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-euh4vucxay/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 602, \"height\": 430, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-euh4vucxay/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 847, \"height\": 424, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-euh4vucxay/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1763, \"height\": 733, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-euh4vucxay/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 773, \"height\": 673, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-euh4vucxay/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 867, \"height\": 475, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-euh4vucxay/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 860, \"height\": 428, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-euh4vucxay/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 703, \"height\": 368, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-euh4vucxay/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 707, \"height\": 212, \"label\": \"Table\"}]"
motivation: 现有ELO评分系统在LLM评估中存在排名不一致和忽略标注者差异。
method: 用最大似然估计替代迭代更新，并修改概率函数以融入标注者能力。
result: 理论证明一致性，实验显示更稳定可靠的排名。
conclusion: am-ELO为LLM竞技场评估提供了理论严谨且稳定的解决方案。
---

## Abstract
Arena-based evaluation is a fundamental yet significant evaluation paradigm for modern AI models, especially large language models (LLMs). Existing framework based on ELO rating system suffers from the inevitable instability problem due to ranking inconsistency and the lack of attention to the varying abilities of annotators. In this paper, we introduce a novel stable arena framework to address these issues by enhancing the ELO Rating System. Specifically, we replace the iterative update method with a Maximum Likelihood Estimation (MLE) approach, m-ELO, and provide theoretical proof of the consistency and stability of the MLE approach for model ranking. Additionally, we proposed the am-ELO, which modify the Elo Rating’s probability function to incorporate annotator abilities, enabling the simultaneous estimation of model scores and annotator reliability. Experiments demonstrate that this method ensures stability, proving that this framework offers a more robust, accurate, and stable evaluation method for LLMs.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）
- **问题**：现有基于ELO评分系统的竞技场式LLM评估存在两个严重缺陷：
  - **排名不一致**：传统ELO采用迭代更新，结果对数据顺序高度敏感，同一批数据不同顺序会得到不同分数。
  - **忽略标注者差异**：所有标注者被视为同质化，未考虑其能力、偏好或可靠性差异，导致偏差和评估不稳定。
- **意义**：竞技场式评估（如Chatbot Arena）被广泛用于LLM能力对比，不稳定的评分会误导模型选择和研究方向。因此需要一种**理论严谨且稳定的评估框架**，既能消除数据顺序影响，又能建模标注者个性。

### 2. 论文提出的方法论
- **核心思想**：将ELO评分从迭代更新改为**最大似然估计（MLE）**，并引入标注者能力参数，实现模型分数与标注者可靠性的联合估计。
- **关键技术细节**：
  1. **m-ELO**（MLE驱动的ELO）：
     - 将传统ELO的评分看作在线梯度下降的一次采样，而MLE基于整个数据集一次优化。
     - 对数似然函数：`ln L = Σ Wij ln P(Ri,Rj) + Wji ln P(Rj,Ri)`，其中`P(Ri,Rj)=1/(1+e^{-C(Ri-Rj)})`。
     - 梯度与ELO更新式结构一致，但通过全局优化消除顺序敏感性。
     - 理论证明（Theorem 4.1）：固定一个模型分数后，对数似然函数是凹函数，有唯一最大值点，保证MLE解的一致性。
  2. **am-ELO**（Annotator-aware MLE-ELO）：
     - 将概率函数中的固定常数`C`替换为标注者能力参数`θ_k`：`P(Ri,Rj|θ_k)=1/(1+e^{-θ_k(Ri-Rj)})`。
     - 同时学习模型分数`R`和标注者能力`Θ`，梯度公式见式(6)。
     - 归一化约束：强制所有`θ_k`之和为1（假设多数标注者正常），避免全局缩放导致的排名反转。
  3. **稳定竞技场框架**（Algorithm 3）：
     - 动态收集新数据；过滤标注记录过少的标注者（低于阈值`δ`）；运行am-ELO；再根据能力阈值`ϵ`剔除异常标注者（如`θ_k < 0`的）。

### 3. 实验设计
- **数据集**：Chatbot Arena真实标注数据集（2023年4-6月，33k对话，13000个IP）。预处理后保留**42个标注者**（每人≥50条记录）、**20个模型**、**4321条对战日志**。
- **基准方法**：
  - **传统ELO**：迭代更新，重复1000次随机打乱后取平均。
  - **m-ELO**：MLE求解，梯度下降（lr=0.1，epoch=2000）。
  - **am-ELO**：加入标注者能力的MLE，训练同m-ELO。
- **评估指标**：MSE、AUC（预测标注结果）；损失函数值；排名一致性（五次随机初始化）；稳定性实验采用四种扰动策略（Random, Equal, Flip, Mixed）模拟异常标注者。

### 4. 资源与算力
- **论文未明确说明**使用的GPU型号、数量或训练时长。仅提到梯度下降实验的学习率0.1，迭代2000次。推测算力需求较低（只有几千条记录、42个标注者），普通GPU即可完成。

### 5. 实验数量与充分性
- **实验组数**：
  - 预测性能对比（表2）：MSE和AUC。
  - 排名可视化与案例分析（图3、图4）：展示了各模型的归一化ELO分数和损失。
  - 收敛性与效率（图5）：记录loss和一致性随epoch变化。
  - 稳定性实验（图6、图7）：四种扰动比例0%~50%，统计排名一致性和异常检测F1分数。
- **充分性评价**：
  - **充分**：覆盖了预测能力、收敛性、排名稳定性、异常检测等关键维度。
  - **公平性**：与传统ELO、m-ELO、am-ELO（w/o Norm）对比，扰动实验在多种场景下验证，F1分数达90%~95%。
  - **略弱**：未在不同数据集或更大规模标注者上验证，但论文承认数据来源单一。

### 6. 论文的主要结论与发现
1. **m-ELO消除了数据顺序敏感性**，且与传统ELO共享相同的概率函数，理论保证了排名一致性。
2. **am-ELO可同时估计模型分数和标注者能力**，其概率函数建模有效：能力高的标注者（θ>0）的标注与整体排名更一致；能力为负的标注者可直接识别为异常。
3. **稳定性大幅提升**：在四种扰动下，am-ELO将排名不一致率降低至传统ELO的30%左右；异常检测F1在阈值0.005时可达95%。
4. **实际案例分析**：传统ELO会因模型频繁击败弱对手而高估其分数，am-ELO纠正了这种偏差（如vicuna-7b排名高于koala-13b，与人类直觉更相符）。

### 7. 优点
- **理论扎实**：给出了MLE的凹性证明（Theorem 4.1）和标注者能力估计的语义解释（Theorem 4.2），方法论有坚实数学基础。
- **实用性强**：am-ELO不仅提高排名稳定性，还能自动检测注释质量，可用于众包标注的质量控制和奖励分配。
- **效率可控**：梯度下降仅需2000步收敛，计算开销低；同时支持Newton加速（文中提及）。
- **可解释性**：标注者能力θ直接反映其判别力与一致性，便于平台运营。

### 8. 不足与局限
- **标注者建模维度单一**：仅通过一个参数θ捕捉“判别能力”，忽略了标注者其他特质（如对某些主题的偏向、一致性变化），未来可借鉴多维IRT。
- **实验覆盖有限**：仅使用一个数据集（Chatbot Arena），未在更多LLM评估场景（如多语言、多轮对话）验证泛化性。
- **依赖假设**：归一化假设“多数标注者正常”，若实际数据中异常标注者占多数，方法可能失效。
- **阈值选择依赖人工**：数据量阈值δ和能力阈值ϵ需要人工设定，未讨论自动优化方法。

（完）
