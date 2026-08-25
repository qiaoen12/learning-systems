# 03｜Karpathy Neural Networks: Zero to Hero

- 原始仓库：[karpathy/nn-zero-to-hero](https://github.com/karpathy/nn-zero-to-hero)
- 整理者：qiaoen12
- 整理日期：2026-08-24
- 难度：L2–L3
- 路线角色：AI 原理主线

## 它解决什么问题

Karpathy 的课程从反向传播、micrograd、语言模型、MLP、BatchNorm、WaveNet 一直推进到 Transformer、GPT 和 Tokenizer。它要求学习者自己推导和实现关键部分，因此特别适合把“我会调用模型”升级成“我知道模型为何工作”。

## 何时开始

应先具备 Python、函数、循环、数组/张量的基本概念，并至少做过一个小型 AI 或数据项目。能接受较慢地读代码、打印中间结果和补一点代数，会明显更顺利。

## 建议的学习方式

每节先按要求手推或手写核心步骤，再与自动微分或框架结果比对。把每个练习保存在自己的仓库，记录梯度、形状、损失变化和一条失败样本。

## 最小验收

- 自己实现并解释一个简单反向传播或 micrograd 练习。
- 能用自己的话说明训练循环、损失和梯度的关系。
- 能运行一个最小语言模型并解释输入到输出的主要数据流。

## 并行与下一步

可低频复习线性代数和概率。完成 Transformer 与 Tokenizer 相关部分后，再系统进入 LLMs from Scratch。

## 现在不做什么

不要只看视频或直接复制 Notebook；不理解的推导先留下问题，再用小数值例子验证。
