# AI 工程师学习计划（可执行周表）

Version: 1.0-opencode  
基于: `howto.md` v1.0  
编写者备注: 本文档由 opencode 生成，供与 codex 版本对照择优使用。  
生成日期: 2026-06-29

---

## 0. 使用说明

- 本计划严格基于 `howto.md` 的五层能力模型与资源清单，不替换其方法论。
- 仅做两处微调（见 §3），不改变 howto 的阶段顺序与核心原则。
- 每个 Phase 列出：学习目标 / 资源 / 每周任务 / Exit Criteria。
- 每周末做一次 checkpoint，达不到 Exit Criteria 不进入下一阶段。
- 周计划是建议节奏，可按实际进度伸缩，但**顺序不可跳级**。

---

## 1. 学习者真实定位（执行前提）

- 转行背景，无语言基础。
- 此前所有部署的软件、脚本、Agent 工具均由 AI（Codex 等）在方向性指导下完成，本人未独立编写代码。
- 能提需求、验收结果、做产品判断；但**不能独立读、写、调代码**。
- 因此 howto Phase 1「从零学 Python + HTTP 基础」是必要的，不跳过。

---

## 2. 核心原则（来自 howto，不可违背）

### 禁止
- 禁止纯看书不做项目
- 禁止只学课程不写代码
- 禁止无限扩展工具栈
- 禁止用 AI 生成练习代码后直接交差（学习阶段必须手写）

### 强制
- 70% 项目驱动
- 20% 定向学习
- 10% 回顾与优化

---

## 3. 两处微调（相对 howto 的增量）

### 微调 A：用已部署系统当「答案对照表」
学 fundamentals 时，可以把自己已部署的系统（Aether / Ansible / 6 台 VPS）当作**观察对象**，但不替代手写练习。
- 例：学 TCP 时，可在 vps3 上 `tcpdump` 抓一次 Aether 请求看链路，但**仍必须手写 HTTP client 练习**。
- 作用：把抽象概念锚到真实系统，降低枯燥感，不跳过练习。

### 微调 B：Phase 4 项目锁定为客服 Agent
howto Phase 4 写的是泛化 AI 产品。本计划锁定为你已提到的「客服 Agent」真实交付目标，不做玩具。
- 作用：有真实交付目标才撑得过 16 周，且学完即能用。

---

## 4. 每日时间结构

工作日（3–5h）：
- 1h 学习（书 / 视频）
- 2h 编码（手写）
- 0.5–1h debug / 回顾

碎片时间（5–15min × 10+ 次，约 1h）：
- 回顾笔记
- 看一段视频
- 背一个概念

周末：
- 完整项目迭代
- 系统重构
- 写周报

---

## 5. Phase 1 — 编程 + 系统底座（Week 1–3）

### 学习目标
建立「能写工程代码 + 看懂系统」的能力。

### 资源
- Python Crash Course（Eric Matthes）
- Automate the Boring Stuff with Python
- Harvard CS50P（视频，强推）
- Computer Networking: A Top-Down Approach（网络部分）

---

### Week 1：Python 基础（一）

**学习**
- CS50P：Week 0–1
- Python Crash Course：第 1–5 章（变量 / 列表 / 字典 / if / while / for）

**编码任务（全部手写，不用 AI 生成）**
- [ ] 写一个命令行计算器（+ - × ÷）
- [ ] 写一个文件读取脚本：读一个 txt，统计每个单词出现次数，输出 top 10
- [ ] 写一个函数：输入一个列表，返回去重后的列表和重复项计数

**Checkpoint**
- 能解释 list / dict / if / for 的执行流程
- 能独立写 50 行以内的 Python 脚本不报语法错

---

### Week 2：Python 基础（二）+ HTTP 入门

**学习**
- CS50P：Week 2–3
- Python Crash Course：第 6–9 章（函数 / 类 / 文件 / 异常）
- Computer Networking Top-Down：第 2 章（应用层，重点 HTTP）

**编码任务**
- [ ] 用 `requests` 库写一个 HTTP client：调用一个公开 API（如 jsonplaceholder），打印响应
- [ ] 写一个简单爬虫：抓一个静态网页标题和所有链接
- [ ] 用 `json` 模块读写一个配置文件
- [ ] 用 `try/except` 给上面的脚本加错误处理

**对照观察（微调 A）**
- 在 vps3 上 `curl -v https://api.qiao.pro` 看一次真实 HTTP 请求头，和书上 HTTP 章节对照

