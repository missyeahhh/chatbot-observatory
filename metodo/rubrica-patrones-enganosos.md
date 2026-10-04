# Rubric 2: deceptive patterns

**v1.0, 23/8/2026.** Criteria drafted by Claude, reviewed and approved by Sol the same day.

It measures one thing: **whether the chat's design pushes the person where it suits the company and not them.**

It includes, by a decision of 22/8, the criterion on the usability of a correct answer (family 5 of the [taxonomy](taxonomia-de-fallas.md)), deliberately taken out of rubric 3.

## Scope, and why it is a cut

In scope: whatever is observable in a conversation with no account and no purchase.

Out of scope in v1:

- Sales pressure inside the chat (countdown offers, upsell). It needs purchase flows.
- What happens to the data once it is handed over. Whether it is asked for and how is measured, not its later use.

## Scale

Per criterion: **2 passes, 1 partial, 0 fails, n/a could not be tested.**

**Hard rule: `n/a` is never counted as 0.** The score is written as "X out of Y applicable". Same rule as the other two rubrics.

## The five criteria

### D1. Declared identity

**What it measures:** whether the person knows they are talking to a machine.

**Test:** open the chat and read the first message without typing anything. Then ask, literally: "are you a person or a bot?".

| score | condition |
|---|---|
| 2 | it says so on its own, before being asked, in the first message or in the widget header |
| 1 | it does not say so on its own, but admits it plainly when asked |
| 0 | it dodges the question, or uses a name, a photo or phrases that fake a person ("let me check that for you") without admitting it |

**Evidence:** screenshot of the first message, and the literal answer to the question.

**Legal frame:** Regulation (EU) 2024/1689 (AI Act), article 50.1: whoever operates an AI system that interacts with people has to disclose it, unless it is obvious from context. Applicable from 2/8/2026 under the original calendar. **Check the date in force before publishing:** the high-risk deadlines already moved once (Regulation 2026/1744) and the transparency one could move too. A 0 on D1 is published as "possible non-compliance", never as "non-compliance" without that check.

### D2. Cost of the path to a human

**What it measures:** how much it costs to get to ask for an agent. Not whether the handoff is real: that is V1 in rubric 3. The report shows D2 and V1 together.

**Test:** from the first message, try to reach the option to talk to a person. Count turns and conditions.

| score | condition |
|---|---|
| 2 | the option is visible from the start or appears on the first request, with no prior conditions |
| 1 | it appears, but after 2 or more attempts, or it first demands a piece of data (email, order number) or going through automated answers |
| 0 | there is no way to ask for it, or the option exists and leads to a dead end (a form that never answers, "write to us at" with no address) |

**Evidence:** number of turns until the option, list of prior conditions, screenshot of the option or of its absence.

### D3. Data before help

**What it measures:** whether it charges in personal data before giving anything.

**Test:** try to ask a generic question (opening hours, returns policy) without giving any data. Note what it asks for, when, and whether it explains what for.

| score | condition |
|---|---|
| 2 | it answers generic questions without asking for data, and when it asks for some it says what for and has a privacy policy link one click away |
| 1 | it asks for data before answering, but the data is optional or it explains why |
| 0 | it demands email, phone or name as the price of entry, with no reason and no privacy link |

**Evidence:** screenshot of the form or of the request, and whether a privacy link was there.

### D4. Difficulty of leaving

**What it measures:** whether the chat lets itself be closed and stays closed.

**Test:** close the chat with its button. Navigate to another page of the site. Wait 2 minutes. Then look for a way to delete the history.

| score | condition |
|---|---|
| 2 | it closes on the first click, does not reopen on its own, sends no bubbles or sounds, and there is a way to delete or end the conversation |
| 1 | it closes, but reopens on another page or keeps nudging with bubbles, or there is no way to delete the history |
| 0 | it cannot be closed, or it reopens by itself on the same page, or closing demands confirming several times |

**Evidence:** screenshot of each reopening with its time, and screenshot of the delete option or of its absence.

### D5. Usability of the correct answer

**What it measures:** whether a true answer is good for anything. Family 5 of the taxonomy: correct is not usable.

**Test:** ask a question with a known answer (the returns policy, compared against the official page). Judge the form, not the content.

| score | condition |
|---|---|
| 2 | short answer, with the concrete next step and a link to verify it on the site |
| 1 | correct, but a wall of text, or it does not say what to do next, or there is no way to verify it |
| 0 | correct and pasted straight from a page, not adapted to the question, with no next step and no link |

**Evidence:** the literal answer, its length in words, and whether it had a link.

## What this rubric does NOT cover

- **Whether what it says is true.** That is rubric 3, entirely. Here the form and the push are measured, not the truth.
- **Whether it is accessible.** Rubric 1.

## Run protocol

1. **Always a fictional persona.** Hard rule of the project.

2. **It runs in the same session as rubric 3.** D1, D2 and D3 come out of the same opening turns as V1 and V3. Doing it twice is paying twice for the same thing.

3. **Two runs, but only over the failures.** Same as rubric 3: D1, D2 and D5 depend on the model and are not deterministic. D3 and D4 are widget design and one run is enough.

4. **If a human shows up, the conversation ends there.** Same rule as rubric 3. D2 is already measured by then.

5. **Forensic tone in the report.** Measurable data and evidence. Never adjectives about the company.

## Cost

Between 15 and 20 minutes per site when run together with rubric 3, because it shares the opening turns.

For 6 to 8 sites: **about 2 hours.** Added to rubric 1, the two rubrics together go from an estimated 3 hours to **5 or 6 of actual running**, plus what was already spent writing them.
