## Decision brief — hr-onboard-offboard (per-event)
**Criteria:** CC6.2, CC1.4   **Owner (you):** hr

**What I did:** Drafted the onboarding/offboarding record template covering joiner/mover/leaver lifecycle events per HR Security Policy and Access Control Policy. This is a **world-act** control — the actual provisioning/deprovisioning is performed by HR; this template records the artifact-of-performance.

**Evidence:** [Evidence doc](compliance-evidence-draft/hr-onboard-offboard-2027-06-29.md)

**Findings / anomalies:** None — no personnel events have occurred to date (first interval). The template and policies are in place and aligned with CC6.2 (register/authorize/deprovision credentials ≤24h) and CC1.4 (commitment to competence through background checks, training, and documented access).

**Open items needing YOUR judgment / inputs only you can provide:**
- On each joiner event: run the onboarding checklist, complete Section A of the template, and attach/commit the completed record
- On each leaver event: complete Section B, revoke ALL access same day (≤24h), rotate shared credentials, and attach/commit the completed record
- On each mover/role-change event: complete Section C, ensuring old-role access is revoked and new-role access follows least-privilege
- Confirm the shared credential inventory is maintained so offboarding rotation is feasible within <24h

**To sign:** edit the `assertion:` line in the ledger artifact (`compliance/evidence-ledger.yml`) to your own words, set `source: human-attested`, `assertion_author: <your login>`, `approver: <your login>`, then Approve. _I drafted this; the decision and the signature are yours._