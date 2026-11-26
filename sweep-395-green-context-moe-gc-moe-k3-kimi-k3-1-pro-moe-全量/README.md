# 【Green Context MoE】GC MoE K3：Kimi K3.1 Pro MoE 全量优化

> 木子知（2026-11-24）用 CUDA Green Context 把整个 Kimi K3.1 Pro latent-MoE 子层当作一个调度单元：计算/通信双分区 + 5 个基础角色 + 2 个条件角色按数据就绪推进，GB200 上相对 SGLang 平均快 1.13×、vLLM 快 1.37×；附 GitHub 实现与 arXiv 论文。MoE 推理调度的硬核实战拆解。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-395-green-context-moe-gc-moe-k3-kimi-k3-1-pro-moe-全量/

🔗 原文：https://zhuanlan.zhihu.com/p/2108321381012203489
