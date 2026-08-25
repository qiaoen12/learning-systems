# 学习系统总地图

> 面向刚进入大学、尚未形成稳定编程基础的学习者：把原始材料中的仓库按能力、难度和使用场景重组为一张可执行的导航图。

- 整理者：qiaoen12
- 整理日期：2026-08-24
- 整理依据：用户提供的仓库清单与说明；所有 GitHub 链接已在整理日检查可访问。
- 使用边界：这是资源地图，不是替代当前研究工作区中的 learning-plan-final.md。个人启动条件、学习日志和练习代码的落点仍以该执行计划与 AGENTS.md 为准；它们不随本仓库发布。

## 先用这张地图的方法

不要同时开十几个课程。对初学者，稳定的组合是：

1. 一条**主线**：软件构建能力中只选 The Odin Project 或 freeCodeCamp 之一。
2. 一条**副线**：先做 MIT Missing Semester，随后再选 Nand2Tetris 或一项 Build Your Own X 重建练习。
3. 一条**观察线**：OSSU 和公司 Handbook 只做导航、阅读与比较，不要求一次完成。

每个仓库文件都会回答：它解决什么问题、何时开始、如何验收、可与谁并行，以及现在不该做什么。

## 难度标记

| 标记 | 适合状态 | 含义 |
| --- | --- | --- |
| L0 | 无编程基础 | 可从电脑、命令行或网页编辑器开始 |
| L1 | 会基本变量、函数、Git | 能跟着课程独立写小程序 |
| L2 | 完成过一个小项目 | 能读较长代码、调试并记录错误 |
| L3 | 有 Python、数据结构或深度学习基础 | 适合系统原理、模型实现与架构权衡 |

## 能力分区

| 分区 | 要解决的能力 | 不把它当成什么 |
| --- | --- | --- |
| [01 学习运行与工具](./01-学习运行与工具/) | 命令行、版本控制、课程导航、用“重建”验证理解 | 不是单纯效率技巧收藏 |
| [02 软件构建能力](./02-软件构建能力/) | 从网页、程序到可展示项目 | 不是同时刷完两套全栈课程 |
| [03 计算机科学与系统思维](./03-计算机科学与系统思维/) | 从底层构建理解、分解复杂系统 | 不是零基础立刻刷系统设计面试题 |
| [04 AI 能力](./04-AI能力/) | AI 应用、深度学习原理与 LLM 实现 | 不是只学 Prompt 或只调用 API |
| [05 组织与公司能力](./05-组织与公司能力/) | 观察真实团队如何协作、决策和运营 | 不是照搬一家公司的制度 |
| [90 课程伴随资源与学习样本](./90-课程伴随资源与学习样本/) | 区分官方补充资料和学习者成果证据 | 不是另一条主学习线 |

## 初学者推荐顺序

    起步：MIT Missing Semester + 选择一条软件主线
      ├─ 主线 A：The Odin Project
      └─ 主线 B：freeCodeCamp
              ↓
    稳住编程后：Nand2Tetris（每周 1 次） + OSSU（只看地图）
              ↓
    有第一个项目后：Build Your Own X（只挑 1 个重建目标）
              ↓
    进入 AI：Microsoft GenAI 或 fast.ai（按目标二选一）
              ↓
    理解原理：Karpathy Zero to Hero
              ↓
    实现 LLM：LLMs from Scratch
              ↓
    项目变复杂后：System Design Primer

    全程低频并行：37signals / Sourcegraph Handbook

## 什么时候选什么

| 当前场景 | 优先仓库 | 可并行 | 暂缓 |
| --- | --- | --- | --- |
| 第一次用终端、Git、编辑器 | MIT Missing Semester | The Odin Project 或 freeCodeCamp 的最前段 | System Design、LLM from Scratch |
| 想做出网页或作品集 | The Odin Project | Missing Semester | freeCodeCamp 的完整第二套主线 |
| 更喜欢互动题、认证式反馈 | freeCodeCamp | Missing Semester | The Odin Project 的完整第二套主线 |
| 想理解电脑为什么能运行程序 | Nand2Tetris | 软件主线，每周一次 | System Design Primer |
| 想验证“自己真的懂了” | Build Your Own X 中的一个目标 | 当前软件主线 | 同时重建数据库、Git、OS 等多个大题 |
| 想做第一个生成式 AI 小应用 | Microsoft Generative AI for Beginners | 软件主线的 API 基础 | Karpathy、Raschka 的完整实现路线 |
| 想第一时间训练真实模型 | fast.ai course22 | Python 复习与项目记录 | 与 Microsoft 课程全量并行 |
| 想知道神经网络和 Transformer 如何工作 | Karpathy Zero to Hero | 少量数学复习 | 直接跳到 LLMs from Scratch 后半段 |
| 想手写 GPT 类 LLM | LLMs from Scratch | 实验记录 | 未完成 Python、PyTorch 和 Transformer 基础时开坑 |
| 想设计多人使用的大系统 | System Design Primer | 现有项目的复盘 | 没有小项目经验时死记答案 |
| 想理解公司怎样运转 | 37signals / Sourcegraph Handbook | 任一技术阶段，每周 30–60 分钟 | 把它们当作“唯一正确管理法” |

## 每阶段的最小完成信号

| 阶段 | 不看时长，先看结果 |
| --- | --- |
| 起步 | 能用终端创建、查看和提交一个小项目；能解释自己用了哪些命令 |
| 软件构建 | 有一个可运行、可展示、自己能讲清的作品 |
| 原理与系统 | 完成 Nand2Tetris 的一个连续模块，或从 Build Your Own X 重建一个小组件 |
| AI 应用 | 能写一个有输入、处理、输出和错误处理的 AI 小应用 |
| AI 原理 | 能手写并解释反向传播、注意力或最小 Transformer 的一个实现 |
| 系统设计 | 能为自己的项目写出需求、规模假设、瓶颈、取舍和失败路径 |
| 公司能力 | 能拿两家 Handbook 对同一制度做比较，并说出适用条件 |

## 收录规则

- **主课程/主仓库**：可成为学习路径节点，放在能力分区中。
- **官方课程伴随仓库**：用于补充主课程，不单独成为一条学习线。
- **学习样本仓库**：用于观察真实学习痕迹、对照提交方式与笔记质量，不复制答案后当作完成。
- Star、Fork 和名气不作为排序主依据；排序优先看先修关系、练习闭环、可验证输出和长期维护。

## 目录索引

| 目录 | 内容 |
| --- | --- |
| [01-学习运行与工具](./01-学习运行与工具/README.md) | MIT Missing Semester、OSSU、Build Your Own X |
| [02-软件构建能力](./02-软件构建能力/README.md) | The Odin Project、freeCodeCamp |
| [03-计算机科学与系统思维](./03-计算机科学与系统思维/README.md) | Nand2Tetris、System Design Primer |
| [04-AI能力](./04-AI能力/README.md) | Microsoft GenAI、fast.ai、Karpathy、Raschka |
| [05-组织与公司能力](./05-组织与公司能力/README.md) | 37signals、Sourcegraph Handbook |
| [90-课程伴随资源与学习样本](./90-课程伴随资源与学习样本/README.md) | fast.ai 课程网站仓库与两份学习样本 |
