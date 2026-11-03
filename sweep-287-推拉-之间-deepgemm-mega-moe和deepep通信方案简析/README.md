# “推拉”之间：DeepGEMM、Mega MoE和DeepEP通信方案简析

> 以 DeepSeek V4.1-Flash 的 MoE 专家并行为例，对照 DeepEP 与 DeepGEMM Mega MoE 的通信设计：为什么 dispatch 一边是推、一边是拉，而 combine 两边都是推。值得他看的是它把推拉选择归结为“写时是否知道最终地址”和“谁控制节奏”，正对 MoE 推理通信与融合 kernel 的核心问题。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-287-推拉-之间-deepgemm-mega-moe和deepep通信方案简析/

🔗 原文：https://zhuanlan.zhihu.com/p/2099874106212628019
