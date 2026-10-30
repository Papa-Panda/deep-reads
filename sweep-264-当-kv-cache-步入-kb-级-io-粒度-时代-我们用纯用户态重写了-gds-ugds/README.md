# 当 KV Cache 步入 KB 级 IO 粒度 时代，我们用纯用户态重写了 GDS：uGDS 开源，吞吐提升 2.63 倍

> 讲推理瓶颈如何从算力转向 KV Cache 在存储层之间的搬运：单 token KV 已缩到 KB 级，历史缓存值得放进 NVMe，但现有 GPU 到 SSD 路径对细粒度访问不友好。作者给出纯用户态方案 uGDS，并附 arXiv 报告与开源链接。值得他看的是这条与推理缓存、LMCache 落地直接相关的存储层分析；注意 2.63 倍是异步/批量、计算掩盖传输场景下的峰值，并非所有传输都快这么多。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-264-当-kv-cache-步入-kb-级-io-粒度-时代-我们用纯用户态重写了-gds-ugds/

🔗 原文：https://zhuanlan.zhihu.com/p/2097033202187637385
