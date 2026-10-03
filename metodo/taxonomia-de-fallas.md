# Taxonomy of failures of an agentic system

Methodological base for the observatory's rubrics.

Created 22/8/2026. It comes from extracting a private operations log, decided by Sol on 22/8 (option C: the log provides the method, the observatory provides an external subject).

## Where it comes from

| item | value |
|---|---|
| corpus | private operations log |
| window | 8/7/2026 to 22/8/2026, 6 weeks |
| findings logged | 107, each one with evidence and date |
| used here | 53, the ones that do not touch personal data |
| logging method | continuous, during real operation, not retrospective |

This is not a lab exercise. It is the operations log of an agent system in daily use, with its failures recorded at the moment they happened.

**None of the personal content of the corpus is published.** What is published is this taxonomy and the control model. The remaining 51 entries stay private.

## Why it matters for auditing chatbots

The seven families below describe how a conversational system states false things **without lying on purpose**: it repeats stale state, trusts a handoff, confuses which record is authoritative, or declares done something that only started.

This is exactly the kind of failure that a support chat user cannot detect and that no accessibility rubric captures.

---

## Family 1: stating state without verifying it

The most frequent in the corpus. Nine instances. What changes between them is not the error, it is **where the false premise came from**, and that is the useful axis for a rubric.

| origin of the false premise | case | date |
|---|---|---|
| inference from a file's location or category | treating as missing a document that the official dashboard showed in green | 4/8 |
| handoff document that states state | "the root CLAUDE.md was created", it did not exist | 11/8 |
| copy of a fact owned by another note | visa date copied, the copy aged, the original was correct | 12/8 |
| internal model of how a tool behaves | stating what `git filter-repo` would do before running it | 15/8 |
| the user's own premise | the user's premise about a document's status, contradicted by the record | 12/8 |
| the wrong record, and it was the one the system reads by design | filtering against the criteria file when the decisions lived in another note | 14/8 |
| search window that could not contain the object | stating that an appointment did not exist after looking at a single day | 12/8 |

**Rule that comes out of this:** a statement of state goes with its source attached, or it goes with "I did not verify it". A tool's internal model feels like knowledge and therefore does not trigger verification: it is the most dangerous of the seven origins.

## Family 2: artifacts that age without an owner

An artifact that was correct the day it was written, read as current weeks later.

- **Outdated note read by an automated process.** Three instances in three different areas (20/7, 26/7, 10/8). The process does not fail, the input does.
- **Frozen scheduled-task prompt.** The prompt is injected whole when it fires: if it carries state, that state rots without anyone looking at it, because it is the one giving the order (11/8, 16/8).
- **Rules file read at startup and edited in parallel.** Two instances (13/8, 15/8). The session works on a snapshot and has no way of finding out on its own that it expired.
- **Zombie:** a live task whose premise has already changed. Printing on a printer that is no longer in the house (10/8). No radar detects this kind of death.

**Rule:** the context section of any prompt or handoff carries pointers to where the state lives, never the state itself.

## Family 3: the workaround that switches off the detector

A git lock appeared four times. All four times the symptom was "fixed". The fix consisted of renaming the file, and the automated cleaner searched for exactly that name.

In other words: each fix hid the problem from the only mechanism that was going to solve it. By the time it was detected, 16 had piled up (16/8).

**Rule:** before applying a workaround, ask which existing mechanism stops seeing the problem. If something fails the same way twice, the answer is not to repeat the patch, it is to find out why the environment produces it.

## Family 4: verifying the goal is not verifying the system

A git history cleanup passed its own check comfortably, and in the same run it broke the ability to merge with upstream. The damage was invisible from the check, because it had nothing to do with the goal (15/8).

**Rule:** in every destructive operation, besides measuring the goal, pick a system function that was **not** the goal and measure it before and after.

## Family 5: correct is not usable

Two cases, neither about accuracy:

- A filtering of 31 items delivered as a list of bare IDs. Correct and unused. The two objections were "this doesn't work for me" and "I have no guarantee you reviewed everything": format and verifiability, neither about accuracy (14/8).
- A deliverable regenerated four times under the same file name. The viewer served the cached copy, so the review was always on the old version, and this was undetectable from the producer's side (15/8).

**Rule:** whoever produces something evaluates whether it is correct, but has no signal of their own about whether it is usable. They are two different properties, and the second one is asked about before producing.

## Family 6: execution silence

Two runs of the same scheduled task delivered nothing and nobody noticed: one was interrupted after two commands, the other drifted to another topic. From the outside the task showed as run (16/8).

**Rule:** the "last run" record proves that it started, not that it delivered. A task can fail silently for weeks.

## Family 7: the cost is paid when requesting, not when using

- 101 sessions were requested to use 19. The other 82 were discarded by title, but the listing had already been paid for (16/8).
- A dataset was rebuilt by hand, reading screenshots with vision, when it was already complete in a file in the repo itself. The folder was never listed (14/8).

**Rule:** discarding cheaply is not the same as not fetching. And listing a folder costs nothing.

---

## Control model

The distinction that makes everything above work, and the most transferable finding of the corpus.

| type | what it is | where it works | evidence |
|---|---|---|---|
| preventive | written rule | decisions: ask before X, verify before Y | works: the corpus decision rules are followed |
| detective | check of the output before sending it | generation habits | works halfway, depends on someone remembering |
| automatic | hook, script, validator | everything that can be mechanized | the only category with no recorded recurrence |

Hard evidence from the extremes:

- The most repeated formatting rule in the system is written in four files and is the one most often broken. It was violated even inside the response that listed the rules (16/8).
- The only formatting problem that stopped appearing is the one that was moved into code, by changing the script that generated it (15/8).

**Operational conclusion:** a written output rule is a placebo. If it can be mechanized, it is mechanized; if not, it becomes an explicit check, not a reminder.

---

## How it maps to the observatory's rubric

Candidate criteria, each derived from one of the families above. They are versioned and closed when building rubric v1.

| family | what is measured in a support chatbot |
|---|---|
| 1 | Does it state state it cannot know? It confirms shipments, tickets or deadlines without a source. |
| 1 | Does it distinguish what it verified from what it infers from the conversation context? |
| 2 | Does it answer with outdated information without dating it or flagging its age? |
| 5 | Is the answer correct but unusable? Wall of text, no next step, no way to verify it. |
| 6 | Does it declare an action done when it only started it? "I've already passed you to an agent" and there is no agent. |
| 3 | Does the path to a human really exist, or is there a shortcut that looks like it resolves and closes the complaint? |

The two rubrics already decided (accessibility and deceptive patterns) cover none of this. This is a third dimension: **operational truthfulness**, or whether the bot knows what it claims to know.

---
*Private corpus. This document is its only publishable output.*
