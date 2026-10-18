# DeepSeek v4.1 RL训练踩坑日记

> 知乎推荐流条目（sallon88，2026-10-13发布，380赞、485收藏）。一线 bring-up 实录：在百度百舸自研 LoongSage 框架（Megatron 训练 + SGLang rollout 共置）里把 DeepSeek V4.1 Flash 的 Agentic RL 跑通——环境 r2e gym + mini-swe-agent、24k response、训推一致性保持在 1e-4 量级。坑几乎全在未文档化的工程细节：权重格式转换要手写、跨机部署撞上两个 DP-attention 隐藏 bug、路由器不感知 DP 让多轮轨迹的 KV cache 大量重算、dummy 快速启动静默丢掉 engram；作者点名最大的瓶颈是主机内存而非显存——R3 专家回放按 960B/token 预留、与 CPU 优化器叠加，把 6 节点 H20（每节点 2T 内存）打到 host OOM，最后靠 chunked offload 把优化器主机峰值从 18N 降到 12N。对他是同构的一手故障账本：Agent RL 训练环路里最先爆掉的往往不是模型，而是主机内存与路由粒度这类账。注：原文未给 RL 算法名与奖励设计。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-200-deepseek-v4-1-rl训练踩坑日记/

🔗 原文：https://zhuanlan.zhihu.com/p/2093494438676927321
