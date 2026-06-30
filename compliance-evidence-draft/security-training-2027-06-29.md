# Security-awareness training — 2027-06-29 (CC1.4/CC2.2)
**Process:** security-training   **Cadence:** annual   **Review date:** 2026-06-30   **Drafted by:** EA (compliance-drafter)
**Status:** DRAFT — executive review required before signing. **WORLD-ACT** — the record template only; the executive runs the training and attaches the completion artifact.

## What I gathered

This is a **world-act** control: security-awareness training must be *performed* (by a person delivering or administering content) and the *artifact-of-performance* (completion roster, LMS export, signed attestations) must be attached by the executive. I can only scaffold the record.

**Control references (from `compliance/control-register.yml`):**
- **CC1.4** — Commitment to competence (attract/develop/retain) → `compliance/policies/hr-security-policy.md`
- **CC2.2** — Internally communicate objectives & responsibilities → `compliance/policies/information-security-policy.md`

**Relevant policy excerpt (from `compliance/policies/hr-security-policy.md`):**
> *All personnel complete security training at onboarding and at least annually. Record completion.*

**Repository policies already installed and available for the training curriculum:**
- `compliance/policies/acceptable-use-policy.md`
- `compliance/policies/information-security-policy.md`
- `compliance/policies/hr-security-policy.md`
- `compliance/policies/incident-response-policy.md`
- `compliance/policies/data-classification-and-retention-policy.md`
- `compliance/policies/privacy-policy.md`
- `compliance/policies/access-control-policy.md`
- `compliance/policies/secure-sdlc-policy.md`
- `compliance/policies/change-management-policy.md`
- `compliance/policies/encryption-policy.md`
- `compliance/policies/risk-management-policy.md`
- `compliance/policies/vendor-management-policy.md`
- `compliance/policies/business-continuity-dr-policy.md`

**No prior training artifact exists in the ledger** (this is the first interval since `effective_from: 2026-06-29`).

> **Artifact needed** (`> un-evidenced`): the executive must provide the training-completion roster or LMS attestation as the artifact-of-performance — see **Coverage / gaps** below.

## Assessment

| Criteria | What it requires | Evidence needed |
|----------|-----------------|----------------|
| CC1.4 | Personnel are competent via training | Training completion record for all personnel |
| CC2.2 | Security responsibilities are communicated to personnel | Record that training content was delivered to all personnel |

This draft serves as the documentary record header. The substantive evidence — proof that training was conducted and attended — must be provided by the executive (HR owner).

## Findings

- **None from automated checks.** This is a world-act; no in-repo automated check can verify training completion.

## Open items needing the executive

- **> Run the annual security-awareness training.** The executive (HR owner) must schedule, conduct, and record the annual training session before the interval closes (2027-06-29). Recommended content: acceptable use, incident reporting, data classification, phishing awareness, password hygiene, and privacy obligations.
- **> Attach the completion artifact.** After running training, commit the completion roster (or LMS export, signed attestations, etc.) under `compliance-evidence/` (e.g., `compliance-evidence/security-training-2027-06-29-roster.md` or `.pdf`) and reference it in the ledger artifact. This is the required artifact-of-performance.

## Coverage / gaps

- ✅ Evidence doc header drafted — record template is in place.
- > **un-evidenced: Training delivery** — must be *performed* by the executive (HR owner). I cannot run training, collect sign-ins, or attest to attendance.
- > **un-evidenced: Completion roster** — the artifact-of-performance is external. The executive must attach the roster (LMS export, signed attendance sheet, or equivalent) and update the ledger artifact with the correct file path.
- > **un-evidenced: Content coverage** — the executive should ensure the training covers: acceptable use (AUP), information security policy, incident reporting procedures, data classification, and privacy obligations per `compliance/policies/`. The policies are in-repo and served as the curriculum scaffold above.