---
name: resume-localize-cn2en
description: |
  Localize a Chinese resume into an English resume for technical roles: demote
  service-industry stints, strip demographic fields, convert duties into
  quantified outcomes, keep the
  tone plain and honest, unify spelling to one English variant, and keep the
  document ATS-parsable. Use when translating or adapting a Chinese CV for
  English-speaking tech job applications, reviewing a bilingual resume before
  submission, preparing a CV for Australian, US, or European tech roles, or
  when a user asks for an English version of 中文简历 / 英文简历 / 简历翻译.
  触发词：简历翻译 / 简历本地化 / 英文简历 / CV localization。
license: MIT
metadata:
  version: "0.2.0"
---

# Resume Localization CN→EN: from duties to outcomes

Convert a Chinese resume into an English resume for technical roles. The
English-language tech market reads resumes as evidence of outcomes: a
recruiter spends seconds scanning for what you shipped and what it changed,
so every line earns its place by quantifying. Localization means reshaping
content for the reader's expectations — the translation is the easy half.

## Rules

1. **Lead with technical evidence; demote service-industry stints.** Food
   service, retail, waiting tables, and similar service jobs rarely help a
   technical application: they consume the seconds that matter and signal a
   career path the reader did not expect. When stronger material exists, cut
   the entry entirely, including the skills listed under it; when it carries
   the only work history, compress it to one line instead of deleting the
   section empty. Professional internships stay.
2. **Strip demographic fields.** Chinese resumes carry gender, age, a photo,
   marital status, and sometimes hukou or political affiliation; AU/US/UK
   employers exclude these so reviewers stay clear of discrimination
   questions. Remove them all. Keep contact details, and keep work-rights or
   licence facts (visa status, "Full driver's licence") when the target job
   uses them.
3. **Convert duties into outcomes.** State each role as what changed because
   you were there, with a number wherever one exists. A duty names a
   responsibility; an outcome names a result.
   - Duty: "负责后台系统开发" → Outcome: "Built the order-processing
     backend, cutting order cycle time from 40 min to 15 min."
4. **Keep the tone plain and honest.** State facts at their size. Enthusiasm
   adjectives ("passionate", "genuinely excited", "world-class") inflate
   claims and read as filler to technical reviewers; a calm sentence with a
   number persuades more than an excited one without.
5. **Unify spelling to one variant.** Pick AU or US English and apply it
   everywhere (organise/organize, colour/color, centre/center). Choose from
   the target job's locale when known; otherwise state the choice and apply
   it consistently.
6. **Keep ATS parsing clean.** Standard section headings (Experience,
   Education, Skills), plain text flow, no tables, no text boxes, no multi-
   column layouts that scramble in parsers.
7. **One date format.** Pick `MM/YYYY` or `Mon YYYY` and apply it to every
   entry, both ends of each range; render 至今 as `Present`.

## Steps

1. **Inventory.** Read the source resume and list every entry with its type:
   technical role, professional internship, service industry, education,
   project. Flag duplicate lines and visibly truncated or garbled passages
   as inventory findings. Done when: every entry carries a type tag and
   every duplicate or truncated passage is flagged.
2. **Cut.** Apply Rules 1-2: remove service-industry entries and demographic
   fields, and merge duplicated lines. Done when: the entry list contains
   zero service-industry entries and zero demographic fields, identical
   bullets appear once, and the cut list is reported to the user so the
   removals are visible.
3. **Convert.** For each surviving entry, rewrite bullet points from duties
   into quantified outcomes per Rule 3.
   Done when: every bullet states an outcome, and every number traces to the
   source or to a user answer.
4. **Polish.** Apply Rules 4-7: tone pass, spelling unification, ATS layout
   check, date format check. Done when: a scan of the document finds one
   spelling variant, one date format, standard headings, and zero
   enthusiasm adjectives.
4. **Ask.** Batch the open questions into one message: numbers the source
   lacks, entries the user must confirm or cut, and any truncated passages
   from the inventory. A placeholder marked `[X]` beats an invented figure,
   and a flagged passage beats a guessed reconstruction.
   Done when: every `[X]` and every flagged passage maps to a question the
   user received.
5. **Return.** Give the user the localized resume plus a short change log:
   what was cut and why, which numbers were added from their answers, and
   the spelling variant chosen.
   Done when: the change log covers every cut, every added number, and the
   spelling choice.
