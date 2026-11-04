# Casey Moser: technical portfolio

I built LLM-based analysis tools at a policy research organization. The work spans multi-stage LLM pipelines that read laws and regulations and produce cost estimates, reproducible pipelines over public federal data, geospatial datasets, document automation, and the AWS deployments behind them.

This portfolio describes that work at the level I would discuss in an interview. It contains no employer code, prompts, data, or internal documents. See [About this portfolio](#about-this-portfolio).

## Live public tools

- **[Texas housing regulation cost map](https://texas-housing-cost-map.dev.cmoser.ofra.io/)** estimates what local zoning and building rules add to the cost of a new home, statewide. [Case study](projects/03-zoning-ordinance-extraction/)
- **[Federal property in Washington, DC](https://dc-federal-property-map.dev.cmoser.ofra.io/)** maps land the U.S. government controls in the capital, by form of control and agency. [Case study](projects/05-dc-federal-property-map/)

## At a glance

| Measure | Value |
|---|---|
| Period | January to November 2026 |
| Commits authored | about 4,800 across 16 repositories |
| Primary or sole author of | 11 repositories |
| Largest codebase | a monorepo with about 950 Python modules and about 960 test files |
| Core stack | Python, TypeScript and Vue, FastAPI, Anthropic and OpenAI APIs, AWS, GitHub Actions |

How these figures were measured is in [Notes on numbers](NOTES-ON-NUMBERS.md).

## Skills and where to see them

| Area | What I did | Where |
|---|---|---|
| LLM systems | Multi-stage pipelines over legal text, structured extraction, repeated sampling with agreement checks, record-and-replay testing of model calls, a provider migration, spend metering | [01](projects/01-llm-cost-estimation-platform/), [03](projects/03-zoning-ordinance-extraction/), [07](projects/07-regulation-retrospective/) |
| Data engineering | Joining public federal datasets, record linkage with human review, provenance manifests, reconciliation and golden-number tests | [05](projects/05-dc-federal-property-map/), [02](projects/02-fifty-state-legal-source-toolkit/) |
| Web extraction at scale | Polite crawling, robots.txt compliance, PDF and scanned-document handling, headless browsers, offline test fixtures | [02](projects/02-fifty-state-legal-source-toolkit/), [03](projects/03-zoning-ordinance-extraction/) |
| Geospatial | Parcel classification from many public layers, geometry cleanup, web maps and print posters | [05](projects/05-dc-federal-property-map/), [03](projects/03-zoning-ordinance-extraction/) |
| Web and infrastructure | FastAPI, Vue, server-sent events, Docker, ECS Fargate, CloudFormation, CodeBuild, Copilot, single sign-on, CI gates | [01](projects/01-llm-cost-estimation-platform/), [05](projects/05-dc-federal-property-map/), [06](projects/06-document-formatting-service/) |
| Document automation | Office Open XML formatting, Word and Excel generation at scale | [06](projects/06-document-formatting-service/), [01](projects/01-llm-cost-estimation-platform/) |
| Testing and QA | Large test suites, deterministic tests for LLM systems, independent human review, inter-rater agreement | [05](projects/05-dc-federal-property-map/), [01](projects/01-llm-cost-estimation-platform/) |
| Applied analysis | Batch campaigns over hundreds of documents for policy audiences | [Applied analyses](#applied-analyses) |

## Projects

| # | Project | My role | When |
|---|---|---|---|
| 01 | [LLM cost-estimation platform](projects/01-llm-cost-estimation-platform/) | Built four estimators, then unified them into one platform as primary developer | Jan to Nov 2026 |
| 02 | [Fifty-state legal-source toolkit](projects/02-fifty-state-legal-source-toolkit/) | Designed the toolkit and onboarded 49 states | Sep to Nov 2026 |
| 03 | [Zoning ordinance extraction and housing-cost scoring](projects/03-zoning-ordinance-extraction/) | Sole developer; public map | Aug to Oct 2026 |
| 04 | [Federal property in Washington, DC](projects/05-dc-federal-property-map/) | Sole developer; public map | Oct 2026 |
| 05 | [Document formatting service](projects/06-document-formatting-service/) | Primary developer of the web service | Jan to Oct 2026 |

## Applied analyses

| Analysis | What it involved | When |
|---|---|---|
| [Onboarding a new state: Mississippi](analyses/02-state-mode-first-live-trial/) | New state readers and a first live trial of all four estimators | Sep to Nov 2026 |
| [A 389-document guidance corpus](analyses/03-guidance-corpus-run/) | Production batch run with provenance for every result | Jun to Oct 2026 |
| [Other campaigns](analyses/04-other-campaigns.md) | Housing reforms, bill scores, an end-to-end calibration run, and more | 2026 |

## Smaller tools

- **Prompt change report.** Ranks prompt files by how much they changed in git history and links reviewers straight to the diffs.
- **Cross-repository change propagation.** Tracks shared changes made in one repository, sorts them, and applies them to sibling repositories, with a dry run by default.
- **Multi-state estimator fork.** Ported engine fixes and model upgrades into a colleague's state-level fork of an estimator.

## How I work

- **AI coding agents as a daily tool.** I build with Claude Code, often running parallel sessions in separate git worktrees, with a plan, implement, and independent review loop.
- **Tests for anything numerical.** Golden-number tests, reconciliation against published figures, and offline fixtures, so results don't drift silently.
- **Decisions written down.** Methodology notes, calibration notes, and runbooks live next to the code they explain.

## About this portfolio

Everything here describes work I did as an employee of a policy research organization between January and November 2026. The systems, code, data, and analyses described belong to that employer.

This portfolio contains none of the employer's source code, prompts, data, internal documents, or unpublished findings, and it does not describe the employer's methodology beyond what the employer has published. It names public data sources and open-source tools, links to two tools the employer has made public, and gives volume figures about my own work. Colleagues, clients, and partners are not named.
