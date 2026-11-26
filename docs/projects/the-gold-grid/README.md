# The Gold Grid

A maths skill trainer for children and their parents. It teaches one trick at a time, practises until each fact sticks, and shows progress as a grid of squares that turn gold. The first skill is times tables, with division as the same facts in reverse.

**Status (27 November 2026):** project started. A working prototype exists as a single page. Nothing is on the eStage site yet, and no domain is registered.

## Where things are

| Thing | Where | State |
| --- | --- | --- |
| eStage project | Genesis project 80750, connector name "The Gold Grid" | Blank: one Home page, nothing built or published. |
| Trainer prototype (times and divide) | https://claude.ai/artifact/TLxZsJjW3UiLMs8Jqcipzx | Private until shared from the page. Source in [`prototypes/times-tables.html`](prototypes/times-tables.html). |
| Factoring quiz (earlier prototype) | https://claude.ai/artifact/JzNExJ3C44JfAbsyW63d4E | Source in [`prototypes/factoring-quiz.html`](prototypes/factoring-quiz.html). |
| Factoring handout | https://claude.ai/artifact/GHAF13oZWY1AATzNfindcm | Source in [`prototypes/factoring-tutorial.html`](prototypes/factoring-tutorial.html). |
| Domain | Not registered. `thegoldgrid.com` was free on 27 November 2026; `knowyourtimes.com` was free as a second address. | Waiting on the owner. |
| These documents | `docs/projects/the-gold-grid/` in the Base-Code repository | Kept here until the project has a repository of its own. |

## The product in brief

**Who it is for:** children learning times tables and division, with a parent alongside.

**What makes it different:** it teaches a strategy for each table instead of drilling against a clock, it names the kind of mistake a child makes, and (in the paid tier) it shows the parent which facts are weak and how to help.

**Tiers**

| Tier | What it is | State |
| --- | --- | --- |
| 1. Free | No sign-up, no AI. The whole trainer, with progress saved on the device. Meant to be shared between parents. | Prototype built. |
| 2. Paid | The memory layer: parent and child sign-ons, progress saved across devices, progress graphed for the parent, a weekly report. Priced per family with a free trial; price to be tested. | Not started. |
| 3. Paid, premium | AI features with monthly limits, such as practice from a photo of homework. Waits until there are more skills. | Not started. |

## What the prototype does

- **Times and Divide**, each with its own grid, levels, best time and "facts to help with" list.
- **13 times levels and 12 divide levels**, in an order where each trick builds on the last.
- **A trick card** at the start of each level, with examples and a dot picture.
- **Multiple choice first**, then typing the answer after two right in a row.
- **A hint** that nudges without giving the answer.
- **Feedback on a miss:** the answer, the kind of slip, the trick worked through, and a second way where one exists.
- **The grid:** a fact turns gold after three right answers without a hint, with other questions in between. Gold facts come back for review and fade if missed.
- **Today's ten** and a streak with one free skip day a week.
- **Beat your time** for facts already gold.
- **A parent corner** with the five facts to help with.

## How to pick this up in a new session

1. Read this file, then [ROADMAP.md](ROADMAP.md) for the next step and [DECISIONS.md](DECISIONS.md) for what is settled.
2. The eStage connector for project 80750 must be connected to the session. Call its `genesis_context` first, as its instructions require.
3. The trainer source to port is [`prototypes/times-tables.html`](prototypes/times-tables.html). It is page content only: the publishing tool adds the `<html>`, `<head>` and `<body>` wrapper.
4. [BACKGROUND.md](BACKGROUND.md) has the full history and reasoning if a decision needs revisiting.

## Files

| File | Purpose |
| --- | --- |
| [README.md](README.md) | Current state. Update when something changes. |
| [ROADMAP.md](ROADMAP.md) | Phases, the next step, and open questions. |
| [DECISIONS.md](DECISIONS.md) | Dated log of what was decided and why. |
| [BACKGROUND.md](BACKGROUND.md) | How the idea developed, teaching ideas, product assessment. |
| [`prototypes/`](prototypes/) | Source of the three pages built so far. |
