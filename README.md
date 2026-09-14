# agent-skills-cn

中英双语 Agent Skills —— 把实战打磨过的领域工作流做成开源 SKILL.md，Claude Code / DSH / Hermes / Codex 通用。

Bilingual (EN/CN) Agent Skills: battle-tested domain workflows packaged as open SKILL.md files, portable across Claude Code, DSH, Hermes, and Codex.

## Why / 为什么

Skill 经济正在爆发（archify 60.9k⭐、humanizer 47.7k⭐），但现有中文生态全是工具/桥接类 —— 领域工作流知识型 skill 是空白。本项目把真实工作里反复验证过的工作流，按爆款 skill 的写法标准（正向表述、可判定完成标准、理念先行）做成中英双语 skill：正文英文（agent 消费、最大化受众），description 内嵌中文触发词，README 双语。

The skill economy is booming, but the Chinese-language ecosystem is all tooling and bridges — domain-workflow knowledge skills are missing. We package workflows that survived real use, written to the quality bar of top skills: positive phrasing, verifiable completion criteria, rationale first.

## Skills

### [email-deliverability-audit](skills/email-deliverability-audit/SKILL.md)
B2B 邮件列表可发送性审计：格式 → 死域 → MX → 占位符四道闸，逐地址判定 sendable / risky / dead，批量 CSV 进 CSV 出，绝不编造通过。
Audit a B2B email list through four sequential gates (format, dead domain, MX, placeholder/role) classifying every address as sendable, risky, or dead — with a hard integrity rule: every verdict traces to a check that actually ran.

```bash
# Claude Code
git clone https://github.com/<you>/agent-skills-cn && cp -r agent-skills-cn/skills/email-deliverability-audit ~/.claude/skills/
# Hermes
cp -r skills/email-deliverability-audit ~/.hermes/skills/
```

### [competitor-recon](skills/competitor-recon/SKILL.md)
动手做功能前先跑的竞品侦察：枚举 3-6 个竞品 → 逐个提取功能/定价/定位/真实用户抱怨 → 抱怨聚类出差异化机会 → 对比表 + 值得抄 + 不值得做，每个功能灵感必须有真实抱怨佐证。
Competitor recon before you build: enumerate 3-6 competitors, extract features/pricing/positioning/user complaints (reviews beat marketing), cluster complaints into differentiation opportunities, and deliver a comparison table plus copy-worthy and skip lists — every feature idea backed by a cited user complaint.

```bash
git clone https://github.com/<you>/agent-skills-cn && cp -r agent-skills-cn/skills/competitor-recon ~/.claude/skills/
```

### [resume-localize-cn2en](skills/resume-localize-cn2en/SKILL.md)
中文简历 → 英文技术岗简历：整段删除服务行业经历，职责改写为量化成果，语气诚恳平淡，拼写统一（AU 或 US），ATS 友好无表格。
Localize a Chinese resume into an English technical CV: cut service-industry stints entirely, convert duties into quantified outcomes, keep the tone plain and honest, unify to one spelling variant, keep it ATS-parsable.

```bash
git clone https://github.com/<you>/agent-skills-cn && cp -r agent-skills-cn/skills/resume-localize-cn2en ~/.claude/skills/
```

### [delivery-checklist](skills/delivery-checklist/SKILL.md)
交付物发出前核对清单：Excel ≤6 列全英文表头、实开文件核对行数与去重计数、已发批次入台账、文件进既定交付目录、候选数与可发送数分开报。
Pre-send verification for deliverables: Excel ≤ 6 columns with English headers, open the real file to verify row/dedup counts, log sent batches in a ledger, keep files in the agreed delivery directory, and report candidate vs sendable counts as different numbers.

```bash
git clone https://github.com/<you>/agent-skills-cn && cp -r agent-skills-cn/skills/delivery-checklist ~/.claude/skills/
```

## Install / 安装

| Platform | Method |
|---|---|
| Claude Code | `cp -r skills/<name> ~/.claude/skills/` |
| DSH | 复制到 DSH 的 skills 目录（或按其插件规范打包） |
| Hermes | `cp -r skills/<name> ~/.hermes/skills/` |
| Codex | 参考 `.claude-plugin/` 打包后按 Codex 插件机制安装 |

每个 skill 独立可用，互不依赖。Each skill is standalone — no cross-dependencies.

## Status / 状态

v0.2.0 — 4 个 skill 全部在 Hermes 真实场景实测通过（邮箱四道闸 DNS 实测 6 样本全对、竞品调研产出带源链接对比表、简历本地化完整走 5 步、交付核对实抓出 185 个表内重复行），并按实测结果修订。License: MIT。

v0.2.0 — all four skills live-tested in real scenarios (DNS-verified email audits, a sourced competitor recon, a full resume localization run, a delivery audit that caught 185 duplicate rows) and revised from the findings. License: MIT.
