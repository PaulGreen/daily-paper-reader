---
title: "ProtGPT3: an Open-source family of Promptable and Aligned Protein Language Models"
title_zh: "ProtGPT3: 一个可提示且对齐的开源蛋白语言模型家族"
authors: "Garibbo, M., Boxo Corominas, G., Stocco, F., Illanes Vicioso, R., Middendorf, L., Ferruz, N."
date: 2026-06-08
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.04.730041v1.full.pdf"
tags: ["query:prompt-learn"]
score: 9.0
evidence: 通过提示实现无需微调的推理时控制
tldr: 生成式蛋白质语言模型能探索海量序列空间进行蛋白质设计，但可靠控制生成以靶向特定功能家族仍是难题。ProtGPT3系列发布覆盖112M至10B参数的开源模型，集成HuggingFace，支持单序列与MSA提示的灵活条件生成。研究系统比较监督微调和少样本提示，并对单序列模型实施基于全蛋白组的序列复杂度和结构置信度对齐。结果显示对齐可显著降低低复杂度序列生成并保持多样性，少样本提示作为监督微调的有竞争力和可扩展替代方案。在低数据脱氟酶案例中，ProtGPT3-MSA获得更高计算成功率，设计经实验验证可溶且表达。进一步探索推理时计算，引入基于同源序列的Feynman-Kac推理过程以引导生成。该工作为可控蛋白质设计提供了开放工具和创新控制方法。
source: biorxiv
selection_source: fresh_fetch
motivation: 生成式蛋白质语言模型在设计蛋白质时空前广阔，但缺乏可靠的对齐方法和推理时提示控制，难以定向生成功能家族序列。
method: 搭建112M-10B参数的单序列与MSA提示蛋白质语言模型家族，系统比较监督微调和少样本提示，并采用序列复杂度和结构置信度指标进行后训练对齐，引入Feynman-Kac推理指导MSA模型生成。
result: 后训练对齐在减少低复杂度序列的同时保持多样性；少样本提示是与监督微调相当且更可扩展的替代方案；脱氟酶案例中ProtGPT3-MSA计算成功率高，设计可溶且表达。
conclusion: ProtGPT3开源家族为蛋白质设计提供了灵活可控的生成工具，展示了后训练对齐和少样本提示的有效性，以及推理时计算在引导生成方面的潜力。
---

## 摘要
生成式蛋白语言模型(pLMs)能够探索广阔的序列空间以进行蛋白质设计，但可靠地控制生成朝向所需功能家族仍然具有挑战性。尽管蛋白质生成总体上遵循了自然语言处理的趋势，但有两个方向仍未被充分探索：优化模型行为以实现设计目标的对齐方法，以及在推理时无需微调即可实现基于提示的控制。我们推出了ProtGPT3，这是一个开源的蛋白语言模型家族，参数规模从1.12亿到100亿，并整合到了Hugging Face生态系统中。该套件包含单序列和多序列比对(MSA)可提示模型，为生成提供了灵活的条件设定。在不同模型规模和蛋白家族中，我们系统比较了监督微调和使用同源序列的少样本提示。类似于大语言模型(LLMs)经常被对齐以符合用户意图，我们使用全蛋白质组的序列复杂度和结构置信度指标研究单序列模型的训练后对齐。我们发现对齐在保留序列多样性的同时减少了低复杂度生成。此外，我们表明，少样本提示是监督微调用于可控生成的一个有竞争力且更可扩展的替代方案。在一个低数据脱氟酶案例研究中，ProtGPT3-MSA取得了比微调基线更高的计算成功率，生成的分子在实验验证中表现出可溶性和表达。最后，我们通过引入基于同源的费曼-卡茨推理过程来探索MSA模型中推理时计算的潜力，以引导蛋白质生成朝向期望目标。所有模型均可在https://huggingface.co/collections/AI4PD/protgpt3-family公开获取。

