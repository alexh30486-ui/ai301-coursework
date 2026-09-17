# Rubric: is this a good first issue?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever checks
you define here. It ships empty on purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where. Name the source
     (repo-facts block, issue body, comment thread, or the locations in
     references/evidence-guide.md). "The repo" is not a source; "the last
     5 default-branch commit dates" is.
   - Pass condition: a condition someone else could apply and get your
     answer. Prefer thresholds with numbers ("a maintainer commented
     within 30 days") over adjectives ("maintainer is responsive").
   - Weight: `required` (a fail here rejects the issue) or `preferred`
     (never changes the verdict; a nice-to-have that helps rank the
     issues you accept).

2. A verdict rule below the table: how the check grades combine into
   accept or reject, including how `unclear` is treated. The verdict
   space is binary. If you write no rule for `unclear`, the skill treats
   it as fail.

Cover what actually kills first contributions. The lecture named four
families: the maintainer is alive, the repo is in use, the scope fits a
newcomer, and nobody else is already on it. A rubric that ignores a family
will fail eval issues designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Maintainer activity | In the repo-facts block, inspect the last 5 default-branch commit dates and authors, and the maintainer first-response sample. In live mode, use the same signals from the repository and recently updated issues. | Pass if at least one of the last 5 default-branch commits was authored by a non-bot within 365 days of the bundle capture date or current date, or at least one sampled issue received a maintainer response within 90 days. Otherwise fail. | required |
| Repository in use | In the repo-facts block, inspect `archived:`, last push to any branch, and latest release. In live mode, use the repository archive flag, branch activity, and Releases panel. | Pass only if the repository is not archived and either the last push or latest release is within 365 days of the bundle capture date or current date. Otherwise fail. | required |
| Bounded newcomer scope | Inspect the issue body, labels, comment thread, the issue open date, and the `linked PRs` line (live mode: the Development box plus PRs mentioned in the thread). Use the scope guidance in `references/evidence-guide.md`. | Grade the size of the work requested, never the polish of the writeup. A one-line body, a bare checklist, or a bug report with no reproduction steps still passes when an owner, member, collaborator, or contributor filed it or it carries a `good first issue`/starter label; a maintainer naming the likely causes or listing the sub-steps of one fix is direction, not disqualification, and the several files or pages one change must touch are not separate issues. Steps, files, or pages that one deliverable must touch are not separate issues, and neither is an optional lower-priority extra offered inside the same body. An author diagnosing which function, module, or query is at fault is naming a location, not declaring the work core-internal. Fail only when one of these holds: (a) the issue calls itself an umbrella, tracking, meta, or mega issue, or its body is a list of separately-titled independent items each meant to become its own PR; (b) the body or a maintainer comment states in words that the work is codebase-wide or must change core internals; (c) it is a usage or support question rather than a request to change something; (d) two or more people in the thread actively disagree about what the expected behavior should be and no maintainer has settled it — an empty or agreeing thread is never unsettled design; (e) the issue has been open 2+ years **and** its history holds 2 or more closed-unmerged linked PRs, the signature of repeated abandoned attempts; (f) the issue asks for a net-new feature rather than a bug, docs, or test fix **and** it has no backing from the project: its opener is a bot or carries author association NONE, no owner/member/collaborator has commented, and it carries no starter or help-wanted label. An unresolved product choice or a "TBD" asset in such a request confirms the fail. When none of (a)-(f) holds and the issue names the behavior, files, or symptoms involved, pass. | required |
| Available to claim | In the repo-facts block, inspect `this issue: assignees` and `linked PRs`; inspect every comment in the thread for current claim language such as "I'll take this" or "working on this," and whether a maintainer closed or redirected that claim. Use the claim guidance in `references/evidence-guide.md`. | Pass only when there is no assignee, no open linked PR, and no unresolved current claim in the comments. A closed or merged linked PR alone does not fail. | required |
| Contribution policy compatible | In the repo-facts contribution policy line, and in live mode `CONTRIBUTING.md`, `.github/`, linked contributor docs, AI policy files, and relevant templates, look for restrictions on AI-assisted contributions. | Pass when the policy is silent or permits assistive AI subject to conditions such as disclosure, testing, human review, or personal understanding. Fail on an outright ban on AI-generated code or documentation. | required |
| Maintainer responsiveness | In the repo-facts maintainer first-response sample, or the equivalent live recently updated issue sample, inspect the days to the first owner/member/collaborator comment. | Preferred pass when at least 3 of the 5 sampled issues received a maintainer response within 30 days; otherwise preferred fail or unclear. This never changes the verdict. | preferred |

## Verdict rule

<!-- State how the grades above combine into accept or reject, and how
unclear is treated. Example shape (write your own): "accept if every
required check passes; preferred checks never change the verdict, they
rank accepted issues; unclear counts as fail." -->

Accept only when every required check passes. Preferred checks are reported
and may rank accepted issues, but never change the verdict. Treat `unclear`
as a fail for any required check; a missing or contradictory signal is not
enough evidence for a first contribution. The verdict is otherwise binary:
`accept` or `reject`.
