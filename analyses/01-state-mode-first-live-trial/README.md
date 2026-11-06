# Onboarding a new state: Mississippi's first live trial

Brought Mississippi online as the 49th state in the cost-estimation platform and ran its first end-to-end live trial across all four estimators.

**Late September to early November 2026** · legal-source readers, live trials, defect triage

## What I did

- **Readers for state law.** Built readers for Mississippi's statutes and administrative code from official and public sources, with fallbacks, and with explicit refusals when a current text can't be confirmed.
- **State profile.** Assembled the state's economic and fiscal parameters, each sourced and documented.
- **Four estimators at once.** Ran all four estimators concurrently on real Mississippi inputs: an administrative rule, a statute section, an agency notice, and a bill.
- **Reading the output like a reviewer.** Two independent readers checked each delivered document against the onboarding checklist. Every reported defect went to an adversarial verifier and was traced to the code that produced it.
- **Fixes in the right place.** Used the trial to separate state-specific problems from problems in the shared pipeline, and fed the fixes back into the platform for every state.

About 45 commits over the onboarding and trial. Part of [the fifty-state toolkit](../../projects/02-fifty-state-legal-source-toolkit/).

## What it shows

Treating a live trial as a test with a defined reading protocol, and routing each defect to its true cause instead of patching symptoms where they appear.

## Not covered here

Trial inputs, figures, defect lists, and source choices belong to my employer and are not described.
