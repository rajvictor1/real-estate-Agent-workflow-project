# Real Estate Lead Management Automation and Workflow

A recruiter-facing portfolio project by Rajesh Kumar. This repository contains a detailed workflow specification, source-faithful screenshot notes, implementation plan, architecture, interview narrative, and a live static case-study website.

## Project status at a glance

| Area | Status | Evidence boundary |
|---|---|---|
| Workflow requirements | Documented from five supplied screenshots | Source describes intended behavior, not a running automation |
| Case-study website | Built and deployed to Vercel | Static HTML/CSS/JavaScript portfolio artifact |
| GitHub source | Private repository | Documentation and source code are versioned here |
| n8n orchestration | Proposed next implementation | No live n8n workflow is included or claimed |
| Google Sheets | Specified as candidate lead record | No connected sheet or integration is included |
| AI calling / WhatsApp | Designed as workflow capabilities | Providers and production integrations are not selected or connected |
| Business results | Not measured | No conversion lift, time savings, or revenue claims are made |

## Why this project

The project models how a real estate team could manage Meta lead forms, website enquiries, and Google Ads enquiries through a shared lead record; respond quickly; qualify needs; continue on WhatsApp; and route leads to Hot, Warm, or Cold follow-up. It includes stop conditions, sales ownership, error alerting, and measurement so the design covers failure and accountability paths as well as the happy path.

The original client reference supplied for the workflow is **Om Shiv Build Vision**, website `omshivbuildvision.com`. This identifier is retained in the private repository for source context. It is deliberately omitted from the public case-study page deployed on Vercel. Keep this repository private unless the client gives explicit permission to disclose the relationship and source details.

## Technology

### Actually used

- HTML, CSS, and JavaScript for the static, responsive project case study.
- Vercel for hosting the case-study site.
- GitHub for private source and documentation version control.

### Proposed for a future automation implementation

- **n8n** as the workflow orchestrator for intake, state checks, call scheduling, messaging routes, human handoff, error branches, and reporting.
- **Google Sheets** as the initial shared lead record, subject to access control, data quality, and concurrency decisions.
- A selected calling/voice provider and WhatsApp Business API provider; none is selected or connected yet.

Do not describe n8n, AI calling, WhatsApp automation, or Sheets integration as built or in production until there is a working workflow export, integration evidence, and end-to-end verification.

## Repository map

- `public/index.html` — public, anonymized case-study site.
- `public/docs/` — sanitized recruiter-facing copies served by Vercel.
- `WORKFLOW-STEPS.md` — detailed process specification and operating steps.
- `SCREENSHOT-WORKFLOW.md` — consolidated workflow diagram with source-specific details.
- `ARCHITECTURE.md` — system boundary, components, status labels, and key decisions.
- `IMPLEMENTATION-ROADMAP.md` — phased MVP, acceptance criteria, and future options.
- `INTERVIEW-GUIDE.md` — concise recruiter story, interview questions, and honest project description.
- `vercel.json` — static site configuration.

## Local preview

Open `public/index.html` in a browser. The site is static and requires no build step.

## Deployment

The case-study site is deployed at <https://lead-management-workflow.vercel.app>. Vercel is configured to publish only `public/`; client-specific source files stay in the private repository and are not part of the website deployment. The public case study and its linked documents use anonymized references. The GitHub repository is private and connected to Vercel.

## Source fidelity and privacy

The workflow screenshots are design inputs, not proof of implementation. Source-specified timing and follow-up rules are identified as requirements; additional safeguards are identified as recommendations. The repo is private because it records a client-specific source reference. Do not publish it or its source-specific files without approval. Vercel publishes only the sanitized `public/` directory; files at the repository root are excluded from the production site.
