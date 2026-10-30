# RL修炼第五弹：训推一致性

> 知乎推荐流专栏，RL 训练系列第五弹，讲训推一致性：RL 里 rollout 策略与 PPO 近端策略理论上应是同一权重下的同一分布，逐 token 概率应当对齐，缺口称为训推失配（TIM）——它不同于多 mini-batch 或异步更新带来的策略陈旧。值得他看的是这条把“同权重却算出不同概率”拆解到底层的分析：即使权重相同，vLLM/SGLang 这类推理引擎与 Megatron/FSDP 这类训练引擎也可能给出不同结果，大到一定程度会让名义上的 on-policy 训练实际变成无修正的 off-policy，危及训练稳定。注：本条大纲已据浏览器通读报告修正，此前“未读到原文细节”的标注作废。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-262-rl修炼第五弹-训推一致性/

🔗 原文：https://zhuanlan.zhihu.com/p/2099184384259760228
