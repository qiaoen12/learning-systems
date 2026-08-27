# Corpus-First 3.2：定位、北极星与边界

方案版本：3.2
结构版本：clean-1
原方案作者：Claude Opus 5
原方案日期：2026-08-26
起跑日期：2026-09-01
状态：当前执行版，尚未开始执行

## 1. 一句话方向

> 先建立读数据、读代码、验证结果的能力，写代码能力在修 bug 和重算数据的过程中长出来。

目标不是先「学完 Python」，而是接管已经在依赖的系统，让原始数据比采集代码活得久。

## 2. 为什么换掉旧路线

旧版 `learning-plan-final-v2.0` 假设根因是「知识不足」，于是给出更好的知识摄入顺序（16 周 Python → HTTP → FastAPI → SQLite → RAG → Agent）。从 2026-06-30 启动到 2026-08-26，即 8 周后的实际产出：

| 旧计划要求的产物 | 实际 |
| --- | --- |
| 周报 | 0 份（只有 README） |
| 失败样本 | 0 个（只有 README） |
| 练习代码 | 0 行（只有空 `.venv`） |
| 学习日志 | 1 条，停在启动日 |
| 待确认项 | 3 项全部未勾选 |

同期实际产出约四五千行规划与地图类文档：软件知识地图、CS2023 知识地图、roadmap.sh 双语方案、翻译批次、`learning-systems/` 15 个文件。

结论不是课程质量不够，而是缺少一个无法自我欺骗的反馈回路。本方案改换假设：**先造回路，知识顺序交给失败去决定。**

旧路线的三个结构性缺陷，本方案逐条针对：

1. **所有阀门都装在门内。** 旧的反退化阀门六条全部预设「你已经在写代码」，检测不到「根本没进门」。本方案增加入口阀门，见 `01-guardrails.md` 第 5 节。
2. **把唯一的真实优势当噪音删掉了。** 旧路线把已有真实系统降级为「可选映射，不作为通过条件」，结果是一个已在运维真实数据平台的人被要求花四周写词频统计。本方案把真实资产升级为唯一训练场。
3. **顺序与行业实际顺序相反。** eval 在 Week 11、产品判断在 Week 14，两个真正的分水岭放在 70% 和 88% 处，按现实完成率永远不会到达。本方案把判据放在第一天。

## 3. Python 零基础这个前提怎么处理

事实（2026-08-26 确认）：**学习者尚未开始学 Python，现有全部代码和工具都是他指导 AI 实现的。**

这不改变方案方向，但改变第一层的内容和顺序，理由是一个容易被忽略的区分：

> **读代码和写代码是两种能力，读比写更早可得。而「接管 AI 写的代码」需要的第一能力是读，不是写。**

所有现成入门路径（CS50P、Python Crash Course，包括旧路线的 Week 1）都从「写」开始教。对一个手上已堆着大量 AI 生成资产、并且要靠这些资产吃饭的人，这个顺序是错的：他每天的实际动作是「看一段 AI 给的代码，判断它对不对」，不是「从空文件开始写」。所以本方案先建读能力（L0.5），写能力在 L1 到 L2 修 bug 的过程里长出来。

**一条已被核查推翻的想法。** 原打算让学习者直接读自己仓库里的 56 个测试文件当 Python 读本——自己的数据、自己的代码，纸面上是完美教材。核查后不成立：最小的那个文件 `reddit/tools/reddit-rpa-assistant/tests/test_collection_scope.py` 只有 56 行，但含 `importlib.util.spec_from_file_location` 动态模块加载、`unittest.TestCase` 加 `setUp`/`tearDown` 生命周期、`-> None` 类型注解、`Path(__file__).resolve().parents[1]` 这种链式调用加魔术属性、以及直接内联在函数调用里的多层嵌套字面量。这是能力不错的 Python，不是零基础可读的 Python。

这条死路推出一个更重要的结论，它是整个方案能否成立的前提，不是风格偏好：

> **如果 AI 用同样的风格写 `corpus-guard`，方案当场失效。** 因为你会再次得到一套自己读不懂的代码，只是这次它叫「学习成果」。

所以 `01-guardrails.md` 第 3 节的代码风格契约是硬约束，优先级高于优雅、简洁和性能。现有那批密集代码不作废，它变成 L3 的目标：能读懂过去的自己和 AI 写的密集代码，是个里程碑，不是起点。

## 4. 北极星

> **当采集器全部被淘汰后，仅凭 `raw/` 目录和 manifest，能否完整重建出 `clean/` 层？**

能，语料就是耐用资产；不能，语料的价值就被锁死在一套你不理解的代码里。整个方案就是把这个「能」一层层证明出来。

## 5. 三个不变量

任何一层都不得违反。

### 5.1 只读生产

学习仓库永不写入 `/Users/qiaoen/Projects/80-knowledge-data/80-data/`。所有产出（报告、数据库、迁移结果、测试产物）写进学习仓库自己的目录。这条保证「补充软件和认知的过程中不去碰太多实际项目」这个约束不被破坏，同时保留真实数据和真实失败。

### 5.2 判据先行

每一层先有可运行的判据，再有实现。判据可以是 pytest、一次集合相等、或一个可复核的数字。自然语言的验收标准可以自我欺骗，pytest 不行。「感觉是对的」不算验收。

### 5.3 双重产出

每个练习必须同时产出两样东西：

- **能力证据**：你能运行、能解释、能定位、能修复；
- **语料永久资产**：校验规则、报告、数据合约、恢复证据或迁移测试。

只能证明你学会了、对语料没留下任何东西的练习，不进主线。这条保证即使学习中断，做过的部分也不作废。

