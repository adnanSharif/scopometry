# Productivity Measurement with Scope Points

!!! info "Status"
    Status: Superseded; earlier iteration.

    Lineage: measurement half of the Scope Points trial proposal, written before the Dyno, Road & Destination method. Sizing and crediting are defined in the [sizing document](../scope-points/sizing-and-crediting.md). Kept for research history; see [Dyno, Road & Destination: a three-lens method](dyno-road-destination.md) for the later approach.

## 1 Purpose and inputs

This document defines how the team's productivity is measured with Scope Points: how much the team delivers for the effort it spends, and how that changes over time. Points come from the Scope Points sizing document; effort comes from developer and QA timesheets. Productivity is points per developer and QA day, compared with a baseline of the first three sprints.

### The process in five lines

1. **Developer:** size the story in Scope Points before work starts.
2. **During delivery:** developers and QA log effort to the ticket; release testing goes to its own code.
3. **Team lead:** collect points, effort, rework and quality in the register.
4. **Every three sprints:** compare like-for-like work with the baseline.
5. **Trust the result** only while sizing, quality and data checks stay healthy.

| Input | Definition | Source |
| --- | --- | --- |
| Credited points | Development share at dev done, QA share at QA pass (sizing document, section 2) | Register |
| Delivery hours | Developer hours up to dev done and QA hours up to QA pass, logged to the story and its sub-tasks | Timesheets |
| Rework hours | Hours after a stage is complete, on own bugs, or on abandoned work | Timesheets and register |
| Available days | Developer and QA working days minus leave | Roster |
| Own bugs | Bugs found after QA pass, caused by the team's change during the trial | Issue tracker and register |
| Release-testing hours | Hours on the release-testing code | Timesheets |

Results are team-level and compared only with the team's own baseline. The rules are fixed for the trial and reviewed at its end. The trial runs for nine sprints, needs no change to the issue tracker and takes about 0.3% of team time.

## 2 Formulas

Every figure in the report is calculated with the formulas below. Definitions and worked figures are in A.1.

**Symbols.**

- `q` = QA members ÷ (developers + QA members), fixed for the trial.
- `P` = points credited in the period; `D` = delivery person-days; `A` = available person-days.
- `b` = baseline period; `c` = current period; `t` = work type.
- `S` = eligible work types (at least 5 stories reaching QA pass in the current period).

| Measure | Formula | Note |
| --- | --- | --- |
| **Stage shares** | `Development share = size × (1 − q)`; `QA share = size × q` | Credited at dev done and at QA pass |
| **Points credited** | `P = Σ development shares at dev done + Σ QA shares at QA pass` | Full points at Done for a story with no QA step |
| **Delivery days** | `D = (frozen delivery hours of the stages completed + rework hours logged in the period) ÷ 8` | Rework goes to the work type of the ticket that caused it |
| **Speed** | `Speed_(t) = P_(t) ÷ D_(t)` | Per work type |
| **Productivity gain** | `Gain = D_(b,S) ÷ Σ_(t∈S) ( P_(b,t) ÷ Speed_(c,t) )` | The primary result. Equals Speed_(c) ÷ Speed_(b) when the work mix is unchanged |
| **Share of baseline time** | `Same work takes 1 ÷ Gain of the baseline time` | 1.6× → about 63% |
| **Likely range** | `100th and 1,900th of 2,000 re-sampled gains (A.1, how the verdict is calculated)` | The middle 90% |
| **Capacity check** | `(P_(c) ÷ A_(c)) ÷ (P_(b) ÷ A_(b)), where A = (developers + QA) × working days − leave days` | Independent of ticket hours |
| **Baseline hours per point** | `H_(t) = 8 × D_(b,t) ÷ P_(b,t)` | |
| **Hours saved** | `Σ (credited points × H_(t)) − frozen delivery hours − rework hours, over the eligible work types` | Matches D |
| **Role view** | `Development speed = development shares ÷ developer delivery days`; `QA speed = QA shares ÷ QA delivery days` | Read with the gain |
| **Own bugs** | `Own bugs found in the period ÷ P_(c) × 100`; by cohort: `own bugs traced to stories that passed QA in a period ÷ their points × 100` | Cohorts are mature two periods after they close |
| **Rework share** | `Rework hours ÷ all ticket hours` | |
| **Hours with no ticket** | `Developer and QA hours without a ticket number or release code ÷ all developer and QA hours, excluding planned non-delivery codes` | Pause above 15% |
| **Measurement overhead** | `Scope Points code hours ÷ available developer, QA and team-lead hours` | Pause above 2% |
| **Check sizing** | `Difference = \|recorded total − average check total\| ÷ recorded total`; `Reviewer spread = (highest − lowest check total) ÷ their average` | Pause if above 20% two sprints in a row; revise guidance if spread is above 30% two sprints in a row |
| **Release testing** | `Per release: hours, elapsed days, share of regression automated, and defects found after release ÷ points released × 100` | Outside the gain |
| **Team change** | `Developers and QA who joined or left ÷ baseline number` | New baseline above 30% |

