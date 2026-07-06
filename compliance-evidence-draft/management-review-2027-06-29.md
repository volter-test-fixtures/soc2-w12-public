# Control monitoring + management review — 2027-06-29 (CC4.1/CC4.2/CC5.1)
**Process:** management-review   **Cadence:** annual   **Review date:** 2026-06-30   **Drafted by:** EA (compliance-drafter)
**Status:** DRAFT — executive review required before signing

## What I gathered

Assembled from the evidence ledger (`compliance/evidence-ledger.yml`), the rendered control register (`compliance/control-register.md`), and workflow-run history:

### Ledger state (all processes)

| Process | Cadence | Last evidence | Next due | State |
|---------|---------|---------------|----------|-------|
| access-review | quarterly | 2026-09-29 (human-attested) | 2026-12-30 | ✅ current |
| vendor-reassessment | annual | 2026-06-29 (since install) | 2027-06-30 | ⏳ first interval |
| security-training | annual | 2026-06-29 (since install) | 2027-06-30 | ⏳ first interval |
| ir-tabletop | annual | 2026-06-29 (since install) | 2027-06-30 | ⏳ first interval |
| dr-test | annual | 2026-06-29 (since install) | 2027-06-30 | ⏳ first interval |
| risk-assessment | annual | 2026-06-29 (since install) | 2027-06-30 | ⏳ first interval |
| **management-review** | **annual** | **2026-06-29 (since install)** | **2027-06-30** | **⬅️ this review** |
| policy-review-ack | annual | 2027-06-29 (human-attested) | 2028-06-29 | ✅ current |
| pen-test | annual | 2026-06-29 (since install) | 2027-06-30 | ⏳ first interval |
| evidence-collection | weekly | liveness-gated (W11) | — | ✅ operational |

All **per-event** processes (hr-onboard-offboard, change-mgmt-infra, background-check) have no events to date — expected for a day-old install.

### Workflow-run history (most recent 20 runs via `gh run list --limit 20`)

Runs in the last 24 hours (since repo creation 2026-06-29):
- **compliance-drafter** — 4 runs (this + 3 concurrent sibiling control-due issues)
- **pm** — 1 run (success) ✅
- **Merge** — 1 run (success) ✅
- **heartbeat** — 1 run (success) ✅
- **soc2-register-check** — 1 run (success) ✅
- **sbom** — 1 run (success) ✅
- **CodeQL** — 1 run (success) ✅
- **Security** — 1 run (**failure** — see Findings) ⚠️
- **secret-scan** — 1 run (success) ✅
- **code-scan** — 1 run (success) ✅
- **supply-chain** — 1 run (success) ✅
- **human-approval** — 1 run (success) ✅

### Previous control-cycle outcomes

| PR | Control | Merged | Outcome |
|----|---------|--------|---------|
| #7 | access-review (quarterly — 2026-09-29) | 2026-06-29 | Exec signed; evidence filed |
| #11 | policy-review-ack (annual — 2027-06-29) | 2026-06-30 | Exec signed; evidence filed |

All prior controls completed with executive sign-off. No rollbacks or contested findings.

## Assessment

### Criteria coverage

| Criterion | Statement | Assessment |
|-----------|-----------|------------|
| **CC4.1** — Perform ongoing/separate monitoring evaluations | On-going monitoring via evidence-collection (weekly snapshot) + heartbeat (liveness) | ✅ Both workflows operational. evidence-collect dispatched weekly; heartbeat run successful. Management review provides the "separate evaluation" leg. |
| **CC4.2** — Evaluate & communicate control deficiencies | Deficiencies surfaced via soc2-control-due issues, compliance-cadence watchdog, and this management review | ✅ Deficiency pipeline operational: 4 soc2-control-due issues opened today. Board/leadership communication leg is external (see Coverage/gaps). |
| **CC5.1** — Select & develop control activities | Control register (61 criteria) maintained and rendered; gate: compliance/** human-approval required | ✅ Register covers all 61 TSC criteria. Enforcement via CI/human gates documented. |

### Overall status

**This is the first management review** at the start of the Type-II observation window (effective_from: 2026-06-29). The control environment was installed ~24 hours ago. All periodic controls are in their first interval and current. The system is operating as designed.

## Findings

### ⚠️ Security workflow failure (workflow static analysis / zizmor)

The **Security** workflow failed on its `zizmor` static analysis step (run #28413390900, triggered by policy-review-ack PR merge). Two findings surfaced:

1. **`excessive-permissions`** — `compliance-cadence.yml:16` has `issues: write` at the workflow level, flagged as overly broad by zizmor.
2. **`template-injection`** — `retention.yml:51` uses `gh pr create --base "${{ github.event.repository.default_branch }}"` which may expand into attacker-controllable code.

These are pre-existing issues in the workflow definitions — not caused by the policy-review-ack PR. They should be triaged and remediated by the maintainer. (See Open items.)

### No other flagged items

- No open incident/blocked issues on the repo.
- No open collaborators exceeding intended access (empty collaborator list per access-review evidence).
- No un-evidenced deficiencies beyond those noted below.

## Open items needing the executive

1. **zizmor findings — triage and assign remediation.** The Security workflow failure flags two workflow-definition issues. These need assignment to the maintainer for fix PRs. The executive should decide severity and timeline.

2. **Annual control evidence — push for completion before interval end.** While all processes are in their first interval (due 2027-06-30), none have evidence filed yet except access-review and policy-review-ack. The executive should ensure the org progresses:
   - vendor-reassessment — needs subprocessor report collection
   - security-training — needs training delivery + attestation
   - ir-tabletop — needs exercise scheduling
   - dr-test — needs restore test scheduling
   - risk-assessment — needs risk register scoring
   - pen-test — needs external penetration test engagement

3. **Board/leadership communication (CC4.2 external leg).** This management review serves as the recorded substitute for board oversight (CC1.2 note), but formal deficiency escalation to leadership/board is an external process. The executive should decide on a communication channel (meeting minutes, email, or this PR as the record).

## Coverage / gaps

- ✅ **Evidence-ledger state** — checked in-repo.
- ✅ **Control-register state** — checked in-repo.
- ✅ **Workflow-run history** — checked via `gh run list`.
- ✅ **Prior control cycles** — reviewed via merged PRs.
- > un-evidenced: **Effectiveness of controls** — this review catalogs what controls exist and whether they've run, but does not independently verify their effectiveness. The technical controls (C1–C20) rely on enforced CI gates; the organizational controls (O1–O11) rely on the executive's program. An independent penetration test or control test would provide effectiveness evidence.
- > un-evidenced: **Board/leadership deficiency communication** (CC4.2 external leg) — formal escalation is an external process. This management review document serves as the deficiency record; the executive should determine whether written escalation is needed.
- > un-evidenced: **External evidence artifacts** — subprocessor SOC 2 reports, penetration test reports, HR rosters, and insurance certificates are outside the repo and require executive action to collect.