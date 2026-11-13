# 从 Dual GEMM 到 MXFP8：拆解与加速 DeepSeek V4 DSA

> Dingirsu 拆解 DeepSeek V4 稀疏注意力 DSA 在 Blackwell 上的 BF16 kernel（Dual GEMM 如何把大 GEMM 拆成小块以喂饱 tensor core），再用 MXFP8 做到相对 FlashMLA 约 2 倍加速（prefill 2.03 倍、decode 2.05 至 2.22 倍），代价是 AIME 2025 掉 10 个点、GPQA 与 GSM8K 掉约 2 至 3.5 个点，作者把精度修复留给未来的 attention QAT。值得他看的是 kernel 级的逐周期 profiling 与 rank-1 量化 scale 分解，正撞稀疏注意力与量化主线。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-336-从-dual-gemm-到-mxfp8-拆解与加速-deepseek-v4-dsa/

🔗 原文：https://zhuanlan.zhihu.com/p/2093333147786266301