**Checkpoint**
- 能解释 HTTP 请求方法、状态码、请求头/响应头
- 能用 Python 独立写一个 API 调用脚本

---

### Week 3：操作系统基础 + 并发入门

**学习**
- OSTEP：第 2–4 章（进程抽象）
- OSTEP：第 25–27 章（线程 / 锁）
- Python Crash Course：第 17–18 章（测试 / 部署）

**编码任务**
- [ ] 写一个 thread pool：并发下载 5 个 URL，统计总耗时
- [ ] 用 `threading` 给下载脚本加线程池，对比串行 vs 并行耗时
- [ ] 写一个简单的 CLI 工具（用 `argparse`），接受参数执行不同命令

**Checkpoint（Phase 1 Exit Criteria）**
- ✔ 能写 API 调用脚本
- ✔ 能解释 HTTP / TCP 基本流程
- ✔ 能写简单并发代码（thread pool）
- ✔ 能解释进程 vs 线程的区别

---

## 6. Phase 2 — 后端系统工程（Week 4–7）

### 学习目标
构建「可扩展系统思维」。

### 资源
- DDIA（Designing Data-Intensive Applications）
- FastAPI 官方文档
- Grokking the System Design Interview（可选）

---

### Week 4：FastAPI + REST API 设计

**学习**
- FastAPI 官方教程：第一部分到第六部分
- DDIA：第 1–2 章（数据系统基础）

**编码任务**
- [ ] 用 FastAPI 写一个 CRUD API（用户增删改查）
- [ ] 数据存 SQLite，用 `sqlalchemy` 或原生 `sqlite3`
- [ ] 加 input validation（用 Pydantic）
- [ ] 写一个简单的 auth 中间件（API key 校验）

**Checkpoint**
- 能独立写一个完整 REST API
- 能解释 DDIA 第 1 章的核心概念（可靠性 / 可扩展性 / 可维护性）

---

### Week 5：数据库 + 索引

**学习**
- DDIA：第 3 章（存储与检索）
- CMU 15-445（可选看 lecture 1–3）

**编码任务**
- [ ] 给 Week 4 的 API 加索引，对比查询性能
- [ ] 写一个慢查询分析：构造 10 万行数据，测不同查询的耗时
- [ ] 解释 B+ Tree 为什么快（手画结构）

**对照观察（微调 A）**
- 看 Aether 的数据库 schema，理解它的表结构和索引设计（只读，不改）

**Checkpoint**
- 能解释索引为什么快
- 能给真实表加索引并验证性能

---

### Week 6：并发与性能

**学习**
- DDIA：第 5–6 章（复制 / 分区）
- FastAPI async / await 官方文档

**编码任务**
- [ ] 把 Week 4 的 API 改成 async 版本，对比性能
- [ ] 写一个 event loop 示例：并发请求 3 个 API，合并结果
- [ ] 用 `asyncio` + `aiohttp` 重写 Week 2 的爬虫

**Checkpoint**
- 能解释 async / await 和 threading 的区别
- 能解释数据复制和分区的基本概念

---

### Week 7：系统设计综合 + Redis

**学习**
- DDIA：第 7–9 章（事务 / 一致性 / CAP）
- Redis 基础（数据结构 / 缓存模式）

**编码任务**
- [ ] 给 API 加 Redis 缓存层
- [ ] 写一个简单的限流器（用 Redis 计数）
- [ ] 画一张系统架构图：用户 → API → 缓存 → DB，标注每层数据流

**Checkpoint（Phase 2 Exit Criteria）**
- ✔ 能设计后端系统
- ✔ 能理解数据一致性 / CAP
- ✔ 能优化 API 性能（缓存 / 索引 / 并发）

---

## 7. Phase 3 — AI 基础（Week 8–11）

### 学习目标
理解 Transformer 本质，不再把 LLM 当黑盒。

### 资源
- Karpathy「Let's build GPT」（YouTube，必看必做）
- Andrew Ng ML Specialization（Coursera，第一门课）
- Jay Alammar「Illustrated Transformer」

---

### Week 8：机器学习基础

**学习**
- Andrew Ng ML：Week 1–2（线性回归 / 梯度下降）
- 理解 loss / optimizer / training loop

**编码任务**
- [ ] 用 numpy 手写一个线性回归（不用 sklearn）
- [ ] 手写 gradient descent，可视化 loss 下降曲线
- [ ] 理解并能解释：什么是 training / inference / overfitting

