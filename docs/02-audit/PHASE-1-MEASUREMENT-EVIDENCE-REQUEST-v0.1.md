# CORTE IBÉRICO — Phase 1 Measurement Evidence Request

**Document:** `PHASE-1-MEASUREMENT-EVIDENCE-REQUEST-v0.1`
**Date:** 2026-10-07
**Status:** WORKING EVIDENCE REQUEST
**Project:** CORTE IBÉRICO / Meta Commerce / Christmas 2026
**Parent evidence matrix:** `docs/01-evidence/MASTER-EVIDENCE-DIAGNOSIS-DECISION-MATRIX.md`
**Related public audit:** `docs/01-evidence/CORTE-IBERICO-PUBLIC-WEB-MEASUREMENT-AUDIT-v0.1.md`

---

## 1. Objective

This document defines the minimum evidence required to move from the public-web preliminary measurement audit into a controlled Phase 1 measurement and commerce audit.

The objective is not to assume that tracking is broken, incomplete, correct, or incorrectly configured.

The objective is to establish, with reproducible evidence:

1. which commercial events actually occur;
2. which measurement systems receive those events;
3. whether browser and server-side events are correctly related and deduplicated;
4. whether purchase values, currencies and product identifiers are preserved;
5. how WhatsApp-assisted conversions are attributed and reconciled;
6. whether shipping thresholds and checkout conditions are consistent with the commercial rules presented to users.

No remediation or performance diagnosis should be promoted from hypothesis to finding until the corresponding evidence is available.

---

## 2. Evidence Boundary

This request covers the following validation items:

- **V-013** — Event chain across product, cart, checkout and purchase.
- **V-014** — CAPI activation and browser/server deduplication.
- **V-015** — Purchase value, currency and product identifier integrity.
- **V-016** — WhatsApp-originated lead and sales attribution/reconciliation.
- **V-017** — Shipping thresholds, offers and checkout consistency.

The public-web audit established only what can be observed from the public surface.

It did **not** establish:

- Meta Business Manager configuration;
- Ads Manager configuration;
- Events Manager configuration;
- Pixel event correctness;
- Conversions API correctness;
- browser/server deduplication;
- purchase value correctness;
- WooCommerce/ecommerce order integrity;
- payment reconciliation;
- WhatsApp attribution;
- CRM attribution;
- account-level campaign performance;
- attribution causality.

Those remain account-level or operational evidence requirements.

---

## 3. Evidence Classification

Every observation must retain its evidence status.

### VERIFIED

Directly supported by an inspectable source, export, configuration, controlled test or operational record.

### OBSERVED

Visible in the inspected surface but not sufficient to establish the underlying system state.

### OPEN

A validation question for which the required evidence has not yet been obtained.

### HYPOTHESIS

A technically plausible explanation that has not yet been demonstrated.

### UNKNOWN

The available evidence does not establish the state.

### NOT FOUND IN INSPECTED SURFACE

The item was not identified in the inspected surface. This does not prove that the item does not exist elsewhere.

---

## 4. Evidence Request — V-013

### V-013 — Event Chain

**Question**

What events actually fire across the customer journey:

`PRODUCT → CART → CHECKOUT → PURCHASE`

### Required evidence

Provide, where applicable:

1. GTM container export or equivalent configuration evidence.
2. Meta Events Manager event inventory.
3. Browser-side event observations.
4. Event parameters for:
   - `ViewContent`;
   - `AddToCart`;
   - `InitiateCheckout`;
   - `Purchase`;
   - any custom conversion events actually used.
5. Event timestamps from a controlled test.
6. Event identifiers where available.
7. Event source:
   - browser;
   - server;
   - other integration.
8. Test-event or diagnostic output showing receipt by Meta.

### Minimum acceptance condition

A valid V-013 result must allow the audit to identify, for at least one controlled journey:

`product view → cart → checkout → purchase`

