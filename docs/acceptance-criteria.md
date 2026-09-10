# Acceptance Criteria

## Step 1

1. Company Origin is required.
2. Dependent Step 1 fields remain disabled until Company Origin is selected.
3. Selecting `TR` derives the Domestic scenario.
4. Selecting any non-TR country derives the International scenario.
5. Agency Name, Registration Contact Name and Registration Contact Email are required before continuing.
6. Agency Class supports A, B and C.
7. When the same-person option is selected, management/signatory information reuses the registration-contact values.

## Step 2

1. Domestic applications receive the Turkish agreement experience.
2. International applications receive the English agreement experience.
3. The applicant must open/view the agreement before continuation can be enabled.
4. The applicant must explicitly accept the agreement.
5. The user can return to Step 1 before final submission.

## Step 3

1. Domestic applications show the Domestic field layout only.
2. International applications show the International field layout only.
3. Domestic applications require a Turkish IBAN.
4. The Domestic IBAN must start with `TR` and contain 26 characters.
5. International applications do not require IBAN in the current flow.
6. The user can return to Step 2 before final submission.

## Final submission

1. Successful submission ends the editable three-step wizard.
2. The stepper is no longer shown as an active navigation element.
3. Back navigation to Steps 1–3 is not available after submission.
4. The Final Application Summary is shown as the completion state.
5. The summary reflects the derived Domestic/International scenario.
6. IBAN is included in the summary only when applicable to the Domestic scenario.
7. Applicant and internal notification flows are treated as post-submit behavior.
