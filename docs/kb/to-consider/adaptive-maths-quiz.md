# Adaptive maths quiz for parents, by grade

**Status:** to consider. A working prototype exists for one topic (factoring). Nothing has been built as a product.
**Recorded:** 26 November 2026

## The idea in one paragraph

A practice tool that teaches one maths skill at a time, explains why each method works, notices which specific mistake a child keeps making, and tells the parent about it in plain words. It would be organised by grade so a parent can pick their child's year and start.

## What exists today

| Item | Where | Notes |
| --- | --- | --- |
| Printable handout, "Factoring Step by Step" | https://claude.ai/artifact/GHAF13oZWY1AATzNfindcm | Private until shared from the page's Share menu. |
| Interactive quiz, "Factoring Quiz" | https://claude.ai/artifact/JzNExJ3C44JfAbsyW63d4E | Was shared as "Anyone with the link" when last published. |
| Source for both | [`adaptive-maths-quiz/`](adaptive-maths-quiz/) | Page content only. The publishing tool adds the `<html>`, `<head>` and `<body>` wrapper, so wrap the file before opening it directly in a browser. |

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