## Abstract
Generative protein language models (pLMs) enable exploration of vast sequence spaces for protein design, but reliably controlling generation toward desired functional families remains challenging. While protein generation has broadly followed trends in NLP, two directions remain underexplored: alignment methods that optimize model behavior toward design objectives, and prompting-based control at inference time without fine-tuning. We introduce ProtGPT3, an open-source family of protein language models spanning 112M to 10B parameters and integrated with the Hugging Face ecosystem. The suite includes both single-sequence and multiple sequence alignment (MSA)-promptable models, enabling flexible conditioning for generation. Across model scales and protein families, we systematically compare supervised fine-tuning and few-shot prompting using homologous sequences. Analogous to how large language models (LLMs) are routinely aligned with user intent, we study post-training alignment in single-sequence models using sequence-complexity and structure-confidence metrics across the proteome. We find that alignment reduces low-complexity generations while preserving sequence diversity. Furthermore, we show that few-shot prompting is a competitive and more scalable alternative to supervised fine-tuning for controlled generation. In a low-data defluorinase case study, ProtGPT3-MSA achieved higher computational success rates than fine-tuned baselines and produced designs that were soluble and expressed following experimental validation. Finally, we explore the potential of inference-time compute in MSA models by introducing a homolog-based Feynman-Kac inference procedure for steering protein generation toward desired targets. All models are publicly available at https://huggingface.co/collections/AI4PD/protgpt3-family.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义

- **研究背景**：蛋白质语言模型（pLMs）通过学习海量蛋白序列的生成分布，能够探索广阔的序列空间，在蛋白质从头设计领域潜力巨大。然而，现有模型生成过程往往“不可控”，难以将输出定向到具有特定功能或结构特征的蛋白家族。
- **核心问题**：如何在不依赖昂贵微调的情况下，通过“对齐（alignment）”和“提示（prompting）”两种机制，实现对生成结果的可靠、灵活控制。这两大方向在自然语言处理中已被深度探索，但在蛋白质生成领域尚属空白。
- **整体含义**：该工作旨在为可控蛋白质设计提供一个开源、可扩展的解决方案，使得研究者可以用“提示”而非重新训练的方式，引导模型朝向目标家族生成，同时保证生成序列的多样性与品质。

## 2. 论文提出的方法论

- **整体框架**：构建ProtGPT3模型家族，覆盖1.12亿至100亿参数规模，全部集成Hugging Face，支持两种提示模式：
  - **单序列模型**：仅以单条蛋白质序列作为输入/条件。
  - **MSA可提示模型**：能够接收多序列比对（MSA）作为提示，进而生成同源家族内的新序列。
- **训练后对齐**：
  - **目的**：优化模型行为，使其生成更“类天然蛋白”的序列。
  - **方法**：利用全蛋白质组数据，定义两类指标——序列复杂度（防止低复杂度重复区）和结构置信度（如基于AlphaFold等的结构可信度评分），以此为奖励信号对单序列模型进行对齐训练（类似于语言模型中的RLHF）。
- **少样本提示**：
  - 将少量同源序列拼接成“提示文本”，直接输入模型以条件生成，无需任何梯度更新。
  - 系统对比了这种推理时提示与经典监督微调的效果。
- **费曼-卡茨（Feynman-Kac）推理引导**：
  - 面向MSA模型，在推理阶段引入基于同源序列相似度的势函数，通过序列级别的加权重采样（费曼-卡茨公式）引导生成过程朝向期望功能特征，实现在推理时计算中“按需引导”。

## 3. 实验设计

- **数据集与场景**：
  - 全蛋白质组序列（用于对齐训练的指标计算）。
  - 多个蛋白家族（未详细列举，但文中明确“跨模型规模和蛋白家族”的系统比较）。
  - 低数据场景典型案例：脱氟酶家族（数据稀缺的功能蛋白），用于验证极端条件下的生成能力。
- **Benchmark与方法对比**：
  - **监督微调**：在目标家族上做传统微调。
  - **少样本提示**：直接输入同源序列作为提示。
  - **对齐前后对比**：比较未对齐模型和对齐后模型在全蛋白质组上的序列复杂度与多样性。
  - 对于脱氟酶案例，同时评估 **计算成功率**（如生成序列符合家族特征的比率）和 **实验验证**（表达可溶性）。
  - **Feynman-Kac推理**对比普通生成。
