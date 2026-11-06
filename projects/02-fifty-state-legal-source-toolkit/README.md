# Fifty-state legal-source toolkit

Extended the cost-estimation platform from federal law to state law: readers for state statutes and administrative codes behind one shared contract, rolled out to 49 states between September and early November 2026.

**September to November 2026** · Python, web and PDF extraction, test infrastructure

## The problem

Every state publishes its laws differently. Some use official HTML sites, some publish only PDFs, some sit behind vendor portals or JavaScript-heavy pages, and some are best reached through public mirrors. Early state integrations duplicated the same plumbing. Scaling to fifty states needed a shared toolkit and a repeatable onboarding process.

## My role

I designed and built the shared toolkit, then onboarded states in waves of about five. Each wave was developed in its own git worktree, several in parallel. I made about 1,360 commits to the main branch between September and early November 2026.

## Engineering highlights

- **One contract for every state.** Each state's reader implements the same interface, and an automated conformance report lists what a new state still owes before it can ship.
- **A polite, shared HTTP layer.** Per-host rate limits, a conditional-GET disk cache, an identifying user agent, and robots.txt compliance, written once and used by every state.
- **Offline tests by default.** State test suites run against recorded fixtures and fail if they touch the network.
- **Freshness checks.** Each reading records how current its source copy is. A stale or unconfirmable text is flagged or refused instead of silently used.
- **Hard sources handled.** PDF text extraction for codes published only as PDFs, and a headless browser for JavaScript portals.
- **Tracked from data, not memory.** A generated per-state issue register keeps open items visible as the rollout proceeds.
- **No host changes per state.** Adding a state touches no server, front-end, or pipeline host code.

## Scale of my work

| Measure | Value |
|---|---|
| States onboarded | 49 |
| Shared toolkit modules | 25 |
| State-related test files | about 130 |
| Per-state source records | about 150 |
| Commits to main, September to early November | about 1,360 |

## Stack

Python, requests, Playwright, pypdf, pdftotext, pytest with fixture-based HTTP transports.

## Not covered here

Which sources each state uses, how texts are brought up to date, and the onboarding protocol's details belong to my employer and are not described. For a worked example of one state's onboarding, see [the first live trial of a new state](../../analyses/01-state-mode-first-live-trial/).
