# Software Requirements Specification

**System:** Ward Office Appointment System
**Version:** 1.0 · **Date:** 26 October 2026 · **Author:** Basant Tamang

| Version | Date | Change | Approved by |
|---|---|---|---|
| 0.1 | 22 Oct 2026 | First draft from hypothesis pain points P1–P7 | — |
| 1.0 | 26 Oct 2026 | Updated after citizen interviews: P1 confirmed; P8–P10 added; unconfirmed requirements lowered in priority; out-of-scope recommendations added | [Stakeholder name] |

> **In simple words:** this is the rule book for the system. Every rule has a number, a priority, and a source: the problem it solves. Version 1.0 is based on what people actually said in interviews, not just my guesses.

**How to read the Source column:** P-numbers are pain points from the [interview notes](02-interview-notes.md). **Confirmed** means someone raised it in an interview. **Assumed** means it's sensible but no one has confirmed it yet; these must be checked with ward staff before go-live.

## 1. Introduction

### 1.1 Purpose

This document defines what the Ward Office Appointment System must do and how well it must do it. It is the agreed basis for design, development and acceptance testing.

### 1.2 Background: what the interviews found

Citizens described four problems: long queues (P1), being sent between rooms (P8), the existing ward computer system going down (P9), and the signing officer not being present (P10). Only the first is solved by booking a time. This specification therefore also covers room information, what happens when the signing officer is away, and how service continues when the system is down.

### 1.3 Scope

**In scope:** booking a time for a ward service; showing the room or counter and required documents; managing the daily queue; marking the signing officer as unavailable and notifying affected citizens; a printable daily list for when the system is down; daily reports.

**Out of scope:** issuing documents or signatures online, payments, integration with live national systems, and fixing the ward's existing computer system. See section 8 for recommendations on problems the software can't solve alone.

### 1.4 Definitions

| Term | Meaning |
|---|---|
| Ward | Lowest local government unit; Kathmandu Metropolitan City has 32 |
| Service | A ward office service, e.g. a recommendation letter (sifaris) or birth registration |
| Slot | A fixed time period in which one citizen can be served for one service |
| Signing officer | The official who must sign a document before it is issued, e.g. the ward chairperson |
| Reference number | Unique code given to a citizen when a booking is confirmed |
| BS / AD | Bikram Sambat (Nepali calendar) / Gregorian calendar |

## 2. Overall description

### 2.1 Users

| User | Description | Main needs |
|---|---|---|
| Citizen | Member of the public, usually on a mobile phone | Book a time, know where to go and what to bring, avoid wasted trips |
| Front-desk staff | Ward employee who receives visitors | See today's queue, record arrivals, keep working if the system fails |
| Ward officer / chairperson | Signs documents; needs reports | Tell citizens in advance when unavailable; see service volumes |
| Administrator | Municipality IT staff | Manage services, rooms, slots and staff accounts |

### 2.2 Constraints

- C1: Must work on low-cost Android phones and on 3G connections
- C2: Interface must be available in Nepali and English
- C3: Personal data must be handled in line with Nepal's Individual Privacy Act 2075
- C4: Walk-in visitors must still be served; booking is optional

### 2.3 Assumptions (to confirm with ward staff)

- A1: Each ward sets its own opening hours and number of slots per service
- A2: An SMS gateway is available to the municipality
- A3: The ward office already uses a computer system that sometimes fails (from P9; details unknown)
- A4: Recommendation letters need the ward chairperson's signature; birth registration and migration certificates are signed by the ward secretary as local registrar

## 3. Functional requirements

Priority uses MoSCoW: **M** must, **S** should, **C** could.

### 3.1 Services and information

| ID | Requirement | Priority | Source |
|---|---|---|---|
| FR-01 | The system shall list the services offered by a selected ward. | M | P8 (confirmed) |
| FR-22 | Each service shall have a room or counter number, shown on the booking page, the booking confirmation and the staff queue. | M | P8 (confirmed) |
| FR-02 | The system shall show the required documents for each service before the citizen books. | S | P2, P3 (assumed) |
| FR-03 | The system shall show the fee (if any) and the expected processing time for each service. | S | Assumed |

### 3.2 Booking

| ID | Requirement | Priority | Source |
|---|---|---|---|
| FR-04 | The system shall show available slots for a selected service and date, for the next 14 days. | M | P1 (confirmed) |
| FR-05 | The system shall allow a citizen to book an available slot by entering their name and a Nepali mobile number. | M | P1 (confirmed) |
| FR-06 | The system shall reject a mobile number that is not a valid 10-digit Nepali mobile number. | M | Assumed |
| FR-07 | The system shall allow a citizen at most one booking per service per day. | M | P1 (stops one person blocking many slots) |
| FR-08 | The system shall not allow two bookings for the same slot. | M | P1 (confirmed) |
| FR-09 | The system shall not allow bookings for past times or for days the ward is closed. | M | Assumed |
| FR-27 | The booking page shall show whether the signing officer is available on the chosen date. | S | P10 (confirmed) |
| FR-10 | On confirmation, the system shall display a unique reference number, the slot time, the room or counter, and the document checklist. | M | P1, P8 (confirmed) |
| FR-11 | The system shall send a confirmation SMS with the reference number, time and room. | S | Assumed (A2) |
| FR-12 | The system shall allow a citizen to cancel a booking using the reference number and mobile number, up to 1 hour before the slot. | S | Assumed |

### 3.3 Signing officer availability