## 3 What we measure

One result and seven checks. The checks show whether the result can be trusted; they are not targets. Formulas are in section 2.

| Measure | What it shows | Healthy when |
| --- | --- | --- |
| **Productivity gain** | How much faster developers and QA together deliver the same kind of work than in the baseline, adjusted for work mix. 1.6× means the same work takes about 63% of the baseline time. | This is the result |
| Quality | Own bugs (found after QA pass) per 100 points; share of hours spent on rework | Not rising |
| Sizing consistency | Two stories a sprint re-sized by hand | Within 20%; reviewers within 30% of each other |
| Capacity check | Points per available developer and QA day, independent of timesheets | Moves with the gain |
| Data quality | Hours with no ticket; carry-over; share of normal work covered | Hours with no ticket under 15% |
| Process overhead | Time spent on Scope Points work | Under 2% of developer, QA and team-lead time |
| Role view | Development shares ÷ developer days; QA shares ÷ QA days. Shows whether gains come from development, testing or both, and whether QA becomes the bottleneck. | Read with the gain, not as a target |
| Release testing | Per release-testing phase: hours, elapsed days, share of regression automated, defects found after release (outside the gain) | Falling, with defects not rising |

## 4 How to interpret results

Sprints 1-3 set the baseline, with the team's current tools and practices. Every three sprints the gain is compared with it, with a likely range showing how far it could move through normal variation between tasks (A.1, A.2, A.3). A result is trusted only while the checks in section 3 are healthy; otherwise the pause rules apply.

| Verdict | Meaning | Use |
| --- | --- | --- |
| **Confirmed** | Better than baseline, beyond normal variation, two periods in a row | May be reported to management |
| Early signal | Better than baseline, beyond normal variation, this period only | Shared with the team; reported once confirmed |
| No clear change | Within normal variation | Keep measuring |
| Decline | Worse than baseline, beyond normal variation | Look at quality, rework and blockers |
| Insufficient data | Fewer than 30 comparable tickets in the period | Keep measuring |

### Pause rules

| Condition | Action |
| --- | --- |
| Measurement overhead over 2% of developer, QA and team-lead time | Simplify before continuing |
| Check sizing (A.1) more than 20% off, two sprints in a row | Suspend reporting; the team reviews the size table together and agrees how to apply it |
| Developer and QA hours with no ticket or release code over 15%, not counting planned non-delivery codes (support, incidents, training, meetings, onboarding) | Correct logging; report only the capacity check for that period |
| More than 30% of developers or QA changed since the baseline | Set a new baseline |

## 5 Roles, rollout and use

| Role | Tasks | Time |
| --- | --- | --- |
| Developer | Accept or flag the sizer's draft at refinement; ticket number on timesheet entries; join check sizing when asked | ~5 min per story, ~10 min per sprint |
| QA engineer | Ticket number or release code on timesheet entries; link bugs found after QA pass to the causing story; join check sizing when asked | ~2 min per story |
| QA lead | Each sprint: decide own bugs with the team lead. Each release: report release-testing hours, elapsed days, the share automated and defects found after release. | ~1 h per release |
| Team lead | Each sprint: settle flagged sizes, assign work types (A.1, order of tests), arrange check sizing, decide own bugs with QA. Each period: match hours to tasks, keep the change log, prepare the report and review it with the team before management. | ~30 min per sprint, ~45 min per period |

