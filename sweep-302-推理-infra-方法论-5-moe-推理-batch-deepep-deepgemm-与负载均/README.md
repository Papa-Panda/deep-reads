# 推理 INFRA 方法论（5）：MoE 推理：Batch、DeepEP、DeepGEMM 与负载均衡

> 推理 INFRA 方法论系列第 5 章，以 Batch 为主线讲 MoE 推理的三块硬骨头：专家越切越碎如何让 GEMM 变小变碎，DeepEP、DeepGEMM、EPLB 各自解决通信、填充与负载偏斜，并用 Qwen3.5-397B-A17B-FP8 的 8 卡实测对照理论预算。值得他看的是它把 MoE 推理的系统问题从“调参”还原为 Roofline、通信建模与 tile 填充的定量分析，且逐项给出优化的收益天花板，正对推理 infra 这一优先方向。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-302-推理-infra-方法论-5-moe-推理-batch-deepep-deepgemm-与负载均/

🔗 原文：https://zhuanlan.zhihu.com/p/2100932196798407277
