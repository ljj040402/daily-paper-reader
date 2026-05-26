---
title: "Wasserstein Gradient Boosting: A Framework for Distribution-Valued Supervised Learning"
title_zh: Wasserstein梯度提升：分布值监督学习框架
authors: Takuo Matsubara
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=cuO0DenqMl"
tags: ["query:ai"]
score: 7.0
evidence: 将梯度提升扩展至分布值监督学习
tldr: 本文提出Wasserstein梯度提升，扩展传统梯度提升至分布值监督学习。通过使用Wasserstein梯度作为伪残差，逐轮拟合新弱学习器，解决了输出为概率分布的回归与分类问题，为分布预测提供了新框架。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-cuo0denqml/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1439, \"height\": 355, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-cuo0denqml/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1429, \"height\": 370, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-cuo0denqml/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1339, \"height\": 327, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-cuo0denqml/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1299, \"height\": 375, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-cuo0denqml/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1207, \"height\": 801, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-cuo0denqml/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1441, \"height\": 1434, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-cuo0denqml/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1296, \"height\": 311, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-cuo0denqml/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1448, \"height\": 776, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-cuo0denqml/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1444, \"height\": 251, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-cuo0denqml/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1169, \"height\": 267, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-cuo0denqml/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1273, \"height\": 181, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-cuo0denqml/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1442, \"height\": 499, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-cuo0denqml/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1389, \"height\": 180, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-cuo0denqml/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1441, \"height\": 179, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-cuo0denqml/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 705, \"height\": 178, \"label\": \"Table\"}]"
motivation: 现有梯度提升无法处理输出为概率分布的学习任务。
method: 基于Wasserstein梯度的伪残差拟合弱学习器。
result: 在分布值回归和分类任务上展示了有效性。
conclusion: 为分布预测提供了一种新的集成学习方法。
---

## Abstract
Gradient boosting is a sequential ensemble method that fits a new weaker learner to pseudo residuals at each iteration. We propose Wasserstein gradient boosting, a novel extension of gradient boosting, which fits a new weak learner to alternative pseudo residuals that are Wasserstein gradients of loss functionals of probability distributions assigned at each input. It solves distribution-valued supervised learning, where the output values of the training dataset are probability distributions. In classification and regression, a model typically returns, for each input, a point estimate of a parameter of a noise distribution specified for a response variable, such as the class probability parameter of a categorical distribution specified for a response label. A main application of Wasserstein gradient boosting in this paper is tree-based evidential learning, which returns a distributional estimate of the response parameter for each input. We empirically demonstrate the competitive performance of the probabilistic prediction by Wasserstein gradient boosting in comparison with existing uncertainty quantification methods.

---

## 论文详细总结（自动生成）

好的，遵照您的要求，以下是对论文《Wasserstein Gradient Boosting: A Framework for Distribution-Valued Supervised Learning》的结构化、详细中文总结。

---

### 1. 论文的核心问题与整体含义（研究动机和背景）

*   **核心问题**：传统梯度提升（Gradient Boosting）只能处理输出为标量或向量的监督学习任务。然而，许多现实应用（如不确定性量化、证据学习）要求模型为每个输入返回一个**概率分布**（例如，响应参数的分布估计）。现有方法（如贝叶斯神经网络）计算复杂或局限于特定形式（如共轭后验）。论文旨在解决**分布值监督学习**（Distribution-Valued Supervised Learning）问题，即训练集输出为概率分布，模型需学会为任意输入预测一个非参数化的分布。
*   **研究动机与背景**：
    *   梯度提升在表格数据上表现优异，但其不确定性量化能力有限。
    *   证据学习（Evidential Learning）通过预测响应参数的个体后验分布来量化不确定性，但现有方法依赖神经网络且要求后验具有闭式解，限制了其应用范围。
    *   作者希望将梯度提升框架与Wasserstein梯度流（Wasserstein Gradient Flow）结合，以粒子形式输出分布，从而规避闭式解的要求，并适用于树模型。

### 2. 论文提出的方法论：核心思想、关键技术细节

