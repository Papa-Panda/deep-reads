# 为什么 veRL 不到两年就几乎重构了整套大模型强化学习系统？——从 HybridFlow、GRPO、AgentLoop、异步 RL、Model Engine 到 OPD的技术思想史

> 知乎收藏条目（万理的探求者，2026-10-14发布，188赞、265收藏，《AI技术思想史》专栏）。按版本逐段拆 veRL 两年内的多次重构：从 HybridFlow 解耦 PPO 逻辑与执行、GRPO 去掉 Critic，到 AgentLoop 把生成变成独立的 Agent 会话、Model Engine 统一后端，再到全异步数据流与 On-Policy Distillation 进入主架构。作者的收束判断是：veRL 已从一个 PPO 实现变成后训练的数据流基础设施。对他是主线中的主线——RL 训练框架演进、异步 RL 的陈旧度控制、OPD 配方，全是他后训练方向的一手技术史。注：已通读全文版本线要点。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-196-为什么-verl-不到两年就几乎重构了整套大模型强化学习系统-从-hybridflow-grpo/

🔗 原文：https://zhuanlan.zhihu.com/p/2093791385761626099
