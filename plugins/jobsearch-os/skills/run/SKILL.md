---
name: run
description: >
  This skill should be used when the user runs "/run" or says "Run", "Run, last 7 days",
  "sync my job search", "update my tracker", "check my job emails", "any new rejections?",
  or asks for a refresh of application statuses from Gmail and Calendar.
metadata:
  version: "0.2.0"
---

# Run a JobSearch OS sync

Sweep Gmail and Calendar and bring the tracker up to date. Read the `jobsearch-os-rules` skill first and load the user's settings. Syncs run only when the user asks, never on a schedule.

## 1. Set the window

- If the user named a window ("Run, last 7 days"), use it.
- Otherwise use the gap since the last sync. Find it from the most recent Status Date or Date Applied in the tracker, or a "Last sync" note in the settings doc. If none exists, ask, suggesting 90 days for a first sync.

## 2. Gather

1. Search Gmail under the job label for the window.
2. Run keyword searches across all mail for the same window: application received, thank you for applying, interview, schedule, availability, unfortunately, regret, not moving forward, other candidates, position has been filled.
3. Search Calendar for interview events in the window and the next 30 days.
4. For each message, read the full body and the sender display name. Work out the real company and role, especially for generic ATS senders.

## 3. Classify and update

1. Read the tracker.
2. Match each item to a row by company and role. Create a row for a new application only when there is a clear confirmation.
3. Apply status changes using only the statuses in the settings. Set Status Date. Increment Interview Rounds when a new round is scheduled or completed, if that column exists. Tag completed interview rows as Interviewed.
4. Flag rows with no response past the ghosted window.
5. Write the changes, read the sheet back, and confirm the Dashboard still calculates.
6. Record the sync date in the settings doc as "Last sync: [date]".

## 4. Report

Reply with a short summary:
- New applications added
- Status changes (company, role, old status to new status)
- Upcoming interviews found, and whether a mock interview block or prep brief is still needed (offer `/prep`)
- Items that could not be classified, with sender and subject, so the user can tell Claude the pattern
- Applications now past the ghosted window

Do not move Drive folders, create calendar events or draft emails during a sync unless the user asks.
