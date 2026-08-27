# 任务 2：roadmap.sh 本地部署与中英双语化执行文档

状态：待独立线程执行  
版本：1.0  
制定日期：2026-07-14  
上游仓库：`https://github.com/nilbuild/developer-roadmap`  
文档语言：中文  

## 1. 任务目标

把 `nilbuild/developer-roadmap` 官方源码克隆到本地，完成可复现的本地部署，并增加独立的简体中文注释层。

最终页面保持英文为主文本，在英文标题、节点名称和正文附近显示字号更小、层级更弱但仍清晰可读的中文注释。

本任务与 CS2023 知识骨架完全独立：

- 不把 roadmap.sh 的分类导入 CS2023 图谱。
- 不修改 CS2023 图谱项目的数据。
- 不重新设计 roadmap.sh 的知识分类。
- 只在 roadmap.sh 自身项目中完成本地运行和双语显示。

## 2. 目标目录与交付物

目标项目目录：

`/Users/qiaoen/Projects/60-software-ai/60-app/developer-roadmap-bilingual/`

正式交付至少包括：

- 可运行的上游源码本地副本。
- 项目级 `AGENTS.md`。
- 独立本地分支，例如 `local/bilingual-zh`。
- 中英文双语渲染机制。
- 与上游内容解耦的简体中文翻译目录。
- 术语表和翻译规范。
- 翻译覆盖率与过期检测脚本。
- 本地运行说明。
- 构建、测试和视觉验收结果。
- 上游基准 commit 记录。

建议新增或维护：

```text
AGENTS.md
docs/local-bilingual-runbook.md
docs/translation-style-guide.md
src/i18n/zh-CN/
scripts/i18n/audit-translations.*
scripts/i18n/extract-translatable-content.*
UPSTREAM_COMMIT.txt
```

实际路径必须服从上游现有架构；在完成代码所有权审计前，不得先创建一套平行框架。

## 3. 范围定义

### 3.1 必做范围

- 克隆并固定上游版本。
- 按上游 README 成功运行原始英文版。
- 识别所有一手文本来源和渲染入口。
- 建立英文原文为 canonical、中文为 annotation 的翻译数据模型。
- 双语化平台 UI、官方路线入口、路线节点和主题详情。
- 未翻译内容安全回退到纯英文。
- 翻译与上游同步时可检测新增、修改和删除。
- 完成本地生产构建或等价的生产模式运行。
- 默认只绑定本机地址，不对公网开放。

### 3.2 翻译覆盖边界

第一阶段正式覆盖：

1. 平台导航、按钮、提示、状态和错误文案。
2. 官方 Roadmap 标题、简介和分类标签。
3. 官方 Roadmap 画布中的 topic、subtopic、label 和 section 文本。
4. Topic 弹窗或详情页中的标题和第一方正文。
5. FAQ、Get Started 等直接服务学习浏览的第一方说明页面。

以下内容默认保持英文，除非存在稳定翻译键且不增加许可风险：

- 外部资源原始标题。
- 品牌、产品、API、协议和代码标识符。
- 用户生成内容、社区资料、登录账号数据。
- 第三方网页正文。

### 3.3 非目标

- 不修改 roadmap.sh 的知识分类或路线顺序。
- 不把英文原文替换掉。
- 不建设独立后端、账号系统、支付系统或数据镜像。
- 不承诺完全离线运行。
- 不进行公网部署、公开镜像发布、公开 fork 或内容再分发。
- 不提交上游 PR，除非用户在后续单独授权。
- 不用运行时 DOM 扫描或 MutationObserver 粗暴追加中文。

## 4. 许可与发布边界

上游 `license` 当前明确允许个人使用，同时限制把项目内容、图片或项目文件拿到其他媒介重新发布。

因此本任务默认授权边界为：

- 仅在用户本机进行个人使用。
- 可以在本机创建翻译和代码改动。
- 不推送到公开 GitHub 仓库。
- 不发布 Docker 镜像、静态站点、公开下载包或公网服务。
- 不将上游内容复制到另一个知识库。

开始写代码前必须重新读取最新上游 `license` 并记录 commit。若许可证已经变化，以最新文件为准。

