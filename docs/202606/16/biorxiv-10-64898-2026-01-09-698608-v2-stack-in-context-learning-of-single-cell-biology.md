---
title: "Stack: In-Context Learning of Single-Cell Biology"
title_zh: STACK：单细胞生物学的上下文学习
authors: "Dong, M., Adduri, A., Gautam, D., Wu, L., Kernick, C., Coons, M. M., Chih, Y.-C., Carpenter, C., Shah, R., Ricci-Tam, C., Tung, P.-Y., Li, N., Dobin, A., Kluger, Y., Burke, D. P., Roth, T., Roohani, Y. H."
date: 2026-06-08
pdf: "https://www.biorxiv.org/content/10.64898/2026.01.09.698608v2.full.pdf"
tags: ["query:prompt-learn"]
score: 9.0
evidence: 利用细胞演示进行上下文学习
tldr: 当前单细胞基础模型受限于预设监督任务，难以用于通用生物发现。Stack在1.49亿人类单细胞上训练，通过表格注意力机制实现上下文学习，使细胞在推理时作为指导示例。零样本性能显著超越基线，据此构建了首个全生物体人类扰动图谱Perturb Sapiens（涵盖28组织、40细胞类型和892种扰动），并利用40供体数据验证了供体特异性效应。该框架为单细胞生物学解锁了通用上下文学习能力。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有单细胞模型受限于固定监督任务，难以泛化至任意生物条件发现。
method: 基于1.49亿单细胞训练，利用表格注意力实现上下文学习，细胞作为上下文示例。
result: 零样本性能大幅提升；构建首个全生物体人类扰动图谱（28组织、40类型、892扰动）；验证供体特异性效应。
conclusion: 提出细胞作为推理指导的新范式，为单细胞生物学解锁通用上下文学习能力，推动生物发现。
---

## 摘要
基于单细胞转录组数据训练的基础模型有望识别和预测跨物种、疾病及其他生物学条件下的细胞表型多样性。然而，当前模型局限于其监督训练条件和任务，限制了其在生物学发现中的应用。在此，我们提出STACK，一个在1.49亿个统一预处理的人类单细胞上训练的基础模型，它利用表格注意力机制，根据上下文中的细胞为每个细胞生成表示。与零样本、微调或从头在目标数据集上训练的基线相比，STACK在零样本设置下的下游任务中表现出显著改进。STACK能够从未标注细胞中学习上下文，这些细胞代表任意条件，如化学扰动或不同供体，并预测这些条件对目标细胞群体的影响，无需数据特异性微调。我们应用STACK生成了Perturb Sapiens，这是首个针对扰动细胞的人类全生物体图谱，涵盖28种组织、40种细胞类型以及892种药物、细胞因子和遗传扰动。我们利用体外刺激谱验证了Perturb Sapiens的子集。STACK独特地支持对供体特异性扰动效应进行优先级排序，这一能力在我们新收集的DiseasePert-3M数据中得到了验证，该数据包含来自14种疾病的40名供体的T细胞，并用11种细胞因子刺激。总体而言，STACK提出了一个新的建模框架，其中细胞本身在推理时充当指导示例，为单细胞生物学解锁了通用的上下文学习能力。

## Abstract
Foundation models trained on single-cell transcriptomic data offer the promise of identifying and predicting the diversity of cellular phenotypes across species, diseases, and other biological conditions. However, the current models are limited to their supervised training conditions and tasks, which limits their utility for biological discovery. Here, we present SO_SCPLOWTACKC_SCPLOW, a foundation model trained on 149 million uniformly preprocessed human single cells that leverages tabular attention to generate representations for each cell informed by the cells in its context. SO_SCPLOWTACKC_SCPLOW offers substantial improvements for downstream tasks in the zero-shot setting compared to baselines, whether they are zero-shot, fine-tuned, or trained from scratch on the target dataset. SO_SCPLOWTACKC_SCPLOW can perform in-context learning from unlabeled cells representing arbitrary conditions, such as a chemical perturbation or a different donor, and predict the effect of those conditions on a target cell population without requiring data-specific fine-tuning. We apply SO_SCPLOWTACKC_SCPLOW to generate Perturb Sapiens, the first human whole-organism atlas of perturbed cells, spanning 28 tissues, 40 cell types, and 892 drug, cytokine, and genetic perturbations. We validated subsets of Perturb Sapiens using in vitro stimulation profiles. SO_SCPLOWTACKC_SCPLOW uniquely empowers prioritization of donor-specific perturbation effects, a capability we validated in our newly collected DiseasePert-3M data, comprising T cells from 40 donors across 14 diseases, stimulated with 11 cytokines. Overall, SO_SCPLOWTACKC_SCPLOW presents a new modeling framework where cells themselves act as guiding examples at inference time, unlocking general-purpose in-context learning capabilities for single-cell biology.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义
- **研究背景**：当前基于单细胞转录组数据的基础模型通常被限定在训练时预设的监督任务（如细胞类型标注、批次校正）上，难以灵活泛化到任意新生物学条件（如新药物扰动、供体差异），限制了其在开放生物发现中的实用性。
- **核心问题**：如何构建一个能够在推理时依据少量未标注“上下文细胞”示例，直接预测新条件对目标细胞群影响的通用单细胞模型，从而摆脱对特定任务微调的依赖。
- **整体含义**：STACK 提出了“细胞本身作为推理指导示例”的新范式，将上下文学习引入单细胞生物学，使模型像语言模型利用上下文示例一样，利用细胞来预测任意生物学条件的效果，推动大规模、灵活的扰动图谱构建和供体特异性效应发现。

