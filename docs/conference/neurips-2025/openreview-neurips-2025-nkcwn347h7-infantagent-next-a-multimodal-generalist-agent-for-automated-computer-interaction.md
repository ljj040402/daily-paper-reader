---
title: "InfantAgent-Next: A Multimodal Generalist Agent for Automated Computer Interaction"
title_zh: InfantAgent-Next：用于自动化计算机交互的多模态通用智能体
authors: "Bin Lei, Weitai Kang, Zijian Zhang, Winson Chen, Xi Xie, Shan Zuo, Mimi Xie, Ali Payani, Mingyi Hong, Yan Yan, Caiwen Ding"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=NKcwN347H7"
tags: ["query:ai"]
score: 6.0
evidence: 多模态通用智能体用于计算机交互，涵盖人工智能研究
tldr: 现有方法要么围绕单一大型模型构建复杂工作流，要么仅提供工作流模块化，缺乏灵活性。本文提出InfantAgent-Next，一个高度模块化的多模态通用智能体，融合工具型与纯视觉智能体，协同解决解耦任务。在OSWorld、GAIA和SWE-Bench等基准上取得领先性能，展示了通用计算机交互的潜力。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-nkcwn347h7/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1373, \"height\": 643, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nkcwn347h7/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1352, \"height\": 1176, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nkcwn347h7/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1452, \"height\": 364, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nkcwn347h7/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 915, \"height\": 637, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nkcwn347h7/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1362, \"height\": 1309, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-nkcwn347h7/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1440, \"height\": 435, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-nkcwn347h7/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1450, \"height\": 614, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-nkcwn347h7/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1454, \"height\": 860, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-nkcwn347h7/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1459, \"height\": 826, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-nkcwn347h7/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1438, \"height\": 389, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-nkcwn347h7/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1445, \"height\": 245, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-nkcwn347h7/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1452, \"height\": 114, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-nkcwn347h7/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1466, \"height\": 176, \"label\": \"Table\"}]"
motivation: 现有计算机交互智能体在灵活性和模块化方面存在不足，难以处理多样化任务。
method: 构建高度模块化的多模态智能体架构，集成工具型与纯视觉智能体协同解决解耦任务。
result: 在多个基准上取得领先性能，展现了通用性。
conclusion: 模块化多模态架构能有效提升智能体的通用性和任务解决能力。
---

## Abstract
This paper introduces \textsc{InfantAgent-Next}, a generalist agent capable of interacting with computers in a multimodal manner, encompassing text, images, audio, and video.
Unlike existing approaches that either build intricate workflows around a single large model or only provide workflow modularity, our agent integrates tool-based and pure vision agents within a highly modular architecture, enabling different models to collaboratively solve decoupled tasks in a step-by-step manner. 
Our generality is demonstrated by our ability to evaluate not only pure vision-based real-world benchmarks (i.e., OSWorld), but also more general or tool-intensive benchmarks (e.g., GAIA and SWE-Bench).
Specifically,
we
achieve a $\mathbf{7.27\\%}$ accuracy gain over Claude-Computer-Use on OSWorld.  
Codes and evaluation scripts are included in the supplementary material and will be released as open-source.

---

## 论文详细总结（自动生成）

# 论文《InfantAgent-Next: A Multimodal Generalist Agent for Automated Computer Interaction》详细总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：现有自动化AI智能体主要分为两类——**工具型智能体**（如OpenHands、AutoGPT）和**纯视觉智能体**（如UI-TARS、Aguvis）。工具型智能体依赖预定义工具集，需要针对每个桌面场景手动集成，缺乏通用性；纯视觉智能体通过vLLM直接控制GUI，适用性更广，但在文档编辑、代码操作等可轻易通过工具调用的任务上精度较低。此外，即使先进模型（如Claude-3.7-Sonnet）能进行精细规划，执行阶段仍常见GUI点击坐标错误或文件编辑行号错误。因此，需要一种融合两者优势的混合范式。
- **核心问题**：如何设计一个能同时处理文本、图像、音频、视频等多种模态，兼具高任务精度和广泛通用性的计算机交互智能体。
- **整体含义**：提出**InfantAgent-Next**，通过高度模块化架构，将不同子任务路由到最合适的专家模型（推理、视觉定位、音频分析等），并统一对话上下文，实现真正的多模态交互。

## 2. 方法论：核心思想、关键技术细节

### 核心思想
- **模块化工作流与多模型协作**：将智能体的工作流程、工具选择、工具执行进行细致模块化，每个子任务由最合适的模型单独完成（如推理模型负责规划、视觉定位模型负责GUI元素定位、音频分析模型处理声音）。
- **统一对话上下文**：各模型输出通过特殊标签（`<thought>`、`<task>`、`<toolkit>`、`<execute_bash>`等）存储并重建为对话历史，保证信息连贯。

### 关键技术细节

