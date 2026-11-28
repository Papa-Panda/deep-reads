# 精读打卡 001：Score Centering 为什么不够

> serein（2026-11-20）精读 arXiv:2609.20807《Score Centering Stabilizes Off-policy RL》：讲清异步 RL 里训推不一致如何产生 Drift（策略梯度被采样分布系统性带偏），Score Centering 怎样用公式消掉它、为什么仍不够（Reweighting Error 需 Importance Sampling 补），以及何时 SC 已足够（看 KL 距离、批量与陈旧度）。短而密的后训练 RL 实操精读，直接对上 Jun 的异步 RL 工作。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-408-精读打卡-001-score-centering-为什么不够/

🔗 原文：https://zhuanlan.zhihu.com/p/2107498238744052551
