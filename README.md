# Job Hunt Assistant (a skill for Claude)

A Claude skill that runs your job search the boring parts for you: it finds and ranks new roles, tailors your resume honestly, writes cover letters and messages that sound like you, fills application forms in your own Chrome, keeps a tracker spreadsheet, and prepares you for interviews.

**You stay in control.** The assistant fills a form and stops at the Review page. It never submits without your explicit "yes", never creates accounts, never logs in for you, and never guesses answers you have not given.

## What it does

- **Collects** roles from job boards in your signed-in Chrome (LinkedIn, Naukri, Indeed, Himalayas, IIMJobs, or any you list) and from your job-alert emails.
- **Filters and ranks** against your profile, with a rough match % and honest labels: *Verified* (posted within 48 hours) or *Lead*, and *Pay shown* or *Pay not shown*.
- **Tailors your resume** without inventing anything: it re-orders and re-words, it never adds skills, tools or numbers you do not have.
- **Writes** a cover letter, a LinkedIn message and a cold email per role, using a built-in humaniser so they do not read like generated text.
- **Fills applications** (LinkedIn Easy Apply and company forms) up to the final Submit.
- **Tracks everything** in `job-hunt-tracker.xlsx`: links, status, follow-up dates, a summary tab.
- **Watches your inbox** for recruiter replies and updates the tracker.
- **Builds interview prep** when a role reaches the interview stage, and can run a one-question-at-a-time mock interview with feedback.

## Requirements

- Claude with skills enabled.
- The **Claude in Chrome** extension, signed in to the job sites you want to use (the assistant never logs in for you).
- A **Gmail** (or other mail) connector, if you want alert-email reading and email drafts.
- Optional: Claude's spreadsheet (xlsx) skill for editing the tracker.

## Install

1. Download this repository.
2. Zip the `job-hunt-assistant` folder (or use the packaged `.skill` file if you have one) and add it in Claude under **Settings, Skills**.
3. Start a chat and say: **"Run my job sweep."** On first use it asks for your resume and preferences, builds `references/profile.md`, and shows it to you. Save that file into your own copy of the skill, because files do not persist between chats.

## Example prompts

- "Run my job sweep."
- "Find remote product marketing roles posted this week and tailor my resume for the top two."
- "Check my inbox for recruiter replies and update my tracker."
- "I got an interview at <company>. Build my prep guide."
- "Weekly summary."

## Files

| Path | Purpose |
|---|---|
| `job-hunt-assistant/SKILL.md` | The workflow and the hard rules |
| `job-hunt-assistant/references/profile.example.md` | Template for your profile (copy to `profile.md`) |
| `job-hunt-assistant/references/humaniser.md` | Writing rules for everything it drafts |
| `job-hunt-assistant/references/interview-prep.md` | Interview prep guide format |
| `job-hunt-assistant/references/browser-notes.md` | Notes on driving job sites through Chrome |
| `job-hunt-assistant/assets/tracker-template.xlsx` | Empty tracker spreadsheet |

## What has been tested

Tested end to end by the author on: LinkedIn (search, notifications, Easy Apply form up to Review), one external employer application form (first page), a remote-jobs board's public listing pages, and Gmail alert emails, reply detection and drafts. Naukri and IIMJobs are supported through their alert emails and through Chrome only when you are signed in; the Chrome flow for those two is not yet tested. Treat other sites as untested, and expect to adjust `browser-notes.md` as sites change.

## Known limits

- It does not run on a schedule by itself; you start it. (Scheduling depends on what your Claude setup offers.)
- Chrome file uploads from Claude's side are not supported, so you attach your resume on application forms yourself.
- Pop-ups can be blocked; you may need to click "Apply on company website" and allow the pop-up.
- Many listings do not show pay or full eligibility, and the assistant says so instead of guessing.
- Job sites change often. If a step breaks, the assistant stops and asks instead of retrying blindly.

## Privacy

Your profile, resume and tracker contain personal data. This repository's `.gitignore` excludes `profile.md`, trackers and resume files. Do not commit them. The assistant never stores passwords, OTPs, card numbers or ID numbers.

## Responsible use

Automated applying can conflict with some sites' terms. This skill is built around a human approving every submission; keep it that way. Read and edit everything you send, and follow any employer rules on AI use in applications. This project is not affiliated with or endorsed by LinkedIn, Naukri, Indeed, Himalayas, IIMJobs or Anthropic.

## Contributing

Issues and pull requests are welcome, especially: notes for more job sites and countries, better filters, and fixes when a site changes. Please never include real personal data in examples.

## License

MIT. See `LICENSE`.
