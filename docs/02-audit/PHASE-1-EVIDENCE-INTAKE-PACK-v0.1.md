# CORTE IBÉRICO — Phase 1 Evidence Intake Pack

**Version:** v0.1
**Date:** 2026-10-07
**Status:** DRAFT — Operational Intake
**Related Request:** `docs/02-audit/PHASE-1-MEASUREMENT-EVIDENCE-REQUEST-v0.1.md`

---

## 1. Purpose

This document converts the Phase 1 Measurement Evidence Request into an
operational evidence-intake procedure.

It defines:

- what evidence must be supplied or made available;
- how evidence must be identified;
- which controlled tests must be performed;
- which evidence is required for validations `V-013` through `V-017`;
- the boundary between Client responsibilities and Clarity responsibilities;
- the conditions required before evidence can support a diagnosis.

This document does not constitute an account-level diagnosis.

It does not authorize configuration changes, campaign changes, tracking
changes or production remediation.

---

## 2. Evidence Boundary

The project currently has:

- documentary project material;
- repository governance artefacts;
- public-web observations;
- a defined evidence model;
- an explicit Phase 1 measurement validation queue.

The project does not yet establish:

- the current Meta account configuration;
- the correctness of Pixel or Conversions API implementation;
- the correctness of purchase values or currencies;
- the correctness of event deduplication;
- the attribution of WhatsApp-originated sales;
- the consistency of shipping and checkout rules.

Those states require account, system and transaction evidence.

The following distinction remains mandatory:

`PUBLIC_META_DOCUMENTATION != ACCOUNT_EVIDENCE`

`ACCESS != CONFIGURATION_VALIDATION`

`VISIBLE_ASSET != FUNCTIONAL_MEASUREMENT`

`VISIBLE_CATALOG != VALID_TRANSACTION_CHAIN`

`DOCUMENTED != IMPLEMENTED != TESTED != VALIDATED != PRODUCTION_OWNED`

---

## 3. Evidence Submission Rules

### 3.1 Accepted evidence

Evidence may be supplied as:

- native platform exports;
- screenshots showing relevant configuration or diagnostics;
- controlled browser-test captures;
- ecommerce order records;
- payment/order reconciliation extracts;
- GTM container exports;
- structured CSV/XLSX exports;
- documented API output where authorized;
- CRM/WhatsApp attribution records;
- written confirmation only where the underlying state cannot reasonably be
  evidenced otherwise.

Written statements alone should not be used as sole evidence for technical
configuration or transaction truth where direct evidence is available.

### 3.2 Security restrictions

Do not place any of the following in the repository or ordinary project
messages:

- passwords;
- API keys;
- access tokens;
- session cookies;
- recovery codes;
- payment-card data;
- unnecessary personal data.

Credentials must be provided only through an approved access mechanism.

Raw evidence containing unnecessary personal or financial data should be
redacted before repository storage.

### 3.3 Evidence provenance

Every submitted artefact must retain:

- source system;
- collection date;
- collector or responsible party;
- relevant account / property / environment;
- original filename where applicable;
- evidence identifier;
- raw/redacted status.

Evidence must not be silently replaced or reclassified.

---

## 4. Client Evidence Submission Checklist

### 4.1 Meta Business

Provide or authorize access to:

- Meta Business Portfolio;
- Business assets;
- Ad Accounts;
- Pages;
- Instagram assets where relevant;
- datasets / Pixel assets;
- Catalog / Commerce assets;
- current users and permissions.

Required outcome:

> Establish the actual asset inventory and ownership boundary.

---

### 4.2 Ads Manager

Provide:

- current campaigns;
- campaign objectives;
- ad sets;
- ads;
- relevant date ranges;
- spend;
- impressions;
- clicks;
- landing-page views where available;
- leads;
- purchases;
- reported purchase value where available.

Historical data should be supplied for the period required to establish a
meaningful baseline.

---

### 4.3 Events Manager

Provide:

