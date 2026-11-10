# VLA 训练如何一步步提速：以 Pi0.5 为例的 3 倍加速实践

> LoongForge 团队把 Pi0.5 SFT 训练做到社区实现 3 倍速的实测复盘：裁空相机槽位、torch.compile 融合、FlexAttention 压激活、选择性重算、无 NVLink 下分层编译隐藏 AllReduce、TorchAO FP8——每一步都有 profile 数据与失败教训，LIBERO 上 bf16 平均 98.75 分反超社区基线。值得他看的是它把 VLA 训练加速拆成一条可复现的工程决策链，正撞他具身智能与训练 Infra 的主线。注意：推荐流里显示的标题是“VLA 领域综述”，但该链接实际内容已是这篇加速实践，入库按实际标题为准。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-322-vla-训练如何一步步提速-以-pi0-5-为例的-3-倍加速实践/

🔗 原文：https://zhuanlan.zhihu.com/p/2095995176691025283
