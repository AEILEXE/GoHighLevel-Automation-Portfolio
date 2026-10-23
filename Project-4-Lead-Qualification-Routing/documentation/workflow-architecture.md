# Workflow Architecture

BrightSmile is a fictional portfolio scenario. No real patient data was used. The workflow is rule-based; no AI model or external integration is configured.

## Saved workflow

- Name: `BrightSmile | Lead Qualification & Routing`
- Status: Draft (never published)
- Builder: GoHighLevel workflow builder.

## Structure (verified after a full page reload)

1. Trigger: Form Submitted, filter "Form is any of" `PORTFOLIO DEMO — BrightSmile Inquiry Form` only. The original form and the marketing form are not selected.
2. Action: Remove Contact Tag, "Clear prior P4 classification tags" (four p4 tags only; Remove all tags is off).
3. Action: If / else, "P4 Classify Inquiry", five paths:
   - Manual - Service Missing: `What are you interested in?` is empty
   - Needs Info - Phone Missing: `Phone` is empty
   - Priority - Braces Consultation: service is Braces Consultation
   - Standard - Mapped Service: service is Dental Cleaning OR Teeth Whitening OR General Consultation (joiner set to OR)
   - Manual - Unmapped Service (default / none branch)
4. On every path: Add contact tag, then Add to notes, then end. 12 actions in total (1 tag removal, 5 tags, 5 notes, 1 If/Else).

Branch actions:

| Path | Tag | Note title |
|---|---|---|
| Manual - Service Missing | p4-manual-review | P4 Classification: manual_review |
| Needs Info - Phone Missing | p4-needs-information | P4 Classification: needs_information |
| Priority - Braces Consultation | p4-priority-review | P4 Classification: priority_review |
| Standard - Mapped Service | p4-standard-review | P4 Classification: standard_review |
| Manual - Unmapped Service | p4-manual-review | P4 Classification: manual_review |

See `diagrams/workflow-architecture.mmd` for the diagram of exactly this structure.

## Design choices

- Rule order puts missing service first, then missing phone, so a record missing both is sent to manual review rather than a lower-confidence outcome.
- The Standard branch lists Teeth Whitening as well as Dental Cleaning and General Consultation, because all three are recognised services on the form; the owner confirmed Teeth Whitening stays under Standard Review. Only Braces Consultation is designated for priority administrative handling and "Other" is unmapped.
- Only tags and notes are used. No opportunity action, pipeline stage change, custom-field update, message, or appointment action exists in the workflow.
- Duplicate-processing guard: none was added. The only mechanism available that is reliable and cannot permanently block a legitimate future inquiry is the tag-clearing step, which makes re-processing idempotent for tags. Notes are not de-duplicated (see limitations).
- Tags: the four p4 tags are new; no existing tag from Projects 1 to 3 was reused or renamed.

## What the trigger can and cannot see

The form requires Email and a consent checkbox; Phone, names and the service dropdown are optional. The workflow checks only Phone and the service field. It does not (and cannot) validate that an email or phone number is genuine.
