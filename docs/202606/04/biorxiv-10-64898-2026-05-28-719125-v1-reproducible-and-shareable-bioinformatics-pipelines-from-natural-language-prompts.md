---
title: Reproducible and shareable bioinformatics pipelines from natural-language prompts
title_zh: 从自然语言提示生成可复现、可共享的生物信息学流程
authors: "Kim, H.-M., Jeong, H., Mekonnen, A. M., Kim, Y., Oh, Y., Lee, H., Jung, C., Park, J."
date: 2026-06-01
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.28.719125v1.full.pdf"
tags: ["query:prompt-learn"]
score: 8.0
evidence: 使用自然语言提示，无任务示例，引导LLM生成生物信息学流程
tldr: 大型语言模型(LLM)生成生物信息学流程时，因对话非确定性和环境差异难以复现，也无法在远程HPC上运行共享。为此，我们提出Autopipe平台，引导MCP兼容LLM生成、执行和发布源码保留、可重执行容器化流程。平台集成桌面应用、在线注册表、网页查看器及CLI工具，支持在任意本地远程服务器执行分析并可视化结果。Autopipe将对话分析转化为可重执行、可共享的工作流，提升研究的可复现性与协作性。
source: biorxiv
selection_source: fresh_fetch
motivation: LLM生成的生物信息学流程难以跨会话复现，无法在远程HPC运行或共享。
method: 提出Autopipe平台，引导MCP兼容LLM生成源码保留、可重执行的容器化流程，并支持远程执行。
result: Autopipe集成桌面应用、在线注册表、网页查看器与CLI工具，实现本地远程服务器分析执行与可视化。
conclusion: 将对话分析转变为可复现、可共享的工作流，推动生物信息学研究协作与传播。
---

## 摘要
大型语言模型（LLM）越来越多地用于生成生物信息学流程，并根据自然语言提示开展分析。然而，由于LLM驱动的对话具有非确定性，且本地执行环境存在异构性，由此产生的分析往往难以跨会话复现，也无法在远程高性能计算（HPC）服务器上运行、共享或复用。我们推出了Autopipe平台，它可引导任何兼容模型上下文协议（MCP）的LLM生成、执行并发布源码保留、可重新执行的容器化流程。Autopipe使用户能够在任何本地部署的远程服务器上执行生物信息学流程——并配有全面的搭建文档，面向无服务器管理经验的研究人员——还能通过可扩展的网页端结果查看器实现结果可视化。Autopipe平台包含四个组件：一个内嵌MCP服务器的桌面应用，用于流程管理与远程执行；一个在线注册中心，用于发现流程与插件；一个基于网页的结果查看器；以及一个用于定制查看器插件的命令行界面工具。Autopipe将对话式分析转化为可重新执行、可共享的工作流。Autopipe可在https://autopipe.org/免费获取。

## Abstract
Large language models (LLMs) are increasingly used to generate bioinformatics pipelines and to carry out analyses from natural-language prompts. However, the resulting analyses are often difficult to reproduce across sessions, owing to the non-deterministic nature of LLM-driven conversations and heterogeneity of local execution environments, and cannot run on remote high-performance computing (HPC) servers or be shared and reused. We present Autopipe, a platform that guides any Model Context Protocol (MCP) - compatible LLM to produce, execute, and publish source-preserved, re-executable containerized pipelines. Autopipe enables users to execute bioinformatics pipelines on any on-premises remote servers - supported by comprehensive setup documentation aimed at researchers without prior server-administration experience - and to visualize results through an extensible web-based viewer. The Autopipe platform comprises four components: a desktop application with an embedded MCP server for pipeline management and remote execution, an online registry for pipeline and plugin discovery, a web-based result viewer, and a CLI tool for customizing viewer plugins. Autopipe turns conversational analysis into re-executable and shareable workflows. Autopipe is freely available at https://autopipe.org/.