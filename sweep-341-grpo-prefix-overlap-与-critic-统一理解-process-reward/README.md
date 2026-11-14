# GRPO、Prefix Overlap 与 Critic：统一理解 Process Reward、Gradient Noise 与 Long-Horizon RL

> haotian 把 ICML 2026《GRPO is Secretly a Process Reward Model》与 Scale Labs《To Critic or Not to Critic》两篇工作统一进一个框架：GRPO 靠同组 rollout 的共享前缀隐式得到蒙特卡洛过程奖励，Critic 则靠函数近似在无重叠处给出低方差 credit；小批量时 Critic 占优、大批量时 GRPO 追平，长 horizon 的 Agent RL 里二者都弱，作者主张 Critic 找节点、主动分支验证的混合路线。值得他看的是它把 GRPO/PPO 的取舍从经验之争变成可算的交叉批量公式与五条可检验假设，正撞 RL 配方与 Agent RL 主线。（作者 haotian，清华信通硕士；编辑于 2026-11-10）

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-341-grpo-prefix-overlap-与-critic-统一理解-process-reward/

🔗 原文：https://zhuanlan.zhihu.com/p/2103848002003772212
