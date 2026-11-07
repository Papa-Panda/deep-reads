# 论文解读：AI 就是编译器——让 LLM 直接写 PTX，绕开整个编译器后端

> 讲论文 "AI as a Compiler"：LLM Agent（TAIC）直接把 Triton 内核翻译成 PTX，绕开整个编译器后端，在 L40S/H100/B200 上相对自调优 Triton 做到 0.83x–3.34x，FlashAttention 1.37x、BitDelta 3.34x；作者还用无 GPU 的 SASS 级复现验证了 wgmma n=64→256 等关键机制，并指出验证才是真正的瓶颈。值得他看的是它把 Agent infra、编译器后端与 GPU 指令级优化连成一条线，且批判性评估很克制——收益只集中在能重组计算与数据搬运的算子上。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-304-论文解读-ai-就是编译器-让-llm-直接写-ptx-绕开整个编译器后端/

🔗 原文：https://zhuanlan.zhihu.com/p/2089495666494011238
