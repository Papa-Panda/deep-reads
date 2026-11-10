# 投机采样 ReaDy 论文：给 DSpark 增加循环状态读取，为什么还能提速？

> willow 图解 ReaDy 论文（arXiv:2610.20503v2）：给 DSpark 草稿模型加一个只读 StateReader，让它直接读混合线性注意力目标模型已维护的循环状态，草稿候选更准、解码提速约 8%——单 B200 上 7 任务平均 302.78 tok/s，对原 DSpark +7.97%。值得他看的是它把“多一次读取为何反而更快”讲透了，且作者诚实区分了两种口径：对无状态微调对照仅 +5.68%，并注明自己未做 GPU 复现。注：文章标注含 AI 辅助创作。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-325-投机采样-ready-论文-给-dspark-增加循环状态读取-为什么还能提速/

🔗 原文：https://zhuanlan.zhihu.com/p/2096273850812068237