For example, an illustrative team of 14 people (10 developers, 3 QA and a team lead) completing about 15 stories per two-week sprint spends about 3 hours per sprint out of about 1,120 hours (0.3%). One-off set-up (the Week 1 prompt check, the register and the release-testing code) takes 3-4 person-days. Actual time is measured from sprint 1 with a Scope Points timesheet code (the Measurement overhead row in A.1).

| When | Activity |
| --- | --- |
| Week 1 | Prompt check: 2-3 members size about 10 recent stories by hand; start when at least 8 of 10 match the sizer and none differs by more than 20%; otherwise clarify the counting rules and repeat. Set the development and QA split and compare it with the QA share of story hours in the last three sprints. |
| Sprints 1-3 | Baseline: size all stories and collect data. Extend if fewer than 30 tickets or 5 of any work type; later periods then move by the same number of sprints. |
| Sprints 4-6 | First comparison; at most an early signal. |
| Sprints 7-9 | Second comparison; a confirmed result is possible, otherwise extend. |
| After sprint 9 | Review the sizing instrument (sizing document, A.3), the split, and the 13-point limit against real story sizes (sizing document, story rule 6). Changes apply to the next trial. |

**Use of results.** Results show whether the team's process is improving. They are never used to rate individuals, set quotas or targets, feed pay or appraisal, or rank teams, and are not comparable between teams unless sizing is calibrated across them. QA is never measured by bugs found or tests written, and developers never by bugs caused.

## 6 FAQ

**How is release testing handled?**

It covers every story in a release and cannot be divided fairly between tickets, so everyone who takes part logs it to its own code. It is reported per release (hours, elapsed days, share automated, defects after release), outside the gain, so a release-testing sprint shows no false drop. Savings from test automation show directly in that report.

**Why are results compared over three-sprint periods?**

A single sprint has too few finished stories for a stable result; a few unusually quick or slow stories can move it. Three sprints give at least 30 stories, which the likely range and verdicts need (A.2).

## Appendix

### A.1 Measurement specification

Exact rules for whoever builds and runs the report. Section 3 summarises what they produce; sizing details are in the sizing document.

#### Definitions

| Element | Definition | Source |
| --- | --- | --- |
| Size | Scope points for what the story changes, read from the requirement (sizing document, section 2) | AI sizer draft, checked by a developer |
| Effort | Hours logged by developers and QA to the task in the timesheet, including its sub-tasks. Hours logged by the team lead or others, release-testing hours and general test-automation hours are not counted in the gain. 8 hours = 1 person-day. | Existing timesheets |
| Productivity | Points credited ÷ developer and QA person-days, per work type (below) | Calculated each period |
| Capacity check | Points credited ÷ available developer and QA person-days (capacity minus leave) in the period. It does not use ticket hours, is not adjusted for work mix, and does not see hours carried in from earlier periods. When it differs from the productivity gain, check in this order: work types left out of the gain, a change in work mix, a change in carry-over, then ticket hours. | Calculated each period |
| Stages | **Dev done**: the code is merged and the story moves to QA. **QA pass**: the story passes QA and moves to Done. A story with no QA step has one stage, Done. | Issue tracker status |
| Stage split | The share of each story's points credited at each stage: QA share = QA members ÷ (developers + QA members), in full-time equivalents at the start of the trial, to the nearest 5%. Fixed for the trial; compared once with the QA share of story hours in the last three sprints | Team roster, Week 1 |
| Period | 3 sprints. All results are calculated and reported per period. Each stage counts in the period in which it is first completed, with all the hours for that stage, including hours logged in earlier periods. | Sprints 1-3, 4-6, 7-9 |
| Delivery hours and points | At dev done, the development share is credited and the developer hours are frozen as the development delivery hours. At QA pass, the QA share is credited and the QA hours are frozen as the QA delivery hours. Each share is credited once: a story returned by QA or reopened later does not credit it again. | Register |
| Rework | Developer hours logged to a story after its dev done, QA hours logged after its QA pass, hours on own bugs, and hours on work the team abandoned. They count in the period in which they are logged, under the work type of the ticket that caused them, with 0 points, and are never added to delivery hours. Own bugs are also reported separately by severity. | Timesheets and register |
| Excluded work | Tasks already in progress when the baseline starts are not counted; their hours are reported as carry-in. Hours on stories cancelled by the business are not counted in productivity; they are reported separately. For a story developed by another team, only the QA share and our QA hours are counted. | Register |
| Baseline | The first period under this method: at least 30 tickets, and at least 5 of each work type. If it is extended, later periods move by the same number of sprints. | Sprints 1-3 |
| Release testing | Hours logged by anyone to the release-testing code. Not part of the gain; reported per release with elapsed days, the share of regression that is automated, and defects found after release. | Timesheets |

