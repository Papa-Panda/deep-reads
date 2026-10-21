# 一篇就够系列：OPD（白盒蒸馏／黑盒蒸馏／自蒸馏），一篇就够了

> 知乎推荐流条目（周星星，2026-10-20 发布，原文已通读）。一篇 OPD（在策略蒸馏）全景综述：广义定义是学生先用自身策略生成、再由教师信号更新，并按信号来源分三章——白盒（教师逐 token 概率，reverse KL 推导、token 级近似的偏差、MiniLLM/GKD 取舍，及 MiMo 多教师合版、DeepSeek-V4、Qwen3 工业实践；Qwen3 同起点下 OPD 以 1,800 额外 GPU 时对 RL 的 17,920、约 1/10 成本反超分数）、自蒸馏（同模型多看特权上下文：OPSD/SDPO/Cursor/OPCD/OEL/RLSD）、黑盒（GAD 判别器与 Rubric 量规把教师文本变成奖励再 GRPO）；末章讲边界：强教师教不好学生的三类失效与单题泛化（单题轨迹覆盖全数据 71.5% 状态簇）。正对他后训练数据/蒸馏主线，是本轮深度最高的一条。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-214-一篇就够系列-opd-白盒蒸馏-黑盒蒸馏-自蒸馏-一篇就够了/

🔗 原文：https://zhuanlan.zhihu.com/p/2095992561735315694
