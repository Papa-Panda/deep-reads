# 【推理优化】投机解码基础详解

> Twinkle（2026-11-17）把投机解码从头讲透：解码慢在访存而非算力（单 token 算力利用率不到 1%），小模型猜 k 个候选、大模型一次前向并行验证，按 min(1, p/q) 投机采样接受、拒则按 norm(max(0, p−q)) 重采样，全接受再得一个 bonus token；无损证明、EAGLE 3.1x 实测、k 取 3–8 与 α 熔断线都给了具体数字。正撞推理优化与 KV Cache 主线。注：文中部分公式为图片，未逐字读到。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-362-推理优化-投机解码基础详解/

🔗 原文：https://zhuanlan.zhihu.com/p/2106135297721360438
