# Unit 1 Issue Selection

## Issue analysis

I compared three open issues in the required Path Review repository:

| Issue | Skill verdict | Reason |
|---|---|---|
| [#73: README and `.env.example` disagree about which LLM API key to set](https://github.com/codepath/pathreview-ai301-fa26-s1/issues/73) | accept | Bounded 1–2 hour docs/config consistency fix; repository is active, issue is unassigned, and there are no comments or linked PRs. |
| [#72: `verify_password` raises `UnknownHashError` on malformed stored hashes](https://github.com/codepath/pathreview-ai301-fa26-s1/issues/72) | accept | Bounded 1–2 hour API bug fix with a covering test; unassigned and active repository. |
| [#69: Output parser crashes on a top-level JSON array fallback](https://github.com/codepath/pathreview-ai301-fa26-s1/issues/69) | accept | Bounded 2–4 hour parser bug fix with a covering test; unassigned and active repository. |

## Trade-offs

I chose [#73: README and `.env.example` disagree about which LLM API key to set](https://github.com/codepath/pathreview-ai301-fa26-s1/issues/73). The skill's verdict is **accept**. It is the easiest fit because it names two relevant files, explains the inconsistency, and estimates only 1–2 hours. The change should be narrowly limited to making `README.md` and `.env.example` agree with `core/config.py`.

Issue #72 is also small, but it changes security behavior and requires handling a malformed password hash correctly. Issue #69 is similarly bounded, but its parser fallback has more behavioral risk and a longer 2–4 hour estimate. I chose #73 because it has the smallest, clearest review surface while still being a real contribution.

The exact rubric check that supports this choice is:

> Pass if the request describes one identifiable change or bug fix with enough behavior, location, reproduction, or acceptance detail to begin implementation. Fail if it is a support question, umbrella/tracking issue, explicitly core-internal or codebase-wide work, or the thread leaves the design/specification materially unsettled.

## Run history

1. I filled `skill/rubric.md` with the required checks and verdict rule.
2. I ran the smoke evaluation with `python3 eval/run_eval.py --rubric skill/rubric.md --limit 3 --workers 1`. It stalled in the external evaluator and was terminated; it did not produce `eval-run.txt`.
3. I copied the skill to `~/.claude/skills/issue-select/`, set its `scope.md` to `codepath/pathreview-ai301-fa26-s1`, and added the fit profile.
4. I ran the live Claude command on issues #73, #72, and #69. It also stalled before returning the required fenced JSON block and was terminated.
5. I verified the live repository and issue state directly with GitHub: the repository is active and unarchived, and all three issues were open, unassigned, and had no comments or linked pull requests.

No `eval-run.txt` was created, so there is no saved full evaluation run to report.

## Reflection

The rubric made the decision by checking repository activity, repository availability, newcomer-sized scope, existing claims, and contribution-policy compatibility. Issue #73 has a concrete problem, names the relevant files, and provides an effort estimate, so its scope is easy to verify.

I did not comment on or claim the issue. Choosing it is separate from claiming it. In Unit 2, I will claim it using the course voice guide, set up the repository environment, reproduce or confirm the configuration mismatch, and then prepare the fix and tests appropriate to the project.
