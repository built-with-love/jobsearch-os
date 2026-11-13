---
name: setup
description: >
  This skill should be used when the user runs "/setup", says "set up JobSearch OS",
  "configure my job search", "start my job search setup", "build my job tracker",
  or wants to create or change their JobSearch OS settings, tracker sheet or Drive folders.
metadata:
  version: "0.1.0"
---

# Set up JobSearch OS

Interview the user, save their settings, and build the tracker. Read the `jobsearch-os-rules` skill first for the standing rules.

## Before starting

1. Check that the Gmail, Google Calendar, Google Drive, Google Docs and Google Sheets connectors are available. If any are missing, list them, tell the user to connect them in Claude's connector settings and switch them on for this chat, and stop.
2. Search Drive for an existing `JobSearch OS Settings` doc. If one exists, read it and ask whether the user wants to update it or start over.
3. Ask whether the user has already created a Gmail label for job mail and a Drive folder for the year. If not, explain briefly that Claude can create the label, but the Gmail filter that applies it has to be made in Gmail by the user (Settings, Filters, or the search-bar sliders icon). Offer to create the Drive year folder with `Rejected` and `Inactive` subfolders.

## Interview

Ask one question at a time and wait for the answer. If an answer is unclear, ask a follow-up. If the user is unsure, suggest a sensible default and say it can change later. Cover these thirteen areas:

1. Name, target roles, level, and locations or remote preference
2. Pay floor
3. Search email or alias, portfolio and LinkedIn links, and the Gmail label name
4. Statuses to track (suggest Applied, Interviewing, Interviewed, Offer, Rejected, Inactive, Withdrew)
5. How often they want a refresh, and whether saying "Run" each time works for them
6. Days of silence before an application counts as ghosted (suggest 60)
7. How they write: two or three samples, words and phrases to avoid, cover letter header, and resume and cover letter naming
8. Claims they can back with evidence, and claims they will never make
9. Where their resume, stories and portfolio live, plus the Drive year folder ID (offer to look it up by name)
10. Whether to archive every job description, and whether referrals get the same treatment
11. Which interview rounds get a mock interview and for how long (suggest 45 minutes for a screen, 60 for a panel), and what prep briefs should draw on
12. Who gets a thank-you email, and when they want to review the drafts
13. What Claude must never do without asking, what to ask for instead of guessing, and how they like to work (targeted edits or rewrites, options first or not)

## Save the settings

1. Write the answers in the layout from `../jobsearch-os-rules/references/settings-template.md`, leaving the tracker Sheet ID as a placeholder.
2. Show the full text and ask for changes. Apply only the changes asked for.
3. Once confirmed, create a Google Doc titled `JobSearch OS Settings` in the Drive year folder with that text. Give the user the link.
4. If the user works inside a Claude Project, suggest pasting the same text into the Project instructions so every chat loads it.

## Build the tracker

1. Ask which optional columns they want: Has Extra Info and Extra Info Notes, Cover Letter, Interview Rounds, Multiple Roles, Salary Range, JD Archive, Contact Name(s) and Contact Email(s), Referral Source, Fit Score.
2. Create a Google Sheet named `[Year]_Job_Applications` in the year folder with three tabs. Follow `references/tracker-spec.md`.
3. Read the sheet back and confirm the Dashboard formulas calculate.
4. Write the new Sheet ID into the settings doc, replacing the placeholder, and read it back.
5. Tell the user setup is done and suggest a first sync: "Run, last 90 days."
