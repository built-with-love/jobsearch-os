---
name: jobsearch-os-rules
description: >
  This skill should be used whenever a JobSearch OS task touches the user's job search tracker,
  job search Drive folders, Gmail job label, interview calendar, cover letters, resumes or
  thank-you emails, for example "update my tracker", "file this in the company folder",
  "what's the status of my applications", or before running any other JobSearch OS skill
  (setup, run, apply, prep, thanks). It holds the standing rules and how to load the user's settings.
metadata:
  version: "0.1.0"
---

# JobSearch OS: standing rules

JobSearch OS is a human-in-the-loop job search workflow. Claude drafts, files, tracks and prepares. The user finds the roles, decides, applies, interviews, edits and sends. Never send an email, submit an application, or delete or trash a file unless the user explicitly asks in this conversation.

## 1. Load the user's settings first

Every JobSearch OS task depends on the user's own details. Load them before doing anything else:

1. If the conversation or Project instructions already contain a "JobSearch OS settings" block, use it.
2. Otherwise, search Google Drive for a Google Doc whose title contains `JobSearch OS Settings` and read it.
3. If neither exists, stop and tell the user to run the setup skill (`/setup`) first. Do not guess any ID, label or rule.

The settings hold: name, target roles and level, locations, pay floor, search email or alias, portfolio and LinkedIn links, Gmail label name, Drive year folder ID, tracker Sheet ID, status list, ghosted window in days, archive rule for referrals, file naming patterns, cover letter header and writing rules, banned words, claims the user won't make, mock interview lengths, thank-you and review timing, approval boundaries, and working style. See `references/settings-template.md` for the exact layout.

If a setting a task needs is still a placeholder (for example, the tracker Sheet ID before the tracker exists), say which one is missing and how to fill it, then stop that part of the task.

## 2. Tracker rules

- The tracker is one Google Sheet. Edit it in place with the Google Sheets connector. Never create an .xlsx file, a dated copy or a second tracker unless the user asks.
- Read the sheet first, make the change, read it back to confirm, and check that the Dashboard tab formulas still calculate.
- If the Sheets connector is off or an edit fails, stop and tell the user. Do not work around it with a new file.
- Use only the statuses in the settings. A status the settings don't list needs the user's confirmation first.
- Flag rows with no response after the ghosted window as likely ghosted. Never change their status on your own.
- Fill Status Date when a status changes and keep Days to Status a plain number.

## 3. Drive rules

- Everything lives under the Drive year folder from the settings. One subfolder per company, named with the company name.
- Companies with status Rejected go in the `Rejected` subfolder, stalled ones in `Inactive`. Active ones stay in the year folder. Ask before moving a folder.
- Find files with a title search on the company name (Drive search uses `title contains`, not `name contains`).
- Save job descriptions, prep briefs and cover letters as Google Docs in the company folder. Save each tailored resume as both a .docx and a Google Doc, using the naming pattern from the settings.
- Never trash or delete a file unless the user asks.

## 4. Gmail and Calendar rules

- Sweep the Gmail label from the settings. Pair the label sweep with keyword searches (application, received, interview, schedule, unfortunately, regret, other candidates, moving forward), and periodically re-run the rejection-language search even when not asked.
- Read full email bodies and sender display names, not just domains, because applicant tracking system (ATS) confirmations often hide the real company.
- Size each search window to the gap since the last sync, unless the user gives one.
- Create calendar events only for mock interviews and draft-review blocks, using the timing rules in the settings.

## 5. Writing rules

- Follow the user's writing rules and banned words from the settings in every draft.
- Never claim anything on the user's "claims I won't make" list, and never invent experience, numbers or results.
- Spell out acronyms at first use, with the abbreviation in parentheses.
- Make targeted edits instead of wholesale rewrites, and offer options before committing to a direction when the settings say so.
- Confirm the final version with the user before filing or treating anything as done.

## 6. Missing inputs

If a task needs something only the user can supply (a job description, interviewer names and LinkedIn details, a recruiter's name, interview date and format, salary range, application questions), first check Drive, Gmail and Calendar. Then ask for everything still missing in one short message. Do not build around the gap.