#### 架构流程
1. **参数配置**：用户可为规划、工具选择、执行三个阶段分别指定不同工作流模型，以及处理图像、音频、视频的专用工具模型。
2. **智能体初始化**：为每个模型分配角色和专用提示模板，初始化内存缓存，存储用户请求。
3. **迭代工作流**：
   - **规划**（Planner模型）：分析请求和当前状态，生成子任务（`<task>`）。
   - **工具选择**（Tool Selection模型）：从7个预定义工具包（文件读写、文件搜索、文件编辑、网页浏览、计算机操作、代码执行、高级工具）中动态选取最合适的一个或多个。
   - **执行**（Executor模型）：调用所选工具，从环境获取反馈（截图、终端输出等）。
   - **检查**：若任务完成则结束，否则进入下一轮迭代。

#### 内存管理
- 每次模型输出用特殊标签存储，重建对话时按阶段抽取相关记忆（规划阶段保留所有记忆但移除工具选择部分；工具选择阶段只保留最近一次任务记忆；执行阶段保留除工具选择外的所有记忆并保留bash/python执行标签）。

#### 鼠标点击（Iterative Region Cropping）
- **算法1**：先判断最近动作是否为`mouse_click`，若是则获取元素描述和初始区域（全屏截图）。循环n次：每次将当前区域和描述输入视觉定位模型（如UI-TARS-1.5-7B）得到候选坐标，然后以该坐标为中心裁剪更小区域。最后再用视觉定位模型预测最终点击坐标并执行点击。通过逐步缩小搜索区域提高定位精度。

#### 文件编辑（File Editing Logic）
- **算法2**：先判断最近动作是否为`file_edit`，若是则提取编辑请求。调用`GenerateEditPlan`得到起止行号和行内容。若实际行内容匹配则直接应用编辑；否则进入回退：模糊匹配起止行内容，找到最相似行范围，更新请求并重试（最多MAX_ITER次）。修复了行号偏移、内容不匹配等常见错误。

#### 工具集
- 7个工具包：File Reading、File Searching、File Editing、Web Browsing、Computer Use、Code Execution、Advanced Tools。每个工具包含具体函数（如`open_file`、`mouse_left_click`、`google_search`等），并有详细文档和示例。

## 3. 实验设计

### 使用的数据集/场景与Benchmark
| 基准 | 任务类型 | 规模 | 关键指标 |
|------|----------|------|----------|
| **OSWorld** | 纯视觉桌面交互（GUI操作） | 369个开放任务 | 成功率（@50步） |
| **SWE-Bench-Lite** | 代码逻辑推理（GitHub bug修复） | 300个问题 | 准确率（Pass@1） |
| **SWE-Bench-Verified** | 代码逻辑推理（子集50例） | 500例中均匀采样50例 | 准确率 |
| **GAIA** | 通用AI辅助（多模态+工具使用） | 验证集（三级难度） | 平均准确率 |
| **ScreenSpot-Pro** | 视觉定位（点击坐标） | 1581张专业截图 | 点击准确率 |
| **SWE-Bench-Verified文件编辑子集** | 文件编辑能力 | 10%采样（按仓库分类） | 修复成功率（RSR）、整体修复率（ORR） |

### 对比方法
- **OSWorld**：对比UI-TARS、OpenAI CUA、Claude Computer Use、Agent S2、AGUVIS、SeeClick等11种方法。
- **SWE-Bench**：对比SWE-agent、OpenHands、AutoCodeRover、Amazon Q Developer Agent等开源/闭源方法。
- **GAIA**：对比Langfun Agent、Trase Agent、OWL、TapeAgents、Open Deep Research等20余种方法（数据来自官方排行榜）。
- **ScreenSpot-Pro消融**：仅自对比，改变裁剪宽度、高度、宽高比、迭代次数。
- **文件编辑评估**：统计不同类型错误（行号偏移、内容不匹配、语法错误等）的修复情况。

### 实验设置
- **OSWorld**：Claude-3.7-Sonnet规划 + UI-TARS-1.5-7B视觉定位，禁用非视觉工具包，max_steps=50。
- **SWE-Bench-Lite**：GPT-4o规划/选择/执行 + DeepSeek-V3-0324文件编辑。
- **SWE-Bench-Verified 50例**：Claude-3.7-Sonnet每步 + DeepSeek-V3-0324文件编辑。
- **GAIA**：Claude-3.7-Sonnet推理+执行，DeepSeek-V3-0324工具选择，gpt-4o-audio-preview音频，UI-TARS-1.5-7B视觉。
- **ScreenSpot-Pro消融**：2×A100 80G GPU，UI-TARS-1.5-7B模型，固定迭代次数n=2或可变。

## 4. 资源与算力

- **明确说明**：在ScreenSpot-Pro消融实验中，使用**2×A100 80G GPU**。其他实验（OSWorld、SWE-Bench、GAIA）未在论文中明确提及使用的GPU型号或数量。实验主要依赖API调用（Claude-3.7-Sonnet、GPT-4o等），本地推理仅涉及UI-TARS-1.5-7B和DeepSeek-V3-0324，但未给出具体算力开销。

