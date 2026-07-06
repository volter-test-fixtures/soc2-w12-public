# Enterprise risk assessment — 2027-06-29 (CC3.1–3.4)
**Process:** risk-assessment   **Cadence:** annual   **Review date:** 2026-06-30   **Drafted by:** EA (compliance-drafter)
**Status:** DRAFT — executive review required before signing

## What I gathered

**Data sources:**
- `compliance/risk-register.md` — current register (9 seeded rows, last effective 2026-06-29, all `[OWNER]` placeholders unfilled)
- `compliance/policies/risk-management-policy.md` — policy defining the process
- `compliance/policies/incident-response-policy.md` — post-incident risk update requirement
- `compliance/control-register.yml` — mapped controls
- Merged PRs since 2026-06-29: `gh pr list --state merged --search "merged:>=2026-06-29"` → **4 PRs** listed below
- Closed security/incident issues since 2026-06-29: `gh issue list --state closed --label "incident,security,agent-blocked,needs-info" --search "closed:>=2026-06-29"` → **0 found**
- Git log since last effective date (`git log --since="2026-06-29"`) → **1 commit touching risk-register.md** (PR #11 policy-review-ack scaffolding)

**Merged PRs reviewed for risk signal:**
| PR | Title | Risk-relevant? |
|----|-------|----------------|
| #11 | [soc2-control-due] policy-review-ack — EA-drafted | No — compliance evidence only |
| #10 | Restore drafter PR path (operator) | Operational refinement to drafter workflow |
| #8  | Update drafter/verifier doctrine (operator) | Operational refinement — no architectural change |
| #7  | [soc2-control-due] access-review — evidence draft | No — compliance evidence only |

## Assessment

The risk register was seeded on 2026-06-29 with 9 rows (R1–R9) covering the fleet-inherent risks:
- Code integrity (R1), exfiltration (R2), subprocessor leakage (R3), supply chain (R4), retention (R5), fleet liveness (R6), spend runaway (R7), branch-protection drift (R8), stale access (R9)
- Row R10 is a placeholder for a product-specific risk — **never filled**

**Key observations:**

1. **No material change** — The 4 merged PRs since the last assessment were all operational/compliance-process refinements or evidence drafts. None introduced new architecture, new subprocessors, new integrations, or new data flows. Score changes are not warranted for existing risks based on signal available in-repo.

2. **No incidents** — Zero closed security/incident issues in this interval. No post-incident risk-register updates triggered.

3. **Owners unfilled** — All nine rows still show `[OWNER]` placeholders. The policy requires an owner per risk.

4. **Last-assessment date unset** — The header `[DATE]` placeholder remains. Dated scoping is needed for the next cycle.

5. **R3 score vs. current subprocessor exposure** — R3 (source code leaks via subprocessor) scored L=3, I=4, Score=12 (treatable threshold). The subprocessors list should be cross-checked — but the actual SOC 2 reports / DPAs are external (see Coverage/gaps below).

6. **R10 empty** — No product-specific risk has been identified or added.

**Suggested register updates** (executive decision required):

| Item | Change | Rationale |
|------|--------|-----------|
| Header date | Set to `2026-06-30` | This assessment date |
| R1–R9 owners | Fill from actual role assignments | Currently all `[OWNER]` — renders register incomplete |
| R10 | Remove or assign a product risk | Empty row signals incomplete assessment |
| R3 score | Re-evaluate if DPAs/SOC2 reports are current | At the treatable threshold — executive to decide |

## Findings

| # | Finding | Detail | Risk(s) affected |
|---|---------|--------|------------------|
| F1 | Risk owners not assigned | All 9 rows use `[OWNER]` — no accountability per risk | All |
| F2 | Register header un-dated | `Last assessment: [DATE]` — not useful for next-cycle reference | All |
| F3 | R10 placeholder empty | Product-specific risk slot unfilled since inception | R10 |
| F4 | No incidents this interval | Zero security incidents or agent-blocked issues — good | All |

## Open items needing the executive

- **Fill risk owners:** Assign an owner for each of R1–R9 (likely maintainer for in-repo controls R1–R2/R4–R8, leadership for R3/R9).
- **Date the header:** Set `Last assessment: 2026-06-30`.
- **R10 decision:** Either remove the placeholder row or identify a product-specific risk.
- **R3 subprocessor evidence:** Cross-check the subprocessor SOC 2 report / DPA expiry dates against current exposure and decide whether the L=3/I=4 score still holds.
- **Accept any score changes** and sign off on the updated register.

## Coverage / gaps

- ✅ Risk register rows reviewed and scored (EA assessed signal available in-repo)
- ✅ Merged PRs reviewed for architectural/new-risk signal
- ✅ Incident/security issues checked
- ✅ Git history reviewed for risk-relevant changes
- ✅ Policy alignment checked
- > **un-evidenced: subprocessor SOC 2 reports / DPAs** — actual vendor risk evidence is external (stored by the org, not in-repo). Executive must attach or reference current reports to validate R3 scoring.
- > **un-evidenced: fraud-risk assessment (CC3.3)** — the register has no dedicated fraud risk row. The policy mentions considering fraud; executive should assess whether R3 (subprocessor leakage) or a new row suffices for CC3.3 coverage.