# 从 Harness 自我改进到模型权重更新：一次 SIA 复现实践

> Johnson7788（2026-11-18）复现 SIA 论文（arXiv:2605.27276）：Harness 自我改进 + 权重更新双循环，Qwen3-8B + deepseek-v4-pro 在 GPQA 上实测；Harness Gen 2 改动反而退化、权重单更新不稳定、两者结合在 40 题上 62.5%→80% 但 p=0.1213 未达显著——罕见诚实的复现日记，LoRA 参数、失败分析与工程踩坑全给齐了。Agent harness 与自蒸馏实战，值得慢读。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-368-从-harness-自我改进到模型权重更新-一次-sia-复现实践/

🔗 原文：https://zhuanlan.zhihu.com/p/2106737988910819302
