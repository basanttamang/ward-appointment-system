# Ward Office Appointment System

*A self-initiated systems analysis and delivery case study by Basant Tamang.*

Citizens visiting ward offices in Kathmandu queue without knowing how long they will wait. Interviews showed that queues are only part of the problem: people are also sent between rooms, the existing ward system goes down, and the officer who must sign is often absent. This project analyses that service and specifies, prototypes and tests an online appointment system that addresses all four problems where software can, and recommends process changes where it can't.

> **Status:** Day 5 of 12 — requirements v1.0 agreed from interview findings; prototype v1.0 ready for user testing on 31 Oct.

> **In simple words:** I talked to people about ward office visits, wrote down the problems, turned them into clear rules for a system, built a working practice version, and will test it with real users.

## Try the prototype

Open [`src/index.html`](src/index.html) in a browser, or on GitHub Pages: `https://basanttamang.github.io/ward-appointment-system/src/`

It runs in the browser and stores data only on your device. Things to try:
- **Book appointment:** choose a recommendation letter; note the room number and the chairperson's availability
- **Staff queue:** mark the chairperson unavailable for a date, then try booking that date again
- **Staff queue:** print or save the day's list (what staff use if the system goes down)
- **Audit log:** see every change recorded

## Deliverables

Every document below is written in **plain Markdown** (`.md`, GitHub's native format — opens automatically formatted on this page) **and** saved as a **Word file** (`.docx`) for easy reading or printing. Click the `.md` link to read it here on GitHub; click `.docx` to download a Word copy. Diagrams are plain `.png` pictures.

**New here? Start with the plain-English walkthrough:** [Explained Simply (.md)](docs/00-explained-simply.md) · [Word copy (.docx)](docs/00-explained-simply.docx) — the whole project in 6 steps, no technical background needed.

| # | Deliverable | Read on GitHub | Word copy | Status |
|---|---|---|---|---|
| 0 | **Explained Simply** | [.md](docs/00-explained-simply.md) | [.docx](docs/00-explained-simply.docx) | The whole project in 6 plain-English steps, with a try-it-yourself walkthrough |
| 1 | Project charter | [.md](docs/00-project-charter.md) | [.docx](docs/00-project-charter.docx) | Done |
| 2 | Baseline project plan | [.md](pm/01-baseline-plan.md) | [.docx](pm/01-baseline-plan.docx) | Done |
| 3 | Interview guide | [.md](docs/01-interview-guide.md) | [.docx](docs/01-interview-guide.docx) | Done |
| 4 | Interview notes and pain points | [.md](docs/02-interview-notes.md) | [.docx](docs/02-interview-notes.docx) | Done — staff interview still to come |
| 5 | Process flows: as-is and to-be (pictures) | [.md](diagrams/process-flows.md) | [as-is.png](diagrams/process-flow-as-is.png) · [to-be.png](diagrams/process-flow-to-be.png) | Done |
| 6 | Software Requirements Specification v1.0 | [.md](docs/03-SRS.md) | [.docx](docs/03-SRS.docx) | Done: 27 functional and 14 non-functional requirements |
| 7 | Data model (picture) | [.md](diagrams/data-model.md) | [erd.png](diagrams/data-model-erd.png) | Done |
| 8 | API specification | [.yaml](api/openapi.yaml) | — (technical file; see README notes) | Done: 9 endpoints, OpenAPI 3 |
| 9 | Acceptance criteria | [.md](docs/04-acceptance-criteria.md) | [.docx](docs/04-acceptance-criteria.docx) | Done: 22 scenarios |
| 10 | Working prototype v1.0 | [src/index.html](src/index.html) | — (open in a browser, not Word) | Done |
| 11 | Requirements traceability matrix | [.csv](docs/05-traceability-matrix.csv) | — (open in Excel/Google Sheets) | Sources and tests linked; results after UAT |
| 12 | UAT results and acceptance record | — | — | Planned 31 Oct |
| 13 | Handover pack and closure report | — | — | Planned 1–2 Nov |

Project management records: Status report 1 ([.md](pm/status-report-1.md) · [.docx](pm/status-report-1.docx)) · [RAID log (.csv)](pm/raid-log.csv) · [Change log (.csv)](pm/change-log.csv) · [Decision log (.csv)](pm/decision-log.csv)

## Progress log

| Date | What was done |
|---|---|
| 22 Oct 2026 | Project charter, baseline plan with three-point estimates, risk log and interview guide created. Team invited. |
| 23–24 Oct 2026 | Citizen interviews. Found that queues are only one of four problems: people are also sent between rooms, the existing system goes down, and the signing officer is often absent. Status report 1 issued. |
| 25–26 Oct 2026 | Change request CR-01 approved to address the new problems. SRS v1.0, process flows, data model and API updated. Prototype v1.0 adds room numbers, signing-officer availability with rebooking, and a printable list for downtime. 22 acceptance scenarios written. |

## How the interview findings shaped the design

| What people said | Pain point | What the system does | What it can't do alone |
|---|---|---|---|
| "Too many lines" | P1 | Book a time slot | — |
| "Go to a different room number" | P8 | Shows the room before you travel and on the confirmation | Signs in the building are still needed |
| "The server is down" | P9 | Printable daily list so service continues; availability target | The cause of today's outages needs investigating |
| "The boss is not there to sign" | P10 | Blocks booking on days the officer is away and tells booked citizens to rebook | Someone must be allowed to sign in their place |

## Tools

Mermaid (process flows), dbdiagram.io (data model), Swagger Editor (OpenAPI), HTML/CSS/JavaScript (prototype), GitHub (plan, tracking and version history).
