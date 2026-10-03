# Scopometry

Open research on **sizing engineering tasks** and **measuring productivity** in AI-assisted, agentic software delivery.

**Website:** https://adnansharif.github.io/scopometry/

## Why

When a team adopts AI coding agents, hours, story points and ticket counts stop being comparable: agents change how work is sliced, estimated and executed. This project develops methods that stay meaningful through that change:

| Component | What it does |
|---|---|
| [Task Points](docs/task-points/guide.md) | Sizes any engineering task (research, dev, review, test planning, testing, defect work) from counts of what it involves, credits only proven work, and reports points per available person-day beside quality measures. |
| [Agentic SDLC](docs/agentic-sdlc/handbook.md) | A delivery model where people orchestrate AI agents through risk tiers, bounded autonomous runs and explicit quality gates. |
| [Dyno, Road & Destination](docs/measurement/dyno-road-destination.md) | A three-lens method to estimate the causal effect of AI (randomised AI-on/AI-off replays), where time goes, and whether outcomes are met. |
| [Scope Points](docs/scope-points/overview.md) | The earlier sizing model, kept with its proposal and pre-mortem as research history. |

## Repository layout

```
docs/
  task-points/      current task-sizing model
  agentic-sdlc/     delivery model for working with AI agents
  measurement/      methods for measuring AI impact
  scope-points/     earlier sizing model (superseded, kept for history)
  research/         evolution, paper outline, open questions, references
mkdocs.yml          site configuration (MkDocs Material)
.github/workflows/  builds the site and publishes it to GitHub Pages
```

## Status

Working research, shared for review ahead of a paper. All thresholds and bands are proposals to be calibrated; all worked examples use illustrative numbers and fictional products.

## Contributing and citing

See [CONTRIBUTING.md](CONTRIBUTING.md). Citation metadata is in [CITATION.cff](CITATION.cff). Content is licensed under [CC BY 4.0](LICENSE).
