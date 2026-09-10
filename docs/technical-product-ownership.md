# Technical Product Ownership

This document describes the technical product decisions represented by the prototype. It is not a production architecture specification.

## Derived state

`FlowType` is derived from `CompanyOrigin` rather than entered directly by the applicant.

Conceptually:

```text
CompanyOrigin == TR
    -> FlowType = Domestic
else
    -> FlowType = INT
```

Both frontend and backend implementations should use the same business rule. The UI may derive the state for immediate presentation, but backend validation should not rely solely on a browser-derived value.

## State across the wizard

The application needs to preserve:

- selected Company Origin
- derived FlowType
- registration contact
- signatory/management relationship
- agreement-viewed state
- agreement-accepted state
- Step 3 scenario-specific values

Changing an earlier routing input can invalidate decisions made in later steps. In a production implementation, changing Company Origin after progressing should therefore cause dependent state to be recalculated.

## Frontend responsibilities

The prototype places the following behavior in the UI:

- require Company Origin before dependent fields are enabled
- present the appropriate agreement
- enforce the agreement-viewed + accepted interaction
- show one Step 3 variant at a time
- enable Domestic IBAN only for the Domestic scenario
- reuse registration-contact values when the same-person option is selected
- replace the wizard with a completion summary after submission

## Backend responsibilities

A production service should be authoritative for:

- deriving/validating FlowType
- validating scenario-specific required fields
- validating persisted application data
- generating a stable application/reference identifier
- storing agreement acceptance evidence according to business requirements
- committing the application before post-submit notifications are triggered

## Notification lifecycle

The product requirement is for the successful application event to trigger:

1. an applicant confirmation
2. an internal operations notification

A robust implementation should avoid turning notification-delivery failure into application-submission failure. Delivery, retry and idempotency mechanics should follow the platform's existing messaging infrastructure.

## Idempotency consideration

Repeated client calls or retries should not create duplicate applications or duplicate notifications. The exact mechanism is implementation-specific, but the lifecycle should distinguish:

`application accepted` from `notification delivered`.

## Prototype limitation

The HTML demo simulates the interaction and conditional state only. It does not persist data or call external services.
