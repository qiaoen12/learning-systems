# AI Engineer / AI Startup Engineer Learning System

Version: 1.0  
Mode: Execution-first (Project Driven + Systemic Knowledge Injection)

---

# 0. 核心目标（Non-Negotiable）

在 16~24 周内完成：

## 🎯 能力目标
- 能独立设计 AI 系统（RAG + Agent + API）
- 能理解并实现 Transformer 基本结构
- 能构建可扩展后端系统（高并发 + 状态管理）
- 能做 AI 产品原型（可变现）

## 🎯 产出目标（必须完成）
- 1 × RAG 知识库系统
- 1 × AI Agent 系统（带工具调用）
- 1 × API 后端系统（FastAPI）
- 1 × Mini AI Product（可部署）

---

# 1. 学习原则（非常重要）

## ❌ 禁止行为
- 不允许“纯看书不做项目”
- 不允许“只学课程不写代码”
- 不允许“无限扩展工具栈”

## ✔ 强制原则
- 70% 项目驱动
- 20% 定向学习
- 10% 回顾与优化

---

# 2. 系统结构（你要构建的能力模型）

AI Engineer =

## Layer 1: Computer Systems
- OS
- Network
- Database

## Layer 2: Backend Engineering
- API
- Concurrency
- System Design

## Layer 3: AI Core
- Transformer
- Embedding
- Training / Inference

## Layer 4: AI Engineering
- RAG
- Agent
- Tool Calling

## Layer 5: Product Layer
- Workflow design
- UX for AI systems
- Cost / latency optimization

---

# 3. Phase 1 — 编程 + 系统底座（Week 1–3）

## 🎯 Goal
建立“能写工程代码 + 看懂系统”的能力

---

## 3.1 Python工程能力

### 学习资源
- Python Crash Course
- Automate the Boring Stuff

### 必做任务
- FastAPI写一个API服务
- 实现：
  - GET/POST
  - JSON处理
  - 文件读写

---

## 3.2 网络基础

### 必学内容
- HTTP / HTTPS
- TCP三次握手
- REST API

### 书
- Computer Networking: A Top-Down Approach

### 必做任务
- 手写一个HTTP client
- 用Python模拟请求链路

---

## 3.3 操作系统基础

### 书
- OSTEP

### 必学
- 进程/线程
- 内存管理
- 文件系统

### 必做任务
- 写一个简单并发程序（thread pool）

---

## Phase 1 Exit Criteria

✔ 能写 API  
✔ 能解释 HTTP / TCP  
✔ 能写简单并发代码  

---

# 4. Phase 2 — 后端系统工程（Week 4–7）

## 🎯 Goal
构建“可扩展系统思维”

---

## 4.1 核心书

- DDIA（重点章节）

## 必读部分
- Chapter 1–2（基础）
- Replication
- Partitioning
- Consistency

---

## 4.2 系统能力

### 必做项目
- 用户系统（auth + API）
- 数据存储（SQLite → PostgreSQL）
- 简单缓存系统（Redis）

---

## 4.3 并发与性能

### 必学
- async / await
- event loop
- request queue

---

## Phase 2 Exit Criteria

✔ 能设计后端系统  
✔ 能理解数据一致性  
✔ 能优化 API 性能  

---

# 5. Phase 3 — AI基础（Week 8–11）

## 🎯 Goal
理解 Transformer 本质

---

## 5.1 Transformer核心

### 必学
- Attention
- Q/K/V
- Tokenization

### 必看
- Karpathy GPT-from-scratch

---

## 5.2 深度学习基础

- Andrew Ng ML course
- Embedding concept

---

## 必做任务

- 用PyTorch实现mini Transformer
- 手写 embedding lookup
- 简单 next-token prediction

---

## Phase 3 Exit Criteria

✔ 能解释 Transformer  
✔ 能手写 attention  
✔ 能理解 embedding  

---

# 6. Phase 4 — AI工程（Week 12–16）

## 🎯 Goal
构建AI应用系统

---

## 6.1 RAG系统

### 必学
- chunking
- embedding search
- vector DB

### 工具（仅辅助）
- FAISS
- Chroma

---

## 必做项目
- PDF知识库问答系统
- 支持多文档
- 支持引用来源

---

## 6.2 Agent系统

### 必学
- ReAct pattern
- tool calling
- memory

---

## 必做项目
- 多工具AI Agent
- 支持：
  - 搜索
  - 文件读取
  - API调用

---

## Phase 4 Exit Criteria

✔ 能写RAG  
✔ 能写Agent  
✔ 能组合工具链  

---

# 7. Phase 5 — AI产品系统（Week 17–24）

## 🎯 Goal
进入“可创业级能力”

---

## 7.1 产品系统设计

### 必学
- prompt routing
- cost control
- latency optimization

---

## 7.2 系统设计

- 多agent协作
- workflow engine
- state machine

---

## 7.3 最终项目（必须）

### AI Product MVP

必须包含：
- RAG
- Agent
- API系统
- UI（简单即可）

---

## 7.4 可选方向

- AI客服系统
- AI知识库系统
- AI研究助手

---

# 8. 每日执行结构（非常关键）

## Weekday (3–5h/day)

- 1h 学习（书/视频）
- 2h 编码
- 1h debug / 优化

---

## Weekend

- 完整项目迭代
- 系统重构
- 写总结

---

# 9. 强制复盘机制

每周必须输出：

## 周报模板
- 本周完成系统
- 遇到的技术问题
- 对应知识缺口
- 下周改进点

---

# 10. 成功标准（最终）

你完成后应该具备：

## 技术能力
- AI系统设计能力
- 后端系统能力
- LLM工程能力

## 产品能力
- AI产品从0到1
- MVP快速构建
- 系统扩展能力

## 创业能力
- 能独立做AI SaaS原型
- 能判断产品技术可行性

---

# END