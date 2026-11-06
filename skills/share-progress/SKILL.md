---
name: share-progress
description: Draft the mentee's one-page progress report and the mentor's suggested feedback from this week's work, show them to the mentee for approval, then email them to the mentor. Use when the mentee runs /share-progress or asks to send an update to her mentor.
---

# Share progress with the mentor

The mentee approves everything before it leaves her machine. Never send without her explicit yes.

## Step 1: Gather

- `mentorship/project.md`: mentee's name, paper, current milestone, week number, mentor's name and email.
- `mentorship/log.md`: entries since the last report (understanding, misconceptions, questions, done, stuck).
- `mentorship/tasks.md`: tasks from the mentor and their status.
- Results files the mentee produced this week (figures, metrics), if any.

If `project.md` has no mentee name or no mentor email, ask the mentee for what's missing and save it there.

## Step 2: Draft the progress report

Fill `progress-report.md` (in this skill's folder) and save it as `mentorship/reports/week-<N>.md`.

- Focus on the **mentee**: what she did, what she understands in her own words, and where her understanding differs from the paper.
- "What I understand" must stay close to the mentee's own words from the log. Never polish it into your own explanation.
- Misconceptions come in two kinds. Corrected ones (`[misconception-corrected]` in the log): what she believed, what she now understands, and the probe question for the mentor. Open ones (`[misconception-open]`): what she believes and what the paper says. Only include items supported by the log.
- One page. Numbers over adjectives.

## Step 3: Draft suggested feedback for the mentor

Fill `mentor-feedback.md` (in this skill's folder) and save it as `mentorship/reports/week-<N>-suggested-feedback.md`. This is a **draft for the mentor**, who will edit it.

- For each corrected misconception: the probe question to ask on the call, so the mentor can verify the correction stuck.
- For each open misconception: the correction you suggest, and a small task that would let the mentee discover it herself (a section to read, a one-sentence explanation to write, a quick experiment).
- What went well: one or two specific things worth praising.
- Focus next: tied to the milestone and the upcoming hidden-curriculum gate.
- Mark anything you are unsure of with "(Claude unsure: please check)". The mentor's expertise is the point; never present your suggestions as settled.

## Step 4: Mentee review

Show the mentee the report. Ask: "Anything you want to change or keep private before this goes to <mentor name>?" Apply her edits. The suggested-feedback draft goes to the mentor only; tell the mentee it exists and what it covers, in one sentence.

## Step 5: Send

Only after the mentee says yes:

1. If an email tool is available (for example a Gmail connector), send one email to the mentor:
   - Subject: `Progress report: <mentee name>, week <N>`
   - Body: the full report, then a divider, then the suggested feedback under the heading "Suggested feedback (draft by Claude, edit before sending back)".
   - Closing line: "Reply with your edited feedback, or save it as mentorship/feedback/week-<N>.md in the project."
   If the tool supports drafts, and the mentee prefers to review the email itself, create a draft instead and tell her where it is.
2. If no email tool is available, say so plainly, then give the mentee the two files to attach or paste into a shared doc.

Then log `- <date> [sent] week-<N> report to <mentor>` in `mentorship/log.md`.
