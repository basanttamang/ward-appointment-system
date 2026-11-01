# Acceptance Criteria and UAT Scenarios

**Version:** 1.0 · Each scenario has an ID used in the [traceability matrix](05-traceability-matrix.csv).

> **In simple words:** simple tests anyone can run. **Given** = the situation, **When** = what you do, **Then** = what should happen. If it happens, the test passes. Version 1.0 adds tests UAT-18 to UAT-22 for the problems found in interviews.

Run each scenario on the [prototype](../src/index.html). Record Pass or Fail, the tester and the date in the results table at the end.

## Citizen: services and booking

**UAT-01 — See services and documents (FR-01, FR-02)**
```
Given I open the booking page for Ward 4
When I choose the service "Birth registration"
Then I see the list of required documents before choosing a slot
```

**UAT-02 — See free slots (FR-04)**
```
Given "Birth registration" has free slots tomorrow
When I choose tomorrow's date
Then I see only the free slots, ordered by time
And I cannot choose a date more than 14 days ahead
```

**UAT-03 — Book a free slot (FR-05, FR-10)**
```
Given the 10:00 slot tomorrow is free
When I enter my name and mobile number 9841234567 and confirm
Then I see a reference number, the slot time and the document checklist
And the 10:00 slot no longer appears as free
```

**UAT-04 — Invalid mobile number rejected (FR-06)**
```
Given I am booking a slot
When I enter the mobile number 12345
Then the booking is not made
And I see the message "Enter a 10-digit mobile number starting with 96, 97 or 98"
```

**UAT-05 — One booking per service per day (FR-07)**
```
Given I already have a booking for "Birth registration" tomorrow with 9841234567
When I try to book another "Birth registration" slot tomorrow with the same number
Then the booking is refused with a message that I already have one
```

**UAT-06 — Slot cannot be double-booked (FR-08)**
```
Given another citizen has just booked the 10:30 slot
When I try to book the 10:30 slot
Then the booking is refused and I am asked to choose another slot
```

**UAT-07 — No past or closed-day bookings (FR-09)**
```
Given today is Saturday, when the ward is closed
When I choose today's date
Then no slots are shown
And slots earlier than the current time today are never shown
```

**UAT-08 — Cancel a booking (FR-12)**
```
Given I have a booking more than 1 hour away
When I enter my reference number and mobile number and cancel
Then the booking shows as Cancelled
And the slot becomes free again
```

## Staff: queue

**UAT-09 — See today's queue (FR-13, FR-17)**
```
Given there are bookings for today
When I open the staff queue
Then I see today's bookings ordered by time
And totals for booked, arrived, completed and no-show
```

**UAT-10 — Find a booking (FR-14)**
```
Given a booking exists with reference W04-…
When I search by its reference number or the citizen's mobile number
Then only matching bookings are shown
```

**UAT-11 — Update status and audit (FR-15, NFR-05)**
```
Given a booking with status Booked
When I mark it Arrived and then Completed
Then the status shows Completed
And the audit log shows two entries with my name, time, old and new status
```

**UAT-12 — Add a walk-in (FR-16)**
```
Given a visitor arrives without a booking
When I add them as a walk-in for "Recommendation letter"
Then they appear in today's queue marked Walk-in, with status Arrived
```

**UAT-13 — Mobile numbers masked (NFR-06)**
```
Given I am viewing the queue
Then mobile numbers appear as 98XXXXX567
```

## Reports

**UAT-14 — Daily report (FR-18)**
```
Given bookings with different statuses exist for today
When I open the daily report
Then I see counts by service for booked, completed, no-show and cancelled
And the totals match the queue
```

**UAT-15 — Export report (FR-19)**
```
Given I am viewing the daily report
When I choose Export CSV
Then I get the same figures as comma-separated text
```

## From the interviews: rooms, signing officer, downtime

**UAT-18 — Room shown everywhere (FR-22, FR-10, FR-13)**
```
Given "Relationship verification recommendation" is handled in Room 3
When I choose that service, book a slot, and staff open the queue
Then I see "Room 3" before booking, on my confirmation, and in the staff queue
```

**UAT-19 — No bookings when the signing officer is away (FR-23, FR-24)**
```
Given staff mark the ward chairperson unavailable on 27 Oct with a reason
When a citizen chooses a recommendation letter on 27 Oct
Then no times are shown and a message says the chairperson is not available
And a service that doesn't need a signature (birth registration) still shows times
```

**UAT-20 — Booked citizens told to rebook (FR-25)**
```
Given a citizen has already booked a recommendation letter on 27 Oct
When staff mark the chairperson unavailable on 27 Oct
Then the citizen is listed as needing an SMS to rebook
And the booking shows "Asked to rebook" in the queue and on "My booking"
```

**UAT-21 — Printable list for downtime (FR-26, NFR-13)**
```
Given there are bookings for today
When staff choose "Print or save today's list"
Then a clean list prints with time, reference, name, service, room and status
And no buttons or menus appear on the printout
```

**UAT-22 — Officer availability shown to citizens (FR-27)**
```
Given the chairperson is available on 28 Oct
When I choose a recommendation letter on 28 Oct
Then I see "Ward chairperson: available on this date"
```

## Non-functional checks

**UAT-16 — Booking under 2 minutes (NFR-08)**
```
Given a tester who has not used the system before
When they book a slot without help
Then they finish in under 2 minutes (time it)
```

**UAT-17 — Works on a phone (NFR-12)**
```
Given the booking page on Chrome for Android
Then all steps work without zooming or horizontal scrolling
```

## Results

| ID | Tester | Date | Result | Defect / notes |
|---|---|---|---|---|
| UAT-01 | | | | |
| UAT-02 | | | | |
| UAT-03 | | | | |
| UAT-04 | | | | |
| UAT-05 | | | | |
| UAT-06 | | | | |
| UAT-07 | | | | |
| UAT-08 | | | | |
| UAT-09 | | | | |
| UAT-10 | | | | |
| UAT-11 | | | | |
| UAT-12 | | | | |
| UAT-13 | | | | |
| UAT-14 | | | | |
| UAT-15 | | | | |
| UAT-16 | | | | |
| UAT-17 | | | | |
| UAT-18 | | | | |
| UAT-19 | | | | |
| UAT-20 | | | | |
| UAT-21 | | | | |
| UAT-22 | | | | |
