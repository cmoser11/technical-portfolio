# Document formatting service

A web service that turns drafts (Word, Markdown, or HTML) into publication-ready Word documents in a house style, with an optional AI copy-editing pass.

**January to October 2026** · Python, Office Open XML, FastAPI, AWS

## The problem

Every report, brief, and estimate had to match a detailed house style. Doing it by hand was slow and inconsistent, and the cost-estimation platform needed to produce formatted documents automatically.

## My role

- **January to April 2026:** contributor to the original formatting scripts.
- **April to June 2026:** built the document-type formatters inside a shared internal agent platform (30 commits).
- **June to October 2026:** built and maintained the standalone web service, with 193 of its 229 commits.

## Engineering highlights

- **Working directly with Office Open XML.** A formatting engine on python-docx and lxml that writes element properties in the order the schema requires, so Word opens the output without repair prompts.
- **Automatic document-type detection.** Weighted signals pick the right formatter, and the service asks the user when confidence is low.
- **Style rules as data.** Abbreviation, title, and citation rules live in JSON files, so editors can extend them without code changes.
- **AI copy editing where the model never writes text.** Deterministic rules find candidate edits, the model only approves or rejects each one, and approved edits are applied mechanically. The pass falls back to rules only if the model is unavailable.
- **Long documents.** Batched model calls with deadlines, and progress reporting in the interface.
- **Deployment.** Docker on ECS Fargate through AWS Copilot, with automatic deploys to development and production by branch. A GitHub Actions gate runs exactly what the deploy build runs.
- **Operations.** CloudWatch alarms for degraded model calls, single sign-on that fails closed while keeping health checks open, and task sizing set from a measured production timeout.

## Scale of my work

| Measure | Value |
|---|---|
| Commits, web service | 193 of 229 |
| Commits, earlier formatter work | about 45 |
| Python files, web service | about 80 |
| Test files, web service | 26 |

## Stack

Python 3.12, FastAPI, python-docx, lxml, mistune, Anthropic API, Docker, AWS Copilot, ECS Fargate, CodePipeline, CloudWatch, GitHub Actions, pytest.

## Not covered here

The house style, brand assets, and rule libraries belong to my employer and are not described.
