# agentq-evals

Building an evaluation and observability system for agentic AI — applied to eDiscovery-style document workflows.

A 4-week project. Each week ends with something committed here. Study is the input; the commit is the proof. A week that ends with notes but no commit didn't happen.

> **Data note:** This repo uses **synthetic data only** — generated emails, contracts, and memos, plus fake review tasks. No proprietary traces or client documents. The goal is a reusable, shareable eval methodology, not an internal artifact.

---

## Progress

- [ ] **Week 1 — Error analysis & failure taxonomy**
- [ ] **Week 2 — Code-based & LLM-as-judge evals**
- [ ] **Week 3 — Observability & CI**
- [ ] **Week 4 — Narrative artifact**

---

## Week 1 — Error analysis & failure taxonomy

Two days reading, three days doing. The doing is the larger half — protect it.

- [ ] **Day 1 — Read (Hamel Husain).** Read with one question: what does "look at your data" mean? Stop when you can explain open-coding + clustering in two sentences.
- [ ] **Day 2 — Read (Eugene Yan).** Eval design. Same stopping rule — two sentences, then stop, even if there's more to read.
- [ ] **Day 3 — Generate the data.** Script (Claude API) to create ~30 synthetic eDiscovery-style docs, then run a summarization/query task to produce 50–100 outputs into `/data`.
- [ ] **Day 4 — Open-code, part 1.** Read each output. Write in plain language what went wrong — a description, not a score. Get through ~half.
- [ ] **Day 5 — Open-code part 2 + cluster.** Finish the labels. Cluster them into ~5 recurring failure types. That cluster set is the taxonomy.
- [ ] **SHIP:** Taxonomy written into this README + labeled dataset committed to `/data`.

> Friday checkpoint: did the commit land? Yes → Week 2. No → the forcing function is too weak; fix it before continuing.

## Week 2 — Code-based & LLM-as-judge evals

The week's real test isn't building a judge — it's proving the judge agrees with you.

- [ ] **Day 1 — Read (LLM-as-judge methodology).** Focus on judge design and, critically, judge–human alignment. Two-sentence stopping rule again.
- [ ] **Day 2 — Code-based evals.** Write assertion checks for deterministic failures from the Week 1 taxonomy: bad format, hallucinated citations, missing entities. These are plain Python, no LLM.
- [ ] **Day 3 — Build the LLM-judge.** An LLM-judge for the subjective failure modes (e.g. "buried the key fact"). Prompt it against your taxonomy categories.
- [ ] **Day 4 — Measure alignment.** Run the judge over Week 1's human-labeled set. Compute agreement: true-positive / true-negative rates. This is the deliverable that separates a real eval from theater.
- [ ] **Day 5 — Tighten + write up.** Adjust the judge prompt where it disagrees with you, re-measure, and write the notebook narrative.
- [ ] **SHIP:** Eval scripts in `/evals` + a notebook reporting judge-alignment metrics.

> If the judge disagrees with your human labels and you can't close the gap — that's a finding, not a failure. Report the number honestly.

## Week 3 — Observability & CI

Lighter study, more wiring. The goal is a closed loop: traces in, evals run automatically.

- [ ] **Day 1 — Read (Langfuse docs).** Tracing concepts: spans, traces, what to instrument. The docs are good — this is the lightest reading day of the project.
- [ ] **Day 2 — Build the toy agent.** A small agent: Claude API + 2 tools. Keep it minimal — it exists to be observed, not to be impressive.
- [ ] **Day 3 — Instrument with Langfuse.** Add tracing to the agent. Confirm traces appear and you can read a full run end-to-end.
- [ ] **Day 4 — Wire CI.** A GitHub Actions workflow that runs the Week 2 evals on every commit. Get it green.
- [ ] **Day 5 — Buffer + badge.** Fix whatever broke in CI (something will), add the green badge to this README.
- [ ] **SHIP:** Instrumented demo in `/agent` + a passing CI badge on this README.

> Day 5 is deliberately a buffer. CI always breaks the first time. Don't schedule over it.

## Week 4 — Narrative artifact

No new studying. This week converts the build into something n8n and Harvey will actually read.

- [ ] **Day 1 — Outline.** Structure the write-up: the problem, your taxonomy-first approach, judge alignment, the observability loop, what you'd do differently at scale.
- [ ] **Day 2 — Draft.** Write "How I'd build an eval & observability system for an agentic product." Staff-level reasoning, not a tutorial — show judgment, not steps.
- [ ] **Day 3 — Edit + visuals.** Tighten the prose. Add one diagram of the loop (traces → evals → CI). Clean up the repo README so a stranger can follow it.
- [ ] **Day 4 — LinkedIn post.** Write the post linking the repo. Lead with the result, not the process. Ties to your "PM who builds, not just describes" positioning.
- [ ] **Day 5 — Publish.** Push final repo state, publish the post.
- [ ] **SHIP:** Write-up in `/docs` + LinkedIn post live, linking the repo.

> The repo proves the skill. The write-up proves you can reason about it at the level the target roles hire for.

---

## Forcing function

- Repo is public and empty from day one. That discomfort is the point.
- One dated, visible deliverable per week.
- Public commitment posted (LinkedIn) or a weekly Friday checkpoint with someone who will ask.
