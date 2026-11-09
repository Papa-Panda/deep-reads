# 再探 CUDA Graph：核心机制、多图复用以及 Dual AR 模型的统一覆盖优化

> Chayenne Zhao 在 SGLang-Omni 为 Fish Audio S2-Pro（PR #153）把 Slow AR（Qwen3-4B）与 Fast AR（9 步码本循环）统一进一张 CUDA Graph 的实战复盘：从捕获/实例化/回放机制与五条约束出发，讲清指针稳定、内存池共享、延迟捕获与持久 buffer 的工程实现；实测 eager 55.6 → 仅图 88 → 全编译 126 tok/s。值得他看的是它把 CUDA Graph 从提速技巧还原为静态化优化的设计哲学，且反直觉的结论是图优化真正 payoff 在微秒级小算子的快头、而非毫秒级大 GEMM 的慢头，正对 CUDA/推理优化主线。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-317-再探-cuda-graph-核心机制-多图复用以及-dual-ar-模型的统一覆盖优化/

🔗 原文：https://zhuanlan.zhihu.com/p/2017950447520980998
