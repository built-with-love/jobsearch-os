---
name: prep
description: >
  This skill should be used when the user runs "/prep" or says "I have an interview",
  "prep me for my interview with", "build a prep brief", "schedule a mock interview",
  "who am I meeting", or shares an interview invite.
metadata:
  version: "0.3.0"
---

# Interview prep: brief and mock interview block

Read the `jobsearch-os-rules` skill first and load the user's settings.

## 1. Inputs

1. Find the interview on the calendar and the related emails in Gmail. Pull the date, time, format (screen, one-on-one or panel), and participant names and roles.
2. Find the company folder: job description, tailored resume and cover letter.
3. Ask for anything still missing, following section 7 of `jobsearch-os-rules` (one request per message, confirm what you found, tappable choices):
   - The interview format, if the invite doesn't say. *Choices*: Screen, One-on-one, Panel.
   - The recruiter's name, if it isn't in the emails.
   - Each interviewer's LinkedIn details, one interviewer per message: headline, current role and recent experience. Claude cannot open LinkedIn, so the user pastes them.

## 2. Prep brief

Create a Google Doc titled `Interview-Prep_[CompanyName]_[Round]` in the company folder. Include:
- The company and role in brief, and what the job description emphasizes most
- Who the user is meeting: name, role, background from the pasted details, and what they will likely care about. Mark any inferred role or focus as unconfirmed.
- Which of the user's stories fit each likely topic, using only experience from their resume, letters and stated stories
- Likely questions with short answer outlines
- Real gaps against the job description, each with honest bridging language. Never overclaim.
- Questions for the user to ask each interviewer
- Logistics: date, time, link or location, format

Share the link and ask for corrections. Apply them so the next brief improves.

## 3. Mock interview block

Create a calendar event titled `Mock interview: [CompanyName]`:
- Length from the settings (default 45 minutes for a screen or one-on-one, 60 for a panel)
- The day before the interview, or earlier the same day on short notice
- Ending at least 2 hours before the interview starts
- Put the prep brief link in the event description

Offer to run the mock interview now or at the scheduled time: ask one question at a time, push back on vague answers, and give brief feedback after each answer.

## 4. Tracker

Set the status to Interviewing and update Interview Rounds if that column exists. Read it back.
