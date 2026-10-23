# Project 1 — Lead-to-Appointment System

A GoHighLevel portfolio demonstration connecting inquiry intake to appointment-driven opportunity management in the fictional BrightSmile Dental Clinic CRM.

> **Status:** Portfolio demonstration. Both portfolio workflows remain in Draft. The recorded workflow tests show selected successful executions; they do not establish a production deployment or prove every branch and duplicate scenario.

## Business problem

A clinic needs a consistent way to capture new inquiries, create an opportunity in the correct pipeline stage, and update that existing opportunity when an appointment is booked—without creating a duplicate opportunity.

## Workflow 1 — Lead-to-Appointment

**Trigger:** Submission of the portfolio inquiry form.

- Applies `brightsmile-new-inquiry`.
- Creates an opportunity in the BrightSmile Dental Clinic — Lead Pipeline at **New Inquiry**.
- Uses duplicate-opportunity protection in the opportunity action.
- Routes Braces Consultation to priority administrative review, missing service interest to missing-information review, and other recognized interests to the general inquiry path.

## Workflow 2 — Appointment Booked

**Trigger:** A customer books the portfolio demo calendar.

- Searches for the existing open opportunity in the BrightSmile pipeline.
- Moves the found opportunity to **Appointment Booked**.
- Ends without creating a new opportunity if none is found.
- Contains no outbound-message actions.

## Evidence

The `evidence/` folder contains six selected original screenshots, copied without resizing or recompression:

1. Workflow list and status overview.
2. Lead intake workflow canvas.
3. Appointment-booking workflow canvas.
4. Lead intake execution log.
5. Appointment-booking execution log.
6. CRM pipeline overview.

Contact/appointment-detail captures and unrelated template screenshots from the source archive were intentionally excluded from this public package because they are not necessary to explain the two workflows and could reveal extra account details.

## Test result and known limitation

The supplied execution evidence shows lead intake actions executing and the booking workflow finding and moving an existing open opportunity. The test appointment was later cancelled, but the opportunity remained at **Appointment Booked**. Cancellation-driven stage correction is not implemented in this project; appointment lifecycle behavior is addressed separately in Project 2.

The lead intake screenshot demonstrates the General Inquiry branch; it should not be treated as proof that every branch or all duplicate-submission scenarios were tested.

## Tools

GoHighLevel · GitHub · Markdown · Mermaid

## Privacy and scope

BrightSmile and the test records are fictional. This is a portfolio workflow demonstration, not a live clinic deployment, a compliance assessment, or a claim of production reliability.
