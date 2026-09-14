# agent-skills-cn

中英双语 Agent Skills —— 把实战打磨过的领域工作流做成开放 SKILL.md，Claude Code / DSH / Hermes / Codex 通用。

Bilingual (EN/CN) agent skills: battle-tested domain workflows packaged as open SKILL.md files, portable across Claude Code, DSH, Hermes, and Codex.

## Skills / 技能列表

每个 skill 独立成库：单独迭代、单独发版、名字即用途。Each skill lives in its own repo — one skill, one name, one release cycle.

| Skill | What it does / 干什么 |
|---|---|
| [email-deliverability-audit](https://github.com/ChenneyZhuang/email-deliverability-audit) | 四道顺序 DNS 闸门（格式/死域/MX/角色占位符），逐地址判定 sendable / risky / dead，绝不编造通过。Four DNS gates classify email addresses before your campaign finds out the hard way. |
| [competitor-recon](https://github.com/ChenneyZhuang/competitor-recon) | 抱怨驱动的竞品调研：评论/论坛/issue 跟踪器取证 → 聚类未满足需求 → 对比表 + 值得抄/不值得做清单。Complaint-driven competitor research with cited evidence. |
| [resume-localize-cn2en](https://github.com/ChenneyZhuang/resume-localize-cn2en) | 中文简历 → 英文技术简历：删人口统计学字段、职责改量化成果、统一拼写与日期、ATS 可解析、附完整变更清单。CN→EN resume localization for tech roles. |
| [delivery-checklist](https://github.com/ChenneyZhuang/delivery-checklist) | 交付前核对：实开文件验行数/去重/占位符，增量文件对基线 diff，台账记录批次，候选数≠可发送数。Verify deliverables by opening the real file. |
| [report-link-verification](https://github.com/ChenneyZhuang/report-link-verification) | 报告链接逐条当次实测：跟随重定向、反爬墙用浏览器 UA 重试、失败修复或删除。Fetch every link for real before a report ships. |
| [project-handoff](https://github.com/ChenneyZhuang/project-handoff) | 项目跨会话交接：handoff.md 记录现状/带理由的决策/症状-原因-对策的坑，新会话免考古接手。Make the next session as smart as this one. |
| [verify-claims](https://github.com/ChenneyZhuang/verify-claims) | 主张核验：文档里每条可核验主张分类分级、追溯到最强来源、当次实测（开链接/重算总数），核不了的如实标注——文档声明自己的证据等级。Every claim carries evidence or a label. |
| [decision-records](https://github.com/ChenneyZhuang/decision-records) | 轻量决策记录：决策/备选/理由/可逆性五字段，追加式、替代不重写——理由比结论活得更久。The why outlives the what. |
| [plain-business-english](https://github.com/ChenneyZhuang/plain-business-english) | 商务英文语域（面向非母语者）：先说重点、按事实本来的尺寸陈述、清除热情/道歉/确定性通胀。Facts at their size. |
| [deliverable-versioning](https://github.com/ChenneyZhuang/deliverable-versioning) | 交付版本纪律：已发出即不可变、日期命名替代 final、一个权威交付目录+台账。Sent means immutable. |
| [backlog-triage](https://github.com/ChenneyZhuang/backlog-triage) | 待办分诊：六种分类各带理由、放弃项归档、承诺变更并入单次审批。A list that only grows is not a plan. |
| [web-cliplibrary](https://github.com/ChenneyZhuang/web-cliplibrary) | 网页剪藏库：URL+日期+逐字引文+笔记分离，源页死了照样可引用。Research that survives the session. |
| [onboarding-pack](https://github.com/ChenneyZhuang/onboarding-pack) | 项目上手包：是什么/怎么跑/权威地图/潜规则/找谁，十分钟读完。The month of asking around, prepaid. |
| [expense-capture](https://github.com/ChenneyZhuang/expense-capture) | 报销捕获：照实转录、不清晰就标注、税额只读不推、批次双向对账。Transcribe, flag, reconcile. |
| [weekly-review](https://github.com/ChenneyZhuang/weekly-review) | 周回顾：承诺对结果逐条对账、成果以证据入账、顺延必须带新理由。Close loops, not vibes. |
| [ask-batch](https://github.com/ChenneyZhuang/ask-batch) | 批量提问：问题停放分组、每题带默认值、一次问完、超时默认显式生效。One sitting instead of all-day interruptions. |
| [estimate-before-build](https://github.com/ChenneyZhuang/estimate-before-build) | 先估后建：S/M/L/XL 档位+不确定性点名、范围vs预算交用户选、终点对账校准。Make the scope decision explicit. |
| [changelog-capture](https://github.com/ChenneyZhuang/changelog-capture) | 变更日志捕获：改动当下写 who/what/upgrade 条目，发版时与实际 diff 双向核对。One minute while the diff is in hand. |
| [template-instantiator](https://github.com/ChenneyZhuang/template-instantiator) | 模板实例化：盘点→替换→机械扫描→出示零残留证明。Proven clean, not assumed clean. |
| [context-budget](https://github.com/ChenneyZhuang/context-budget) | 上下文预算：分层读文件、笔记落盘抗压缩、检查点复述——长任务靠笔记收尾而不是硬撑。The window is working memory — spend it deliberately. |

## Why bilingual / 为什么中英双语

Skill 正文用英文（agent 消费、最大化受众），description 内嵌中文触发词（中文任务描述也能自动命中），每个 README 双语、附真实实测案例。英文与中文生态对同一工作流的写法差异，本身就是这个系列的一手经验。

Bodies are English (agent-facing, maximum reach); descriptions carry Chinese trigger words so Chinese task phrasings still auto-load the skill. Every README is bilingual and includes a worked example from live testing.

## Install / 安装

```bash
# Claude Code — the clone IS the install
git clone https://github.com/ChenneyZhuang/<skill-name> ~/.claude/skills/<skill-name>
# Hermes
cp -r <skill-name> ~/.hermes/profiles/<profile>/skills/
```

每个 skill 独立可用，互不依赖。Each skill is standalone — no cross-dependencies.

## Status / 状态

v0.2.0 — 前六个 skill 在真实场景实测通过并按实测修订；后四个（verify-claims / decision-records / plain-business-english / deliverable-versioning）已实测发布。License: MIT.

v0.2.0 — the first six skills are live-tested in real scenarios and revised from findings; the latest four shipped after their own live tests. License: MIT.
