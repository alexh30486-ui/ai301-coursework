# Unit 4: Pull request

## GitHub username
alexh30486-ui

## Issue
https://github.com/codepath/pathreview-ai301-fa26-s1/issues/62

## Pull request
https://github.com/codepath/pathreview-ai301-fa26-s1/pull/86

## Branch
fix/62-redis-health-check

## Own precheck verdict
Accept. The final live check ran after adding the unit marker and pushing commit 10d7400. All seven required checks passed.

### Saved live output

pr-precheck: live mode, issue #62, branch fix/62-redis-health-check at 10d7400
Target: codepath/pathreview-ai301-fa26-s1 main (in scope per scope.md)
Base: refs/remotes/course/main = upstream main = f89c06f (current, not stale)

Summary
- Diff: 3 files, 3 commits. api/routes/health.py builds the client with
  redis.Redis.from_url(settings.redis_url, decode_responses=True); pyproject.toml
  drops only "attr-defined" for api.routes.health; new
  tests/unit/test_health_redis.py (pytestmark = pytest.mark.unit) covers reachable
  and unreachable Redis, asserts dependencies.redis and the exact from_url call.
  Matches plan steps 1-3 plus the recorded Unit 4 deviation. No debris;
  repro-62-output.txt is untracked and not in the PR.
- Before (f89c06f, repro-62-output.txt):
  redis_health_check_failed error="'Settings' object has no attribute 'redis_host'",
  redis: unhealthy. After (repro-62-after.txt): redis_health_check_passed,
  redis: healthy, postgres still unhealthy as the plan predicted.
- Evidence: make test-unit (pytest tests/unit -v -m unit) 377 passed, 53 xfailed,
  both test_health_redis.py tests PASSED (unit4-marked-tests.txt); earlier
  pytest tests/unit 377 passed, 53 xfailed; ruff "All checks passed!"; mypy
  "Success: no issues found in 76 source files"; black 111 files unchanged;
  frontend 18 passed; integration collected 0 items, exit 5, disclosed as no
  pass claimed.
- Template: every section filled; CI box honestly unchecked (pending open);
  seeded-bug box checked, no health xfail marker exists in tree; AI assistance
  disclosed. docs/CONTRIBUTING.md has no explicit AI policy; scope.md house rule
  requires disclosure, satisfied.
- Thread: TF ZJShown's plan comment proposes the identical from_url fix. No
  maintainer requests. No new comments since 2026-10-03T14:50Z. Classmate parallel
  work is non-blocking.

Voice notes (do not affect verdict)
- No rule broken. Description names the specific symptom, shows the before/after
  artifact before claiming the fix, says what differed (postgres 503), discloses
  AI help in one sentence, promises nothing beyond the delivered change.
- Minor: the after-output block does not state its commit hash. Optional.

```json
{
  "item": "https://github.com/codepath/pathreview-ai301-fa26-s1/issues/62",
  "checks": [
    {"name": "plan-fidelity", "grade": "pass",
     "evidence": "Diff touches only health.py from_url swap, attr-defined suppression removal, and new marked route tests; plan steps 1-3 plus the recorded Unit 4 deviation cover all three, PostgreSQL excluded as planned."},
    {"name": "description-faithful", "grade": "pass",
     "evidence": "Claims match diff and output: make test-unit '377 passed, 53 xfailed' with both test_health_redis.py tests PASSED, mypy 'Success: no issues found', integration 'collected 0 items' disclosed, CI box left unchecked as pending."},
    {"name": "regression-evidence", "grade": "pass",
     "evidence": "Before at f89c06f: redis_health_check_failed \"'Settings' object has no attribute 'redis_host'\"; after: redis_health_check_passed, dependencies redis 'healthy' via real TestClient route; mock tests labeled as mocks."},
    {"name": "repository-checks", "grade": "pass",
     "evidence": "make test-unit 377 passed, ruff 'All checks passed!', mypy clean, black '111 files would be left unchanged', frontend '18 passed'; integration 'no tests ran' exit 5 explained and not attributable to the diff."},
    {"name": "diff-reviewable", "grade": "pass",
     "evidence": "Three hunks, three commits, no debug prints or experiments; untracked repro-62-output.txt is not committed."},
    {"name": "template-and-disclosure", "grade": "pass",
     "evidence": "All template sections filled with real content; seeded-bug suppression removed and no health xfail marker exists; description states 'I used ChatGPT ... and Claude Code ...'."},
    {"name": "thread-engagement", "grade": "pass",
     "evidence": "No maintainer requests in 24 comments; TF plan comment 5876517744 proposes the same from_url fix; classmate parallel PRs are non-blocking under house rules."}
  ],
  "verdict": "accept"
}
```

## Posted PR description

## Summary
Fix the Redis health probe to build its client from `settings.redis_url`. Previously it accessed nonexistent `redis_host` and `redis_port` settings, reporting reachable Redis as unhealthy.

## Issue
Closes #62

## Changes
- Replace the Redis host/port constructor with `Redis.from_url`, preserving `ping()` and failure handling.
- Add route tests for reachable and unreachable Redis, marked `pytest.mark.unit` so `make test-unit` selects them.
- Remove the obsolete `attr-defined` suppression for the health module.
- Record the suppression cleanup as a deviation in the course plan.

