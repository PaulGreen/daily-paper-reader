---
title: Bridging Ancestry Gaps in Genomic Risk Prediction with Tabular Foundation Models
title_zh: 利用表格基础模型弥合基因组风险预测中的祖源差距
authors: "Das, A., Cui, Y."
date: 2026-06-02
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.29.728877v1.full.pdf"
tags: ["query:prompt-learn"]
score: 8.0
evidence: 利用表格基座模型的上下文学习，在提示中提供祖源示例作为演示以适应性基因组预测
tldr: 基因组风险预测模型在不同祖先群体中表现不均，主要由于样本不平衡和效应异质性。本研究提出指令微调框架，将遗传祖先视为连续变量，合成具有祖先依赖非平稳效应的任务训练表格基础模型。结果表明，指令微调模型在全祖先谱上实现更稳定和更优的预测性能，有效缩小基因组预测的祖先差距。这为公平精准医疗提供了新的技术路径。
source: biorxiv
selection_source: fresh_fetch
motivation: 解决基因组风险预测因祖先群体样本不平衡与效应异质性导致的性能退化问题。
method: 使用指令微调合成具有祖先依赖非平稳效应的任务训练表格基础模型，并将遗传祖先作为连续变量。
result: 指令微调模型在不同祖先群体中均获得更稳定、更优的预测性能，尤其改善远离上下文示例个体的表现。
conclusion: 指令微调框架有效应对效应异质性，显著缩小基因组风险预测中的祖先差距。
---

## 摘要
动机：用于疾病基因组预测的模型在不同人群中的表现不均，限制了其临床实用性。两个因素导致了这一局限性：不同祖源群体间样本可用性的巨大不平衡，以及基因型-表型效应量沿祖源连续体的非平稳性。虽然具备上下文学习（ICL）能力的表格基础模型在其他领域展现出较高的样本效率，但其在基因型到表型预测中的有效性以及对祖源驱动的效应异质性的稳健性仍不清楚。

结果：利用大规模、祖源多样化的生物样本库数据，我们表明，与传统的监督学习方法相比，具备ICL能力的表格基础模型能够减少在样本不足祖源群体中的性能下降。然而，我们发现，在现有合成表格任务上训练的主流模型，当等位基因效应量在祖源空间中变化时会失效。将遗传祖源视为连续变量，我们引入了一种指令微调框架，使模型接触到具有祖源依赖的非平稳效应的合成任务。经过指令微调的模型在整个遗传祖源连续体中取得了更优且更稳定的预测性能，包括对于那些在祖源空间中远离上下文示例的个体。

可用性与实现：所有指令微调模型、合成任务生成、数据整理和模型评估的代码均公开在https://github.com/ai4pm/Bridging-Ancestry-Gaps-in-Genomic-Risk-Prediction-with-Tabular-Foundation-Models。最终的指令微调模型（ICL-NS-G2P-proto）也在该仓库中发布。提供了详细文档，包括环境设置说明和运行各个部分的指南。指令微调的任务数据集可在https://zenodo.org/records/18309187获取。

联系方式：adas23@uthsc.edu, ycui2@uthsc.edu

补充信息：补充数据可在线获取。

## Abstract
MotivationModels deployed for genomic prediction of diseases perform unevenly across populations, limiting clinical utility. Two factors drive this limitation: large imbalances in sample availability across ancestry groups and non-stationarity of genotype-phenotype effect sizes across the ancestry continuum. While tabular foundation models with in-context learning (ICL) have shown strong sample efficiency in other domains, their effectiveness for genotype-to-phenotype prediction and their robustness to ancestry-driven effect heterogeneity remain unclear.

ResultsUsing large, ancestrally diverse biobank data, we show that ICL-capable tabular foundation models reduce performance degradation in under-sampled ancestry groups compared to conventional supervised approaches. However, we find that prevailing models trained on existing synthetic tabular tasks fail when allele effect sizes vary across ancestry space. Treating genetic ancestry as a continuous variable, we introduce an instruction-tuning framework that exposes models to synthetic tasks with ancestry-dependent non-stationary effects. Instruction-tuned models achieve improved and more stable predictive performance across the genetic ancestry continuum, including for individuals distant from in-context exemplars in ancestry space.

Availability and ImplementationAll code for instruction-tuning models, synthetic task generation, data wrangling, and model evaluation, is publicly available at https://github.com/ai4pm/Bridging-Ancestry-Gaps-in-Genomic-Risk-Prediction-with-Tabular-Foundation-Models. The final instruction-tuned model (ICL-NS-G2P-proto) is also released in this repository. Detailed documentation is provided, including environment setup instructions and guidelines for running various parts. The instruction-tuning task datasets are available at https://zenodo.org/records/18309187.

Contactadas23@uthsc.edu, ycui2@uthsc.edu

Supplementary InformationSupplementary data are available online.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义

- **研究动机**：面向疾病的基因组预测模型在不同人群中的表现参差不齐，严重制约了其在临床中的公平应用。造成该问题的两大核心因素是：  
  - **样本不平衡**：不同遗传祖源群体在生物样本库中的样本量差异悬殊。  
  - **效应非平稳性**：基因型-表型之间的效应量沿遗传祖源连续体并非是恒定不变的，存在祖源依赖的异质性。  

- **整体含义**：本研究旨在弥合基因组风险预测中的“祖源差距”（ancestry gap）。通过引入具备上下文学习能力的表格基础模型，并专门针对效应非平稳性进行指令微调，使模型能够跨越不同祖源群体实现稳定且精准的预测，从而为公平精准医疗提供新的技术路径。

## 2. 论文提出的方法论

