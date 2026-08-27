# 学习系统总地图

> 面向从零开始、目标是能独立构建并验收软件或 AI 系统的自学者：把公开的优质学习仓库按能力、难度和使用场景重组为一张可执行的导航图。

- 整理者：qiaoen12
- 首次整理：2026-08-24
- 最近核查：2026-08-26
- 使用边界：这是资源地图，不是替代当前研究工作区中的 learning-plan-final.md。个人启动条件、学习日志和练习代码的落点仍以该执行计划与 AGENTS.md 为准；它们不随本仓库发布。

## 这份地图和 awesome-list 的区别

收录的仓库大多是几十万星的知名项目，找到它们不需要这份地图。地图提供的是两样清单类项目通常不给的东西：

**一是判断。** 每个条目都回答：它解决什么问题、何时开始、如何验收、可与谁并行，以及**现在不该做什么**。最后一项往往最有用——大多数自学失败不是因为资料不够，而是同时开了太多条线。

**二是时效。** 每个条目标注上游最后更新时间和状态。学习资料会死，而清单类项目通常不告诉你哪一条已经归档了。本次核查就发现了一条：Sourcegraph Handbook 已于 2024 年归档。

## 第一步：先选主线

两条主线的分岔点在语言和领域，不在难度。选错了不会白费，但会绕远路。

| 你的目标 | 走哪条 | 编程入口 |
| --- | --- | --- |
| 做 AI 应用、Agent、知识库、数据工具 | **主线 B：AI 应用工程** | Python（CS50P） |
| 做网站、前端、Web 全栈、通用软件 | **主线 A：通用软件工程** | JavaScript（Odin 或 freeCodeCamp） |

分流的依据很实际：AI 工程链路上的每一环——数据处理、API 服务、模型调用、检索、评测——默认都在 Python 生态里。

两条主线**共用**三样东西：起步的 MIT Missing Semester、导航层（roadmap.sh / Teach Yourself CS / OSSU）、观察线（公司 Handbook）。

## 主线 A：通用软件工程

    起步：MIT Missing Semester
              ↓
    主线（二选一）：The Odin Project 或 freeCodeCamp
              ↓
    有第一个项目后：Project Based Learning 挑 1 个 / Nand2Tetris 每周 1 次
              ↓
    进入 AI：Microsoft GenAI 或 fast.ai（按目标二选一）
              ↓
    理解原理：Karpathy Zero to Hero
              ↓
    实现 LLM：LLMs from Scratch
              ↓
    项目变复杂后：System Design 101 → System Design Primer → DDIA

## 主线 B：AI 应用工程

    起步：MIT Missing Semester + CS50P（Python）
              ↓
    做出服务：requests → FastAPI 官方教程 → SQLite
              ↓
    接入模型：Microsoft GenAI for Beginners + OpenAI Cookbook
              ↓
    检索：手写最小 RAG → RAG Techniques 排障
              ↓
    验收：promptfoo 建测试表（这一步不能跳）
              ↓
    Agent：手写 ReAct loop → Microsoft AI Agents for Beginners
              ↓
    产品判断：AI Engineering（Chip Huyen）
              ↓
    补原理（可选）：Karpathy「Let's build GPT」前 1 小时

    全程低频并行：37signals / GitLab Handbook

主线 B 刻意把 Nand2Tetris、OSSU 完整课表和 LLMs from Scratch 排除在外。它们不是不好，是在这条路径上短期内没有回报——懂 ALU 不会让你更快定位一次检索失败。

## 难度标记

| 标记 | 适合状态 | 含义 |
| --- | --- | --- |
| L0 | 无编程基础 | 可从电脑、命令行或网页编辑器开始 |
| L1 | 会基本变量、函数、Git | 能跟着课程独立写小程序 |
| L2 | 完成过一个小项目 | 能读较长代码、调试并记录错误 |
| L3 | 有 Python、数据结构或深度学习基础 | 适合系统原理、模型实现与架构权衡 |

## 状态标记

每个条目文件都标注上游状态和核查日期。三级分类：

