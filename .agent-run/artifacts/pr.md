## Decision brief — pen-test (annual)
**Criteria:** CC7.1   **Owner (you):** maintainer

**What I did:** Drafted the pen-test record template for the 2027-06-29 interval. This is a **world-act** — I cannot commission or perform an external pen test. I documented the automated scanning already in place (SAST, secret-scan, dependency review, actions hardening, supply-chain checks), defined the system boundary for a pen test, and flagged all items requiring your action.

**Evidence:** [`compliance-evidence-draft/pen-test-2027-06-29.md`](compliance-evidence-draft/pen-test-2027-06-29.md)

**Findings / anomalies:**
- ⚠️ No external pen test conducted yet — this is the first annual interval (effective 2026-06-29)
- ⚠️ Automated scanners (Semgrep, CodeQL, gitleaks, dependency-review, zizmor) run continuously but are not a substitute for a human-led pen test
- ℹ️ All automated scanners passing — no blocking security findings currently outstanding

**Open items needing YOUR judgment / inputs only you can provide:**
- **Commission an external pen test** covering the system boundary (Actions workflows, branch protection, merge-boundary controls, egress lockdown, supply-chain checks, model proxy integration)
- **Attach the pen test report** to this record under `compliance-evidence/pen-test/`
- **Track findings** in the risk register and remediate per change management policy
- (> un-evidenced: I cannot commission tests, receive reports, or validate findings)

**To sign:** edit the `assertion:` line in the ledger artifact to your own words, set `source: human-attested`, `assertion_author: <your login>`, `approver: <your login>` (+ attach the pen test report as the artifact-of-performance), then Approve. _I drafted this; the decision and the signature are yours._