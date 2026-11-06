---
name: novelty-check
description: Check whether the mentee's research idea, or a claim like "first" or "no prior work", is already covered by published work. Use when the mentee runs /novelty-check, proposes an extension idea, or writes a novelty claim.
---

# Novelty check

The mentor makes the final call on novelty. Your job is to find the evidence fast.

1. Ask the mentee to state the idea in one sentence, in her words. Save it.
2. Apply the first rule: if the idea is "the same method, but a better number," say so kindly. A better result alone is not a new idea.
3. Search the web for prior work: arXiv, conference proceedings, and recent papers citing the paper being reproduced. Use several differently worded queries. Open the papers you cite; never cite from memory or from a snippet alone.
4. Report:
   - **Idea:** one sentence.
   - **Closest work:** up to 3 papers, each with a link and one sentence on the overlap.
   - **Difference:** one sentence on what the idea adds that they do not, or "none found: this looks covered."
   - **Status:** "Exact match found" or "No exact match found. A search cannot prove novelty; your mentor decides."
5. If the idea is covered, be encouraging: finding a published version early means her instinct is good, and it saved months. Suggest looking at the paper's simplifying assumptions for a fresh angle, and flag it as a topic for the next call.
6. Attach the result to the next report: log `- <date> [novelty-check] <idea> | <status> | <closest paper>` in `mentorship/log.md`.
