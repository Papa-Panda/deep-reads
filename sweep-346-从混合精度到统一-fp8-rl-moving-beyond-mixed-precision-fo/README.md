# 从混合精度到统一 FP8 RL：Moving Beyond Mixed Precision for Stable and Accelerated MoE RL

> 多团队工程报告（InfiXAI、蚂蚁 AQ、SGLang RL、slime，2025-11-19）：把 FP8 推进 MoE 模型 RL 训练，先以对照实验归因 KL Loss 异常来自前向量化误差而非实现 bug，再在 Qwen3-30B-A3B 与 Qwen3-235B-A22B 上验证 FP8 的 TIS clipfrac 更低、训推 logprob 差更窄，且模型越大优势越明显；正撞 RL 训练与量化主线。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-346-从混合精度到统一-fp8-rl-moving-beyond-mixed-precision-fo/

🔗 原文：https://zhuanlan.zhihu.com/p/1974681194017865986
