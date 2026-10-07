# CORTE IBÉRICO — Evidence Intake Register

## Purpose

This register defines the evidence currently available for the CORTE IBÉRICO
project, the evidence that has been identified but is not present in the
repository, and the evidence required to validate material technical and
commercial conclusions.

The register prevents three different states from being conflated:

1. Evidence actually available.
2. Evidence referenced or expected but not currently available.
3. Evidence required to validate an open claim.

A source being mentioned in project documentation does not mean that the
underlying evidence has been independently verified.

---

## Evidence and Validation Status Vocabulary

| Status | Meaning |
|---|---|
| `PRESENT` | Evidence is currently available and identifiable in the repository or current project context. |
| `REGISTERED` | Evidence is identified by reference but the underlying material is not stored in this repository. |
| `MISSING` | Evidence is required or expected but has not yet been obtained. |
| `PENDING_VALIDATION` | Evidence is available but has not yet been independently validated for the relevant claim. |
| `VALIDATED` | Evidence has been checked and is sufficient for the stated claim. |
| `NOT_APPLICABLE` | Evidence is not required for the stated scope. |
| `INTEGRITY_CHECKED` | Repository artefact existence, content integrity or provenance has been checked; this does not validate the underlying business or technical claim. |

---

## 1. Documentary Evidence Currently Registered

| ID | Evidence | Status | Source | Validation State | Notes |
|---|---|---|---|---|---|
| EI-001 | `a_CORTE IBERICO · Contexto y metodología.pdf` | `REGISTERED` | `SRC-001` | `PENDING_VALIDATION` | Documentary project material; not automatically treated as account evidence. |
| EI-002 | `b_CORTE IBERICO META-002 — Cómo se convierte la frontera en un proceso operativo.pdf` | `REGISTERED` | `SRC-002` | `PENDING_VALIDATION` | Contains Meta evidence boundary and technical research material. |
| EI-003 | `c_CORTE IBERICO · Perímetro técnico y cadena comercial.pdf` | `REGISTERED` | `SRC-003` | `PENDING_VALIDATION` | Contains technical perimeter, funnel, measurement and execution material. |
| EI-004 | `d_CORTE IBERICO · Contexto de las siguientes capturas.pdf` | `REGISTERED` | `SRC-004` | `PENDING_VALIDATION` | Contextual material for Meta documentation, Andromeda and scaling claims. |
| EI-005 | `e_CORTE IBÉRICO · PROPUESTA COMERCIAL Y MODELOS DE CONTRATACIÓN.pdf` | `REGISTERED` | `SRC-005` | `PENDING_VALIDATION` | Pre-contractual proposal; does not establish contractual acceptance. |

### Source Integrity

The five documentary sources are registered in `SOURCE-REGISTER.md` with:

- source identifier;
- filename;
- receipt date;
- page count;
- SHA-256 hash;
- documentary class;
- registration status;
- documentary role.

The underlying PDFs remain outside the Git repository because they may contain
sensitive or proprietary project material.

---

## 2. Evidence Present in the Repository

| ID | Evidence | Status | Validation State | Scope |
|---|---|---|---|---|
| EI-006 | Master Evidence → Diagnosis → Decision Matrix | `PRESENT` | `INTEGRITY_CHECKED` | Evidence governance and project traceability |
| EI-007 | Source Register | `PRESENT` | `INTEGRITY_CHECKED` | Documentary source registration |
| EI-008 | Claim Validation Register | `PRESENT` | `INTEGRITY_CHECKED` | Claim status and required validation |
| EI-009 | Git history documenting foundation creation | `PRESENT` | `INTEGRITY_CHECKED` | Repository provenance |
| EI-010 | GitHub remote publication state | `PRESENT` | `INTEGRITY_CHECKED` | Repository publication/provenance |

`INTEGRITY_CHECKED` in this section refers to the existence, content integrity
or provenance of the repository artefact itself. It does not validate the
business or technical claims contained in the project documentation.

---

## 3. Account-Level Evidence Not Yet Obtained

The following evidence is required before account-specific technical
conclusions can be treated as established.