*   **核心思想**：提出**Wasserstein梯度提升（WGBoost）**。在传统梯度提升中，每个弱学习器拟合损失函数的负梯度（伪残差）。WGBoost将其推广：对于一个输出分布为 $\mu_i$ 的训练样本，弱学习器拟合的是**损失泛函在Wasserstein空间中的梯度**（Wasserstein梯度），该梯度引导当前集成模型输出的经验分布 $\hat{\mu}_{m,i}$ 向真实分布 $\mu_i$ 移动。
*   **关键技术细节**：
    1.  **模型输出**：WGBoost维护 $N$ 个集成模型 $\{F^1_m, ..., F^N_m\}$，对应 $N$ 个粒子。对于输入 $x$，输出为 $N$ 个点 $\{\theta^1(x), ..., \theta^N(x)\}$，其经验分布近似于目标输出分布。
    2.  **迭代更新**：在第 $m$ 步，对于每个训练样本 $(x_i, \mu_i)$，计算当前粒子集 $\{F^n_m(x_i)\}$ 的经验分布 $\hat{\mu}_{m,i}$。然后，基于损失泛函 $\mathcal{D}(\cdot | \mu_i)$（论文选用KL散度）的估计Wasserstein梯度 $G_i(\hat{\mu}_{m,i})$，计算每个粒子的目标值。
        $$ g^n_i = -[G_i(\hat{\mu}_{m,i})](F^n_m(x_i)) $$
        然后训练 $N$ 个新的弱学习器 $\{f^{n}_{m+1}\}$ 来分别拟合这些目标值。
    3.  **Wasserstein梯度估计**：由于KL散度的Wasserstein梯度在经验分布上无定义，作者采用**核平滑**技巧（源于Stein变分梯度下降SVGD）。平滑后的梯度 $G^*_i(\mu)$ 定义为：
        $$ [G^*_i(\mu)](\theta) := -\mathbb{E}_{\theta_* \sim \mu}\left[\nabla \log \mu_i(\theta_*) k(\theta_*, \theta) + \nabla k(\theta_*, \theta)\right] $$
        其中 $k$ 是高斯核函数。该式对任何分布（包括经验分布）都有良好定义。
    4.  **二阶WGBoost（WEvidential）**：为对标现代梯度提升库（如XGBoost）的对角牛顿法，作者进一步推导了**对角近似Wasserstein Hessian** $H^*_i(\mu)$，并将其用于计算对角牛顿方向作为伪残差，加速收敛。
        $$ [H^*_i(\mu)](\theta) := \mathbb{E}_{\theta_* \sim \mu}\left[-\nabla^2_d \log \mu_i(\theta_*) k(\theta, \theta_*)^2 + \nabla k(\theta, \theta_*) \odot \nabla k(\theta, \theta_*)\right] $$
        最终的伪残差为 $[G^*_i(\mu)](\cdot) \oslash [H^*_i(\mu)](\cdot)$。
    5.  **算法流程**（Algorithm 2）：
        *   **输入**：训练集 $\{x_i, y_i\}$，响应分布 $p(y|\theta)$，个体后验 $p(\theta|y_i)$，粒子数 $N$，弱学习器 $f$。
        *   **初始化**：$N$ 个常数集成模型 $\{F^n_0\}$。
        *   **循环** $m = 0$ to $M-1$：
            *   对每个样本 $i$：获取当前粒子 $\{\theta^n_i\}$，计算每个粒子的平滑梯度 $g^n_i$ 和Hessian $h^n_i$（使用公式(7)(8)）。
            *   对每个粒子 $n$：用数据集 $\{x_i, g^n_i / h^n_i\}$ 训练新的弱学习器 $f^{n}_{m+1}$，并更新集成 $F^n_{m+1}(\cdot) = F^n_m(\cdot) + \nu f^{n}_{m+1}(\cdot)$，$\nu$ 为学习率。
        *   **输出**：最终的 $N$ 个集成模型。对于新输入 $x$，其粒子为 $\{F^n_M(x)\}$，预测分布为 $p(y|x) = \frac{1}{N}\sum_n p(y|\theta = F^n_M(x))$。

### 3. 实验设计：数据集、场景、对比方法

*   **场景一：实例性条件密度估计**
    *   **数据集**：两个一维回归数据集 (`bone mineral density`, `old faithful geyser`)。
    *   **目的**：可视化WGBoost的输出粒子及其条件密度估计效果。
*   **场景二：概率回归基准测试**
    *   **数据集**：9个UCI回归数据集（`boston`, `concrete`, `energy`, `kin8nm`, `naval`, `power`, `protein`, `wine`, `yacht`, `year msd`）。
    *   **对比方法**：Monte Carlo Dropout (MCDropout), Deep Ensemble (DEnsemble), Concrete Dropout (CDropout), Natural Gradient Boosting (NGBoost), Deep Evidential Regression (DEvidential)。
    *   **评价指标**：负对数似然 (NLL) 和 均方根误差 (RMSE)。
*   **场景三：分类与异常检测（OOD Detection）**
    *   **数据集**：两个多分类UCI数据集 (`segment`: 7类, `sensorless`: 11类)。OOD样本由保留的类别构成。
    *   **对比方法**：MCDropout, DEnsemble, Distributional Distillation (DDistillation), Posterior Network (PNetwork)。
    *   **评价指标**：分类准确率 (Accuracy) 和 OOD检测的PR-AUC (Precision-Recall Area Under Curve)。
