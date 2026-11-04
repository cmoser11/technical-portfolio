# LLM cost-estimation platform

Four LLM pipelines that read a regulation, a statute, a bill, or an agency guidance document and produce a ten-year cost estimate as a Word report, an Excel workbook, and a one-page summary. I built them as separate tools, then unified them into one platform with a web interface.

**January to November 2026** · Python, LLM APIs, FastAPI, Vue, AWS

## The problem

Analysts needed consistent, sourced cost estimates for federal and state rules, laws, bills, and guidance, at a pace manual review can't match. Each estimate depends on reading the source text correctly, gathering evidence, computing numbers that can be reproduced and audited, and delivering a polished document.

## My role

- **January to May 2026:** sole developer of the first estimator (federal regulations), then three siblings for statutes, bills, and guidance memos. About 750 commits across four repositories.
- **May to November 2026:** consolidated the four into a single monorepo and became its primary developer, with about 3,200 of its roughly 3,300 commits.

## How it works, at a high level

A user submits a citation or a document. The platform fetches the official text and parses it. LLM stages research the subject and extract the facts an estimate needs. Ordinary code, not the model, does the arithmetic, so every number can be reproduced and traced. Validation and review stages check the result. A document builder renders the Word report, the workbook, and the one-pager. Staff run single jobs or large batches from a web app and watch progress live.

## Engineering highlights

- **Monorepo consolidation.** Merged four diverging codebases into a `uv` workspace with one shared library and four thin pipeline packages, so a fix lands once instead of four times.
- **Deterministic tests for an LLM system.** Added a record-and-replay layer for model calls, so end-to-end golden tests run in CI with no network access and no API spend.
- **Provider migration.** Moved all four pipelines from OpenAI to Anthropic models in June 2026.
- **Web control plane.** FastAPI backend with live log streaming over server-sent events, a bounded job runner, and batch execution with a global concurrency limit, staggered starts, and clean cancellation of whole process trees. Vue 3 and TypeScript front end with single sign-on.
- **State law as a mode, not a fork.** Extended the platform from federal to state law through configuration, so the same pipelines serve every jurisdiction. See [the fifty-state toolkit](../02-fifty-state-legal-source-toolkit/).
- **Production batch use.** Ran campaigns of hundreds of documents through the platform. See [Applied analyses](../../README.md#applied-analyses).
- **CI and deployment.** GitHub Actions for linting and golden tests. Docker images on AWS ECS Fargate.

## Scale of my work

| Measure | Value |
|---|---|
| Repositories | 4 predecessors, then 1 monorepo |
| Commits, predecessors | about 750 (January to May 2026) |
| Commits, monorepo | about 3,200 (May to November 2026) |
| Monthly commits, monorepo | 287 in June, rising to 1,182 in October |
| Monorepo size | about 950 Python modules in the library, pipelines, and server; about 960 test files |

## Stack

Python, `uv` workspaces, Anthropic and OpenAI APIs, Perplexity for web research, python-docx, openpyxl, lxml, pandas, FastAPI, Vue 3, Vite, TypeScript, Docker, AWS ECS Fargate, GitHub Actions, pytest, ruff.

## Not covered here

The economic methodology, prompts, stage design, review rubrics, and estimate results belong to my employer and are not described.
