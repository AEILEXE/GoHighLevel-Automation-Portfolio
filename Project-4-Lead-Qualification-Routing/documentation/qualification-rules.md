# Qualification Rules

BrightSmile is a fictional portfolio scenario. No real patient data was used. This is a rule-based CRM operations demonstration, not a medical or clinical triage system. Classifications are administrative routing labels only and say nothing about clinical urgency, diagnosis or eligibility for treatment.

## Inputs actually inspected (verified in the account)

Form: `PORTFOLIO DEMO — BrightSmile Inquiry Form` (ID 2NS3jJ6HkbIVH2GeL0vE)

| Form field | Required? | Used by workflow? |
|---|---|---|
| First Name | No | No |
| Last Name | No | No |
| Email | Yes (enforced by form) | No (cannot be empty on a valid submission) |
| Phone | No | Yes (Needs Information rule) |
| What are you interested in? (`contact.what_are_you_interested_in`, SINGLE_OPTIONS) | No (no required marker on the form) | Yes (service category) |
| Consent checkbox (terms_and_conditions) | Yes | No |

Service options (exact values): Dental Cleaning, Braces Consultation, Teeth Whitening, General Consultation, Other.

## Step 0 — clear prior Project 4 classification tags

Before the If/Else runs, a Remove Contact Tag action ("Clear prior P4 classification tags") removes only the four Project 4 tags (p4-standard-review, p4-priority-review, p4-needs-information, p4-manual-review). "Remove all tags" is switched off, so tags from Projects 1 to 3 and unrelated processes are never touched. This keeps a contact from carrying two conflicting Project 4 outcomes after a re-run.

## Rule order (first match wins, evaluated top to bottom)

| # | Branch name | Condition | Classification | Tag |
|---|---|---|---|---|
| 1 | Manual - Service Missing | Service field is empty | manual_review | p4-manual-review |
| 2 | Needs Info - Phone Missing | Phone is empty | needs_information | p4-needs-information |
| 3 | Priority - Braces Consultation | Service is "Braces Consultation" | priority_review | p4-priority-review |
| 4 | Standard - Mapped Service | Service is Dental Cleaning OR Teeth Whitening OR General Consultation | standard_review | p4-standard-review |
| 5 | Manual - Unmapped Service (default) | Nothing above matched (includes "Other" and any unknown value) | manual_review | p4-manual-review |

No branch rejects a lead. Anything unclear goes to a human.

## Meaning of each outcome

- standard_review: a recognised service was selected and a phone number is present; staff handle it in normal order.
- priority_review: the fictional clinic has designated the braces-consultation option for earlier administrative handling. This is an operational routing example only. It does not mean the person is medically urgent or clinically higher priority.
- needs_information: a service was selected but the optional phone field is blank, so staff should request a contact number. The Email field is form-enforced, so email is not re-checked; this is stated honestly rather than claimed as validated.
- manual_review: the service is missing, is "Other", or is not covered by the rules. A staff member decides the next step.

## What the workflow does not do

It does not read free text, infer symptoms, judge urgency, check whether an email or phone number is real, or reject anyone.
