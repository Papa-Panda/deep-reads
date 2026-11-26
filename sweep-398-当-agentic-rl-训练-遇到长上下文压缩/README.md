# 当 Agentic RL 训练，遇到长上下文压缩

> 喔喔喔（2026-11-22）从 RL 前缀一致性出发，讲清 Agentic RL 长轨迹触发上下文压缩后为何不能再把整条轨迹拼成一个训练样本：按压缩边界切分、优势广播到各段、摘要生成本身也要进 loss（CompactionRL 实测 +2.3pp），并给出 Gateway 采集轨迹树的工程实现。Agent RL 训练与上下文压缩的硬核工程拆解。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-398-当-agentic-rl-训练-遇到长上下文压缩/

🔗 原文：https://zhuanlan.zhihu.com/p/2107938229118842397
