# Plan for Path Review issue #62

Issue: https://github.com/codepath/pathreview-ai301-fa26-s1/issues/62

Code branch in my fork: `fix/62-redis-health-check`

## Evidence and diagnosis

At commit `f89c06f`, on macOS 26.6 with Python 3.13, my direct Redis `PING` succeeded, but `GET /health` logged `redis_health_check_failed error="'Settings' object has no attribute 'redis_host'"` and reported `redis: unhealthy`. In `api/routes/health.py`, the Redis check constructs `redis.Redis` using `settings.redis_host` and `settings.redis_port`; `core/config.py` defines `redis_url` instead. The missing attribute raises before the Redis connection attempt. The same request also reported PostgreSQL unhealthy because the separate SQLAlchemy check rejects its raw `"SELECT 1"` string. That independent failure means an overall HTTP 503 does not by itself prove whether the Redis fix worked.

## Scope and implementation

1. In `api/routes/health.py`, create the Redis client from the configured `settings.redis_url` using `redis.Redis.from_url(settings.redis_url, decode_responses=True)` and retain its `ping()` call. Inspect existing Redis client construction before editing to ensure this follows the repository's configuration convention.
2. Keep the existing Redis error handling and the response's dependency keys. Do not change `Settings` or add parallel `redis_host` and `redis_port` fields for a URL that already exists.
3. Add a focused health-route regression check if the repository's test dependencies support it. The check should exercise the route with a reachable Redis target and assert `dependencies.redis == "healthy"`; also check that a failed Redis connection still reports `dependencies.redis == "unhealthy"`. Do not make an assertion about the overall HTTP status while the independent PostgreSQL check remains broken.

This plan excludes the PostgreSQL raw-SQL issue, vector database behavior, and unrelated health-route cleanup.

## Validation

Before editing, preserve the Unit 2 baseline: direct Redis `PING: True`, `redis_host defined: False`, the Redis attribute error, and Redis reported unhealthy. After editing, rerun the same FastAPI `TestClient` request with the real database dependency and the same Redis and PostgreSQL setup. Expect direct Redis `PING: True`, no missing-attribute Redis error, and `dependencies.redis == "healthy"`. PostgreSQL may still be unhealthy and the overall endpoint may still return 503; inspect the Redis dependency in the response detail separately. Run the focused regression check as well, recording its actual command and output. Keep the before/after output in `plan-and-implement.md`.

## Risks and decision points

Confirm that `redis.Redis.from_url` accepts the configured URL and `decode_responses` argument in the installed Redis client. If testing through the route requires adjusting dependencies, keep that change limited to the regression test. A failure in the PostgreSQL probe should remain visible and must not be counted as failure of the Redis change.

## Deviations from posted plan

The build has not started. After implementation, record either “No deviations” with what was built or each change to the approach, why it was necessary, and any follow-up posted on the issue. Do not leave this section in its current state for final submission.
