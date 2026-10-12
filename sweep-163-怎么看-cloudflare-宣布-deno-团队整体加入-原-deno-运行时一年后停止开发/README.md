# 怎么看 Cloudflare 宣布 Deno 团队整体加入，原 Deno 运行时一年后停止开发？

> 知乎热榜条目（约111万热度，23个回答，浏览约6万）。头部回答（71/47/39赞）质量明显高于一般热榜题：先纠正框架——这不是收购 Deno，而是团队整体加入 Cloudflare；Cloudflare 要的不是 Deno 运行时本身，而是团队的 celld 与 rusty_v8，并入 workerd，让 Workers/Durable Objects 编程模型能自托管。处置时间表很具体：Deno 运行时再维护一年（月度 bugfix 与安全更新）后官方停开发、项目开源待社区接手，Deno Deploy 半年后关闭，JSR 继续。分歧点在价值判断：Deno 作为完整 JS 工具链（一体化包管理、打包、检查与格式化）的价值，是否被运行时之争掩盖。对他正对口 runtime 方向：一个运行时项目的终局，往往由宿主平台的执行模型决定（V8 isolate 短命轻量 vs 完整长驻运行时），而不是语言生态的热度。已读默认排序前3答。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-163-怎么看-cloudflare-宣布-deno-团队整体加入-原-deno-运行时一年后停止开发/

🔗 原文：https://www.zhihu.com/question/2092196286669895651
