# Interview guide

## One-line project description

I designed a state-based real estate lead-management workflow that connects multi-source enquiry capture, AI-assisted qualification, WhatsApp follow-up, sales ownership, failure handling, and measurement. I built the case-study website; the n8n and provider integrations are proposed next steps, not completed work.

## 45-second version

“Real estate leads arrive through paid social, a website, and search ads, and the operational risk is losing context or following up inconsistently. I translated the desired process into one shared lead-state model. The design includes a one-minute first call target, a bounded retry policy, structured qualification, WhatsApp with full history, a 30-minute chat hold, Hot/Warm/Cold routing, same-day sales ownership for Hot leads, and error/reporting controls. I built and deployed the recruiter-facing project site on Vercel and documented the architecture and implementation plan in a private GitHub repository. I have not represented the n8n or calling/WhatsApp integrations as live; the next milestone is a controlled MVP with synthetic data and clear acceptance tests.”

## What is implemented versus designed

**Implemented:** static responsive case-study site (HTML/CSS/JavaScript), Vercel deployment, private GitHub repository, screenshot-based workflow specification, step-by-step operating guide, architecture, roadmap, and interview narrative.

**Designed, not implemented:** n8n orchestration, Google Sheets connection, AI voice calls, WhatsApp Business messaging, channel triggers, reporting automation, and end-to-end lead handling.

**Not measured:** response-time improvement, contact rate, visits, conversion lift, revenue, cost reduction, or automation savings.

## Likely recruiter questions

### Why n8n?
It is a reasonable candidate to orchestrate webhook triggers, state checks, delays, branches, retries, and human escalation in a visual workflow. It is proposed, not a proven selection; provider support, operational controls, security, observability, and scale should be assessed during the MVP.

### Why use Google Sheets?
The source workflow specifies a Google Sheet as a shared lead record. It can be a quick pilot store if concurrency, access, and audit requirements are modest. A CRM or database may be better if multiple workflows and staff need transactional updates or detailed access control.

### How do you prevent duplicate contact?
Use a stable lead identity, deduplicate at intake, make external actions idempotent, re-read the current state before each action, and cancel stale scheduled work after booking, opt-out, or human ownership.

### How do you keep a human in control?
Sales takes Hot leads; price negotiation and requested human assistance are handed off. Booking and human ownership suppress general automation. Errors remain visible for operator resolution.

### What would you build first?
One source to a durable, auditable lead record, using synthetic data, with duplicate handling and status checks. Then add the call path and prove bounded retries and suppression before enabling real outreach.

### How would you measure success?
Define baseline and pilot cohorts. Measure first-attempt latency, contact rate, qualification completeness, visit booking, handoff response, missed/stale actions, duplicate rate, opt-outs, failure recovery, and cost per contacted lead. Report results only after collecting data.

## Demo walkthrough

1. Open the case-study site and state clearly that it is a design and portfolio presentation.
2. Trace a lead from the three anonymized sources into the shared lead record.
3. Explain the call eligibility check and bounded retry path.
4. Show the qualification fields and explain that the scoring rubric is an open business decision.
5. Compare Hot, Warm, and Cold routes, then point out the chat hold and sales handoff.
6. Finish with architecture status, failure controls, proposed MVP phases, and the measurement plan.

## Avoid these claims until verified

Do not say n8n automation is deployed, leads are being called or messaged, integrations are connected, the project improved conversion, saved time, generated revenue, or is production-ready. Say “designed,” “proposed,” “built,” “deployed,” or “measured” according to the evidence available.
