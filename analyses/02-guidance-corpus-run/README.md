# A 389-document guidance corpus

Ran the cost-estimation platform over a corpus of 389 sub-regulatory guidance documents from a federal agency and delivered an estimate package for each.

**June to October 2026** · batch operations, run provenance, release engineering

## What I did

- **Batch operations.** Ran the corpus in tranches with a runner, a watchdog that halts the batch on repeated fast failures, and retries informed by the previous attempt's findings.
- **Provenance for every result.** Made sure each delivered estimate could be tied to the exact code version that produced it, including after a shared checkout changed during a run. The affected documents were identified and rerun.
- **A lesson worth keeping.** A git worktree isolates edits, not imports, when packages are installed in editable mode, so isolating a run takes more than a separate worktree.
- **Integration under load.** About 200 commits of related platform work, including consolidating long chains of stacked pull requests, each step checked against commit ancestry.
- **Delivery.** An index workbook, a manifest, and a package of estimates per document.

## What it shows

Operating an LLM pipeline as a production batch system: monitoring, recovery, and traceable results at the scale of hundreds of documents.

## Not covered here

Results, quality figures, and document details belong to my employer and are not described.