and establish which measurement system receives each relevant event.

The existence of a Meta tracking reference in public HTML is not sufficient.

---

## 5. Evidence Request — V-014

### V-014 — Conversions API and Deduplication

**Question**

Is Conversions API active and, where browser and server events represent the same customer action, correctly deduplicated?

### Required evidence

Provide, where applicable:

1. Events Manager data-source configuration.
2. CAPI integration/configuration evidence.
3. Representative browser event.
4. Representative server event.
5. Shared event identifier or documented deduplication mechanism.
6. Events Manager diagnostics or test-event evidence.
7. Any documented warnings related to:
   - duplicate events;
   - missing event IDs;
   - poor event match quality;
   - event delivery failures;
   - server/browser disagreement.

### Minimum acceptance condition

The evidence must distinguish between:

- browser-only measurement;
- server-only measurement;
- browser + server measurement;
- browser + server measurement with demonstrated deduplication.

The mere presence of server-side code, API references or a claimed CAPI integration is not sufficient.

---

## 6. Evidence Request — V-015

### V-015 — Purchase Value, Currency and Product Identity

**Question**

Does the purchase event preserve the commercial truth represented by the actual ecommerce order?

### Required evidence

Provide a representative sample of real or authorized test orders containing, at minimum:

- order identifier;
- order timestamp;
- product identifier / SKU;
- product quantity;
- product price;
- subtotal;
- discount, where applicable;
- shipping amount;
- tax, where applicable;
- final order value;
- currency;
- payment status.

Provide the corresponding measurement payload or Events Manager representation for the same order.

### Reconciliation model

The audit must be able to compare:

`Ecommerce Order Value`
↔
`Purchase Event Value`
↔
`Actual Paid Order`

and, where applicable:

`Product / SKU`
↔
`Measured Product Identifier`

### Minimum acceptance condition

No purchase-value finding should be issued unless the order and corresponding measurement evidence can be linked or otherwise reconciled with sufficient confidence.

### Privacy requirement

Do not provide:

- passwords;
- API keys;
- access tokens;
- CVV;
- complete payment-card information;
- unnecessary customer personal data.

Use anonymised or pseudonymised identifiers where possible.

---

## 7. Evidence Request — V-016

### V-016 — WhatsApp-Originated Conversion Attribution

**Question**

How are WhatsApp-originated leads and sales attributed and reconciled?

The public surface contains commercially relevant WhatsApp conversion paths.

This establishes the existence of a human-assisted conversion mechanism, not its attribution quality.

### Required evidence

Provide, where available:

1. WhatsApp entry/source.
2. Campaign or UTM information.
3. Landing page or originating URL.
4. Lead timestamp.
5. Internal lead identifier.
6. Quote/proposal identifier, where applicable.
7. Order/CRM identifier, where applicable.
8. Final commercial outcome:
   - no sale;
   - quote;
   - sale;
   - cancelled;
   - pending.
9. Revenue associated with the converted lead.
10. Attribution/reconciliation method currently used.

A representative sample should be sufficient to establish the current operating model. Personal data should be minimised and anonymised/pseudonymised wherever practical.

### Minimum acceptance condition

The audit must be able to describe the actual reconciliation path:

`SOURCE → WHATSAPP LEAD → QUALIFICATION → QUOTE → SALE → REVENUE`

If one or more links are unavailable, the missing link must remain explicitly marked as `UNKNOWN` or `OPEN`.

No claim should be made that Meta receives or correctly attributes WhatsApp-originated revenue without evidence establishing that relationship.

---

## 8. Evidence Request — V-017

### V-017 — Shipping Threshold and Checkout Consistency

**Question**

Are shipping thresholds, delivery methods and offers presented publicly consistent with the actual checkout calculation?

### Required evidence

Execute controlled checkout tests covering representative scenarios.

At minimum, capture:

