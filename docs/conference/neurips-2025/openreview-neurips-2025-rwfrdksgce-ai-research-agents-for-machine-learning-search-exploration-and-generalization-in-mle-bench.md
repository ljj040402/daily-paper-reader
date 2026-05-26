---
title: "AI Research Agents for Machine Learning: Search, Exploration, and Generalization in MLE-bench"
title_zh: AI研究代理：MLE-bench中的搜索、探索与泛化
authors: "Edan Toledo, Karen Hambardzumyan, Martin Josifoski, RISHI HAZRA, Nicolas Baldwin, Alexis Audran-Reiss, Michael Kuchnik, Despoina Magka, Minqi Jiang, Alisia Maria Lupidi, Andrei Lupu, Roberta Raileanu, Tatiana Shavrina, Kelvin Niu, Jean-Christophe Gagnon-Audet, Michael Shvartsman, Shagun Sodhani, Alexander H Miller, Abhishek Charnalia, Derek Dunfield, Carole-Jean Wu, Pontus Stenetorp, Nicola Cancedda, Jakob Nicolaus Foerster, Yoram Bachrach"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=RwfrdKSgCE"
tags: ["query:ai"]
score: 6.0
evidence: AI研究代理自动化机器学习
tldr: 该论文将AI研究代理人形式化为在候选解空间中搜索的策略，通过系统设计不同的算子集和搜索策略（贪婪、MCTS、进化），发现其相互作用对性能至关重要。最佳组合在MLE-bench上取得了突破性结果。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-rwfrdksgce/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 714, \"height\": 452, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rwfrdksgce/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1076, \"height\": 607, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rwfrdksgce/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1006, \"height\": 367, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rwfrdksgce/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1181, \"height\": 449, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rwfrdksgce/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1195, \"height\": 502, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rwfrdksgce/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1494, \"height\": 339, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rwfrdksgce/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 338, \"height\": 338, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rwfrdksgce/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 911, \"height\": 739, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rwfrdksgce/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1439, \"height\": 440, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rwfrdksgce/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1439, \"height\": 396, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rwfrdksgce/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1446, \"height\": 860, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rwfrdksgce/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1443, \"height\": 496, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rwfrdksgce/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1437, \"height\": 1278, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rwfrdksgce/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1444, \"height\": 1442, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rwfrdksgce/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1036, \"height\": 1884, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rwfrdksgce/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1598, \"height\": 1814, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rwfrdksgce/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1746, \"height\": 2022, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-rwfrdksgce/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 649, \"height\": 297, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rwfrdksgce/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1452, \"height\": 218, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rwfrdksgce/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1441, \"height\": 1908, \"label\": \"Table\"}]"
motivation: AI研究代理有望加速科学进展，但方法设计缺乏系统理解。
method: 将代理视为搜索策略，通过变化算子集和搜索策略进行实验，分析其影响。
result: 发现搜索策略与算子集的精心配对显著提升Kaggle竞赛性能。
conclusion: 系统化设计搜索策略与算子是构建高效AI研究代理的关键。
---

## Abstract
AI research agents are demonstrating great potential to accelerate scientific progress by automating the design, implementation, and training of machine learning models. We focus on methods for improving agents' performance on MLE-bench, a challenging benchmark where agents compete in Kaggle competitions to solve real-world machine learning problems. We formalize AI research agents as search policies that navigate a space of candidate solutions, iteratively modifying them using operators. By designing and systematically varying different operator sets and search policies (Greedy, MCTS, Evolutionary), we show that their interplay is critical for achieving high performance. Our best pairing of search strategy and operator set achieves a state-of-the-art result on MLE-bench lite, increasing the success rate of achieving a Kaggle medal from 39.6% to 47.7%. Our investigation underscores the importance of jointly considering the search strategy, operator design, and evaluation methodology in advancing automated machine learning.

---

## 论文详细总结（自动生成）

好的，作为一名资深学术论文分析助手，我将严格按照您的要求，对这篇论文进行结构化、深入、客观的中文总结。

---

### **论文核心分析与总结**

#### **1. 论文的核心问题与整体含义（研究动机和背景）**

