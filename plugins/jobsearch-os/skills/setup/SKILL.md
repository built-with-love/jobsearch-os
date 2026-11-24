---
name: setup
description: >
  This skill should be used when the user runs "/setup", says "set up JobSearch OS",
  "configure my job search", "start my job search setup", "build my job tracker",
  or wants to create or change their JobSearch OS settings, tracker sheet or Drive folders.
metadata:
  version: "0.3.0"
---

# Set up JobSearch OS

Interview the user, save their settings, and build the tracker. Read the `jobsearch-os-rules` skill first for the standing rules, including "How to ask" in section 7.

## How this interview works

- **One request per message.** Ask one thing, wait for the answer, then move on. Never bundle two questions.
- **Pre-fill first, then confirm.** Before asking a field marked *Look up* below, search the user's connected accounts for the answer. If you find it, ask the user to confirm it ("I found the Gmail label `Jobs`. Use it?") instead of asking them to type it. If you find several candidates, offer them as choices. If you find nothing, ask the question normally.
- **Tappable choices with a recommended default.** For a field marked *Choices*, offer two to four options with the recommended one first and labeled "(Recommended)". Use the client's multiple-choice question tool when one is available; otherwise list the options as a short numbered list. The user can always tap an option or type their own answer.
- **A short running tally.** After each answer, show one compact line of progress, for example: `Captured 9 of 30: name, roles, level, locations, pay floor, email, portfolio, LinkedIn, Gmail label. Next: statuses.` Keep it to one or two lines.
- **Take extra answers when given.** If the user answers more than one field at once, record every field they answered, show them in the tally, and skip those questions. Never re-ask something already answered.
- **"default" and "skip".** Tell the user at the start that "default" takes the recommended answer and "skip" leaves a field for later.

## Before starting

1. Check that the Gmail, Google Calendar, Google Drive, Google Docs and Google Sheets connectors are available. If any are missing, list them, tell the user to connect them in Claude's connector settings and switch them on for this chat, and stop.
2. Search Drive for an existing `JobSearch OS Settings` doc. If one exists, read it and ask whether the user wants to update it or start over (*Choices*: Update my settings (Recommended), Start over).
3. Look up the user's Gmail labels. If one looks like a job label (for example contains "job"), ask the user to confirm it. If none exists, explain that Claude can create the label, but the Gmail filter that applies it has to be made in Gmail by the user (Settings, then Filters, or the sliders icon in the search bar), and offer to create the label.
4. In a separate message, look up Drive folders named for the current year. If one fits, ask the user to confirm it. If none exists, offer to create it with `Rejected` and `Inactive` subfolders.

Answers confirmed here count toward the tally (Gmail label and Drive year folder ID).

## Interview

Ask these one at a time, in this order, skipping any field already captured.

About the search
1. Name. *Look up*: the display name on the user's Google account or sent mail.
2. Target roles. *Look up*: role titles in a resume found in Drive; offer them to confirm or edit.
3. Level or seniority. *Choices*, built from the resume and target roles, for example: Senior, Staff or principal, Director, Other.
4. Locations. *Choices*: Remote only (Recommended if the resume or past applications suggest it), Remote or a named metro, On-site in a named metro, Other.
5. Pay floor. Ask plainly; never guess a number.

Contact and links
6. Email address or alias for applications. *Look up*: the address recent job applications were sent from or to.
7. Portfolio link. *Look up*: links in the user's email signature or resume. If none, *Choices*: No portfolio (Recommended), Add a link.
8. LinkedIn URL. *Look up*: the email signature or resume.
9. Gmail label for job mail. Already confirmed in "Before starting" unless skipped.

Tracking
10. Statuses to track. *Choices*: Applied, Interviewing, Interviewed, Offer, Rejected, Inactive, Withdrew (Recommended); a shorter set of Applied, Interviewing, Offer, Rejected; Custom.
11. Ghosted window. *Choices*: 60 days (Recommended), 30 days, 45 days, 90 days.

Then state, without asking, that syncs run only when the user says "Run".

Writing
12. Writing samples. *Look up*: cover letters in Drive (titles containing "cover letter" or "Cover-Letter"). Offer the two or three most recent to confirm, or ask the user to share some.
13. Words and phrases to avoid. Ask plainly, and offer common ones as suggestions the user can accept: em dashes, "I'd welcome", "passionate", "leverage".
14. Cover letter header. *Choices*: Name, title and links on the left with phone and email on the right (Recommended); Centered name with one contact line; Match my existing letters (shown only if letters were found).
15. Resume file naming. *Choices*: Resume_[YourName]_[CompanyName] (Recommended), [CompanyName]_Resume, Custom.
16. Cover letter file naming. *Choices*: Cover-Letter_[CompanyName] (Recommended), [CompanyName]_Cover-Letter, Custom.
17. Claims you can back with evidence. Ask plainly; offer achievements found in the resume as a starting list to confirm.
18. Claims you will never make. Ask plainly; never pre-fill this one.

Source material
19. Where resume versions live. *Look up*: Drive files with "resume" in the title; confirm the folder.
20. Where stories and portfolio live. *Look up*: Drive docs with "stories", "STAR", "portfolio" or "case study" in the title; confirm or ask.
21. Drive year folder ID. Already confirmed in "Before starting" unless skipped.

Interviews
22. Which rounds get a mock interview. *Choices*: All rounds (Recommended), Panels and final rounds only, None.
23. Mock length for a screen or one-on-one. *Choices*: 45 minutes (Recommended), 30 minutes, 60 minutes.
24. Mock length for a panel. *Choices*: 60 minutes (Recommended), 45 minutes, 90 minutes.
25. What prep briefs draw on. *Choices*: Resume, cover letter, job description and pasted interviewer details (Recommended); Add company news and earnings; Custom.
26. Who gets a thank-you email. *Choices*: Everyone I met (Recommended), Only the hiring manager, Ask me each time.
27. When to review thank-you drafts. *Choices*: Next morning, or that evening if the interview was early (Recommended); Same evening; Next morning only.

Approvals and working style
28. What Claude must never do without asking. *Choices*: Send email, submit applications, delete files (Recommended); the same plus calendar changes; Custom.
29. Edits. *Choices*: Targeted edits (Recommended), Full rewrites, Ask me each time.
30. Options first. *Choices*: Yes, offer options before committing (Recommended), No, just pick the best.

Every job description is archived, including referrals. Do not ask about skipping the archive.

## Save the settings

1. Write the answers in the layout from `../jobsearch-os-rules/references/settings-template.md`, leaving the tracker Sheet ID as a placeholder. Fill skipped answers with the recommended default and mark them "(default)".
2. Show the full text and ask for changes. Apply only the changes asked for.
3. Once confirmed, create a Google Doc titled `JobSearch OS Settings` in the Drive year folder with that text. Give the user the link.
4. If the user works inside a Claude Project, suggest pasting the same text into the Project instructions so every chat loads it.

## Build the tracker

1. Explain that the tracker always includes the core columns from `references/tracker-spec.md`, including Referral Contact.
2. Offer the optional columns one at a time, each as a tappable Yes or No question, in the order listed in the spec. Before the first one, tell the user they can answer "all" or "none" to settle the rest at once. Keep the running tally for this part too.
3. Create a Google Sheet named `[Year]_Job_Applications` in the year folder with three tabs. Follow `references/tracker-spec.md`.
4. Read the sheet back and confirm the Dashboard formulas calculate.
5. Write the new Sheet ID into the settings doc, replacing the placeholder, and read it back.
6. Tell the user setup is done and suggest a first sync: "Run, last 90 days."
