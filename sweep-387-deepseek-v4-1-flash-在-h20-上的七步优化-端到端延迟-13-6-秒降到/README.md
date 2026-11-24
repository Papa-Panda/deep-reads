# DeepSeek-V4.1-Flash 在 H20 上的七步优化：端到端延迟 13.6 秒降到 4.7 秒

> BBuf 解读蚂蚁国际 AI Infra 团队的 LMSYS 博客（2026-11-19）：8 卡 H20-3e + SGLang 上 DeepSeek-V4.1-Flash 的七步优化——prefill CP + decode DP、FP8 DeepGEMM 做 Indexer 打分、可中断 CUDA Graph、MoE EP 改 TP 等，端到端延迟 13.63s→4.70s、吞吐 847→2465 tok/s，GSM8K 精度基本无损（96.42% vs 96.50%）；附每步开关与 SGLang PR，可直接复现。推理优化 + 稀疏注意力 kernel 的实战手记。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-387-deepseek-v4-1-flash-在-h20-上的七步优化-端到端延迟-13-6-秒降到/

🔗 原文：https://zhuanlan.zhihu.com/p/2108248698329229282
