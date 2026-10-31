# 理解 DeepInfer（二）：并行策略与负载均衡

> 知乎推荐流专栏（作者 mingming，AI-HPC 专栏，DeepInfer 理解系列第二篇，全文已通读）。中心论点：并行决定等待出现在哪里，负载均衡决定等待能否被消掉。文章拆解 DeepSeek 开源推理框架 DeepInfer 的并行与均衡：注意力按请求做数据并行、MoE 按专家做专家并行；decode 用 Wide-EP 开到 64～128 卡而 prefill 只用小规模并行；EPLB 靠重排加副本压峰值负载；DPLB 靠请求落点与 prefill 切块对齐注意力耗时；末节讲视觉编码按 patch 数估负载。值得他看的是这条把推理 infra 的等待结构讲透的分析：两类等待（注意力后等专家分发、专家后等结果汇聚）要由两套均衡机制分别处理。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-271-理解-deepinfer-二-并行策略与负载均衡/

🔗 原文：https://zhuanlan.zhihu.com/p/2098821657376845972
