## Decision brief — policy-review-ack (annual)
**Criteria:** CC1.1, CC2.2, CC5.3   **Owner (you):** leadership

**What I did:** Ran the policy-review playbook — checked `git log -1` across all 13 policies in `compliance/policies/`. No policy exceeds 12 months since last change (all installed 2026-06-29 at baseline). Drafted the evidence doc and a DRAFT assertion.

**Evidence:** [compliance-evidence-draft/policy-review-ack-2027-06-29.md](compliance-evidence-draft/policy-review-ack-2027-06-29.md)

**Findings / anomalies:** None — all policies are <1 day old. This is the first annual interval; no policy is overdue.

**Open items needing YOUR judgment / inputs only you can provide:**
1. **Policy adoption** — All 13 policies are shipped but un-adopted. Please read the key policies (especially `information-security-policy.md`, `acceptable-use-policy.md`, `hr-security-policy.md`, `privacy-policy.md`) and confirm they match your org's posture.
2. **Employee acknowledgement roster** — I cannot see external HR data. Please collect signed acknowledgement forms (or an HR-system export) and attach/commit them as the artifact-of-performance.
3. **Annual cadence** — Schedule next review before 2027-06-29.

**To sign:** First, the compliance-verifier will post advisory findings here. Once you've considered those: edit the `assertion:` line in `compliance/evidence-ledger.yml` to your own words, set `source: human-attested`, `assertion_author: <your login>`, `approver: <your login>`, attach the acknowledgement roster, then Approve. _I drafted this; the decision and the signature are yours._
