# Weight Resharding in RL System

> NVIDIA 上海工程师讲 RL 系统里训练权重同步到推理侧的 resharding：训练（FSDP/TP/PP/EP）与推理并行布局不同，同步不是拷贝而是按元素重分片；按“全量张量在哪物化×发送方是否预筛”两轴比较各方案（NCCL vs NIXL、verl 路径），结论是按参数混用多条路径。值得他看的是它正撞 RL 训练 Infra 主线，把权重同步的通信量、临时显存、工程复杂度都算清楚了。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-326-weight-resharding-in-rl-system/

🔗 原文：https://zhuanlan.zhihu.com/p/2096895081047446225
