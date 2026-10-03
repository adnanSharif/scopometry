# Scope Points Pre-mortem

!!! info "Status"
    Superseded by Task Points; kept for research history.

    Lineage: Scope Points (earlier sizing model), pre-mortem companion to the [Proposal](proposal.md). The amendments below were proposed against an earlier draft of the proposal and were not applied to that draft at the time; several are reflected in the later [Proposal](proposal.md) (for example the capacity check, the 13-point cap, baseline minimums and frozen instruments).

## How Scope Points could fail

Imagine it is sprint 9 and the trial has failed, or worse, produced a **confident but wrong** number. This page lists how that could happen, the early warning signs, and what to do now so it does not.

| Count | What |
|---|---|
| 18 | Failure scenarios in 5 groups |
| 2 | High likelihood and high damage |
| 10 | Amendments to make before sprint 1 |
| 5 | Stop rules that pause the trial |

## Bottom line

**The method's logic holds. Its inputs and incentives are where it breaks.**

Most failures are not maths errors. They come from hours that are not really measured, people reacting to how the number might be used, and other changes being credited to AI. These three matter most:

1. **B1 (Hours): timesheets fill the day, not the task.** If hours are allocated to match billing, time saved by AI never shows. **Fix:** add points per available person-day as a second headline. It does not depend on ticket hours.
2. **D1 (Attribution): other changes get credited to AI.** Migration phases, new people and tooling all move productivity. **Fix:** call it a productivity gain, and print a change log on every snapshot.
3. **A1 + A2 (Incentives): the number becomes a target, or a threat.** If the number can drive appraisals or headcount, people protect it. **Fix:** a written use-of-results agreement before sprint 1.

## Risk map: where each scenario sits

Act before sprint 1 on the high-likelihood, high-damage scenarios. Build prevention into the process for the high-damage and the high-likelihood ones. Watch the rest.

| Likelihood \ Damage | Low damage | Medium damage | High damage |
|---|---|---|---|
| **High** | A4 (the AI tag stops meaning anything) | A3 (small breakdowns expose individuals), C3 (one big ticket swings a period), D3 (expectations were set against "before AI"), E1 (process discipline fades) | **B1** (timesheets fill the day, not the task), **D1** (other changes get credited to AI) |
| **Medium** | C5 (the Large bucket is too wide), E3 (overhead creeps up) | B2 (hours move off the tickets), B3 (saved time is absorbed), C2 (the "own bug" rule drifts), E2 (too slow to prove, support fades) | A1 (the number becomes a target), A2 (fear that gains will cut the team), C1 (AI drafting inflates the sizes), C4 (a thin or unusual baseline), D2 (the team changes) |
| **Low** | none | none | none |

## Group A: People and incentives

The number changes how people behave, and the new behaviour then changes the number.

### A1. The number becomes a target

Likelihood: Medium. Damage: High.

**What:** Management asks for 2x by year end, or points per day show up in appraisals. Medium items quietly become Large, and borderline bugs are called "old" rather than "ours".