如果用户后续要求公网访问、团队共享或内容再发布，立即停止，先完成单独的许可审查和授权确认。

## 5. 已知上游技术事实与复核要求

截至制定本计划时，抽样审查发现：

- 项目使用 Astro、React、Tailwind 和 TypeScript。
- `astro.config.mjs` 使用 `output: 'server'` 与 Node standalone adapter。
- 默认 `PUBLIC_API_URL` 指向 `https://api.roadmap.sh`。
- 上游 README 要求安装 workspace 依赖，并用 `pnpm dev` 启动。
- 没有在抽样源码中发现现成的通用 i18n 层。
- Roadmap JSON 同时包含语义节点、画布坐标、分区、连线和装饰元素。

执行线程必须在最新 commit 上重新核验这些事实，不能假设它们永久不变。

## 6. “本地部署”的准确含义

本任务默认交付：

> 前端和 Node 服务运行在本机，但允许只读访问上游公开 API 和外部学习资源。

这不等于完全离线。

执行线程必须在原始英文版运行后完成网络依赖审计，并列出：

- 页面渲染依赖哪些远程 API。
- 哪些 Roadmap 数据随源码存在，哪些来自远程服务。
- 登录、进度、AI 功能和用户数据依赖哪些后端。
- 分析、指纹、支付、广告或遥测请求。
- 远程服务不可用时的表现。

默认关闭或移除本地浏览不需要的分析、指纹、支付和遥测能力。

若用户要求所有内容、API、账号和数据完全离线，视为新的大型后端镜像任务；本线程必须停止并请求重新定范围。

## 7. Git 与上游同步策略

### 7.1 克隆和版本固定

建议流程：

```bash
cd /Users/qiaoen/Projects/60-software-ai/60-app
git clone https://github.com/nilbuild/developer-roadmap.git developer-roadmap-bilingual
cd developer-roadmap-bilingual
git remote rename origin upstream
git switch -c local/bilingual-zh
git rev-parse HEAD > UPSTREAM_COMMIT.txt
```

命令执行前必须确认目标目录不存在，避免覆盖已有内容。

### 7.2 本地改动原则

- 英文原文和上游 JSON 保持 canonical。
- 翻译数据单独存放，不直接批量改写上游英文。
- 对上游核心组件只做最小接入修改。
- 不提交构建产物、密钥、`.env`、缓存或日志。
- 每个阶段形成小而可验证的本地 commit；是否真正提交由执行线程按用户授权判断，默认可以本地 commit，但不得 push。

### 7.3 后续同步

同步前：

```bash
git fetch upstream
git log --oneline --decorate HEAD..upstream/master
```

翻译审计工具必须能根据原文 hash 识别：

- 新增文本。
- 原文发生变化、中文已过期。
- 原文被删除、翻译成为孤儿。
- 节点 ID 或 Roadmap slug 发生迁移。

不得把“翻译键存在”误判为“翻译仍然有效”。

## 8. 翻译数据架构

### 8.1 核心原则

- 英文是事实源，中文是可选注释。
- 翻译通过稳定 ID 关联，不通过英文字符串模糊匹配。
- 原文改变后，翻译自动标记过期。
- 缺少中文时只显示英文，不阻塞页面。
- 不在渲染后扫描 DOM 追加翻译。

### 8.2 翻译键建议

```text
ui.<semantic-key>
roadmap.<roadmap-slug>.title
roadmap.<roadmap-slug>.description
node.<roadmap-slug>.<node-id>.label
content.<resource-id>.title
content.<resource-id>.body
faq.<roadmap-slug>.<item-id>.question
faq.<roadmap-slug>.<item-id>.answer
```

每条翻译至少保存：

```json
{
  "key": "node.computer-science.node-id.label",
  "sourceText": "Operating Systems",
  "sourceHash": "sha256:...",
  "zhCN": "操作系统",
  "status": "reviewed",
  "translatedAt": "2026-07-14",
  "upstreamCommit": "..."
}
```

允许状态：

- `draft`：初译，未复核。
- `reviewed`：已核对术语和语义。
- `stale`：英文改变，需要重译。
- `blocked`：存在歧义或许可问题。

