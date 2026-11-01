# Ward Office Appointment System — Explained Simply

*A plain-language walkthrough of the project, for anyone with no technical background.* Oct 29, 2026

---

## The problem, in one sentence

Citizens visiting a ward office in Kathmandu face four separate problems — long queues, being sent between rooms, the office system going down, and the signing officer being absent — and only one of these (queues) was expected before anyone actually asked citizens about it.

## The solution, in one sentence

**A free online appointment system that lets citizens book a time slot, see the right room in advance, and automatically blocks bookings on days the signing officer is unavailable — with a printable backup list for when the computer system itself goes down.**

---

## The story, in 6 steps

### Step 1 — Plan before building anything

Before any interviews or design work, a short project charter and baseline plan were written: what the project would deliver, who was involved, and what could go wrong. This is standard practice — a project starts with a plan, not with code.

> Like planning a wedding: date, guest list, budget, and a list of what could go wrong, all written down before anything is booked.

### Step 2 — Ask citizens what actually goes wrong

Citizens who had recently visited a ward office were interviewed about their experience. This is the step that mattered most — it overturned the starting assumption.

**Expected going in:** the main problem would be long queues.

**What citizens actually said:**

| What was said | The real problem |
| --- | --- |
| "The officer tells you to go to a different room number." | Citizens are sent between rooms — unclear which counter handles their service |
| "The server is down." | The office's existing computer system is often unavailable |
| "There are too many lines." | Long queues (the only problem that was expected) |
| "Sometimes the boss is not there to sign." | The signing officer is often absent, so citizens must return another day |

**The key insight:** a booking system alone only fixes the queue problem. Two of the four complaints happen *after* the citizen has already arrived — a booking slot doesn't help if the system is down or the signer isn't there that day.

> Like a doctor who asks "where does it hurt?" instead of assuming the diagnosis before the patient has spoken.

### Step 3 — Turn each real complaint into a specific, numbered rule

Every confirmed problem became a traceable requirement — not a vague goal, but a rule a developer or tester can check directly.

| Citizens' problem | Rule the system must follow |
| --- | --- |
| Sent to the wrong room | The booking confirmation and staff screen must show the exact room number for that service |
| System goes down | Staff can print the day's booking list, so the ward keeps working even if the computer system fails |
| Signing officer absent | Staff can mark the officer "unavailable" for a date; the system then blocks new bookings needing a signature that day, **and automatically notifies anyone already booked** to reschedule |
| Long queues | Citizens pick a specific time slot online instead of a first-come queue |

The result: 27 functional requirements and 14 non-functional requirements (like "the system must work even with a poor internet connection"), each one traceable back to a specific pain point from the interviews — nothing was invented without evidence.

> Like the rules of a football match — written down in advance, so everyone agrees what "fair" means before the game starts.

### Step 4 — Draw the process and the data, before writing any code

Two kinds of diagrams were produced:

- **Process flows** — a before-and-after picture of a citizen's visit, showing exactly where today's process breaks down and how the new one avoids it
- **Data model** — a map of everything the system needs to remember (bookings, services, staff, signing-officer availability) and how those pieces connect

> Like an architect's drawing of a house before any bricks are laid — it's far cheaper to fix a mistake on paper than after building.

### Step 5 — Build a working version and test it against real scenarios

A functioning prototype was built — not a mockup, an actual browser app you can click through: pick a service, see the room number, book a time, and see staff mark the signing officer unavailable and watch bookings react to that.

Alongside it, 22 specific test scenarios were written in "Given/When/Then" form — for example: *"Given the signing officer is marked unavailable for a date, when a citizen tries to book that date, then the system shows no available slots and suggests another date."* Each scenario is a concrete, checkable test — not a vague hope that "it should work."

> Like a model house you can actually walk through, paired with an inspector's checklist for exactly what to verify.

### Step 6 — Track the project honestly as it runs

Weekly status reports, a risk log, and a change log were kept throughout — including the moment the interview findings forced a change of direction (adding the room-number and officer-availability features that weren't in the original plan). This is normal, honest project management: plans change when real evidence comes in, and that change is recorded rather than hidden.

---

## Proof it actually works — try it yourself

The prototype isn't a slideshow — it's a real working mini-app:

1. Choose a service and note the room number shown
2. Book a time slot with a name and phone number
3. Switch to the staff view and mark the signing officer "unavailable" for a date
4. Try booking that same date again — the system now blocks it and explains why

Every one of the four citizen complaints has a visible, working fix in the prototype — not just a written promise.

---

## The one-breath answer for an interview

> "I went in assuming queues were the main problem, interviewed real citizens, and found three other issues I hadn't expected. I turned each confirmed problem into a specific, numbered requirement, designed the process and data model around them, and built a working prototype with 22 concrete test scenarios proving each fix actually works — including a printable fallback for when the computer system itself fails."

---

## Where each step lives in the project files

| Step | File |
| --- | --- |
| 1. Plan | `docs/00-project-charter.md` · `pm/01-baseline-plan.md` |
| 2. Interviews | `docs/01-interview-guide.md` · `docs/02-interview-notes.md` |
| 3. Requirements | `docs/03-SRS.md` (27 functional, 14 non-functional requirements) |
| 4. Diagrams | `diagrams/process-flows.md` · `diagrams/data-model.md` |
| 5. Prototype and tests | `src/index.html` · `docs/04-acceptance-criteria.md` (22 scenarios) |
| 6. Project tracking | `pm/status-report-1.md` · `pm/raid-log.csv` · `pm/change-log.csv` · `pm/decision-log.csv` |
