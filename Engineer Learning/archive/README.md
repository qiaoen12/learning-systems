# 历史快照说明

版本：1.0
整理日期：2026-08-26

本目录只做追溯，**不参与当前执行**。快照保持原文逐字不动，不在这里修订；需要纠错时，在 `../current/` 里写新判断。

默认会话不读本目录。只有三种情况才进来：比较版本、追溯原文措辞、审计这次迁移。

## 1. 已同步快照

| 文件 | 原始来源 | 角色 |
| --- | --- | --- |
| `corpus-first-v3.2-original.md` | `AI student/learning-plan-2026-09-corpus-first.md` | 现行清洁版的逐字源稿，510 行 |
| `learning-plan-final-v2.0.md` | `AI student/learning-plan-final.md` | 被隔离的旧 16 周执行版，844 行 |
| `howto-v1.0.md` | `AI student/frozen/howto.md` | 更早的 16–24 周通用框架，365 行 |

原始来源目录：`/Users/qiaoen/Projects/80-knowledge-data/80-research/AI student/`

## 2. 校验值

以下 SHA-256 在复制后与原文件逐一比对通过，用于确认快照未被改写：

```text
0e11ee13e0e10735d69e41f29e9f509a4e7971aa8f671760bc0164434d48e175  corpus-first-v3.2-original.md
7790fd8b213b75cf60235eaf32eb5635e1492385639b2c15be2ef24f60aff2f8  learning-plan-final-v2.0.md
1df01ac90b83f0e4b55757de49171afe96a51f4110dd18ca7285b1d821e47e98  howto-v1.0.md
```

复核命令：

```bash
cd "/Users/qiaoen/Projects/80-knowledge-data/80-research/Engineer Learning/archive"
shasum -a 256 -c CHECKSUMS.txt
```

## 3. 三份快照的关系

```text
howto-v1.0            早期通用框架，16–24 周，四层能力模型
      ↓  被吸收
learning-plan-final   16 周单链路，假设根因是「知识不足」
      ↓  被替代（不是被否证：它只是回答了另一个问题）
corpus-first-v3.2     假设根因是「缺少无法自我欺骗的反馈回路」  ← 现行版来源
```

3.2 原案自身声明与 `learning-plan-final` **并行存在、不覆盖不替代**。本目录选择 3.2 作为现行版，是一次执行决策，不是对旧版的技术否证。旧版的六条反退化阀门仍被现行版继承，见 `../current/01-guardrails.md` 第 6 节。

## 4. 故意没有同步的材料

以下材料留在原 `AI student/` 目录，需要审计时定向读取，不复制进来。

| 材料 | 位置 | 为什么不复制 |
| --- | --- | --- |
| `QA.md`（1644 行） | `AI student/frozen/QA.md` | 能力盘点原始问答。当前所需事实已压缩进 `../context/learner-profile.md`；全文会挤爆单会话上下文 |
| `learning-plan-codex.md` | `AI student/frozen/` | 不同 AI 生成的对照方案，已被 final 2.0 吸收 |
| `learning-plan-opencode.md` | `AI student/frozen/` | 同上 |
| `learning-plan-融合.md` | `AI student/frozen/` | 同上 |
| `deep-research-report.md` | `AI student/frozen/` | final 2.0 的升级依据，已体现在 final 2.0 里 |
| `learning-systems/`（15 文件，独立 git 仓库） | `AI student/learning-systems/` | 课程与资料索引。现行版明确禁止扩展这类清单 |
| CS2023 知识地图、roadmap.sh 双语方案、翻译批次 | `AI student/docs/` | 同上，属于入口阀门禁止新增的元文档类别 |
| 软件知识地图（md / html / png / pdf） | `AI student/` 根与 `output/` | 同上 |

**这些材料不是垃圾，但它们正是失败模式的证物**：8 周里它们产出了四五千行，而练习代码是 0 行。把它们排除在默认读取路径之外，是本次结构调整的目的之一，不是遗漏。

## 5. 现行版对原案做的非语义调整

`../current/` 是 3.2 原案的重排，**规则语义未改**。为便于审计，以下四处与原文不是逐字对应：

| 处 | 原案 | 现行版 | 原因 |
| --- | --- | --- | --- |
| 重算判据 A 级 | 写「重现 6 个数字」，但只列出 5 项 | 补上 `source_file_count`，凑齐 6 项 | 原文内部计数不一致；manifest 里除 `canonical_sha256`（属 D 级）外恰好 6 个数字 |
| 入口阀门触发条件 | 「`corpus-guard` 连续 7 天没有 commit」 | 「产生第一个 commit 之后，连续 7 天没有新 commit」 | 原文在仓库尚不存在时无法判定触发 |
| 门内阀门六条 | 只写「原有六条继续保留有效」，正文不列 | 六条逐条列入 `../current/01-guardrails.md` 第 6 节 | 消除对 `learning-plan-final-v2.0.md` 的运行时依赖，使 `current/` 自足 |
| 「第一天做什么」 | 无 | `../current/03-execution.md` 第 6 节新增 3 步 | 纯操作衔接，不引入新规则 |

其余内容按章节重排：原案 §1–3 → `00-overview.md`；§5、5.1、5.2、6 → `01-guardrails.md`；§7 与九月验收 → `02-milestones.md`；§4、8、9、10、11 → `03-execution.md`。

## 6. 旧目录的状态

`AI student/` 本次迁移**未被修改、未被删除**，全部旧材料原样保留。

注意一处已知的历史声明冲突：`AI student/AGENTS.md` 仍写着「当前执行版路线为 `learning-plan-final.md`」。那句话在本次切分后已过期。以本目录 `../README.md` 的版本边界为准。
