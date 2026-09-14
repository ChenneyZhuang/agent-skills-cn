---
name: email-deliverability-audit
description: |
  Audit a B2B email list for deliverability before any sending: four sequential
  gates (format, dead domain, MX, placeholder/role accounts) that classify every
  address as sendable, risky, or dead. Use when validating a contact list before
  a campaign, verifying single addresses from lead-gen sources, cleaning a CSV
  of signups or scraped contacts, checking whether a domain can receive mail,
  or auditing addresses collected from LinkedIn outreach, Apollo, or event lists.
  触发词：邮箱验证 / 邮件列表清洗 / 可发送性检查 / email audit。
license: MIT
metadata:
  version: "0.2.0"
---

# Email Deliverability Audit: four gates before you send

Classify every email address as sendable, risky, or dead by running it through
four sequential gates. A list is only as good as its worst verifiable address:
one fabricated pass poisons the whole batch, so every verdict rests on a check
you actually ran. Bounce rates above ~5% push campaigns to spam folders and
burn domain reputation, so gating the list before sending is the cheapest
deliverability work available.

## The four gates, in order

Run gates in order and stop at the first failure. Each address records which
gate produced its verdict.

### Gate 1 — Format

Check the string against the RFC shape: exactly one `@`, no whitespace, a
domain part containing at least one dot, and a plausible TLD (2+ letters, in
the IANA list). Do not chase RFC 5322 full compliance; the goal is catching
the malformed strings that every provider rejects, with the common length
limits (local part ≤ 64 chars, domain ≤ 255) as additional shape checks.
Quoted strings and comments in the local part are rare; classify by outcome
and record the gate.

- **Pass** — all four shape checks pass. Continue to Gate 2.
- **Fail** — classify `dead (gate 1: format)`. Format failures need no DNS work.
  Gate 1 output feeds Gate 2: pass the local part and domain onward as parsed.

### Gate 2 — Dead domain

Resolve the domain: query `A` or `NS` records for the domain itself. A domain
with no answer for both record types does not exist as a mail origin and
cannot receive mail regardless of MX state.

- **Pass** — the domain resolves. Continue to Gate 3.
- **Fail** — classify `dead (gate 2: dead domain)`. Dead domains end the audit:
  every address at an unresolvable domain shares the verdict.

### Gate 3 — MX

Query MX records for the domain. No MX record means no server accepts mail
for the domain, so the address fails regardless of the local part. A live
website with no MX is the tell to expect: in a September 2026 audit,
australia.gov.au answered DNS and served its site while returning no MX —
the site was up and the mail was not.

- **Pass** — MX exists. Continue to Gate 4.
- **Fail** — no MX record found: classify `dead (gate 3: no MX)`.

### Gate 4 — Placeholder and role accounts

Flag as `risky` addresses whose local part matches a role account (`info@`,
`admin@`, `contact@`, `support@`, `noreply@`, `no-reply@`, list ended with your
own context) or a placeholder pattern: `test@`, `example@`, repeated characters
(`aaa@`), long digit runs, obvious test strings (`asdasd`, `abc123`), or a
local part that is all digits. Senders and receivers both punish role accounts;
placeholders are fabricated addresses with zero chance of delivery.

- **Pass** — a plausible personal or named address. Classify `sendable`.
- **Flag** — classify `risky (gate 4: role/placeholder)`. Keep it in the list
  only when the campaign tolerates risk; report it separately.

## Verdicts

- `sendable` — passed all four gates.
- `risky` — passed gates 1–3, flagged at gate 4.
- `dead` — failed any of gates 1–3.

## How to run

1. **Single address.** Run the four gates inline with `dig` or a Python
   resolver. State the verdict and the deciding gate. The verdict is final
   only when each gate's check actually ran against real DNS.
2. **Batch mode (CSV in, CSV out).** Read the input CSV, run each row through
   the four gates, and write one row per address with the original data plus
   the verdict and deciding gate columns. Output rows match input rows 1:1,
   with no row silently dropped.
3. **Confidence boost.** A candidate's company website that resolves and
   serves real content raises confidence from medium to high. Record this as a
   `verified_web` column rather than upgrading a verdict beyond what gates 1–3
   establish.

## Integrity rule

Never invent a pass. Every verdict must trace to a check you ran in this run:
a `dig` query, a resolver call, or an explicit format regex evaluation.
When DNS resolution itself fails on your network, record the verdict as
`unverified (DNS unreachable)` with the cause named, rather than guessing in
either direction: a failed probe is evidence about your network, and the
address keeps its previous state.

## Done when

- Every address has a verdict from a real gate evaluation, with the deciding gate recorded.
- Batch mode: output CSV rows == input CSV rows, 1:1, with verdict + deciding-gate columns.
- No verdict rests on a guess; every pass claims a check you ran in this run.
