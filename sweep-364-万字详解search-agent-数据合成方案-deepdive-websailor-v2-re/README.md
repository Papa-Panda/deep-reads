# 万字详解Search Agent 数据合成方案（DeepDive、WebSailor-V2、REDSearcher）

> 余培杰（腾讯混元，2026-02-20，113 赞 / 213 收藏）万字拆解三套 Search Agent 数据合成方案：共用“建图 → 随机游走取子图 → 生成 QA”三步；DeepDive 开源代码逐行讲透（出度过滤 + LLM 选下一跳 + 四测难度过滤）；WebSailor-V2 用 Weisfeiler-Leman 保证子图非同构多样性与三招混淆法；REDSearcher 再加树宽 / 信息分散度与五步 Verifier Pipeline；BrowseComp 15.3 → 35.3 → 42.1，上下文管理再推到 57.4。正撞 Agent 数据合成与后训练主线。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-364-万字详解search-agent-数据合成方案-deepdive-websailor-v2-re/

🔗 原文：https://zhuanlan.zhihu.com/p/2007944059558323475
