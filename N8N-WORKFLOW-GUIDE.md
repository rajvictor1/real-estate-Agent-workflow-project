# n8n workflow starter guide

## What is included

- `workflows/real-estate-lead-lifecycle.json` — inactive n8n workflow starter with 18 nodes: lead intake/eligibility, call outcome and retry planning, WhatsApp request routing, and a daily follow-up/report trigger.
- `workflows/real-estate-lead-error-alert.json` — companion 3-node error workflow.
- Matching public copies are in `public/downloads/`; the one-page Vercel case study links to both.

## Honest implementation status

These are workflow starters, not a connected production automation. The files contain no credentials and the workflows are inactive. Service actions are `No Operation` placeholders: Google Sheets writes, outbound voice calls, WhatsApp replies/bookings/handoffs, due-lead reads, report delivery, and operator alerts do not occur yet. Code nodes only normalize/classify the example webhook data and prepare next-step fields. The template has not been imported or run in a live n8n instance.

Webhook nodes require a Header Auth credential before use. Configure authentication, select providers, map the actual lead schema, define idempotent storage operations, and test with synthetic data before activation. After importing the companion error workflow, set it as the main workflow's error workflow in n8n settings and configure its alert destination.

## Import the main workflow

1. Download `real-estate-lead-lifecycle.json` from this repository or the case-study website.
2. In n8n, open the workflows menu and choose **Import from File**.
3. Select the JSON and inspect the canvas. The workflow remains inactive.
4. Configure Header Auth credentials for the intake, call-outcome, and WhatsApp webhooks.
5. Replace the labelled no-op placeholders only after deciding on providers and data permissions.
6. Test each path with synthetic leads and no real outbound calls/messages. Verify duplicate suppression, booked/opt-out checks, three-attempt cap, two-hour wait, chat hold, temperature transitions, and failure recovery.
7. Import `real-estate-lead-error-alert.json`, configure its operator alert, and select it in the main workflow's error-workflow setting.
8. Confirm workflow timezone for the 1 PM schedule. Keep inactive until validation and human approval are complete.

n8n's official docs describe JSON import through the workflow menu's **Import from File** option: https://docs.n8n.io/build/manage-workflows/export-and-import.md. n8n warns that exported workflow JSON may include credential names and IDs; these templates intentionally include no credential data.

## Main workflow layout

| Segment | Entry / nodes | Intended responsibility |
|---|---|---|
| Intake | Webhook → Code → IF → sheet/call placeholders or suppression log | Normalize the lead and suppress missing-phone, booked, opted-out, or permission-unconfirmed contacts |
| Call outcome | Webhook → Code → IF → Wait 2 hours / update placeholder | Capture qualification; retry an unanswered lead before attempt three; mark a third miss Cold |
| WhatsApp | Webhook → Code → response/booking/handoff placeholder | Compute a 30-minute hold and route requested action; history lookup and actual replies still need service connections |
| Follow-up / report | Daily 1 PM Schedule Trigger → Code → service placeholder | Prepare the Hot/Warm/Cold action or a leads/calls/visits report; no sheet query or delivery is connected |
| Error handling | Companion Error Trigger → Code → alert placeholder | Format a failure summary; select this as the main workflow's error workflow after importing |

## Example lead intake payload

```json
{
  "name": "Sample Lead",
  "phone": "+910000000000",
  "project": "Sample project",
  "source": "website",
  "contactAllowed": true,
  "optOut": false,
  "booked": false
}
```

Use synthetic data only. Replace the example phone with no real person's details when sharing screenshots. The permission flag is a safety gate added to the design; align it with the actual business process and applicable requirements before using it.
