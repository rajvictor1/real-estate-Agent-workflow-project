# Implementation roadmap

This roadmap follows the visual n8n workflow case study. The importable implementation package is not included in this public repository; see BrandOps for access options. The current repository contains no connected or running n8n automation.

## Phase 0 — Confirm the operating contract

**Deliverables:** agreed lead schema, qualifying questions, score rubric, Hot/Warm/Cold definitions, ownership map, channel permission rules, approved WhatsApp content, timezone, and visit-booking policy.

**Acceptance criteria:** a team member can decide the expected next state for representative new, duplicate, booked, opted-out, unreachable, warm, and human-owned lead examples.

## Phase 1 — Intake and shared state

**Proposed stack:** one form/source, n8n, and a controlled lead store (Google Sheets only if it supports needed access, concurrency, and audit requirements).

**Build:** validate/normalize fields, assign stable lead ID, deduplicate, persist source attribution, log events, and provide a human review view. Start in test mode with synthetic records.

**Acceptance criteria:** replaying the same source event does not create a second lead; malformed records are visible; opted-out and booked records are suppressed; every accepted record has a traceable source and timestamp.

## Phase 2 — Calling with human review

**Build:** connect one approved calling provider; enforce first-attempt timing, skip booked/held/ineligible records, retry unanswered leads after two hours, cap at three total attempts, capture structured qualification, and notify a human on exceptions.

**Acceptance criteria:** tests cover answer, no answer, retry answer, third missed attempt, existing booking, opt-out, invalid phone, provider failure, and a lead whose status changes while a call is queued. No duplicate attempt is made on workflow replay.

## Phase 3 — WhatsApp and handoff

**Build:** connect an approved WhatsApp Business provider; retrieve lead history; respond only with approved facts/material; pause calls for an active chat; support site booking and human transfer; cancel stale nurture after ownership or booking changes.

**Acceptance criteria:** tests cover Hindi/English routing, unknown question, approved and unapproved content, active hold, extended conversation, booking, price negotiation handoff, opt-out, delivery failure, and duplicate inbound webhook.

## Phase 4 — Temperature-based follow-up

**Build:** schedule Warm messages for days 2/5/10 and a call on the record's follow-up date; define eligible Cold monthly re-engagement; promote booked/near-term leads to Hot; alert sales same day.

**Acceptance criteria:** every scheduled job checks current state at send time; Hot/Booked/Human-owned/Opted-out leads do not receive stale nurture; time-zone and daylight-saving behavior is documented; handoff delivery is logged.

## Phase 5 — Reporting and controlled pilot

**Build:** 1 PM report for leads, calls, and visits; error alert; event reconciliation; dashboard/weekly review; pilot with an agreed cohort and a human override.

**Acceptance criteria:** report counts reconcile to defined source records; failures are visible; no outreach happens outside the approved cohort; baseline and comparison windows are documented; stakeholders agree on the go/no-go criteria.

## Required now

- Validate the business's actual process and permitted contact rules.
- Select providers and determine whether Sheets is adequate.
- Implement stable identity, state checks, logs, and human ownership before autonomous outreach.

## Recommended

- Pilot one intake channel and one contact path first.
- Keep AI-generated qualification summaries reviewable by sales.
- Measure latency, contact, visit, suppression, error, and cost rates from day one.

## Future / optional

- Replace Sheets with CRM/database when concurrency, access, or audit requirements warrant it.
- Add richer lead scoring only after outcome labels and sufficient quality data exist.
- Add multiple channels and predictive prioritization only after the single-channel path is dependable.