| 状态 | 含义 | 怎么用 |
| --- | --- | --- |
| 活跃 | 近半年内有更新 | 正常使用 |
| 低频维护 | 半年到两年无更新 | 可用，但要留意有没有更新的替代 |
| 已停更 / 已归档 | 两年以上或已 archived | 内容不一定失效，但引用时必须带时间限定 |

**上游停更不等于内容失效。** 反向传播的原理不会过期，2020 年的学习样本也仍是有效的样本。标注的意义是让你知道自己在读什么年份的东西。

## 能力分区

| 分区 | 要解决的能力 | 主线归属 |
| --- | --- | --- |
| [01 学习运行与工具](./01-学习运行与工具/) | 命令行、版本控制、课程导航、用“重建”验证理解 | 共用 |
| [02 软件构建能力](./02-软件构建能力/) | 从脚本、网页到可展示项目 | 分岔点，三选一 |
| [03 计算机科学与系统思维](./03-计算机科学与系统思维/) | 从底层构建理解、分解复杂系统 | 主线 A 必经，主线 B 可选 |
| [04 AI 能力](./04-AI能力/) | 模型为什么能工作：应用入口、深度学习原理、LLM 实现 | 主线 A 主要方向 |
| [06 AI 工程与产品能力](./06-AI工程与产品能力/) | 系统能不能交付：调用、检索、评测、Agent 控制、成本判断 | 主线 B 核心区 |
| [05 组织与公司能力](./05-组织与公司能力/) | 观察真实团队如何协作、决策和运营 | 共用，低频 |
| [90 课程伴随资源与学习样本](./90-课程伴随资源与学习样本/) | 区分官方补充资料和学习者成果证据 | 共用，不是学习线 |

阅读顺序是 04 → 06 → 05。06 在编号上排最后只是为了不打断已有链接。

## 什么时候选什么

| 当前场景 | 优先条目 | 可并行 | 暂缓 |
| --- | --- | --- | --- |
| 第一次用终端、Git、编辑器 | MIT Missing Semester | 所选主线的最前段 | System Design、LLM from Scratch |
| 想做 AI 应用，从零学编程 | CS50P | Missing Semester | Odin、freeCodeCamp、Nand2Tetris |
| 想做出网页或作品集 | The Odin Project | Missing Semester | freeCodeCamp 的完整第二套主线 |
| 更喜欢互动题、认证式反馈 | freeCodeCamp | Missing Semester | The Odin Project 的完整第二套主线 |
| 学完语言基础，不知道做什么项目 | Project Based Learning 挑 1 个 | 当前主线 | 同时开多个项目 |
| 想理解电脑为什么能运行程序 | Nand2Tetris | 软件主线，每周一次 | 主线 B 请整门跳过 |
| 第一次调模型 API | Microsoft GenAI for Beginners | OpenAI Cookbook 按需查 | Karpathy、Raschka 的完整路线 |
| RAG 跑通了但答不准 | RAG Techniques 按症状查 | LLM 评测（必须同时用） | 换框架、加更多技术 |
| 不知道改动是变好还是变坏 | promptfoo 建测试表 | RAG Techniques | 追求分数和覆盖率 |
| 想做 Agent | 先手写 ReAct loop | Microsoft AI Agents for Beginners | Agent 框架、多 Agent |
| 不确定这个方向值不值得做 | AI Engineering | 自己项目的成本核算 | 继续加功能 |
| 想知道神经网络和 Transformer 如何工作 | Karpathy Zero to Hero | 少量数学复习 | 直接跳到 LLMs from Scratch 后半段 |
| 想手写 GPT 类 LLM | LLMs from Scratch | 实验记录 | 未完成 Python、PyTorch 和 Transformer 基础时开坑 |
| 想设计多人使用的大系统 | System Design 101 → DDIA | 现有项目的复盘 | 在 System Design Primer 里刷场景题 |
| 想理解公司怎样运转 | 37signals + GitLab Handbook 对读 | 任一技术阶段，每周 30–60 分钟 | 把任一家当作“唯一正确管理法” |

