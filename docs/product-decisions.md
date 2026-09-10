# Product Decisions

## Problem framing

The requirement initially resembled a standard agency-registration form. Analysis showed that this framing hid multiple business scenarios behind a common entry point.

The decisive insight was that **Company Origin is not merely profile data**. It changes legal/document behavior, financial requirements and downstream data collection.

A static form would therefore create one of two poor outcomes:

1. show every possible field to every applicant and explain which fields to ignore, or
2. create separate registration journeys and force users to choose a process before they understand the distinction.

The chosen solution keeps one onboarding journey while allowing the system to adapt behind the scenes.

## Why three steps?

The information is separated by user intent and cognitive task:

**Step 1 — Identity and routing**  
Collect enough information to identify the applicant and derive the applicable business scenario.

**Step 2 — Agreement**  
Present the applicable contractual content and capture explicit acceptance.

**Step 3 — Operational membership data**  
Collect the detailed information required for the derived scenario.

This structure reduces the amount of information presented at once and prevents later steps from showing irrelevant fields.

## Progressive disclosure

Conditional behavior is used to reveal requirements only when they become relevant.

Examples:

- fields dependent on Company Origin are initially disabled,
- agreement content changes after flow classification,
- Domestic and International Step 3 layouts are mutually exclusive,
- duplicate signatory input can be removed through the same-person option.

## Completion is not Step 4

The final summary is deliberately not represented as another step in the wizard.

The three numbered steps are tasks the user performs. The summary is a **post-transaction state** after submission has already occurred.

This distinction makes the transaction boundary clear and prevents the completion view from implying that another action is required.

## Portfolio outcome

The case study demonstrates how product discovery and business analysis can change the shape of a requirement before implementation:

`generic form requirement → business-rule analysis → adaptive flow → delivery-ready behavior`
