# n8n workflow case study

This project presents the real-estate lead workflow as a visual case study. The public repository and Vercel page do not include an importable workflow JSON package.

## What the workflow is designed to do

1. Capture leads from paid social, the website, and search ads; normalize details and check permission, booked status, and opt-out state.
2. Route eligible leads toward a shared record and first-call process. Suppress contacts that are invalid, booked, opted out, or lack confirmed contact permission.
3. Receive call outcomes, prepare qualification fields, and plan a bounded retry after two hours when an unanswered attempt is eligible. Cap attempts at three.
4. Route inbound WhatsApp requests toward approved replies, visit booking, or a human sales handoff, while noting the proposed 30-minute call hold.
5. Prepare Hot/Warm/Cold follow-up actions and a daily leads/calls/visits report.
6. Surface workflow errors for operator review.

These are proposed workflow behaviors shown in the visual diagram and screenshot. The integrations are not connected or running, and no business performance results are claimed.

## Implementation access

For the importable workflow package and setup options, visit [BrandOps](https://brandops.site).