- dataset / Pixel identity;
- event inventory;
- event diagnostics;
- event match quality where available;
- browser/server event sources;
- Purchase event configuration;
- deduplication diagnostics where available;
- recent event activity.

---

### 4.4 Conversions API

Provide evidence sufficient to establish:

- whether server-side events are active;
- which events are sent server-side;
- event identifiers used for deduplication;
- browser/server relationship;
- deduplication behaviour;
- implementation ownership.

The existence of a server-side integration alone is not sufficient to establish
correctness.

---

### 4.5 GTM / Web Measurement

Provide:

- GTM container export where available;
- relevant tags;
- triggers;
- variables;
- consent configuration;
- Meta-related tags;
- ecommerce-related tags;
- relevant custom scripts where they affect measurement.

Secrets must be removed before submission.

---

### 4.6 Ecommerce

Provide:

- ecommerce platform identification;
- product/catalogue configuration;
- cart behaviour;
- checkout configuration;
- order structure;
- purchase event implementation;
- shipping rules;
- currency configuration;
- relevant tax configuration.

The authoritative ecommerce system must be identified.

If multiple public ecommerce surfaces exist, their status must be explicitly
classified as:

- authoritative;
- secondary;
- staging;
- legacy;
- campaign-specific;
- unknown.

No classification should be inferred solely from public appearance.

---

### 4.7 Transaction / Payment Reconciliation

Provide a representative transaction sample containing, where available:

- order ID;
- product ID;
- product;
- quantity;
- order value;
- currency;
- payment status;
- order timestamp;
- purchase-event timestamp;
- purchase-event value;
- purchase-event currency.

Payment information should demonstrate paid-order truth without exposing
unnecessary payment credentials or card data.

---

### 4.8 WhatsApp / CRM

Provide, where applicable:

- campaign/source identifier;
- WhatsApp click or conversation;
- qualified lead;
- customer;
- order;
- revenue;
- attribution method.

The following must remain separate:

`CLICK != CONVERSATION != QUALIFIED LEAD != SALE != REVENUE`

---

### 4.9 Checkout / Shipping

Provide evidence for at least the relevant delivery contexts covering:

- destination;
- cart value;
- shipping method;
- shipping charge;
- free-shipping threshold;
- final checkout total.

The publicly observed values `1,825` and `2,999` remain observations pending
dynamic checkout validation.

---

## 5. Controlled Browser Test

The controlled browser test must be performed in an environment where the
relevant measurement implementation can be observed.

### 5.1 Test preparation

Record:

- test date/time;
- browser;
- device type;
- consent state;
- test environment;
- product selected;
- test order identifier if an order is completed.

Do not use real customer personal data.

---

### 5.2 Test sequence

Perform, where technically possible:

1. Open the authoritative product page.
2. Record the product identity and displayed price.
3. Observe consent behaviour.
4. Trigger product-view behaviour.
5. Add the product to cart.
6. Observe cart state.
7. Initiate checkout.
8. Record checkout totals.
9. Complete a controlled purchase where authorized.
10. Record the resulting order identifier.
11. Verify the resulting ecommerce order.
12. Inspect relevant browser/network measurement evidence.
13. Inspect relevant server-side evidence where available.
14. Compare the purchase event with the actual paid order.

The test must not be interpreted as representative of campaign performance.

Its purpose is measurement and transaction-chain validation.

---

## 6. V-013 → V-017 Intake Matrix

| Validation | Evidence Required | Primary Source | Acceptance Question | Status |
|---|---|---|---|---|
| `V-013` Event Chain | Browser event evidence, ecommerce event evidence, controlled test | Website / GTM / Events Manager | Can the event chain from product interaction to purchase be demonstrated? | `OPEN` |
| `V-014` CAPI / Deduplication | Events Manager evidence, implementation evidence, event IDs | Meta / server implementation | Can browser/server event relationship and deduplication be demonstrated? | `OPEN` |
| `V-015` Purchase Truth | Order sample, payment status, Purchase event and value/currency | Ecommerce / payment / Meta | Can Purchase data be reconciled with actual paid orders? | `OPEN` |
| `V-016` WhatsApp Attribution | Source, conversation, qualified lead, sale and revenue records | WhatsApp / CRM / commercial records | Can WhatsApp-originated commercial outcomes be traced and reconciled? | `OPEN` |
| `V-017` Checkout / Shipping | Controlled checkout observations by relevant destination/cart | Ecommerce / checkout | Are shipping rules and displayed thresholds consistent with actual checkout behaviour? | `OPEN` |

