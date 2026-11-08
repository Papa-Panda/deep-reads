# 从混合 Batch 到 GPU Kernel：读懂 vLLM 与 SGLang 的 Attention 执行

> 讲 vLLM 与 SGLang 如何执行一轮混合 batch 的 Attention：从 chunked prefill 调度、变长张量与分页 KV，到 FlashAttention/FlashInfer 的后端组织、FA3 PackGQA 源码案例、CUDA Graph 复用与后端选择规则，并给出性能对照与调优排查顺序。值得他看的是它把推理 infra 从“调哪个后端”还原为调度、后端、kernel 三层分工的定量问题，且对引用数据的适用范围做了明确标注，正对推理优化主线。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-309-从混合-batch-到-gpu-kernel-读懂-vllm-与-sglang-的-attent/

🔗 原文：https://zhuanlan.zhihu.com/p/2102456332972449965
