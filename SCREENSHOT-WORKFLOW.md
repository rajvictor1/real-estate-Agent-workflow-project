# Lead Management Workflow

## One end-to-end flow

```mermaid
flowchart TD
    A[Meta lead form<br/>Facebook / Instagram] --> D[Google Sheet: Leads<br/>one row per lead]
    B[Website form<br/>omshivbuildvision.com] --> D
    C[Google Ads<br/>Search / Display] --> D
    D --> E[AI calling agent<br/>attempt first call within 1 minute<br/>Hindi; read lead record; skip booked leads]
    E --> F{Call answered?}
    F -- No --> G[Retry after 2 hours]
    G --> H{Answered on retry?<br/>Maximum 3 total attempts}
    H -- No --> I[Mark Cold<br/>stop automated calls;<br/>team may revive later]
    H -- Yes --> J[Qualify conversation]
    F -- Yes --> J
    J[Capture project, budget, size,<br/>own use or investment, timeline;<br/>write summary and score to sheet] --> K{Outcome / intent}
    K -- Site visit booked --> L[Hot: same-day sales alert;<br/>sales team owns next step]
    K -- Interested later --> M[Warm: follow-up sequence]
    K -- Not interested --> N[Cold: stop calls;<br/>one message per month; team may revive]
    K -- Questions / brochure / booking --> O[WhatsApp AI agent<br/>Hindi or English; use full lead history]
    O --> P{Chat active?}
    P -- Yes --> Q[30-minute call hold<br/>no calls while chat is active]
    O --> R[Answer questions / send brochure]
    O --> S[Book site visit in chat]
    O --> T{Price negotiation or sales request?}
    T -- Yes --> U[Human handoff to sales]
    R --> V[Update sheet: status, score,<br/>conversation, outcome, next follow-up, owner]
    S --> V
    U --> V
    Q --> V
    L --> V
    M --> V
    N --> V
    I --> V
    V --> W{Current lead temperature}
    W -- Hot --> X[Sales team takes over]
    W -- Warm --> Y[WhatsApp day 2, 5, 10;<br/>AI call on scheduled follow-up date]
    W -- Cold --> Z[One message per month;<br/>no calls; team can revive]
    Y --> AA{Books a visit / becomes ready?}
    Z --> AA
    AA -- Yes --> X
    AA -- No --> V
    V -. any workflow failure .-> AB[Instant WhatsApp error alert]
    V -. daily at 1 PM .-> AC[Report: leads, calls, visits]
```

## Operating rules

1. **One record per lead:** Google Sheet is the shared source of truth. Store contact details, source, consent/communication preference, status, score, call/chat summaries, attempts, hold, follow-up date, and assigned owner.
2. **One owner at a time:** Automation owns new leads and scheduled follow-up. Sales owns Hot leads and any explicit human handoff. Log the owner and handoff time.
3. **Stop duplicate outreach:** Before any call or message, check the latest status, active WhatsApp hold, opt-out, booked visit, and last contact time. A booking or opt-out suppresses all queued outreach immediately.
4. **Call policy:** First attempt within one minute; retry unanswered leads after two hours, capped at three total attempts. Then mark Cold and stop automated calls.
5. **WhatsApp policy:** Use lead history; pause calls during an active chat for 30 minutes. Answer questions, share approved brochure material, and book visits. Route price negotiation or requested human help to sales.
6. **Temperature policy:** Hot means a visit is booked or purchase intent is within 30 days; alert sales the same day. Warm means interested in 1–3 months; use the scheduled day 2, 5, 10 messages and a dated call. Cold means no answer after three attempts, not interested, or not ready; no calls and at most one monthly message where permitted. If a Warm/Cold lead books a visit or becomes ready, promote to Hot.
7. **Monitoring:** Send an immediate WhatsApp alert on workflow failures. Send one daily 1 PM report with lead, call, and visit counts.

## Build notes and decision points

- The screenshots describe intended behavior, not verified integrations. Connectors, permissions, timing, and spreadsheet fields still need implementation and validation.
- Confirm consent and applicable messaging rules before automated calls or WhatsApp messages; honor opt-outs across every channel.
- The diagram suggests WhatsApp messages to Cold leads. Apply that only where the person has the required permission and the message is allowed; otherwise suppress it.
- Define what “active chat” means operationally (for example, a recent inbound message) and extend the hold when the conversation continues, so calls do not resume mid-conversation.
- Choose a reliable lead identifier and deduplicate on intake (normalized phone number plus source/form context) to prevent duplicate records and parallel calls.