### 8.3 文件组织

根据规模选择按语义拆分，避免单个巨型 JSON：

```text
src/i18n/zh-CN/ui.json
src/i18n/zh-CN/roadmaps.json
src/i18n/zh-CN/nodes/<roadmap-slug>.json
src/i18n/zh-CN/content/<roadmap-slug>.json
src/i18n/zh-CN/faqs/<roadmap-slug>.json
src/i18n/zh-CN/glossary.json
```

若上游已有更合适的数据加载层，应按实际架构调整，但必须保持翻译与英文源解耦。

## 9. 双语渲染规格

### 9.1 视觉层级

- 英文保持原字号、字重和主要颜色。
- 中文显示在英文下方或紧邻位置。
- 中文建议使用英文的 70%–82% 字号，不能低于可读下限。
- 中文使用较弱颜色，但必须达到对比度要求。
- 英文与中文之间保持紧密语义组合，不能看起来像两个独立节点。

示意：

```text
Operating Systems
操作系统
```

### 9.2 统一组件

建立一个集中式双语文本组件或渲染函数，例如：

```text
BilingualText
  ├─ English primary text
  └─ Chinese annotation
```

该组件至少支持：

- 行内与块级模式。
- 单行和多行截断。
- 无中文时回退。
- `aria-label` 或屏幕阅读器顺序。
- 不同表面所需的密度规格。

禁止为每个页面分别拼接中文 `<span>`。

### 9.3 Roadmap 画布节点

这是最高风险区域。中文增加后必须重新考虑：

- 节点真实高度。
- 自动换行。
- 连接点位置。
- 分区边界。
- 节点之间的间距。
- 原始手工坐标是否仍适用。

首选实现顺序：

1. 找到 renderer 接收节点数据的规范化入口。
2. 在进入 renderer 前把中文作为独立字段附加到语义节点。
3. 在节点组件内部渲染中英文。
4. 让测量逻辑使用双语后的真实尺寸。
5. 重新验证边路由、分区和导出。

若上游 `roadmap-renderer` 或 `@roadmapsh/editor` 不允许扩展节点字段，先评估 wrapper、adapter 或本地 patch；不得直接用 DOM 后处理掩盖架构问题。

### 9.4 详情正文

- 英文段落先显示。
- 中文翻译紧随其后并使用较小字号。
- 长正文可以折叠中文，但默认应能发现其存在。
- 代码块、命令、API 名称、URL 和产品名不翻译。
- 外部资源列表默认保留原始标题。

## 10. 翻译规范

### 10.1 术语原则

- 标准中文术语优先，例如 Operating Systems → 操作系统。
- 行业通常保留英文的名词不强行翻译，例如 Kubernetes、Docker、FastAPI。
- 缩写首次出现时可使用“中文（英文，缩写）”。
- 同一术语在全部 Roadmap 中只能有一个首选译法。
- 容易混淆的词必须进入术语表并写出边界。

### 10.2 文体

- 中文注释简短、准确，不增加英文原文不存在的结论。
- 不把翻译改写成教程或营销文案。
- 不翻译代码、字段、命令和 URL。
- 不使用未经验证的中文行业黑话。

### 10.3 质量流程

- 先机器或 AI 辅助初译，状态为 `draft`。
- 按术语表规范化。
- 抽样回译或对照英文检查。
- 技术歧义由人工裁决后改为 `reviewed`。
- 原文改变时自动变为 `stale`。

## 11. 执行阶段

### 阶段 0：目录、规则与许可检查

- 读取 `/Users/qiaoen/Projects/AGENTS.md`。
- 读取 `/Users/qiaoen/Projects/60-software-ai/AGENTS.md`。
- 读取 `/Users/qiaoen/Projects/60-software-ai/60-app/AGENTS.md`。
- 确认目标目录不存在或为空。
- 重新读取上游 README、贡献规则和许可证。
- 明确本地个人使用边界。

验收：无目录冲突，许可证允许当前本地用途。

### 阶段 1：克隆和原版基线