#### Work types

| Type | Definition |
| --- | --- |
| Feature | New or changed behaviour that users or the product owner asked for. |
| Bug | A fix for behaviour that does not meet an existing requirement, including performance or security that falls short of a stated requirement. |
| Modernization | A change that keeps behaviour: migration, refactoring, speed-up or security beyond existing requirements (Technical items only). |
| Data | A change whose main purpose is stored data: structure, conversion or upgrade scripts. |

The team lead assigns one type when the story is Ready, and it does not change afterwards. The first test that applies decides:

1. **Bug**, if the story restores behaviour an existing requirement already defines;
2. **Modernization**, if every item is Technical;
3. **Data**, if Data items hold most of its points;
4. otherwise **Feature**.

The same minimum applies in every period: a type with fewer than 5 stories reaching QA pass is left out of that period's headline figures (A.1), and the report says so.

#### Tasks that span two periods

Example, with an 80% and 20% split: a 5-point story reaches dev done in sprint 3 after 32 developer hours, and passes QA in sprint 4 after 8 QA hours. Period 1 (sprints 1-3) is credited 4.0 points with 32 hours; period 2 (sprints 4-6) is credited 1.0 point with 8 hours. The story totals 5 points and 40 hours (5 person-days), and each period counts only the work finished in it. Hours logged at the end of a period to stages not yet completed are reported as carry-over. Because the capacity check uses only the period's own capacity, a change in carry-over between periods moves it without any logging problem.

The baseline reflects the team's current tools and practices. The trial measures change from that point.

**The work-mix-adjusted productivity gain is the primary metric.** All other measures are guardrails or diagnostics, reported beside it to show whether it can be trusted, not as targets.

#### Controls

Each known way the measure could be distorted has a control.

| Risk | Control |
| --- | --- |
| Size shrinks as the team gets faster | Points come from the requirement; effort is measured separately |
| Splitting changes the total | Points belong to items; split items divide their points; split-only work scores 0 |
| Large code changes inflate size | Size is set from the requirement before work starts |
| Speed gained at the cost of quality | Bugs caused by the team's own changes during the trial score 0 while their hours count; own bugs per 100 points is reported by severity |
| A change in work mix looks like a productivity change | Each work type is compared with itself, then combined using the baseline mix |
| A random good period is reported as improvement | An improvement is confirmed only when it holds in two consecutive periods |
| A story spanning two sprints is counted twice | Points are split between development and QA, never repeated; each story totals exactly its size |
| Testing becomes faster but misses more defects | Own bugs found after QA pass and defects found after release are reported per 100 points |
| Sizes drift upward | Check sizing each sprint (A.1) |
| The AI drafts sizes inconsistently | A tested sizing prompt (sizing document, A.4); model and prompt, with its rules and built-in reference stories, frozen for the trial (sizing document, A.1, sizing instrument); every draft is reviewed by a developer; check sizing detects lasting shifts |
| Hours recorded against tickets are incomplete or inaccurate, for example logged to a general code instead of the ticket | The capacity check (A.1) measures points per available person-day, so it does not depend on ticket hours. If the two measures differ noticeably, work types left out of the gain are checked first, then the work mix, the change in carry-over and ticket hours. The share of logged hours without a ticket number is also reported. |
| One large ticket dominates a period | Stories are limited to 13 points (sizing document, story rule 6); results are also shown without the 3 largest tickets |
| A gain is credited to the wrong cause | The result is called a productivity gain; team, tool and release-process changes are logged on each report |

#### Per task