*   **核心问题**：当前AI研究代理（如AIDE）的性能提升是一个“黑箱”，其设计耦合了多个因素（算法、实现、算力），导致难以识别性能瓶颈。论文旨在通过形式化和解耦研究代理的设计组件，系统性地分析哪些因素是性能提升的关键，以及如何设计更优的代理。
*   **整体含义**：该研究将AI研究代理形式化为一种搜索算法，由两个核心组件构成：**搜索策略**和**算子**。通过系统性地变化这两部分，揭示了二者之间的相互作用关系。研究发现，算子是当前性能提升的主要瓶颈，改进算子比使用更复杂的搜索策略（如MCTS、进化算法）能带来更显著的性能提升。最终，通过设计更好的算子集合，并在AIRA-dojo框架中实现，论文在MLE-bench基准测试上取得了新的最佳成绩（SOTA）。这为如何系统化设计高性能AI研究代理提供了重要的理论和实践指导。

#### **2. 论文提出的方法论：核心思想、关键技术细节**

*   **核心思想**：将AI研究代理建模为一个在**图结构搜索空间**中运行的搜索算法。
    *   **搜索空间**：由节点（候选解决方案，即Python代码）和边（通过算子对节点进行的变换）构成的有向图。
    *   **框架定义**：一个图搜索算法由以下五元组定义： `(F, π_sel, O, π_op, τ)`
        *   `F` (适应度函数)：评估节点质量（论文中为5折交叉验证分数）。
        *   `π_sel` (选择策略)：选择哪些节点去进行操作（例如贪婪、MCTS、进化选择）。
        *   `O` (算子集)：用于变换/生成新节点的方法（例如 Draft、Improve、Debug）。
        *   `π_op` (算子策略)：决定在选定的节点上应用哪个算子。
        *   `τ` (终止规则)：何时停止搜索（例如达到时间或节点数上限）。
*   **关键技术细节——AIRA代理**：
    1.  **AIRA算子集 (O_aira)**：这是论文最重要的技术贡献，相较于基线AIDE (O_aide) 算子集进行了以下改进：
        *   **提示自适应复杂度 (Prompt-adaptive complexity)**：根据子节点数量动态调整 Draft 和 Improve 算子的提示，引导生成从“简单”到“高级”不同复杂度的方案，避免过早过拟合。
        *   **作用域记忆 (Scoped memory)**：Memory算子根据当前使用的算子提取不同类型的记忆。Draft和Improve算子获取**兄弟节点**的记忆以促进多样性；Debug算子获取**祖先节点**的记忆以避免重复错误修复。
        *   **思考令牌 (Think Tokens)**：针对推理模型（如DeepSeek R1），在系统提示中明确鼓励使用思考令牌进行推理和反思。
        *   **引入交叉算子 (Crossover Operator)**：新增一个交叉算子，用于重组两个有效解决方案的优异部分，从而生成新的候选方案。
    2.  **搜索策略**：
        *   **AIRA GREEDY**：使用AIRA算子集，但搜索策略与AIDE相同（贪婪选择最佳节点）。
        *   **AIRA MCTS (蒙特卡洛树搜索)**：使用AIRA算子集，遵循MCTS的标准流程（选择、扩展、评估、反向传播），并为UCT公式中的探索常数 `c` 设定了特定值。
        *   **AIRA EVO (进化搜索)**：使用AIRA算子集，维护一个固定大小的种群，通过适应度比例选择父代，通过Improve或Crossover算子生成子代，并替换适应度最低的个体。

#### **3. 实验设计**

*   **数据集/场景**：主要使用 **MLE-bench lite**，这是一个从MLE-bench中精选出的22个Kaggle任务的子集。部分实验（附录E）也使用了包含75个任务的完整 **MLE-bench**。
*   **Benchmark**：MLE-bench是评估机器学习工程代理的公开基准。其核心评价指标是**奖牌成功率（Medal Success Rate）**，即代理在任务中获得任意奖牌（铜、银或金）的比例。
*   **对比方法**：
    *   **基线方法**：原始的AIDE代理（使用o1-preview模型）[OAI] AIDE Greedy o1-preview
    *   **同环境基线**：将AIDE代理在论文自己开发的AIRA-dojo环境中重新实现 [DOJO] AIDE Greedy o1-preview / R1 / o3
    *   **论文提出的AIRA代理**：AIRA Greedy, AIRA MCTS, AIRA EVO（分别使用R1和o3模型）
    *   **消融实验**：
        *   去掉AIDE的Memory算子。
        *   使用AIDE的算子集，但替换搜索策略为MCTS或EVO（以验证算子瓶颈假说）。
        *   改变MCTS的探索常数 `c`。

#### **4. 资源与算力**

*   **环境**：由AIRA-dojo框架管理的隔离容器环境。
*   **硬件配置**：
    *   每项任务对应一个独立的代理，分配1 个专用的 **NVIDIA H200** GPU。
    *   24 个逻辑CPU核心。
    *   100 GB 内存。
    *   1 TB 额外临时存储。
