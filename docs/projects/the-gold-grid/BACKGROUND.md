# The Gold Grid: background and thinking so far

**Status:** this is now a project. [README.md](README.md) has the current state and [ROADMAP.md](ROADMAP.md) has what is next. This file keeps the history and the reasoning behind the decisions.
**Recorded:** 26 November 2026

## Agreed direction (26 November 2026)

The first product is a times tables skill trainer, not a grade-based course. Grades are dropped for now. The sections further down record the earlier thinking and still apply where they do not conflict with this one.

**Agreed**

1. Facts up to 10 × 10, with 11 and 12 as a bonus level.
2. Division comes in the second version, as the same facts in reverse.
3. Aimed at children with their parents.
4. The free version launches first on its own. Tier 2 follows once people are using it.

**Tiers as agreed**

- **Tier 1, free, no sign-up, no AI.** As much as possible goes here. Progress is saved on the device only.
- **Tier 2, paid, the memory layer.** Saved progress, a parent sign-on and a child sign-on that show different things, and progress graphed for the parent. Pricing is the critical decision; to be tested per family with a free trial.
- **Tier 3, paid, premium, with usage limits.** AI features such as practice from a homework photo. Held until there are more skills than times tables.

**Why times tables first:** no grade or curriculum mapping is needed, the audience is wide, later maths depends on it, and it suits generated questions with predictable mistakes. The catch is a crowded field of speed-drill apps (not yet surveyed). The difference here is teaching strategies and showing the parent which facts are weak.

### Outline of version 1 (free)

**Strategies taught**

| Table | Strategy | Example |
| --- | --- | --- |
| Any | Turn it around | 7 × 3 = 3 × 7 |
| ×10 | Each digit moves one place left | 6 × 10 = 60 |
| ×5 | Half of the ×10 answer | 5 × 8 = half of 80 = 40 |
| ×2 | Double | 2 × 7 = 14 |
| ×4 | Double, then double again | 4 × 7 = 14, then 28 |
| ×8 | Double three times | 8 × 6 = 12, 24, 48 |
| ×3 | Double, plus one more lot | 3 × 7 = 14 + 7 = 21 |
| ×6 | The ×5 answer plus one more lot | 6 × 7 = 35 + 7 = 42 |
| ×7 | The ×5 answer plus the ×2 answer | 7 × 8 = 40 + 16 = 56 |
| ×9 | The ×10 answer minus one lot | 9 × 7 = 70 − 7 = 63 |
| Squares | Learn as anchors, then step from them | 7 × 8 = 49 + 7 = 56 |

With turning facts around and ×1, ×2, ×5 and ×10 known, 21 facts remain up to 10 × 10. With the ×9 strategy, 15 remain.

**Levels, in order**

1. ×1 and ×10
2. ×2
3. ×5
4. Turn it around (mixed facts from levels 1 to 3, both ways round)
5. ×4
6. ×9
7. ×3
8. ×6
9. ×8
10. Squares
11. ×7
12. Mixed, all facts
13. Bonus: ×11 and ×12

**Each level**

- Opens with a strategy card: the idea, a dot or box picture showing why it works, and two worked examples.
- Starts as multiple choice, then moves to typing the answer after two right in a row.
- A hint shows the strategy applied to that fact, not the answer.
- A miss shows the answer, the strategy for it, and what kind of slip it was.

**Slips tracked:** neighbouring fact (one lot out), a known mix-up (6 × 7, 6 × 8, 7 × 8, 6 × 9), adding instead of multiplying, and a turned-around fact the child knows one way but not the other.

**The grid**

- A 10 × 10 grid where each square lights up as that fact becomes solid.
- A fact is solid after it is answered correctly, unaided, on three separate occasions.
- A "facts left" counter beside it.
- Solid facts come back for review at growing intervals and go dim again if missed.

**Fun layer**

- A daily set of ten questions with a clear "done for today".
- A streak with one free skip day a week.
- "Beat your own time" for solid facts only, kept apart from the learning levels.

**Parent corner (on the device)**

- The grid, the weakest five facts, and the strategy to remind the child of for each.
- A note that progress is saved on this device only.

**Built as:** one self-contained page with no sign-up and no server, like the factoring quiz.

### Version 1 as built (26 November 2026)

Published at https://claude.ai/artifact/TLxZsJjW3UiLMs8Jqcipzx (private until shared from the page) and saved as [`prototypes/times-tables.html`](prototypes/times-tables.html).

It follows the outline above, with these choices made during the build:

