## Decision brief — ir-tabletop (annual)
**Criteria:** CC7.3 (evaluate → determine incidents), CC7.4 (respond)   **Owner (you):** maintainer

**What I did:** Drafted the tabletop-exercise record template per the IR policy — this is a **world-act** control that only you (the executive) can perform. The template includes 4 exercise scenario candidates, a completed exercise record form to fill after the exercise, and a full coverage/gaps assessment of the documented IR posture.

**Evidence:** [compliance-evidence-draft/ir-tabletop-2027-06-29.md](compliance-evidence-draft/ir-tabletop-2027-06-29.md)

**Findings / anomalies:** None in the documentation layer — IR policy, SECURITY.md, detection channels (CodeQL, Dependabot, secret-scanning, supply-chain, heartbeat) are all defined and operational. The real findings will surface during the exercise.

**Open items needing YOUR judgment / inputs only you can provide:**
1. **Run the tabletop exercise** (≥1 scenario from the template or your own) before 2027-06-29
2. **Attach the completed exercise record** — fill in the template fields and commit the result
3. **Contact list** — the IR policy requires a maintained contact list for the incident commander + maintainers (not found in-repo; confirm it exists externally)
4. **If gaps are found** — update the risk register and assign remediation

**To sign:** After running the tabletop and filling the exercise record, edit the `assertion:` line in the ledger artifact to your own words, set `source: human-attested`, `assertion_author: <your login>`, `approver: <your login>`, then Approve. _I drafted the template; the decision, the exercise, and the signature are yours._