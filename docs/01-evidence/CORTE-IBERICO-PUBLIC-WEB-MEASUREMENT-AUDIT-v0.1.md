# CORTE IBÉRICO — Public Web & Measurement Audit v0.1

## Audit metadata

- Date: 2026-10-07
- Target: `https://corteiberico.com/`
- Scope: public web surface, ecommerce structure, visible measurement references, conversion paths, consent documentation, and commercial funnel topology.
- Method: public web inspection only.
- Access boundary: no Meta Business Manager, Ads Manager, Events Manager, GTM container, WooCommerce admin, analytics account, payment provider, or server-side infrastructure access was used.
- Status: preliminary evidence package; not an account audit.

## Evidence classification

This document uses:

- `VERIFIED`: directly supported by the inspected public web surface.
- `OPEN`: relevant question requiring authorized access or dynamic validation.
- `HYPOTHESIS`: technically plausible but not established by current evidence.
- `NOT FOUND IN INSPECTED SURFACE`: absence from the inspected public surface; not proof of non-existence.

---

## 1. Executive finding

The public site is not a single-purpose brochure site. It exposes at least three commercially distinct paths:

1. ecommerce;
2. event services;
3. academy / professional training;

with WhatsApp functioning as an additional human-assisted conversion channel.

The site also exposes Google Tag Manager and Meta/Facebook tracking references in the public implementation inspected previously. The current public-search evidence confirms the ecommerce, event, academy and WhatsApp surfaces, while the exact live tag/event configuration remains an access-controlled validation item.

The correct technical question is therefore not simply:

> Are the Meta campaigns performing?

It is:

> Is the complete acquisition → measurement → conversion → business-reconciliation chain providing Meta with reliable signals for each materially different conversion path?

That question must be answered before attributing poor performance to campaign configuration alone.

---

## 2. Public ecommerce surface

The current indexed store exposes a paginated product catalogue. The inspected store result reports:

- `1–30 of 47 results`;
- product categories including meats, hams, combos, sliced products, cheeses and specialties;
- direct `Añadir al carrito` actions;
- MXN pricing;
- products spanning materially different price points.

Source: https://corteiberico.com/tienda/

Examples visible in the indexed store include:

- Rulo de queso de cabra: approximately MXN 103.50;
- Combo – Cata Madrid: approximately MXN 852.06;
- Combo Festejo: approximately MXN 1,825.00;
- Pata de jamón Serrano: approximately MXN 6,344.04;
- Centro de jamón 50% ibérico: approximately MXN 10,002.29;
- Pata de jamón 50% ibérico de cebo: approximately MXN 13,245.80;
- premium jamón products above MXN 20,000.

Source: https://corteiberico.com/tienda/

### Diagnosis

A `Purchase` event cannot be interpreted only as a count. Performance analysis should preserve at least:

- purchase count;
- purchase value;
- currency;
- average order value;
- product/category mix;
- shipping economics;
- margin where available.

The relevant reconciliation is:

`Meta purchase value ↔ ecommerce order value ↔ actual paid order`

Status: **OPEN / P0**

---

## 3. Shipping / offer messaging

The public site currently exposes different shipping messages by surface.

Home:

- free shipping / minimum purchase messaging around MXN 1,825.

Source: https://corteiberico.com/

Store/event/category surfaces:

- CDMX delivery from MXN 1,825;
- national `Ocurre` from MXN 2,999;
- free-shipping messaging.

Sources:
- https://corteiberico.com/tienda/
- https://corteiberico.com/experiencia-corte-iberico/
- https://corteiberico.com/categoria-producto/jamones/jamones-ibericos/

This is not enough evidence to call the messaging contradictory. The thresholds may correspond to different shipping modes.

### Required validation

Test the actual cart/checkout path for:

- destination;
- shipping method;
- free-shipping threshold;
- displayed offer;
- final payable amount.

Status: **OPEN / P1**

---