*   **软件与模型**：
    *   主力模型：**DeepSeek-R1** 和 **OpenAI o3**。
    *   代码解析模型：**GPT-4o**（用于提取代码执行结果）。
*   **时间限制**：每个任务有 **24小时** 的墙面时间限制，每次代码执行最长 **4小时**。

#### **5. 实验数量与充分性**

*   **实验数量**：非常充分。
    *   在MLE-bench lite上，大部分实验使用了 **20个随机种子** 以降低方差。对于OpenAI o3模型的实验，使用了 **10个种子**。
    *   在完整MLE-bench上使用AIRA Greedy o3进行了 **20个种子** 的实验。
    *   进行了细致的消融实验来验证记忆算子、搜索策略（MCTS vs. Greedy vs. Evo）和算子集（O_aide vs. O_aira）的独立贡献。
    *   对AIDE进行了超21小时的性能剖面分析。
    *   **充分性与公平性**：大多数实验均达到20种子，这在AI代理领域是非常高的标准，能极大提升结果统计显著性。通过与MLE-bench官方相同的评估协议，保证了实验的客观与公平。论文还专门讨论了种子数量对排名稳定性的影响（附录J），进一步证明了其选择的合理性。

#### **6. 论文的主要结论与发现**

1.  **算子是性能瓶颈**：当使用AIDE的原始算子集（O_aide）时，无论采用多么先进的搜索策略（MCTS、进化算法），性能都没有显著提升。图3清晰地展示了这一点。
2.  **改进的算子集是性能提升关键**：通过将算子集从O_aide替换为论文设计的O_aira，即使使用相同贪心搜索策略，性能也获得了显著提升（+14% 相对提升），证明了算子的主导作用。
3.  **搜索策略与算子集协同作用**：只有在配备了强大的算子集（O_aira）后，更先进的搜索策略（如AIRA MCTS）才能发挥优势。AIRA MCTS和AIRA Greedy在不同模型和指标上各有优劣，但总体上都超越了之前的SOTA。
4.  **达到新的SOTA**：最佳代理 **AIRA MCTS** 在MLE-bench lite上将奖牌成功率从之前的39.6% 提升至 **47.7%**，取得了新的最佳成绩。
5.  **泛化差距是关键限制**：搜索过程中使用的验证分数与最终的测试分数之间存在“泛化差距”，导致系统性过拟合。使用测试分数（而非验证分数）来选择最终节点，可以使奖牌率提高9-13个百分点。这揭示了鲁棒的最终节点选择策略是极具潜力的未来研究方向。

#### **7. 优点**

*   **形式化框架**：将AI研究代理的形式化定义为一个清晰的搜索五元组，为系统性地研究和比较不同代理设计提供了理论基础。
*   **系统性的解耦分析**：关键的创新之处在于能够将算子、搜索策略和评估方法解耦并进行独立控制实验，从而准确定位了性能瓶颈。
*   **有力的实验验证**：通过大量的消融实验和统计检验，有力地支撑了其核心论点（算子是瓶颈）。使用大量随机种子保证了结论的可靠性。
*   **开源基础设施**：开发并开源了AIRA-dojo框架，为社区提供了一个可靠、可扩展、可定制的研究平台，这本身是很有价值的贡献。
*   **对新问题的洞察**：揭示并量化了“泛化差距”对AI研究代理性能的重大影响，并提出了通过多次提交来弥补这一差距的可行方案。

#### **8. 不足与局限**

*   **计算资源昂贵**：论文的结论建立在大量昂贵计算资源之上（H200 GPU），且实验周期长（24小时/任务），这限制了论文方法的可复现性和可负担性，特别是对于算力有限的实验室。
*   **有限的任务范围**：实验主要集中在Kaggle竞赛这类结构化问题上。论文的结论是否能够推广到更广泛、更复杂的科学研究场景（如论文所述的自然科学领域）尚不明确。
*   **过拟合风险未根本解决**：虽然论文揭示了泛化差距问题，但仅仅是分析了其影响，并未提出一个能从根本上解决此问题的方法。论文提出的“多次提交”方案在现实场景中可能不具普适性，因为它依赖于对测试集的多次访问。
*   **数据污染风险**：论文承认DeepSeek R1等模型可能在训练数据中见过部分Kaggle任务，这可能有助于其性能。尽管作者在附录E中讨论了这个问题，但这是一个固有的、无法完全控制的风险。
*   **模型选择依赖**：论文结论高度依赖于所使用的LLM模型（DeepSeek R1, GPT-4o, o3）。如果更换模型，结论中的相对排名和性能优势可能会改变。

（完）
