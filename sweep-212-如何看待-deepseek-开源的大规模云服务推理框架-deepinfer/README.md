# 如何看待 DeepSeek 开源的大规模云服务推理框架 DeepInfer ？

> 知乎热榜条目（522 人关注、约 52.7 万浏览、134 个回答；已通读问题页官方公告与默认排序前 5 个高赞回答）。DeepSeek 把生产推理框架 DeepInfer 开源（Apache-2.0，同步 deepseek-recipe）：本质是只跑 V4.1-Flash 的专用离线引擎，以 vLLM 为出身、集成 FlashMLA/DeepEP/DeepGEMM、MoE EP+EPLB、DSpark 推测解码与批次不变/确定性采样，官方自报单集群日吞吐 155 万亿 Token、每卡每小时 38 美元（谷价）。最有分量的批评也来自高赞回答：开源版缺 KV 缓存系统、PD 分离与跨副本负载均衡，官方经济性靠的正是未开源的这一层。对他是推理 infra 的一手材料，好看点在并行/调度细节与这条交付边界。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-212-如何看待-deepseek-开源的大规模云服务推理框架-deepinfer/

🔗 原文：https://www.zhihu.com/question/2095922064804636469
