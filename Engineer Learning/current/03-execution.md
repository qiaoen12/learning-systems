# Corpus-First 3.2：落点、节奏与模板

方案版本：3.2
结构版本：clean-1

## 1. 固定落点

只有两个活动落点：**手写的东西写这里，代码写 `corpus-guard`。**

| 用途 | 路径 | 写入权限 |
| --- | --- | --- |
| 路线文档（合约区） | `80-research/Engineer Learning/current/` `context/` `archive/` | **只读**，执行期间不改 |
| 日志 / 问题 / 周报 / 失败样本 | `80-research/Engineer Learning/records/` | 可写，天天写 |
| 唯一练习代码仓库 | `60-software-ai/60-dev/corpus-guard/` | 可写 |
| 代码入口软链接 | `80-research/Engineer Learning/code/` → 上一行 | 链接本身不用管 |
| 生产数据 | `80-knowledge-data/80-data/` | **只读，永不写入** |
| 旧练习目录 | `60-software-ai/60-dev/ai-student-mini-projects/` | 停用，不删除 |
| 旧记录目录 | `50-career/50-skill/ai-student-learning/` | 停用，已迁入 `records/` |

`ai-student-mini-projects/` 停用后不再往里放东西。它的空 `.venv` 保留为证据。

`ai-student-learning/` 的内容已按新方案格式重建进 `records/`，那条 2026-06-30 的历史日志保留在 `records/learning-log.md` 末尾存证。旧目录不再写入。

### 1.1 手写记录放哪里

```text
Engineer Learning/records/
├── learning-log.md              # 每天一行，格式见第 3 节
├── questions.md                 # 语法疑问，L0.5 判据要求 ≥10 条
├── weekly/week-NN.md            # 周报，格式见第 4 节
└── failures/YYYY-MM-DD-<现象>.md # 真实失败样本，L1 判据要求 ≥3 个
```

### 1.2 代码和产出放哪里

`corpus-guard` 里的文档不搬进研究目录，因为它们必须和测试放在一起，而且 **L0 的通过条件是 `CORPUS_MAP.md` 加第 1 个 commit**——文档不在 git 里，这条判据就不成立。

`Engineer Learning/code/` 是指向它的软链接，只为省一次路径切换。**`corpus-guard` 建起来之前这个链接是断的，这正好是「L0 还没开始」的可见信号。**

```text
corpus-guard/
├── docs/CORPUS_MAP.md              # L0 产物
├── docs/DECISION_LOG.md            # 判断力证据，贯穿全程
├── docs/DISCORD_DATA_CONTRACT.md   # L2 产物
├── reports/integrity-<日期>.md     # L1 产物
└── tests/                          # pytest 裸函数，一条规则一个函数
```

## 2. 每日节奏

| 时间块 | 用途 | 规则 |
| --- | --- | --- |
| 60–90 分钟主块 | 写规则 **或** 读/改代码 | 一次只做一件，不混 |
| 5–15 分钟碎片 ×10 | **读 `corpus-guard` 里的一个函数** | 不学新概念、不看教程 |
| 15 分钟收口 | 写一条日志 | 固定四行 + 一个数字 |

碎片时间的用途和旧方案不同。旧方案让碎片时间复习术语，本方案让它读代码——每次只读一个函数，读完能说出「拿什么、还什么」就够。这是零基础也能做满 5 分钟的动作，而且它直接服务于「接管」这个目标。

**读的对象必须是 `corpus-guard`**（按代码风格契约写的），**不是**现有那批工具代码。后者是 L3 的目标，现在读只会挫败。

## 3. 日志模板

追加到 `learning-log.md`，固定一行四段：

```text
日期 | 层 | 今天动了什么（一句） | 数字（用例数 / 通过率 / 覆盖频道数）
```

## 4. 周报模板

写进 `weekly/`。旧方案的八小节模板取消——它从未被填写过一次。

```markdown
## Week N（日期范围） · 当前层：Lx

1. 本周判据前进了什么：
2. 卡住的一处，根因是：
3. 哪一步明显是 AI 帮我兜过去的：
4. 语料这周多了什么，使它更接近可用于研究或产品：

数字：pytest 通过 __ / __ ，覆盖 __ 个频道，断电测试最高级 跑 / 读 / 修 / 写 / 未做，语法输入累计 __ 小时
入口阀门：未触发 / 已触发（触发日期：）
```

第 4 行是为了不让四个月的数据工程和创业目标断掉联系。它只要一句话，**不允许展开成文档**——展开就触发入口阀门第 2 条。

## 5. 明确不做

- 不改采集器、不改 `raw`、不重新采集、不动生产数据。
- **不修 Python 课程。** 语法输入 6 小时硬上限，当手册查，不当课程修。不做 CS50P、不做 Python Crash Course、不建教材清单。
- 不学 `class`、装饰器、类型注解、async、推导式、包管理原理。写代码的 AI 也不许用（见代码风格契约）。
- 不上 FastAPI、不上 Docker、不上 Redis、不做部署（L4 之前都不需要服务端）。
- 不系统性读 OSTEP、DDIA 第 5-7 章、计算机网络第 2 章。需要时按问题查。
- 不碰 Transformer 内部原理。CS336 那条线是给要做模型的人准备的，2026 年做 AI 产品的分水岭是 eval、context、失败模式和成本。想看，等 L5 之后当支线。
- 不做 fine-tuning、不做多 Agent、不做 LangChain。
- 不新建任何规划文档、知识地图、课程清单、翻译工程。

## 6. 第一天做什么

不需要再读任何路线文档。按顺序：

1. 打开 `02-milestones.md` 的 L0 一节。
2. 挑 1 个 Discord 频道，先预测再运行第一条命令。
3. 把预测错的地方写进 `learning-log.md`。

`corpus-guard/` 此刻还不存在，建它是 L0 通过条件的一部分（`git init` + 第 1 个 commit）。

## 7. 一句话总结

旧方案要你证明「我学完了这一周」。本方案要你证明一件更难也更有用的事：

> 我能独立重算出我自己的数据，所以采集器可以被淘汰，语料不会。
