# Changelog

All notable user-facing changes to the agent-skills-cn catalog and the skill repos.

## [0.3.0] — 2026-09-14

### Added
- **Batch 2: ten new skill repos** (backlog-triage, web-cliplibrary, onboarding-pack, expense-capture, weekly-review, ask-batch, estimate-before-build, changelog-capture, template-instantiator, context-budget). Who: anyone browsing the catalog. Upgrade: install via `npx skills add ChenneyZhuang/<skill>`.
- **COMPATIBILITY.md in every skill repo** — per-agent install paths and runtime requirements. Who: users on any of the 75+ agents the skills CLI supports.

### Changed
- **Install commands in every README now lead with `npx skills add`** (was: manual clone/copy paths first). Who: everyone. Upgrade: nothing — old paths still work.
- **Hub catalog lists ten skills** (was: six). Upgrade: nothing.

## [0.2.0] — 2026-09-14

### Breaking
- **Skill repos are now one-repo-per-skill**; the four skills that lived in agent-skills-cn moved to their own repos and the catalog repo no longer ships skill bodies. Who: anyone who cloned agent-skills-cn before this date. Upgrade: clone the individual skill repos (links in the hub README); the old layout will not receive updates.

### Added
- MIT LICENSE, dsh.bundle manifests (package.json + cordis.patch.yml), and .gitignore protecting private working files in every repo.

## [0.1.0] — 2026-09-14

### Added
- Initial four skills drafted and live-tested: email-deliverability-audit, competitor-recon, resume-localize-cn2en, delivery-checklist.