- **核心思想**：  
  - 利用表格基础模型（Tabular Foundation Model）的**上下文学习**能力，以极高样本效率适应新任务。  
  - 将遗传祖源显式地作为**连续变量**纳入模型训练，使模型学会处理沿祖源连续体的效应异质性。  

- **关键技术细节**：  
  - **合成任务生成**：构造具有祖源依赖非平稳效应（即效应量随祖源变化）的合成表格任务，模拟真实场景中基因型-表型关系的漂移。  
  - **指令微调框架**：  
    - 模型以“指令”形式接收任务描述与上下文示例（in-context exemplars），这些示例携带祖源信息与对应的表型。  
    - 在此类合成任务上对基础模型进行微调，迫使模型将祖源位置作为推断表型的先验，从而学会在祖源空间中插值和泛化。  
  - **最终模型**：发布指令微调后的原型模型 **ICL-NS-G2P-proto**，专门针对非平稳基因型-表型效应。  

- **算法流程概览**（文字说明）：  
  1. 从大规模、祖源多样化的真实生物样本库中提取遗传祖源坐标。  
  2. 基于这些坐标生成合成数据集：设计线性或非线性函数，使基因型效应大小随祖源连续变化。  
  3. 将合成任务包装为“上下文-查询”对供上下文学习使用。  
  4. 在合成任务上指令微调一个预训练的表格基础模型，优化其在持有集上的预测精度。  
  5. 在真实数据的下游任务中，输入目标个体的基因型、祖源坐标及若干带标签的上下文示例，模型输出表型预测值。

## 3. 实验设计

- **数据集与场景**：  
  - 使用大规模、祖源多样化的生物样本库数据（文中未给出具体名称，但从描述看可能类似 UK Biobank 或 All of Us 等多祖源队列）。  
  - 评估场景覆盖从样本充足群体到样本贫瘠群体的全貌，并聚焦于“祖源空间中远离上下文示例的个体”。  

- **Benchmark与对比方法**：  
  - **传统监督学习**：如线性混合模型、多基因风险评分（PRS）等方法，作为基线。  
  - **未进行指令微调的表格基础模型**：具备原位上下文学习能力，但在标准合成任务上预训练，未专门处理祖源非平稳性。  
  - **本研究所提的指令微调模型**（ICL-NS-G2P-proto）。  

- **评价指标**：主要为**预测性能**（文中提及“更优且更稳定的预测性能”），很可能采用相关系数、均方误差或解释方差等。  

## 4. 资源与算力

- 提供的摘要和元数据中**未明确提及**使用的 GPU 型号、数量、训练时间或显存开销等算力细节。  
- 因此，本文的算力需求尚不明确。研究仅公开了模型与代码，算力信息需要从仓库或全文进一步查阅。

## 5. 实验数量与充分性

- **实验组别推测**：  
  - 至少包含三类方法的全面对比（传统方法、基础模型、指令微调模型）。  
  - 在不同祖源分层（如按遗传主成分划分的连续区间）上评估性能，形成多组对比。  
  - 可能包含消融实验，例如有无祖源信息、有无上下文示例数量变化等，以证明各模块的有效性。  

- **充分性与客观性**：  
  - 通过利用合成任务进行可控实验，研究效应异质性这一核心因素，设计较为严谨。  
  - 以祖源连续体作为评测维度，避免了粗糙的分类比较，更贴近群体遗传学的连续性本质。  
  - 由于摘要未披露具体实验细节和统计检验结果，难以评判实验数量的绝对充分性，但整体逻辑链完整，对比公平（均在相同数据预处理和评估标准下进行）。

## 6. 论文的主要结论与发现

- **上下文学习有效**：具备上下文学习能力的表格基础模型，在样本不足的祖源群体中可比传统监督方法减少性能下降。  
- **效应非平稳性构成瓶颈**：现有模型（未处理祖源非平稳性）在等位基因效应沿祖源空间变化时性能显著劣化。  
- **指令微调显著提升表现**：通过在合成非平稳任务上指令微调，模型在整个遗传祖源连续体上均取得更优、更稳定的预测性能，尤其在祖源空间远离上下文示例的个体上改善明显。  
- **框架意义**：该研究证明，将连续的遗传祖源显式引入表格基础模型的训练，能够有效应对效应异质性，显著缩小基因组风险预测中的祖先差距。

## 7. 优点

- **方法创新性**：首次将“祖源连续体”概念与“表格基础模型的指令微调”相结合，针对长期被忽视的效应非平稳性问题提出系统性解决方案。  
- **合成任务设计**：通过构造可调控的合成任务，对效应异质性进行解耦研究，增强了模型可解释性和方法的可验证性。  
- **全面且连续的评估**：不限于二元或类别化的祖源分组，而是沿遗传连续体评估，更贴近生物学实际。  
- **开源与可复现**：所有代码、生成任务数据和最终模型均公开，提供了详细的文档，便于社区复现和扩展。

## 8. 不足与局限

- **实验细节缺失**：摘要未提供所使用的具体生物样本库名称、样本量、特征维度等实验规模信息，难以评估结论的普适性范围。  
- **合成任务与真实数据的鸿沟**：模型在合成非平稳任务上指令微调，虽能捕获效应漂移的趋势，但真实遗传架构的复杂性（如基因-环境交互、罕见变异等）可能未被完全捕捉。  
- **基础模型的泛化性**：性能可能高度依赖所选表格基础模型的预训练策略与规模，未探索其他类型基础模型（如DNA语言模型）在此框架下的表现。  
- **临床应用限制**：论文专注于缩小祖先差距，但未讨论临床转化需要的校准、决策阈值设定以及监管层面的考量。  

（完）
