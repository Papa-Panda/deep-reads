# 从 verl 与 slime 最近两个月的更新，看 RL 基础设施的演进，以及 DeepSeek V4.1 Flash 的支持现状

> 讲 verl 与 slime 近两个月更新的对照复盘：两大 RL 框架正收敛为“连续流训练系统”——异步调度、版本窗口、量化/路由一致性、token 级轨迹语义、权重快速切换与跨故障恢复成为标准组件；并分层核查了 DeepSeek V4.1 Flash 的支持现状，指出推理已支持但主线尚无稳定可验证的完整 RL 训练方案。值得他看的是它把 RL infra 的演进从功能清单还原为“控住偏差/故障成本与有效策略更新”的系统设计问题，且对 Miles 分叉报告的未核实点做了明确标注，正对后训练主线。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-308-从-verl-与-slime-最近两个月的更新-看-rl-基础设施的演进-以及-deepseek/

🔗 原文：https://zhuanlan.zhihu.com/p/2101471664965997651
