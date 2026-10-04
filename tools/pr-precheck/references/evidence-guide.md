# Evidence guide: where evidence lives in a PR package

## Plan fidelity (harness category: silent-drift)
Eval: pair plan-context scope, exclusions and deviations with candidate diff, commits and description. Live: read course plan.md, posted plan, issue and complete default-branch three-dot diff. Map each behavior to a commitment or deviation; identify missing promised work.

## Test evidence (harness category: not-tested)
Eval: pair test-evidence commands and observed before/after with repro, plan expectations and repo-facts checks. Live: read captured output and its revision/environment, added tests, README, CONTRIBUTING, project scripts and CI. Record command, result and exercised path. Distinguish mock evidence from integration proof and unrelated failures from target failures.

## Diff quality (harness category: unreviewable)
Inspect every supplied hunk and commit. Live: also inspect status; untracked notes are not automatically in the PR. Identify unrelated churn, debug leftovers and experiments. Necessary tests and supporting changes belong.

## Standards and comms (harness category: standards-wall)
Eval: read repo-facts template, policy, assistance assumptions and thread. Live: read actual PR template, contribution documents, linked policies, issue thread and scope. Pair every obligation with real draft content. Required disclosure must appear. Report voice notes separately.