1. destination;
2. cart contents;
3. cart subtotal;
4. applied discount;
5. available shipping methods;
6. shipping cost;
7. free-shipping threshold;
8. final payable total;
9. checkout timestamp;
10. screenshots or equivalent reproducible evidence.

Where multiple shipping contexts exist, test each relevant context separately.

### Current public observation

The public website currently exposes shipping messaging around:

- `1,825 MXN`;
- `2,999 MXN`.

These values are not currently treated as contradictory findings.

They require controlled checkout validation.

### Minimum acceptance condition

The audit must establish whether the public shipping statements correspond to the actual checkout calculation for the relevant destination and delivery method.

Do not infer business-rule inconsistency solely from different public messages.

---

## 9. Required Access

Where relevant to the validation item, Phase 1 requires controlled access to:

### Meta

- Meta Business Manager / Business Portfolio;
- Ads Manager;
- Events Manager;
- Commerce Manager;
- relevant Pixel/data sources;
- relevant ad accounts;
- relevant catalogues;
- relevant permissions.

### Web measurement

- Google Tag Manager;
- analytics platform;
- relevant consent-management configuration;
- browser-side measurement configuration.

### Ecommerce

- ecommerce/WooCommerce administration;
- product catalogue;
- orders;
- checkout configuration;
- shipping configuration;
- discount rules.

### Commercial reconciliation

- payment provider;
- order records;
- CRM or lead-management system;
- WhatsApp operational records where relevant.

Access must be granted through controlled client-owned accounts and least-privilege permissions where practical.

Credentials, tokens and secrets must never be placed in the repository or evidence package.

---

## 10. Controlled Browser Test

The Phase 1 browser test should use a clean or controlled browser environment.

### Test sequence

1. Open the relevant public website.
2. Record consent state before interaction.
3. Record consent action, if required.
4. Open a representative product.
5. Observe `ViewContent` or equivalent event.
6. Add the product to cart.
7. Observe `AddToCart` or equivalent event.
8. Start checkout.
9. Observe `InitiateCheckout` or equivalent event.
10. Complete a test purchase only if explicitly authorised.
11. Observe `Purchase` or equivalent event.
12. Record timestamps and relevant event identifiers.
13. Compare browser-side observations with Events Manager/test-event evidence.
14. Preserve raw evidence before interpretation.

No real transaction should be executed without explicit client authorisation.

---

## 11. WhatsApp Test

Where the conversion path uses WhatsApp:

1. enter through the relevant public CTA;
2. record the originating URL;
3. preserve available UTM/source information;
4. record the lead timestamp;
5. identify the internal lead record;
6. follow the lead through qualification;
7. identify quote/order state where available;
8. reconcile final commercial outcome;
9. document which system owns each stage.

The test must distinguish:

`click / conversation start`

from:

`qualified lead`

from:

`sale`

from:

`reconciled revenue`.

These are not interchangeable metrics.

---

## 12. Evidence Acceptance Criteria

An evidence item is acceptable when it has sufficient provenance to be independently reviewed.

At minimum record:

- evidence identifier;
- source system;
- date/time;
- environment;
- responsible owner;
- relevant account/property;
- artifact type;
- collection method;
- redaction status;
- interpretation status.

Where an artifact is stored as a file, preserve its original file and, where practical, record a cryptographic hash.

Recommended evidence package structure:

