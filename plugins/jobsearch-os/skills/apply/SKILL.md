---
name: apply
description: >
  This skill should be used when the user runs "/apply", shares a job posting or job description,
  or says "I'm applying to", "help me apply", "write a cover letter", "review my cover letter",
  "tailor my resume", "which resume should I use", "archive this job description",
  or "answer these application questions".
metadata:
  version: "0.1.0"
---

# Apply: archive, fit, resume and cover letter

Read the `jobsearch-os-rules` skill first and load the user's settings. The user decides whether to apply and submits the application. Claude prepares.

## 1. Inputs

Collect, in one message, whatever is missing: the job description (link or pasted text), company, role, requisition ID if any, salary range if posted, whether it is a referral, and any application questions. If a link won't open, ask the user to paste the text.

## 2. Folder and archive

1. Find or create the company folder in the Drive year folder.
2. Unless the settings say to skip archiving for this case (for example referrals), save the job description as a Google Doc in the company folder, titled `JD_[CompanyName]_[Role]`.
3. Note the employer-disclosed salary if present. Use an aggregator estimate only as a labeled fallback.

## 3. Fit check

Give a short fit read against the user's target roles, level, pay floor and locations: strong matches, real gaps, and anything that conflicts with the settings. Suggest a fit score if the tracker has that column. If the fit is poor, say so plainly and let the user decide.

## 4. Resume

1. Look in the user's resume source location for niche or variant resumes. Recommend the closest one and say why, then wait for confirmation.
2. Suggest targeted changes to the summary and emphasis only. Never add claims from the user's "claims I won't make" list or anything not supported by their materials.
3. After the user approves, save the tailored resume in the company folder as both a .docx and a Google Doc, using the naming pattern from the settings.

## 5. Cover letter and answers

Ask which approach the user wants, unless they already said:
- **Claude drafts first:** draft from the job description, the user's resume and their earlier approved letters as voice examples. Follow the header and writing rules from the settings. Connect the company's mission to the user's values. Get straight to why the user is qualified; do not tell the company what it already knows about itself. Vary how experience is introduced.
- **User drafts first:** review for grammar, tangled or ambiguous sentences, tone risks, gaps against the job description and mismatches with the application form. Suggest targeted fixes, line by line.

Draft application question answers the same way. Confirm the final version, then save the cover letter as a Google Doc named per the settings in the company folder.

## 6. Track

After the user says they have applied, add or update the tracker row (Date Applied, Status Applied, Source, Cover Letter, JD Archive link, Salary Range and any other chosen columns). Read it back to confirm.
