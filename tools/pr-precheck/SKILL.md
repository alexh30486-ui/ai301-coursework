---
name: pr-precheck
description: Check one candidate PR against its issue, plan, diff and evidence before submission, or grade one frozen eval bundle.
---

# pr-precheck: rubric-driven PR grading

## The question
Decide whether exactly one PR package is ready to submit. Read title, description, commits, complete diff and test evidence against its issue, repro, plan and deviations.

## Inputs and modes
Live inputs: plan.md with deviations, fork checkout and branch, draft title/description, captured test evidence and issue URL. Gather real thread, template and contribution policy. House-chain students use the supplied house plan and repro pack. Inspect status, commits and git diff main...HEAD when main is the verified default branch; otherwise use the actual default branch. Verify the base represents the target branch and report a stale or unavailable base.
Eval: the supplied bundle is the whole world. Fetch nothing and read no outside artifacts, scope, voice or gold labels. Use the supplied grading components and execute every check and the full verdict rule.

## The scope seam (live mode only)
Read scope.md before anything else. Stop without grading on a repository placeholder and request the finalized cohort scope file. Never guess it. Refuse outside targets and apply house rules. Eval ignores scope.

## The voice seam (live mode only)
Read voice-guide.md after scope. Check outgoing title and description and report specific violations. Voice alone never changes the verdict unless a rubric check explicitly reads it. Eval ignores voice.

## Component reads
Read rubric.md, references/evidence-guide.md and procedure.md. Follow the procedure. Refuse an empty rubric or procedure, ignoring comments and blank template rows when deciding emptiness. Report gaps instead of inventing checks; affected unverifiable required evidence is unclear.

## Verdict and output
Use only accept (submit) or reject (hold). A summary may precede the result. Include every check. End with valid fenced JSON in this exact schema and field order, with nothing afterward:
```json
{
  "item": "<PR URL or bundle id>",
  "checks": [
    {"name": "<check name>", "grade": "pass|fail|unclear",
     "evidence": "<one line: the fact or quote that decided it>"}
  ],
  "verdict": "accept|reject"
}
```

## Grading discipline
Name the deciding evidence. Grade artifacts rather than polish, length or commit count. The rubric decides; the procedure determines execution. Unclear required evidence holds the package. Apply honest-limitations rules. Never invent tests, inspections, policies or live results.
