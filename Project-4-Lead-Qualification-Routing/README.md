# Project 4 — Lead Qualification & Routing

A rule-based GoHighLevel workflow that classifies fictional BrightSmile inquiry records for administrative review using the selected service and whether a phone number is present.

> **Status:** The workflow is saved in Draft. Five classification scenarios were tested through the workflow builder's Test workflow feature. The live portfolio-form trigger was **not verified**; do not describe the project as fully end-to-end verified or AI-powered.

## What it demonstrates

- Exact-form trigger filtering.
- Ordered If/Else branches for missing service, missing phone, priority administrative review, standard review, and default/manual review.
- Project-specific classification tags and internal notes.
- Clearing only Project 4 classification tags before reclassification.
- Scenario-based test reporting and explicit limitations.

## Classification rules

1. Service missing → `p4-manual-review`.
2. Phone missing → `p4-needs-information`.
3. Braces Consultation → `p4-priority-review` for administrative handling only; not medical urgency.
4. Dental Cleaning, Teeth Whitening, or General Consultation → `p4-standard-review`.
5. Other / unmatched selection → `p4-manual-review`.

## Evidence

The `evidence/` folder includes the workflow inventory, saved workflow overview, branch canvas, execution logs, and Draft-status screenshot. Source PNGs were copied without resizing or recompression. The extra account-wide contact, task, opportunity, audit-log, and settings captures from the source bundle are intentionally excluded from the public package.

## Test status

T1 standard review, T2 priority review, T3 missing phone, T4 missing service, and T5 Other/default manual review were reported as PASS using the builder's Test workflow feature and confirmed from tags, notes, and execution logs. The live form-submission trigger remains NOT VERIFIED because the workflow was kept in Draft and the public form has a Cloudflare bot check. The test run does not prove live trigger enrollment.

## Limitations

- No live AI model or external AI integration is implemented.
- This is administrative routing, not clinical triage or diagnosis.
- Notes are not de-duplicated on rerun.
- Contact detail pages for T2–T5 were not captured; execution-log screenshots and API read-back were used as evidence.
- Protected Projects 1–3 were checked at workflow-list level in the final review, not re-opened individually.

## Privacy and scope

BrightSmile and all test contacts are fictional. Raw audit-log and opportunity exports, account-level contact/task screens, and unrelated captures are excluded. This is a portfolio demonstration, not a production deployment or compliance assessment.
