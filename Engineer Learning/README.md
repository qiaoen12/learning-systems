# Engineer Learning

结构版本：1.1
初始化日期：2026-08-26
当前执行方案：Corpus-First 3.3
最近修订：2026-08-26（3.3，修 10 处，见 `archive/README.md` 第 7 节）
起跑日期：2026-09-01

AI 工程学习路线的**唯一现行根目录**。分四种角色，与 `AGENTS.md` 的权限表一一对应：

| 角色 | 目录 | 权限 |
| --- | --- | --- |
| 合约 | `current/` `context/` | 只读。它规定你要做什么、怎么验收 |
| 工作区 | `records/` | 天天写。日志、问题清单、周报、失败样本 |
| 史料 | `archive/` | 冻结，不执行也不编辑 |
| 代码入口 | `code/`（软链接） | 指向 `corpus-guard`，不递归读 |

代码不放在这里，但 `code/` 软链接指向它，所以从这一个目录能进到全部东西。**语料**留在 `80-data/` 且永远只读。

## 最短读取路径

一次新会话默认读 5 个文件，顺序固定，合计 917 行，与 `AGENTS.md` 的读取顺序一致：

1. `README.md` — 本文件：分区、落点、版本边界
2. `current/00-overview.md` — 定位、北极星、三个不变量、manifest 判据
3. `current/01-guardrails.md` — AI 分工、代码风格契约、四级断电测试、三态入口阀门
4. `current/02-milestones.md` — L0 到 L6 各层判据、九月出口验收
5. `current/03-execution.md` — 落点、每日节奏、日志与周报模板、明确不做

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
│   ├── questions.md                 # 语法疑问，L0.5 的诊断指标，不是通过条件
│   ├── weekly/                      # 周报
│   └── failures/                    # 真实失败样本，L1 判据要求 ≥3 个
├── archive/                         # 【史料·不执行】冻结快照
│   ├── README.md                    # 来源表、校验值、修订记录、故意未同步的材料
│   ├── CHECKSUMS.txt
│   ├── corpus-first-v3.2-original.md    # 3.2 原案的逐字源稿
│   ├── v3.2-clean/                      # 被 3.3 替代的 3.2 清洁版四份文件
│   ├── learning-plan-final-v2.0.md      # 被隔离的旧 16 周版
│   └── howto-v1.0.md                    # 更早的通用框架
└── code -> ../../../60-software-ai/60-dev/corpus-guard   # 软链接，不是真目录
```

### 关于 `code/`

它是软链接，解析为 `/Users/qiaoen/Projects/60-software-ai/60-dev/corpus-guard`。作用只是让你从一个目录能进到全部东西，文件本身没有搬。

**`corpus-guard/` 现在还不存在，所以这个链接是断的。** 这是预期状态，不是错误——它在 L0 你亲手 `git init` 的那一刻自动接上。

链接断着不只是一个信号，它还是一个开关：`corpus-guard` 没有第一个 commit 时，入口阀门处于**冷启动锁定**态，唯一允许的学习动作是完成 L0，不许改路线、不许新增元文档、不许进 L0.5。见 `current/01-guardrails.md` 第 5.1 节。

代码不搬进来的理由很具体：L0 的通过条件是「`CORPUS_MAP.md` 存在 + `git init` + 第 1 个 commit」，入口阀门数的也是 `corpus-guard` 的 commit。文档一旦离开那个 git 仓库，这两条判据当场失效。

读取时**不要顺着 `code/` 递归读**——那里面有 `.venv` 和测试缓存。要读代码就直接进 `corpus-guard/` 定向读某个文件。

## 版本边界

| 区域 | 作用 | 能否当作当前指令 |
| --- | --- | --- |
| `current/` | Corpus-First 3.3 的独立可执行版本 | **是** |
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
- `AI student/` 的历史材料未被修改也未被删除。唯一动过的是 `AI student/AGENTS.md`：它原本写着「当前执行版路线为 `learning-plan-final.md`」，会对进入旧目录的代理下达过期指令，所以 3.3 修订时给它加了归档墓碑并把断言改成过去式。理由见 `archive/README.md` 第 6 节。

## 初始化状态

截至 2026-08-26：

- 本文档结构已建立，`current/` 四份文件齐全，无断链，无双当前版。
- **`corpus-guard/` 尚不存在**，所以 `code/` 软链接目前是断的。本次初始化没有替用户启动 L0、创建代码仓库或修改生产数据。
- `records/` 已建好空骨架，模板与命名规则就位，等第一条日志。
- 旧记录目录 `ai-student-learning/`（`learning-log.md` 1 条、`questions.md` 3 项未勾选、两个 README）的内容已按新方案格式重建进 `records/`；旧目录本身未被修改或删除。
- 语料已做一次冷备：`~/Backups/corpus-80-data/2026-08-26/`，29612 个文件的 SHA-256 清单，恢复演练 74/74 通过。**仍是同盘副本，异地副本未做。**
- 方案语义版本为 3.3。结构切分（1.0）未改规则语义；3.3 改了规则语义，逐条见 `archive/README.md` 第 7 节。

**下一步不是继续扩写路线，而是 `current/03-execution.md` 第 6 节的「第一天做什么」。** 在 `corpus-guard` 出现第一个 commit 之前，这是唯一允许的动作。
