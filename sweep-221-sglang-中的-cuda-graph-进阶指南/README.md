# SGLang 中的 CUDA Graph 进阶指南

> 知乎推荐流条目（BBuf 发布、SGLang Team 署名，2026-08-17 发表；读时 134 赞同、204 收藏、3 评论。已据登录态通读原文更正——先前版本为未读原文的提纲版）。SGLang 与 Meta 合作把 CUDA Graph 支持重构为 Runner/Backend 解耦：Runner 管捕获形状、静态 buffer 与 padding，Backend 决定怎么成图——Full 整图、Breakable 可断图（BCG）、TC Piecewise 编译切图。核心是 BCG：在捕获期用标记把不兼容算子留在图外 eager 执行、边界张量固定地址、重放时拷入新值，521 行实现编译路线 1771 行的效果，prefill 建图快 3.8–5.2 倍，已成 prefill 默认；prefill 单测（gpt-oss-120b）Full 1.93 倍、BCG 1.70 倍于 eager。显存一节反直觉：捕获到 chunked prefill 上限反而能把激活峰值压到近零、总显存低于无图基线。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-221-sglang-中的-cuda-graph-进阶指南/

🔗 原文：https://zhuanlan.zhihu.com/p/2072995351972397993
