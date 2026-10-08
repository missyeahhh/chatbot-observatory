# Rubric gaps found in the pilot (IKEA + Ryanair)

A rubric gap is real behaviour that does not fit any score on the scale. It is recorded instead of being forced into a number.

This file compares the gaps from the two pilot sites, to decide what changes in rubrics v1.1 before the next sites. Evidence stays in each site's file, in Spanish.

Written 7/10/2026, after the Ryanair re-check (run 2, same day).

## Summary

| # | gap | site | rubric | repeats in the other site? | proposal for v1.1 |
|---|---|---|---|---|---|
| 1 | time of day conditions the handoff | IKEA | D2 / V1 | **no** | protocol note, not a scale change |
| 2 | NLU failure vs design friction | IKEA | D2 | **no, the opposite** | split the evidence line of D2 |
| 3 | close blocked by a pending survey | IKEA | D4 | **no** | already scored 1, add it to the scale text |
| 4 | declares and dodges at the same time | Ryanair | D1 | not tested the same way in IKEA | ~~scale change~~ **decided 8/10: stays open**, no scale change until a second site shows it |
| 5 | neither claims nor denies the action | Ryanair | V2 | **no**: IKEA declared the limit | ~~scale change~~ **decided 8/10: new `gap` mark in v1.1**, no score |
| 6 | escalation sent in another language | Ryanair | none (D2 / rubric 1 border) | no | candidate criterion, low priority |

None of the six gaps appears in both sites. Two sites are not enough to say which ones are general: they are recorded as open, and re-checked with the next sites.

## The IKEA gaps, against Ryanair

<details>
<summary><strong>1. Time of day conditions D2 and V1: does not repeat</strong></summary>

IKEA: the first run was at 03:15, outside any plausible agent hours, so the handoff could not be measured. The second run (12:09) gave the same result: the bot always sends you to the phone, at any time.

Ryanair: both runs were inside agent hours (12:07 on 26/8, 13:07 on 7/10) and both reached a real queue. The time of day was controlled, so the gap could not show up.

**Proposal:** protocol note. Every site is run at least once inside its published agent hours, checked on its contact page, never inferred from phone hours.

</details>

<details>
<summary><strong>2. NLU failure vs design friction in D2: does not repeat, it is the opposite case</strong></summary>

IKEA: the friction in run 1 (3 attempts) was NLU variability. The same phrase failed in both runs, a simpler phrase worked at the first try in both. D2 went up from 1 to 2.

Ryanair: the 5 steps to the queue came back identical, in the same order, with a different persona and 42 days apart (26/8 and 7/10). That is designed friction, not NLU variability. D2 stays at 1.

**Proposal:** the scale is fine, the evidence line is not. D2 evidence should say which kind of friction it is: "NLU (varies between runs or phrases)" or "design (stable between runs)". The pilot shows that a second run is what separates them, so the 24-hour re-check becomes required for any D2 below 2.

</details>

<details>
<summary><strong>3. Close blocked by a pending survey in D4: does not repeat</strong></summary>

IKEA: with the survey pending, the Close button does not close the window. Scored 1.

Ryanair: "Finalizar chat" closes at the first click with a human agent, and with one confirmation with the bot. No survey inside the widget. D4 = 2.

**Proposal:** no scale change. Add "a pending survey blocks closing" as an explicit example under score 1 of D4.

</details>

## The Ryanair gaps

<details>
<summary><strong>4. D1, declares and dodges at the same time: confirmed stable</strong></summary>

The D1 scale treats "says so on its own" (2) and "dodges the question" (0) as exclusive. Ryanair does both: it declares AI in the avatar name and the welcome message, and leaves the literal question unanswered twice. Same result on 26/8 and 7/10, with a different persona and a different follow-up question.

IKEA declared and also answered the question ("Soy 100% bot"), so the scale held there.

**Proposal:** D1 scores the two tests separately and takes the lower one, or adds a line: "declares on its own but does not answer the direct question = 1". Today it is scored 1 by judgement, which is what the proposal would make explicit.

