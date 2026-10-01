# 一文读懂KVCache

> 2024 年经典硬核长文（1861 赞、3629 收藏）：从 GPT2 实测讲起——新增 token 时历史 embedding 变化仅 1e-5，这是 KV Cache 的实验依据；对比三种缓存方案的存储与计算开销，给出 PagedAttention 的工程实现，并点出成立条件是因果性（decoder-only 才可用）。评论区有作者亲承的算术勘误和 KV Cache 本质是变长 RNN state 的点睛，推理优化基本功，配 vLLM 源码看最对味。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-113-一文读懂kvcache/

🔗 原文：https://zhuanlan.zhihu.com/p/686183300
