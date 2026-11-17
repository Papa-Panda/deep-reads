# RL修炼第六弹：低精度FP8，FP4 和 Trace

> 大海无量（2026-11-05，RL修炼系列第六弹）把 RL 训练的低精度 rollout 从头讲透：FP8/FP4/MXFP4/NVFP4 的格式与 scale 算法、Hopper 与 Blackwell 的硬件路径、哪些层可量化、QAT 如何让训练看到 rollout 的权重，以及 TRACE 论文如何用 rollout 的码点指导训练侧舍入——联合 FP4 下平均分 75.3，超过 BF16 的 74.9。正撞后训练 RL 与量化主线，22 赞 / 37 收藏。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-354-rl修炼第六弹-低精度fp8-fp4-和-trace/

🔗 原文：https://zhuanlan.zhihu.com/p/2102050054647309505