## 6. 唯一载体

唯一练习代码仓库：

```text
/Users/qiaoen/Projects/60-software-ai/60-dev/corpus-guard/
```

它是一个**影子校验器**：只读生产数据，只往自己目录写。第一天 `git init`，每一层都是给它加一层能力，不是换一个新练习项目。

完整落点清单见 `03-execution.md` 第 1 节。

## 7. 事实源边界

可作为输入事实源（绝不写入）：

```text
80-data/discord/<server>/raw/<channel-slug>/canonical_messages.ndjson
80-data/discord/<server>/raw/<channel-slug>/canonical_manifest.json
80-data/discord/<server>/raw/<channel-slug>/snapshots/...
80-data/discord/<server>/rules/channel_registry.json
80-data/reddit/VR-XR/raw/<subreddit-slug>/<post-id>--<url-slug>/
80-data/reddit/VR-XR/rules/subreddit_registry.json
```

不作为事实源：

- `clean/`、`translated/`、`insights/`：派生层；
- `reddit/VR-XR/frozen/`：原方案已标记为不可信；
- `.discord-rpa-control/`、`.reddit-rpa-control/`：运行时状态。

## 8. manifest 就是标准答案

Stanford CS336 的教学机制是不提供脚手架代码，但提供单元测试和 adapter 接口——学生拿到的第一样东西是判据。语料里已经有一份现成的、自己生成的标准答案。

以 `discord/Unseen Reality/raw/discussions/canonical_manifest.json` 为例，它声明：

```text
source_file_count                  = 28    （每个源文件都带 path / message_count / sha256）
records_read                       = 9930
duplicate_records_removed          = 4923
synthetic_channel_headers_excluded = 0
anonymous_records_excluded         = 0
unique_message_ids                 = 5007
canonical_sha256                   = <输出文件的哈希>
```

以及一条写成散文、但精确到可重新实现的去重规则：

```text
record_selection: prefer higher content/author/timestamp/content-length/attachment quality;
                  break ties with newer last_seen_at
last_seen_at:     maximum valid source value per message_id
attachments:      union across duplicate records
edited:           true when true in any duplicate record
```

于是有了一个无法自我欺骗的判据：

> **从那 28 个源文件出发，用你自己写的代码，独立重算出这个 canonical。**

**已核实的前置条件**（2026-08-26，只读核对）：28 个源文件全部存在于磁盘；抽检 3 个源文件的实际 SHA-256 与声明一致；28 个 `message_count` 求和恰好等于 `records_read = 9930`；`canonical_messages.ndjson` 的实际 SHA-256 与 `canonical_sha256` 一致。这个重算任务在原理上可完成，不是陷阱。

### 8.1 重算判据必须是阶梯，不能是字节级哈希

已核过字节格式：这个文件里存在 **4 种不同的 key 顺序**，且不是字母序——`edited` 和 `last_seen_at` 在一部分行里被追加到末尾，`author_inferred_from_message_id` 也不在字母位。这说明 key 顺序编码的是合并代码触碰字段的先后，字节级重现等于复刻原代码的变量赋值顺序。那是序列化琐事，教不到任何东西。所以判据分四级：

| 级 | 判据 | 性质 |
| --- | --- | --- |
| A | 重现 6 个数字（`records_read`、`duplicate_records_removed`、两个 excluded、`unique_message_ids`、`source_file_count`） | 必须达到 |
| B | 重现那 5007 个 `message_id` 的**集合**，逐个相等 | 必须达到 |
| C | 每条记录逐字段相等（比较**解析后的对象**，不比较字节） | 必须达到，这是真正的学习目标 |
| D | 字节级 SHA-256 相等 | 选做，不达到不影响通过 |

C 级通过就说明理解了那条去重规则的每一个细节。D 级达不到是正常的，且原因本身是个发现。

### 8.2 那 4 种 key 顺序是语料的真实性质

它不是你的 bug：**这个 canonical 在记录层面是规范的，在字节层面不是。** 重新跑一次合并，语义相同的数据可能产生不同的字节流和不同的 `canonical_sha256`，于是哈希无法用于跨次比对。这是北极星直接关心的问题，也是 L6 的一个具体任务：定义一个字节稳定的序列化（key 排序固定、分隔符固定），让语料变成可跨次哈希比对的。发现它，比重现它有价值得多。

### 8.3 这个判据为什么可靠

- 它有唯一正确答案，且答案不是别人给的，是自己的数据生成的。
- 它无法靠 AI 蒙过去。AI 可以帮写代码，但 A/B/C 三级对不上就是对不上。
- 它有天然的难度阶梯。约 60 个 Discord 频道加 49 个 subreddit，每一个都是独立实例。`discussions` 频道的两个 excluded 都是 0，别的频道不一定；forum 类频道结构更复杂。
- 它的产物对语料永久有益：一个独立于采集器的校验器，意味着采集器被淘汰时语料不会跟着失效。

## 9. 当前范围

- 九月的通过范围是 **L0 + L0.5 + L1**。
- L2 是加分项，顺延到十月不叫落后。
- L3 到 L6 只有在前层通过后按需展开，不按日历预排。
- 进入下一层只看通过条件，不看「计划到了第几周」。

## 10. 继续读什么

| 文件 | 回答什么问题 |
| --- | --- |
| `01-guardrails.md` | AI 和我怎么分工、代码要写成什么样、什么时候必须停 |
| `02-milestones.md` | 每一层做什么、判据是什么、九月怎么验收 |
| `03-execution.md` | 东西放哪里、每天怎么排、日志和周报怎么写、什么不做 |
