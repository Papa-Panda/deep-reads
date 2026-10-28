# 2026年了，关于大模型kv cache的优化有什么新的方法吗？

> 知乎推荐流首选（登录态核验为账号 971775；回答已经登录浏览器通读）。作者菽陌松囿，2026-10-27 发布，23 赞同、26 收藏；问题 78 人关注、8,994 次浏览、共 8 个回答。这篇不走 token 剪枝的算法路线，而是从系统层盘点 KV Cache 优化的七个新方向：存储介质三层设计与 GDS/GDR 无状态化、3FS 与 Mooncake 两类存储系统、传输侧 prefetch 与 PD 分离的小包打包、链式哈希带来的淘汰依赖、长输入的并行切分、部分前缀匹配的 cache edits、量化加压缩，以及在架构层把单 token 的 KV 做小——据作者称 DeepSeek V4.1 靠 KV 复用与 SWA 回放把 1M 上下文的 KV 压到约 1GB。与今早入清单的 Mooncake 推理实战正好互补。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-250-2026年了-关于大模型kv-cache的优化有什么新的方法吗/

🔗 原文：https://www.zhihu.com/question/2081079592870212699/answer/2098560632811528397
