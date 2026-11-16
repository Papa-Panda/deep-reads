# 从一次GDR的D2H拷贝，理解 QP、MR、CQ 和网卡 DMA

> 德布劳钦（LLM Infra 底层码农，2026-10-25）以 DeepSeek DeepInfer 的 KV swap-in 为引子，用一个 4096 字节 GDR D2H 拷贝最小 demo，把 RDMA READ 全链路讲透：QP/MR/CQ、控制面与数据面、网卡 DMA 如何绕过 CPU 与 GPU SM、经 PCIe BAR 搬数据；64 赞 / 142 收藏，正撞推理优化与 GPU 底层主线，适合当作 RDMA/GDR 的案头手册。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-351-从一次gdr的d2h拷贝-理解-qp-mr-cq-和网卡-dma/

🔗 原文：https://zhuanlan.zhihu.com/p/2097738239109079766
