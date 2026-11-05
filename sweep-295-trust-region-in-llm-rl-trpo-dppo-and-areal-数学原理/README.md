# Trust Region in LLM RL: TRPO, DPPO and AReaL 数学原理

> 从性能差引理出发，推导 LLM 有限时域下的信任域界，并对照 TRPO、PPO、DPPO 与 AReaL 在信任域中心、距离定义与约束方式上的差别：为什么单 token 比率是失真的代理、完整分布散度与异步解耦各解决什么问题。值得他看的是它直击后训练 RL 的核心数学——长 CoT 下耦合误差如何累积、异步训练中新鲜度与漂移须联合监控。注：该文为理论综合学习笔记（标注 AI 辅助创作，发表时仅 6 赞 9 收藏），无新实验，宜对照引用的 TRPO/DPPO/AReaL 原文核验。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-295-trust-region-in-llm-rl-trpo-dppo-and-areal-数学原理/

🔗 原文：https://zhuanlan.zhihu.com/p/2101270035574552548
