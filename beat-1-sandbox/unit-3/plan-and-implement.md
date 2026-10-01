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

1. I installed plan-check, filled the rubric, evidence guide, and procedure, and carried forward my voice guide.
2. I manually graded the four calibration packages and matched all four gold labels. These were manual calibration results, not scored harness results.
3. I clarified that every Unit 3 eval package is treated as AI-assisted and that explicit repository disclosure requirements must be enforced.
4. My live plan-check attempt was blocked by the individual spend limit and produced no verdict. I manually reviewed and posted the plan; I do not claim that the live skill approved it before posting.
5. The first full evaluation attempt errored on all 20 packages. A diagnostic revealed an expired OAuth session. No complete evaluation file was saved.
6. After restoring authentication, the full harness returned 20/20 PASS and saved eval-run.txt. Categories matched: clear-accept 7/7, scope-creep 4/4, thread-convention 2/2, unbuildable 3/3, wrong-cause 4/4. No further revisions or evaluation reruns were needed.

## Package analysis

For scored package pkg-20, the gold verdict was reject and my skill returned reject. The plan was technically strong and followed the thread, but the repository explicitly required disclosure of AI assistance and the candidate comment omitted it. All Unit 3 evaluation packages are treated as AI-assisted, so the missing disclosure was a demonstrated policy violation.

## Check rationale

The conventions check in my submitted rubric reads:

> Pass when applicable explicit requirements are met, including AI disclosure only when required. Fail for a demonstrated violation or a prohibited contribution. Missing evidence of a required condition is unclear. Silence is not a disclosure requirement; polished prose is not evidence of AI authorship. A human-own-words rule alone does not prove a violation.

This check explains pkg-20's rejection: a strong technical plan does not satisfy a separate, explicit disclosure requirement. The check also avoids inventing disclosure requirements for repositories whose policies are silent.

## Trade-offs

This check can hold an otherwise buildable plan because its comment violates an explicit contribution policy. It does not infer authorship from polished writing. A limitation is that a frozen package may omit a policy; live mode therefore reads the actual contribution documents. I made no changes after the 20/20 run, so no canary rerun was needed. If I later loosen disclosure handling, pkg-20 would be a canary before a confirming full run.

## Plan deviations

No deviations. The build used `settings.redis_url` in the Redis probe and added focused route tests as stated in the plan. The real health request confirmed Redis healthy while the separate PostgreSQL issue still produced 503. See [plan.md](plan.md) for the full plan and build notes.
