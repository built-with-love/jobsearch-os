---
name: setup
description: >
  This skill should be used when the user runs "/setup", says "set up JobSearch OS",
  "configure my job search", "start my job search setup", "build my job tracker",
  or wants to create or change their JobSearch OS settings, tracker sheet or Drive folders.
metadata:
  version: "0.2.0"
---

# Set up JobSearch OS

Interview the user, save their settings, and build the tracker. Read the `jobsearch-os-rules` skill first for the standing rules.

**One request per message.** Every question and every request in this skill goes in its own message. Ask it, wait for the answer, then move on. Never bundle two questions, even closely related ones. Show progress as "Question 4 of 30" so the user knows how far along they are. Tell the user at the start that they can answer "default" to take the suggested answer or "skip" to come back to it later.

## Before starting

1. Check that the Gmail, Google Calendar, Google Drive, Google Docs and Google Sheets connectors are available. If any are missing, list them, tell the user to connect them in Claude's connector settings and switch them on for this chat, and stop.
2. Search Drive for an existing `JobSearch OS Settings` doc. If one exists, read it and ask whether the user wants to update it or start over.
3. Ask whether the user has already created a Gmail label for job mail. If not, explain that Claude can create the label, but the Gmail filter that applies it has to be made in Gmail by the user (Settings, then Filters, or the sliders icon in the search bar).
4. In a separate message, ask whether the user has already created a Drive folder for the year. If not, offer to create it with `Rejected` and `Inactive` subfolders.

## Interview

Ask these one at a time, in this order. If an answer is unclear, ask a single follow-up before moving on. If the user is unsure, suggest the default shown and say it can change later.

About the search
1. What's your name?
2. Which roles are you targeting?
3. What level or seniority?
4. Which locations, or do you want remote only?
5. What is your pay floor?

Contact and links
6. Which email address or alias do you use for applications?
7. Do you have a portfolio link? (Default: none)
8. What is your LinkedIn URL?
9. What is your Gmail label for job mail called?

Tracking
10. Which statuses will you track? (Default: Applied, Interviewing, Interviewed, Offer, Rejected, Inactive, Withdrew)
11. How many days of silence before an application counts as ghosted? (Default: 60)

Then state, without asking, that syncs run only when the user says "Run".

Writing
12. Please share two or three samples of your writing, such as a cover letter or email you were happy with.
13. Which words or phrases should I never use?
14. What should your cover letter header include?
15. How do you want resume files named? (Default: Resume_[YourName]_[CompanyName])
16. How do you want cover letter files named? (Default: Cover-Letter_[CompanyName])
17. Which claims can you back with evidence?
18. Which claims will you never make?

Source material
19. Where do your resume versions live?
20. Where do your stories and portfolio live?
21. What is your Drive year folder ID? (Offer to look it up by name.)

Interviews
22. Which interview rounds get a mock interview? (Default: all of them)
23. How long should a mock interview be for a screen or one-on-one? (Default: 45 minutes)
24. How long for a panel? (Default: 60 minutes)
25. What should prep briefs draw on? (Default: resume, cover letter, job description and the interviewer details you paste)
26. Who gets a thank-you email? (Default: everyone you met)
27. When do you want to review the thank-you drafts? (Default: the next morning, or that evening if the interview was early in the day)

Approvals and working style
28. What must I never do without asking? (Default: send email, submit applications, delete files)
29. Do you prefer targeted edits or full rewrites? (Default: targeted edits)
30. Should I offer options before committing to a direction? (Default: yes)

Every job description is archived, including referrals. Do not ask about skipping the archive.

## Save the settings

1. Write the answers in the layout from `../jobsearch-os-rules/references/settings-template.md`, leaving the tracker Sheet ID as a placeholder. Fill skipped answers with the default and mark them "(default)".
2. Show the full text and ask for changes. Apply only the changes asked for.
3. Once confirmed, create a Google Doc titled `JobSearch OS Settings` in the Drive year folder with that text. Give the user the link.
4. If the user works inside a Claude Project, suggest pasting the same text into the Project instructions so every chat loads it.

## Build the tracker

1. Explain that the tracker always includes the core columns from `references/tracker-spec.md`, including Referral Contact.
2. Offer the optional columns one at a time, each as its own yes-or-no question, in the order listed in the spec. Before the first one, tell the user they can answer "all" or "none" to settle the rest at once.
3. Create a Google Sheet named `[Year]_Job_Applications` in the year folder with three tabs. Follow `references/tracker-spec.md`.
4. Read the sheet back and confirm the Dashboard formulas calculate.
5. Write the new Sheet ID into the settings doc, replacing the placeholder, and read it back.
6. Tell the user setup is done and suggest a first sync: "Run, last 90 days."
