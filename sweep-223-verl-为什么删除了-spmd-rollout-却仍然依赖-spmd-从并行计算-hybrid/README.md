# veRL 为什么删除了 SPMD Rollout，却仍然依赖 SPMD？——从并行计算、HybridFlow、Ray WorkerGroup，到Server Mode 的技术思想史

> 知乎推荐流条目（万理的探求者，发布于 2026-10-15，专栏「AI技术思想史」；读时 9 赞同、21 收藏、0 评论；已通读原文，更正版——先前版本作者与数据有误）。一篇 16 部分、58 节的 veRL 架构思想史：起点是 v0.7.0 的一处表面矛盾——release notes 删掉 SPMD Rollout，架构文档却说 Model Engine 仍以 SPMD 运行。文章从 SPMD 的历史与 rank/集合通信讲起，经 HybridFlow 的双层数据流、WorkerGroup 如何把 SPMD 藏进 Worker 抽象，再到多轮 Agent 的长尾如何冲击旧 Rollout、Server Mode 如何按请求调度，并专门辟一节摆四个反例（单轮大 batch 未必受益、Server Mode 不自动消除 GPU 空闲等）。结论：SPMD 没有被淘汰，只是被放回适合它的位置。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-223-verl-为什么删除了-spmd-rollout-却仍然依赖-spmd-从并行计算-hybrid/

🔗 原文：https://zhuanlan.zhihu.com/p/2094203587006051708
