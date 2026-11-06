# HerShot

**Frontier AI research mentorship, built with Claude.**

*Courses teach what's known. We teach how to find out what isn't.*

Experienced AI researchers are few and busy. Most people who want to do research never sit next to one. HerShot is a Claude Code plugin that lets a mentor guide a mentee through a real research cycle (reproduce a recent paper, extend it, submit to a workshop) in about 45 minutes every two weeks.

Claude does not replace the mentor. It mediates:

- **`/select-project`** checks what the mentee's computer can run, asks about her experience, and recommends a project and mentor from the catalog. Projects are matched to what her computer can run; every project comes with the same mentorship.
- **While the mentee works**, Claude helps with code and setup, asks her to explain ideas in her own words, and logs what she understands and where she's mistaken.
- **`/share-progress`** turns that into a one-page report about the mentee, plus *suggested feedback* for the mentor, and emails both to the mentor after the mentee approves.
- **The mentor** reads for five minutes, edits the suggested feedback, adds what only an expert would catch, and sends it back.
- **`/apply-feedback`** turns the mentor's corrections into tasks for the mentee's next session.
- **`/novelty-check`** searches prior work before the mentee claims an idea is new. The mentor decides.

The plugin also encodes the **hidden curriculum** of research: the unwritten rules most people only learn from a mentor. A better number isn't a new idea. "First" needs a search for counterexamples. Pretty pictures aren't evidence. Reproduce before you extend, and use your reproduction as the baseline.

## Install

From Claude Code:

```
/plugin marketplace add drlynetchapmi/hershot
/plugin install hershot@hershot-marketplace
```

Or load it locally for one session:

```
claude --plugin-dir ./hershot
```

## Set up a project

In an empty project folder, run `/select-project`; it creates `mentorship/project.md`. Or create it by hand from `examples/project.md`. Mentors add projects to `skills/select-project/catalog.md`. To email reports, connect a Gmail connector; without one, `/share-progress` saves the files for the mentee to send.

## Files it keeps

```
mentorship/
  project.md        paper, milestone, week, mentor's name and email, mentor's notes for Claude
  log.md            what the mentee understands, misconceptions, questions, progress
  tasks.md          tasks from the mentor
  reports/          weekly reports and suggested mentor feedback
  feedback/         the mentor's edited feedback
```

All code and data stay on the mentee's machine. Only the reports she approves are shared.
