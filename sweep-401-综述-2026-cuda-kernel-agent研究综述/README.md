# [综述]2026 CUDA Kernel Agent研究综述

> Yazhu（NUS）的长篇综述（11 节、21 篇参考文献，2026-10-06 修订）：系统梳理 CUDA Kernel Agent 全貌——KernelBench 与 fast_p 度量、T0–T6 基线分层、SFT→多轮 RL（Kevin）→对比 RL（CUDA-L1）→Agentic RL（CUDA Agent）训练路线、免训练框架（CudaForge/KernelEvolve/KDA/GEAK），以及 TF32 基线修正、reward hacking 与变异测试揭示的评测可信度问题。核心结论：写出正确 kernel 不等于更快，分数的可信度取决于度量协议。Jun 做 CUDA/GPU 底层与 Agent infra 可直接对照；页面标注含 AI 辅助创作。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-401-综述-2026-cuda-kernel-agent研究综述/

🔗 原文：https://zhuanlan.zhihu.com/p/2090816107342983990
