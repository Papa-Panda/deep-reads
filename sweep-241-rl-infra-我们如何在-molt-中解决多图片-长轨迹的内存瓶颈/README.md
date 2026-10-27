# RL Infra: 我们如何在 Molt 中解决多图片、长轨迹的内存瓶颈

> 知乎推荐流专栏（作者 初七9527，编辑于 2026-09-02；74 赞同、75 收藏。已由登录浏览器通读原文更正——本条先前据未读原文兜底写入）。一篇定位极准的 RL Infra 实战：OSWorld rollout 的 batch 从 128 提到 1024 时，GPU 还没吃饱，controller 的 CPU 内存先爆——根因不在 batch 本身，而在数据通路：所有轨迹都经 controller 中转，使只该做调度的它变成全集群的图片仓库。Molt v0.1.3 的解法是给 Experience 加 offload/reload：重字段（图片、多模态输入、attention mask、log_probs 等）在生产端经 Ray 对象存储卸载、只留 heavy_ref，controller 只收轻字段（reward、轨迹长度、group id）做过滤与调度，训练 rank 真正计算时再按引用取回。对他做 Agent RL / 长轨迹训练的人，这条『瓶颈常在数据通路、不在模型』的判断值得记。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-241-rl-infra-我们如何在-molt-中解决多图片-长轨迹的内存瓶颈/

🔗 原文：https://zhuanlan.zhihu.com/p/2078810043420504749