- **实验验证**：脱氟酶设计进行湿实验表达与可溶性测试。

## 4. 资源与算力

- 论文中**未明确给出**训练所用GPU型号、数量及具体训练时长。
- 但考虑到模型规模最大达10B参数，以及多尺度训练与评估，预估需使用大量高端GPU（如A100）进行较长时间的预训练、对齐及消融实验。具体算力细节需参考原文或附录（基于提供的元数据无法获取）。

## 5. 实验数量与充分性

- **实验模块**大致可分为：
  1. 多尺度模型构建与基本生成能力验证。
  2. 训练后对齐前后的生成质量对比（复杂度、多样性指标）。
  3. 不同蛋白家族上的监督微调 vs. 少样本提示的定量比较。
  4. 低数据脱氟酶案例的全面评估（计算+实验）。
  5. Feynman-Kac推理引导的探索性实验。
- **充分性判断**：从研究框架看，同时涵盖了对齐方法、推理时控制方法、多规模模型、计算机评估与真实实验验证，结构完整。比较涉及多种蛋白家族和多种模型尺寸，消融较充分。作为预印本，实验设置较大规模，客观性较强，但缺少与外部其他蛋白生成工具（如ProGen、ProtGPT2）的直接对比数据，这部分在摘要中未体现，可能需看全文。

## 6. 论文的主要结论与发现

- **对齐的有效性**：训练后对齐能显著减少低复杂度序列的生成，同时基本保持了生成序列的天然多样性，不损害探索能力。
- **少样本提示的竞争力**：在多个蛋白家族上，少样本提示取得了与监督微调相当甚至更好的控制效果，且无需重新训练，具有极强的可扩展性和部署灵活性。
- **低数据场景的优势**：在脱氟酶案例中，ProtGPT3-MSA的少量提示即可获得高于微调基线的计算成功率，且生成变体在实验中可溶、可表达，证明方法适用于数据匮乏的目标。
- **推理时引导的潜力**：基于同源的费曼-卡茨推理可在不改变模型参数的条件下，按需将生成分布推向期望功能区域，为事后控制提供了新范式。

## 7. 优点（方法或实验设计亮点）

- **完全开源与生态整合**：全套模型（112M–10B）公开在Hugging Face，降低使用门槛，方便社区进行提示、对齐等下游扩展。
- **双模提示设计**：同时支持单序列和MSA提示，灵活适应不同蛋白质设计场景。
- **首次系统引入对齐概念**：将LLM中对齐的思想迁移到蛋白质生成，并证实其对低复杂度生成的抑制效果。
- **少样本提示替代微调**：展示了不更新模型即可控制生成的简便途径，极大提升了蛋白质设计流程的迭代速度。
- **“干湿结合”验证**：并非纯粹的计算评估，有真实蛋白表达与可溶性数据支撑，增强了方法可信度。
- **推理时计算创新**：尝试费曼-卡茨推理，为未来更复杂的“推理时优化”打开大门。

## 8. 不足与局限

- **实验验证范围有限**：湿实验仅针对脱氟酶一个案例，其他蛋白家族的功能验证仍属空缺，泛化性待进一步证明。
- **对齐指标的局限性**：序列复杂度和结构置信度虽能过滤掉部分不合理序列，但与实际功能（如催化活性、热稳定性）之间可能存在差距，对齐目标未必完全反映设计意图。
- **少样本提示的依赖性**：提示的质量和同源序列的选取策略对生成结果有显著影响，但论文可能未全面探讨提示构造的鲁棒性。
- **大模型推理成本**：10B级模型在推理时计算或费曼-卡茨采样中可能产生较高延迟，实际应用中的效率考量未充分讨论。
- **对比基线不足**：摘要未提及与当前其他前沿蛋白生成模型（如ESM-IF、ProteinMPNN配合扩散模型等）的横向比较，可能遗漏了更强大的竞争方法。

（完）