*   **额外实验**：附录中还有与贝叶斯神经网络（BNN）、高斯过程（GP）的比较，以及不同Wasserstein梯度估计的消融研究（Smoothed Gradient, Diagonal Newton, Full Newton, Langevin Gradient Boosting）。

### 4. 资源与算力

*   **明确说明**：论文仅在附录中提到所有实验使用 **x86-64 CPUs**，部分实验并行使用 **最多10个CPU**，其余使用1个CPU。**未提及GPU**，也未提供训练时长或具体硬件型号。
*   **主观判断**：这说明WGBoost的原始实现是CPU友好的，未进行大规模GPU加速。由于树模型和粒子更新（N=10）的计算规模相对较小，CPU资源够用。

### 5. 实验数量与充分性

*   **实验数量**：
    *   回归：在9个数据集上进行了20次随机分割（大数据集次数少）。
    *   分类：在2个数据集上进行了5次重复。
    *   附录：额外与BNN/GP对比3-6个数据集，以及合成数据消融实验。
*   **充分性与客观性**：
    *   **优点**：采用了领域内广泛使用的基准测试协议（如Hernandez-Lobato & Adams的20次划分），对比了多种主流不确定性量化方法，结果有标准差，较为规范和客观。
    *   **不足**：
        1.  **分类任务对比不全**：仅对比了2个数据集且未与NGBoost等树基方法对比。
        2.  **超参数敏感性探索不足**：核函数带宽 $h$ 和粒子数 $N=10$ 的选择缺乏系统性论证（虽然附录有 $h$ 的敏感性实验）。
        3.  **消融实验**：虽然在附录对比了不同梯度估计方法，但对树模型深度、学习率等核心超参数的消融研究不充分。
        4.  **样本量**：分类数据集规模较小，缺乏大规模高维分类数据的验证。

### 6. 论文的主要结论与发现

1.  **WGBoost框架有效**：成功将梯度提升扩展至分布值输出，提供了一种非参数的分布预测方法。
2.  **WEvidential性能优异**：基于KL散度和二阶Wasserstein梯度（WEvidential）的默认算法在概率回归基准上取得了**与顶尖方法竞争甚至最佳**的结果（表1，在多数数据集上NLL和RMSE接近或优于NGBoost、Deep Ensemble等）。
3.  **出色的OOD检测能力**：在分类实验中，WEvidential的OOD检测性能（PR-AUC）远超MCDropout、DEnsemble等，甚至高于专为OOD设计的Posterior Network（在segment数据集上），展现了其不确定性量化的潜力。
4.  **二阶方法有效性**：对角线近似Wasserstein牛顿方向在合成数据上展现出比一阶平滑梯度和Langevin梯度更快的收敛速度和更好的最终误差。

### 7. 优点：方法或实验设计上的亮点

*   **方法论创新**：创造性地将Wasserstein梯度流融入梯度提升，利用粒子更新解决分布值监督学习，是该领域的首个框架。它规避了对后验闭式解的依赖，拓宽了证据学习的适用范围。
*   **实用性强**：专门实现了二阶WGBoost（WEvidential），使其与现代梯度提升库（如XGBoost）的风格一致，有望获得可扩展性。
*   **实验设计完整**：涵盖了回归、分类、可视化、OOD检测、消融研究等多个方面，对比方法全面（包括SOTA的深度集成和天然梯度提升），且提供了代码。
*   **清晰的图示**：论文图1和图3直观展示了WGBoost如何用粒子逼近分布，图2清晰对比了WGBoost与贝叶斯学习，非常有助于理解。

### 8. 不足与局限

*   **应用领域的局限性**：作者坦诚“当数据不是表格数据时，WGBoost可能表现不佳”，这是梯度提升类方法的通病，限制了其在图像、文本等领域的应用。
*   **计算复杂度**：虽然二阶方向计算复杂度为 $O(N \times d)$，但全牛顿法复杂度 $O(N^3 \times d^3)$ 过高。默认算法需要对每个样本的每个粒子计算核函数，当数据量大、粒子数和深度增加时，计算量会显著增长。
*   **理论分析缺失**：论文未对WGBoost的收敛性、泛化界等进行严格的数学证明，仅给出了启发式直觉和实验验证。
*   **超参数敏感**：核带宽 $h$ 对性能影响显著（附录D.1），但论文仅推荐 $0.01 \le h \le 1$ 并固定为0.1，缺乏针对不同数据集的自动选择机制。
*   **实验设计的不完全公平性**：在分类OOD检测中，OOD定义（保留最后几类）相对简单。实际场景的OOD复杂得多（如语义偏移、分布外概念）。此外，未与Tree-based OOD方法（如孤立森林）进行对比。
*   **与贝叶斯方法对比的局限**：在附录中与BNNs对比时，数据集较少，且WGBoost在`naval`和`yacht`数据集上表现不如部分BNN（如SWAG），说明并非在所有场景下都占优。

（完）
