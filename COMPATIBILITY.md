\# WFSL Compatibility Matrix



This document defines which WFSL components compose and what signals they exchange.



\## Signals



\- SHELL\_OK  

&nbsp; Execution environment verified safe.



\- EVIDENCE\_EMITTED  

&nbsp; Deterministic evidence artefact produced.



\- ADMISSION\_OK  

&nbsp; Declared surface admitted, undeclared surface blocked.



---



\## Component Compatibility



| Component              | Requires        | Emits              | Composes With                    |

|-----------------------|-----------------|--------------------|----------------------------------|

| wfsl-shell-guard      | none            | SHELL\_OK           | All executable WFSL components   |

| wfsl-evidence-guard   | SHELL\_OK        | EVIDENCE\_EMITTED   | Shell Guard, Governance Chain    |

| wfsl-admission-guard  | SHELL\_OK        | ADMISSION\_OK       | Shell Guard, Evidence Guard      |

| wfsl-governance-chain | all above       | Combined proof     | All core components              |



---



\## Notes



Composition is enforced in CI using multi-repository checkout.

No component is duplicated or embedded.