| ID | Required Evidence | Status | Required For |
|---|---|---|---|
| EI-011 | Meta Business Manager / Business Portfolio inventory | `MISSING` | Asset and ownership audit |
| EI-012 | Meta Ad Account inventory and identifiers | `MISSING` | Account audit |
| EI-013 | Current user/role/permission inventory | `MISSING` | Access and responsibility audit |
| EI-014 | Current campaign structure and configuration | `MISSING` | Campaign diagnosis |
| EI-015 | Historical campaign performance data | `MISSING` | Performance comparison |
| EI-016 | Current Meta Pixel configuration | `MISSING` | Measurement diagnosis |
| EI-017 | Current Conversions API configuration | `MISSING` | Measurement diagnosis |
| EI-018 | Events Manager event quality / diagnostics | `MISSING` | Event integrity validation |
| EI-019 | Ecommerce platform and checkout configuration | `MISSING` | End-to-end measurement audit |
| EI-020 | Independent transaction / sales records | `MISSING` | Meta-to-sale reconciliation |
| EI-021 | Historical commercial results and baseline | `MISSING` | Performance diagnosis |
| EI-022 | Current media budget and scaling constraints | `MISSING` | Commercial/media planning |
| EI-023 | Christmas 2026 commercial objective | `MISSING` | Scope and planning |
| EI-024 | Product availability and operational capacity | `MISSING` | Feasibility and scaling |
| EI-025 | Explicit audit vs execution scope | `MISSING` | Responsibility and proposal boundary |

---

## 4. Security Evidence

| ID | Security Event | Status | Required Evidence |
|---|---|---|---|
| EI-026 | Temporary GitHub credential created for Corte Ibérico repository access | `REGISTERED` | Existing project/email evidence outside this repository |
| EI-027 | Revocation of temporary GitHub credential | `MISSING` | GitHub security/audit evidence or equivalent confirmation |

### Security Rule

The existence of a credential creation event must not be interpreted as evidence
of continued access, and the absence of a revocation record must not be
interpreted as proof that the credential remains active.

Until revocation is independently established, the item remains:

`OPEN — REVOCATION NOT VERIFIED`

No credential value is stored in this repository.

---

## 5. Claim-to-Evidence Gaps

The current open claims require the following evidence boundaries:

| Claim | Required Evidence | Current State |
|---|---|---|
| `CV-001` | Official Meta documentation plus applicable primary legal/regulatory source | `OPEN` |
| `CV-002` | Account data, campaign objective, historical baseline and controlled comparison | `OPEN` |
| `CV-003` | Official Meta documentation or reproducible controlled evidence | `OPEN` |
| `CV-004` | Account-level evidence plus official Meta documentation | `OPEN` |
| `CV-005` | Authorized account access and account-level audit | `OPEN` |
| `CV-006` | Events Manager, implementation inspection and transaction reconciliation | `OPEN` |
| `CV-007` | Signed agreement or explicit contractual acceptance | `OPEN` |
| `CV-008` | GitHub security/audit evidence or equivalent revocation confirmation | `OPEN` |

---

## 6. Evidence Boundary

The current repository establishes a documentary and governance foundation.

It does **not** currently establish:

- the current state of the Corte Ibérico Meta account;
- the correctness or incorrectness of the current Meta configuration;
- the current state of Pixel or Conversions API instrumentation;
- the causal mechanism behind any historical campaign outcome;
- the existence of undocumented Meta scaling thresholds;
- the contractual acceptance of the proposed commercial phase.

Those conclusions require additional evidence.

---

## 7. Gate to Diagnosis

The project may begin a formal diagnosis only when the minimum evidence
required for the specific diagnosis has been obtained.

A diagnosis may be partial and evidence-bounded.

The following rule applies:

> No account-level diagnosis without account-level evidence.

The following rule also applies:

> No causal attribution without evidence capable of supporting causality.

---

## 8. Immediate Evidence Actions

1. Close or independently verify the temporary GitHub credential revocation.
2. Obtain authorized Meta account/business access or equivalent account exports.
3. Inventory Meta assets, permissions and campaign structure.
4. Obtain current measurement configuration and Events Manager evidence.
5. Obtain independent sales/transaction reconciliation data.
6. Obtain the minimum business inputs required for the Christmas 2026 scope.
7. Map each obtained artefact to the relevant `EI-*`, `CV-*` and `E-*` identifiers.
8. Only then promote supported findings into the diagnosis layer.

---

## 9. Change Control

Any new evidence should update:

1. this register;
2. `SOURCE-REGISTER.md` where a new documentary source is introduced;
3. `CLAIM-VALIDATION-REGISTER.md` where claim status changes;
4. `MASTER-EVIDENCE-DIAGNOSIS-DECISION-MATRIX.md` where the evidence changes a
   diagnosis, decision or validation queue.

Evidence must never be silently replaced or reclassified.