- **Levels are all open.** The next unfinished level is marked "Up next", but a child or parent can pick any table. There is no automatic moving down.
- **Passing a level:** 7 right out of the last 8 answers at that level.
- **A solid fact:** three right answers without a hint, with at least five other questions between each one that counts. This stands in for "three separate occasions" so a square can turn gold within one sitting.
- **Each fact fills two squares** (3 x 7 and 7 x 3), so the grid has 55 facts, not 100.
- **Today's ten** picks up to five weak facts, up to three reviews, then new facts from the newest level.
- **Beat your time** unlocks at 10 solid facts and does not change the grid.
- **Slips named in feedback:** one lot out, adding instead of multiplying, and the well-known mix-ups (42, 48, 54, 56, 63).

Tested with a logic script and a headless browser run through a level, a daily ten, the timed round and a reload. Not yet tried with a child.

### Version 2: division (27 November 2026)

Added to the same page as a Times / Divide switch on the home screen.

- **Separate memory.** Divide has its own grid, levels, best time and "facts to help with" list, because knowing 7 x 8 does not always mean knowing 56 / 7. The streak and "done for today" are shared.
- **Levels:** the same order as Times without "Turn it around": divide by 1 and 10, 2, 5, 4, 9, 3, 6, 8, squares, 7, mixed, bonus 11 and 12.
- **Tricks:** halve for 2, halve twice for 4, halve three times for 8, double then divide by 10 for 5, move the digits right for 10. For 3, 6, 7 and 9: "ask what times the number makes it". For 12: guess from the tens digit, check with "10 lots plus 2 lots", and go down if it is too much. For 11: the double digits. The 9s card adds the shortcut that the answer is one more than the tens digit.
- **Slips named:** one out (with a check by multiplying), giving the number divided by, and subtracting instead of dividing.
- **Times change made at the same time:** facts with a 9 use the "x10, take one away" trick first, and a second way is shown when a fact has two tricks.

Tested with the logic script and a headless browser run in Divide mode. Not yet tried with a child.

### What comes after version 1

1. Try version 1 with three to five children and watch where they get stuck or bored.
2. Version 2: division as the same facts in reverse. Done, see above.
3. Tier 2: parent and child sign-ons, saved progress, the grid over time.
4. More skills, each one building on the last: multiplying larger numbers by breaking them apart, fractions, negative numbers, simple equations, then factoring (already prototyped).
5. Tier 3 once there are enough skills for the homework photo to be useful.

## The idea in one paragraph

A practice tool that teaches one maths skill at a time, explains why each method works, notices which specific mistake a child keeps making, and tells the parent about it in plain words. It would be organised by grade so a parent can pick their child's year and start.

## What exists today

| Item | Where | Notes |
| --- | --- | --- |
| Printable handout, "Factoring Step by Step" | https://claude.ai/artifact/GHAF13oZWY1AATzNfindcm | Private until shared from the page's Share menu. |
| Interactive quiz, "Factoring Quiz" | https://claude.ai/artifact/JzNExJ3C44JfAbsyW63d4E | Was shared as "Anyone with the link" when last published. |
| Source for both | [`prototypes/`](prototypes/) | Page content only. The publishing tool adds the `<html>`, `<head>` and `<body>` wrapper, so wrap the file before opening it directly in a browser. |

## How we got here

Each step was a small request, and each one made the thing simpler or added one teaching idea.

1. **Explained factoring in chat** with a few examples of each type.
2. **Turned it into a printable handout** covering ten methods, with a "which method do I use" table, worked examples and practice questions.
3. **Made it simpler.** Cut it to the four basics (numbers, taking out what is shared, a square minus a square, three terms starting with x²). Shorter sentences, smaller numbers.
4. **Added the why.** Every section got a "Why it works" box that shows the multiplication going forwards first, so factoring reads as the same thing backwards. Added a box (area) picture for three-term problems and a "check by multiplying back" line on the first example of each method.
5. **Made it a quiz.** Multiple choice, six levels, questions generated on the fly, an explanation after every answer, and difficulty that moves with the percentage correct.
6. **Rebuilt the quiz around how people learn** (the version that is live now). See the next section.

The lesson from steps 3 and 4: the first version was complete but too much. Cutting scope and then adding reasons made it better than adding more topics would have.

## How the quiz works

Everything is one self-contained HTML page. No server, no question bank.

**Questions are generated, not stored.** Each level has a small function that picks random numbers and returns the expression, the correct answer, three wrong answers, a hint, the steps, and the reason the method works. Wrong answers are built from real mistakes, not random numbers, and each is tagged with the kind of slip it represents.

**Levels**