---

## 7. Evidence Acceptance Criteria

Evidence can support a validation only when it is:

1. identifiable;
2. attributable to the relevant system or source;
3. temporally relevant;
4. sufficiently complete for the stated claim;
5. internally consistent;
6. reproducible where the validation requires a controlled test;
7. capable of supporting the specific conclusion being made.

Evidence quality must be evaluated against the claim.

A screenshot proving that a Pixel exists does not prove that Purchase is
correct.

An event firing does not prove that its value is correct.

A Purchase event does not prove that the underlying order was paid.

A WhatsApp conversation does not prove a sale.

---

## 8. Client Responsibilities

The Client is responsible for:

- authorizing access;
- providing accurate account/system information;
- providing required exports;
- providing transaction evidence;
- providing access to the relevant ecommerce and commercial systems;
- identifying authoritative systems;
- approving controlled purchases where required;
- protecting credentials;
- confirming operational constraints;
- confirming the commercial scope and decision authority.

The Client remains the owner of its accounts, business assets and commercial
data.

---

## 9. Clarity Responsibilities

Clarity is responsible for:

- defining the evidence requirements;
- maintaining the evidence boundary;
- designing the controlled validation procedure;
- reviewing submitted evidence;
- recording evidence provenance;
- mapping evidence to `EI-*`, `CV-*`, `E-*` and `V-*` identifiers;
- identifying inconsistencies and evidence gaps;
- performing evidence-bounded technical analysis;
- producing the resulting diagnosis only where the evidence supports it.

Clarity must not represent missing evidence as validated account state.

---

## 10. Evidence Intake Status

Each requested item should use one of the following states:

`REQUESTED`

`RECEIVED`

`PENDING_VALIDATION`

`VALIDATED`

`INSUFFICIENT`

`CONFLICTING`

`MISSING`

`NOT_APPLICABLE`

The state describes evidence availability and validation status.

It does not describe business performance.

---

## 11. Decision Gate

Phase 1 measurement diagnosis may proceed only for claims for which the
required evidence has reached an adequate validation state.

Possible outcomes include:

### VALIDATED

Evidence is sufficient for the stated conclusion.

### PARTIALLY VALIDATED

Evidence supports a bounded subset of the conclusion.

### OPEN

Required evidence has not yet been obtained.

### CONFLICTING

Evidence sources disagree and require reconciliation.

### UNKNOWN

Available evidence does not establish the mechanism or state.

No `UNKNOWN`, `OPEN` or `CONFLICTING` item may be silently promoted to a
verified diagnosis.

---

## 12. Relationship to Existing Registers

This pack operates together with:

- `docs/01-evidence/EVIDENCE-INTAKE-REGISTER.md`
- `docs/01-evidence/SOURCE-REGISTER.md`
- `docs/01-evidence/CLAIM-VALIDATION-REGISTER.md`
- `docs/01-evidence/MASTER-EVIDENCE-DIAGNOSIS-DECISION-MATRIX.md`
- `docs/02-audit/PHASE-1-MEASUREMENT-EVIDENCE-REQUEST-v0.1.md`

This document is the operational intake layer.

It does not replace the evidence register or the Phase 1 measurement request.

---

## 13. Final Principle

The purpose of Phase 1 is not to confirm a preconceived diagnosis.

It is to establish enough evidence to determine what is actually happening.

The operating sequence remains:

`EVIDENCE → VALIDATION → RECONCILIATION → DIAGNOSIS → REMEDIATION → EXECUTION`

No step should be skipped merely because the expected diagnosis appears
obvious.