| Field | Formula | Example |
| --- | --- | --- |
| Points credited | Development share at dev done plus QA share at QA pass (sizing document, section 2) | 6.4 + 1.6 = 8 |
| Delivery hours | Developer hours logged to the task and its sub-tasks up to dev done, plus QA hours up to QA pass, in any period; person-days = hours ÷ 8. Later hours are rework (A.1). | 44 h + 8 h = 52 h ÷ 8 = 6.5 person-days |
| Points per person-day | Points ÷ delivery person-days | 8 ÷ 6.5 = 1.23 |
| Hours saved against baseline speed | Points × baseline hours per point for the work type − delivery hours. Baseline hours per point = baseline hours ÷ baseline points for that work type. | 8 × 8 h − 52 h = 12 h (illustrative feature baseline of 8 h per point) |

#### Period report

**Terms:** P = points credited in the period: development shares of stories reaching dev done and QA shares of stories reaching QA pass. D = the frozen delivery hours of those stages, plus rework hours logged in the period, in developer and QA person-days (hours ÷ 8); rework is added to the work type of the ticket that caused it. S = the eligible work types: those with at least 5 stories reaching QA pass in the current period (the baseline already has at least 5 of every type). If the eligible types change between periods, the report notes it. A = available developer and QA person-days (developers and QA engineers × working days − leave). Subscript b = baseline period, c = current period, t = work type. Speed = P ÷ D.

Illustrative figures, sprints 7-9 compared with sprints 1-3.

| Measure | Formula | Result |
| --- | --- | --- |
| Productivity gain | D_(b,S) ÷ Σ_(t∈S) (P_(b,t) ÷ Speed_(c,t)): baseline person-days of the eligible types divided by the person-days that same baseline work would take at current speed. A type left out is removed from both sides, so the remaining baseline shares add up to 100%. If the work mix is unchanged this equals Speed_(c) ÷ Speed_(b). Same work takes 1 ÷ gain of the baseline time. | 1.6× (likely range 1.3-1.9×). Confirmed. The same work takes about 63% of the baseline time. |
| Capacity check | (P_(c) ÷ A_(c)) ÷ (P_(b) ÷ A_(b)) | 1.6×, consistent with the productivity gain |
| Hours saved | Σ over the eligible stages completed in the period (credited points × baseline hours per point for its work type) − their frozen delivery hours − all rework hours logged in the period for the eligible work types. This matches D. Baseline hours per point_(t) = 8 × D_(b,t) ÷ P_(b,t). | 760 h (about 95 person-days) |
| Own bugs found this period | Own bugs found in the period ÷ P_(c) × 100, shown by severity; the current cost of rework | 1.2 (baseline 1.9); none critical |
| Own bugs by delivery cohort | Own bugs traced to stories that passed QA in a period ÷ the points of those stories × 100, updated as later bugs are found. A cohort's figure is treated as mature two periods after it closes; only mature figures are used for conclusions about quality. | Sprints 1-3: 1.6 (mature); sprints 4-6: 0.9 (not yet mature) |
| By work type | Speed_(c,t) ÷ Speed_(b,t) | Features 1.8×, modernization 2.2×, bugs 1.25×, data upgrades 1.2×. Combined with the baseline shares of person-days (45%, 20%, 25%, 10%): 1 ÷ (0.45 ÷ 1.8 + 0.20 ÷ 2.2 + 0.25 ÷ 1.25 + 0.10 ÷ 1.2) = 1.6×. This is the productivity gain formula; a plain weighted average of the gains (1.68×) is not correct. |
| Team change | Developers and QA engineers who joined or left since the baseline ÷ their baseline number | 10% (one developer joined in sprint 8; onboarding hours reported separately) |
| Hours with no ticket | Developer and QA hours without a ticket number or release code ÷ all developer and QA hours, excluding planned non-delivery codes | 7% |
| Planned non-delivery | Developer and QA hours on support, incidents, training, meetings and onboarding ÷ all developer and QA hours | 18% |
| Carry-over | Developer and QA hours logged in the period to stages not yet completed, compared with the previous period | 96 h (previous period 88 h) |
| Rework | Developer and QA rework hours (reopened tickets, own bugs, abandoned work) ÷ all ticket hours | 6% |
| Measurement overhead | Hours logged to the Scope Points code (sizing review, check sizing, register, reporting) ÷ available developer, QA and team-lead hours | 0.4% |
| Cancelled work | Developer and QA hours on stories cancelled by the business (not in productivity) | 12 h |
| Release testing | For a release in the period: release-testing hours and elapsed days, the share of regression that is automated, and defects found after release ÷ points released × 100 (not in productivity) | Release in sprint 8: 1,150 h over 12 working days; 20% run by agents; 0.6 defects after release |
| Largest-ticket check | Productivity gain recalculated without the 3 largest tickets | 1.55× |

