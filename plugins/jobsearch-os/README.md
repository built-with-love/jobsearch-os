# JobSearch OS (Claude plugin)

An add-on to the article "JobSearch OS: How I run my job search with AI (and what I still do myself)" by Kevin Segedi:
https://kevinsegedi.com/articles/jobsearch-os.html

JobSearch OS runs your job search with Claude and the Google apps you already use. Claude drafts, files, tracks and prepares. You find the roles, decide, apply, interview, edit and send.

## What you need

- A Claude plan that supports plugins
- The Gmail, Google Calendar, Google Drive, Google Docs and Google Sheets connectors, connected and switched on in your chat

## Skills

| Skill | What it does |
| --- | --- |
| `/setup` | Interviews you (13 questions), saves your settings as a "JobSearch OS Settings" Google Doc, and builds your tracker Google Sheet with a Dashboard and Legend |
| `/run` | Sweeps your Gmail job label and calendar, updates the tracker in place, flags likely ghosted applications, and lists anything it couldn't classify |
| `/apply` | Archives the job description, checks fit, recommends and tailors a resume, drafts or reviews your cover letter, and updates the tracker after you apply |
| `/prep` | Builds an interview prep brief as a Google Doc and adds a mock interview block to your calendar |
| `/thanks` | Drafts one thank-you email per interviewer in Gmail and adds a 20-minute review block |
| `jobsearch-os-rules` | The standing rules every other skill follows (loads automatically) |

## Getting started

1. In Gmail, create a label for job mail and a filter that applies it (Claude can create the label, but not the filter).
2. Run `/setup` and answer the questions.
3. Run `/run` with a wide window, for example "Run, last 90 days".
4. After that, type "Run" whenever you want an update.

Your settings live in the "JobSearch OS Settings" Google Doc in your Drive year folder. Edit it any time, or run `/setup` again.

## Guardrails

- Nothing is sent, submitted, deleted or trashed without your explicit request.
- Syncs run only when you ask.
- Claude never invents experience and respects your "claims I won't make" list.

## License

CC BY-NC 4.0 (https://creativecommons.org/licenses/by-nc/4.0/). Share and adapt it with credit to Kevin Segedi, but not for commercial use. Please don't package and sell it. Job searching is hard enough.
