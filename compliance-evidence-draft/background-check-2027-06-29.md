# Pre-employment background screening — 2027-06-29 (CC1.1, CC1.4)
**Process:** background-check   **Cadence:** per-event   **Review date:** 2026-06-30   **Drafted by:** EA (compliance-drafter)
**Status:** DRAFT — record template only; world-act performed by HR

## What I gathered

This is a **WORLD-ACT** control. The screening record template below documents the process and
the evidence artifacts HR must attach after performing the actual background check. Per SOC 2
policy (CC1.1 commitment to integrity & ethical values, CC1.4 commitment to competence), a
background check must be completed before granting system access to new personnel, where lawful.

**Policy reference:** `compliance/policies/hr-security-policy.md` — onboarding section states:
> "Before access is granted: background check where lawful, signed acceptable-use acknowledgement,
> and role-appropriate least-privilege access. Record the date."

## Screening record template

For each new hire requiring system access, HR completes the following record:

```
## Screening record

**Candidate name:** ____________________________
**Position / role:** ____________________________
**Screening vendor:** ___________________________
**Vendor reference / case ID:** _________________

**Check components completed (check all that apply):**
- [ ] Identity verification (government-issued ID)
- [ ] Criminal record / background history (jurisdiction: _______)
- [ ] Employment history verification
- [ ] Education / credential verification
- [ ] Professional reference checks
- [ ] Credit check (where lawful and role-relevant)
- [ ] Other: ____________________________

**Date initiated:** ____________________________
**Date completed:** ____________________________
**Result:**  [ ] Clear  [ ] Flagged (see attached)
**Flag details (if any):** ____________________________

**Attestation (HR):**
_I confirm the screening was performed per policy; results are attached._
**Name:** ____________________________   **Date:** ____________________________
**Signature:** ____________________________
```

## Coverage / gaps

- `> un-evidenced: needs the completed screening record with actual name, vendor, result, and
       HR attestation for each hire — attached by the executive/HR after performing the check`
- `> un-evidenced: needs the screening vendor SOC 2 / background-check program report on file
       (vendor due diligence per CC9.2) — HR or leadership collects`
- `> un-evidenced: for hires where a background check was not performed (jurisdictional
       prohibition, contractor scope), a documented rationale per policy is required`

## Findings
None (template only — no screening performed by this agent).

## Open items needing the executive
- **Perform screening**: for each hire, run the background check via the org's screening vendor,
  complete the template above, attach the vendor report / results to this PR or commit them to
  `compliance-evidence/`.
- **Vendor due diligence**: if the org uses a new vendor that hasn't been assessed, run a
  vendor risk assessment (see `vendor-reassessment` process) before engaging.
- **Policy updates**: if the screening policy (`hr-security-policy.md`) needs updating, do so
  during the annual `policy-review-ack` cycle.

## Artifacts-of-performance (to be attached by HR)
- [ ] Completed screening record (per template above)
- [ ] Vendor background-check report (PDF or secure link)
- [ ] Acceptable-use policy acknowledgement (signed)