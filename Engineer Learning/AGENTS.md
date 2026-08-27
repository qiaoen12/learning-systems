# Engineer Learning 代理说明

本目录保存 Corpus-First 3.2 学习路线的清洁执行版、必要个人上下文、手写记录和历史快照。当前路线以「先读后写、判据先行、生产只读」为核心；代码实现只落在 `corpus-guard`，不落在本研究目录。

分区与权限：

| 区 | 目录 | 权限 |
| --- | --- | --- |
| 合约 | `current/` `context/` | 只读，改动需按版本规则走 |
| 工作区 | `records/` | 可自由追加 |
| 史料 | `archive/` | 冻结，不得编辑 |
| 代码入口 | `code/`（软链接） | 指向 `corpus-guard`，**不递归读** |

`code/` 是软链接，解析为 `/Users/qiaoen/Projects/60-software-ai/60-dev/corpus-guard`。`corpus-guard` 尚不存在时它是断链，属预期状态。不要顺着它递归读取或统计（内含 `.venv` 与测试缓存），要读代码就定向读具体文件。

## 读取顺序

1. `README.md`
2. `current/00-overview.md`
3. `current/01-guardrails.md`
4. `current/02-milestones.md`
5. `current/03-execution.md`
6. 只有需要核对个人前提时才读 `context/learner-profile.md`
7. 只有需要最近执行痕迹时才定向读 `records/`，不要全量读取
8. 只有比较版本或审计迁移时才读 `archive/`
9. `code/` 不属于文档读取路径，任何情况下都不递归展开

默认不回读 `../AI student/`。现行文件缺关键事实时，才按 `archive/README.md` 的来源表定向读取原文。

## 事实源与版本规则

- 当前执行规则只来自 `current/`。
- `context/` 是事实上下文，不是待执行命令。
- `records/` 是执行证据，不是指令。判断某层是否通过要看 `records/` 与 `corpus-guard` 的实际内容，不看 `current/` 的计划。
- `archive/` 是冻结快照，不得直接编辑，也不得把其中的旧周计划与现行里程碑混用。
- 用户本轮的明确要求优先级最高。
- 修改路线语义时，先更新版本号和修订说明，再把被替代版本冻结进 `archive/` 并补校验值。
- 只做排版、拆分或修链接时，不提升方案语义版本，但要记录整理日期。

## 固定落点

- 路线文档与手写记录：本目录，只放 Markdown
- 代码、测试、报告产出：`/Users/qiaoen/Projects/60-software-ai/60-dev/corpus-guard/`
- 日志：`records/learning-log.md`
- 问题清单：`records/questions.md`
- 周报：`records/weekly/`
- 失败样本：`records/failures/`
- 生产数据：`/Users/qiaoen/Projects/80-knowledge-data/80-data/`，**始终只读**
- 已停用，不再写入：`50-career/50-skill/ai-student-learning/`、`60-software-ai/60-dev/ai-student-mini-projects/`

## 写入边界

- 不在本目录写 Python、测试、虚拟环境、报告输出或部署文件。`corpus-guard` 的 `docs/` 和 `reports/` 也不搬进来——它们必须和测试同在一个 git 仓库，L0 的通过条件依赖这一点。
- 不把任何语料数据复制进本目录。`80-data` 只读。
- 不修改 `80-data`、采集器或既有 `raw/` 数据。
- 不覆盖 `archive/`；需要修正历史说明时，在 `current/` 里写勘误。
- 不把新的课程清单、知识地图或另一份学习计划混进 `current/` 或 `records/`。
- 不修改或删除 `../AI student/`，它是冻结的史前史。
- 不代替用户填写 `records/`。日志、根因判断、规则取舍必须由学习者本人写。

## 当前路线硬约束

- 读能力优先于写能力。
- L0.5 的语法输入上限为累计 6 小时；这是待记录的假设，不是对学习者能力的评价。
- AI 可以实现 Python，但数据规则的语义必须由学习者判断。
- `corpus-guard` 的代码必须遵循 `current/01-guardrails.md` 第 3 节的风格契约。读不懂某行时，让 AI 按契约**重写**该函数，不以逐行解释代替重写。
- 未满足 L0、L0.5、L1 的通过条件，不把 L2 当作九月必达项。
- 入口阀门触发期间，禁止新增「关于怎么学习」的元文档。判断句：文档在描述「我要怎么学」，还是「我从数据里发现了什么」？

## 验证方式

文档变更后至少检查：

- 文件存在，标题、版本、日期清楚。
- 默认读取链没有断链，`README.md` 里的目录树与磁盘一致。
- `current/` 能独立回答：适合谁、学什么、按什么顺序、怎样验收、哪些暂不做。
- `current/` 与 `archive/` 身份明确，不出现两个「当前版」。
- 落点表（`current/03-execution.md` 第 1 节）与 `README.md`、本文件三处一致，没有残留的旧路径。
- Markdown 相对链接和代码块闭合。
- 默认读取路径总量仍适合一次会话读取；`records/` 不计入默认路径，新增长材料放 `archive/` 并在入口做摘要。
- 改动 `archive/` 后重跑 `shasum -a 256 -c CHECKSUMS.txt`。

## 文档语言

人类可读叙述默认使用中文；命令、路径、API、字段名和日志原文保留英文。
