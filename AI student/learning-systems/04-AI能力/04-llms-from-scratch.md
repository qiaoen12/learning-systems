# 04｜LLMs from Scratch

- 原始仓库：[rasbt/LLMs-from-scratch](https://github.com/rasbt/LLMs-from-scratch)
- 上游状态：活跃（最后更新 2026-08-24）
- 核查日期：2026-08-26
- 整理者：qiaoen12
- 整理日期：2026-08-24
- 难度：L3
- 适用主线：主线 A 的终点；主线 B 请放到 16 周能力验收之后
- 路线角色：LLM 系统实现主线

## 它解决什么问题

该仓库把 GPT 类语言模型拆成可实现的步骤：文本处理、Tokenizer、Embedding、Attention、多头注意力、Transformer、预训练、微调和指令微调。每章配有代码、Notebook、练习与实验，适合在已有基础后建立系统实现理解。

## 何时开始

应已能使用 Python、虚拟环境、Notebook 和 PyTorch 的基本张量操作；最好完成 Karpathy 课程中的反向传播、注意力和 Transformer 相关内容。

## 建议的学习方式

严格按章节顺序运行、修改和验证。每到一个模块，先画出张量形状和数据流，再改一个小实验，例如上下文窗口、注意力头数或 Tokenizer 设置，并记录结果和失败原因。

## 最小验收

- 能从文本、Tokenizer 和 Embedding 走到一个可运行的最小 Transformer。
- 能解释 Self-Attention 中 Q、K、V 的作用及张量形状。
- 完成一个预训练或微调实验，并记录可复现的配置与结果。

## 并行与下一步

可与少量 PyTorch 文档、数学复习并行。完成后可回到 Build Your Own X 选择 LLM/RAG 主题，或将原理连接到自己的 AI 应用项目。

## 现在不做什么

不要把目标定成复刻商业大模型，也不要跳过前面的文本、Tokenizer 和注意力章节直接下载权重。
