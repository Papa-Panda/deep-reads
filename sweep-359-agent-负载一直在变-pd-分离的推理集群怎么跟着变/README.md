# Agent 负载一直在变，PD 分离的推理集群怎么跟着变

> momo（2026-11-17）解读 Georgia Tech 等的论文《Evolving Infra: Agent-Adaptive LLM Serving at Scale》：Agent 负载下最优 PD 配比随任务类型与负载混合漂移，固定配比最多损失 24% 吞吐；Evolving Infra 用免重启换角色、按活跃分支引用计数的 KV 驱逐与在线拟合的延迟模型，在 36 张 GB300 上相对 NVIDIA Dynamo 达到 1.10–2.73 倍吞吐。正撞 Agent infra 与推理优化主线。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-359-agent-负载一直在变-pd-分离的推理集群怎么跟着变/

🔗 原文：https://zhuanlan.zhihu.com/p/2106204450557903675
