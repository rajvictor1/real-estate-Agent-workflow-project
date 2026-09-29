# What this workflow does, step by step

## 1. Capture every enquiry
Meta lead forms, the website form, and Google Ads enquiries feed one shared Google Sheet. Create one row per person and capture contact details, source, current status, communication permission, and owner. Match returning submissions to the existing lead record so two automations do not treat one person as two leads.

## 2. Make the first call promptly
The calling agent checks the latest record and calls within one minute. The screenshot says it skips leads already marked as booked. The agent speaks Hindi and asks the qualifying questions configured by the business. It should not invent answers or promise availability.

## 3. Handle unanswered calls
Wait two hours before retrying. Allow no more than three total attempts. After the third missed call, mark the lead Cold and stop automated calls. Keep the outcome in the record so another workflow cannot restart the same call sequence.

## 4. Qualify answered leads
Capture project, budget, size, own-use versus investment, and timing. Save a short call summary and lead score in the sheet. A booked visit is Hot; interest 1–3 months away is Warm; not interested or not ready is Cold.

## 5. Respond to WhatsApp messages
The WhatsApp agent reads the lead’s full history from the sheet, replies in Hindi or English, answers common questions, and can share approved photos, brochure, map, and layout. During an active chat, apply a 30-minute call hold so the calling agent does not interrupt.

## 6. Book or hand off
The WhatsApp agent can book a site visit in chat. Route price negotiation or a request for a salesperson to a human. Once a visit is booked or near-term buying intent is confirmed, mark Hot and alert the sales representative the same day. The screenshots say the team takes Hot leads from there.

## 7. Follow up by temperature
- **Hot:** sales team owns the conversation and next action.
- **Warm:** WhatsApp follow-up on days 2, 5, and 10, plus an AI call on the specific follow-up date.
- **Cold:** no calls; the diagram proposes one message per month and says the team can revive the lead later. Send that message only where permission and applicable messaging rules allow it.

If a Warm or Cold lead books a visit, promote the lead to Hot and stop the old nurture sequence.

## 8. Keep one shared record
Every stage updates the same Google Sheet: status, score, call attempt/result, chat summary, hold, follow-up date, visit, and owner. Check the latest record immediately before each queued action, and cancel stale actions after a booking, handoff, or opt-out.

## 9. Monitor the automation
Send an instant WhatsApp error alert when a step fails. Send one daily report at 1 PM with leads, calls, and site visits. Reconcile the report with the sheet so missing events are visible.

## Screenshot-faithful details versus implementation safeguards
The screenshot explicitly shows three intake sources, Google Sheets, first call within one minute, Hindi calling, skipped booked leads, team-defined questions, three attempts with a two-hour retry delay, answered-call qualification fields, call summary and score, the WhatsApp full-history lookup and 10–20 second response target, Hindi/English, questions/brochure/visit/human handoff outcomes, 30-minute hold, Hot/Warm/Cold routing, Warm day 2/5/10 messages and dated AI call, monthly Cold message/no calls, same-day Hot sales alert, revival by the team, immediate error alert, and 1 PM daily report.

Deduplication, consent/opt-out suppression, record locking, stale-job cancellation, and report reconciliation are reliability safeguards added to make those paths safe to operate. The 10–20 second reply is a target stated by the screenshot, not a measured service guarantee. Integration readiness has not been established by the screenshots.
