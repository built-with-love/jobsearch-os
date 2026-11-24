# Tracker specification

## Applications tab

Core columns, always included, in this order:
Company, Role, Date Applied, Status, Rejected?, Source, Referral Contact, Notes, Status Date, Days to Status

- Date Applied and Status Date are dates.
- Days to Status is a formula (Status Date minus Date Applied) formatted as a plain number.
- Source is Referral or Portal (or the job board name).
- Referral Contact holds the referrer's name and contact details (email, phone or LinkedIn URL), for example `Jane Doe, jane@example.com`. Leave it blank for non-referral applications.
- Add the optional columns the user chose after the core columns.

Optional columns, offered one at a time in this order:
- Has Extra Info, Extra Info Notes: flags confirmation emails with extra details, such as a nondisclosure agreement (NDA) request or a description of the interview process
- Cover Letter: whether one was written
- Interview Rounds: number of rounds so far
- Multiple Roles: marks companies with more than one application
- Salary Range: employer-disclosed first; an aggregator estimate only as a labeled fallback
- JD Archive: link to the archived job description Google Doc
- Contact Name(s), Contact Email(s): recruiters and hiring contacts at the company
- Referral Source: how the referral came about, for example former colleague or alumni network
- Fit Score: 1 High to 3 Low

## Dashboard tab

Live formulas (no pasted values):
- Total applications, active, rejected
- A status breakdown with a count and percentage for every status in the settings
- Referral applications (rows where Source is Referral) and their response rate
- Response rate (applications with any reply / total) and rejection rate
- Count of stale applications with no response past the ghosted window
- Counts for chosen optional columns, such as cover letters written and total interview rounds

## Legend tab

A color key with one color per status in the settings. Suggested: pink or red for Rejected, blue for Interviewed, green for Interviewing, light gray or white for Applied. Apply the colors to rows by status with conditional formatting.

## Adding Referral Contact to an older tracker

Trackers built before version 0.2.0 may not have the Referral Contact column. When a referral needs recording and the column is missing, ask the user once whether to add it. If they agree, insert it after Source, move no other data, read the sheet back, and confirm the Dashboard still calculates.
