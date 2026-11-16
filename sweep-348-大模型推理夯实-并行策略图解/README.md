# 大模型推理夯实：并行策略图解

> 科英（2026-05-09，491 赞 / 1402 收藏）把推理并行 7 种策略 TP、PP、DP、EP、DP Attention、SP、CP 按权重 / 批次 / 序列 / 层四个切分维度一次讲透，每种都按「切什么、在哪通信、何时用」展开，并对照 SGLang / vLLM 源码（2026-05-05）讲清 DP+EP 语义分歧与 DP Attention 的真相；正撞推理优化与 MoE 部署主线，适合当作并行策略的案头手册。文中通信量均为量级估算，非实测基准。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-348-大模型推理夯实-并行策略图解/

🔗 原文：https://zhuanlan.zhihu.com/p/2035106376138085860
