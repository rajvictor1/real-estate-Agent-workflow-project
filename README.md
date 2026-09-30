# Real Estate Lead Management Automation and Workflow

A recruiter-facing portfolio project by Rajesh Kumar. This repository contains a detailed workflow specification, source-faithful screenshot notes, implementation plan, architecture, interview narrative, and a live static case-study website.

## Project status at a glance

| Area | Status | Evidence boundary |
|---|---|---|
| Workflow requirements | Documented from five supplied screenshots | Source describes intended behavior, not a running automation |
| Case-study website | Built and deployed to Vercel | Static HTML/CSS/JavaScript portfolio artifact |
| GitHub source | Public repository | Code and project documentation are visible to anyone |
| n8n workflow design | Visual case study | Importable implementation package and access options are on BrandOps; no live services are connected here |
| Google Sheets | Specified as candidate lead record | No connected sheet or integration is included |
| AI calling / WhatsApp | Designed as workflow capabilities | Providers and production integrations are not selected or connected |
| Business results | Not measured | No conversion lift, time savings, or revenue claims are made |

## Why this project

The project models how a real estate team could manage Meta lead forms, website enquiries, and Google Ads enquiries through a shared lead record; respond quickly; qualify needs; continue on WhatsApp; and route leads to Hot, Warm, or Cold follow-up. It includes stop conditions, sales ownership, error alerting, and measurement so the design covers failure and accountability paths as well as the happy path.

The original client reference supplied for the workflow is **Om Shiv Build Vision**, website `omshivbuildvision.com`. This identifier is retained in the repository for source context at the owner’s request. It is deliberately omitted from Vercel output. Repository visibility is public at the owner’s request, so this source-specific identifier is publicly visible in repository files.

## Technology

### Actually used

- HTML, CSS, and JavaScript for the static, responsive project case study.
- Vercel for hosting the case-study site.
- GitHub for public source and documentation version control.

### Proposed for a future automation implementation

- **n8n** as the proposed workflow orchestrator. This public portfolio shows the workflow visually; implementation package access is handled through [BrandOps](https://brandops.site). No live n8n instance or integrations are connected here.
- **Google Sheets** as the initial shared lead record, subject to access control, data quality, and concurrency decisions.
- A selected calling/voice provider and WhatsApp Business API provider; none is selected or connected yet.

The public case study describes the workflow design and does not include importable n8n JSON. Do not describe AI calling, WhatsApp automation, or Sheets integration as connected or in production until configured and verified end to end.

## Repository map

- `public/index.html` — the one-page public case study. Its navigation jumps to the embedded Flow Diagram, plain-language explanation, technology, and project-detail sections on the same URL.
- `public/flow-diagram.html` — retained standalone diagram route; the main site now uses the embedded diagram so visitors can review the full project on one page.
- `public/docs/` — sanitized recruiter-facing copies served by Vercel.
- `N8N-WORKFLOW-GUIDE.md` — public step-by-step explanation of the workflow design and implementation access link.
- `public/images/n8n-workflow-editor.png` — screenshot reference shown in the n8n section.
- `WORKFLOW-STEPS.md` — detailed process specification and operating steps.
- `SCREENSHOT-WORKFLOW.md` — consolidated workflow diagram with source-specific details.
- `ARCHITECTURE.md` — system boundary, components, status labels, and key decisions.
- `IMPLEMENTATION-ROADMAP.md` — phased MVP, acceptance criteria, and future options.
- `INTERVIEW-GUIDE.md` — concise recruiter story, interview questions, and honest project description.
- `vercel.json` — static site configuration.

## n8n workflow access

This public portfolio includes a workflow diagram, screenshot, and step-by-step explanation, but no importable workflow JSON. Visit [BrandOps](https://brandops.site) for implementation package access and setup options. See [N8N-WORKFLOW-GUIDE.md](N8N-WORKFLOW-GUIDE.md) for the public workflow explanation.

## Local preview

Open `public/index.html` in a browser. The site is static and requires no build step.

## Deployment

The case-study site is deployed at <https://lead-management-workflow.vercel.app>. Vercel is configured to publish only `public/`; source-specific files at the repository root are not deployed. The public case study and guides omit the client name/domain. The renamed GitHub repository is public and connected to Vercel.

## Source fidelity and privacy

The workflow screenshots are design inputs, not proof of implementation. Source-specified timing and follow-up rules are identified as requirements; additional safeguards are identified as recommendations. The repository is public by owner request and includes the client name/domain in source context files. Vercel publishes only the sanitized `public/` directory; the public website and guides do not include that identifier. This public repository provides a visual specification rather than the importable workflow package.
