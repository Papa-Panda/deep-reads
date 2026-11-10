# 几百G的DeepSeek，竟然被洋垃圾给跑起来了，速度快的出乎意料！

> ZZ是画渣用 220 元闲鱼主板 + 双路 E5-2698B v3 + 512GB DDR3 + 2 块 V100，实测把 423GB 的 DeepSeek-V4.1-Flash-1017（GGUF）跑起来：Strata 框架做分层推理 + CPU 内存 offload，MoE 专家层在 CPU/GPU 间分工绕开显存墙，单卡约 19 Token/s、双卡最高约 33.5 Token/s，400GB+ IQ3_S 模型仍有约 16.7 Token/s 并验证了 256K 上下文。值得他看的是它是一份可复现的廉价大模型本地部署实操记录，含从个位数 Token/s 优化到 19 的完整提速弧线。注：数字为单次 headline 实测，未注明测量口径（prompt 长度、batch、TTFT/解码），非严谨 benchmark；视频标注含 AI 生成内容；仅读到视频简介与数据，正片未逐段核验。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-321-几百g的deepseek-竟然被洋垃圾给跑起来了-速度快的出乎意料/

🔗 原文：https://www.bilibili.com/video/BV1JvW761ET3
