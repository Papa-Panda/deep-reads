# 在 H100 上看见 PDL：让下一个 kernel 提前启动

> 抖音 AI Infra 作者在 H100 上实测 CUDA PDL：RMSNorm→QKV 场景下后继 kernel 提前 152µs 启动，但端到端只快 14.6µs——他拆解了重叠被等待与竞争吃掉的 138µs，并用 3×3 扫掠证明收益成立的充要条件（producer tail 与 consumer prologue 必须双长，最高 47.3%），附 Triton launch_pdl=True 的完整映射与可复现代码。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-392-在-h100-上看见-pdl-让下一个-kernel-提前启动/

🔗 原文：https://zhuanlan.zhihu.com/p/2080422439973041738
