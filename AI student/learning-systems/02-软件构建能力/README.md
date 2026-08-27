# 02｜软件构建能力

这一分区的目标是让初学者尽早获得“自己做出能运行、能展示的软件”的体验。它现在包含**三条互斥的主线**，必须三选一，不能并行。

- 整理者：qiaoen12
- 整理日期：2026-08-24
- 核查日期：2026-08-26

## 先按目标分流

选哪条主线取决于你要去哪里，不取决于哪条更有名。

| 你的目标 | 选哪条 | 语言与领域 |
| --- | --- | --- |
| **做 AI 应用、后端服务、数据工具** | [CS50P](./03-cs50p.md) | Python |
| 做网站、前端、Web 全栈，且愿意自己查资料做项目 | [The Odin Project](./01-the-odin-project.md) | HTML/CSS/JS，后接 Node 或 Rails |
| 做网站，但需要互动练习、短反馈和认证节点 | [freeCodeCamp](./02-freecodecamp.md) | 主干为 Web，另有 Python 认证 |

前两行对应地图的两条主线：CS50P 是**主线 B（AI 应用工程）**的编程入口，Odin 和 freeCodeCamp 是**主线 A（通用软件工程）**的两个选项。

分流的依据很实际：AI 工程链路上的每一环——数据处理、API 服务、模型调用、检索、评测——默认都在 Python 生态里。走 Web 主线再转 Python 不会白费，但那几百小时不在通往目标的直线上。

## 项目练习

三条主线之外，[Project Based Learning](./04-project-based-learning.md) 是按语言组织的项目库，作为副线使用。学完语言基础不知道做什么时打开它，挑一个，做完，加一个教程里没有的功能。

## 与其他分区的关系

- 和 [MIT Missing Semester](../01-学习运行与工具/01-mit-missing-semester.md) 同时开始，两条主线都一样。
- 主线 B 学完 CS50P 后，下一步是 `requests` → FastAPI 官方教程 → SQLite，然后直接进 [06 AI 工程与产品能力](../06-AI工程与产品能力/README.md)。
- 主线 A 做出第一个项目后，再进入 [Nand2Tetris](../03-计算机科学与系统思维/01-nand2tetris.md)、Build Your Own X 和 [04 AI 能力](../04-AI能力/README.md)。
- 本区的普遍价值不是某种职业路线，而是编程、调试、Git 和项目交付的基本能力。这部分三条主线都能给。
