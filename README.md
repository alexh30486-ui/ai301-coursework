# AI301 — Open Source Contribution Coursework

**Student:** Alex Hernandez  
**GitHub username:** [alexh30486-ui](https://github.com/alexh30486-ui)  
**Course:** CodePath AI301 — Fall 2026

This repository contains my issue-selection skill, reproduction-check skill, evaluation records, and contribution write-ups.

| Unit | Work completed | Evaluation agreement |
| --- | --- | --- |
| Unit 1 — Issue Selection | Evaluated candidate issues and selected #73 | 20/20 — PASS |
| Unit 2 — Reproduction | Claimed and reproduced issue #62 | 18/20 — PASS |

These scores measure agreement with the course evaluation labels. They are not assignment grades.

## Start here

| Deliverable | Location |
| --- | --- |
| Unit 1 skill | [tools/issue-select](tools/issue-select/) |
| Unit 1 selection and analysis | [selection.md](beat-1-sandbox/unit-1/selection.md) |
| Unit 1 complete evaluation | [eval-run.txt](beat-1-sandbox/unit-1/eval-run.txt) |
| Unit 2 skill | [tools/repro-check](tools/repro-check/) |
| Unit 2 reproduction and analysis | [reproduction.md](beat-1-sandbox/unit-2/reproduction.md) |
| Unit 2 complete evaluation | [eval-run.txt](beat-1-sandbox/unit-2/eval-run.txt) |

The phase write-ups contain the detailed assignment responses. The evaluation files preserve the harness output.

## Repository structure

```text
tools/
├── issue-select/
│   ├── SKILL.md
│   ├── rubric.md
│   ├── scope.md
│   └── references/
│       └── evidence-guide.md
└── repro-check/
    ├── SKILL.md
    ├── rubric.md
    ├── scope.md
    ├── voice-guide.md
    └── references/
        └── evidence-guide.md

beat-1-sandbox/
├── unit-1/
│   ├── selection.md
│   └── eval-run.txt
└── unit-2/
    ├── reproduction.md
    └── eval-run.txt
```

## Unit 1 — Issue Selection

### Goal and decision

I developed an `issue-select` skill to evaluate whether an issue was a reasonable first contribution. Its required checks cover repository activity, repository use, newcomer scope, availability, and contribution-policy compatibility. Maintainer responsiveness is a preferred check.

I selected [issue #73](https://github.com/codepath/pathreview-ai301-fa26-s1/issues/73), which describes a disagreement between the README and `.env.example` about the LLM API key.

The live results accepted #73, #72, and #69. The skill ranked #72 and #69 higher for the configured Python and testing profile. I chose #73 because resolving one documentation/configuration mismatch offered a bounded first contribution.

### Evaluation history

Initial evaluation and live-selection attempts stalled and were terminated. I did not count those attempts as completed runs.

After refining the scope check:

1. A targeted evaluation of `issue-01`, `issue-19`, and `issue-20` matched **3/3** labels.
2. The complete evaluation matched **20/20** labels.
3. I preserved the complete harness output in the Unit 1 submission folder.

| Category | Matching verdicts |
| --- | ---: |
| Claimed | 4/4 |
| Clear accept | 8/8 |
| Dead repository | 3/3 |
| Policy | 1/1 |
| Scope | 4/4 |
| **Total** | **20/20** |

### Analysis: what the scope check measures

The scope check distinguishes one deliverable from several independent tasks. A change that updates two related files can still be manageable. A short issue description can also contain enough direction when the expected behavior and affected area are clear.

In the scored evaluation, `issue-19` received **accept** from both my rubric and the gold label. My analysis explains why the named causes and related suggestions describe work within one reported behavior rather than several independent deliverables.

The trade-off is hidden complexity. An apparently small documentation mismatch might depend on an unresolved configuration decision or changes across several providers. The rubric can evaluate the evidence supplied in the issue, but a passing scope check does not guarantee the implementation will be easy.

The exact check quotation, missed-case analysis, and proposed validation cases are recorded in [selection.md](beat-1-sandbox/unit-1/selection.md).

### Evidence limitation

The complete original three-issue live transcript was not preserved in this repository. The selected-issue JSON record in `selection.md` summarizes retained results; it should not be treated as a complete original transcript.

The saved 20-item evaluation is separate evidence and does not substitute for live-mode output.

## Unit 2 — Reproduction Check

### Issue and posted work

For Unit 2, I worked on [issue #62](https://github.com/codepath/pathreview-ai301-fa26-s1/issues/62), concerning a Redis health check that accesses settings absent from the configuration model.

This differs from the issue selected in Unit 1: #73 remains my recorded Unit 1 selection; #62 is the issue I actually claimed and reproduced in Unit 2.

- [My claim comment](https://github.com/codepath/pathreview-ai301-fa26-s1/issues/62#issuecomment-5804257717)
- [My reproduction comment](https://github.com/codepath/pathreview-ai301-fa26-s1/issues/62#issuecomment-5804391603)

Both links and the comment text appear in [reproduction.md](beat-1-sandbox/unit-2/reproduction.md).

### Reproduction environment

| Component | Recorded environment |
| --- | --- |
| Source commit | `f89c06f` |
| Operating system | macOS 26.6 |
| Python | 3.13 |
| Redis server | Redis 7 in Docker |
| PostgreSQL | PostgreSQL 16 on local port 5434 |
| Request method | FastAPI `TestClient`, using the repository's health router and real database dependency |

Port 5434 was used because port 5433 was already occupied.

### Observed behavior and interpretation

The run produced these observations:

```text
Redis PING: True
redis_host defined: False
redis_health_check_failed error="'Settings' object has no attribute 'redis_host'"
HTTP status: 503
Response dependencies: postgres=unhealthy, redis=unhealthy, vector_db=healthy
```

A direct Redis request succeeded using `settings.redis_url`. The health route accessed `settings.redis_host`, which the settings object did not define. The error therefore occurred before the Redis probe could connect.

The same request also encountered a separate PostgreSQL failure: SQLAlchemy rejected the route's raw `"SELECT 1"` query.

The HTTP 503 alone does not isolate the Redis bug. The successful direct Redis PING, missing attribute, and Redis-specific error log provide the evidence for #62. The PostgreSQL error explains the other unhealthy dependency.

### Evaluation history

The completed `repro-check` evaluation matched **18/20** gold verdicts and met the category floor.

| Category | Matching verdicts |
| --- | ---: |
| Clear accept | 6/8 |
| Disclosure | 1/1 |
| No evidence | 4/4 |
| Unfollowable communications | 3/3 |
| Wrong target | 4/4 |
| **Total** | **18/20** |

The disagreements were:

| Package | Gold verdict | My verdict | Check involved |
| --- | --- | --- | --- |
| `pkg-03` | Accept | Reject | `conventions` |
| `pkg-10` | Accept | Reject | `steps-followable` |

A later attempt using revised wording encountered errors on 15 packages. That partial run did not replace the saved complete evaluation. I restored the rubric and evidence guide corresponding to the saved run.

### Analysis: an honest failure to reproduce

My detailed package analysis focuses on `pkg-10`.

The candidate tested the Starship issue on Linux with zsh, while the reporter used macOS with fish. The directory module remained visible. The candidate disclosed the environment differences and reported that the attempt did not reproduce the symptom.

The gold label accepted that report. My evaluation rejected it under `steps-followable`.

This exposed an ambiguity: a reader can repeat a well-documented attempt even when that attempt does not reproduce the reported failure. An honest negative result can be useful evidence.

The trade-off is that loosening this check too far could accept a changed trigger as proof of the original bug. A report claiming successful reproduction still needs evidence of the reported behavior. A cannot-reproduce report needs repeatable steps, observed output, and a clear account of relevant differences.

The exact check quotations and proposed validation approach appear in [reproduction.md](beat-1-sandbox/unit-2/reproduction.md). These proposed changes are analysis, not a claim that a revised rubric completed another successful evaluation.

### Remaining limitations

The live `repro-check` runs on my claim and full reproduction package were not completed because Claude credits were unavailable. I have not claimed that the skill approved the posted comments.

My posted reproduction includes the tested commit, environment, request command, output, and expected behavior. It does not include every dependency-installation and service-start command. Those setup details would make reproduction from a clean environment easier.

## What I learned

The evaluation score and the quality of the evidence answer different questions. Agreement with a fixed set of labels helps test the rubric, while live work requires checking the actual environment and recording what happened.

Three practices mattered most:

1. **Separate completed runs from attempts.** A stalled or partial evaluation cannot replace a complete harness record.
2. **Compare the precise behavior.** An error response alone does not establish that the intended bug was reproduced.
3. **Explain the check's trade-off.** A useful reflection identifies what a rule catches, what it can miss, and how a revision would be tested.

## Submission

Submit the entire course repository:

[https://github.com/alexh30486-ui/ai301-coursework](https://github.com/alexh30486-ui/ai301-coursework)

The skill files, phase write-ups, and original evaluation records are linked above.
