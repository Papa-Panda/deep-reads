# REINFORCE Zero：为什么内核对齐后，极简 IS 能让异步 RL 稳定训练 20,000 步？

> 讲异步 LLM RL 为何不稳、又如何用内核对齐加最简单的 token 级重要性采样稳住 20,000 步：把对数比拆成权重滞后与内核失配两项，前者可由 IS 修正，后者必须靠训练-推理数值一致性消除。值得他看的是它把异步 RL 的不稳定从调参问题还原为数值执行问题，并给出可复用的对齐验证流程与泛化实验。注：该文标注 AI 辅助创作，发表时仅 4 赞，宜对照原文与 REINFORCE-Zero 项目核验。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-297-reinforce-zero-为什么内核对齐后-极简-is-能让异步-rl-稳定训练-20-00/

🔗 原文：https://zhuanlan.zhihu.com/p/2101589373355569444
