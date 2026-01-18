# WFSL Compatibility Matrix

This matrix describes which WFSL components are designed to compose together,
which operate standalone, and which are experimental.

Compatibility is defined by **enforced integration**, not conceptual alignment.

---

## Legend

- **Authoritative**: Enforces or verifies outcomes used by other components
- **Composable**: Designed to be executed as part of a chain
- **Standalone**: Operates independently
- **Experimental**: Not part of the canonical enforcement chain

---

## Canonical Enforcement Chain (Tier 1)

| Component               | Role            | Depends On            | Enforced By           |
|------------------------|-----------------|-----------------------|-----------------------|
| wfsl-shell-guard       | Authoritative   | None                  | CI / Direct invocation|
| wfsl-evidence-guard    | Authoritative   | wfsl-shell-guard      | CI                    |
| wfsl-admission-guard   | Authoritative   | wfsl-shell-guard      | CI                    |
| wfsl-governance-chain  | Orchestrator    | All above             | CI                    |

---

## Trust and Authority Spine

| Component               | Role            | Composes With                     | Notes                           |
|------------------------|-----------------|-----------------------------------|---------------------------------|
| wfsl-trust-spec        | Authoritative   | licence, evidence, admission      | Defines trust semantics          |
| wfsl-licence-core      | Authoritative   | evidence, verification            | Authority over outputs           |
| WFSL-Licence-Engine    | Authoritative   | licence-core, verification        | Deterministic licence engine     |

---

## Supporting / Active Systems (Tier 2)

| Component                   | Role        | Compatibility                      |
|----------------------------|-------------|------------------------------------|
| wfsl-route-sentinel        | Composable  | admission, shell                   |
| wfsl-org-profile-guard    | Standalone  | evidence                            |
| wfsl-cloudflare-guard     | Composable  | shell, evidence                    |
| wfsl-repo-guard           | Standalone  | none                               |
| wfsl-control-plane        | Standalone  | governance tooling                 |
| wfsl-cross-verify         | Standalone  | evidence, licence                  |
| wfsl-guard-consumer-proof | Standalone  | evidence                           |
| wfsl-web                  | Interface   | none                               |

---

## Experimental / Parallel Lines (Tier 3)

| Component                     | Status        |
|------------------------------|---------------|
| triggerguard-*               | Experimental |
| wyneos-core / WyneOS         | Experimental |
| sentinel-*                   | Experimental |
| aletheseal-infrastructure   | Experimental |
| commercial-wfsl-*            | Experimental |

---

## Notes

- Only Tier 1 components form the **canonical proof chain**.
- Tier 2 components may be elevated if enforcement is added.
- Tier 3 components make no verification claims.

Compatibility claims are updated only when enforcement exists.
