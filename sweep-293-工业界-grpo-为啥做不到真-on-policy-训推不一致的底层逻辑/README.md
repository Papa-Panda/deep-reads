# 工业界 GRPO 为啥做不到真 on-policy？—— 训推不一致的底层逻辑

> 讲工业界 GRPO 做不到真正 on-policy 的原因：训练引擎与推理引擎即使权重相同也会算出不同的 logprob，MoE 路由放大了这种训推不一致，并给出 FP16、路由回放、GSPO 与一系列工程补丁等解法。值得他看的是它直击后训练 RL 的一个真实落地痛点——不是调参问题，而是 on-policy 假设本身在双引擎架构下就不成立。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-293-工业界-grpo-为啥做不到真-on-policy-训推不一致的底层逻辑/

🔗 原文：https://zhuanlan.zhihu.com/p/2024520001596454677