- 克隆完整仓库。
- 记录 default branch 和 commit。
- 创建本地双语分支。
- 按上游文档安装依赖。
- 从 `.env.example` 创建仅本地配置，不写入真实密钥。
- 运行原始英文版。
- 运行最小构建和测试。

验收：未修改源码前，英文版可在本机正常打开；失败则先解决基线，不能进入翻译。

### 阶段 2：运行依赖与隐私审计

- 检查远程 API、分析、指纹、支付、认证和第三方请求。
- 区分本地源码数据与远程 API 数据。
- 禁用本地浏览不需要的遥测能力。
- 记录断网、API 失败和未登录状态。

验收：形成网络依赖表；用户知道该部署是否依赖远程 API。

### 阶段 3：文本与渲染所有权审计

- 枚举 UI 文案来源。
- 枚举 Roadmap 元数据、节点 JSON、内容 Markdown、FAQ 和 API 内容。
- 定位所有主要渲染组件。
- 定位 Roadmap 节点尺寸和连线测量逻辑。
- 统计待翻译字符串数量和稳定 ID 覆盖率。

验收：给出翻译表面、字符串数量、所有者文件和风险，不凭猜测开改。

### 阶段 4：翻译基础设施

- 建立 locale 状态，默认显示 `en + zh-CN annotation`。
- 建立 `BilingualText`。
- 建立翻译目录、类型定义和 fallback。
- 建立源文本 hash、状态和覆盖率审计。
- 为 UI 文案完成第一个端到端样例。

验收：一个集中机制覆盖多个表面；缺少翻译时页面仍正常。

### 阶段 5：Roadmap 画布双语化原型

先只选择三个代表性 Roadmap：

- `computer-science`
- `backend`
- `ai-agents`

完成：

- topic、subtopic、label、section 双语。
- 节点尺寸和连接点重算。
- 桌面和手机检查。
- SVG/PDF/图片导出检查，如果上游支持。

这是架构验证门。三个代表路线全部通过后，才能批量扩展。

### 阶段 6：官方 Roadmap 批量翻译

- 按 Roadmap slug 分批抽取。
- 生成 `draft` 翻译。
- 应用术语表和格式规则。
- 运行重复、缺失、过期和孤儿检查。
- 每批选择高风险术语人工复核。

建议批次：

1. Computer Science、DSA、System Design、Software Architecture。
2. Backend、DevOps、Security、Data Engineering。
3. Machine Learning、AI Engineer、MLOps、AI Agents、AI Product Builder。
4. 语言、框架、数据库和平台专项路线。

验收：覆盖报告明确显示每个 Roadmap 的总字符串、已译、已复核、过期和缺失数量。

### 阶段 7：正文和 FAQ

- 双语化第一方 Topic 正文。
- 双语化 FAQ 与学习入口说明。
- 保留代码和外部资源原文。
- 验证长文本、Markdown、链接和代码块。

验收：中英文语义成对，正文不溢出、不破坏 Markdown。

### 阶段 8：构建、测试和本地生产运行

- 运行格式、类型、构建和上游最小测试。
- 运行新增翻译完整性测试。
- 按实际 Astro standalone 输出启动生产模式。
- 只绑定 `127.0.0.1`，除非用户明确授权局域网访问。
- 编写本地 runbook。

验收：重启后可按文档复现；无密钥进入版本库。

### 阶段 9：视觉、移动端和同步验收

- 首页、Roadmap 列表、三个代表画布、Topic 详情、FAQ 截图检查。
- 验证 1440px、1280px、390px 和 360px。
- 验证长英文、长中文、缩写和无翻译 fallback。
- 模拟一条上游原文变化，确认翻译变为 `stale`。
- 清理缓存、日志和临时产物。

验收：满足第 12 节完成定义。

## 12. 完成定义

全部满足才算完成：

