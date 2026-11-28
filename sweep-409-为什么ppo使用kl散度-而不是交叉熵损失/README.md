# 为什么PPO使用KL散度，而不是交叉熵损失？

> 白露未晞me（2026-11-27）讲清 PPO 里 KL 与交叉熵的分工：SFT 的交叉熵是“方向盘”，RLHF 的 KL 是“刹车”——推导了两者等价性、算了一个 KL≈0.104 的数值例子，并讲了 PPO-Penalty 自适应系数与采样估计 KL 的工程细节。后训练 RL 的第一性原理小品，直接对上他的 RLHF 日常。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-409-为什么ppo使用kl散度-而不是交叉熵损失/

🔗 原文：https://www.zhihu.com/question/2004944038659387885/answer/2109791784373064748
