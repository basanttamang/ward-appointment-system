# Interview Notes

**Interviews held:** 23–24 October 2026 · **Interviewer:** Basant Tamang
**People interviewed:** 10 citizens who had recently visited a ward office in Kathmandu · 3 ward staff
**Method:** [in person / by phone], about 15 minutes each, using the [interview guide](01-interview-guide.md). No names recorded.

> **In simple words:** I asked people about their last visit to the ward office. They told me about four problems. Only one of them (long queues) was something I had expected. The other three were new, which is exactly why interviews matter.

## What people told us

| # | What was said | How we describe the problem |
|---|---|---|
| 1 | "The officer tells you to go to a different room number." | Citizens are sent between rooms because it's not clear which room or counter handles their service |
| 2 | "The server is down" or "the system is not working." | The ward office's existing computer system is often unavailable, which stops service |
| 3 | "There are too many lines in front of the offices." | Long queues and waiting |
| 4 | "Sometimes the boss is not there to sign." | The officer who must sign is not always present, so citizens have to come back another day |

## Pain points

Pain point IDs are never reused, so the requirements stay traceable. P1–P7 were my starting hypotheses; P8–P10 are new from the interviews.

| ID | Pain point | Source | Status |
|---|---|---|---|
| P1 | Long and unpredictable waiting times at the ward office | Interview finding 3 | **Confirmed** |
| P2 | Citizens arrive without the required documents and must return | — | Not raised; keep as an assumption |
| P3 | Citizens don't know which documents a service needs before visiting | — | Not raised; keep as an assumption |
| P4 | Staff cannot predict daily demand or plan their time | — | Not raised (no staff view yet) |
| P5 | No record of who was served, when, or how long it took | — | Not raised |
| P6 | Ward officers lack simple reports on service volumes | — | Not raised |
| P7 | Some citizens have no smartphone or limited internet | — | Not raised |
| **P8** | Citizens are sent between rooms; unclear which room or counter handles their service | Interview finding 1 | **New, confirmed** |
| **P9** | The existing ward computer system is often down, stopping service | Interview finding 2 | **New, confirmed** |
| **P10** | The signing officer is often absent, so citizens must return another day | Interview finding 4 | **New, confirmed** |

## Key findings

1. **Booking a time solves only part of the problem.** It helps with queues (P1), but two of the four complaints (P9 system down, P10 officer absent) happen *after* the citizen arrives. A booking system alone won't fix them.
2. **The ward office already has a computer system.** "The server is down" tells us there is an existing system that a new solution must work with or replace. We need to find out what it is.
3. **The signing officer is a bottleneck.** If one person must sign everything and isn't there, the whole service stops. This is partly a **process** problem (who else is allowed to sign?), not only a technology problem.
4. **Nobody mentioned documents.** I had assumed missing documents were a major problem (P2, P3). The interviews didn't confirm this, so those requirements are now lower priority until evidence appears.

## What this changes in the requirements (for SRS v1.0)

| Pain point | Proposed change |
|---|---|
| P8 Rooms | New requirement: booking confirmation and staff queue show the **room or counter number** for each service |
| P9 System down | Stronger availability requirement, plus a **fallback**: staff can print the day's booking list, so service continues if the system fails |
| P10 Officer absent | New requirement: staff can mark the signing officer as **unavailable**, which blocks new bookings needing a signature that day and **notifies booked citizens** to reschedule. Recommend the ward agrees a **delegated signer** (process change, outside the system) |
| P2, P3 Documents | Lower priority from Must to Should until confirmed |

## Gaps and next steps

- [ ] Talk to at least one **ward staff member** to understand the existing system (P9) and the signing rules (P10)
- [ ] Ask whether anyone has needed a **recommendation letter (sifaris)** and how it went (input for Project 3)
- [ ] Find out which **services** people were visiting for