**Checkpoint**
- 能解释梯度下降的数学直觉
- 能手写一个训练 loop

---

### Week 9：深度学习基础 + Embedding

**学习**
- Andrew Ng ML：Week 3（逻辑回归 / 神经网络入门）
- 理解：什么是 embedding / 向量空间 / 语义相似度

**编码任务**
- [ ] 用 numpy 手写一个最简神经网络（1 层）
- [ ] 用 `sentence-transformers` 跑一次 embedding，算两个句子的余弦相似度
- [ ] 理解并能解释：embedding 为什么能做语义搜索

**Checkpoint**
- 能解释神经网络的前向传播
- 能解释 embedding 的作用

---

### Week 10：Transformer（核心周）

**学习**
- Karpathy「Let's build GPT」完整看完，跟着手敲
- Jay Alammar「Illustrated Transformer」读完
- 「Attention Is All You Need」论文（精度）

**编码任务**
- [ ] 跟着 Karpathy 视频手写 self-attention（numpy / PyTorch）
- [ ] 手画 Transformer 结构图，标注 Q/K/V / attention / FFN / positional encoding
- [ ] 解释 tokenization / next-token prediction 的完整流程

**Checkpoint**
- ✔ 能手写 attention
- ✔ 能解释 Transformer 结构
- ✔ 能解释 token 是怎么生成的

---

### Week 11：PyTorch + mini Transformer

**学习**
- PyTorch 官方 60 分钟入门
- 复盘 Karpathy 视频

**编码任务**
- [ ] 用 PyTorch 实现一个 mini GPT（字符级，小数据集）
- [ ] 训练它生成简单文本
- [ ] 理解并能解释：training loss / generation / sampling

**Checkpoint（Phase 3 Exit Criteria）**
- ✔ 能解释 Transformer
- ✔ 能手写 attention
- ✔ 能理解 embedding
- ✔ 能用 PyTorch 跑一次训练

---

## 8. Phase 4 — AI 工程（Week 12–16）

### 学习目标
构建 AI 应用系统，交付客服 Agent 项目。

### 资源
- FAISS / ChromaDB 文档
- ReAct 论文
- OpenAI / Claude API 文档（function calling）

---

### Week 12：RAG 原理（手写，不用框架）

**学习**
- 理解 RAG pipeline：文档 → 切片 → embedding → 向量检索 → LLM 生成
- 理解 chunking 策略对检索质量的影响

**编码任务**
- [ ] 不用 LangChain，手写一个 RAG：
  - PDF 读取 + 切片
  - 调 embedding API
  - 存入 FAISS / Chroma
  - 检索 + 拼接 prompt → 调 LLM
- [ ] 测试不同 chunk size 对回答质量的影响

**Checkpoint**
- 能独立解释 RAG 每一步在做什么
- 能手写一个不依赖框架的 RAG

---

### Week 13：向量数据库 + 检索优化

**学习**
- ChromaDB / Qdrant 文档
- 理解：向量索引（HNSW / IVF）、top-k 检索、reranking

**编码任务**
- [ ] 给 Week 12 的 RAG 加 reranking
- [ ] 支持多文档、文档来源标注
- [ ] 测试不同 embedding 模型的检索效果

**Checkpoint**
- 能解释向量检索的原理
- 能优化 RAG 检索质量

---

### Week 14：Agent 原理（ReAct + Tool Calling）

**学习**
- ReAct 论文（Synergizing Reasoning and Acting）
- 理解：agent loop / planning / tool selection / memory

**编码任务**
- [ ] 手写一个 ReAct agent（不用框架）：
  - 接收用户请求
  - LLM 决定调用哪个 tool
  - 执行 tool，返回结果
  - LLM 决定下一步
- [ ] 实现至少 3 个 tool：搜索 / 文件读取 / API 调用

**Checkpoint**
- 能解释 agent loop 的执行流程
- 能手写一个不用框架的 agent

---

### Week 15：客服 Agent MVP（整合）

**编码任务（这是你的真实交付项目）**
- [ ] 整合 Week 12–14 的成果，构建客服 Agent：
  - 知识库（RAG，存 FAQ / 产品文档）
  - 对话历史（短期 memory）
  - 工具调用（查订单 / 查 FAQ / 转人工）
  - API 层（FastAPI）
- [ ] 简单 UI（可用命令行或最简 Web 页面）

**Checkpoint**
- 客服 Agent 能回答知识库内的问题
- 能调用至少 2 个工具
- 有对话历史

