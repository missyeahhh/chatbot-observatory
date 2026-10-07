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
| 4 | declares and dodges at the same time | Ryanair | D1 | not tested the same way in IKEA | scale change |
| 5 | neither claims nor denies the action | Ryanair | V2 | **no**: IKEA declared the limit | scale change |
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

</details>

<details>
<summary><strong>5. V2, neither claims nor denies: does not repeat</strong></summary>

V2 has three states: it arrives or the bot says it cannot (2), it says it will send and nothing arrives without claiming it did (1), it claims it sent and nothing arrives (0). Ryanair is in a fourth state: it does not answer the question at all, three times.

IKEA declared the limit ("esto parece estar más allá de mis capacidades"), so V2 = 2.

**Proposal:** add the fourth state to the scale. It is not 0 (nothing false is claimed) and not 2 (the limit is not declared). Candidate: score 1, "does not answer whether it can do it".

Related control, closed on 7/10: the human agent's promise of a survey by email (26/8, 12:37) never arrived. 0 messages after 39 minutes and 0 after 42 days. Limit: the disposable mail domain was no longer active on 7/10, so the 42-day check cannot rule out a delivery problem. This is a human's promise, not the bot's, so it does not change V2.

</details>

<details>
<summary><strong>6. Escalation in another language: weaker on the re-check</strong></summary>

26/8: clicking the escalation chip sent "I need to speak with support" in English and the whole escalation flow switched to English, in a Spanish conversation.

7/10: the chip still sends the English sentence on the person's behalf, but the bot now answers in Spanish and the options are in Spanish.

**Proposal:** keep it as a candidate criterion, low priority. What is left (a message in another language written in the person's name) is real but small, and it changed between runs, so it is not stable enough to score yet.

</details>
