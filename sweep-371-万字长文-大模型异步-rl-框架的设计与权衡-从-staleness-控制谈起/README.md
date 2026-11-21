# 「万字长文」大模型异步 RL 框架的设计与权衡：从 Staleness 控制谈起

> 小八在coding（北大 PKU-DAIR 博士在读，2026-11-16）万字拆解异步 RL 框架的 staleness 控制：先给“严格上限”下定义（每个参训 token 的生成版本与训练版本之差 ≤ 上限），再横评 verl / TRL / AReaL / SkyRL / NeMo-RL 等 14 种配置的三层机制（L1 准入 / L2 生成中 / L3 训练前），指出只限准入的框架管不住慢轨迹（AReaL 上限设 1、实际最高到 3，50 批里 46 批超限），而严格的办法要么丢弃（浪费算力、偏向短序列）要么等待（固定批次、调度僵化）；最后提出 Reserve–Occupy 协议——把 staleness 控制变成放置问题（v_buffer ≤ v_traj + η），生成前按最差情况预留合法槽位、完成后按最好情况尽早占用，SimRL 验证 600 批零超限、零丢弃，有效吞吐在各上限下均为最高。异步 RL infra 的核心设计文，协议已在作者的 PSRL 框架中实现。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-371-万字长文-大模型异步-rl-框架的设计与权衡-从-staleness-控制谈起/

🔗 原文：https://zhuanlan.zhihu.com/p/2105466561272211209