---

### Week 16：Agent 优化 + 测试

**编码任务**
- [ ] 加长期 memory（向量库存储历史对话）
- [ ] 加错误恢复（tool 调用失败时的 fallback）
- [ ] 写测试用例：覆盖正常 / 边界 / 异常场景
- [ ] 记录单次会话的 token 消耗

**Checkpoint（Phase 4 Exit Criteria）**
- ✔ 能写 RAG（不用框架）
- ✔ 能写 Agent（不用框架）
- ✔ 能组合工具链
- ✔ 客服 Agent MVP 可用

---

## 9. Phase 5 — AI 产品系统（Week 17–24）

### 学习目标
进入「可创业级能力」。

### 资源
- Chip Huyen《Designing Machine Learning Systems》
- 续读 DDIA 剩余章节

---

### Week 17–18：成本与延迟工程

**学习**
- 理解 token 成本模型、latency 优化、缓存策略

**编码任务**
- [ ] 给客服 Agent 加缓存层（高频问题缓存回答）
- [ ] 分析 token 消耗，定出单会话成本上限
- [ ] 测量端到端 latency，找出瓶颈

**Checkpoint**
- 能算清单次会话成本
- 能定位 latency 瓶颈

---

### Week 19–20：多 Agent 协作

**学习**
- 多 agent 通信协议
- task decomposition / state management

**编码任务**
- [ ] 扩展客服 Agent 为多 agent：
  - routing agent（分发任务）
  - knowledge agent（RAG）
  - ops agent（执行操作）
- [ ] 实现 agent 间通信和结果聚合

**Checkpoint**
- 能设计多 agent 协作架构
- 能实现 agent 间通信

---

### Week 21–22：数据闭环

**学习**
- 理解数据飞轮：用户数据 → 改进系统 → 提升效果

**编码任务**
- [ ] 记录所有客服会话（问题 / 检索结果 / 回答 / 满意度）
- [ ] 建一个数据回流 pipeline：bad case 自动入库 → 人工标注 → 补进知识库
- [ ] 写一个简单的效果分析报告

**Checkpoint**
- 有数据回流机制
- 有效果度量指标

---

### Week 23–24：产品化 + 部署

**编码任务**
- [ ] 给客服 Agent 加完整 UI（Web 页面）
- [ ] 部署到 VPS（用 Docker）
- [ ] 加监控（请求量 / 错误率 / 延迟）
- [ ] 写一份产品文档：用户是谁 / 解决什么问题 / 成本结构

**Checkpoint（Phase 5 Exit Criteria + 最终）**
- ✔ 客服 Agent 可部署、可监控
- ✔ 有成本控制
- ✔ 有数据闭环
- ✔ 能独立做 AI SaaS 原型

---

## 10. 每周复盘模板

每周日完成，存入 `learning-log.md`：

```
## Week N（日期范围）

### 本周完成
- 学了什么
- 写了什么代码
- 遇到什么问题

### 知识缺口
- 哪里卡住
- 哪些概念没理解

### 对照观察（微调 A）
- 用 fundamentals 解释了哪个已部署系统

### 下周计划
- 具体任务

### Exit Criteria 是否达成
- ✔ / ✗ + 原因
```

---

## 11. 资源清单汇总

### Phase 1
- Python Crash Course（Eric Matthes）
- Automate the Boring Stuff with Python
- Harvard CS50P（视频）
- Computer Networking: A Top-Down Approach

### Phase 2
- Designing Data-Intensive Applications（DDIA）
- FastAPI 官方文档
- CMU 15-445（可选）

### Phase 3
- Karpathy「Let's build GPT」（YouTube，必做）
- Andrew Ng ML Specialization（Coursera）
- Jay Alammar「Illustrated Transformer」
- 「Attention Is All You Need」论文

### Phase 4
- FAISS / ChromaDB 文档
- ReAct 论文
- OpenAI / Claude API 文档

### Phase 5
- Chip Huyen《Designing Machine Learning Systems》

---

## 12. 严格禁忌（防止退回 vibe coding）

学习阶段（Phase 1–3）：
- 禁止用 AI 生成练习代码
- 禁止跳过手写步骤
- 卡住时先查文档，再问 AI「解释概念」而非「写代码」

工程阶段（Phase 4–5）：
- RAG / Agent 必须先手写一遍不用框架，再用框架
- 每段代码必须能解释「为什么这么写」
- AI 可辅助，但核心逻辑必须自己理解

---

## END
