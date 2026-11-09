# AI Infra 软核教程（一）为什么我们需要 AI Infra

> 锦恢为入行 Agentic RL 而写的 AI Infra 原理向开篇：从 2T 参数模型、FP16 权重 4TB、单卡 B200 仅 180GB 的显存账出发，论证 Infra 的价值不在 GPU 数量而在调度效率；系统梳理训练/推理/数据/集群/Agent 五大板块与 slime、dressage、verl 等 RL 训练框架及 Sandbox 等 Agent Infra 组件，并预告后续 DP/PP/SP/CP/EP 与推理中台章节。值得他看的是它把 Infra 还原为“让成百上千张卡像一台机器”的系统问题，且直接对准 Agentic RL 的 infra 需求；本篇偏原理、无代码与实测。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-318-ai-infra-软核教程-一-为什么我们需要-ai-infra/

🔗 原文：https://zhuanlan.zhihu.com/p/2063938554061967779
