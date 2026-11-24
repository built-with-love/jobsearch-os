---
name: thanks
description: >
  This skill should be used when the user runs "/thanks" or says "my interview is done",
  "I just finished my interview", "draft thank-you emails", "write thank-you notes",
  or "follow up with the interviewers".
metadata:
  version: "0.2.0"
---

# After the interview: thank-you drafts and a review block

Read the `jobsearch-os-rules` skill first and load the user's settings. Claude drafts. The user edits and sends. Never send.

## 1. Inputs

1. Find the interview on the calendar. Take participant names and roles from the invite.
2. Find participant email addresses in the invite or related emails. If they are missing or hidden, plan to address that note to the recruiter with a line asking them to forward it, and say so.
3. Ask about one participant per message: one or two specifics from that conversation (a topic discussed, a question asked, something to reinforce). Wait for the answer before asking about the next person. If the user has nothing to add for someone, draft that note from the prep brief and job description and say it will be more generic.

## 2. Drafts

Create one Gmail draft per participant, sent from the user's search address:
- Subject: `Thank you, [Role] interview` or similar, short
- Body: 90 to 150 words. Thank them by name, reference the specific point from that conversation, connect it to one strength relevant to the role, and close with interest in next steps.
- Follow the user's writing rules and banned words. No claims from the "claims I won't make" list.
- Vary each note so no two read the same.

## 3. Review block

Create a 20-minute calendar event titled `Review thank-you drafts: [CompanyName]`:
- The next morning by default
- That evening instead if the interview ended before noon
- Use the user's timing rule from the settings if it differs

## 4. Tracker and report

1. Set the row to Interviewed and update Interview Rounds if that column exists. Read it back.
2. Tell the user how many drafts were created, for whom, and when the review block is. Remind them to check the From address and send each draft themselves.
