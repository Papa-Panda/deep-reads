# Pi-Agent源码解析四_上下文压缩Compaction

> 以 pi v0.83.0 源码为据，讲 Agent harness 的上下文压缩 Compaction：何时触发、如何把当前路径切成三段、摘要如何生成、又如何只追加一条 compaction 节点回填 Session 树。值得他看的是它把长会话上下文管理拆成触发、切点合法性、分段 turn 处理与滚动摘要四个可复用的机制，正对 Agent infra/harness 这一优先方向。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-291-pi-agent源码解析四-上下文压缩compaction/

🔗 原文：https://zhuanlan.zhihu.com/p/2091244664074528318
