# Unit 1 — Issue Selection

## Issue link

**Selected issue:** [#73 — README and `.env.example` disagree about which LLM API key to set](https://github.com/codepath/pathreview-ai301-fa26-s1/issues/73)

**Verdict:** `accept`

## Verdict output

The live `issue-select` run graded #72, #69, and #73 independently and accepted all three. It ranked #72 and #69 ahead of #73 for my Python and testing fit. The #73 object below records the checks and verdict from that earlier live output. The complete three-issue JSON array was not saved in this repository; the separate `eval-run.txt` is the 20-package evaluator run, not this live issue verdict.

Issue URL: https://github.com/codepath/pathreview-ai301-fa26-s1/issues/73

```json
{
  "item": "https://github.com/codepath/pathreview-ai301-fa26-s1/issues/73",
  "checks": [
    {
      "name": "Maintainer activity",
      "grade": "pass",
      "evidence": "Last 5 main commits authored by Aburke225, newest 2026-09-16T21:42Z"
    },
    {
      "name": "Repository in use",
      "grade": "pass",
      "evidence": "archived=false, pushed_at 2026-09-16T21:48Z; no releases"
    },
    {
      "name": "Bounded newcomer scope",
      "grade": "pass",
      "evidence": "COLLABORATOR-filed, labels bug/good first issue/docs/tier-1, names README.md and .env.example, 1-2h"
    },
    {
      "name": "Available to claim",
      "grade": "pass",
      "evidence": "assignees [], zero comments, no linked or referenced PRs"
    },
    {
      "name": "Contribution policy compatible",
      "grade": "pass",
      "evidence": "docs/CONTRIBUTING.md and PR template contain no AI restriction"
    },
    {
      "name": "Maintainer responsiveness",
      "grade": "unclear",
      "evidence": "No maintainer comments in 8-issue sample; nothing to measure"
    }
  ],
  "verdict": "accept"
}
```

## Issue analysis — `issue-19`

For scored package `issue-19` (`zxcalc/zxlive#517`), my rubric returned **accept**, matching the gold label **accept**. The issue reports that selecting large subgraphs in proof mode freezes the UI, and it was filed by a collaborator. It identifies two possible causes in the matching and UI-update paths. The three further suggestions are presented as options within this same bug report, not as separately titled issues or independent deliverables. Under my **Bounded newcomer scope** rule, naming likely causes and related steps is direction, not proof of umbrella scope. The package also reports an active, unarchived repository and no assignee or linked PR. Those facts support the matching verdicts.

## Check rationale

I focused on **Bounded newcomer scope**, a required check. The exact rubric says, “Grade the size of the work requested, never the polish of the writeup.” It also says, “When none of (a)-(f) holds and the issue names the behavior, files, or symptoms involved, pass.” The rule rejects umbrella or tracking work, explicitly codebase-wide or core-internal changes, support questions, unresolved design disagreements, repeatedly abandoned old work, and unsupported new feature requests.

Issue #73 names one disagreement between `README.md` and `.env.example` and asks for one consistent account of the LLM API key. Two files can be part of one deliverable. A collaborator opened it, it had the `good first issue` and `docs` labels, and its estimate was 1–2 hours. No disqualifying scope condition appeared in the issue or thread at the time of the live check, so `pass` followed the written rule.

The other required checks supported `accept`: recent collaborator commits and a September 16 push showed activity in an unarchived repository; the issue had no assignee, comments, or linked or referenced PRs at that check; and the contribution guide and PR template imposed no AI restriction. Maintainer responsiveness remained `unclear` because the sampled issues had no maintainer comments. It was preferred, so it did not change the verdict. These are observations from the September 2026 live run, not a claim about the issue's present availability.

## Trade-offs

**Issue choice:** #73 has a smaller documentation and configuration review surface than [#72](https://github.com/codepath/pathreview-ai301-fa26-s1/issues/72), which changes password-verification behavior, or [#69](https://github.com/codepath/pathreview-ai301-fa26-s1/issues/69), which changes parser fallback behavior. That choice gives up some Python implementation and testing practice. The skill ranked #72 first and #69 second for my technical fit; I still chose #73 as a bounded first contribution.

**Check trade-off:** The quoted **Bounded newcomer scope** rule deliberately accepts a named behavior and a single deliverable even when the issue description is brief. This avoids rejecting a reasonable starter issue merely because the report is short or touches two related files. It can miss hidden complexity: for example, a labeled docs mismatch might actually require changes across several providers or an unsettled configuration decision that the issue does not disclose. The rule only catches codebase-wide work or design disagreement when the body or thread provides that evidence. Its `pass` for #73 does not prove the fix will take exactly 1–2 hours.

If I tightened this check after discovering such a miss, I would first rerun a canary that should still pass (`issue-19`, the maintainer-diagnosed bounded performance bug) and scope rejections that should stay rejected (`issue-05`, the umbrella issue, and `issue-20`, the underspecified feature wish). I would then rerun the full evaluation and compare all categories. This is a future validation plan, not a claim that I ran another evaluation after the final 20/20 result.

## Selection rationale

I selected #73 because the verdict correctly identified a live repository, a then-available issue, and a bounded deliverable. The relevant files and mismatch are explicit, so I could begin by checking the actual configuration in `core/config.py`, deciding which API key the application expects, and making the setup instructions consistent. I made the final choice myself even though the skill ranked the more code-focused #72 and #69 higher.

**Claiming difficulty:** The issue was open and unassigned with no claim comments when I evaluated it, which made an initial claim straightforward. That could change between selection and posting. Path Review's classroom rule allows multiple students to claim the same issue, so another student's comment would not reserve it or block mine, but shared work could complicate coordination and review. Maintainer response time was also unmeasured. Before claiming I would recheck the thread, write a specific comment promising investigation rather than a fix or deadline, and keep any later report grounded in my own observed output. I did not claim #73 during Unit 1; issue selection and claiming were separate steps.

## Run history

1. I wrote the required checks and verdict rule in `skill/rubric.md`. An initial smoke evaluation stalled and was terminated, so I did not count it as a completed run.
2. I installed the `issue-select` skill, configured `scope.md` for `codepath/pathreview-ai301-fa26-s1`, and set my fit profile. The first live attempt against #73, #72, and #69 also stalled and was terminated.
3. I checked repository and issue activity directly, then refined **Bounded newcomer scope** to distinguish one deliverable across related files from an umbrella issue.
4. The targeted evaluation of `issue-01`, `issue-19`, and `issue-20` matched **3/3** expected verdicts.
5. The completed full evaluation matched **20/20** scored items, above the **18/20 PASS** bar. It matched claimed **4/4**, clear-accept **8/8**, dead-repo **3/3**, policy **1/1**, and scope **4/4**. The original harness output is in [`eval-run.txt`](eval-run.txt).
6. A subsequent live run accepted #72, #69, and #73 and produced the #73 verdict recorded above. I chose #73 despite its third-place fit ranking. No claim or implementation was part of Unit 1.

## Final evaluation output

The saved 20-package evaluator run ends with:

```text
categories: claimed 4/4  clear-accept 8/8  dead-repo 3/3  policy 1/1  scope 4/4
agreement: 20/20 scored items  (bar: 18/20: PASS)
```

This evaluator result measures the rubric against fixed bundles. The `Verdict output` section above records the separate live grading of the selected GitHub issue.