1. Take out a number
2. Take out x
3. A square minus a square
4. Three terms, all plus
5. Three terms with minus signs
6. Two steps (take out a number, then factor the bracket)
7. Mixed: no method is named, and the question is "what is the first step?"

**Rules**

| Rule | Detail |
| --- | --- |
| Moving up | 4 or more right out of the last 5 answers at the current level. |
| Moving down | Fewer than 40% right after at least 3 answers at the current level. |
| Pick, then produce | A level starts as multiple choice. After two right in a row, the choices go away and the learner fills in the missing numbers and signs. A miss brings the choices back. |
| After a miss | The feedback shows the right answer, why the chosen one fails, a "watch for" tip for that kind of slip, the steps, and why the method works. The next question is one more of the same kind. |
| Review | A finished level comes back after 4 questions. Each right answer doubles the gap (8, 16, up to 32). A miss brings it back after 3. |
| Hints | A hint is a nudge, not the answer. A hinted right answer counts in the score but not toward moving up. On three-term fill-in questions the hint shows a live box picture that updates as the learner types. |
| Progress | Saved in the browser only. Nothing is sent anywhere. |

**Slip kinds tracked:** signs, picking the pair of numbers, dividing every term, taking out a letter, the square minus a square pattern, stopping too early, choosing the method. The page shows the learner's most common one.

**How it was tested.** A script generated about 56,000 questions and checked that each has exactly one correct answer, distinct wrong answers, and a fill-in solution that marks as correct. A headless browser then clicked through 140 questions at phone width with no errors. Nobody has yet checked the layout by eye or tried it with a real learner.

**Two bugs worth remembering**

- A three-term question with both numbers equal to −1 produced only two wrong answers. Fixed by adding more candidate pairs. Found only because the test generated thousands of questions.
- Hiding elements with the `hidden` attribute did nothing where the element had its own `display` style. Fixed with an explicit `[hidden] { display: none !important; }` rule.

## Teaching ideas

**Built into the current quiz**

1. Make the learner produce the answer instead of only recognising it.
2. Teach to the specific mistake, using the tagged wrong answers.
3. Bring old material back at growing intervals.
4. Train the choice of method, not just the method.
5. Offer a hint before giving the answer.
6. Show the working as a picture (the box).

**Not built yet**

- A "try one" question straight after each section of the handout.
- A common mistakes page showing a wrong answer beside the right one.
- Working space on the printout so it doubles as a worksheet.
- A one-page summary card.
- Fully typed answers (the learner writes the whole expression) at the top levels.
- Using the slip history to pick the next question across the whole session, not just the one after a miss.

**Where the same approach fits:** topics where skills build in a clear order and mistakes are predictable. Fractions, negative numbers, solving linear equations, expanding brackets, percentages, exponent rules.
**Where it fits less well:** word problems and proofs, where the difficulty is setting the problem up.

## Making it fun

Children dropping off is the biggest risk, so this matters more than extra topics. Ideas, strongest first:

1. **Short sessions with a clear finish.** Five questions a day, then "done for today". A visible end is easier to start than an endless quiz.
2. **A streak the child owns.** Days in a row, with one free "skip day" a week so a missed day does not wipe it out.
3. **Beat your own best, not other children.** Longest run of right answers, fastest clean level. No leaderboards against classmates.
4. **Progress you can see.** A map or path where each skill is a stop, so finishing a level visibly moves the child forward.
5. **A puzzle wrapper.** Each right answer reveals a piece of a picture, opens a lock on a code, or moves a character. The maths stays the same; the reason to answer changes.
6. **Boss questions.** The last question of a level is a harder two-step one, presented as the challenge that unlocks the next level.
7. **Parent and child together.** A two-player mode where the parent answers too, or a weekly "challenge your parent" set. This also fits selling to the parent.
8. **Choice.** Let the child pick the theme or which skill to practise next from two options.

Things to avoid: timers on every question (they raise anxiety and reward guessing), penalties for wrong answers, and rewards so large the child clicks through to get them without reading the explanation.

Cheapest to try first: 1, 2 and 5. They need no accounts and fit in the single page.

## What would make it different from other courses

Competitors have not been surveyed in detail. Check each of these against the main products before relying on it.

**The three to bet on**

1. **Practice from this week's homework.** The parent photographs a homework sheet or textbook page and the tool generates practice on those skills. This matches school without mapping every curriculum. Uses AI.
2. **Tracing a mistake back to its cause.** A child who keeps getting signs wrong in factoring usually has a gap in multiplying negative numbers. The tool drops back to that earlier skill, fixes it, and returns. Needs a map of which skill depends on which; no AI.
3. **Coaching the parent.** The weekly note includes a two-minute script for explaining the one thing the child is stuck on, and a refresher for parents who have forgotten the maths. Can start from fixed text per slip kind; AI makes it personal.

