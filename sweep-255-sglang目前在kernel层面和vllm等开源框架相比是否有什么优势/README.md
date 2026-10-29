# SGLang目前在kernel层面和vLLm等开源框架相比是否有什么优势?

> 知乎推荐流回答（已登录浏览器通读核验：作者刘景初，清华大学信息与通信工程博士，2026-10-27 发布，11 赞同、9 收藏；页面标注含 AI 辅助创作）。借 DeepSeek V4.1 这一轮检验一个判断：开源推理框架的 kernel 终将趋同，但趋同只发生在有官方 kernel 覆盖的平台上——SM100 上 SGLang 与 vLLM 用的是同一批 DeepSeek 开源 kernel，差距只剩融合细节且收益很小；而在官方不覆盖的 Hopper、SM120 这类平台上，谁先补上算子谁就更快，差距可以拉到数倍。值得做推理框架选型的人看：它把“框架之争”还原成了“平台覆盖 + 补丁速度”之争。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-255-sglang目前在kernel层面和vllm等开源框架相比是否有什么优势/

🔗 原文：https://www.zhihu.com/question/1903024030996472309/answer/2098734831022641302
