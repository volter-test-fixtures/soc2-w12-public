# Vendor/subprocessor risk reassessment — 2027-06-29 (CC9.2/P6.4/P6.5)
**Process:** vendor-reassessment   **Cadence:** annual   **Review date:** 2026-06-30   **Drafted by:** EA (compliance-drafter)
**Status:** DRAFT — executive review required before signing

## What I gathered

Parsed `compliance/subprocessors.md` for report/DPA dates across all 7 listed entities. The inventory has no actual dates — all SOC 2 report entries are qualitative statements and all DPA entries are `[link]` placeholders — so every data-processing subprocessor is flagged.

**Repository:** soc2-w12-public · **Effective from:** 2026-06-29 · **Review interval:** 2026-06-29 → 2027-06-29

| # | Subprocessor | Role | Data shared | SOC 2 report date | DPA date |
|---|---|---|---|---|---|
| 1 | **GitHub** (Microsoft) | Code host, CI/CD, Actions, secret store | Source code, issues/PRs, secrets, run logs | "Yes — request via GitHub Trust Center" — **no date** | `[link]` — **no signed DPA on file** |
| 2 | **Open Autonomy model proxy** | Gates agent model spend, holds provider keys | Model requests/responses (code + prompts in transit); spend ledger | "Verify with the proxy operator" — **not verified, no report** | `[link]` — **no signed DPA on file** |
| 3 | **Cloudflare** | Hosts model proxy (Workers + Durable Objects) | Same as proxy (runs there); at-rest ledger | "Yes — Cloudflare Trust Hub" — **no date** | `[link]` — **no signed DPA on file** |
| 4 | **OpenRouter** | Upstream model routing (proxy forwards to it) | Model requests/responses (code + prompts) | "Verify" — **not verified, no report** | `[link]` — **no signed DPA on file** |
| 5 | **Model provider(s)** (DeepSeek/Anthropic via OpenRouter) | LLM inference | Model requests/responses | "Verify per provider" — **not verified, no report** | `[link]` — **no signed DPA on file** |
| 6 | **npm registry** | Dependency source | none (read-only fetch) | n/a (integrity enforced by `check-supply-chain.ts`) | n/a — read-only, no data shared |
| 7 | _[compliance platform — Vanta/Drata]_ | Continuous control monitoring | Repo/control metadata | "Yes" — **no date** | `[link]` — **no signed DPA on file** |

**Policy references checked:**
- `compliance/policies/vendor-management-policy.md` — requires annual re-review of each subprocessor's SOC 2 report, risk ranking, and signed DPAs.
- `compliance/policies/privacy-policy.md` — referenced by P6.4 (vendor privacy commitments) and P6.5 (vendor breach-notification commitments).
- `compliance/control-matrix.md` — O4: "Vendor/subprocessor mgmt — Collect reports, risk-rank".

**Criteria coverage:**
| Criteria | Statement | Evidence path |
|----------|-----------|--------------|
| CC9.2 | Assess & manage vendor/business-partner risk | Subprocessor inventory + collected reports + DPAs |
| P6.4 | Vendor privacy commitments + periodic assess | Signed DPAs + breach-notification clauses |
| P6.5 | Vendor breach-notification commitments | DPA terms re: notification timelines |

## Assessment

**All 5 data-processing subprocessors are unevidenced for SOC 2 reports and DPAs.** The sixth (npm) is read-only and integrity-enforced, so it is low risk and exempt. The seventh (`_` placeholder for a compliance platform) is also unevidenced.

The **proxy → OpenRouter → provider chain** is the highest-risk path (source code transits it in-flight per policy), and all three links in that chain lack both a verified SOC 2 report and a signed DPA. This is a **critical gap** for the executive to address.

