# 强化学习算法：从 PPO 到 GRPO 的演化史

> 从两条轴讲清 PPO 到 GRPO 的演化：优势估计怎么算、策略能走多远。核心论点是 GRPO 只改了优势估计（组内基线替代 Critic），没改 PPO 的裁剪目标；随后用 Dr. GRPO、DAPO、GSPO 三个 2025 补丁讲清组内归一化的长度/难度偏差、熵坍塌与 token 级比率方差问题。值得他看的是它把后训练 RL 配方的关键取舍拆成了可对照的机制与公式，并明确划了适用边界：这套路子在 LLM 上成立，在游戏/控制任务里不成立。注：知乎直取 403，内容据浏览器通读整理，概括转述。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-279-强化学习算法-从-ppo-到-grpo-的演化史/

🔗 原文：https://zhuanlan.zhihu.com/p/2098863328114238908
