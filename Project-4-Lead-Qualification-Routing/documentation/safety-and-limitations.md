# Safety Controls and Limitations

BrightSmile is a fictional portfolio scenario. No real patient data was used. This is rule-based CRM routing, not clinical triage and not a live AI system.

## Safety controls applied

- Fictional contacts only: `p4.test.*@example.com`, reserved 555-01xx phone numbers, Do Not Disturb enabled.
- No outbound actions: the workflow contains only tag removal, If/Else, add-tag and add-to-notes actions.
- Workflow left in Draft; never published.
- Trigger restricted to the single portfolio form.
- Tag clearing limited to the four new Project 4 tags; "Remove all tags" is off.
- No opportunity, pipeline stage, appointment, calendar or custom-field action in the workflow.
- Priority outcome described only as demonstration administrative routing; notes state it is not medical urgency.
- Nothing is rejected automatically; unclear records go to manual review.
- Protected assets (original workflow, original form, original calendar, Projects 1–3 workflows) were not modified or republished. The original workflow was opened once, read-only, to read its trigger filter, and closed without saving.
- A Tax ID compliance pop-up appeared in the account; it was dismissed with Cancel and nothing was entered.

## Final review checks

Workflow re-opened and confirmed Draft with 12 actions, none outbound; execution logs show no message steps; API conversation search returned 0 conversations for all five contacts. Outbound sending is therefore not evidenced anywhere, though the conversation check covers API-visible conversations only.

## Limitations

1. Live trigger not verified. Draft workflows do not enroll from the form trigger, so tests used the builder's Test workflow on API-created contacts. Whether a real submission fires the workflow once published is expected, not proven.
2. Workflow API disabled for this sub-account, so the workflow was built and inspected through the browser interface.
3. Notes are not de-duplicated: a re-run adds another note (tags stay consistent).
4. No reliable guard against duplicate enrollment was added, to avoid blocking a legitimate later inquiry.
5. Email is form-enforced and not re-checked; the workflow cannot validate that an email or phone number is real.
6. The "needs information" rule is based on the optional Phone field only.
7. The opportunity-safety check is an API search plus the absence of any opportunity action; it is not an exhaustive audit.
8. Execution-log screenshots exist for all five test contacts (see `evidence/06-classification-execution-logs.png`), but contact-record screenshots for T2-T5 could not be captured (contact detail page rendered blank); tags and notes were confirmed by API read-back. Projects 1–3 workflows were compared at list level only.
9. Teeth Whitening is treated as a standard service. The brief's rule text named Dental Cleaning and General Consultation only; this was kept because all three are recognised form options, and the owner confirmed Teeth Whitening stays under Standard Review.
10. The consent checkbox is not evaluated by the workflow.
11. No AI integration was configured or tested; see `future-ai-enhancement.md`.
