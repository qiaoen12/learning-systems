# 04｜AI 能力（原理层）

这一区回答“模型为什么能工作”。它按三层递进：先能做出应用，再理解网络和 Transformer，最后才手写 LLM。这个顺序刻意避免初学者直接跳进大模型源码而失去反馈。

- 整理者：qiaoen12
- 整理日期：2026-08-24
- 核查日期：2026-08-26

## 和 06 的分工

新增的 [06 AI 工程与产品能力](../06-AI工程与产品能力/README.md) 回答的是另一个问题：**这个 AI 功能可不可靠、什么时候会失败、值不值得做下去。**

| | 04 原理层 | 06 工程层 |
| --- | --- | --- |
| 回答 | 模型为什么能工作 | 系统能不能交付 |
| 产出 | 能手写反向传播、注意力 | 能给 AI 功能定验收标准 |
| 主线 | A 的主要方向 | B 的核心区 |

阅读顺序是 04 → 06 → 05。编号上 06 排在最后只是为了不打断已有链接。

**主线 B 在本区只需要两件事**：做完一个 AI 应用入口，以及跟着 Karpathy 手写一次 self-attention。其余留到 16 周能力验收之后。

## 本区顺序

1. [Microsoft Generative AI for Beginners](./01-microsoft-generative-ai-for-beginners.md) 或 [fast.ai](./02-fastai-course22.md)：按目标二选一作为应用入口。
2. [Karpathy Zero to Hero](./03-karpathy-nn-zero-to-hero.md)：补齐神经网络、反向传播和 GPT/Tokenizer 的实现理解。
3. [LLMs from Scratch](./04-llms-from-scratch.md)：在 PyTorch 和 Transformer 基础稳定后，系统实现 GPT 类模型。

## 两个入口如何选

| 想先解决的场景 | 先学 |
| --- | --- |
| 用 API、Python/TypeScript 做生成式 AI 小应用 | [Microsoft Generative AI for Beginners](./01-microsoft-generative-ai-for-beginners.md) |
| 尽快训练真实模型、以项目体验深度学习 | [fast.ai](./02-fastai-course22.md) |

这两者都不应和 Karpathy、Raschka 的完整路线同时全量推进。一个阶段只保留一个 AI 主课程。

**主线 B 选微软那门**，因为它直接对应 API 调用、应用结构和失败处理；fast.ai 的训练优先取向对应的是建模路径，可以整门跳过。

## 关于上游状态

本区两个条目的上游已经停更，但内容不过期，需要知道的是它们的正确入口：

- fast.ai：`fastai/course22` 是 2022 版快照（2024-10 停更），以 [course.fast.ai](https://course.fast.ai/) 主站为准。
- Karpathy：`nn-zero-to-hero` 2024-08 后无新提交，原理不过时；后续工作转到了 `nanoGPT` 和 `nanochat`，`LLM101n` 已归档。
