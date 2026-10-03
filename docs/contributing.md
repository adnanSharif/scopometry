# Contributing

This is open research. The most useful contributions are:

- **Critique** — a rule that can be gamed, a formula that misleads, a case the model does not cover. Open an issue describing the scenario.
- **Pilot data** — results from trying Task Points or Dyno, Road & Destination in a real team. Share aggregated, anonymised figures only.
- **Replications** — independent re-sizing of the same tasks, to test whether the counting rules are reproducible.
- **Related work** — papers, standards or industry reports that support or contradict the approach.

## Ground rules

1. **No confidential information.** Never submit employer, customer or product names, internal tool names, ticket keys, source code or individual-level data. Replace them with neutral placeholders (`Team Alpha`, `EX-101`, `Dev A`).
2. **Never rank individuals.** Contributions that turn these measures into per-person scorecards will not be accepted.
3. **Show your evidence.** Prefer worked examples with explicit counts and arithmetic over opinions.

## Working on the site locally

```bash
python -m venv .venv && . .venv/bin/activate
pip install -r requirements.txt
mkdocs serve        # http://127.0.0.1:8000
mkdocs build --strict
```

Pages live in `docs/`; navigation is in `mkdocs.yml`. Pull requests run a strict build, and merges to `main` publish the site to GitHub Pages.