## 4. Event-services conversion path

The event page exposes an explicit service funnel and WhatsApp actions.

Observed public content includes:

- event-service proposition;
- `Reserva tu evento`;
- `Cotiza tu evento`;
- direct WhatsApp interaction.

Source: https://corteiberico.com/experiencia-corte-iberico/

This creates a conversion path materially different from ecommerce:

`Meta / web traffic → event page → WhatsApp → human qualification → quotation → sale`

The final commercial conversion may therefore occur outside the ecommerce transaction system.

Status:
- event-service funnel: **VERIFIED**
- WhatsApp attribution: **OPEN / P0**
- lead-to-revenue reconciliation: **OPEN / P0**

---

## 5. Academy / professional funnel

The public Academy surface exposes a separate commercial/operational line including programmes, calendar information, professional training and business-oriented training/diagnostic paths.

Source: https://corteiberico.com/academia/

This creates another materially different funnel:

`Traffic → programme / business proposition → enquiry / WhatsApp / registration → enrolment or B2B sale`

It should not automatically be evaluated using the same KPI model as ecommerce.

Status:
- academy funnel: **VERIFIED**
- attribution: **OPEN / P1**
- lead value / revenue reconciliation: **OPEN / P1**

---

## 6. Measurement architecture

The public implementation previously inspected exposed Google Tag Manager and Meta/Facebook tracking references. The existence of those integrations is not, by itself, proof that the implementation is correct.

The following must remain open until dynamic/account-level inspection:

- GTM container configuration;
- tag inventory;
- triggers;
- Meta Pixel configuration;
- Pixel event inventory;
- `ViewContent`;
- `AddToCart`;
- `InitiateCheckout`;
- `Purchase`;
- event parameters;
- `value`;
- `currency`;
- `content_ids`;
- `contents`;
- `event_id`;
- Conversions API;
- browser/server deduplication;
- catalogue matching;
- consent propagation;
- UTM propagation.

Status: **OPEN / P0**

### Important control

The presence of a Meta request or Pixel is not evidence that:

- the correct event fires;
- the event fires exactly once;
- the event contains correct business values;
- CAPI is configured;
- browser/server events are deduplicated;
- Meta can optimise correctly;
- Meta-reported revenue equals business revenue.

---

## 7. Consent / cookie documentation

The privacy policy states that Corte Ibérico uses cookies and similar technologies and describes collection/use of technical and browsing information.

Source: https://corteiberico.com/privacy-policy/

The inspected public footer did not expose a separate cookie-policy link alongside the shipping, privacy and refund/return policy links.

This is classified narrowly as:

> No independent cookie-policy link was found in the inspected public surface.

It is **not** classified as proof that no consent mechanism exists.

### Required validation

Use a real browser session to inspect:

1. first-party cookies before interaction;
2. third-party cookies before interaction;
3. consent banner;
4. consent categories;
5. GTM firing before/after consent;
6. Meta requests before/after consent;
7. consent state propagation;
8. withdrawal behaviour.

Status: **OPEN / P1**

---

## 8. Funnel topology

The public evidence supports at least:

### Funnel A — Ecommerce

`Ad / organic → product/category → cart → checkout → purchase`

Primary economic signal:

`Purchase + value`

### Funnel B — Events

`Ad / organic → event proposition → WhatsApp → qualification → quotation → sale`

Primary economic signal:

`Qualified lead → revenue`

### Funnel C — Academy

`Ad / organic → programme / B2B proposition → enquiry → registration / sale`

Primary economic signal:

`Qualified enquiry → enrolment / contract value`

### Cross-channel bridge

`Meta → website → WhatsApp → human sale`

This is potentially invisible or only partially visible to standard ecommerce conversion reporting.

---

## 9. Priority audit questions

### P0 — Measurement

