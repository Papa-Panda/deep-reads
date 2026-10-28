# 910C 超节点推理实践：从 CP Prefill 到 Mooncake

> 知乎推荐流首选（登录态核验为账号 971775；原文已经两份独立全文读数交叉核验，初稿误用的串稿版本已更正）。小红书基模 Infra 团队（作者署名「异构计算教父」）在华为计算与 Mooncake 社区 Meetup 上的实战整理：团队从零行 NPU 推理代码起步，在 CloudMatrix 384 超节点（384 颗 910C）上部署自研 Dots3 Note（280B 总参/16B 激活、DSA+SWA 混合注意力），目标同 SLO 下吞吐达 H800 的四分之一。核心链条：DSA 的逐 query Top-K 让 TP Prefill 失效、改用 CP16（单层算子链实测约 12.2 倍）；KV 随计算分片并做碎片治理（SDMA 带宽约 5.72 倍）；Mooncake Store 跨实例复用前缀；SWA checkpoint 启发式把前缀命中率从 47% 拉到 63%。注意：文中加速比均为算子级口径，非端到端，且未披露最终 TTFT/QPS。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-247-910c-超节点推理实践-从-cp-prefill-到-mooncake/

🔗 原文：https://zhuanlan.zhihu.com/p/2098443602183693903
