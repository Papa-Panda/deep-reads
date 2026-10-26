# vime、slime、AReaL、VeRL在NPU上的性能对比

> 知乎推荐流专栏（作者 kaiyuan，2026-09-29 发布；45 赞同、68 收藏。原文已经二次通读核验更正——本条先前据一份错误读数写入的作者、模型与秒级数据均已作废）。一篇方法交代得很清楚的 RL 框架昇腾实测：因 vime 的 Ascend 分支进入『大部分功能已支持、常见模型能跑』阶段，团队把 vime、slime、AReaL、VeRL 四套框架在 NPU 上同场对比；本轮不追求各自调优上限，只在固定条件下测 Qwen 系列，并立了三条公平规则（只开共同功能交集、各用能跑完的最新稳定版、每个框架由其负责人亲自测）。共用设置以 Megatron 后端 + GRPO 为主，系统性差异主要在 rollout 引擎（slime 用 SGLang，其余用 vLLM-Ascend）。结论：同配置下 vime 多数场景最快，AReaL 与之接近，VeRL 明显慢一档。对他做 RL 训练框架选型与国产算力迁移，是带方法论边界的一手证据。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-238-vime-slime-areal-verl在npu上的性能对比/

🔗 原文：https://zhuanlan.zhihu.com/p/2088579596216226383
