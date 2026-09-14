---
name: competitor-recon
description: |
  Run competitor reconnaissance before building any feature: enumerate 3-6 real
  competitors, extract each one's features / pricing / positioning / user
  complaints (reviews beat marketing pages), cluster complaints into unmet
  needs, and output a comparison table plus copy-worthy features and a
  skip list. Use when planning a new feature or product, validating an idea
  before writing code, researching a market before a pitch, or deciding what
  to build next. 触发词：竞品调研 / 竞品分析 / 功能灵感 / competitor scan。
license: MIT
metadata:
  version: "0.2.0"
---

# Competitor Recon: look before you build

Run competitor reconnaissance before building any feature. Building from a
blank page repeats competitors' mistakes and misses their proven wins; the
review sections of existing products are the cheapest requirements research
that exists. One grounded user complaint is worth more than any amount of
feature-page copy, because marketing pages state intentions while reviews
state outcomes.

## Rules

1. **Reviews outrank marketing pages.** A complaint from a real user on a
   review site, forum, or app store beats any claim on the competitor's own
   site. When the two conflict, the review wins and the marketing claim gets
   recorded as a claim.
2. **Complaint clusters are the finding.** One complaint is anecdote; three
   independent users describing the same gap is an unmet need and a
   differentiation opportunity. Harvest complaints where users already
   congregate: app-store reviews, forums, community posts, and the
   competitor's own public issue tracker, where a reaction count doubles as
   a frequency statistic.
3. **Search both ecosystems.** English and Chinese sources surface different
   competitors and different complaints. A recon that reads one language
   samples half the market.
4. **Evidence or it goes in the skip list.** A feature idea enters the build
   list only with at least one real user complaint behind it, with a source
   link. Ideas without evidence stay on the skip list.
5. **Record the date.** Competitor pages change; every extraction records the
   date it was observed.
6. **Switch clients, not sources.** When a page-extraction tool fails or
   returns only search snippets, fetch the page with a direct client instead:
   a command-line HTTP client carrying a browser User-Agent, or the source's
   own API (for example, a repository's issue API). A blocked tool is a
   transport problem, not a dead source; the evidence bar never drops.

## Steps

1. **Enumerate competitors (target: 3-6).** Search the web for the product
   category and adjacent terms, in English and in Chinese. Include one
   adjacent or indirect competitor when the direct set is thin —
   users solving the same job a different way are competitors too.
   Done when: the list holds 3-6 named competitors, each with a URL.
2. **Extract per competitor.** For each one, pull: feature list, pricing
   (numbers, not "contact us"), positioning in one sentence, and user
   complaints with source links (reviews, forums, app stores, social posts).
   Done when: each competitor has all four fields filled and every complaint
   carries a source link fetched during this run.
3. **Cluster complaints.** Group complaints across competitors by the
   underlying need. Rank clusters by frequency and by how many competitors
   share the gap. Done when: each cluster lists the competitors and users it
   draws from.
4. **Produce the deliverable.** Output three artifacts:
   - **Comparison table**: competitor × (positioning, pricing, key features,
     top complaint).
   - **Copy-worthy list**: features proven by market adoption, each with the
     competitor offering it and a one-line reason it earns a copy.
   - **Skip list**: directions with weak or no complaint evidence, each with
     the reason it fails the evidence bar.
   Done when: the table covers every enumerated competitor and both lists
   cite at least one source link per item.

## Completion criteria

The recon is done when at least one feature inspiration carries a real user
complaint with a working source link, the comparison table covers every
competitor in the enumeration, and every item on the copy-worthy list traces
to cited evidence while the skip list states why each direction failed the
evidence bar.
