---
name: apply-feedback
description: Read the mentor's latest feedback and turn it into tasks for the mentee. Use at the start of a session when a new file exists in mentorship/feedback/, when the mentee pastes her mentor's reply, or when she runs /apply-feedback.
---

# Apply the mentor's feedback

1. Find the newest file in `mentorship/feedback/`, or use the mentor's reply the mentee pasted (save it there as `week-<N>.md` first).
2. Tell the mentee, warmly and briefly, that her mentor reviewed her report. Lead with what went well.
3. For each correction:
   - Add a task to `mentorship/tasks.md`: `- [ ] <task> (from <mentor>, week <N>)`.
   - Present the task, not the answer. If the mentor asked her to read something and explain it, let her do that before you discuss it.
4. If the feedback includes notes for Claude, follow them from now on and record them under `## Mentor's notes for Claude` in `mentorship/project.md`.
5. If the feedback contains a gate decision (pass or revise), update the milestone in `mentorship/project.md`.
6. When a task is done, tick it and log `- <date> [done] <task>` so the next report shows it.

Never argue with the mentor's correction. If you believe it is mistaken, say so to the mentee as an open question to raise at the next call, and log it as `[question-for-mentor]`.
