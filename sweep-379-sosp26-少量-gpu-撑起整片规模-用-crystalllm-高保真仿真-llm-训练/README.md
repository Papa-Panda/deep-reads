# 【SOSP26】少量 GPU，撑起整片规模：用 CrystalLLM 高保真仿真 LLM 训练

> 想飞的石头（2026-11-21）精讲 SOSP'26 论文 CrystalLLM：用不到 1% 的 GPU 高保真仿真千卡级 LLM 训练——执行图捕获 + 混合重放，2048 卡只需 32 卡，迭代时间误差仅 0.58%、峰值显存误差 <0.01%，还能拿来调并行配置、查显存泄漏、定位降频节点。分布式训练系统方向的硬核长文，值得慢读。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-379-sosp26-少量-gpu-撑起整片规模-用-crystalllm-高保真仿真-llm-训练/

🔗 原文：https://zhuanlan.zhihu.com/p/2107580162787251598
