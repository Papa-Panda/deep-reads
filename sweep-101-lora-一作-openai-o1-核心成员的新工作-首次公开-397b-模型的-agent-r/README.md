# LoRA 一作、OpenAI o1 核心成员的新工作：首次公开 397B 模型的 Agent RL 训练配方

> LoRA 一作、OpenAI o1 核心成员 Edward Hu 加入 Mercor 后与 SkyRL 团队联合发布：Qwen3.5-397B-A17B 在 APEX-Agents（480 个长程知识工作任务）上 Pass@1 从 16.11% 提到 27.29%。最震撼的结论是只修 Harness（PDF 解析、工具返回 None、沙箱超时）就让未训练模型平均奖励从 22.74% 升到 28.69%，涨幅相当于一个 epoch 的训练。公开 TITO token 对齐、Fully Async RL 的 KV Cache 并发上限、Prompt Mean+DPPO+Context Nudge 组合等工程细节。正中他 Agentic RL Infra 主线。（未读到原文细节：大纲按浏览器任务通读摘要重构）

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-101-lora-一作-openai-o1-核心成员的新工作-首次公开-397b-模型的-agent-r/

🔗 原文：https://zhuanlan.zhihu.com/p/2082860762947703480
