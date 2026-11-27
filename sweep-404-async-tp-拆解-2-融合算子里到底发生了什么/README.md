# Async TP 拆解（2）：融合算子里到底发生了什么

> Mxandre（2026-11-11）逐行拆解 PyTorch 的 fused_all_gather_matmul / fused_matmul_reduce_scatter：不写新 GEMM 核，只靠 stream、对称内存、barrier 与 channel 四件套重排 aten.mm 与拷贝，让通信与计算重叠；单卡模拟 1.33–1.48×，并坦言稳定性取舍与未覆盖的真实多卡验证。通信-计算重叠的硬核实战拆解。注：知乎页为摘要，全文在作者博客。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-404-async-tp-拆解-2-融合算子里到底发生了什么/

🔗 原文：https://zhuanlan.zhihu.com/p/2104022003141427822
