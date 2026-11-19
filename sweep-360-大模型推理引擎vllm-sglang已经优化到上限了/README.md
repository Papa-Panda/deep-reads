# 大模型推理引擎vllm、sglang已经优化到上限了？

> 不归牛顿管的熊猫（2026-11-17）论证：固定模型、硬件与负载时推理引擎确有上限（8B BF16 在 H100 上约 200 tokens/s），但注意力压缩、MoE、Agent 长上下文、硬件换代与优化目标迁移不断把上限往前推；附 DeepSeek V4 CSA/HCA、Kimi K3.1 KDA 与 SGLang HiCache 的具体数字。正撞推理优化与 KV Cache 主线。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-360-大模型推理引擎vllm-sglang已经优化到上限了/

🔗 原文：https://zhuanlan.zhihu.com/p/2106108436127785288
