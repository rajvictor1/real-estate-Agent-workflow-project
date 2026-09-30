# Architecture and decision log

## Boundary: portfolio site versus lead automation

This project has two distinct systems:

1. **Portfolio website — implemented.** Static HTML, CSS, and JavaScript hosted on Vercel. It presents an anonymized project narrative and does not process real leads.
2. **Lead-management automation — designed, not implemented.** Proposed n8n workflow connecting approved lead sources, a shared record, calling/WhatsApp services, sales ownership, and reporting.

Vercel hosts the case-study site; it is not the proposed workflow orchestration layer.

## Proposed runtime flow

```text
Meta lead forms ─┐
Property website ├─> n8n intake + normalization ─> shared lead record (initially Google Sheets)
Google Ads ──────┘                                  │
                                                   ├─> call eligibility check ─> voice provider / AI caller
                                                   ├─> inbound WhatsApp event ─> context-aware response
                                                   ├─> Hot/Warm/Cold router ─> sales / scheduled nurture
                                                   └─> event log + failure alert + 1 PM report
```

The diagram is a proposed design. Providers, authentication, exact integration contracts, and data retention are not chosen.

## Responsibilities

| Component | Responsibility | Status |
|---|---|---|
| Lead source adapters | Receive Meta, website, and Google Ads submissions with attribution | Proposed |
| n8n | Orchestrate triggers, idempotent steps, delays, branching, retries, and escalation | Proposed |
| Lead record | Store identity, source, state, attempt count, history, hold, next action, and owner | Specified; Google Sheets is the initial candidate |
| Calling service | First attempt, unanswered retries, structured qualification result | Provider and integration TBD |
| WhatsApp service | Inbound conversation, approved replies/media, site booking, human handoff | Provider and integration TBD |
| Sales owner | Take Hot leads and negotiated/requested human conversations | Process specified; operational routing TBD |
| Monitoring | Error notification and daily leads/calls/visits report | Requirements specified; implementation TBD |
| Vercel | Serve this static recruiter case-study site | Implemented |
| GitHub | Store code and project documentation privately | Implemented |

## State model

Lead status and automation ownership must be explicit. Suggested status fields:

- `NEW`: captured, not yet attempted.
- `CALLING`: a permitted call attempt is in progress.
- `CONTACTED`: two-way contact occurred; qualification/outcome must be saved.
- `HOT`: visit booked or buying intent within 30 days; sales takes ownership.
- `WARM`: interested in 1–3 months; dated nurture sequence.
- `COLD`: three missed calls, not interested, or not ready; no calls.
- `BOOKED`: confirmed site visit; suppress all generic outreach.
- `HUMAN_OWNED`: accepted by a salesperson; automation stops except approved logging/reminders.
- `OPTED_OUT`: suppress the relevant outreach channel and any dependent queue.

These are implementation recommendations. The source screenshots use simpler labels; map them explicitly during build rather than silently changing source rules.

## Required record fields for an MVP

`lead_id`, normalized phone, name (when available), source, created_at, channel eligibility/consent evidence, status, temperature, score and score rationale, call_attempt_count, last_call_at, last_call_result, call_summary, WhatsApp conversation reference/summary, `hold_until`, follow_up_at, booking status/time, owner, handoff timestamp, opt-out state, last_action, and `updated_at`.

Avoid storing sensitive data that is not needed. Confirm provider access controls, retention, and business policy before using real lead data.

## Reliability decisions

- **Idempotency:** Every inbound event and outbound action needs a stable key so retries cannot duplicate leads, messages, calls, or bookings.
- **Concurrency:** Recheck and claim a due action before sending. Define how simultaneous call and WhatsApp triggers update the same lead.
- **Stale work:** Re-evaluate status, booking, ownership, eligibility, attempt count, and active hold immediately before every action.
- **Bounded retries:** Three total call attempts; two-hour spacing after a missed call. Integration retries are separately bounded and logged.
- **Human ownership:** An accepted handoff or booking cancels generic nurture and call queues.
- **Chat hold:** No calls during the 30-minute active chat window; extend while conversation continues and do not replay stale calls after expiry.
- **Observability:** Log action, result, time, workflow/run identifier, and failure reason. Alert an operator and retain recoverable work.
- **Measurement:** Define funnel denominators and a baseline before asserting performance improvement.

## Open decisions before implementation

1. Which source is the first MVP integration?
2. Which telephony and WhatsApp providers are approved and available?
3. What exact permission/consent evidence controls calling and messaging?
4. What are the team's qualifying questions and scoring rubric?
5. How are visits confirmed, changed, cancelled, and handed to sales?
6. Who owns Hot leads, errors, and after-hours exceptions?
7. Is Google Sheets sufficient for row locking, access control, and audit history, or should the lead store move to a database/CRM?
8. Which timezone does the 1 PM report use?
9. What baseline and pilot success thresholds will be used?
