# 从 16 卡到 512 卡：训练的吞吐优化

> 知乎推荐流专栏（作者 a'晨，编辑于 2026-10-12 上海；读时 20 赞同、37 收藏、0 评论。已通读原文的更正版——本轮早先因通读报告迟到曾以未读原文兜底写入）。文章基于 Aleph Alpha 的 scaling 实践报告、用 torchtitan 在 B200 上拆 30B-A3B MoE 的训练吞吐：16 卡 FSDP=16 时 28.4k tok/s/卡、MFU 37.5%；128 卡 28.0k、37.0%；512 卡改用 FSDP=128×外层 DP=4 的 HSDP 后 26.7k、35.3%——卡数 ×32、总吞吐 ×30.1，单卡保留约 94%，按此速率 20T tokens 约 17 天。关键手法是 selective recompute 与 LBS 的联合 sweep、通信与计算重叠、以及把跨副本 all_reduce 推迟到最后一个 microstep 的 backward 才做。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-231-从-16-卡到-512-卡-训练的吞吐优化/

🔗 原文：https://zhuanlan.zhihu.com/p/2092999317804130662