- 上游仓库、commit 和许可证已记录。
- 原始英文基线在修改前已验证。
- 本地开发和生产模式都有可复现命令。
- 服务默认仅绑定本机。
- 英文始终保留为主要文本。
- 中文以较小注释形式显示，字号和对比度仍可读。
- UI、官方 Roadmap 标题、画布节点和 Topic 详情进入统一翻译机制。
- 三个代表 Roadmap 无节点重叠、中文裁切、连接点错位或导出异常。
- 未翻译文本安全回退为英文。
- 每条中文翻译关联稳定 key、原文 hash 和上游 commit。
- 覆盖率报告可列出已译、未译、过期和孤儿翻译。
- 上游原文变化能使相应翻译变为 `stale`。
- 技术名词遵循统一术语表。
- 断网或上游 API 不可用时有明确状态，不假装完全离线。
- 无敏感密钥、支付配置、账号数据、缓存或日志进入版本控制。
- 没有公开 push、公开部署或再分发上游内容。

## 13. 验证矩阵

| 类别 | 最小验证 |
| --- | --- |
| 安装 | 全新终端按 runbook 完成依赖安装 |
| 基线 | 原始英文版启动、构建和最小测试 |
| UI 翻译 | 导航、按钮、状态、错误和 fallback |
| Roadmap 节点 | CS、Backend、AI Agents 三条代表路线 |
| 长文本 | Topic 正文、FAQ、代码块和外部链接 |
| 布局 | 中英文换行、节点高度、连线和分区 |
| 响应式 | 1440、1280、390、360px |
| 无障碍 | DOM 顺序、焦点、屏幕阅读器名称、对比度 |
| 构建 | 上游 build、类型检查、E2E 或等价验证 |
| 同步 | 新增、修改、删除和迁移节点模拟 |
| 隐私 | 第三方请求、遥测、密钥和本地绑定检查 |
| 许可 | 不公开发布、不复制到其他知识库 |

## 14. 停止条件

出现任一情况立即停止并汇报：

- 最新许可证不允许计划中的本地派生使用。
- 目标目录已存在且包含不明或未提交改动。
- 原始英文版连续 3 次仍无法完成最小启动或构建。
- 上游运行必须使用用户未提供的生产密钥或账号权限。
- 用户实际要求完全离线后端或公网部署。
- 双语节点无法在 renderer 的数据或组件层实现，只能依赖脆弱 DOM 后处理。
- 双语高度变化导致画布布局体系需要整体重写，且三条代表路线无法验证。
- 翻译范围无法通过稳定 ID 与原文关联。
- 同一修复方向连续失败 3 次。
- 上游同步会覆盖用户已有改动。

## 15. 主要风险与回退

| 风险 | 处理 |
| --- | --- |
| 许可证限制 | 仅本机个人使用；任何公开行为重新审批 |
| 远程 API 依赖 | 明确“本地运行、非完全离线”；显示失败状态 |
| 上游无统一 i18n | 建独立翻译层和统一组件，不散改字符串 |
| Roadmap 节点高度变化 | 先验证三个代表路线，再批量扩展 |
| 翻译量巨大 | 分 Roadmap 批次、覆盖率和状态管理 |
| 上游更新导致翻译失效 | 原文 hash + commit + `stale` 状态 |
| 术语不一致 | 中央术语表与自动检查 |
| 本地补丁难同步 | 最小改动上游组件，翻译数据单独存放 |

回退顺序：

1. 关闭中文注释，确认英文版仍正常。
2. 回退最近一个本地阶段 commit。
3. 保留翻译目录和审计报告，不覆盖上游英文。
4. 必要时重新克隆相同 `UPSTREAM_COMMIT.txt` 对应版本复现基线。

## 16. 独立线程启动提示

将下面内容作为新线程开场说明：

> 请严格执行 `/Users/qiaoen/Projects/80-knowledge-data/80-research/AI student/docs/task-2-roadmap-sh-bilingual-local-execution.md`。目标是把 `nilbuild/developer-roadmap` 克隆到 `/Users/qiaoen/Projects/60-software-ai/60-app/developer-roadmap-bilingual/`，先验证原始英文基线，再实现英文主文本 + 中文小字注释。翻译必须与上游英文解耦，并带稳定 ID、原文 hash、状态和上游 commit。默认仅本机个人使用，不公网部署、不 push、不把内容导入其他知识库。遇到许可、基线、完全离线或 renderer 架构停止条件时立即汇报，不扩大范围。

