# 关于分离架构的一点碎碎念——从 Prefill/Decode 分离到 Attention/FFN 分离，重新理解大模型推理的性能

> 美团 mlsys 实习生 QIU Chengyu（2026-11-20，19 赞）从一年分离式推理实践出发：MFU、利用率、峰值吞吐都是局部指标，真正该比的是同预算同 SLO 下的整机可服务吞吐；P/D 分离与 AFD 分离的收益要扣掉「承载能力税」与通信等待——Qwen3-235B 仿真里 FFN 局部 MFU 涨 3 倍，整机吞吐反而只剩 70.7%。推理优化的一线实测与度量框架，值得慢读。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-375-关于分离架构的一点碎碎念-从-prefill-decode-分离到-attention-ffn/

🔗 原文：https://zhuanlan.zhihu.com/p/2107188712182395488
