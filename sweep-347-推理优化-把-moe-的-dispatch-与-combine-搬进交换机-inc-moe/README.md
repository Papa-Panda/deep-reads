# 推理优化：把 MoE 的 dispatch 与 combine 搬进交换机（INC-MoE）

> 华为 INC-MoE 论文精讲：把 MoE 推理的 dispatch/combine 搬进交换机，利用网内 AllGather 收重、ReduceScatter 发重的互补让两者同时在飞，OLMoE-1B-7B 上 TTFT 最高降 33%；正撞推理优化与通信主线，作者的七条自我批判（模拟交换机、只有 prefill、未开源）同样值得看。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-347-推理优化-把-moe-的-dispatch-与-combine-搬进交换机-inc-moe/

🔗 原文：https://zhuanlan.zhihu.com/p/2099380728895104850
