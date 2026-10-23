# Project 3 — Lead Nurture & Re-engagement Automation

A fictional BrightSmile Dental Clinic GoHighLevel portfolio project demonstrating rule-based lead nurture, stop conditions, and manually triggered re-engagement eligibility.

> **Status disclosure:** The three workflows were tested and returned to Draft. No outbound-message actions are configured. This is a workflow-logic demonstration, not a live AI system or production deployment.

## Workflows included

- `BrightSmile | Lead Nurture` — triggered by submission of the portfolio inquiry form, with an active-tag guard, internal notes, stop-tag checks, and completion handling.
- `BrightSmile | Lead Nurture Stop Handler` — responds to a booking on the portfolio calendar by applying a stop tag and recording a note; the nurture workflow checks the stop tag at its next checkpoint.
- `BrightSmile | Lead Re-engagement` — starts when the `p3-reengage-eligible` tag is added; eligibility is manual because the account did not provide a suitable native inactivity trigger.

## Evidence

The `evidence/` folder contains original GHL screenshots of the workflow inventory, each workflow, selected canvas views, execution logs, and status. Files were renamed for clarity without recompressing or resizing the source PNGs. Exact duplicate captures were not included twice.

## Test summary

Recorded tests included lead entry, nurture progression, booking stop, manual stop, re-engagement eligibility, re-engagement stop, and cross-workflow isolation. The native reply-stop test was blocked because a genuine reply requires an outbound message, which this no-message design intentionally does not send. DND safety was only partially tested; no outbound message actions existed to test message suppression. The duplicate-entry guard was not independently exercised beyond the platform's enrollment behavior.

## Known limitations

- No live AI model or AI integration is implemented.
- No outbound emails, SMS, or WhatsApp messages are configured.
- Reply-based stopping was not verified.
- Re-engagement eligibility is tag-triggered and manual, not a native inactivity trigger.
- The stop handler adds a stop tag and note; the nurture workflow exits when it reaches a stop-tag check rather than using a direct removal action.
- Tests were performed with fictional contacts and the workflows were returned to Draft.

## Privacy and scope

BrightSmile and all test contacts are fictional. Raw audit exports, opportunity/contact exports, contact detail screenshots, and unrelated account-level screenshots are excluded from this public package. This project documents observed tests and limitations, not production reliability or compliance.
