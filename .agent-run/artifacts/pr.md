## Decision brief — vendor-reassessment (annual)
**Criteria:** CC9.2, P6.4, P6.5   **Owner (you):** leadership

**What I did:** Parsed `compliance/subprocessors.md` for SOC 2 report and DPA dates across all 7 listed entities. Cross-referenced against `vendor-management-policy.md`. No actual dates exist in the inventory — all SOC 2 report entries are qualitative ("Yes", "Verify") and all DPA entries are `[link]` placeholders.

**Evidence:** [Evidence doc](compliance-evidence-draft/vendor-reassessment-2027-06-29.md) — full analysis with per-subprocessor table, risk tiers, and flagged items.

**Findings / anomalies:**
- 🔴 **SOC 2 reports missing (5/5 data-processing subprocessors):** None collected or committed. GitHub and Cloudflare reports exist at their trust centers but not downloaded. Proxy, OpenRouter, and model providers are completely unverified.
- 🔴 **No signed DPAs on file (6/6 requiring one):** All entries are placeholder `[link]`. Legal DPAs not signed.
- 🔴 **High-risk chain (proxy → OpenRouter → model providers) completely unevidenced:** This is where source code leaves the repo boundary in-flight.
- ⚠️ **Subprocessors.md header placeholder** (`[OWNER]`, `[DATE]`) and compliance platform row unresolved.

**Open items needing YOUR judgment / inputs only you can provide:**
1. **Collect SOC 2 reports** from GitHub Trust Center, Cloudflare Trust Hub, the proxy operator, OpenRouter, and each model provider. Commit to `compliance-evidence/`.
2. **Sign DPAs** with all data-processing subprocessors. Commit signed copies.
3. **Fill inventory metadata** — set owner name and review date in `compliance/subprocessors.md`.
4. **Resolve compliance platform** placeholder if a platform has been onboarded.

**To sign:** Edit the `assertion:` line in `compliance/evidence-ledger.yml` under `vendor-reassessment` to your own words, set `source: human-attested`, `assertion_author: <your login>`, `approver: <your login>`, commit the collected SOC 2 reports and signed DPAs as artifacts-of-performance, then Approve. _I drafted this; the decision and the signature are yours._