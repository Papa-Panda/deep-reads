# RL算法同学如何自己做训推diff对齐

> 知乎推荐流条目（haotian，编辑于 2026-10-20，35 赞、56 收藏；原文已通读）。作者把 RL 训推 diff 在 Qwen3.5-4B 的 GDN 层上做到了逐位为零：根因是训练侧 chunk 并行内核把 fp32 状态截断成 bf16、而 SGLang 递归 decode 全程 fp32，原生两路逐位一致仅约 38–41%。解法 ISO 是两遍计算——先并行算 64-token 边界的 fp32 状态、再在 chunk 内逐 token 递归——且训练与 rollout 三条路径共用同一套内核；纯 GRPO 实跑 146 步 diff 与 KL 全程为 0，代价是 decode 慢 5.5%、训练前向 +21%，且仅在 4B 单轮上验证、MoE 未做。对他是后训练正确性的一手实作：logprob 对齐可以不靠容差和重要性校正，而靠构造。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-213-rl算法同学如何自己做训推diff对齐/

🔗 原文：https://zhuanlan.zhihu.com/p/2095863677282996988
