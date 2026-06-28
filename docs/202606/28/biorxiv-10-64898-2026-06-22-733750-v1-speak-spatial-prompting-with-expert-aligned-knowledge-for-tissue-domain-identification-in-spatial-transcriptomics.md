---
title: "SPEAK: Spatial Prompting with Expert Aligned Knowledge for Tissue Domain Identification in Spatial Transcriptomics"
title_zh: SPEAK：基于专家对齐知识的空间提示用于空间转录组学组织域识别
authors: "Wei, H., Luo, X., Yu, H., Liang, J., Yang, L., Sauler, M., Kaminski, N., Popa, A., Yan, X."
date: 2026-06-26
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.22.733750v1.full.pdf"
tags: ["query:prompt-learn"]
score: 6.0
evidence: 为每个细胞构建基于离散自然语言的空间上下文提示
tldr: 空间转录组学中准确识别组织域是下游分析的关键，但现有方法难以有效利用先验知识。SPEAK创新性地借助大语言模型，根据邻近细胞的类型和标志基因构建空间上下文提示，通过零样本推理和专家引导的两阶段微调实现原型更新，无缝整合跨领域知识。在STARmap、Visium、MERFISH和Xenium等多个实验数据上，SPEAK在域预测准确度、对有限先验的鲁棒性、生物学可解释性以及高效微调泛化方面均优于现有方法，为空间转录组智能分析开辟了新途径。
source: biorxiv
selection_source: fresh_fetch
motivation: 空间转录组数据分析中，组织域识别亟需融入专家先验以提升准确性，但现有计算方法欠缺。
method: SPEAK通过大语言模型，根据邻近细胞类型和标记基因构建空间上下文提示，执行零样本推理与专家引导的两阶段微调。
result: 在STARmap、Visium等数据集上，SPEAK的域预测准确度、有限先验鲁棒性和生物学可解释性均超越现有方法。
conclusion: SPEAK成功融合大语言模型与专家知识，提升空间域识别性能，并提供跨组织泛化能力。
---

## 摘要
空间解析转录组数据需要空间域识别，以实现组织微环境特异性的下游分析。本文提出SPEAK（基于专家对齐知识的空间提示），一种基于大语言模型的方法，通过利用大语言模型和人类专家的先验知识，从空间转录组数据中识别空间域。SPEAK根据每个细胞/斑点的相邻细胞的细胞类型和标记基因，为其构建空间上下文提示，通过两阶段提示实现零样本推理、专家指导微调和原型更新。在STARmap、Visium、MERFISH和Xenium数据集上的应用表明，SPEAK在域预测准确性、对有限先验知识的鲁棒性、生物学可解释性以及高效专家指导微调并能推广到其他组织切片方面，均优于现有的空间域识别方法。

## Abstract
Spatially resolved transcriptomic (SRT) data requires spatial domain identification to enable tissue microenvironment-specific downstream analyses. Here we present SPEAK (Spatial Prompting with Expert-Aligned Knowledge), a large language model (LLM) -based method to identify spatial domains from SRT data by taking advantage of the prior knowledge from both LLM and human experts. SPEAK constructs a spatial context prompt for each cell/spot based on cell types and marker genes of its neighboring cells, enabling zero-shot inference, expert-guided fine-tuning, and prototype updating through two-stage prompting. Applications to STARmap, Visium, MERFISH and Xenium datasets showed advantages of SPEAK over existing spatial domain identification methods in domain prediction accuracy, robustness to limited prior knowledge, biological interpretability, and capacity for efficient expert-guided fine-tuning with generalizability to other tissue sections.