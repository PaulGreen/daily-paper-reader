<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-06-04
- 运行时间：2026-06-04 21:38:03 UTC
- 运行状态：成功
- 本次总论文数：17
- 精读区：10
- 速读区：7

### 今日简报（AI）
今日聚焦提示工程前沿：精读两篇10分论文揭示“训练提示”如何提升微调鲁棒性，以及双曲注意力蒸馏如何校准多模态上下文学习。  
最值得关注：状态自适应优化让模型学会“何时信赖提示”，而超双曲空间中的锚点蒸馏有效防止注意力崩塌。  
建议读者跟进“虚假提示”攻击性研究，并尝试将鲁棒提示策略迁移到低资源语言场景。
- 详情：[/202606/04/README](/202606/04/README)

### 精读区论文标签
1. [Training Prompt Matters: State-Adaptive Optimization for Robust Fine-Tuning](/202606/04/2606.01967v1-training-prompt-matters-state-adaptive-optimization-for-robust-fine-tuning)  
   标签：评分：10.0/10、query:prompt-learn
   evidence：揭示训练提示显著影响跨任务泛化，并提出状态自适应提示优化
2. [Hyper-ICL: Attention Calibration with Hyperbolic Anchor Distillation for Multimodal In-Context Learning](/202606/04/2606.04434v1-hyper-icl-attention-calibration-with-hyperbolic-anchor-distillation-for-multimodal-in-context-learning)  
   标签：评分：10.0/10、query:prompt-learn
   evidence：通过轻量级适配器重建多模态上下文演示效果，无需推理时演示
3. [Structured Prompt Optimization Meets Reinforcement Learning for Global and Local Interpretability over Complex Text](/202606/04/2605.29076v2-structured-prompt-optimization-meets-reinforcement-learning-for-global-and-local-interpretability-over-complex-text)  
   标签：评分：9.0/10、query:prompt-learn
   evidence：结构化提示优化学习用于文本分类的自然语言规则手册
4. [Personalize Your Large Vision-language Models With In-context Prompt Tuning](/202606/04/2605.31513v1-personalize-your-large-vision-language-models-with-in-context-prompt-tuning)  
   标签：评分：9.0/10、query:prompt-learn
   evidence：提出上下文提示调优，使用连续提示向量
5. [SALSA: Speech Aware LLM Adaptation via Learned Steering Activation Vectors](/202606/04/2606.00460v1-salsa-speech-aware-llm-adaptation-via-learned-steering-activation-vectors)  
   标签：评分：9.0/10、query:prompt-learn
   evidence：通过监督优化学习转向向量，类似于软提示调优
6. [Towards Lightweight Reliability: Using Soft Prompts for Hallucination Mitigation in Large Language Models](/202606/04/2606.00919v1-towards-lightweight-reliability-using-soft-prompts-for-hallucination-mitigation-in-large-language-models)  
   标签：评分：9.0/10、query:prompt-learn
   evidence：使用复合损失训练软提示以抑制幻觉，直接应用了连续提示嵌入的梯度调优
7. [Decomposing how prompting steers behavior](/202606/04/2606.03093v1-decomposing-how-prompting-steers-behavior)  
   标签：评分：9.0/10、query:prompt-learn
   evidence：研究提示如何改变LLM/VLM中的表示几何
8. [Beyond Retrieval: Learning Compact User Representations for Scalable LLM Personalization](/202606/04/2606.04547v1-beyond-retrieval-learning-compact-user-representations-for-scalable-llm-personalization)  
   标签：评分：9.0/10、query:prompt-learn
   evidence：用于用户个性化的可学习前缀嵌入
9. [CRAFT: Cost-aware Refinement And Front-aware Tuning of Prompts](/202606/04/2606.04661v1-craft-cost-aware-refinement-and-front-aware-tuning-of-prompts)  
   标签：评分：9.0/10、query:prompt-learn
   evidence：帕累托前沿提示优化器，平衡准确率与令牌成本。
10. [Fast & Faithful Function Vectors](/202606/04/2606.05079v1-fast--faithful-function-vectors)  
   标签：评分：9.0/10、query:prompt-learn
   evidence：功能向量作为连续任务表示，用于引导LLM，类似于软提示

### 速读区论文标签
1. [Spurious Prompts: Can Irrelevant Prompts Steer Large Language Models?](/202606/04/2605.29678v1-spurious-prompts-can-irrelevant-prompts-steer-large-language-models)  
   标签：评分：8.0/10、query:prompt-learn
   evidence：研究离散无关提示对LLM的引导；提出黑盒搜索发现有效提示
2. [Turning Back Without Forgetting: Selective Backward Refinement for Parameter-Efficient Continual Learning](/202606/04/2606.01379v1-turning-back-without-forgetting-selective-backward-refinement-for-parameter-efficient-continual-learning)  
   标签：评分：8.0/10、query:prompt-learn
   evidence：在基于提示的持续学习中，通过梯度更新精化任务特定提示，以实现向后知识迁移
3. [From Script to Semantics: Prompting Strategies for African NLI](/202606/04/2606.03304v1-from-script-to-semantics-prompting-strategies-for-african-nli)  
   标签：评分：8.0/10、query:prompt-learn
   evidence：评估五种零样本提示策略，排除少样本示例影响，隔离提示设计效果
4. [Activation-Based Active Learning for In-Context Learning: Challenges and Insights](/202606/04/2606.05134v1-activation-based-active-learning-for-in-context-learning-challenges-and-insights)  
   标签：评分：8.0/10、query:prompt-learn
   evidence：研究基于激活的上下文示例选择以优化ICL
5. [Reproducible and shareable bioinformatics pipelines from natural-language prompts](/202606/04/biorxiv-10-64898-2026-05-28-719125-v1-reproducible-and-shareable-bioinformatics-pipelines-from-natural-language-prompts)  
   标签：评分：8.0/10、query:prompt-learn
   evidence：使用自然语言提示，无任务示例，引导LLM生成生物信息学流程
6. [Hidden Thoughts Are Not Secret: Reasoning Trace Exposure in LLMs](/202606/04/2606.00642v1-hidden-thoughts-are-not-secret-reasoning-trace-exposure-in-llms)  
   标签：评分：7.0/10、query:prompt-learn
   evidence：利用带演示的提示提取推理痕迹
7. [On the Limits of LLM Adaptability: Impact of Model-Internalized Priors on Annotation Task Performance](/202606/04/2606.00467v1-on-the-limits-of-llm-adaptability-impact-of-model-internalized-priors-on-annotation-task-performance)  
   标签：评分：6.0/10、query:prompt-learn
   evidence：研究零样本标注性能及提示中额外信息对修正错误的影响


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
