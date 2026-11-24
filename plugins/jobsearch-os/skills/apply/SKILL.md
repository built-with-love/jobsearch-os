---
name: apply
description: >
  This skill should be used when the user runs "/apply", shares a job posting or job description,
  or says "I'm applying to", "help me apply", "write a cover letter", "review my cover letter",
  "tailor my resume", "which resume should I use", "archive this job description",
  "I got a referral", or "answer these application questions".
metadata:
  version: "0.2.0"
---

# Apply: archive, fit, resume and cover letter

Read the `jobsearch-os-rules` skill first and load the user's settings. The user decides whether to apply and submits the application. Claude prepares.

**One request per message.** Ask for each missing input in its own message, wait for the answer, then ask for the next. Never bundle two requests.

## 1. Inputs

Work out what the user already gave. Then ask only for what is missing, one item at a time, in this order:

1. The job description, as a link or pasted text. If a link won't open, ask the user to paste the text.
2. The company, if the job description doesn't make it clear.
3. The role title, if the job description doesn't make it clear.
4. The requisition ID, if the posting has one. Accept "none".
5. Whether this is a referral.
6. If it is a referral, the referrer's name.
7. If it is a referral, the referrer's contact details: email, phone or LinkedIn URL. Accept whatever the user has.
8. Any application questions the form asks. Accept "none".

Take the salary range from the posting. Ask for it separately only if the posting has none and the tracker has a Salary Range column, and accept "unknown".

## 2. Folder and archive

1. Find or create the company folder in the Drive year folder.
2. Save the job description as a Google Doc in the company folder, titled `JD_[CompanyName]_[Role]`. Archive it for every application, referrals included.
3. Note the employer-disclosed salary if present. Use an aggregator estimate only as a labeled fallback.

## 3. Fit check

Give a short fit read against the user's target roles, level, pay floor and locations: strong matches, real gaps, and anything that conflicts with the settings. Suggest a fit score if the tracker has that column. If the fit is poor, say so plainly and let the user decide.

## 4. Resume

1. Look in the user's resume source location for niche or variant resumes. Recommend the closest one and say why, then wait for confirmation.
2. Suggest targeted changes to the summary and emphasis only. Never add claims from the user's "claims I won't make" list or anything not supported by their materials.
3. After the user approves, save the tailored resume in the company folder as both a .docx and a Google Doc, using the naming pattern from the settings.

## 5. Cover letter and answers

Ask which approach the user wants, unless they already said:
- **Claude drafts first:** draft from the job description, the user's resume and their earlier approved letters as voice examples. Follow the header and writing rules from the settings. Connect the company's mission to the user's values. Get straight to why the user is qualified; do not tell the company what it already knows about itself. Vary how experience is introduced. For a referral, mention the referrer by name in the opening only if the user agrees.
- **User drafts first:** review for grammar, tangled or ambiguous sentences, tone risks, gaps against the job description and mismatches with the application form. Suggest targeted fixes, line by line.

Draft application question answers the same way, one question at a time. Confirm the final version, then save the cover letter as a Google Doc named per the settings in the company folder.

## 6. Track

After the user says they have applied, add or update the tracker row: Date Applied, Status Applied, Source, Cover Letter, JD Archive link, Salary Range and any other chosen columns. For a referral, set Source to Referral and fill Referral Contact with the referrer's name and contact details, for example `Jane Doe, jane@example.com`. If the tracker has no Referral Contact column, follow "Adding Referral Contact to an older tracker" in `../setup/references/tracker-spec.md`. Read the row back to confirm.
