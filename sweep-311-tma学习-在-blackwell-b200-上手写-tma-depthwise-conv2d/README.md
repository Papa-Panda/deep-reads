# TMA学习：在 Blackwell B200 上手写 TMA Depthwise Conv2D

> 在 B200 上手写 TMA Depthwise Conv2D 的实战记录：从 naive 实现的性能下限，到共享内存复用、TMA 异步搬运、producer/consumer 流水线与 n_stage 取舍，实测 n_stage=2 追平 cuDNN、n_stage=4 反而更慢。值得他看的是它把 TMA 从概念讲到可跑的代码与实测曲线，且对 n_stage=4 变慢的第二点原因明确标为未验证的推测，正对 CUDA/GPU 底层主线。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-311-tma学习-在-blackwell-b200-上手写-tma-depthwise-conv2d/

🔗 原文：https://zhuanlan.zhihu.com/p/2035478413146838335
