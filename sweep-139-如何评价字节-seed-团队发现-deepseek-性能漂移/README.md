# 如何评价字节 Seed 团队发现 DeepSeek 性能漂移？

> 知乎热榜约291万热度、18个回答。字节 Seed 论文《Periodic Weak Spots》指出 DeepSeek V4 系列的压缩稀疏注意力会让长上下文检索精度随 token 位置周期性起伏：同一条事实只因前缀多了几个 token、落进压缩窗口的不同槽位，命中率可差出数十个百分点，而平均分几乎看不出来。前排三答从机制、消融因果到线上复现（系统提示多一个空格就可能翻车）层层坐实，并给出 padding 扫描、按相位报告精度等可落地的评测与部署对策。已读默认排序前3答。

📖 阅读版：https://papa-panda.github.io/deep-reads/sweep-139-如何评价字节-seed-团队发现-deepseek-性能漂移/

🔗 原文：https://www.zhihu.com/question/2091513666864682278