- **Why it fails:** Once a measure becomes a target, people optimise the measure instead of the work (Goodhart's law). Points are judgement calls, so they bend first.
- **Early warning:** The blind re-size gap trends upward. Average points per story rise while the stories look no different.
- **How to avoid it:** Get a written agreement before sprint 1: no targets, no use in appraisals, team level only.
- **If it happens anyway:** Stop making claims. Re-size the affected period against the reference stories and restate the result.

### A2. Fear that gains will cut the team

Likelihood: Medium. Damage: High.

**What:** The team suspects a proven gain will let stakeholders cut headcount or reduce funding. People log time generously, and AI use is under-reported.

- **Why it fails:** The people who produce the data have a stake in what the data implies about their jobs.
- **Early warning:** Hours per point stop falling although work visibly finishes faster. AI tags shift after budget conversations.
- **How to avoid it:** Agree in writing how gains will be used (for example, reinvested in modernization and backlog) and that trial figures stay internal until reviewed.
- **If it happens anyway:** Pause external reporting and restate the use-of-gains agreement with the team.

### A3. Small breakdowns expose individuals

Likelihood: High. Damage: Medium.

**What:** Only two people do data upgrades, so the "data upgrades 1.1x" bar is really their personal score, and everyone knows it.

- **Why it fails:** The team-only promise is kept in how results are presented, not in how finely the data is split. In a team of about 10 (an illustrative size), many slices are one or two people.
- **Early warning:** Someone says: "that chart is basically just me."
- **How to avoid it:** Hide any breakdown with fewer than 3 contributors in the period. Merge it into "other".
- **If it happens anyway:** Remove the breakdown from the published snapshot. Recompute at a coarser level.

### A4. The AI tag stops meaning anything

Likelihood: High. Damage: Low.

**What:** Tags are bulk-ticked from memory at sprint end, or everyone picks "Agent-led" because leadership is pushing AI.

- **Why it fails:** A self-reported tag with no evidence behind it drifts toward what people think is wanted.
- **Early warning:** Tags are entered in batches days after close. The share of Agent-led jumps with no change in tooling.
- **How to avoid it:** Set the tag when the PR is merged, based on evidence: Agent-led only if the PR description says an agent wrote most of the change. Spot-check 5 per month.
- **If it happens anyway:** Treat the AI breakdown as unreliable for that period. The headline figure is unaffected because it does not use tags.

## Group B: Hours data

Points are only half the ratio. If the hours are wrong, the whole ratio is wrong.

### B1. Timesheets fill the day, not the task

Likelihood: High. Damage: High.

**What:** Timesheets double as billing or cost-recovery data, so every day is logged at 8 hours. When AI saves half a day, the half day is still logged against the ticket. Hours per ticket barely fall, and the productivity figure stays flat.

- **Why it fails:** The method assumes hours are measured. In many organisations they are partly *allocated*, to match estimates, utilisation or cost recovery.
- **Early warning:** Logged hours closely match estimates. Hours per point stay flat while points finished per sprint rise.
- **How to avoid it:** Make points per **available** person-day (capacity minus leave) a second headline. It needs no ticket hours, so padding cannot hide gains. Once per period, compare a sample of ticket hours with commit and PR activity.
- **If it happens anyway:** Report the capacity-based figure only, and fix the logging guidance before the next period.

### B2. Hours move off the tickets

Likelihood: Medium. Damage: Medium.

**What:** Review, investigation and rework get logged to "general" or "meetings" instead of the ticket. Tickets look cheaper and productivity looks higher than it is.

- **Why it fails:** Once people know hours per ticket are watched, hours that make a ticket look bad drift elsewhere.
- **Early warning:** The share of hours with no ticket rises.
- **How to avoid it:** Keep hours with no ticket at or below 10% of logged hours. Report it next to the headline figure.
- **If it happens anyway:** Mark the period as unreliable. Use the capacity-based figure, which counts all available time.

### B3. Saved time is absorbed

Likelihood: Medium. Damage: Medium.

**What:** AI saves time, but sprint commitments do not change. The spare time goes into polishing, extra refactoring, or waiting, because the backlog is thin.

- **Why it fails:** Work expands to fill the time available (Parkinson's law). If nobody pulls more work in, the gain turns into slack, not output.
- **Early warning:** Sprints finish early, or the same amount is committed every sprint. Hours with no ticket go up.
- **How to avoid it:** Pull more work into sprints as speed rises. Management decides in advance what freed capacity goes to, such as modernization or tech debt.
- **If it happens anyway:** Report the freed capacity explicitly: the gain is real but unused. That is a planning decision, not a measurement failure.

## Group C: Measurement mechanics

Small rule gaps that bend the number without anyone intending it.

### C1. AI drafting inflates the sizes

Likelihood: Medium. Damage: High.

**What:** A newer model or an edited prompt finds more items in the same ticket: an extra Rule here, a Data item there. The same feature grows from 8 to 11 points, and productivity appears to rise.

- **Why it fails:** The sizing instrument changed while it was measuring. It is like recalibrating a scale during the weigh-in.
- **Early warning:** Items per story rise over time. The AI draft disagrees with the blind human re-size in one direction.
- **How to avoid it:** Freeze the prompt, model version and size table for the trial. After any unavoidable change, re-size 10 reference stories. Accept the change only if totals move by 10% or less.
- **If it happens anyway:** Re-size the affected period with the original prompt, or restate it using the drift factor from the reference stories.

### C2. The "own bug" rule drifts

Likelihood: Medium. Damage: Medium.

**What:** A new tech lead reads "recent" as "this sprint". Also, a bug in AI-written code found in month 7 falls outside the 6-month window and earns points as an "old" bug.

- **Why it fails:** The rule depends on judgement and a time window. AI-written code can fail late, and the window turns that late failure into credit.
- **Early warning:** The share of bugs classed as "own" falls while escaped defects stay the same.
- **How to avoid it:** Change the rule to: code changed by the team since the trial started, per git blame, counts as the team's own at any age. Write it down and include classifications in the blind audit.
- **If it happens anyway:** Re-classify the period with the written rule and restate it.

### C3. One big ticket swings a period

Likelihood: High. Damage: Medium.

**What:** A 40-point migration closes in sprint 8 with all its hours. The current period swings up or down on that one ticket, and its single AI tag covers three sprints of mixed work.

- **Why it fails:** With 30-50 tickets per period, one very large ticket can dominate the totals.
- **Early warning:** The largest ticket holds more than 15% of the period's points or hours.
- **How to avoid it:** Cap stories at 13 points and split larger ones along item boundaries, which is already point-neutral. Show the result with and without the 3 largest tickets.
- **If it happens anyway:** Report both versions. If they disagree on the verdict, call it no clear change.

### C4. A thin or unusual baseline

Likelihood: Medium. Damage: High.

**What:** The baseline sprints hit a release crunch and were mostly urgent bugs, with only 2 data-upgrade tickets. Every later comparison inherits that distortion, and the data-upgrade ratio swings wildly.

- **Why it fails:** Everything is measured against the baseline. A small or unusual baseline makes every later result unreliable.
- **Early warning:** Fewer than 5 tickets of a work type in the baseline, or a known unusual event in those sprints.
- **How to avoid it:** Require at least 30 tickets in total and at least 5 per work type, extending the baseline if needed. Exclude the practice week. Record unusual events.
- **If it happens anyway:** Extend the baseline by one sprint, or merge the thin work type into "other".

### C5. The Large bucket is too wide

Likelihood: Medium. Damage: Low.

**What:** "Large Rule" covers a 1-day tax-rate tweak and a 2-week end-of-period processing rewrite. If a period happens to have more of the huge ones, the team looks slower.

- **Why it fails:** Three sizes are deliberately coarse. Coarseness averages out only if the mix inside each bucket is stable.
- **Early warning:** Hours per Large item spread by more than 3x between periods.
- **How to avoid it:** At the month-6 review, add an XL = 8 size if Large items vary too much. Until then, watch the hours spread.
- **If it happens anyway:** Note it in the report. Re-size the obvious extra-large items as XL at month 6 and restate the history.

## Group D: Attribution

The number is right, but AI is credited for something else.

### D1. Other changes get credited to AI

Likelihood: High. Damage: High.

**What:** The platform migration reaches an easy phase, a senior developer joins, the CI pipeline gets faster, and requirements improve. Productivity rises to 1.6x and the report says "AI gain".

- **Why it fails:** The method measures productivity, not its cause. Several things change at once in a real team.
- **Early warning:** The gain lines up with programme milestones or roster changes rather than with the mix of AI tags.
- **How to avoid it:** Call it a "productivity gain", not an "AI gain". Keep a change log (people, tools, programme milestones) and print it on every snapshot. Show the result with modernization included and excluded.
- **If it happens anyway:** Restate the claim with the change log beside it. Use the AI-tag breakdown only as supporting evidence.

### D2. The team changes

Likelihood: Medium. Damage: High.

**What:** Between the baseline and sprints 7-9, three of ten developers rotate off and are replaced by less experienced engineers who are still ramping up.

- **Why it fails:** "The team's own baseline" assumes the same team. With more than 20% turnover, the comparison is partly seniority, not method.
- **Early warning:** Productivity swings track joining and leaving dates.
- **How to avoid it:** Log the roster every sprint. Report onboarding hours (first 4 weeks) separately. Flag any comparison with more than 20% roster change, and re-baseline above 30%.
- **If it happens anyway:** Re-baseline, or report the result with a clear roster-change caveat.

### D3. Expectations were set against "before AI"

Likelihood: High. Damage: Medium.

**What:** Management expects 2-4x, but the team already used AI during the baseline. The confirmed result is 1.3x against the baseline, and the reaction is "AI isn't working".

- **Why it fails:** The proposal measures progress *from now*. Gains already made before the baseline are invisible to it.
- **Early warning:** Early conversations quote pre-AI hopes against post-baseline numbers.
- **How to avoid it:** State in the approval that the baseline already includes AI. Optionally, present a clearly labelled estimate of the gain before the baseline.
- **If it happens anyway:** Re-frame the result: measured gain since the baseline, plus the estimated earlier gain, shown separately.

## Group E: Process and adoption

The method works on paper but fades out or loses support in practice.

### E1. Process discipline fades

Likelihood: High. Damage: Medium.

**What:** By sprint 6, sizing is done after the work is finished, when the effort is already known, and tags and entries are made in batches from memory.

- **Why it fails:** No one owns data quality itself. Sizing after the fact leaks effort into size, which is exactly what the method forbids.
- **Early warning:** Sizing is dated after work started. Entries are made in batches.
- **How to avoid it:** Require sizing before a ticket can move to In Progress. The engineering lead checks entry dates monthly, not just totals.
- **If it happens anyway:** Exclude late-sized tickets from the period and restate it.

### E2. Too slow to prove, support fades

Likelihood: Medium. Damage: Medium.

**What:** The real gain is about 1.2x, which needs more than 9 sprints to confirm. At sprint 9 the verdict is still "no clear change", and the trial is dropped.

- **Why it fails:** Small gains with a small team are statistically slow to prove. In simulation, a real 1.2x is confirmed only about half the time within two periods.
- **Early warning:** Early signal at sprints 4-6, but a range that still reaches close to 1.0x.
- **How to avoid it:** Agree up front that "no clear change" at sprint 9 means extend, not fail, as long as the early signal is positive.
- **If it happens anyway:** Extend by one or two periods. Look at the per-work-type ranges for where the gain concentrates.

### E3. Overhead creeps up

Likelihood: Medium. Damage: Low.

**What:** Refinement turns into debates about Medium versus Large, and bug classification arguments add meetings. The "under 1%" becomes 3-4%, and the team resents it.

- **Why it fails:** Any sizing scheme invites debate unless someone decides quickly.
- **Early warning:** Sizing takes more than 15 minutes per story. People complain in retrospectives.
- **How to avoid it:** Two-minute rule: if people disagree, pick the smaller size and move on, and the tech lead decides. Time the process in sprint 1 and publish the figure.
- **If it happens anyway:** If it exceeds 2% of team time, simplify further, for example by having the tech lead size alone from the AI draft.

## 10 amendments to make before sprint 1

Proposed changes to the proposal as it stood when the pre-mortem was written. Together they close the high-damage scenarios.

| # | Amendment | Closes | Extra effort |
|---|---|---|---|
| 1 | **Use-of-results agreement**, signed off with the proposal: no targets, no appraisal use, no headcount decisions based on trial figures, no external use before a joint review, and gains reinvested in agreed priorities. | A1, A2 | One meeting |
| 2 | **Second headline: points per available person-day** (capacity minus leave). It does not need ticket hours, so padding or hours moving off tickets cannot hide gains. | B1, B2, B3 | None: available days are already known |
| 3 | **Freeze the instruments**: prompt, model version, size table and bug rule, each with a version stamp. After any change, re-size 10 reference stories and accept only drift of 10% or less. | C1 | About 1 hour per change |
| 4 | **New "own bug" rule**: code changed by the team since the trial started (git blame) counts as the team's own, at any age. | C2 | None |
| 5 | **Story cap of 13 points**, split on item boundaries. Show results with and without the 3 largest tickets. | C3 | None |
| 6 | **Baseline minimums**: at least 30 tickets and at least 5 per work type, practice week excluded, unusual events recorded. | C4 | Possibly one extra sprint |
| 7 | **Change log and roster log** printed on every snapshot. Onboarding hours reported separately. Re-baseline after more than 30% roster change. | D1, D2 | 5 min per sprint |
| 8 | **Wording and expectations**: say "productivity gain", not "AI gain". State in writing that the baseline already includes AI, and that "no clear change" at sprint 9 means extend, not fail. | D1, D3, E2 | None |
| 9 | **Privacy floor**: hide any breakdown with fewer than 3 contributors. | A3 | None |
| 10 | **Entry discipline**: size before In Progress; set the AI tag at PR merge from evidence; check entry dates monthly; two-minute rule for sizing disputes. | A4, E1, E3 | About 10 min per month |

## Stop rules: when to pause the trial and fix it

Agreed in advance so that pausing is a rule, not a debate. A pause means fixing the cause and restating the affected period, not abandoning the trial.

1. **Overhead above 2% of team time** in sprint 1 or 2. Simplify before continuing.
2. **Blind re-size differs by more than 20%** in two sprints running. Stop claims and re-align on the size table.
3. **Hours with no ticket above 15%** of logged hours in a period. Fix logging, and use only the capacity-based figure for that period.
4. **Roster change above 30%** since the baseline. Re-baseline.
5. **The figure is used as a target, in appraisals, or externally** before it is confirmed. Stop and reset the use-of-results agreement.

## Early-warning signals: what to watch

| Signal | Healthy | Act when | Checked | Catches |
|---|---|---|---|---|
| Blind re-size gap | within +/-10% | more than 10% in one direction twice | Every sprint | A1, C1 |
| Average points per story (same kind of work) | stable | up more than 15% with no change in requirements | Every period | A1, C1 |
| Hours with no ticket | 10% or less | above 15% | Monthly | B2, B3 |
| Logged hours vs estimate | varies | logged hours match estimates on most tickets | Monthly sample | B1 |
| Ticket-hours gain vs capacity gain | similar | differ by more than 0.3x | Every period | B1, B2, B3 |
| Share of bugs classed as "own" | stable | falls while escaped defects hold | Every period | C2 |
| Largest ticket's share of a period | 15% or less | above 15% | Every period | C3 |
| Roster change since baseline | 20% or less | above 20% flag, above 30% re-baseline | Every sprint | D2 |
| Entries made late or in batches | rare | more than 10% of tickets | Monthly | A4, E1 |
| Process time | under 1% | above 2% | Sprint 1, then quarterly | E3 |

## Method: how this was produced

Three independent pre-mortems were merged: one on people, incentives and attribution (a mid-tier model), one on measurement mechanics (a small model), and a direct review of the proposal and its earlier simulation. Overlapping findings were combined. Findings that the existing proposal already handles, such as story counts being affected by splitting, were dropped. Likelihood and damage are judgement ratings for an illustrative team of about 10 on a mature product with legacy code.

## References

| Source | Used for |
|---|---|
| Goodhart's law | A1: a measure that becomes a target stops being a good measure |
| Parkinson's law | B3: work expands to fill the time available |
