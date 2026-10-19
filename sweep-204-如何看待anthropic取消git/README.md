# 如何看待anthropic取消git？

> 知乎推荐流条目（21 个回答、约 19.7 万浏览）。所谓「取消 git」是 Anthropic 把自家 monorepo 从 Git 迁到自研的 Scion：AI Agent 把日合并量四个月内从约 2500 推到 3 万以上、主干历史涨到约 100GB、CI 每天约 2500 万次 checkout，Git 的分布式离线设计成了瓶颈。实质内容集中在第 5 高赞的 Kevin 回答（34 赞，唯一引用 Anthropic 官方博文《Redesigning source control at Anthropic》）：Scion 仿 Google Piper 与 Meta Sapling，服务端承担历史与合并、数据存 Spanner 与对象存储、无 packfile、分层缓存命中率 99% 以上，号称比 Git 镜像系统省 200 倍 CPU/内存、CI 省下 25% 算力。高赞前四条多是质疑与玩笑，需跳读。对他的价值在 Agent 时代的开发基础设施：当客户端几乎全是常在线的 Agent 时，基础设施要按 Agent 的规模重做——这正是 harness/infra 线的一手案例。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-204-如何看待anthropic取消git/

🔗 原文：https://www.zhihu.com/question/2094352602074965020
