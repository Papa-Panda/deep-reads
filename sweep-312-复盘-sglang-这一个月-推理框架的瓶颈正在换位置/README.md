# 复盘 SGLang 这一个月：推理框架的瓶颈正在换位置

> SGLang 42 天（2026-09-15—10-26）2693 次提交的逐 PR 复盘：缓存统一寻址、PD 状态控制面、投机解码正确性、NVFP4 容量 trade-off，结论是推理框架的瓶颈正在从单点加速换到状态正确性与按负载选策略。值得他看的是它把推理 infra 从 benchmark 数字还原为可复现、可组合的机制与代价，且对每项收益的适用边界都做了标注，正对推理优化主线。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-312-复盘-sglang-这一个月-推理框架的瓶颈正在换位置/

🔗 原文：https://zhuanlan.zhihu.com/p/2098076331066012706
