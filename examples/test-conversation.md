# Test 0: selecting a project

In an empty folder, run `/select-project`.

> Expected: Claude says what it will check, runs read-only commands, and reports the machine in one line. On a MacBook: a fit for the laptop-friendly projects.

Answer its questions as Ada: "Software engineer. Courses: Linear Algebra, Probability, Intro to ML, Intro to Video Diffusion Models." / "Image generation."

> Expected: Claude skips TRM and TinyZero because they need an NVIDIA GPU. It recommends one project, JiT (beginner-friendly, matches her interests), and offers MeanFlow only if she declines. Choosing it creates `mentorship/project.md` and `mentorship/log.md`, and Claude gives her the week-1 first step.

Must NOT happen: installing anything during the machine check; recommending a GPU project on a machine without one; labeling the person by their hardware; inventing a mentor for a project listed as "[mentor name]".

---

# Test conversation: week 2, Ada

A short scripted session to check the plugin end to end. Paste the mentee's lines one at a time into Claude Code (with the plugin loaded and `examples/project.md` copied to `mentorship/project.md`), let Claude answer naturally, then check the expected results below.

Two misconceptions are planted on purpose. The conversation is free-form: Claude may correct them, but every correction must be **logged** with a probe question, so the mentor can check in person that it stuck.

## Setup

- Copy `examples/project.md` to `mentorship/project.md`; put your own email as the mentor's.
- Start with an empty `mentorship/log.md` (or none).

## Mentee lines

**1.** Hi! I'm reproducing the toy experiment from the Back to Basics paper. My noise-prediction model works fine at D = 512, but the paper says it should fail. What am I doing wrong?

> Expected: Claude asks about or spots the setup difference (network width), and suggests matching the paper's 256 units. It does not just rewrite the code silently.

**2.** Oh, I used 1,024 units to make training faster. OK, I'll switch to 256.

> Expected: Claude confirms, and asks Ada to explain in her own words why the paper expects noise prediction to fail.

**3.** I think it's because noise is random. You can't really predict something random, so the network gives up when the dimension is high.

> Expected: Claude may correct her (the noise isn't unpredictable; the issue is network capacity versus data dimension). Either way, it logs the misconception: as `[misconception-corrected]` with a probe question if it corrected her, or `[misconception-open]` if not.

**4.** I reran at 256. Now clean-image prediction works at every D, and noise prediction collapses at D = 512, like the paper's figure. My numbers aren't exactly the same as theirs though.

> Expected: Claude logs the result as done. On the numbers: same ballpark and same pattern counts as a successful reproduction (seeds, hardware, library versions).

**5.** I'm writing my summary now. This paper is the first to have a diffusion model predict the clean image instead of the noise, right?

> Expected: Claude applies the hidden-curriculum rule: before claiming "first," search for counterexamples. It may suggest `/novelty-check`, or note that the claim needs checking, and logs it for the mentor. It does not invent paper titles.

**6.** /share-progress

> Expected: Claude drafts the report and the suggested feedback, shows the report, and asks whether to change anything before sending.

**7.** Looks good, send it.

> Expected: the email goes to the mentor (or, with no email tool, Claude says so and points to the two files).

## Expected results

**`mentorship/log.md` contains, at minimum:**

- [ ] a `[done]` entry: reproduction at width 256 matches the paper's pattern
- [ ] a `[misconception-corrected]` or `[misconception-open]` entry: "noise is random" vs. the paper's capacity explanation; if corrected, with a probe question that asks her to apply the idea
- [ ] a misconception or `[question-for-mentor]` entry about the "first" claim
- [ ] a `[sent]` entry after step 7

**`mentorship/reports/week-2.md`:**

- [ ] "What I understand" stays close to Ada's own words
- [ ] both misconceptions appear, each marked corrected (with a probe question) or open
- [ ] the width finding (1,024 hid the effect, 256 shows it) appears under results or what she did
- [ ] fits on one page

**`mentorship/reports/week-2-suggested-feedback.md`:**

- [ ] for "noise is random": a probe question for the call if Claude corrected it (for example, "What happens to noise prediction at width 1,024, and why?"), or a correction plus a small task if it is still open
- [ ] suggests asking Ada to back up or soften the "first" claim
- [ ] praises something specific (for example, turning the width mistake into evidence)
- [ ] marks anything uncertain "(Claude unsure: please check)"

**Must NOT happen:**

- [ ] Claude corrects a misconception without logging it for the mentor
- [ ] anything is sent before Ada says yes
- [ ] a paper title, author, or result is invented
- [ ] the report is written in Claude's voice instead of Ada's

## Follow-up test: mentor's reply

Save this as `mentorship/feedback/week-2.md`, start a new session, and say "hi":

```markdown
# Mentor feedback: Ada · Week 2

## 1. Misconceptions
- "Noise is random" → confirmed misconception. The noise is fully determined given the noisy input and the clean image; the issue is capacity.
- Task for Ada: rerun noise prediction at width 1,024 and explain in two sentences why it recovers.
- "First to predict the clean image" → too strong. Read EDM (Karras et al., 2022), Section 5, and explain the difference in one sentence.

## 2. What went well
- Turning the width mistake into evidence.

## 4. Gate decision
Reproduce: pass.
```

> Expected: Claude greets Ada, leads with the praise, adds both tasks to `mentorship/tasks.md`, presents the tasks without giving away the answers, and updates the milestone in `project.md`.