## Testing
- [ ] **CI is green on this PR (all five jobs)** — pending until the PR is opened.
- [x] Unit tests pass: `make test-unit` (`pytest tests/unit -v -m unit`) — 377 passed, 53 xfailed; both `tests/unit/test_health_redis.py` tests reported `PASSED`. Earlier full-directory run `python -m pytest tests/unit -q --tb=short` (the CI command) — 377 passed, 53 xfailed.
- [ ] Integration tests pass (`make test-integration`) — attempted; collected zero tests, pytest exited 5. No integration-suite pass is claimed.
- [x] Linter passes (`make lint`).
- [x] Type checker passes (`make typecheck`), including after suppression removal.
- [x] New tests cover reachable and unreachable Redis.
- [x] Seeded-bug cleanup: removed the matching `attr-defined` suppression. No existing health-test `xfail` marker was found.
- Formatting: `black --check .` — 111 files unchanged.
- Frontend: `npm ci` then `npm test -- --run` — 18 tests passed.

## Screenshots / Demo
Reproduction steps and environment:
https://github.com/codepath/pathreview-ai301-fa26-s1/issues/62#issuecomment-5804391603

macOS 26.6, Python 3.13, Redis 7, PostgreSQL 16 on local port 5434. The request used FastAPI TestClient with the actual health router and database dependency.

Before at `f89c06f`:
```text
Redis PING: True
redis_host defined: False
redis_health_check_failed error="'Settings' object has no attribute 'redis_host'"
HTTP status: 503
Dependencies: postgres=unhealthy, redis=unhealthy, vector_db=healthy
```

After the Redis code change:
```text
redis_health_check_passed
HTTP status: 503
Dependencies: {'postgres': 'unhealthy', 'redis': 'healthy', 'vector_db': 'healthy'}
REDIS FIX: PASS
```

## Notes for Reviewers
The remaining 503 comes from the separate PostgreSQL raw `SELECT 1` check. This PR verifies Redis's dependency status independently and leaves that PostgreSQL issue outside its scope.

The focused route tests mock Redis responses; the separate manual reproduction used reachable Redis and the real database dependency. The repository's integration suite collected no tests. npm also reported dependency vulnerabilities during installation; this PR does not change frontend dependencies.

Plan:
https://github.com/codepath/pathreview-ai301-fa26-s1/issues/62#issuecomment-5896417466

AI assistance: I used ChatGPT to help draft the plan, code, tests, and PR text, and Claude Code for tool evaluation and the PR precheck. I ran the commands and reviewed the results myself.

## Run history

1. I installed pr-precheck and filled its frame, rubric, procedure and evidence guide, carrying forward my voice guide.
2. I manually reviewed calib-01 and calib-04. Their accept and reject judgments matched the calibration labels. These were manual checks, not scored harness runs.
3. I ran the complete 20-package harness. It returned 19/20 PASS and wrote eval-run.txt. Categories matched: clear-accept 6/7, not-tested 4/4, silent-drift 4/4, standards-wall 2/2, unreviewable 3/3.
4. The only disagreement was pkg-16, rejected on description-faithful although its gold label was accept. I inspected the package and retained the passing tool without further revisions or full evaluation runs.
5. The first live attempt was blocked by file and command permissions. I reran interactively, where all seven checks passed.
6. I added the recommended unit marker so the documented make test-unit target includes both Redis tests. That target passed with 377 passed and 53 xfailed. I pushed 10d7400 and reran the live precheck; every check passed again.
7. I opened PR #86 from my fork against the course repository and saved the final verdict, description and complete harness run in my coursework repository.

## Package analysis

Scored package pkg-16, minikube #23471, had gold accept and my tool reject on description-faithful. Its evidence shows corrupt image input changing from silent exit 0 to a visible error and exit 1; a valid image still loads successfully, and the touched Go package tests pass.

The description explicitly defers changes to start-time failure policy. The shared loader now returns an error when every target fails but still tolerates partial success. I interpret the disagreement as my tool reading the description's statement about tolerant start behavior more broadly than the gold label did. The harness table identifies the failed check but does not preserve its detailed deciding evidence, so this interpretation is not a claim about the grader's exact reasoning. The gold acceptance recognizes the disclosed boundary and verified targeted fix.

## Check rationale

The description-faithful check in my submitted rubric reads:

> Pass when claims match delivered changes and observed outcomes, including material limitations. Fail for contradicted or unsupported success claims.

This check compares claims with the actual diff and observed output. It catches unsupported success claims while requiring material limitations to be disclosed. In pkg-16, the targeted behavior was demonstrated and the deferred start-time policy was explicitly described; that makes the rejection worth examining rather than treating the gold acceptance as permission to conceal limitations.

## Trade-offs

A strict description-fidelity check can catch misleading claims about a shared code path, but it may also reject a useful bounded fix whose description honestly defers a broader decision. It cannot establish untested caller behavior from a short diff alone. I kept the evaluated rule and recorded this disagreement instead of changing the tool after its passing run. No check was loosened, so no canary rerun was needed; a future revision should test both an honest-limitation case such as pkg-16 and a silent-drift reject before a confirming full run.

## Reflection: what changed during preparation?

The Redis implementation followed the posted plan. During PR preparation I removed the matching attr-defined suppression and recorded that cleanup in plan.md. I also added a unit marker so both new route tests run under make test-unit. These changes support the same Redis fix without changing the separate PostgreSQL behavior.

## Reflection: what evidence gives me confidence?

The manual reproduction used reachable Redis and the real health router and database dependency. Redis changed from unhealthy with a missing-attribute error to healthy. The two route tests cover reachable and unreachable Redis. The full unit suite, lint, type checking, formatting and frontend tests passed.

## Reflection: what limitations remain?

The endpoint can still return 503 because the separate PostgreSQL raw-SQL check fails. The focused tests mock Redis; the manual reproduction supplies the real-service evidence. The integration command collected zero tests and exited 5, so I do not claim an integration-suite pass. CI was pending when the draft was checked and the PR opened. npm reported dependency vulnerabilities; this PR does not change those dependencies.
