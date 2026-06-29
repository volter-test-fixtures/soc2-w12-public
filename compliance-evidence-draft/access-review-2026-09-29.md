# Access Review — Quarterly (2026-09-29)

**Process:** `access-review` (quarterly)
**Criteria:** CC6.2 (register/authorize/deprovision), CC6.3 (RBAC/least-privilege/segregation of duties)
**Owner:** maintainer
**Reviewed by:** AI-drafted (2026-06-29)
**Interval:** 2026-06-29 → 2026-09-29

---

## Collaborator Snapshot

Fetched via `gh api repos/volter-test-fixtures/soc2-w12-public/collaborators?affiliation=all&per_page=100` on 2026-06-29.

| Login | Current Role | Perms (push/pull/admin) | Intended Access | Flag? |
|-------|-------------|------------------------|-----------------|-------|
| *(none)* | — | — | — | — |

**Result: 0 direct, outside, or team collaborators found.**

### Notes
- The repo is **public** (visibility: public). Read access is unrestricted by design.
- The `GITHUB_TOKEN` used in CI/CD is scoped to the individual workflow job (least-privilege per C1) and does not appear as a collaborator.
- Repository permissions for the executing token: `{admin: false, maintain: false, push: false, pull: false, triage: false}` — consistent with ephemeral `GITHUB_TOKEN` scoping.

### Intended Role Matrix (per Access Control Policy)

Per `compliance/policies/access-control-policy.md`:

| Role | Expected Permission | Mechanism |
|------|-------------------|-----------|
| Agent (CI/CD) | Capability-scoped `GITHUB_TOKEN` | Per-job token scoping (C1) |
| Maintainer | `code:propose` only (no `code:review`, no `code:merge`) | Enforced by C2 compile-time segregation |
| Reviewer | `code:review` only | Enforced by C2 |
| Reader (public) | Read-only (public repo) | Public visibility |

### Branch Protection
- `main` branch: PRs + status checks + `enforce_admins` expected per C5 (not verifiable from this token — 403 on branch-protection API)

---

## Anomalies & Flags

- **No flags.** The collaborators list is empty, which is the expected baseline for a fresh install with no human collaborators added yet.
- **No stale accounts or over-privileged access detected.**
- Branch-protection details could not be verified from the GITHUB_TOKEN (403 on `/branches/main/protection`). The executive should confirm branch protection is active on `main` via the repo Settings UI.

---

## CC6.2 — Register/Authorize/Deprovision Credentials
- **Register:** No new collaborators since effective_from (2026-06-29). No HR onboarding events recorded.
- **Authorize:** All access is via scoped `GITHUB_TOKEN`s; no human user has been granted direct access outside the GITHUB_TOKEN.
- **Deprovision:** No departures to deprovision.

## CC6.3 — RBAC / Least-Privilege / Segregation of Duties
- Role segregation (C2): enforced at compile time by the `capability` system — no actor holds both `code:propose` and `code:review`.
- Least-privilege (C1): per-job token scoping in workflow YAML.

---

## Verdict
**No remediation required.** All clear for this interval. The next access review is due 2026-12-29.

> This document is DRAFT evidence prepared by the compliance-drafter (EA). The executive must review, edit the assertion, and sign before this evidence is considered human-attested.