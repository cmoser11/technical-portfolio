# Zoning ordinance extraction and housing-cost scoring

An AI tool that reads local zoning ordinances, development regulations, and building codes, extracts the rules that raise the cost of building a home, and estimates what each one costs over ten years, with the reasoning shown. The results are published as a public statewide map for Texas.

**August to October 2026** · Python, LLM APIs, document AI, AWS

**Live tool:** [Texas housing regulation cost map](https://texas-housing-cost-map.dev.cmoser.ofra.io/)

## The problem

Local rules such as minimum lot sizes, setbacks, parking minimums, fees, and permitting steps add to the cost of new housing. They are scattered across hundreds of ordinances in inconsistent formats, many of them scanned, so measuring them consistently across a whole state means reading every ordinance.

## My role

Sole developer, working with an outside research organization as partner. 408 commits in about ten weeks.

## What the public map shows

As of 4 November 2026, the map reports 361 of 1,224 Texas municipalities measured, plus 157 counties. Each figure is the median of 10,000 sampled scenarios, shown with a p10 to p90 range, broken down by categories such as minimum lot size, setbacks, parking, fees, and permitting time.

## Engineering highlights

- **Corpus acquisition at scale.** Discovered and downloaded ordinance text for over a thousand Texas jurisdictions from code-hosting services and city websites. Downloads are idempotent and checksum-verified, and the multi-gigabyte corpus can be rebuilt from a committed manifest.
- **Standards-correct crawling.** Wrote a robots.txt matcher that follows RFC 9309 exactly, after the standard-library parser misread one site's rules. Tested against real robots files.
- **LLM extraction you can audit.** Repeated sampling with agreement measures, so uncertain readings are flagged for review instead of published as fact.
- **Scanned documents.** OCR and vision-model passes audit ordinances and tables that exist only as images.
- **Uncertainty shown, not hidden.** Monte Carlo sampling over low, base, and high values produces the published medians and ranges.
- **Cost control.** In-process metering records API spend for every run.
- **Output at scale.** A Word report, an Excel workbook, and a standalone replication script per jurisdiction, over 500 jurisdictions per run.
- **Deployment.** Docker image built natively for amd64 by AWS CodeBuild and served from ECS Fargate behind a load balancer, with a CloudFormation stack that imports shared network resources as parameters.

## Scale of my work

| Measure | Value |
|---|---|
| Commits | 408, sole author |
| Python modules | about 230 |
| Test files | about 140 |
| Lines of Python | about 84,000 |

## Stack

Python, Anthropic and OpenAI APIs, pandas, pyarrow, geopandas, shapely, pypdf, pypdfium2, Pillow, httpx, tenacity, BeautifulSoup, FastAPI, Docker, AWS CloudFormation, CodeBuild, ECR, ECS Fargate, pytest.

## Not covered here

The scoring design, extraction prompts, and cost methodology belong to my employer and are not described beyond what the public map states.
