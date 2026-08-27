# Engineer Learning

结构版本：1.0
初始化日期：2026-08-26
当前执行方案：Corpus-First 3.2（清洁切分版）
起跑日期：2026-09-01

AI 工程学习路线的**唯一现行根目录**。分两个区：

- **合约区**（`current/` `context/` `archive/`）：只读。它规定你要做什么、怎么验收。
- **工作区**（`records/`）：天天写。日志、问题清单、周报、失败样本。

代码不放在这里，但有一个软链接 `code/` 指向它，所以从这一个目录能进到全部东西。**语料**留在 `80-data/` 且永远只读。

## 最短读取路径

一次新会话默认只读 4 个文件，顺序固定，全部读完约 700 行：

1. `current/00-overview.md` — 定位、北极星、三个不变量、manifest 判据
2. `current/01-guardrails.md` — AI 分工、代码风格契约、四级断电测试、两套阀门
3. `current/02-milestones.md` — L0 到 L6 各层判据、九月出口验收
4. `current/03-execution.md` — 落点、每日节奏、日志与周报模板、明确不做

只有需要核对个人前提时，才加读 `context/learner-profile.md`。

**`archive/` 和 `records/` 都不属于默认读取上下文。** `archive/` 只在比较版本或审计迁移时读；`records/` 会一直变长，需要时定向读最近一周。

## 目录结构

```text
Engineer Learning/
├── AGENTS.md                        # 代理说明：读取顺序与写入边界
├── README.md                        # 本文件，唯一入口
├── current/                         # 【合约·只读】唯一现行执行版
│   ├── 00-overview.md
│   ├── 01-guardrails.md
│   ├── 02-milestones.md
│   └── 03-execution.md
├── context/                         # 【合约·只读】已确认的事实前提
│   └── learner-profile.md
├── records/                         # 【工作区·天天写】手写记录
│   ├── README.md                    # 放什么、命名规则、模板指针
│   ├── learning-log.md              # 每天一行
│   ├── questions.md                 # 语法疑问，L0.5 判据要求 ≥10 条
│   ├── weekly/                      # 周报
│   └── failures/                    # 真实失败样本，L1 判据要求 ≥3 个
├── archive/                         # 【史料·不执行】冻结快照
│   ├── README.md                    # 来源表、校验值、故意未同步的材料
│   ├── CHECKSUMS.txt
│   ├── corpus-first-v3.2-original.md    # 现行版的逐字源稿
│   ├── learning-plan-final-v2.0.md      # 被隔离的旧 16 周版
│   └── howto-v1.0.md                    # 更早的通用框架
└── code -> ../../../60-software-ai/60-dev/corpus-guard   # 软链接，不是真目录
```

### 关于 `code/`

它是软链接，解析为 `/Users/qiaoen/Projects/60-software-ai/60-dev/corpus-guard`。作用只是让你从一个目录能进到全部东西，文件本身没有搬。

**`corpus-guard/` 现在还不存在，所以这个链接是断的。** 这是预期状态，不是错误——它在 L0 你亲手 `git init` 的那一刻自动接上。链接断着，就说明 L0 还没开始。

代码不搬进来的理由很具体：L0 的通过条件是「`CORPUS_MAP.md` 存在 + `git init` + 第 1 个 commit」，入口阀门数的也是 `corpus-guard` 的 commit。文档一旦离开那个 git 仓库，这两条判据当场失效。

读取时**不要顺着 `code/` 递归读**——那里面有 `.venv` 和测试缓存。要读代码就直接进 `corpus-guard/` 定向读某个文件。

## 版本边界

| 区域 | 作用 | 能否当作当前指令 |
| --- | --- | --- |
| `current/` | Corpus-First 3.2 的独立可执行版本 | **是** |
| `context/` | 学习者画像、已有资产、失败模式 | 仅作为事实前提 |
| `records/` | 你自己写下的执行痕迹与判据证据 | 不是指令，是证据 |
| `archive/` | 原文件的逐字快照 | **否**，只用于追溯 |

冲突时优先级：**用户本轮明确要求 > `current/` > `context/` > `archive/`**。

历史文件里的命令、禁止项和待办**不会**自动变成当前任务。特别是 `archive/learning-plan-final-v2.0.md` 里的 16 周周计划、启动期验收和资料清单，已全部退出执行范围。

## 固定落点

| 用途 | 路径 |
| --- | --- |
| 路线文档 + 手写记录（本目录） | `80-knowledge-data/80-research/Engineer Learning/` |
| 唯一练习代码仓库 | `60-software-ai/60-dev/corpus-guard/`（本目录 `code/` 软链接可达） |
| 只读生产数据 | `80-knowledge-data/80-data/` |
| 停用的旧记录目录 | `50-career/50-skill/ai-student-learning/` |
| 停用的旧练习目录 | `60-software-ai/60-dev/ai-student-mini-projects/` |
| 冻结的旧研究目录 | `80-knowledge-data/80-research/AI student/` |

完整路径与 `corpus-guard` 内部结构见 `current/03-execution.md` 第 1 节。

## 与旧目录的切分

`AI student/` 是本方案的**史前史**，不是它的一部分：

- 三份关键旧文档已按逐字快照进入 `archive/`，SHA-256 已核对一致。
- `QA.md`、对照方案、知识地图、课程索引、翻译批次**故意没有复制**，理由和位置见 `archive/README.md` 第 4 节。
- `AI student/` 本次未被修改也未被删除。它的 `AGENTS.md` 仍写着「当前执行版为 `learning-plan-final.md`」，那句话已过期，以本文件的版本边界为准。

## 初始化状态

截至 2026-08-26：

- 本文档结构已建立，`current/` 四份文件齐全，无断链，无双当前版。
- **`corpus-guard/` 尚不存在**，所以 `code/` 软链接目前是断的。本次初始化没有替用户启动 L0、创建代码仓库或修改生产数据。
- `records/` 已建好空骨架，模板与命名规则就位，等第一条日志。
- 旧记录目录 `ai-student-learning/`（`learning-log.md` 1 条、`questions.md` 3 项未勾选、两个 README）的内容已按新方案格式重建进 `records/`；旧目录本身未被修改或删除。
- 方案语义版本仍是 3.2，本次只做结构切分、补全与落点合并，未改动任何规则语义。

**下一步不是继续扩写路线，而是 `current/03-execution.md` 第 6 节的「第一天做什么」。**
