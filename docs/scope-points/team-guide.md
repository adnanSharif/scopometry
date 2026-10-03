# Scope Points Team Guide

!!! info "Status"
    Superseded by Task Points; kept for research history.

    Lineage: Scope Points (earlier sizing model), short team-facing guide with development and QA crediting. Full rules are in [Sizing and Crediting](sizing-and-crediting.md).

The aim is to measure the team's productivity: how much the team delivers for the effort it spends, from requirement to QA pass, and how that changes over time. Estimates in days cannot show this, because they shrink as the team gets faster. So the team sizes **what each story delivers** in Scope Points, and takes effort from the timesheets it already fills in. Productivity is points per developer and QA day, compared with the team's own baseline. Sprint planning, estimates and the issue tracker stay as they are.

## 1 How to size a story

List what the story adds or changes, give each item a size from the table, and add them up. Before a story is Ready, the AI sizer drafts this and a developer checks it; the team lead settles any disagreement, and the smaller size wins if still unsure. If the sizer asks a question whose answer could change the size (for example, whether a report needs a totals row), get the answer from the product owner and size the story again before marking it Ready.

| Item | Count | Small = 1 | Medium = 3 | Large = 5 | Split above |
| --- | --- | --- | --- | --- | --- |
| **Screen**: form, dialog, menu | Fields, buttons, grid columns | 1-4 | 5-15 | 16-30 | 30 |
| **Rule**: validation, calculation, logic | Conditions or calculated values | 1-3 conditions | 4-8 conditions, or 1-2 values | 9-16 conditions, or 3-5 values | 16 conditions or 5 values |
| **Data**: tables, columns, upgrade scripts | Columns | 1-4 | 5-15, or a new table | 16-30 | 30 |
| **Output**: report, print, import or export | Fields | 1-5 | 6-19 | 20-40 | 40 |
| **External call**: another system | Operations | 1 | 2-3 | 4-6 | 6 |
| **Technical**: migration, refactor, crash, speed, security | Settings, error cases or functions affected | 1 setting or error case | 2-5 settings, or 1 function | 2-5 functions | 5 functions |

The "Split above" column is the limit above which the item is split.

1. **Count only what changes.** On a new screen or report every field counts; on an existing one, only added, changed or removed fields.
2. **Tables used.** A Screen or Output using one business table goes one size down; one combining many (Screen 3+, Output 4+) goes one size up.
3. **Where the code sits does not matter.** A query that fills a screen is part of the Screen; logic in a stored procedure is a Rule.
4. **Split, do not cap.** Split an item over its limit. Split a story over **13 points** along its items; the total stays the same.
5. **Size is fixed at Ready.** New scope is a new story; dropped scope is subtracted.
6. **Effort never adds points.** Complexity, risk, investigation, code review and testing show up in hours, not points.

??? example "A password-change story sized from its acceptance criteria (9 points)"
    Story: "As a user, I can change my password." Acceptance criteria:

    1. The Settings menu has a "Change password" entry that opens a dialog with current password, new password, confirm password, Save and Cancel.
    2. The current password must be correct.
    3. The new password has at least 8 characters and contains a number.
    4. The new and confirm passwords must match.
    5. The new password must differ from the last 3 passwords used; password history is not stored today.
    6. After a successful change, the user gets a confirmation email through the company email service.

    Sizing prompt output:

    | Item | From criteria | Count | Size | Points |
    | --- | --- | --- | --- | --- |
    | "Change password" entry on the Settings menu | 1 | 1 field, 1 table (users) | Screen, Small | 1 |
    | Change-password dialog | 1 | 5 fields, 1 table (users): Medium, one size down | Screen, Small | 1 |
    | Password checks | 2-5 | 5 conditions: current password, length, number, match, not recently used | Rule, Medium | 3 |
    | Password history | 5 | A list per user, so a new table | Data, Medium | 3 |
    | Confirmation email | 6 | 1 operation with the email service | External call, Small | 1 |
    | **Story size** | | | | **9** |

## 2 How points are credited

A story's points are counted once, in two fixed shares: the **development share** when the code is merged and the story moves to QA, and the **QA share** when it passes QA. The split follows the team's make-up: QA share = QA members / all members. For example, a team of 3 developers and 2 QA engineers gives 60% for development and 40% for QA.

| A 10-point story, team of 3 developers and 2 QA (60% and 40%) | Sprint 5 | Sprint 6 | Total |
| --- | --- | --- | --- |
| Developers finish; story moves to QA | 6.0 | n/a | 6.0 |
| QA tests; story passes | n/a | 4.0 | 4.0 |
| **Story** | 6.0 | 4.0 | 10 |

- **Returned by QA:** no extra points; the fix and retest hours still count.
- **Developed by another team, tested by the team's QA:** the team is credited the QA share only.
- **No QA step:** full points when Done.

## 3 FAQ

??? question "A small fix touches 30 files. Is it still small?"
    Yes. Points follow what changes for the user, not the amount of code. The extra effort shows up in hours.

??? question "Why do complexity, risk or uncertainty not add points?"
    They change how long the work takes, not what it delivers, so they show up in hours. If they added points, work that gets easier over time would still score as hard, and the improvement would not show.

??? question "Do code review, investigation or writing tests earn points?"
    No. They are part of delivering the story, so their hours are logged to it. Time saved on them shows as higher productivity.

??? question "How are bugs counted?"
    A bug found after QA pass that the team's own change caused during the trial scores 0 points; its hours count as rework. Any other bug is sized like a normal change.

??? question "What if the requirement changes after the story is Ready?"
    The size stays as it was at Ready. New scope becomes a new story and is sized on its own; dropped scope is subtracted.

??? question "Do we stop estimating for sprint planning?"
    No. Keep estimating as before. Scope Points are only for measuring productivity.

## Related pages

- [Sizing and Crediting](sizing-and-crediting.md) for the full rules, formulas and sizing prompt
- [Trial Guide](trial-guide.md) for the short trial plan
- [Proposal](proposal.md)
