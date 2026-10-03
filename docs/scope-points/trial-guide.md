# Scope Points Trial Guide

!!! info "Status"
    Superseded by Task Points; kept for research history.

    Lineage: Scope Points (earlier sizing model), draft trial guide for team review (a four-sprint trial with AI use and complexity tags).

## Why

The question is whether AI is making the team faster. Estimates in days shrink as AI shortens the work, and estimate / actual stays at 1.0. Scope Points size **what a story delivers**, not how long it takes, so the size stays fixed and the speed-up becomes visible.

| Same story | Estimate (days) | Actual (days) | Scope Points | Points per day |
|---|---|---|---|---|
| Before AI | 10 | 10 | 10 | 1.0 |
| With AI | 4 | 4 | 10 | 2.5 |

Nothing else changes: sprint planning, estimates and the issue tracker stay as they are.

## How to size a story

List what the story adds or changes, give each item a size from the table, and add them up. An AI sizer drafts it; the developer checks it at refinement.

| Item | What you count | Small = 1 | Medium = 3 | Large = 5 | Split above |
|---|---|---|---|---|---|
| Screen (form, dialog, menu) | Fields, buttons, grid columns | 1-4 | 5-15 | 16-30 | 30 |
| Rule (validation, calculation, logic) | Conditions or calculated values | 1-3 conditions | 4-8 conditions or 1-2 values | 9-16 conditions or 3-5 values | 16 conditions or 5 values |
| Data (tables, columns, upgrade scripts) | Columns | 1-4 | 5-15, or a new table | 16-30 | 30 |
| Output (report, print, import/export) | Fields | 1-5 | 6-19 | 20-40 | 40 |
| External call (another system) | Operations | n/a | 1 | 2-5 | 5 |
| Technical (migration, refactor, crash, speed, security) | Screens or functions affected | 1 setting or error case | 2-5 settings, or 1 function | 2-5 functions | 5 functions |

The "Split above" column is the limit above which the item is split (for example, a screen over 30 fields, an output over 40 fields, or a technical item over 5 functions).

1. **Count only what changes.** On a new screen or report every field counts; on an existing one, only added or changed fields.
2. **Tables used.** A Screen or Output that uses only one business table (customer, order, ...) goes one size down; one that combines many (Screen 3+, Output 4+) goes one size up.
3. **Where the code sits does not matter.** A query that fills a screen is part of that Screen; logic in a stored procedure is a Rule.
4. **Over the split limit?** Split the item. A story over **13 points** is split into smaller stories along its items; the total stays the same.
5. **Size is fixed at Ready.** New scope becomes a new story; dropped scope is subtracted.
6. **Bugs.** A bug in code the team changed during the trial scores 0 (its hours count as rework); any other bug is sized normally.

## Example

??? example "Story: add a discount to sales orders, applied before sales tax and shown on the print = 8 points"

    | Item | Kind and size | Points |
    |---|---|---|
    | Discount field on the order form (1 field) | Screen, Small | 1 |
    | Discount applied to net, sales tax and total (4 calculated values) | Rule, Large | 5 |
    | Discount column in the order table | Data, Small | 1 |
    | Discount on the printed order | Output, Small | 1 |
    | **Total** | | **8** |

## What we track

One result, two checks. Hours come from the timesheets the team already fills in, so developers only add the ticket number.

| Measure | How | Healthy when |
|---|---|---|
| **Speed** (the result) | Points delivered / developer days, compared with the baseline for the same kind of work (feature, bug, data, modernization) | Higher than baseline |
| **Quality** | Bugs caused by the team's own changes per 100 points, and share of hours spent on rework | Not rising |
| **Sizing check** | Each sprint, 2 finished stories are re-sized by hand by 2 developers | Within 20% of the recorded size |

Each ticket also gets two tags, used only to compare like with like: **AI use** (none, assisted, agent-led) and **complexity** (low, medium, high). Tags never change the points.

## Trial plan: 4 sprints

The baseline is built from work already finished, so the trial starts measuring from sprint 1.

| When | What | Done when |
|---|---|---|
| Week 0 | 2-3 developers size 10 recent stories by hand; the AI sizer sizes the same 10 | 8 of 10 totals within 20% (otherwise clarify the rules and repeat) |
| Week 0 | The AI sizer sizes the stories finished in the last 2-3 sprints; hours come from the timesheets | At least 30 tickets in the baseline |
| Sprints 1-4 | Size every story before Ready; tag AI use and complexity at merge | Every story sized |
| End of each sprint | Compare the last 2 sprints with the baseline | Report shared with the team |
| After sprint 4 | Decide: keep, adjust or stop | Decision recorded |

**How to read it:** a single report can move by chance. Trust a change only when it shows in two reports in a row and quality is not worse. A short trial reliably shows only large changes (about 1.4x or more); smaller gains need more sprints.

If past stories lack clear requirements, the baseline is built live in sprints 1-2 instead and the comparison starts in sprint 3.

## Roles, tools and use

| Who | Does | Time |
|---|---|---|
| Developer | Runs the AI sizer, checks the draft, flags anything wrong; adds the ticket number to timesheet entries; tags AI use and complexity at merge | About 5 min per story |
| Team lead | Settles flagged sizes (if still unsure, the smaller size wins); runs the sizing check; updates the points sheet and shares the sprint report | About 30 min per sprint |

- **Tool:** a coding agent with the shared sizing prompt. Use one full-size model and keep it for the whole trial; changing it mid-trial shifts the sizes.
- **Records:** one sheet, a row per story: ticket, points, work type, tags. The issue tracker and timesheets stay as they are.
- **Use:** results are for the team, to see whether the process is improving. They are never used to rate individuals, set targets or compare teams.

## FAQ

??? question "Why do complexity, risk, uncertainty or testing not add points?"
    They change how long work takes, not what it delivers, so they show up in hours. If they added points, work that AI makes easier would still score as hard and the gain would disappear. System impact is counted: every screen, function or table changed is an item. The complexity tag lets the team compare hard work with hard work.

??? question "Do we stop estimating for sprint planning?"
    No. Keep estimating as before for planning. Scope Points are only for measuring.

??? question "A small fix touches 30 files. Is it still small?"
    Yes. Points follow what changes for the user; the extra effort shows in hours.

??? question "Do investigation, meetings, code review and writing tests earn points?"
    No. Their hours are logged to the story, so time saved on them shows as higher speed.

??? question "Is a particular coding agent required?"
    No. The sizer is a prompt and works with any capable model. Pick one, check it in Week 0, and keep it for the trial.

## Related pages

- [Team Guide](team-guide.md)
- [Sizing and Crediting](sizing-and-crediting.md)
- [Proposal](proposal.md)