## 每阶段的最小完成信号

不看时长，先看结果。

**两条主线共用**

| 阶段 | 完成信号 |
| --- | --- |
| 起步 | 能用终端创建、查看和提交一个小项目；能解释自己用了哪些命令 |
| 编程基础 | 有一个可运行、可展示、自己能讲清的作品 |
| 公司能力 | 能拿两家 Handbook 对同一制度做比较，并说出适用条件 |

**主线 A**

| 阶段 | 完成信号 |
| --- | --- |
| 原理与系统 | 完成 Nand2Tetris 的一个连续模块，或重建一个小组件 |
| AI 原理 | 能手写并解释反向传播、注意力或最小 Transformer 的一个实现 |
| 系统设计 | 能为自己的项目写出需求、规模假设、瓶颈、取舍和失败路径 |

**主线 B**

| 阶段 | 完成信号 |
| --- | --- |
| 服务能力 | 写出一个 FastAPI 服务，数据存进 SQLite 且重启不丢 |
| 受控调用 | 能让模型稳定返回结构化结果，并处理超时、格式漂移和 API 报错 |
| 检索 | 能手写一条 RAG 链路，并解释切片大小如何影响回答质量 |
| 验收 | 能拿测试表判断一次错误回答是检索失败、prompt 失败还是知识缺失 |
| 控制 | 能说明哪些工具不该让 Agent 自动执行，低置信度时怎么转人工 |
| 判断 | 能算清一次会话成本，并回答“为什么用户要用这个而不是直接用 ChatGPT” |

## 收录规则

- **主课程/主仓库**：可成为学习路径节点，放在能力分区中。
- **查阅型资源**：Cookbook、技术目录、工具文档。**不排进学习计划**，遇到具体问题才打开。混淆这一类和课程型，是把地图变成收藏夹的主因。
- **官方课程伴随仓库**：用于补充主课程，不单独成为一条学习线。
- **学习样本仓库**：用于观察真实学习痕迹、对照提交方式与笔记质量，不复制答案后当作完成。
- **状态与时效**：每个条目必须标注上游最后更新时间和核查日期。归档或长期停更的条目要写明状态，不能只留链接。
- **利益相关**：条目背后有商业主体时要说明，例如 Build Your Own X 现由 CodeCrafters 维护、System Design 101 来自 ByteByteGo。
- Star、Fork 和名气不作为排序主依据；排序优先看先修关系、练习闭环、可验证输出和长期维护。

## 目录索引

| 目录 | 内容 |
| --- | --- |
| [01-学习运行与工具](./01-学习运行与工具/README.md) | MIT Missing Semester、OSSU、Build Your Own X、Teach Yourself CS、roadmap.sh |
| [02-软件构建能力](./02-软件构建能力/README.md) | The Odin Project、freeCodeCamp、CS50P、Project Based Learning |
| [03-计算机科学与系统思维](./03-计算机科学与系统思维/README.md) | Nand2Tetris、System Design Primer、System Design 101 |
| [04-AI能力](./04-AI能力/README.md) | Microsoft GenAI、fast.ai、Karpathy、Raschka |
| [05-组织与公司能力](./05-组织与公司能力/README.md) | 37signals、GitLab、Sourcegraph（已归档） |
| [06-AI工程与产品能力](./06-AI工程与产品能力/README.md) | OpenAI Cookbook、RAG Techniques、LLM 评测、AI Agents、Hugging Face Learn、AI Engineering |
| [90-课程伴随资源与学习样本](./90-课程伴随资源与学习样本/README.md) | fast.ai 课程网站仓库与两份学习样本 |

## 用这张地图的三条硬规则

1. **一条主线**：02 分区里三选一，不并行。
2. **一门课程**：任何时候只有一门课程型资源在推进。查阅型资源不受此限，因为你不会去读完它们。
3. **一次一改**：改配置、改 prompt、改切片，一次只动一处，并且有办法验证改动是否有效。

违反第三条的代价最隐蔽：你会一直在动，但永远不知道哪一下起了作用。
