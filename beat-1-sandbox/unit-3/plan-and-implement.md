# Unit 3: Plan and implement

GitHub username: `alexh30486-ui`

Issue: https://github.com/codepath/pathreview-ai301-fa26-s1/issues/62

Branch: `fix/62-redis-health-check` in my fork `alexh30486-ui/pathreview-ai301-fa26-s1`

Build commit: `5fe8844` — Fix Redis health check to use configured URL

## Plan comment

Link: https://github.com/codepath/pathreview-ai301-fa26-s1/issues/62#issuecomment-5896417466

My [reproduction of #62](https://github.com/codepath/pathreview-ai301-fa26-s1/issues/62#issuecomment-5804391603) at `f89c06f` included these results from the direct Redis check and `GET /health`:

```text
Redis PING: True
redis_host defined: False
redis_health_check_failed error="'Settings' object has no attribute 'redis_host'"
HTTP status: 503
Response dependencies: postgres=unhealthy, redis=unhealthy, vector_db=healthy
```

The route reads `redis_host` and `redis_port`, while `Settings` defines `redis_url`.

I plan to build the health check's Redis client from `settings.redis_url`, keep its existing `ping()` and failure handling, and add a focused check for reachable and unreachable Redis. I will rerun my Unit 2 request and inspect `dependencies.redis`: after the change, reachable Redis should be reported healthy without the missing-attribute error.

The same request also has a separate PostgreSQL raw-SQL failure, so the endpoint may still return 503. I will leave that issue outside this Redis change and report the Redis result separately. If the build requires a different approach, I will record what changed and why before updating this thread.

## Evidence

Before, on commit `f89c06f`, macOS 26.6 and Python 3.13, with Redis 7 reachable and PostgreSQL 16 on port 5434, my Unit 2 request through the real health router and database dependency recorded:

```text
Redis PING: True
redis_host defined: False
redis_health_check_failed error="'Settings' object has no attribute 'redis_host'"
HTTP status: 503
Response dependencies: postgres=unhealthy, redis=unhealthy, vector_db=healthy
```

After the change on `fix/62-redis-health-check`, I repeated the FastAPI `TestClient` GET `/health` with `DATABASE_URL=postgresql+asyncpg://pathreview:pathreview@localhost:5434/pathreview_dev` and a direct Redis `PING`:

```text
postgres_health_check_failed error="Textual SQL expression 'SELECT 1' should be explicitly declared as text('SELECT 1')"
redis_health_check_passed
vector_db_health_check_passed
HTTP status: 503
Dependencies: {'postgres': 'unhealthy', 'redis': 'healthy', 'vector_db': 'healthy'}
REDIS FIX: PASS
```

The focused route tests for reachable and unreachable Redis returned `2 passed, 4 warnings in 0.62s` with `.venv/bin/python -m pytest -q tests/unit/test_health_redis.py`. The overall 503 persists because PostgreSQL fails independently. The Redis-specific log and dependency status changed as the plan predicted. The code and tests were committed and pushed to my fork as `5fe8844`.

## Run history

1. I installed the Unit 3 `plan-check` skill and filled its `rubric.md`, `references/evidence-guide.md`, and `procedure.md`; I carried forward and extended my Unit 2 voice guide. The installed copy is the one intended for live and eval grading.
2. I manually reviewed `calib-01` through `calib-04` against the rubric, then compared my accept/reject calls with the four gold labels: all four matched. Calibration items are not scored in the 20-package run.
3. After reading the scored-set convention guidance, I clarified in all three authored components that the Unit 3 eval treats every candidate package as AI-assisted. Explicit repo disclosure rules must therefore be applied to the candidate plan comment. This clarification was installed before any full Unit 3 eval.
4. I attempted a live `plan-check` run on the #62 draft. Claude stopped after one second with `You've hit your individual spend limit`; no per-check grades or JSON verdict were produced. I manually checked the draft and posted the plan comment. I do not represent the manual check as a successful live skill run.
5. **Full evaluation: pending.** No Unit 3 `eval-run.txt` has been generated. When credits become available, run the complete harness against this installed rubric and evidence guide, examine its disagreements and category floor, and copy only its harness-written complete `eval-run.txt` into this directory. Record the actual score and any subsequent changes here; never invent or hand-edit that run.

## Package analysis

The manual calibration item `calib-03` (bat #3831) earned gold `reject` and my manual `reject`: its proposed pager binding change cannot explain a 25.8-second run with no pager involved, while disabling highlighting cuts it to about 0.2 seconds. This is **calibration, not a scored package**. Replace this paragraph after the full evaluation with one scored `pkg-XX`, its gold verdict, the skill's actual verdict, and an evidence-based explanation of why the check reached that result.

## Check rationale

The installed `diagnosis-grounded` rubric says: “Pass when the diagnosis explains the observed behavior without contradicting the supplied evidence. A hypothesis may pass when labeled uncertain and paired with a concrete check before the dependent implementation. Fail when the plan ignores decisive evidence or asserts a cause the evidence contradicts.” The `calib-03` no-pager timing is decisive counterevidence to its pager-binding diagnosis. After a full evaluation, connect this exact check or another verbatim quoted check from the uploaded rubric to one scored package's actual result. If the rubric changes, update the quotation to match the submitted file.

## Trade-offs

This check prevents a confident but incorrect thread diagnosis from overruling a controlled reproduction. It can reject a useful exploratory plan if the cause is genuinely uncertain and the plan never states a concrete discriminating check. The rubric permits a labeled hypothesis with such a check. A future loosening should be tested against a scored wrong-cause package and a clear accept canary before a confirming full run; the final write-up will name the actual packages and results once the eval is available.

## Plan deviations

No deviations. The build used `settings.redis_url` in the Redis probe and added focused route tests as stated in the plan. The real health request confirmed Redis healthy while the separate PostgreSQL issue still produced 503. See [plan.md](plan.md) for the full plan and build notes.
