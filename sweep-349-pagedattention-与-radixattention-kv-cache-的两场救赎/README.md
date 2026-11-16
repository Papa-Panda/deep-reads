# PagedAttention 与 RadixAttention：KV Cache 的两场救赎

> Arthur（芯片公司 AI Infra 工程师）把 PagedAttention 与 RadixAttention 两篇奠基工作放进同一框架讲透：前者借操作系统分页思想解决 KV 显存碎片化（利用率 20%→约 99%，吞吐 2–4×），后者用基数树复用历史前缀、省掉重复 prefill（多调用任务最高 6.4×）；附 V1–V4 纯 Python 模拟器实测数据与 vLLM / SGLang 源码学习路径，正撞推理优化主线，适合当作推理引擎的案头手册。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-349-pagedattention-与-radixattention-kv-cache-的两场救赎/

🔗 原文：https://zhuanlan.zhihu.com/p/2077530713042187116
