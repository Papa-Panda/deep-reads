# 【RL 入门到 GRPO 18】GRPO 到底改了 PPO 什么？去掉 Critic、换成组内基线、KL 进损失

> 58 秒把 GRPO 对 PPO 的改动讲到公式级：删掉与策略等大的 Critic；同题采样一组答案，用组均值与标准差算优势（G=64）；KL 不进奖励、以 k3 估计量直接进损失（β=0.04）。还点出一个常被漏掉的细节——每轮只更新一次使 ratio 恒为 1、clip 失效。短而密，适合他做 RL 配方对照。注：字幕轨错配，大纲据 UP 简介整理。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-129-rl-入门到-grpo-18-grpo-到底改了-ppo-什么-去掉-critic-换成组内基线/

🔗 原文：https://www.bilibili.com/video/BV1e6hm6uEYW
