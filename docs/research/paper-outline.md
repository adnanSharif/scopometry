# Paper outline

Working outline for a research paper based on this repository.

**Working title:** *Measuring Engineering Work in Agentic Software Delivery: Count-Based Task Sizing and Multi-Lens Evaluation of AI Productivity*

## Abstract (draft)

AI coding agents change how software work is sliced, estimated and executed, which undermines traditional productivity proxies such as logged hours, story points and ticket counts. We propose Task Points, a sizing method in which an AI assistant counts the units a task involves and quotes evidence, a person verifies the counts, and a fixed mapping converts counts to a size that is independent of who does the work and how much AI they use. Points are credited only for proven work and reported per available person-day alongside quality measures. We complement this output-based trend with Dyno, Road & Destination, a three-lens method that estimates the causal effect of AI through randomised AI-on/AI-off task replays, measures time use through random sampling, and evaluates value through outcome statements. We describe the delivery model these measures sit in, report the failure modes found by pre-mortem and adversarial review, and outline a pilot protocol for validation.

## Structure

1. **Introduction** — why AI-assisted delivery breaks existing productivity proxies; research questions.
2. **Background and related work** — story points and estimation; functional size measurement (IFPUG, COSMIC); flow metrics; DORA and SPACE; controlled studies of AI coding assistants. See [References](references.md).
3. **Design goals** — size independent of worker and tool; credit only proven work; no individual ranking; low overhead; resistance to gaming.
4. **Task Points** — task types, units counted, bands, triggers, checkpoints, rework, reporting. Source: [guide](../task-points/guide.md), [life of a task](../task-points/life-of-a-task.md); earlier reference-task form: [specification](../task-points/specification.md).
5. **Delivery model** — the agentic SDLC with risk tiers and gates in which the measures are collected. Source: [handbook](../agentic-sdlc/handbook.md).
6. **Causal measurement: Dyno, Road & Destination** — design, statistics, safeguards. Source: [method](../measurement/dyno-road-destination.md).
7. **Threats to validity** — pre-mortem failure scenarios, Goodhart effects, drift, small samples. Source: [pre-mortem](../scope-points/pre-mortem.md), [limitations](../measurement/dyno-road-destination.md#limitations-stated-honestly).
8. **Evolution and lessons** — Scope Points to Task Points. Source: [evolution](evolution.md).
9. **Evaluation plan** — pilot protocol, inter-rater reliability study, agreement between methods. Source: [open questions](open-questions.md).
10. **Conclusion.**

## Evidence still needed

- Inter-rater agreement data for Task Points sizing on a shared task set.
- At least one team's baseline and post-adoption trend, with quality measures.
- A small Dyno pilot to estimate effect sizes and variance.
