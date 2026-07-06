# Policy review + employee acknowledgement — 2027-06-29 (CC1.1/CC2.2/CC5.3)
**Process:** policy-review-ack   **Cadence:** annual   **Review date:** 2026-06-30   **Drafted by:** EA (compliance-drafter)
**Status:** DRAFT — executive review required before signing

## What I gathered

All 13 policies under `compliance/policies/` were checked for their last modification date using `git log -1 --format=%ai`:

```
compliance/policies/acceptable-use-policy.md              2026-06-29
compliance/policies/access-control-policy.md              2026-06-29
compliance/policies/business-continuity-dr-policy.md      2026-06-29
compliance/policies/change-management-policy.md           2026-06-29
compliance/policies/data-classification-and-retention-policy.md  2026-06-29
compliance/policies/encryption-policy.md                  2026-06-29
compliance/policies/hr-security-policy.md                 2026-06-29
compliance/policies/incident-response-policy.md           2026-06-29
compliance/policies/information-security-policy.md        2026-06-29
compliance/policies/privacy-policy.md                     2026-06-29
compliance/policies/risk-management-policy.md             2026-06-29
compliance/policies/secure-sdlc-policy.md                 2026-06-29
compliance/policies/vendor-management-policy.md           2026-06-29
```

All 13 policies were last modified on **2026-06-29** (the repository initialization / baseline date). The first interval of this annual process began on `effective_from: 2026-06-29`; none have had substantive review since the baseline commit.

**Criteria coverage (from control-register.yml):**
| Criteria | Relevant policies | Last change |
|----------|------------------|-------------|
| CC1.1 — Commitment to integrity & ethical values | `acceptable-use-policy.md`, `information-security-policy.md` | 2026-06-29 |
| CC2.2 — Internally communicate objectives & responsibilities | `information-security-policy.md` | 2026-06-29 |
| CC5.3 — Deploy controls via policies & procedures | `compliance/policies/` (all 13) | 2026-06-29 |

No policies are >12 months stale — the entire policy set was installed yesterday (2026-06-29) at baseline.

## Assessment

All 13 policies are <1 day old relative to this review date. During this first annual window, no policy is overdue for review — the executive may choose to review and adopt them substantively before the window closes on 2027-06-29.

The policies cover the full SOC 2 trust-services criteria scope documented in `compliance/control-matrix.md` (O1 — Security policies). They have been bundled with the repository but **not yet formally adopted or approved by leadership.** This draft is the first step in that process.

## Findings

- **None.** No policy exceeds 12 months since last change.

## Open items needing the executive

- **Policy adoption:** All 13 policies need leadership review and formal approval. The review date above shows <1 day since creation — this is the *first* interval. The executive should read the policies (especially `information-security-policy.md`, `acceptable-use-policy.md`, `hr-security-policy.md`, `privacy-policy.md`) and confirm they match the org's expected posture.
- **Employee acknowledgement roster** (> un-evidenced: needs the executive): The policy-acknowledgement process requires that all employees have read and acknowledged each policy. The roster is an external HR input — the executive must collect signed acknowledgement forms (or an HR system export) and commit them under `compliance-evidence/` or attach them to the PR. This is a required artifact-of-performance that I cannot generate.
- **Annual review cadence:** A note should be added to the calendar or compliance-cadence workflow to ensure the next review occurs before 2027-06-29.

## Coverage / gaps

- ✅ Policy last-change dates — checked in-repo.
- > un-evidenced: **Employee acknowledgement roster vs headcount** — this is an external HR input. The executive must provide the roster of signed acknowledgements.
- > un-evidenced: **Policy content review** — the executive should read each policy for accuracy against their org's actual practices. `git log` only tells me when the file changed, not whether it was substantively reviewed.