# 盘点近期loop架构的工业级实现及带来的scaling law

> 盘点商汤 SenseNova-Loop-9B 与英伟达 Dory1.0-4B 两个 loop 架构的工业实现：只 loop 中间层、mHC 与 nGPT 两种跨 loop 控制、TBPTL 与难度感知 RLVR 课程、自投机解码与 KV 缓存优化，以及“隐式计算替代显式 token、推理深度不等于知识容量、k=2 是甜点”的 scaling law。直接对口后训练与 Agent 任务的架构选型，值得慢读。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-380-盘点近期loop架构的工业级实现及带来的scaling-law/

🔗 原文：https://zhuanlan.zhihu.com/p/2107139630764250597