1. Which Meta Business Manager / ad account is authoritative?
2. Which Pixel is connected?
3. Which events are active?
4. Is Conversions API active?
5. Are browser and server events deduplicated?
6. What event is used for campaign optimisation?
7. Is purchase value transmitted correctly?
8. Is currency transmitted correctly?
9. Are product IDs aligned with the catalogue?
10. Are WhatsApp-originated sales attributed?

### P0 — Business reconciliation

11. Where is the authoritative order record?
12. Where is payment confirmation recorded?
13. What is actual AOV?
14. What is actual margin by major product group?
15. What proportion of sales is closed through WhatsApp?
16. What proportion of event/academy revenue is outside ecommerce?

### P1 — Web conversion

17. Are shipping rules consistent at checkout?
18. Are promotional messages consistent between landing surfaces and checkout?
19. Are high-value products available when advertised?
20. Are unavailable products still receiving paid traffic?

---

## 10. Current diagnosis

### D-WEB-001 — Multiple conversion economies

Corte Ibérico has materially different conversion paths rather than a single ecommerce funnel.

Confidence: **HIGH**

Evidence:
- ecommerce store;
- event-service funnel;
- academy/professional funnel;
- WhatsApp conversion path.

### D-WEB-002 — Measurement must be audited before campaign causality is assigned

The public presence of tracking infrastructure does not establish event correctness or economic reconciliation.

Confidence: **HIGH**

### D-WEB-003 — Purchase count alone is insufficient

The catalogue spans materially different price levels, so performance analysis requires purchase value and product mix.

Confidence: **HIGH**

### D-WEB-004 — WhatsApp attribution is a critical unknown

Event and other human-assisted sales may close outside ecommerce.

Confidence: **HIGH**

### D-WEB-005 — Consent implementation requires dynamic validation

The privacy policy documents cookie use, but the inspected public surface does not establish the actual consent/firing sequence.

Confidence: **HIGH**

---

## 11. Evidence boundaries

The following are deliberately **NOT established** by this audit:

- that Meta Ads campaigns are incorrectly configured;
- that the Pixel is incorrectly configured;
- that Conversions API is absent;
- that events are duplicated;
- that events are missing;
- that attribution is wrong;
- that Meta is under-reporting or over-reporting;
- that the shipping rules are contradictory;
- that the cookie implementation violates a legal requirement;
- that any specific Meta algorithm caused a business outcome.

Those require additional evidence.

---

## 12. Required Phase 1 evidence acquisition

### Access required

- Meta Business Manager / Business Portfolio;
- Ads Manager;
- Events Manager;
- Commerce Manager / catalogue where applicable;
- GTM container;
- ecommerce administration;
- analytics platform;
- payment/order reconciliation source;
- WhatsApp / CRM attribution source where available.

### Dynamic browser test

Run controlled tests for:

- landing;
- product view;
- add to cart;
- checkout;
- purchase/test order where authorized;
- event CTA;
- academy CTA;
- WhatsApp CTA;
- consent acceptance;
- consent rejection;
- consent withdrawal.

Capture:

- request URL;
- event name;
- parameters;
- timestamp;
- event ID;
- source;
- browser/server origin;
- resulting Meta event state.

---

## 13. Audit conclusion

The correct immediate engagement is not:

> campaign optimisation in isolation.

The evidence supports:

> **Measurement & Commerce Audit → evidence-backed diagnosis → controlled remediation → Christmas acquisition execution.**

This keeps the technical conclusion ahead of the implementation decision and prevents unverified assumptions about Meta, the account or the existing team from becoming project facts.

---

## Sources

- Home: https://corteiberico.com/
- Store: https://corteiberico.com/tienda/
- Events: https://corteiberico.com/experiencia-corte-iberico/
- Academy: https://corteiberico.com/academia/
- Privacy: https://corteiberico.com/privacy-policy/
- Jamones: https://corteiberico.com/categoria-producto/jamones/
- Ibérico hams: https://corteiberico.com/categoria-producto/jamones/jamones-ibericos/
