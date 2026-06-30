# Onboarding/offboarding (deprovision <=24h) — 2027-06-29 (CC6.2, CC1.4)
**Process:** hr-onboard-offboard   **Cadence:** per-event   **Review date:** 2026-06-30   **Drafted by:** EA (compliance-drafter)
**Status:** DRAFT — record template only; world-act performed by HR

## What I gathered

This is a **WORLD-ACT** control. The EA cannot provision or deprovision real users. The
onboarding/offboarding record template below documents the process and the evidence artifacts
HR must attach after performing each joiner/mover/leaver event. Per SOC 2 policy:

- **CC6.2** — Register, authorize, and deprovision credentials. Offboarding requires revocation
  of all access (GitHub org, Cloudflare, provisioning/admin tokens, secret access) **the same day**
  as departure.
- **CC1.4** — Commitment to competence: onboarding ensures personnel have the training and
  documented access they need; offboarding ensures departed personnel no longer represent the org.

**Policy reference:** `compliance/policies/hr-security-policy.md` — key requirements:

| Phase | Requirement | Evidence |
|-------|-------------|----------|
| **Onboarding** | Background check (where lawful), signed acceptable-use acknowledgement, role-appropriate least-privilege access per `access-control-policy.md`, security-awareness training completion | Dated onboarding record + signed ack |
| **Offboarding** | Revoke all access (GitHub org, Cloudflare, provisioning/admin tokens, secret access) **same day**; rotate shared credentials | Dated offboarding record + ticket/receipt |
| **Role change (mover)** | Revoke access to old systems, grant access to new systems per new role; rotate shared credentials if needed | Dated mover record + ticket/receipt |

**Intended role matrix:** `compliance/policies/access-control-policy.md` documents least-privilege
and segregation of duties principles. The HR onboarding record should reference the role being
provisioned and map it to the access granted.

**No prior events recorded** — this is a per-event process; no joiner/mover/leaver events have
occurred to date.

## Onboarding/offboarding record template

For each personnel lifecycle event, HR completes the appropriate section(s):

```
## Personnel lifecycle record

**Employee/contractor name:** ____________________________
**Email / GitHub handle:** ____________________________
**Role / title:** ____________________________
**Manager:** ____________________________

### Event type
[ ] Onboard (new hire / new contractor)
[ ] Offboard (departure)
[ ] Role change / transfer (mover)

---

### SECTION A: ONBOARDING (complete for new joiners)

**Pre-requisite checklist (must complete before granting access):**
- [ ] Background check complete (where lawful) → ref #: __________________
- [ ] Acceptable-use policy acknowledgement signed → `compliance/policies/acceptable-use-policy.md`
- [ ] Security-awareness training assigned → completion target date: __________________
- [ ] Role documented in org structure → role: __________________

**Access provisioning:**
- [ ] GitHub org team added: __________________ (permission level: _____)
- [ ] Cloudflare account provisioned (if applicable)
- [ ] Model provider / agent access granted (if applicable)
- [ ] Secret store access granted (if applicable)
- [ ] Other: __________________

**Start date:** ____________________________

**Attestation (HR):**
_I confirm the pre-requisites were completed and access was provisioned following
least-privilege principles per the access control policy._
**Name:** ____________________________   **Date:** ____________________________

---

### SECTION B: OFFBOARDING (complete for departures)

**Last working date:** ____________________________

**Access revocation checklist (all must be completed SAME DAY):**
- [ ] GitHub org membership removed or suspended
- [ ] Cloudflare account revoked
- [ ] Model provider / agent access revoked
- [ ] Secret store / shared credential access revoked
- [ ] Shared credentials rotated (if applicable)
- [ ] Engineering token / personal access tokens revoked
- [ ] Email / collaboration tool access revoked
- [ ] Other: __________________

**Departure type:** [ ] Voluntary resignation  [ ] Termination  [ ] Contract end
**Exit interview completed:** [ ] Yes  [ ] No

**Attestation (HR):**
_I confirm all access was revoked on the same day as departure per policy (<24h)._
**Name:** ____________________________   **Date:** ____________________________

---

### SECTION C: ROLE CHANGE (complete for movers — internal transfer)

**Previous role:** __________________   **New role:** __________________
**Effective date:** __________________

**Access removed (old role):**
- [ ] Previous GitHub team(s) removed: __________________
- [ ] Previous Cloudflare access revoked
- [ ] Previous secret store permissions revoked
- [ ] Other: __________________

**Access granted (new role):**
- [ ] New GitHub team added: __________________ (permission level: _____)
- [ ] New Cloudflare account provisioned (if applicable)
- [ ] New secret store access granted (if applicable)
- [ ] Other: __________________

**Attestation (HR):**
_I confirm access was updated on effective date per least-privilege principles; old-role access
was revoked and new-role access was granted._
**Name:** ____________________________   **Date:** ____________________________
```

