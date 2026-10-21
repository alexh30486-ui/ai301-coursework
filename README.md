# AI301 — Open Source Contribution Coursework

**Student:** Alex Hernandez

**GitHub username:** [alexh30486-ui](https://github.com/alexh30486-ui)

**Course:** CodePath AI301 — Fall 2026

**Documentation reviewed:** October 21, 2026

This repository follows my progression from classroom issue selection and reproduction to a real C# contribution in the .NET MAUI Community Toolkit. The earlier work developed evaluation rubrics and communication tools. The real contribution applied those ideas to an existing project's analyzer/code-fix tooling, exposed a gap in what the tests checked, and resulted in a merged two-file change.

**Start with the [Assignment 5 contribution story](beat-2-contribution/contribution-story.md).** That file contains the graded account: selection, reproduction, source analysis, plan changes, tests, public discussion, PR, four weekly Toolkit entries, and reflection. This root README provides navigation and context; it does not replace the required story at its exact path.

## Real contribution: CommunityToolkit/Maui #879

| Item | Public record or documented result |
| --- | --- |
| Original issue | [UseCommunityToolkitInitializationAnalyzer is not tested — #879](https://github.com/CommunityToolkit/Maui/issues/879) |
| My investigation and claim | [Issue comment](https://github.com/CommunityToolkit/Maui/issues/879#issuecomment-6098129467) |
| Pull request | [CommunityToolkit/Maui #3343](https://github.com/CommunityToolkit/Maui/pull/3343) |
| Human review | [TheCodeTraveler's APPROVED review](https://github.com/CommunityToolkit/Maui/pull/3343#pullrequestreview-5479894783) |
| Final contribution commit | [`91583887`](https://github.com/alexh30486-ui/Maui/commit/915838870f6bb95cfc3993dbc895a8016ba34b9f) |
| Implementation size | Two files; 52 insertions and one deletion |
| Test totals | 16 baseline project tests; 17 after adding one regression |
| Target-class coverage | One ID assertion plus five analyzer-behavior tests; one code-fix test added |
| Outcome | PR merged October 10, 2026; issue closed as completed |
| Later tool work | Scout and orientation October 17; monitor October 21; explicitly retrospective |

### The problem in plain language

The analyzer points out missing toolkit initialization, and its code fix offers to insert the missing call. The existing tests checked the diagnostic identifier and when the analyzer should report a problem, but none applied the offered edit and inspected the edited source. Those are different responsibilities: correctly noticing a missing step does not establish that the proposed repair puts the step in the right place.

My new regression test applied the provider to a builder chain ending in `Build()`. It expected toolkit initialization on the builder before the application is built. The old provider instead appended initialization after `Build()` because it selected the outermost invocation in the chain.

```csharp
// Expected fixed call order:
MauiApp.CreateBuilder()
    .UseMauiApp<Microsoft.Maui.Controls.Application>()
    .UseMauiCommunityToolkit()
    .Build();

// Old generated order observed in the verifier difference:
MauiApp.CreateBuilder()
    .UseMauiApp<Microsoft.Maui.Controls.Application>()
    .Build()
    .UseMauiCommunityToolkit();
```

`UseMauiCommunityToolkit` is declared for `MauiAppBuilder`, while `Build()` produces `MauiApp`. The source therefore supports the receiver-mismatch explanation. The directly executed observation was a generated-source difference in the Roslyn verifier; I did not separately compile the generated snippet as a standalone application or verify the action interactively in an IDE.

The submitted provider change selects the syntax node at the diagnostic's full span through `FindNode(diagnosticSpan, getInnermostNodeForTie: true)`. The new regression verifies the diagnostic location, the added import, and the expected normalized fixed source. The [contribution story](beat-2-contribution/contribution-story.md#understanding-the-issue) explains the source relationships and test boundary in detail.

### What the results establish

| Observation | Supported interpretation |
| --- | --- |
| Existing project passed 16 tests | Baseline was green, but the original offered edit was not covered |
| New regression failed with old provider | The test detected the wrong generated call order |
| Same regression passed after span selection | The submitted change corrected that exercised edit |
| Full Debug and Release reports show 17 passed | Existing project tests and the added regression passed in the recorded runs |
| Repository-derived local checks passed | Selected formatting/build/test scope was checked; broader exclusions remain disclosed |
| Human approval and merge | The maintainer accepted the contribution; this is separate from local tool verdicts |

The detailed account distinguishes early check logs from final-commit evidence, local commands from CI jobs, and observed test output from source-based conclusions. It also records a later reproduction attempt blocked by package-audit errors before tests ran. That later setup failure is not counted as a reproduction of the code-fix defect.

### Where the AI toolkit helped and where it fell short

| Phase | Actual use and limitation |
| --- | --- |
| Original selection | Manual reading; no contemporaneous scout verdict for the Maui issue |
| Investigation and implementation | ChatGPT helped read code and draft the test/change; its first `.First()` proposal failed the regression |
| Historical execution | Claude Code ran local commands, saved reports, and helped prepare the PR description |
| Voice guard | Rejected local drafts that asserted results before evidence; later draft passes do not establish that the original issue comment was protected or posted verbatim |
| Ship gate | Rejected stale commit references and an unreadable body-file path; passed after evidence/path corrections |
| Retrospective scout | Scanned 100 results and graded five, then graded two course-site candidates; a vague accepted issue led to an actual scope-rule correction |
| Retrospective orientation | Read the affected analyzer/provider/test subsystem and distilled local memory; it occurred after the implementation |
| PR-monitor | Read the merged PR and drafted a follow-up; incomplete issue/lock context made the draft unnecessary, so I declined it |

The scout and orientation runs are dated October 17, and the monitor run October 21. Their later timing is part of the story, not evidence that they shaped the October 10 selection or implementation. No second contribution is claimed from the comparison-candidate exercise.

### Evidence and interpretation boundaries

The public [issue](https://github.com/CommunityToolkit/Maui/issues/879), [claim comment](https://github.com/CommunityToolkit/Maui/issues/879#issuecomment-6098129467), [commit](https://github.com/alexh30486-ui/Maui/commit/915838870f6bb95cfc3993dbc895a8016ba34b9f), and [PR](https://github.com/CommunityToolkit/Maui/pull/3343) support the contribution account. The story also includes the important local before/after excerpts and result summaries so it does not rely on a grader opening a private log folder.

Local `evidence-879/`, `drafts-879/`, `CLAUDE.local.md`, and installed tool files are working records. They are not promised as public links or separate Assignment 5 submissions. A saved draft, a passed guard check, a published comment, and an API record are different artifacts. The story explicitly corrects the comment-creation/guard chronology and preserves the fact that my remembered CLA reply has no comment I can cite in the inspected API record; the queued CLA integration is not represented as completed merely because the PR merged.

## Start here

| Work | Location |
| --- | --- |
| **Assignment 5: real contribution, Units 5–8** | **[Contribution story](beat-2-contribution/contribution-story.md)** |
| Classroom issue selection | [Unit 1 selection](beat-1-sandbox/unit-1/selection.md) |
| Classroom reproduction | [Unit 2 reproduction](beat-1-sandbox/unit-2/reproduction.md) |
| Classroom plan and implementation | [Unit 3 account](beat-1-sandbox/unit-3/plan-and-implement.md), [plan](beat-1-sandbox/unit-3/plan.md) |
| Classroom PR preparation | [Unit 4 account](beat-1-sandbox/unit-4/pull-request.md) |
| Unit 1 evaluation record | [eval-run.txt](beat-1-sandbox/unit-1/eval-run.txt) |
| Unit 2 evaluation record | [eval-run.txt](beat-1-sandbox/unit-2/eval-run.txt) |
| Unit 3 evaluation record | [eval-run.txt](beat-1-sandbox/unit-3/eval-run.txt) |
| Unit 4 evaluation record | [eval-run.txt](beat-1-sandbox/unit-4/eval-run.txt) |
| Saved rubric/skill files | [tools/](tools/) |

The earlier reported evaluation agreements were **20/20 for Unit 1** and **18/20 for Unit 2**. They measure agreement with course evaluation labels; they are not course grades, test totals for the Maui contribution, or proof of live-tool approval. The existing sandbox explanations below preserve the differences between completed evaluations, stalled attempts, proposed revisions, and missing live-run evidence.

## Repository structure and scope

| Path | Purpose |
| --- | --- |
| `beat-1-sandbox/unit-1/` | Selection analysis and its evaluation record |
| `beat-1-sandbox/unit-2/` | Reproduction analysis and its evaluation record |
| `beat-1-sandbox/unit-3/` | Planning/implementation account, plan, and evaluation record |
| `beat-1-sandbox/unit-4/` | PR-preparation account and evaluation record |
| `beat-2-contribution/contribution-story.md` | The complete graded Assignment 5 narrative |
| `tools/` | Saved coursework skill folders; their separate portfolio assessment is outside this story |
| `skill/` and `eval/` | Earlier starter/rubric and evaluation materials retained in the course repository |

The transition between the two parts matters. Unit 1 selected classroom Path Review #73; Unit 2 investigated classroom #62. Assignment 5 concerns CommunityToolkit/Maui #879 and PR #3343. The issue numbers, repositories, local results, and evaluation scores should not be mixed across these projects.

## How I make the contribution account reviewable

The detailed story is organized around questions a reader can check: what behavior was missing, why the test was absent, how the failure was observed, what changed, which checks ran against which revision, what the maintainer said, and how the tools affected the work. More text is useful only when it answers one of those questions or exposes a limitation that could otherwise be missed.

The account follows five evidence practices:

1. **Name the artifact and revision.** The final commit is the source for the submitted diff; an earlier patch or report is identified as earlier evidence.
2. **Show the relevant behavior.** The generated-source difference explains this defect; a nonzero command by itself does not. Dependency restore failures remain separate.
3. **Separate tool roles.** ChatGPT suggestions, Claude execution, deterministic hook checks, the monitor's model-generated draft, automated review, and human approval have different evidentiary value.
4. **Keep chronology honest.** Original work, edited public comments, later evidence capture, and retrospective tool runs retain their actual dates and limits.
5. **Preserve uncertainty.** Missing scout timing, unverified CLA posting, limited test scope, and a declined draft remain visible rather than being rewritten into a perfect process.

These practices explain the choices and corrections in the story. They do not promise a particular assignment score or imply that every optional tool improvement was implemented.

The first-issue evidence guide supplied during the October 21 review adds a useful source map: maintainer signals come from human activity and thread responses; repository-use signals come from archive/release/push/adoption records; scope comes from the requested change and discussion; availability requires both linked PRs and comment history; contribution policy requires reading applicable rules, including linked documents and templates. The story now maps those families to what is actually established for this contribution and says where the original selection record is incomplete. A snapshot's recency must be measured from its capture date, while a live run uses its own date; neither a label nor a star count is a substitute for examining the work.


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

## Assignment 5 submission

Submit the entire course repository through the **Unit 5 Assignment tab**:

[https://github.com/alexh30486-ui/ai301-coursework](https://github.com/alexh30486-ui/ai301-coursework)

The supplied assignment instructions identify **November 8, 2026, at 11:59 PM PST** as the deadline. Graders read the contribution story at its required path, the issue thread, and the PR page; no separate tool files, evidence uploads, or monitor output are submitted for Assignment 5. The four weekly Toolkit entries and seven phase Toolkit blocks are contained in the story.

A merged PR is the project's outcome, while course submission is a separate action. A documentation commit, successful push, or README link does not prove that the course portal submission was completed.
