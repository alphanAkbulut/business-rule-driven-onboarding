# Business Rules

## 1. Company Origin is a decision input

Company Origin must be selected before the downstream registration fields become active.

The selected value is used to derive a system-level flow classification:

- `TR` → `Domestic`
- any other country → `INT`

The applicant does not manually choose the flow type.

## 2. Registration contact and authorized signatory

The flow captures a registration contact and an authorized signatory / management contact.

If **Same with Authorized Person for Registration** is selected:

- the signatory/management values are copied from the registration contact,
- duplicate fields are disabled,
- the user is not required to enter the same person twice.

If it is not selected, the signatory/management fields remain independently editable.

## 3. Agreement behavior

Agreement behavior depends on the derived flow:

| Flow | Agreement |
|---|---|
| Domestic | Turkish agreement |
| International | English agreement |

The user must open/view the agreement before the acceptance state can enable continuation.

Agreement acceptance alone, without the agreement first being presented/opened, is insufficient in the prototype.

## 4. Step 3 field behavior

### Domestic

The Domestic layout is shown.

A Turkish IBAN is required and must:

- begin with `TR`
- contain 26 characters

### International

The International layout is shown.

IBAN is not required and is disabled in the prototype.

## 5. Agency class

Agency Class is a required selection with the values:

- A
- B
- C

No additional branching is currently derived from Agency Class.

## 6. Navigation and submission

The process contains three steps only.

Before final submission, the applicant can navigate back from Step 2 to Step 1 and from Step 3 to Step 2.

There is no Previous button inside Step 1 because any language selection or pre-registration entry point occurs outside this wizard.

After successful final submission:

- the wizard is no longer presented as editable,
- backward navigation is removed,
- the Final Application Summary becomes the completion state.

## 7. Confirmation and notifications

The final summary confirms that the application was received.

The intended notification behavior is:

- Domestic applicant → Turkish confirmation
- International applicant → English confirmation
- internal operations notification → operational summary

Notification delivery infrastructure is not implemented in this static prototype.