| Risk tier | Subprocessors | Count | Status |
|-----------|--------------|-------|--------|
| **High** (code-in-flight transit) | Open Autonomy model proxy, OpenRouter, Model provider(s) | 3 | ❌ No SOC 2 reports; no DPAs |
| **Medium** (infrastructure hosting) | GitHub, Cloudflare | 2 | ❌ No dated SOC 2 reports on file; no DPAs |
| **Low** (read-only, integrity-enforced) | npm registry | 1 | ✅ n/a |
| **Placeholder** (compliance platform — TBD) | _[Vanta/Drata]_ | 1 | ❌ No date; no DPA |

**Narrative:** The entire vendor-management program for this repository is in setup phase. The subprocessor inventory identifies the right entities and their risk profile, but none of the artifacts-of-performance (downloaded SOC 2 reports, signed DPAs) have been collected into this repository. The policy requires ≥ annual re-review and DPA coverage for all data processors. The first interval (2026-06-29 → 2027-06-29) could be used to close these gaps before the next annual review.

## Findings

- **🔴 FLAG — SOC 2 reports not on file (5/7 entities):** None of the subprocessors that process data have a dated SOC 2 report committed to the repo. For GitHub and Cloudflare the reports exist at their trust centers but have not been downloaded, reviewed, or stored here. For the proxy, OpenRouter, and model providers, the reports are unverified entirely.
- **🔴 FLAG — No signed DPAs on file (6/7 entities, excluding npm):** All DPA entries are `[link]` placeholders. Signed DPAs are a legal requirement for data processors.
- **🔴 FLAG — High-risk chain (proxy → OpenRouter → provider) completely unevidenced:** This is the path where source code leaves the repo boundary in-flight. All three entities need SOC 2 report review and DPA signing as a priority.
- **⚠️ FLAG — Subprocessors.md has placeholder inventory metadata:** The file header shows `[OWNER]`, `[DATE]` — these should be filled in with the actual responsible person and last review date.
- **⚠️ FLAG — Compliance platform placeholder unresolved:** The compliance platform (Vanta/Drata) row is a template; if the org has onboarded one, its specific data and DPA should replace the placeholder.

## Open items needing the executive

- **Collect SOC 2 reports (#1 priority):** Obtain the SOC 2 (or equivalent) reports for GitHub (via GitHub Trust Center), Cloudflare (via Cloudflare Trust Hub), the Open Autonomy proxy operator, OpenRouter, and each model provider. Commit them under `compliance-evidence/vendor-reassessment/` or a subdirectory. Review each for exceptions that might affect this repo.
- **Sign DPAs (#1 priority):** Sign DPAs with all data-processing subprocessors (GitHub, Cloudflare, Open Autonomy proxy, OpenRouter, model providers). The signed DPAs should be committed to the repo.
- **Record review dates in subprocessors.md:** Update the SOC 2 report and DPA columns with actual review dates so the next interval's review has a baseline to compare against.
- **Fill inventory header metadata:** Set `[OWNER]` and `[DATE]` in `compliance/subprocessors.md` to the responsible person and today's review date.
- **Resolve compliance platform placeholder:** If a compliance monitoring platform has been adopted, replace the placeholder row with specifics and collect its SOC 2 report and DPA.
- **(> un-evidenced: needs the executive)** I cannot download external SOC 2 PDFs from trust centers, verify their contents, or sign legal DPAs. All of these are org/legal tasks that require the executive's involvement.

## Coverage / gaps

- ✅ Subprocessor inventory parsed — 7 entities reviewed.
- ✅ Risk-tier analysis by data sensitivity — complete.
- ✅ Policy requirement check — vendor-management-policy.md obligations surfaced.
- ✅ Flagged items prioritized for executive action.
- > un-evidenced: **SOC 2 / equivalent reports** — external PDFs behind trust centers; the executive must collect and attach.
- > un-evidenced: **Signed DPAs** — legal documents; the executive (or legal counsel) must sign and commit.
- > un-evidenced: **Breach-notification clause verification** — DPA content review; requires signed DPAs first.
- > un-evidenced: **Remediation follow-up for any report exceptions** — requires reviewing the reports once collected.