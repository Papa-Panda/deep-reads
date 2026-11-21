# DeepSeek-V4的并行策略和计算通信遮掩

> 九老师（2026-05-04，502 赞 / 754 收藏）精讲 DeepSeek-V4 论文的并行策略：MoE 的 MFU 塌陷本质是通信 bound 而非专家切太小；16 PP × 64 EP × ZeRO-1 DP 跑在 2048 张 H800 上，DualPipe 挤气泡 + Waved-EP 在单 kernel 内做波次重叠，小批量 RL 场景相对 Comet 加速 1.96×；附 TileLang vs Triton 的取舍与硬件启示。AI Infra 深度长文，值得慢读。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-373-deepseek-v4的并行策略和计算通信遮掩/

🔗 原文：https://zhuanlan.zhihu.com/p/2034669267807888405
