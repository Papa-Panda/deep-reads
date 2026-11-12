# 字节OneTrans-GSR：一场本末倒置的执念

> 石塔西（清华博士、《互联网大厂推荐算法实战》作者）拆解字节 2026 年 11 月的 OneTrans-GSR 论文：用一个自回归 Transformer 一次生成整页推荐 slate（6–10 条），走预训练 + 会话级奖励模型 + GRPO 三段式；核心批评是预训练目标本末倒置——只学“好会话”会让模型模仿其中未被点击的条目、浪费曝光位，RL 只能锦上添花、修不好地基。值得他看的是它把生成式推荐的训练目标、GRPO 落地与 Meta HSTU 的对照讲透了，正撞 RL 配方与推荐系统主线。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-334-字节onetrans-gsr-一场本末倒置的执念/

🔗 原文：https://zhuanlan.zhihu.com/p/2104138586929026717
