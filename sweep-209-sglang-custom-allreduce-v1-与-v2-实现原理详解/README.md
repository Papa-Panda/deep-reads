# SGLang Custom AllReduce v1 与 v2 实现原理详解

> 知乎推荐流条目（作者 BBuf，编辑于 2026-07-27，56 赞、87 收藏）。源码级拆解 SGLang 自研 Custom AllReduce：TP 下每层两次 all-reduce、decode 单条消息仅约 16KB，瓶颈是固定开销而非带宽，NCCL 的环形多步与协议选择太重。v1（源自 vLLM）用 IPC 共享缓冲区 + Signal 双相计数 barrier，含 1stage 全读归约与 2stage 分片两档；v2 是 SGLang 自研重写（存算分离、阈值改实测调优表），新增 1shot_push 用数据本身的 +0.0 位模式作到达哨兵、彻底去掉跨卡 barrier，并有 NVLS 交换机硬件归约与 PDL 重叠。正对他的推理优化与 CUDA 底层主线。注：已通读原文（更正：本条初版摘要的作者/日期/赞藏数与一处 bug 说法有误，已按原文核实修正）。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-209-sglang-custom-allreduce-v1-与-v2-实现原理详解/

🔗 原文：https://zhuanlan.zhihu.com/p/2065205306540531895