The productivity gain, its likely range and the hours saved always use the same eligible work types. Diagnostic rows show all work. The report also states the **eligible coverage**: the share of baseline developer and QA person-days that the eligible types represent (example: 92%). A result based on a small share of normal work is reported with that caveat.

**Worked example.** For simplicity, every work type has the same baseline speed here: 1.0 point per person-day, or 8 h per point. Baseline: 160 points in 160 person-days (1,280 h), a speed of 1.0. Current: 255 points in 160 person-days, a speed of 1.59. With an unchanged work mix, gain = 1.59 ÷ 1.0 ≈ 1.6×. Hours saved = 255 × 8 h − 1,280 h = 760 h. With 285 available person-days in both periods, the capacity check is (255 ÷ 285) ÷ (160 ÷ 285) ≈ 1.6×.

#### Evaluation

##### Exact verdict conditions

| Verdict | Condition | Use |
| --- | --- | --- |
| Confirmed | The lower end of the likely range is above 1.0× in the current and previous period | May be reported to management |
| Early signal | The lower end is above 1.0× in the current period only | Shared with the team as a progress indicator. Reported to management once it is confirmed in the next period, because a single period can be above 1.0× by chance. |
| No clear change | The likely range includes 1.0× | Continue measuring |
| Decline | The upper end of the likely range is below 1.0× | Investigate quality, rework and blockers |
| Insufficient data | Fewer than 30 stories reaching QA pass across the eligible work types in a period | Continue measuring |

##### How the verdict is calculated

The verdict depends on the likely range of the productivity gain, calculated each period with a spreadsheet or a short script:

1. List the completed stages (dev done and QA pass) of the eligible work types for the baseline and the current period (work type, credited points and delivery hours), and the rework hours of each type in each period.
2. Calculate the productivity gain with the formula above.
3. Draw a random sample of the same size from each period's completed stages within each work type, with replacement (a stage can be picked more than once). Add each type's observed rework hours to its person-days unchanged, and calculate the gain again.
4. Repeat step 3 2,000 times and sort the 2,000 results.
5. The 100th result is the lower end and the 1,900th result is the upper end of the likely range: the middle 90% of results.
6. Apply the conditions in the table above, using this period's range and the previous period's range.

| Period | Gain | Likely range | Lower end above 1.0×? | Verdict |
| --- | --- | --- | --- | --- |
| Sprints 4-6 | 1.4× | 1.2-1.7× | Yes | Early signal |
| Sprints 7-9 | 1.6× | 1.3-1.9× | Yes, second period in a row | Confirmed |

Example: if sprints 7-9 had instead shown a range of 0.9-1.5×, the range would include 1.0× and the verdict would be No clear change.

#### Check sizing

The formula is in section 2 and the pause rule in section 4.

Each sprint, a sample of stories is sized again by hand to confirm that recorded sizes stay consistent.

- **Which stories:** 2 stories that passed QA, picked at random.
- **Who:** 2 or 3 team members, each sizing on their own from the requirement, without the AI draft and without seeing the recorded size. Their totals are averaged.
- **Result:** the difference between the recorded total and the check total, as a percentage of the recorded total.
- **If the difference is over 20%:** the AI sizer is re-run on the same stories. This shows whether the gap comes from the AI draft or from changes made to it at refinement.
- **Agreement between reviewers:** the range between the highest and lowest independent total is also reported, as a percentage of their average. If it is over 30% in two sprints in a row, the sizing guidance is revised, even when the average matches the recorded size.

| Stories checked | Recorded size | Check size (average) | Difference | Outcome |
| --- | --- | --- | --- | --- |
| 2 stories, sprint 5 | 25 | 23 | 8% | Within 20%: no action |
| 2 stories, sprint 6 | 25 | 19 | 24% | Over 20%: if repeated next sprint, reporting pauses |

#### Register

