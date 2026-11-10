# 【11-09】agentic 方式合成 / 清洗训练数据 (SFT・mid-training・RL)

> Lei Tian 的每周论文精读：8 篇 11 月新论文，讲如何用 agentic 方式合成、筛选与清洗训练数据，服务 SFT、mid-training 与 RL——主线是把真实交互中的信息变成下一轮可验证的训练信号。值得他看的是它正撞后训练数据主线：Harness-S 用“兄弟 harness”解决 GRPO 有效组不足、Agent-R² 用真实附件与交付级 rubric 做办公 agent 数据、ToolSpace 以可执行工具依赖为合成单元、Axion 拆分“变难”与“真需工具”两条数据流；作者还逐篇标注了实验口径上的坑（均值 vs 最佳值、dev/test 混淆），可直接当本周数据工作的阅读地图。全文已通读。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-320-11-09-agentic-方式合成-清洗训练数据-sft-mid-training-rl/

🔗 原文：https://zhuanlan.zhihu.com/p/2103100374513082636
