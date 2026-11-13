# 乱谈kernel之large EP is not all you need

> 是小肖啊在 NVL72 上实测 DeepInfer 的 DeepGEMM MegaMoE kernel，拆解 DeepSeek V4.1 Flash decode 的 MoE 层：生产负载下 EP32→EP64/72 只快约 5%，因为每专家约 135 行已越过约 120 行/专家的阈值，权重读取不再是瓶颈，剩下的是计算、NVLink 与约 45µs 固定开销；而大 EP 的故障、同步与部署粒度成本随卡数线性增长。值得他看的是它把“EP 越大越好”的官方建议用实测和延迟模型（留出误差 2.5%–6.4%）逐项证伪，并给出按延迟预算选 EP 的四步决策法，正撞 MoE 推理优化主线。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-335-乱谈kernel之large-ep-is-not-all-you-need/

🔗 原文：https://zhuanlan.zhihu.com/p/2101054133134537189