Points are kept in a register outside the issue tracker, one row per story: ticket number, work type, items (kind, count, size, points), total points, instrument version (exact model and version, and prompt version), Ready date, dev done date, QA pass date, credited shares, developer and QA delivery hours, period of each stage, external-development flag, own-bug flag and severity, rework hours, cancelled or removed scope and the cancellation reason. The issue tracker remains the source for ticket status, the timesheets for hours, and the register for points; the team lead reconciles the three each period.

### A.2 How reliable the verdicts are

This answers two questions: how often the method reports an improvement that did not happen, and how often it detects one that did.

No real data exists yet, so this was tested with a computer simulation: a short program that generates made-up task data where the true answer is known in advance, then checks whether the method finds it.

1. **Create a baseline period.** 45 finished tasks: 18 features, 11 bugs, 9 modernization and 7 data tasks (at least 5 of each, as the baseline requires), each with a size of 1-13 points, and hours equal to points × a typical hours-per-point for that work type, varied at random by about ±40% to mimic real work.
2. **Create a later period with a known change.** The same kind of data, but with hours reduced by a chosen amount: no change, 1.2×, 1.3× or 1.5× more productive.
3. **Apply this proposal's method unchanged.** Calculate the productivity gain, the likely range (2,000 re-samples) and the verdict. For "confirmed", a second later period is created and both must pass.
4. **Repeat 1,000 times for each scenario**, each time with new random data, and count how often each verdict appears.

Because the true change is known, the results show how often the verdict is right or wrong. The ±40% variation is an assumption; the test is repeated with the team's real data after the baseline sprints. The simulation models variation between finished tasks only; it does not model rework or cancelled work.

| Actual change in productivity | Teams shown an early signal | Teams shown confirmed |
| --- | --- | --- |
| None | 5 in 100 (wrong) | about 1 in 100 (wrong) |
| 20% more productive (1.2×) | 69 in 100 | 55 in 100 |
| 30% more productive (1.3×) | 93 in 100 | 87 in 100 |
| 50% more productive (1.5×) | almost all | almost all |

**How to read it:** under these assumptions (45 tasks per period, about ±40% variation), when nothing has changed a confirmed improvement is reported in about 1 of 100 cases. With fewer tasks (the minimum is 30) or more variation, the ranges are wider and a result takes longer to confirm; very few tasks of one type make that type's result unstable. A large improvement is almost always detected within two periods. A small one (around 1.2×) is confirmed about half the time within two periods and may need longer.

### A.3 Likely range and work-mix adjustment

These are the two adjustments behind the productivity gain in A.1.

#### Likely range

**Why:** with about 45 tasks in a period, a few unusually quick or slow tasks can move the result. The likely range shows how far the gain could move by chance.

**How:** the steps are in A.1 ("How the verdict is calculated"). The gain is recalculated 2,000 times on random re-samples of the completed stages, and the middle 90% of the results is the likely range.

**Example:** a gain of 1.6× with a likely range of 1.3-1.9× means that re-sampling the same tasks mostly gives gains between 1.3× and 1.9×. Because even the low end is above 1.0×, the result is unlikely to be explained by differences between individual tasks. The range describes uncertainty from the task sample, not a guaranteed probability for the true gain.

#### Work-mix adjustment

**Why:** some kinds of work are naturally faster than others. If a period happens to contain mostly fast work, a simple average rises even though nobody got faster.

**How:** each work type is compared only with the same work type in the baseline. The gain is the baseline's person-days divided by the person-days the baseline's work would take at current speeds.

| Example: nobody got faster, but the work mix changed | Baseline | Current |
| --- | --- | --- |
| Features (2.0 points per person-day in both periods) | 100 points, 50 days | 180 points, 90 days |
| Data upgrades (1.0 point per person-day in both periods) | 100 points, 100 days | 20 points, 20 days |
| Total | 200 points, 150 days (1.33 per day) | 200 points, 110 days (1.82 per day) |

The simple ratio is 1.82 ÷ 1.33 = 1.36×, which suggests a 36% improvement that did not happen. The adjusted calculation costs the baseline's work at current speeds: 100 ÷ 2.0 + 100 ÷ 1.0 = 150 days, the same as the baseline's actual 150 days. The gain is therefore 150 ÷ 150 = 1.0×, which is correct. When the work mix does not change, both calculations give the same result.
