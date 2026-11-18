# Zero-SM NCCL：把 GPU 集合通信从 SM 上彻底摘下来

> Arthur（2026-11-16，31 赞 / 71 收藏）解读 ETH Zurich + NVIDIA 的 Zero-SM NCCL 论文（arXiv:2611.18075）：把 NCCL 集合通信从 SM 上彻底摘掉，改由 Copy Engine 与 NIC DMA 搬数据、CUDA 流内存操作做同步；144 MiB AllGather 下 GEMM 减速从 legacy ring 的 32.9% 降到 3.9%，但结论克制——只适用于大消息、GPU-bound 步骤与深流水线，对默认已选对称核的 tuner 多为打平或小胜。正撞 GPU 底层与分布式训练主线。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-357-zero-sm-nccl-把-gpu-集合通信从-sm-上彻底摘下来/

🔗 原文：https://zhuanlan.zhihu.com/p/2105892924793934296
