# Meta FAIR 把 Transformer 循环了 32 次：循环哪里、要不要分化、能不能并行

> momo 全文解读 Meta FAIR 2026-10 论文《How to Loop Your Transformer》（arXiv:2610.40325）：同一组权重反复跑最多 32 次，不加参数就能加深模型；全栈循环在固定参数预算下质量最强、中段循环在训练算力受限时更划算、每轮加小 LoRA 适配器轮数越多越有用、并行循环要靠“保留当前 token embedding + 分别归一化 + 门控混合”才能保住质量。值得他看的是它把“深度换参数还是换算力”这笔账算清楚了，且数字都给到了可复核的程度（100M 上 BPB 1.115→1.075→L=32 回升超 1.2；1B 上移位 PLT 0.877 胜全栈 0.883），正撞他模型架构与推理效率的主线。全文已通读。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-329-meta-fair-把-transformer-循环了-32-次-循环哪里-要不要分化-能不能并/

🔗 原文：https://zhuanlan.zhihu.com/p/2101136130968139533
