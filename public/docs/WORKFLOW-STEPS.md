# What this workflow does, step by step

This guide turns the five screenshots into one operating sequence. Each step states its trigger, what the automation or person does, what gets recorded, and how the lead moves next. The screenshots describe the intended design; they do not prove that the integrations have been built or tested.

## 1. Bring enquiries into one queue
**Trigger:** A person submits a Meta lead form, the website form at `the property website`, or a Google Ads enquiry.

**Action:** Send the enquiry into the shared Google Sheet. Capture available name, phone, project interest, source, submission time, and communication preference or permission recorded by the source. Preserve the source label for channel reporting.

**Next:** Create or update a lead record, then check whether it is eligible for the calling workflow.

## 2. Normalize and deduplicate the lead
Normalize phone numbers and search for an existing record before creating a row. Append repeat enquiries to the existing history so two submissions do not start parallel calls or messages. Use a stable lead ID and retry-safe intake. The screenshots show one sheet, but do not specify a deduplication rule; that is an implementation safeguard.

## 3. Maintain one current lead record
Use the Google Sheet as the shared source of truth for contact details, source, status, temperature/score, attempt count and results, conversation summary, visit, active hold, next follow-up, owner, and update time. Every automation reads the latest row before acting and writes its outcome and timestamp afterward. Avoid decisions based on stale copies.

## 4. Check eligibility before outreach
Before any due call or message, check whether the lead is already Booked, opted out, in an active WhatsApp hold, already contacted for that action, or otherwise no longer eligible. The screenshot explicitly says to skip Booked leads; opt-out, duplicate-attempt, and stale-action checks are added safeguards. Record the suppression reason and cancel obsolete queued actions.

## 5. Make the first AI call within one minute
When an eligible new lead is written, the AI calling agent reads the current row and attempts the first call within one minute. It speaks Hindi and asks the qualifying questions defined by the business. It must not invent project facts or claim a booking is confirmed when it is not. Route requests for a person or questions outside its approved scope to the team.

## 6. Retry unanswered leads with a firm limit
Record each missed call, wait two hours, and recheck the row before retrying. Allow three total attempts including the first. After attempt three, mark Cold and stop automated calls; the team can revive the lead later. If a retry is answered, cancel remaining retries and proceed to qualification.

## 7. Qualify the answered lead and save the result
Capture project, budget, size, own use versus investment, and timeline. Use the team's configured question wording. Save a concise call summary, outcome, score, attempt count, and next action in the sheet. The screenshots do not define a scoring formula; configure agreed criteria before automated scoring is used.

## 8. Choose one temperature and route
- **Hot:** A site visit is booked or buying is expected within 30 days. Alert sales the same day; the team takes over.
- **Warm:** Interested, but likely 1–3 months away. Start scheduled follow-up.
- **Cold:** Three unanswered calls, not interested, or not ready. Stop calls and use only the permitted low-frequency re-engagement path.

Record why the status changed and cancel its old sequence so the lead is not in multiple active paths.

## 9. Handle inbound WhatsApp from full history
When the lead messages, the WhatsApp AI agent reads the lead's full history from the sheet and replies in Hindi or English. The screenshot's 10–20 second response is a target, not a measured guarantee. It can answer approved questions about price, size, location, or loans; share approved photos, brochure, map, or layout; book a visit; or hand off price negotiation and requested sales help to a person. Log the message, response, and next action.

## 10. Prevent calls from colliding with a chat
During an active WhatsApp conversation, apply the screenshot's 30-minute no-call hold. Store a `hold_until` time and check it immediately before dialing. Extend it if the conversation continues. When it expires, recheck status, booking, owner, opt-out, and attempt limit; do not replay calls that became stale during the hold.

## 11. Book the visit or transfer to a person
For a site visit, record date/time and relevant details, mark Hot, cancel nurture and calls, and alert sales the same day. For price negotiation or requested sales help, send the conversation context to a human. Mark the lead human-owned so automation does not compete with the salesperson, and record who accepted the handoff and when.

## 12. Run the Hot, Warm, and Cold follow-up paths
- **Hot:** The sales team owns the next action. General nurture stops after handoff or booking.
- **Warm:** WhatsApp messages on days 2, 5, and 10, plus an AI call on the follow-up date recorded for that lead. Recheck eligibility before each touch.
- **Cold:** No calls. The screenshot proposes one message per month and says the team may revive the lead. Send only where the channel is eligible; suppress after opt-out, booking, or human takeover.

If a Warm or Cold lead books a visit or shows near-term readiness, promote to Hot, alert sales, and cancel the old sequence immediately.

## 13. Log events and alert on failures
Record timestamps for triggers, attempts, messages, holds, suppressions, bookings, status changes, and handoffs. Send the screenshot's instant WhatsApp error alert when a step fails, with enough context to locate the lead and failed step without exposing unnecessary personal data. Bound retries and make them safe from duplicate records, messages, or bookings. Keep unresolved work visible for human resolution.

## 14. Send and reconcile the 1 PM report
At 1 PM, send one daily report covering leads, calls, and visits. Define the time zone and whether a lead count means unique people or form submissions. Reconcile totals against the sheet/event log, surface missing updates and open errors, and treat the report as an operational check rather than proof that each automation succeeded.

## 15. Review outcomes and improve
Review source volume, contact rate, qualification completeness, visits, Hot handoffs, follow-up completion, opt-outs, duplicates, failures, and lead-to-visit conversion. Use outcomes to refine question wording and scoring. Change one rule at a time, document it, and monitor whether lead quality and the contact experience improve.

## Screenshot coverage and boundaries
The screenshots specify three lead sources (Meta/Facebook/Instagram, website form, Google Search/Display), Google Sheets, a first call within one minute, Hindi calling, skipping Booked leads, team-defined questions, a two-hour retry and three total attempts, qualification fields (project, budget, size, own-use/investment, timeline), call summary and score, WhatsApp full-history lookup with Hindi/English and a 10–20 second response target, question answers, brochure/photos/map/layout, chat booking, price-talk sales handoff, a 30-minute call hold, Hot/Warm/Cold routes, same-day Hot sales alert, Warm WhatsApp on days 2/5/10 and a dated AI call, Cold no-calls and a monthly message with possible team revival, instant WhatsApp error alert, and a 1 PM leads/calls/visits report.

Deduplication, opt-out suppression, stable IDs, event logging, stale-action cancellation, score criteria, explicit human ownership, safe retries, report reconciliation, and outcome review are recommendations to make the depicted flow operable. Confirm actual sheet fields, service connections, message eligibility, time zone, score criteria, and owners before enabling automation. The screenshots do not verify integrations or production behavior.