## 5. 实验数量与充分性

- **实验组数**：
  - 主要性能：4个基准测试（OSWorld、SWE-Bench-Lite、SWE-Bench-Verified 50例、GAIA），每个均与多个基线对比。
  - 消融实验：ScreenSpot-Pro上从**宽度、高度、宽高比、迭代次数**四个维度系统探究Iterative Region Cropping。
  - 文件编辑评估：在SWE-Bench-Verified子集（约50例）上统计7类错误（含修复成功/失败的分布）。
- **充分性评估**：
  - **全面**：覆盖了视觉、逻辑推理、通用任务、精准定位、文件编辑等多个维度，且对比了开源和闭源SOTA方法。
  - **公平**：SWE-Bench-Lite实验中统一使用GPT-4o确保可比性；OSWorld对比在相同步数下比较；GAIA对比直接引用官方排行榜数据。
  - **消融设计合理**：对核心算法（Iterative Region Cropping）的参数进行系统搜索，找到了最优配置。
  - **统计意义**：部分实验（如文件编辑）包含误差/分布分析，但主要性能指标未给出误差棒（除ScreenSpot-Pro消融图外）。整体可复现性较好（开源代码）。

## 6. 主要结论与发现

1. **OSWorld**：在50步限制下达到35.3%准确率，比Claude Computer Use（Claude-3.7-Sonnet @50步）高7.27个百分点，优于所有开源框架（Agent S2 34.5%）。
2. **SWE-Bench-Verified（50例）**：以66%准确率领先许多闭源代理（如Amazon Q Developer Agent 54%），仅次于SWE-agent+Claude 3.7 Sonnet w/ Review Heavy（72%）和CodeStory Midwit Agent（70%）。
3. **SWE-Bench-Lite（GPT-4o条件下）**：31.67%准确率，与Agentless-1.5（32%）相当，高于OpenHands+CodeAct（22%）。
4. **GAIA**：平均56.97%，在开源方法中排名第二，仅在OWL（58.18%）之后；在Level 2任务上达到62.79%，为开源最佳。
5. **Iterative Region Cropping消融**：通过3次迭代、裁剪区域宽高比0.3和0.25可获得最佳精度（约51.36%），且2次迭代即可获得良好折中（约49.53%）。
6. **文件编辑**：修复成功率（RSR）84.3%，整体修复率（ORR）51.4%，成功修复了大部分行号偏移、内容不匹配和语法错误。

## 7. 优点

- **高度模块化设计**：将规划、工具选择、执行分离，支持不同模型分工协作，避免单一模型瓶颈。
- **多模态与多模型支持**：文本、图像、音频、视频全模态覆盖，可配置不同专家模型（如Claude for推理、UI-TARS for视觉定位、gpt-4o-audio for音频）。
- **创新的鼠标点击算法**：Iterative Region Cropping通过逐步缩小搜索区域，显著提升GUI点击定位精度（尤其在专业高分辨场景下）。
- **稳健的文件编辑机制**：结合边界行内容校验和模糊回退匹配，有效解决行号偏移和内容不匹配问题，修复成功率超84%。
- **动态工具选择**：将工具分为7个工具包，每次只选择相关子集，降低推理开销和选择难度。
- **完整开源与复现支持**：代码、模型、评估脚本全部开源，附带详细README。
- **实验设计全面**：覆盖多个主流基准，消融研究系统，对比方法多样，结论可信。

## 8. 不足与局限

- **实验覆盖偏差**：
  - 部分基准仅使用子集（如SWE-Bench-Verified只测试50例），可能未充分反映完整数据集上的性能波动。
  - GAIA实验截止于2025年4月17日，后续其他方法可能有更新，缺乏持续追踪。
- **算力信息不透明**：除ScreenSpot-Pro外，其他实验未说明GPU型号、数量或推理时间，不利于复现和成本评估。
- **性能上限受限于底层模型**：依赖Claude-3.7-Sonnet、GPT-4o、UI-TARS-1.5-7B等外部模型，若这些模型更新或关闭API，智能体性能可能波动。
- **局限性与未来工作**（论文附录F）：
  - 当前仅限于推理阶段，需要大量手动提示工程（prompt engineering）。未来应训练模型自动调用工具，减少人工干预。
  - 未探讨跨领域泛化能力（如不同操作系统、非桌面环境）。
  - 未分析用户隐私与安全风险（智能体在真实Web上的操作可能暴露敏感信息）。
- **消融深度有限**：仅对鼠标点击算法做了系统消融，对其他组件（如记忆重建策略、动态工具选择效果）未进行量化分析。
- **公平性讨论缺失**：未分析在长尾任务或非英文界面上的表现，可能存在偏见。

（完）
