# Unit 1 — Issue Selection

## Selected issue

**Selected issue:** #73 — README and `.env.example` disagree about which LLM API key to set

**Issue link:** https://github.com/codepath/pathreview-ai301-fa26-s1/issues/73

**Verdict:** Accept

I selected issue #73 as my first contribution because it describes a concrete configuration/documentation mismatch involving two named files. The requested change has a bounded review surface and can be understood without requiring a large architectural change. The issue also includes an effort estimate, which makes the expected contribution size easier to assess.

I did not comment on or claim the issue during Unit 1. Selection is separate from claiming the issue. I will claim it in Unit 2 before beginning implementation.

## Issue analysis

| Issue | Verdict | Analysis |
|---|---|---|
| #73 | Accept | The issue identifies a specific disagreement between the README and `.env.example`. It names the relevant files and provides a concrete problem to resolve. The requested work is bounded and has a small review surface. |
| #72 | Accept | The issue concerns `verify_password` raising `UnknownHashError` for malformed stored hashes. It describes a concrete behavior problem, but the implementation touches authentication/password-handling behavior, so it has a more security-sensitive review surface than #73. |
| #69 | Accept | The issue describes an output-parser crash when the fallback response is a top-level JSON array. It identifies a concrete parser behavior problem, but parser behavior is more implementation-sensitive than the documentation/configuration mismatch in #73. |

## Check rationale

For issue #73, I evaluated the required checks from the issue-selection rubric.

### Repository activity

The repository was verified as active and unarchived. This means the issue is in a repository that is currently being maintained rather than an archived repository.

### Repository availability

The issue was open, unassigned, and available to claim. I did not find an existing claimant.

### Bounded newcomer scope

The issue describes one identifiable deliverable: resolving the disagreement between the README and `.env.example` regarding the LLM API key. The relevant files are named in the issue, which makes the review surface clear.

The rubric's bounded-scope check is:

> "Pass when the issue describes one bounded deliverable that a newcomer could begin implementing from the information provided."

Issue #73 meets that description. The fact that the change involves two files does not make it an umbrella issue because both files are part of the same configuration/documentation mismatch.

### Existing claims

The issue was open and unassigned when I checked it. I did not claim it during Unit 1.

### Contribution-policy compatibility

The live issue-selection check also considered whether the contribution was compatible with the repository's contribution policy. Issue #73 was compatible with the policy checks used by the skill.

## Trade-offs

I compared #73 with #72 and #69 rather than selecting an issue solely because it was the first candidate.

Issue #72 involves password verification behavior and therefore has a more security-sensitive implementation surface. Issue #69 involves parser behavior and requires reasoning about fallback JSON handling. Issue #73 is narrower: the problem is a disagreement between two explicitly named configuration/documentation files.

The trade-off is that #73 is primarily a documentation/configuration consistency change rather than a deeper code-behavior fix. I chose it because the first contribution benefits from a clearly bounded problem and a straightforward review surface.

## Selection rationale

I selected #73 because it is the clearest bounded first contribution among the three candidates I evaluated. The issue has a concrete problem statement, identifies the relevant files, and has an understandable expected outcome. The change can be reviewed by comparing the README and `.env.example` and confirming that they consistently describe the required API-key configuration.

This choice also keeps the first contribution separate from the more security-sensitive password behavior in #72 and the parser behavior in #69.

## Run history

1. I filled `skill/rubric.md` with the required checks and verdict rule.

2. I initially ran a smoke evaluation from the starter repository. The external evaluator stalled and that attempt was terminated.

3. I installed the `issue-select` skill to `~/.claude/skills/issue-select/`, configured `scope.md` for `codepath/pathreview-ai301-fa26-s1`, and added the repository fit profile.

4. I ran the live Claude issue-selection command against issues #73, #72, and #69. The initial attempt stalled before returning the expected result and was terminated.

5. I verified the repository and issue state directly with GitHub. The repository was active and unarchived, and the three candidate issues were open, unassigned, and had no comments or linked pull requests at the time of that check.

6. I revised the bounded-newcomer-scope rubric check to distinguish a single bounded deliverable from umbrella issues and to define explicit failure conditions.

7. I ran a targeted evaluation of issues #01, #19, and #20 after the rubric revision. The result was:

   `agreement: 3/3 scored items`

8. I then ran the required full evaluation with 20 scored issues. The final result was:

   `agreement: 20/20 scored items (bar: 18/20: PASS)`

9. The final evaluation run was saved to `eval/eval-run.txt` and copied to the required assignment location:

   `beat-1-sandbox/unit-1/eval-run.txt`

## Final evaluation output

The final full evaluation produced the following results:

```text
issue-01 accept accept yes
issue-02 reject reject yes
issue-03 reject reject yes
issue-04 accept accept yes
issue-05 reject reject yes
issue-06 accept accept yes
issue-07 reject reject yes
issue-08 reject reject yes
issue-09 accept accept yes
issue-10 reject reject yes
issue-11 accept accept yes
issue-12 reject reject yes
issue-13 reject reject yes
issue-14 accept accept yes
issue-15 reject reject yes
issue-16 accept accept yes
issue-17 reject reject yes
issue-18 reject reject yes
issue-19 accept accept yes
issue-20 reject reject yes

categories: claimed 4/4 clear-accept 8/8 dead-repo 3/3 policy 1/1 scope 4/4
agreement: 20/20 scored items (bar: 18/20: PASS)
run written to eval-run.txt