### 2. 论文提出的方法论
- **核心思想**：在预训练阶段让模型学会从上下文细胞集合中提炼条件信号（如某种扰动或供体背景），并在查询细胞上预测该条件下基因表达的变化，实现零样本上下文学习。
- **关键技术细节**：
  - **表格注意力机制**：将一组上下文细胞与查询细胞共同输入模型，通过特殊的注意力结构，使查询细胞的表示融合上下文细胞所携带的条件信息。
  - **统一预处理**：对 **1.49 亿个人类单细胞** 进行标准化预处理，消除批次和技术差异，保证大规模训练的稳定性。
  - **上下文学习范式**：推理时提供若干属于同一条件（如受药物 X 处理）但未标注的细胞，模型即可为任意目标细胞生成该条件下的表达预测，无需针对该条件进行任何参数更新。
- **公式或算法流程说明**：虽然摘要未呈现具体公式，但整体流程可概括为：
  1. 将上下文细胞集 \(C = \{c_1,...,c_k\}\) 与查询细胞 \(q\) 的表征进行注意力交互；
  2. 通过多层表格注意力编码，上下文条件信号被隐式提取并融合到 \(q\) 的表示 \(h_q\) 中；
  3. 基于 \(h_q\) 解码出条件特异表达值或扰动效应。

### 3. 实验设计
- **数据集与场景**：
  - **预训练数据**：1.49 亿统一预处理的人类单细胞（涵盖多种组织、条件和平台）。
  - **下游评估**：零样本设置下的多项下游任务（文中未详列，但明确包含扰动效应预测、供体特异性效应预测）。
  - **大规模应用**：构建 **Perturb Sapiens** 图谱（28 种组织、40 种细胞类型、892 种药物/细胞因子/遗传扰动），并使用体外刺激谱进行子集验证。
  - **供体特异性验证**：新收集的 **DiseasePert-3M** 数据集（40 名供体，覆盖 14 种疾病，11 种细胞因子刺激 T 细胞）。
- **Benchmark 与对比方法**：
  - 与三种基线比较：① 零样本其它模型，② 在目标任务数据集上微调的模型，③ 在目标任务数据集上从头训练的模型。
  - STACK 在零样本设定下即显著超越以上所有基线。

### 4. 资源与算力
- 文中**未明确说明**训练所使用的 GPU 型号、数量、训练时长等具体算力信息。仅提及模型在 1.49 亿单细胞规模上训练，推断所需算力极高，但缺少可复现的硬件指标。

### 5. 实验数量与充分性
- **实验组数**：从摘要推断，至少包含：
  - 多组下游任务零样本对比实验（与零样本、微调、从头训练基线比较）；
  - 全生物体 Perturb Sapiens 图谱的生成与体外验证实验；
  - 供体特异性扰动优先级排序的独立验证（DiseasePert-3M）。
- **充分性与公平性**：
  - 对比基线多样，涵盖无训练、微调、重训三种策略，较为公平。
  - 通过体外实验验证了图谱子集，增强了实效性证据。
  - 然而，摘要未提供消融实验细节（如上下文细胞数量的影响、不同注意力机制变体比较），实验深度在摘要层面无法完全评判。

### 6. 论文的主要结论与发现
- STACK 成功实现了单细胞数据上的通用上下文学习，**零样本性能大幅超越** 微调或从头训练的专用模型。
- 基于 STACK 构建了首个全生物体级别人类扰动图谱 Perturb Sapiens，覆盖多组织、多类型、大量扰动，且部分预测经体外实验验证。
- 模型能够**优先排序供体特异性扰动效应**，在包含多种疾病和供体的 DiseasePert-3M 数据上证明了其能力。
- 整体建立了以细胞为推理指导的新框架，使单细胞模型从固定的监督任务中解放，走向灵活的生物学发现。

### 7. 优点
- **通用性与灵活性**：上下文学习范式使模型无需微调即能适应任意新条件，极大降低应用门槛。
- **大规模验证**：利用超过 1 亿细胞训练，并在 28 组织、892 扰动的规模上生成图谱，体现方法的 scalability。
- **生物学价值**：首次提供全生物体扰动图谱和供体特异性效应排序，对药物开发、个性化医学具有直接意义。
- **实验验证加持**：对图谱进行的体外实验验证，将计算预测与实验证据结合，增强了可信度。

### 8. 不足与局限
- **物种限制**：仅基于人类数据训练，跨物种泛化能力未知。
- **算力未披露**：缺少 GPU 型号、训练时长等关键复现信息，可能掩盖方法的高计算成本。
- **任务评估细节缺失**：摘要未列出具体下游任务类型、评估指标和消融实验，难以判断模型在细粒度任务上的优劣。
- **上下文构造依赖性**：实际应用中上下文细胞的选择策略对性能影响可能很大，但文中未见讨论。
- **可解释性**：表格注意力机制如何编码条件信号的机理未阐明，可能影响模型在关键发现中的可信度。
- **数据偏差风险**：预训练数据虽大，但可能未完全覆盖所有细胞状态或稀有扰动，对极罕见条件的效果未知。

（完）
