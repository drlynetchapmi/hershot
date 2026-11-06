---
name: select-project
description: Help a new mentee choose a research project and mentor. Checks what her computer can run, asks about her background and interests, and recommends a project from the catalog. Use when the mentee runs /select-project, is starting the program, or asks which project or paper to work on.
---

# Select a project

## Style rules (strict)

- Every chat reply is **3 lines or fewer**. No headings, no tables, no notes to the plugin author.
- **One step per turn.** Ask, then stop and wait for the mentee's answer.
- Warm and plain. Talk about what the computer can run, never about the person's means. Every project comes with the same mentorship.

## Turn 1: Ask to check the computer

Say, in your own words, in at most 3 lines: welcome to HerShot, you'll check what her computer can run (read-only, nothing installed), OK to go ahead? Then stop.

## Turn 2: Check, then ask about background

After she agrees, run read-only commands silently:
- macOS: `sw_vers`, `sysctl -n machdep.cpu.brand_string hw.ncpu hw.memsize`, `system_profiler SPDisplaysDataType | grep -E "Chipset|Metal"`
- Linux: `nproc`, `free -g`, `nvidia-smi --query-gpu=name,memory.total --format=csv`
- Both: `python3 -c "import torch; print(torch.__version__, torch.cuda.is_available(), torch.backends.mps.is_available())"` (skip quietly if missing)

Note which catalog projects this computer can run: laptop-friendly projects need no NVIDIA GPU; single-GPU projects need one NVIDIA GPU with 24 GB or more; multi-GPU projects need two or more. This describes the machine only; never label the machine or the person out loud.

If the commands show you are in a Linux sandbox rather than her real machine (for example, the user asked about a Mac but `uname` says Linux), do not report sandbox specs as hers. Ask her instead: "What computer are you on? (Apple menu → About This Mac shows the chip and memory.)"

Reply in at most 3 lines: one line with the result (for example, "MacBook Air, Apple M2, 16 GB: a great fit for our laptop-friendly projects."), then ask: what's your background, and which courses have you taken? Stop.

## Turn 3: Ask about interests

Acknowledge her courses in a few words, then ask which topics excite her most (for example, image generation, reasoning, language models). Stop.

## Turn 4: Recommend

Read `catalog.md` in this skill's folder. Rank by: what this computer can run first (skip projects that need hardware it doesn't have), then the courses she listed against each project's prerequisites, then interest.

Recommend **one** project only, in at most 3 lines: the paper, its mentor (named once), and one reason tied to her courses or interests. End with a short question such as "Want to start with this one?"

Only if she says no, offer the next best project the same way.

If a project's mentor is "[mentor name]", it has no mentor yet; never recommend it as if it had one. Stop.

## Turn 5: Set up

When she picks, silently create:
1. `mentorship/project.md`: mentor name and `<mentor email>`, paper and link, reproduction scope, the computer it runs on, week 1 of 12, milestones (Reproduce weeks 1-4, Probe 5-6, Extend 7-10, Write and submit 11-12), and an empty `## Mentor's notes for Claude` section.
2. `mentorship/log.md`: today's date, `[done] selected project <ID>`, and her background and interests as `[understanding]` notes.

Reply in at most 3 lines: she's set up with her mentor, and her first step: read the abstract and the section being reproduced, then explain the idea back in her own words.
