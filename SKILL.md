---
name: decision-or-default
description: Use before showing any visual work to a demanding client - a landing page, a first screen, a dashboard, a slide deck, a PDF, a palette or type choice - and before deploying a visual to a live address. Answers the one question a mechanical linter cannot - is this a DECISION or the DEFAULT of its category - and returns a verdict with a score on the client's scale, not the model's. Also use when a visual was already rejected and needs a rerun.
---

# decision-or-default

A mechanical detector catches markup flaws (contrast, font size, banned patterns). It returns an empty list on pages a client rates 1/10, because it cannot see the one thing that sinks them: the page is exactly what any model produces for that category. An empty detector output is absence of evidence, not proof of quality.

This skill answers the question the detector cannot:

> **Does this look like a decision, or like the default of its category?**

Run it in full before every show. Skipping it is unfinished work, not "unoptimized" work. None of these cancel the run: "the detector came back empty", "I checked the style guide", "it follows the reference", "it's a small change", "no time", "I already know what they'll say".

## Pass 1. The category-default test (first, before anything)

Three steps, written down, none skipped:

1. **Name the category out loud.** "Landing page of an AI studio", "SaaS pricing page", "personal portfolio", "internal dashboard", "sales deck".
2. **Describe the default of that category from memory.** What the average model output looks like for this request: composition, palette, typography, the set of blocks.
3. **Compare your work with that description line by line.**

**Three matches or more: it is the default. Verdict FAIL, stop here.**

A real failure: category "AI company site" -> default "light minimal, big grotesk, uppercase kicker, one dark button, three rows of cards" -> the build was exactly that, 5 of 5. The client pointed at the kicker before reading a word.

**Follow-up question if the test passed:** name ONE decision on this screen that a competitor who built the same thing in an hour would not have. Cannot name it: there is no decision, there is a tidy default.

## Pass 1-bis. The three questions demanding clients ask every time

**1. "Did you explore variants, or take the first thing that came?"**
Rule: for every visible block, at least three different constructions, and the report names which one was chosen and why the others were dropped. One option is not a choice, it is a reflex. Rough but original beats tidy and nothing.

**2. "How does the reference do it, and how do you?"**
Rule: for every device the reference uses, OPEN the reference and MEASURE how it works before building yours. Memory of a reference stores the mood ("light premium, a lead form") and loses the mechanics (the device at an angle, the floating cards, the light). Not the same - not worse.

**3. "Do you seriously consider this normal?"**
Asked when a block is crooked in composition. The typical crookedness: a full-width heading on the left, a lone button top right, a hole under it, decoration cut off by the block edge. Check: does the block have one axis? is there empty space that does not work as air? is the decoration fully inside the block?

**The scale.** A demanding client gives 3/10 where the builder feels 7. If your own score is above 6, rerun Pass 2: you are most likely grading your work, not what a person sees.

## Pass 2. The squint test, ten seconds

Look at it as someone who did not make it.

- Is the main thing visible in one second? Does every section have a dominant?
- **Mentally remove all the text. What is left?** Only lines: there is no block, there is a draft. On light backgrounds "expensive" is made by material: a surface with a gradient, a light edge on top, a layered shadow, warm light.
- Is there an OBJECT to look at and a LIGHT SOURCE that shapes it? Or is it text on paper?
- **What moves?** A completely still page is a dead page. The reference breathes constantly and reacts to the cursor.
- The honest "what I see in a second": if it is "a white site with a big heading", you described a mood, and a mood means the concept was not accepted.

## Pass 3. Client remarks as detectors

What they say -> what it means mechanically -> where to look. Run all of them.

| they say | mechanically | look at |
|---|---|---|
| "Cheap, the typical neural-net style" | minimalism on white without material | surfaces, edges, shadows, light |
| "Every first draft from an AI looks like this" | the category template was taken | Pass 1 |
| "The colors are off" | cream/sand canvas (L .84-.97, S<.06, hue 40-100) | token names like `--paper`, `--sand` are already evidence |
| "Looks cheap" | icon in a colored tile + pastel fill | drop the icons, give the card a micro-widget from data |
| "Simple, no wow" | system font, the page has no voice | not fixable with spacing; own font + three layers of shadow |
| "Just text. Plain text." | paragraphs where structure is needed | lists, ledger rows, tables, micro-charts |
| "Everything is huge" | sizes inflated, air replaced by size | scale 1.25, display separately |
| "Why is everything centered in one column, so much unused space" | one 860px column on a wide screen | 1560px, a side column, blocks 2-4 in a row |
| "You just copied it" | the reference carried over as a tracing | take the principle, not the form; write the headline yourself |
| "No single system, some centered, some at the edge" | alignment not held | one axis for the whole layout |
| "Washed out" | contrast and depth lowered | deeper accent, secondary text not faint |
| "Boring. Just three blocks." | three identical cards for things different in nature | different block types, different sizes |
| "Terrible, google what it looks like" | drawn from memory, not from nature | open the real thing and look |
| "Raw, check your own work" | not all states were run | every phase, every slide, every edge |

Tells that are bans, not defaults, for most demanding clients: an uppercase kicker above a heading; pulsing dots and running underline lines; small gray text on white and text under 13px on dark; three identical cards with icons; a copied reference.

## Calibration: the client's own taste file

The passes above are generic. The score is not: it must be on the client's scale. Keep a `TASTE.md` next to the project (template in this repo) with two lists:

- **What the client NAMED good**, verbatim, with the mechanism you extracted (not "liked the second one" but the principle that separates the chosen from the rejected). Do not paste a liked device everywhere: record it as taste, apply it where it fits.
- **What the client rejected**, verbatim, as a stop-list.

Two working methods for filling it:

- **Show variants, do not describe them.** Demanding clients choose well and describe badly. Put 3-4 constructions that differ in structure (not in trim) on one page, switch them with keys 1-4, keep the address stable between rounds so they refresh a tab instead of opening a new one. Ask for numbers, not adjectives.
- **Rejected twice with words about quality: change the tool, not the effort.** "Cheap", "looks like a child made it" after two rounds means the instrument (hand-drawn SVG where a generator belongs, vector where a photo belongs) is the wrong class. Say so before the client does.

## Verdict

Strict format. Shown to the client together with the work.

```
VERDICT: FAIL / FIX PART / PASS        Score: N/10

Category:               <which>
Category default:       <what the average result looks like>
Matches with default:   N of 5   -> <decision or default>
One decision a competitor would not have: <one, concrete> / NONE

Kill:     <what to remove entirely - a list, not "tweak">
Fix:      <what to rework>
Keep:     <what works>
```

Below 7: do not show, rebuild. "Kill" empty while the verdict is not PASS means the critic did not run; run again. Defaults are cured by removal, not by repainting.

## How to look, not guess

A screenshot shows one frame; hover, motion and page rhythm are invisible in it. Before the verdict, capture the page at the client's real viewport(s) and in the client's browser engine, take a full-page shot after scrolling, and film the hero for a few frames if it moves. Judging motion from a still is guessing.

## What the critic does not do

- Does not praise. "Keep" is a list of what not to touch, not a compliment.
- Does not suggest cosmetics. A default is not cured by a new accent color.
- Does not check markup: sizes, contrast, overflow belong to a linter and a browser diff, run separately and after.
- Does not argue about taste. The taste file is the client's; arguing with it is arguing with the client.
