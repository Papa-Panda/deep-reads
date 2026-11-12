# 面向 SGLang 的 Profile Analysis SKILL: 3 张表定位 Kernel Fuse 和 Overlap 机会

> BBuf 做的 SGLang Profile Analysis SKILL：把 torch profiler 的 trace 归纳成 kernel 表、overlap 机会表、fuse 模式表三张表，定位新模型在 SGLang 上的 kernel 融合与重叠优化点；Qwen3.5-4B 与 gpt-oss-20b 的 H100 实测演示，外加 H100/H200/B200 上 Torch Compile 的跷跷板对比。值得他看的是它把“新模型冷启动性能分析”做成可复用的 agent 工作流，正撞推理优化与 SGLang 内核主线，且附开源 SKILL 可直接用。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-332-面向-sglang-的-profile-analysis-skill-3-张表定位-kernel/

🔗 原文：https://zhuanlan.zhihu.com/p/2025648183569655286
