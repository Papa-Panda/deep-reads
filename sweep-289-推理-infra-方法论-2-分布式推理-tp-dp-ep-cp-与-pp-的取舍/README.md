# 推理 INFRA 方法论（2）：分布式推理：TP、DP、EP、CP 与 PP 的取舍

> 从权重、KV、激活与通信预算出发，推导分布式推理中 TP、DP、EP、CP、PP 各自的适用边界：GQA 与 MLA 在 TP 下为何不同、MoE 为何要按最差专家定容量、CP 只在长上下文时划算、PP 为何不适合在线解码。值得他看的是它把并行策略变成“先看哪个瓶颈先 binding”的系统设计问题，并给出可算的内存与气泡估算。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-289-推理-infra-方法论-2-分布式推理-tp-dp-ep-cp-与-pp-的取舍/

🔗 原文：https://zhuanlan.zhihu.com/p/2100931715350935161
