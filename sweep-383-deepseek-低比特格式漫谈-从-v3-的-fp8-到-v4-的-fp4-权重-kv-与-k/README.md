# DeepSeek 低比特格式漫谈：从 V3 的 FP8 到 V4 的 FP4，权重、KV 与 kernel

> 刘景初（清华博士）沿 DeepSeek V3→V4.1-Flash 的技术报告精讲低比特格式：FP8 训练如何用细粒度 scale 与 DeepGEMM 啃下 671B 模型、KV 怎样从 MLA 压到 FP8 再进 FP4、以及为什么权重与 KV 在 4bit 时走了不同的格式路线。量化、KV Cache 与 kernel 三线合一的硬核长文，直接对口推理优化与 GPU 底层，值得慢读。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-383-deepseek-低比特格式漫谈-从-v3-的-fp8-到-v4-的-fp4-权重-kv-与-k/

🔗 原文：https://zhuanlan.zhihu.com/p/2094539296342656554
