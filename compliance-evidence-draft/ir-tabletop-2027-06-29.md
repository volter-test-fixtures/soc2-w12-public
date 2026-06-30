# Incident-response tabletop exercise — 2027-06-29 (CC7.3/CC7.4)
**Process:** ir-tabletop   **Cadence:** annual   **Review date:** 2026-06-30   **Drafted by:** EA (compliance-drafter)
**Status:** DRAFT — record template; executive runs the tabletop and attaches the completed record

## What I gathered

This is a **world-act** control. The EA cannot perform the tabletop exercise. What is available:

- **Incident Response Policy** (`compliance/policies/incident-response-policy.md`) — defines severities (SEV1–SEV3), the 5-step process (triage → contain → eradicate/recover → notify → post-incident review), roles, and the requirement for ≥1 tabletop per audit window.
- **SECURITY.md** (`SECURITY.md`) — documents the private vulnerability reporting channel, scope, trust model, and operating responsibilities.
- **Control matrix** (`compliance/control-matrix.md`) — O5 (incident response) notes the org must run a tabletop in the window. C16 (audit logging) + C17 (liveness watchdog) provide detection and tamper-evident evidence channels the exercise should test.
- **Business Continuity & DR Policy** (`compliance/policies/business-continuity-dr-policy.md`) — defines RTO/RPO, backup posture, and the restore test process (exercised separately under `dr-test`, but relevant to IR coordination).
- **No prior tabletop records** exist — this is the first interval (`effective_from: 2026-06-29`).

### Exercise scenario candidates

Based on the threat model documented in the policies and SECURITY.md, the tabletop should exercise at minimum these scenario types:

| # | Scenario | What it tests | Relevant policy |
|---|---|---|---|
| 1 | **Agent token compromise via PR** — a malicious PR bypasses supply-chain gate and exfiltrates `GITHUB_TOKEN` | Detection (SEV1 ack ≤1h), containment (revoke token, lock branches), kill-switch (`PUBLIC_AGENT_REPO_PAUSED`) | IR policy §Detection, §Process steps 1–3 |
| 2 | **Secrets exposed in transcript** — a transcript includes an unredacted secret (token/API key) | Secret-scanning gate (C12), redaction (C13), disclosure notification (IR step 4) | SECURITY.md §Reporting; IR policy §Process step 4 |
| 3 | **Supply-chain dependency compromise** — a pinned dependency is found to have a known vulnerability or is withdrawn from registry | Detection via Dependabot/CodeQL, dependency-review (C9), emergency remediation process | IR policy §Severities (SEV2); change management |
| 4 | **Fleet unavailability (loss of heartbeat)** — the PM/watchdog stops running for >interval | Liveness detection (C17/heartbeat.yml), recovery procedure, communications | BC/DR policy; IR policy §Detection |

The executive should select and run ≥1 scenario. A realistic exercise picks scenarios that match the org's actual risk profile.

## Assessment

### Criteria coverage

| Criterion | Statement | Assessment (template) |
|-----------|-----------|----------------------|
| **CC7.3** — Evaluate security events to determine incidents | Detection signals exist (private vuln reporting, CodeQL, Dependabot, secret-scanning, supply-chain gates, heartbeat). IR policy defines severities and triage criteria. | ✅ **Detection channels documented.** Tabletop determines whether detection actually works in practice → to be confirmed by executive after the exercise. |
| **CC7.4** — Respond to identified security incidents | IR policy defines 5-step process, roles, kill-switch, notification obligations. SECURITY.md documents the reporting channel. | ✅ **Response process defined.** Tabletop determines whether the defined process is operable, timely, and complete → to be confirmed by executive after the exercise. |

### Overall status

**This is the first tabletop exercise** at the start of the Type-II observation window (effective_from: 2026-06-29). The exercise has not yet been conducted. All preparatory documentation (IR policy, SECURITY.md, control matrix) is in place and current.

## Findings

### No findings from EA review — exercise has not been conducted

The policies and evidence-gathering infrastructure (C16 audit logging, C17 heartbeat, C12 secret scanning) are documented and operational. No deficiencies are visible in the documentation layer.

The tabletop exercise itself may surface findings — those will be recorded in the completed exercise record by the executive.

## Open items needing the executive

1. **Conduct the tabletop exercise.** Select ≥1 scenario from the candidates above (or design your own) and run through the full 5-step IR process with participants. **Target before 2027-06-29** (end of this interval).
2. **Attach the completed exercise record.** After the exercise, fill out the record template below and commit it alongside this evidence document (or as a replacement if the filled record supersedes this template).
3. **If findings surface:** update the risk register (`compliance/risk-register.md`) with any new risks and assign remediation owners.
4. **Schedule the next exercise.** Annual cadence means the next is due by 2028-06-29.

> ℹ️ **How to run a tabletop**: gather the incident responders (at minimum [OWNER] as incident commander + maintainers). Read the scenario aloud. Walk through each step of the IR process verbally — do not touch production systems. Record who said what, what decisions were made, what information was needed but unavailable, and what gaps were identified. Time the exercise. The record is the artifact-of-performance.

## Coverage / gaps

- ✅ **Incident Response Policy** — defined, current, covers severities/process/roles.
- ✅ **SECURITY.md** — published, covers reporting channel and scope.
- ✅ **Detection channels** — CodeQL, Dependabot, secret-scanning, supply-chain gates, heartbeat all operational per workflow-run history.
- ✅ **Incident response infrastructure** — kill-switch (`PUBLIC_AGENT_REPO_PAUSED`), branch-protection revocation, token revocation procedures documented.
- > ⚠️ **un-evidenced: tabletop not yet conducted** — this is the record template only. The executive must run ≥1 scenario and attach the completed exercise record as the artifact-of-performance.
- > ⚠️ **un-evidenced: participant contact list** — the IR policy states "maintain an up-to-date contact list" for the incident commander and maintainers. No contact list was found in the repo. The executive should confirm this exists outside the repo (e.g., in the org's internal directory / PagerDuty).
- > ⚠️ **un-evidenced: actual detection timeliness** — tabletop will determine whether the 1-hour SEV1 target ack is achievable with current team size/timezone coverage.

---

## Exercise record template (fill after the tabletop)

| Field | Value |
|---|---|
| **Exercise date** | `________` |
| **Scenario(s) exercised** | `________` |
| **Participants** | `________` |
| **Duration** | `________` |
| **Scenario trigger / how it was introduced** | `________` |
| **Detection & triage (CC7.3)** — Was the simulated incident detected? How long to triage? | `________` |
| **Containment actions taken** — Were containment steps effective? Was the kill-switch used? | `________` |
| **Eradication & recovery** — Steps taken, RTO/RPO considered | `________` |
| **Notification** — Were affected parties notified? Per what timeline? | `________` |
| **Post-incident review** — Root cause identified, corrective actions defined | `________` |
| **Gaps identified** — What didn't work, what was missing, what would block a real response | `________` |
| **Corrective actions / remediation plan** | `________` |
| **Attachments** | `________` (log, chat transcript, screenshots) |

> **After filling**: commit this completed record to `compliance-evidence-draft/ir-tabletop-2027-06-29.md` (overwriting this template) and update the assertion in `compliance/evidence-ledger.yml`.