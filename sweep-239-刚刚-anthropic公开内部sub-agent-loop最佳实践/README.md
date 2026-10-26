# 刚刚，Anthropic公开内部Sub-Agent+Loop最佳实践

> 知乎推荐流专栏（作者 PaperAgent，2026-10-25 发布，专栏「Agent」；已由登录浏览器读到开头与章节结构）。转述 Anthropic 官方 Agent 工程实践的一个反直觉结论：Sub-Agent 不是越多越好——企业落地中「一个主 Agent Loop + 渐进披露的 skills 与工具」在质量上同时胜过单体大 prompt 与多 Sub-Agent 编排，单 Loop 在一处对比中还快约 2 倍。文章拆了上下文交接损失、Sub-Agent 蔓延、渐进披露与评测先行的迁移路径，正对他 Agent infra/harness 的主线。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-239-刚刚-anthropic公开内部sub-agent-loop最佳实践/

🔗 原文：https://zhuanlan.zhihu.com/p/2097745558991590963
