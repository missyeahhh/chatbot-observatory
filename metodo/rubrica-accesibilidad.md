# Rubric 1: accessibility

**v1.0, 23/8/2026.** Criteria drafted by Claude, reviewed and approved by Sol the same day.

It measures one thing: **whether a person who does not use a mouse, or does not see the screen, can open the chat, talk, and leave.**

Every criterion is anchored to a WCAG 2.2 success criterion, so that each finding cites a standard and not an opinion.

## Scope, and why it is a cut

In scope: whatever can be tested from a Mac with Safari, with no account on the site and no extra hardware.

Out of scope in v1, for cost, not for lack of interest:

- Screen readers on Windows (NVDA, JAWS). They are the ones most used by blind people, but they need a Windows machine. Decided by Sol on 23/8: v1 uses VoiceOver on Safari only, and declares that limit in every report.
- Voice navigation and switch access.
- Dark mode and reduced motion preferences.

## Scale

Per criterion: **2 passes, 1 partial, 0 fails, n/a could not be tested.**

**Hard rule: `n/a` is never counted as 0.** The score is written as "X out of Y applicable", never out of a theoretical maximum. Same rule as rubric 3.

## The five criteria

### A1. Reach it and open it with the keyboard

**What it measures:** whether the chat exists at all for someone navigating with Tab.

**Test:** from the address bar, Tab to the button that opens the chat. Enter or Space. See where focus lands.

| score | condition |
|---|---|
| 2 | the launcher takes focus, opens with Enter or Space, and focus moves into the widget (text field or first control) |
| 1 | it opens, but focus stays outside and you have to tab around to find it |
| 0 | the launcher never takes focus, or takes focus and does not respond to the keyboard |

**Evidence:** screenshot with the focus ring visible on the launcher, and the number of Tabs from the address bar.

**WCAG:** 2.1.1 Keyboard, 2.4.3 Focus Order.

### A2. Leave without getting trapped

**What it measures:** whether the widget gives control back.

**Test:** with the chat open, press Esc. Then Tab 20 times in a row. Then close with the button and see where focus lands.

| score | condition |
|---|---|
| 2 | Esc closes it, Tab leaves the widget back into the page, and on close focus returns to the launcher |
| 1 | you can get out, but only one of those ways works, or focus is lost on close (back to the top of the page) |
| 0 | focus is trapped inside the widget with no keyboard way out |

**Evidence:** key transcript (Esc, Tab x N) and a screenshot of where focus ended up.

**WCAG:** 2.1.2 No Keyboard Trap.

### A3. Screen reader

**What it measures:** whether the chat can be used without seeing the screen.

**Test:** VoiceOver on Safari (Cmd + F5). Open the chat, send a message, wait for the answer, walk the controls with VO + right arrow.

| score | condition |
|---|---|
| 2 | the widget has a name, the bot's answer is announced on its own when it arrives, and every button says what it does |
| 1 | it can be operated, but one of the three is missing: no name, or the answer is not announced and you have to go looking for it, or there are unlabeled "button" controls |
| 0 | VoiceOver does not enter the widget, or reads the content as one block with no structure |

**Evidence:** audio recording or transcript of what VoiceOver reads, with the exact moment the bot answers.

**WCAG:** 4.1.2 Name, Role, Value. 4.1.3 Status Messages.

**Declared limit:** VoiceOver on Safari only. A 2 here does not guarantee NVDA or JAWS.

### A4. Contrast and zoom

**What it measures:** whether the text is readable with low vision.

**Test:** measure the contrast of the bot's text and the user's text against their background with a tool (Safari's inspector shows it under Elements > Styles, or any contrast checker). Then zoom the browser to 200%.

| score | condition |
|---|---|
| 2 | every chat text at 4.5:1 or more, and at 200% nothing is clipped or overlapping |
| 1 | contrast passes but 200% breaks the layout, or the other way around |
| 0 | text below 4.5:1 in the bot's or the user's bubbles |

**Evidence:** the measured values per type of text, and a screenshot at 200%.

**WCAG:** 1.4.3 Contrast (Minimum), 1.4.4 Resize Text.

### A5. Timeouts

**What it measures:** whether time works against someone who is slow.

**Test:** type half a message without sending it. Leave the session idle for 10 minutes. Come back.

| score | condition |
|---|---|
| 2 | it does not expire, or it warns before expiring and lets you extend, and what was typed is still there |
| 1 | it expires with no warning but what was typed and the history survive |
| 0 | it expires with no warning and what was typed or the history is lost |

**Evidence:** start time and return time, screenshot of the state on return.

**WCAG:** 2.2.1 Timing Adjustable.

## What this rubric does NOT cover

- Whether the bot understands what it is told. That is answer quality, not accessibility.
- Whether the page around the chat is accessible. The widget is audited, not the site.

## Run protocol

1. **Clean Safari**, no extensions, window at 1280 px wide.

2. **Fixed order:** A1, A2, A4, A5 in one session. A3 in a separate session, because VoiceOver changes how focus behaves and would contaminate A1 and A2.

3. **One run is enough.** Unlike rubric 3, the behavior here is deterministic: the widget is the same code every time. A failure is documented with a screenshot and needs no second run.

4. **A screenshot for every 0.** No screenshot, no finding.

## Cost

Between 25 and 35 minutes per site, of which 10 are the wait in A5, which runs in parallel with something else.

For 6 to 8 sites: **between 3 and 4 hours.** That holds only if rubric 2 runs in the same session per site, which is how the runs are planned.
