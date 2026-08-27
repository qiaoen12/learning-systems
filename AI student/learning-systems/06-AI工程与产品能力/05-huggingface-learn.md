# 05｜Hugging Face Learn（LLM / Agents / MCP 三门课）

- 课程入口：[huggingface.co/learn](https://huggingface.co/learn)
- LLM Course：[huggingface/course](https://huggingface.co/learn/llm-course)
- Agents Course：[huggingface/agents-course](https://github.com/huggingface/agents-course)，活跃（最后更新 2026-06-30）
- MCP Course：[huggingface/mcp-course](https://github.com/huggingface/mcp-course)，活跃（最后更新 2026-05-26）
- 核查日期：2026-08-26
- 整理者：qiaoen12
- 整理日期：2026-08-26
- 难度：L2
- 适用主线：主线 B
- 条目类型：**课程型**，三门课里按需选一门
- 路线角色：AI 工程的开放替代路线

## 它解决什么问题

Hugging Face 的免费课程体系覆盖三个方向，全部带实操和在线环境：

| 课程 | 解决什么 | 什么时候选它 |
| --- | --- | --- |
| **LLM Course** | Transformer 库、tokenizer、数据集、微调、推理 | 想动手碰模型本身，而不只是调 API |
| **Agents Course** | Agent 原理、工具、框架对比、评测、最终项目 | 作为 Agent 主线的另一个选项 |
| **MCP Course** | Model Context Protocol，工具与上下文的标准化接入 | 已经手写过工具调用，想理解协议层 |

## 和微软那门课怎么选

Agents Course 和 [Microsoft AI Agents for Beginners](./04-microsoft-ai-agents-for-beginners.md) 是同一位置的两个选项，**只能选一门**。

微软那门更偏概念结构和设计模式讲解，章节边界清楚，适合喜欢先建立框架再动手的人。Hugging Face 这门更偏动手和生态实践，有最终项目和排行榜，适合需要外部节奏感的人。两门都免费、都在活跃更新，质量没有明显高下之分。

选择依据只有一条：你更需要“讲清楚”还是更需要“被推着做完”。

## 何时开始

和微软那门课的前置条件一样：能受控调用模型 API、做过一次检索、能读懂自己的代码。

LLM Course 的前置更高一些，需要能接受阅读 PyTorch 张量操作。如果目标是做 AI 应用而不是碰模型，这门课可以整门跳过。

## 建议的学习方式

选定一门后走完，不要三门同时开。这三门课的内容有交叠，同时推进会反复看到相似材料却始终没有一条完整链路。

用 Hugging Face 的在线环境跑通示例后，**必须在本地重做一遍**。在线环境把依赖、密钥和运行时都准备好了，这恰好屏蔽掉了真实部署中最容易出问题的部分。

## 最小验收

按选定课程各自的最终项目验收即可，但要额外满足一条：能在自己的机器上从零把它跑起来，包括装依赖、配密钥、处理报错。

## 并行与下一步

MCP Course 适合作为 Agent 主线之后的补充，篇幅不长。学完转 [AI Engineering](./06-aie-book.md) 做产品判断。

## 现在不做什么

不要因为 Hugging Face 生态庞大就顺着模型库、数据集、Spaces 一路逛下去。它的资源规模足以吞掉几个月而不产出任何一条完整链路——这一区所有条目里，它是最容易变成漫游的一个。