```text
evidence/
  phase1/
    measurement/
    ecommerce/
    whatsapp/
    checkout/
    meta/
Raw evidence should not be silently modified after collection.

If redaction is required, preserve the distinction between:

RAW EVIDENCE

and:

REDACTED EVIDENCE.

13. What Is Not Acceptable as Sole Evidence

The following are insufficient on their own:

screenshots of the public website;
presence of a Meta Pixel reference;
presence of GTM;
public JavaScript references;
a statement that CAPI is installed;
a statement that tracking is correct;
a statement that attribution is correct;
campaign screenshots without underlying event evidence;
aggregate platform metrics without ecommerce reconciliation;
a single example used to generalise account behaviour;
public documentation used as proof of account configuration.
14. Interpretation Prohibitions

Until the required evidence is obtained, the audit must not assert as fact:

that Meta tracking is broken;
that CAPI is missing;
that CAPI is incorrectly deduplicated;
that Purchase is incorrectly valued;
that Meta attribution is wrong;
that WhatsApp revenue is lost;
that a particular campaign caused a particular sale;
that a specific Meta algorithm or internal mechanism caused a result;
that shipping configuration is contradictory;
that one public catalogue surface is obsolete, duplicated, staging or authoritative.

Those may become findings only after evidence supports them.

15. Public Catalogue Surface Discrepancy

The public audit identified more than one ecommerce surface.

The inspected public website includes a /tienda/ surface previously indexed with a reported 47-result count, while /tienda-corteiberico/ exposes a separate product listing with materially different visible inventory.

Current public evidence therefore establishes:

MULTIPLE PUBLIC COMMERCE SURFACES = OBSERVED

It does not establish:

duplicate catalogue;
staging catalogue;
obsolete catalogue;
production catalogue;
synchronisation failure;
administrative ownership;
intended customer journey.

This discrepancy must be validated against the ecommerce administration before being converted into a diagnosis.

16. Phase 1 Deliverable

After evidence collection, produce an updated evidence matrix containing, for V-013 through V-017:

Validation	Status	Evidence	Finding	Confidence	Next Action
V-013	OPEN / VERIFIED / FAILED	Evidence IDs	Evidence-backed finding	HIGH / MEDIUM / LOW	Action
V-014	OPEN / VERIFIED / FAILED	Evidence IDs	Evidence-backed finding	HIGH / MEDIUM / LOW	Action
V-015	OPEN / VERIFIED / FAILED	Evidence IDs	Evidence-backed finding	HIGH / MEDIUM / LOW	Action
V-016	OPEN / VERIFIED / FAILED	Evidence IDs	Evidence-backed finding	HIGH / MEDIUM / LOW	Action
V-017	OPEN / VERIFIED / FAILED	Evidence IDs	Evidence-backed finding	HIGH / MEDIUM / LOW	Action

The resulting diagnosis must preserve the distinction between:

OBSERVATION → EVIDENCE → FINDING → INFERENCE → HYPOTHESIS → ACTION

17. Decision Gate

Phase 1 should not move directly into optimisation or Christmas execution based solely on the public audit.

The preferred sequence is:

PUBLIC WEB EVIDENCE
        ↓
PHASE 1 ACCOUNT / SYSTEM EVIDENCE
        ↓
MEASUREMENT VALIDATION
        ↓
COMMERCE RECONCILIATION
        ↓
EVIDENCE-BACKED DIAGNOSIS
        ↓
CONTROLLED REMEDIATION
        ↓
PERFORMANCE / GROWTH EXECUTION

The commercial execution layer must inherit the validated measurement model.

The measurement layer must not be retrofitted after performance claims are made.

18. Immediate Collection Order

Recommended order:

Confirm controlled access and ownership.
Inventory Meta assets and data sources.
Validate GTM and browser events.
Validate Events Manager event reception.
Validate CAPI and deduplication.
Reconcile ecommerce orders against Purchase events.
Trace WhatsApp-originated leads through commercial outcome.
Test shipping thresholds and checkout calculations.
Resolve public catalogue-surface discrepancy.
Update the master evidence matrix.
Produce evidence-backed diagnosis.
Only then define remediation and Christmas execution priorities.
19. Final Principle

The purpose of Phase 1 is not to prove that the current implementation is wrong.

The purpose is to determine, with sufficient evidence, what is actually true.

No missing evidence should be silently replaced by assumptions.

No public observation should be promoted to account-level fact.

No platform metric should be treated as economic truth without reconciliation to the underlying commercial system.