| ID | Requirement | Priority | Source |
|---|---|---|---|
| FR-23 | Staff shall be able to mark the signing officer as unavailable for a whole day, with a reason. | M | P10 (confirmed) |
| FR-24 | When the signing officer is unavailable on a date, the system shall not offer slots on that date for services that need their signature. | M | P10 (confirmed) |
| FR-25 | When the signing officer is marked unavailable, the system shall list citizens already booked for affected services that day and send each an SMS asking them to rebook. | S | P10 (confirmed) |

### 3.4 Staff queue

| ID | Requirement | Priority | Source |
|---|---|---|---|
| FR-13 | The system shall show staff today's bookings for their ward, ordered by slot time, with the room for each. | M | P1, P8 (confirmed) |
| FR-14 | The system shall allow staff to find a booking by reference number or mobile number. | M | Assumed |
| FR-15 | The system shall allow staff to change a booking's status to Arrived, Completed or No-show. | M | Needed for NFR-05 and FR-18 |
| FR-16 | The system shall allow staff to add a walk-in visitor to today's queue. | S | C4 |
| FR-17 | The system shall show a count of booked, arrived, completed and no-show visitors for the day. | S | Assumed |
| FR-26 | Staff shall be able to print, or save as PDF, the day's booking list, so the ward can keep serving booked citizens if the system goes down. | M | P9 (confirmed) |

### 3.5 Reports and administration

| ID | Requirement | Priority | Source |
|---|---|---|---|
| FR-18 | The system shall produce a daily report of bookings by service and status for a selected ward and date. | S | P6 (assumed) |
| FR-19 | The system shall allow ward officers to export reports as CSV. | C | P6 (assumed) |
| FR-20 | The system shall allow administrators to create, edit and deactivate services, rooms, required documents, signature requirements and slot schedules. | M | A1, P8 |
| FR-21 | The system shall allow administrators to create staff accounts and assign each to one ward and one role. | M | Assumed |

## 4. Non-functional requirements

| ID | Category | Requirement | Priority | Source |
|---|---|---|---|---|
| NFR-01 | Performance | The booking page shall load within 3 seconds on a 3G mobile connection. | M | C1 |
| NFR-02 | Availability | The system shall be available 99.5% of the time during ward opening hours each month, excluding announced maintenance. | M | **P9 (confirmed)** |
| NFR-13 | Continuity | If the system is unavailable during opening hours, staff shall be able to serve booked citizens from the printed daily list (FR-26); visits handled on paper shall be entered within 1 working day. | M | **P9 (confirmed)** |
| NFR-14 | Continuity | During planned maintenance, the booking page shall show a message with the expected return time. | S | P9 (confirmed) |
| NFR-03 | Security | Staff, officer and administrator access shall require a username and password; passwords shall be stored hashed. | M | C3 |
| NFR-04 | Access control | Staff shall see bookings only for their own ward; only administrators may change services and accounts. | M | C3 |
| NFR-05 | Audit | The system shall record every booking status change and every signing-officer availability change with user, date and time, old value and new value. Audit records shall not be editable. | M | P10, C3 |
| NFR-06 | Privacy | Citizen mobile numbers shall be partly hidden on screens (e.g. 98XXXXX123). | M | C3 |
| NFR-07 | Retention | Booking records shall be kept for 2 years and then anonymised. | S | Assumed |
| NFR-08 | Usability | A first-time citizen shall be able to complete a booking in under 2 minutes without help. | M | P1 |
| NFR-09 | Language | All citizen-facing text shall be available in Nepali and English. | M | C2 |
| NFR-10 | Accessibility | Citizen pages shall meet WCAG 2.1 level AA. | S | Assumed |
| NFR-11 | Recoverability | Data shall be backed up daily; a restore shall be tested monthly with a recovery time under 4 hours. | M | P9 |
| NFR-12 | Compatibility | The system shall work on current Chrome for Android and on desktop Chrome, Firefox and Edge. | M | C1 |

## 5. External interfaces

| Interface | Direction | Purpose | Status |
|---|---|---|---|
| SMS gateway | Outbound | Booking confirmations; rebooking messages when the officer is unavailable | Specified; simulated in prototype |
| Existing ward system | Unknown | May hold current records (A3) | To be investigated |
| National ID system | Inbound lookup | Verify citizen identity | Future phase; out of scope |

The system's own API is specified in [api/openapi.yaml](../api/openapi.yaml).

## 6. Data requirements

The data model is in [diagrams/data-model.md](../diagrams/data-model.md).

| Data | Personal? | Who can see it | Kept for |
|---|---|---|---|
| Citizen name and mobile number | Yes | Staff of the booked ward, administrators | 2 years, then anonymised |
| Booking and status history | Linked to person | Staff of the ward, ward officer | 2 years |
| Officer availability | Staff identity | Everyone (available yes/no); reason visible to staff only | 2 years |
| Audit log | Staff identity | Administrators | 5 years |

## 7. Acceptance

Each must-have requirement has at least one acceptance scenario in [04-acceptance-criteria.md](04-acceptance-criteria.md). The system is accepted when all must-have scenarios pass and no critical defects are open.

## 8. Problems software can't solve alone: recommendations

| Pain point | Why software isn't enough | Recommendation |
|---|---|---|
| P10 Signing officer absent | The system can warn citizens, but someone still has to sign | The ward agrees a **delegated signer** for days the chairperson is away, confirmed by the municipality. Project 3 (digital recommendation letters) looks at this further |
| P9 Existing system down | Outages may be caused by power, internet or the server, outside this project | Interview ward IT staff to find the cause; record outages for one month to measure them |
| P8 Sent between rooms | Room numbers on screen help, but the building also needs clear signs | Put a printed sign at the entrance listing each service and its room |
