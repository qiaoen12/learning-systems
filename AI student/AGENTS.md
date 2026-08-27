# AI student 代理说明

本目录保存 AI 时代个人学习路线、能力盘点问答和不同 AI 生成的对照方案；冻结材料统一放在 `frozen/`。当前执行版路线为根目录的 `learning-plan-final.md`。

## 项目定位

- `frozen/QA.md` 是个人画像、能力盘点和目标上下文的事实源。
- `frozen/howto.md` 是早期通用执行框架，不等同于最终个人路线。
- `learning-plan-final.md` 是当前 16 周学习路线的最终执行版，准备期和每周验收以它为准。
- `frozen/learning-plan-*.md` 是不同 AI 生成的可对照学习方案。

## 事实源入口

1. 先读 `frozen/QA.md`。
2. 再读 `frozen/howto.md`。
3. 执行学习路线时读取 `learning-plan-final.md`。
4. 对比方案时读取对应 `frozen/learning-plan-*.md`。

## 固定执行落点

- 学习记录工作区：`/Users/qiaoen/Projects/50-career/50-skill/ai-student-learning/`
- 练习代码工作区：`/Users/qiaoen/Projects/60-software-ai/60-dev/ai-student-mini-projects/`
- 学习日志：`/Users/qiaoen/Projects/50-career/50-skill/ai-student-learning/learning-log.md`
- 问题清单：`/Users/qiaoen/Projects/50-career/50-skill/ai-student-learning/questions.md`
- 周报目录：`/Users/qiaoen/Projects/50-career/50-skill/ai-student-learning/weekly/`
- 失败样本目录：`/Users/qiaoen/Projects/50-career/50-skill/ai-student-learning/failures/`

## 常用命令

- 查看目录：`ls -la`
- 快速搜索：`rg "<关键词>" .`
- 查看 Markdown：`sed -n '1,220p' <file>`

## 禁止事项

- 不覆盖其他 AI 生成的方案文件。
- 不把学习计划写成具体项目实施计划。
- 不在本目录放代码、脚本、部署文件或临时产物。
- 不把练习代码、虚拟环境、运行日志或部署材料放入本研究目录。
- 不在未满足 `learning-plan-final.md` 的启动期验收前推进 Week 1。

## 验证方式

- 新增或修改文档后，确认文件存在且 Markdown 标题、日期、作者标注清楚。
- 对照方案必须能回答：适合谁、学什么、每周做什么、如何验收、哪些暂不做。
- 启动准备期验收必须确认：能进入学习记录工作区和练习代码工作区，能运行 `python --version`，能创建并激活 `.venv`，已写入一条学习日志，并能说明学习日志、周报、失败样本、问题清单和练习代码分别放哪里。

## 文档语言

人类可读叙述默认使用中文；命令、路径、产品名、API 名称可保留英文。
