# Open questions

Questions the current material does not yet answer. Each is a candidate for a pilot, a replication or a section of the paper. Contributions are welcome — see [Contributing](../contributing.md).

## Sizing validity

1. **Inter-rater reliability.** How often do two people (or two AI runs) produce the same Task Points size from the same task description? What agreement level is good enough for trend reporting?
2. **Band calibration.** The count bands and trigger rules are first-version proposals. Do sizes correlate with effort across task types, and does one point mean roughly the same effort in research as in testing?
3. **Count-based vs reference-based sizing.** Is counting units (current form) more reproducible than comparison with reference tasks (first form), and at what overhead?
4. **Drift.** Does the same task get larger sizes over time (point inflation), and does the quarterly re-sizing of frozen reference tasks detect it reliably?

## Measuring the effect of AI

5. **Attribution.** Points per available person-day can rise for many reasons. How much of a measured change can be attributed to AI use, and does a change log plus an AI-use tag at merge give a defensible reading?
6. **Agreement between methods.** Do Task Points trends and Dyno replay effects agree in direction and size for the same team and period?
7. **Bounded-task bias.** Replay tasks are short and local. How large is the gap between replay gains and gains on long, cross-module work?
8. **Quality guardrails.** Which quality measures (rework share, reopened tasks, escaped defects per 100 points) catch speed gained at the expense of quality soonest?

## Organisational effects

9. **Goodhart pressure.** Does publishing points per person-day change how tasks are split or how counts are recorded, even with the use-of-results rules in place?
10. **Overhead.** What does sizing, checkpoint confirmation and reporting cost per sprint, and is it below the proposed ceiling?
11. **Small teams.** What is the minimum team size and number of sprints for a reliable baseline, and when should teams pool data?
