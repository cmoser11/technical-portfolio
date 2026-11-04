# Regulation retrospective pipeline

Contributed outcome-measurement and verification features to a pipeline that evaluates economically significant federal regulations after the fact.

**June to July 2026** · Python, LLM APIs, Federal Register data

## Context

The pipeline, built with a colleague, finds economically significant regulatory actions since 1993 (about 2,000 rules), retrieves their Federal Register text, extracts structured cost and intent data, scores each rule, and runs evidence-based deep dives. I authored 48 of its 112 commits.

## What I built

- **Ex-post outcome measurement.** A module that quantifies what happened after a rule took effect, gated on evidence quality. When the evidence is too thin, it records an explicit null with a reason instead of producing a number.
- **Deterministic citation audit.** Checks every cited claim against its recorded sources and logs any claim without one. No model involved.
- **Cross-artifact consistency gates.** The memo, the scorecard, and the report tables are checked against each other so they cannot disagree.
- **Model resilience.** A fallback when a model declines a request, default-model upgrades, and spend tracking.
- **Tests** for each module I added.

## Stack

Python, Anthropic and OpenAI APIs, Perplexity, Federal Register and GovInfo APIs, JSON Schema, pytest.

## Not covered here

Scoring rubrics, verdicts, and results belong to my employer and are not described.