**Other additions**

| Addition | What it does | Needs AI |
| --- | --- | --- |
| Explain it back | The child says or types why an answer is right, and the reasoning is checked. | Yes |
| Find the mistake | A worked solution with one error to spot. | No |
| "How sure are you?" | A confidence tap before the answer is revealed. Exposes guessing and confident errors. | No |
| Mastery that has to last | A skill counts as mastered only after a correct answer weeks later. | No |
| Weekly printed page | One worksheet built from that child's own slips. | No |
| A tutor that asks, not tells | A leading question about the current problem when the child is stuck. | Yes |

AI features cost money on every use and need safeguards suitable for children. The others are ordinary code.

## Tiers

The owner's direction (26 November 2026): layer the app. A free tier with no AI that is valuable on its own and that a parent would share with other parents, then two paid tiers that add chargeable AI features.

**Proposed split**

| Tier | For | Contains | Running cost |
| --- | --- | --- | --- |
| 1. Free, no AI | Any parent, no sign-up | The quizzes and printable handouts for every skill, hints, explanations, review, the fun layer (daily five, streak, puzzle), progress saved on the device, and the child's most common slip shown on screen. | Close to nothing: static pages. |
| 2. Paid | Parents who want to follow progress | A parent account, more than one child, progress across devices, the weekly report, tracing mistakes back to the earlier skill, mastery checks weeks later, the weekly printed page, and the parent script per slip. | Low: a database, email, and light AI at most for wording the weekly note. |
| 3. Paid, higher | Parents who want it fitted to their child | Practice from a photo of homework, explain it back, and the tutor that asks questions. | Real cost per use. |

**Why this split**

- The free tier costs almost nothing to serve, so sharing it widely is safe. With no accounts it also collects no data about children, which is a selling point and avoids the privacy rules until tier 2.
- Tier 2 is where the parent angle lives, and most of it does not need AI. Charging for it funds the product before any AI cost is taken on.
- Tier 3 carries the per-use cost, so it should have monthly limits (for example a set number of homework photos) and a price set from measured cost.

**Risks to watch**

- If the free tier is thin, nobody shares it. If it is complete, nobody upgrades. The line proposed here: the child's practice is free and complete; the parent's view is paid.
- The free tier shows the most common slip on screen as a taste of the report. The trend over weeks and what to do about it are paid.
- Two paid tiers can confuse buyers. Launch with free plus tier 2, and add tier 3 once people are paying and asking for more.
- Prices are not set. Test them with the first families.

## Is it a product?

Possibly, with a narrow angle.

**For it**

- Parents already pay for maths help, and the parent is the buyer.
- The method carries across grades.
- Adding a skill means writing one generator and its list of typical mistakes, not a question bank.

**Against it**

- Khan Academy is free, and IXL, Prodigy and Mathletics already cover every grade. "Adaptive maths practice by grade" does not stand out on its own.
- Children stop coming back. Keeping them is harder than teaching them.
- Parents expect it to match school, and curricula differ by country and region.
- Accounts for children under 13 bring privacy rules (COPPA in the US, similar elsewhere).

**The opening:** sell to the parent. The quiz already knows which mistake a child keeps making. A weekly note such as "solid on taking out common factors, keeps getting signs wrong in three-term problems, here is a two-minute way to explain it" is something mainstream products do not report clearly. The "why it works" explanations also help parents who have forgotten the maths.

## Tracking usage

The quiz records nothing beyond the learner's own browser. Two routes were identified; neither is built.

- **Shared page, signed-in Claude users only.** The page itself can save each person's attempts and show the owner a results view. People need permission to interact, not just view.
- **Public audience.** Needs a small website with a database. Supabase and Vercel are already connected, so it could be hosted there, either anonymously (totals and averages) or with a name or email asked at the start.

Suggested measures either way: number of people, questions answered, percent correct per level, and which slip kinds are most common.

## If this is picked up

1. Choose one grade band and about ten skills (for example ages 11 to 13: fractions, negative numbers, simple equations).
2. Put it on a real site with a parent sign-up and the weekly report.
3. Give it to 10 to 20 families.
4. Watch two numbers: do children come back in week three, and do parents open the report.

If both hold, expand grade by grade. If children drop off, the report alone will not carry it.

## Open questions

- Who is the first audience: people already in the eBiz123s community, or parents found some other way?
- Which country's curriculum comes first?
- Does the child sign in, or only the parent?
- Free with a paid report, or paid from the start?