## Assessment

### Criteria coverage

| Criterion | Statement | Assessment (template) |
|-----------|-----------|----------------------|
| **CC6.2** — Register, authorize, and deprovision credentials | Onboarding/offboarding policy defines the process. De-provisioning must happen ≤24h of departure. | ✅ **Process defined.** Access-control and HR policies document the requirements. Template covers provisioning and same-day revocation. Actual execution to be confirmed by HR after each event. |
| **CC1.4** — Commitment to competence (attract/develop/retain) | Onboarding includes background check, policy acknowledgement, and training. | ✅ **Process defined.** Pre-requisite checklist covers all required elements. Security-awareness training assigned at onboarding ensures competence commitment. Actual completion to be confirmed by HR. |

### Overall status

**No events have occurred to date** — this is the first interval (effective_from: 2026-06-29).
All preparatory documentation (HR security policy, access control policy, training materials) is
in place and current. The template below is ready for use when the first joiner/mover/leaver
event occurs.

## Findings

### No findings from EA review — no events have occurred

The policies and template are documented and aligned with CC6.2 and CC1.4 requirements. No
deficiencies are visible in the documentation layer.

The actual onboarding/offboarding events may surface findings — those will be recorded in the
completed lifecycle records by HR.

## Open items needing the executive

1. **On each joiner event** — run through the onboarding checklist (background check, policy
   acknowledgement, training, least-privilege provisioning), complete Section A of the template,
   and attach or commit the completed record to `compliance-evidence/`.
2. **On each leaver event** — complete Section B of the template, revoke ALL access the **same day**
   (≤24h departure), rotate shared credentials, and attach or commit the completed record.
3. **On each mover/role-change event** — complete Section C, ensuring old-role access is revoked
   and new-role access follows least-privilege.
4. **Security-awareness training** — ensure new hires complete training within the first 30 days
   (linked to `security-training` annual process; record completion there as well).
5. **Quarterly access reviews** — the quarterly `access-review` process (CC6.2/CC6.3) acts as a
   detective control to catch any missed offboarding. Ensure those reviews continue on schedule.

## Coverage / gaps

- ✅ **HR Security Policy** — defined, current, covers onboarding/offboarding requirements.
- ✅ **Access Control Policy** — defined, current, covers least-privilege provisioning principles.
- ✅ **Onboarding/offboarding record template** — drafted (this document), covers all event types
  with complete checklists and attestation fields.
- `> ⚠️ **un-evidenced: no actual provisioning/deprovisioning events have occurred** — this
       is the record template only. HR must complete and attach the onboarding/offboarding
       lifecycle record for each personnel event as the artifact-of-performance.`
- `> ⚠️ **un-evidenced: shared credential rotation process** — offboarding requires rotating
       shared credentials the departed person held. HR should confirm the inventory of shared
       credentials (e.g., service account tokens, shared API keys) is maintained and rotation is
       feasible within <24h.`
- `> ⚠️ **un-evidenced: background check vendor due diligence** — the background check vendor
       should be included in the vendor-reassessment process (CC9.2). The org's HR or leadership
       must ensure the vendor has current SOC 2 or equivalent.`