---
name: Meeting Scheduler
description: "Schedules meetings with internal and external stakeholders, managing invitations, and finding suitable time slots."
license: "MIT"
---

### Workflow
1.  **Parse Request**: Identify participants, topic, and desired timeframes from the user's request.
2.  **Check Calendars**: Access internal calendars to find mutual availability.
3.  **Propose Times**: Suggest available slots to all participants.
4.  **Send Invitations**: Once a time is confirmed, send out calendar invitations.
5.  **Handle RSVPs**: Track responses and manage rescheduling if necessary.

### Usage
To schedule a meeting, provide a natural language request:
`"Schedule a 30-minute meeting with John and Jane to discuss the Q3 report next week."`

### Example
`"Book a 1-hour project kickoff meeting with the engineering team for next Monday or Tuesday afternoon."`