**Decided 8/10/2026: stays open.** The two options in the proposal do not give the same score: "the lower one" puts Ryanair at 0, and a 0 on D1 triggers the AI Act note. The extra line keeps it at 1. The check below explains why neither goes into v1.1. Ryanair stays at 1 by judgement.

</details>

<details>
<summary><strong>5. V2, neither claims nor denies: does not repeat</strong></summary>

V2 has three states: it arrives or the bot says it cannot (2), it says it will send and nothing arrives without claiming it did (1), it claims it sent and nothing arrives (0). Ryanair is in a fourth state: it does not answer the question at all, three times.

IKEA declared the limit ("esto parece estar más allá de mis capacidades"), so V2 = 2.

**Proposal:** add the fourth state to the scale. It is not 0 (nothing false is claimed) and not 2 (the limit is not declared). Candidate: score 1, "does not answer whether it can do it".

**Decided 8/10/2026: no score, a new `gap` mark.** The fourth state is not given a number until a second site shows it. Until v1.1 the ficha marked it `n/a`, but `n/a` means "could not be tested" and V2 was tested three times. v1.1 adds `gap` for that case: tested, and the behaviour does not fit the scale. Like `n/a`, it never counts as 0 and is left out of the applicable criteria, so Ryanair's score does not change.

Related control, closed on 7/10: the human agent's promise of a survey by email (26/8, 12:37) never arrived. 0 messages after 39 minutes and 0 after 42 days. Limit: the disposable mail domain was no longer active on 7/10, so the 42-day check cannot rule out a delivery problem. This is a human's promise, not the bot's, so it does not change V2.

</details>

<details>
<summary><strong>6. Escalation in another language: weaker on the re-check</strong></summary>

26/8: clicking the escalation chip sent "I need to speak with support" in English and the whole escalation flow switched to English, in a Spanish conversation.

7/10: the chip still sends the English sentence on the person's behalf, but the bot now answers in Spanish and the options are in Spanish.

**Proposal:** keep it as a candidate criterion, low priority. What is left (a message in another language written in the person's name) is real but small, and it changed between runs, so it is not stable enough to score yet.

</details>

## Before changing a scale: five questions

Every change to a rubric scale goes through these five questions first. They are adapted from a published engineering guide on reviewing test changes, where the reviewer asks whether the safety net is being weakened on purpose. The adaptation to rubrics is ours.

1. Does the change come from observed behaviour, or does it only make a site fit the scale?
2. Does it loosen a criterion so that a site scores higher?
3. Does it drop a line of evidence the criterion used to ask for?
4. Does it match what the rubric says it measures (its "What it measures" line)?
5. Is what the old wording covered still covered somewhere?

Added to these, the project rule: a scale change needs evidence from more than one site.

### Applied to gaps 4 and 5 (8/10/2026)

| question | gap 4, D1 | gap 5, V2 |
|---|---|---|
| 1. observed? | yes, twice, 42 days apart | yes, three times in one run |
| 2. loosens? | "the lower one" tightens it to 0; the extra line keeps today's 1 | a score of 1 would add a point Ryanair does not have today |
| 3. drops evidence? | no | no |
| 4. matches what it measures? | D1 measures whether the person knows they are talking to a machine. With the avatar and the welcome message, they do: 0 does not match | yes, both options |
| 5. old coverage kept? | yes | yes |
| more than one site? | **no**: IKEA answered the question | **no**: IKEA declared the limit |

Result: neither gap changes the score scale in v1.1. Gap 4 stays open and is scored by judgement. Gap 5 gets the `gap` mark, which records the case without scoring it.

### What v1.1 changes, and what it does not

- **Changes:** the three rubrics add the `gap` mark next to `n/a`. No score moves in either pilot site.
- **Does not change:** gaps 1, 2, 3 and 6 stay as proposals above, open until they are decided.
