# Unit 2: Reproduction Check

## Run history

I evaluated the installed `repro-check` rubric and evidence guide on all 20 scored packages. The completed run agreed with the gold verdicts on **18/20**, meeting the **18/20 PASS** bar. I saved that full run as `beat-1-sandbox/unit-2/eval-run.txt` and committed it with the skill files in commit `6928087`. Two packages disagreed: `pkg-03` failed my `conventions` check and `pkg-10` failed my `steps-followable` check, although both gold labels were `accept`.

I later tried revised wording, but Claude exited with errors on 15 packages. That attempt was a partial run, not a second full score; it did not overwrite the saved `eval-run.txt`. I restored the original rubric and evidence guide before copying the skill files into the coursework repository. The **18/20** run is the evaluation evidence for the committed version.

## Package analysis — `pkg-10`

`pkg-10` concerns Starship issue #7648, where the `directory` module reportedly disappears when a symlink points to a subdirectory inside a Git repository and `repo_root_style` is enabled. The candidate report does **not** claim to reproduce that failure. It describes Starship 1.26.0 on Ubuntu 24.04 with zsh 5.9, creates the Git repository and symlink layout, shows the `[directory]` configuration, and records a prompt in which the directory module remains visible. It also says that the original report used macOS and fish 4.7.1 and that those environment differences may matter. The claim comment promises further investigation on a matching environment rather than a fix or date.

The gold verdict is `accept`; my rubric returned `reject` for `steps-followable`. The report supplies enough information to repeat **the attempt it actually made** and is explicit that it did not reproduce the macOS/fish symptom. The evaluator appears to have treated a difference from the issue's original environment as a failure to follow the steps. That is stricter than the gold label's treatment of an honest cannot-reproduce report. The displayed `starship.toml` content is a reproducible input even though the transcript shows `cat` rather than the command that created the file. I would still reject a report that hid a required input, omitted the essential symlink/configuration trigger without saying so, or claimed to reproduce the bug using a different trigger.

## Check rationale

My `outcome-honest` check says: “A cannot-reproduce passes when it says so plainly, shows what it got, and names what differed from the issue (platform, version, data shape) or what a triggering setup likely needs.” `pkg-10` does those things: it says “cannot reproduce,” gives the visible prompt and `starship explain` result, and identifies the OS and shell differences.

My `steps-followable` check says: “A stranger with only public access could re-run every step from the stated starting state to the trigger: inputs, commands, and config are shown or publicly fetchable, and the trigger used is the same one the issue describes (same flag/operator/syntax/expression), not a variant.” The report shows the symlink, Git repository, and configuration. The tension is that the check does not explicitly say whether, for a **cannot-reproduce** report, the stranger must recreate the original reporter's platform or the candidate's disclosed attempt. I intended the latter while requiring an exact trigger for a claim of successful reproduction. That ambiguity explains the false rejection.

## Trade-offs and next step

I could clarify `steps-followable` so a disclosed, nonmatching environment can pass when the candidate honestly reports what happened and supplies repeatable steps for that attempt. I would keep the requirements for public inputs, the issue's essential trigger, and evidence matching any claim of successful reproduction. This preserves protection against plausible reports that actually test a different command or private setup.

The saved rubric already passed at 18/20. I did **not** replace it with wording that lacks a completed full evaluation: the later partial run cannot establish whether a change improves `pkg-10` without regressing other packages. A future revision would need a successful complete run, including checks on cases from the categories it might affect. The Starship report here is an evaluation package, not an observation I personally made or a comment to post upstream.

## Live issue #62

Issue: https://github.com/codepath/pathreview-ai301-fa26-s1/issues/62

Live `repro-check` run: not completed because Claude credits were unavailable.

### Claim comment

Link: https://github.com/codepath/pathreview-ai301-fa26-s1/issues/62#issuecomment-5804257717

I’d like to investigate #62. The issue points to the Redis probe in `api/routes/health.py` reading `settings.redis_host` and `settings.redis_port`, while `Settings` defines `redis_url` instead.

I’ll reproduce `GET /health` with Redis running, record my environment and the response and logs I actually observe, then report the steps and findings here before proposing a change.

### Reproduction comment

Link: https://github.com/codepath/pathreview-ai301-fa26-s1/issues/62#issuecomment-5804391603

I reproduced the Redis health-check failure on macOS 26.6, Python 3.13, at commit f89c06f. Redis 7 was running, and redis-cli ping returned PONG. PostgreSQL 16 was running on local port 5434 because port 5433 was occupied.
I called the repository’s /health route with FastAPI’s TestClient and its real database dependency:

env DATABASE_URL='postgresql+asyncpg://pathreview:pathreview@localhost:5434/pathreview_dev' .venv/bin/python - <<'PY'
import redis
from fastapi import FastAPI
from fastapi.testclient import TestClient
from api.routes.health import router
from core.config import settings

print("Redis PING:", redis.Redis.from_url(settings.redis_url).ping())
print("redis_host defined:", hasattr(settings, "redis_host"))

app = FastAPI()
app.include_router(router)
response = TestClient(app).get("/health")
print("HTTP status:", response.status_code)
print("Response:", response.json())
PY
Relevant output:
Redis PING: True
redis_host defined: False
redis_health_check_failed error="'Settings' object has no attribute 'redis_host'"
HTTP status: 503
Response dependencies: postgres=unhealthy, redis=unhealthy, vector_db=healthy
I expected the reachable Redis service to be reported healthy. The Redis probe instead fails before connecting because it reads settings.redis_host, while Settings defines redis_url.
This run also logged a separate PostgreSQL failure: SQLAlchemy rejected the route’s raw "SELECT 1" query. The 503 response therefore has two causes in this run. The successful Redis PING, missing attribute check, and Redis error log are the evidence specific to #62.
