# SIMT 真的比 SIMD 更好编程吗？从 DeepSeek 量化算子到 Element-wise for/if

> 以 DeepSeek TileKernels 量化算子为试验场，在 Ascend 950 上实测对比 SIMD 与 SIMT：连续规约与简单位运算两者接近，Transpose/Gather/二维规约 SIMT 更自然；FP4 纯 SIMT 软模拟慢约 90 倍、只把最后 Cast 移回 SIMD 则差距缩到 1.26 倍；PTO 虚拟指令集把 MXFP8→BF16 反量化从 144μs 降到 113μs。值得他看的是它把“SIMD 难写”拆成执行模型与接口层次两个问题，并给出 Element-wise for/if + PTO + 超标量 NPU 的完整路线图，正对量化与 GPU/NPU 底层主线。注：文中两张图表为图片，未逐数核验。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-314-simt-真的比-simd-更好编程吗-从-deepseek-量化算子到-element-wis/

🔗 原文：https://zhuanlan.zhihu.com/p/2098368540835430430
