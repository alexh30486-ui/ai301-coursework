# Contribution: Fix the MCT001 code fix so it inserts `UseMauiCommunityToolkit()` before `Build()`, with a regression test (CommunityToolkit/Maui #879)

**Contribution Number:** 1
**Student:** Alex Hernandez
**GitHub Username:** alexh30486-ui
**Issue:** https://github.com/CommunityToolkit/Maui/issues/879
**Pull Request:** https://github.com/CommunityToolkit/Maui/pull/3343

Fork: https://github.com/alexh30486-ui/Maui, branch `test/879-initialization-codefix`, final commit `915838870f6bb95cfc3993dbc895a8016ba34b9f` on top of `main` at `34bce1ad`.

## Toolkit

**Unit 5: Issue scout installed and run retrospectively on 2026-10-17; no scout run existed when #879 was selected**
2026-10-17, one week after the Maui contribution was selected and merged on 2026-10-10; this run did not guide that selection, and the selection gap stands. I installed the scout under `~/.claude/skills/issue-scout`, restored my Python fit profile into `scope.md`, and tested the one `gh search issues` query in `search-strategy.md`: 100 results, five graded, three accepted, two rejected for open PRs saying "Closes #5". The accepted one-line issue "Review security concepts" (almadhlom/cyber-security-basics#869) exposed a bounded-scope loophole, so I added fail branch (g) to `rubric.md` requiring a named behavior, file, symptom, or concrete deliverable that author identity and starter labels cannot override. Direct grading of Canner/WrenAI#1202 and Clawdlinux/agentic-operator-core#132 under the patched rubric accepted both at moderate and low personal fit, and left unresolved that the scout read months-old claim comments as inactive without a defined cutoff (60-day rule proposed in `scan-notes.md`, not applied; records in `scan-output.md`).

**Unit 6: Voice guard stopped two comment drafts for claims without evidence, then passed the revised drafts**
2026-10-10, 08:20 to 08:33 PDT. The guard (`~/.claude/voice-guard/check_voice.py`, log at `~/.claude/voice-guard/guard-log.md`) stopped my first issue-comment draft at 08:20 and a second at 08:30 with the same rule: "No conclusion without its artifact in the same comment." Both drafts said the defect was confirmed before showing a command or output. I moved the filtered test command, the before output (exit 2), and the after output (exit 0) above the claim. The comment draft passed at 08:31; the PR draft passed at 08:30 and again at 08:33. Two stops on `gh issue comment --help` and `gh pr create --help` at 08:20 were deliberate hook-wiring tests: the guard refuses bodyless forms by design.

2026-10-17, orientation. The same day I ran one read-only orientation agent scoped to the MCT001 analyzer, its code-fix provider, the `Verifiers/` helpers, and the initialization test class, a week after the PR merged; no orientation run existed before or during the contribution, and the earlier `CLAUDE.local.md` was hand-written inspection notes, not a tool run. The agent confirmed the mechanism the fix relied on: the analyzer reports the `UseMauiApp<T>()` invocation span and scans the whole method for the toolkit call, so the old `AncestorsAndSelf().Last()` selection appended after `Build()` yet still silenced the diagnostic. The existing analyzer-only tests did not inspect the edited source; the new code-fix regression test checks that output. The regression is tested in exactly one place, `VerifyCodeFixInitializesToolkitBeforeBuild`, through the `CSharpCodeFixVerifier` overload that passes the toolkit `Options` types. Findings saved to `evidence-879/20261017-orientation.md`; `~/maui-issue-879/CLAUDE.local.md` rewritten from them on the staff template (25 lines, still excluded via `.git/info/exclude`). Claude Code ran the agent and wrote both files.

**Unit 7: Ship gate blocked stale before/after evidence after a commit amend, passed after recapture, then blocked a literal `~` path on the real `gh pr create`**
2026-10-10, 08:33 to 08:44 PDT. The gate (`~/.claude/ship-gate/check_gate.py`, log at `~/.claude/ship-gate/gate-log.md`) ran four manifest checks sourced from CONTRIBUTING.md and `.github/workflows/dotnet-build.yml`, then my own pr-precheck in live mode. First manual pass at 08:33 was against commit `9a93b284`. I then amended to `91583887` to drop one blank line. The 08:36 run blocked: `regression-evidence [unclear]: Before/after evidence cites commit 9a93b284 and '53 insertions', but the branch commit is 91583887 with 52 insertions`. I recaptured the before and after runs against `91583887`, updated `test_evidence.md`, and the gate passed at 08:38 and 08:40 with all four manifest checks ok and all seven pr-precheck checks pass. At 08:44 the hook blocked `gh pr create` with `could not read the body file: [Errno 2] No such file or directory: '/Users/alexhernandezm/maui-issue-879/~/ai301-unit1-starter/...'` because the hook reads the literal argument before shell expansion. The absolute path passed, the hook honored the 08:40 manual pass, and the PR opened. The title file began with the literal text `PR Title: `, which I stripped before passing `--title`.

**Unit 8: PR-monitor run once, retrospectively, on 2026-10-21; it read MERGED and drafted a close-the-loop note I declined**
2026-10-10, 15:11 PDT. One `gh pr view` snapshot of PR #3343 (state, reviews, checks) and one `gh api` read of the issue comments. That was an ordinary status fetch, not a monitor run; no monitor existed on my machine until 2026-10-21.

2026-10-21, 15:39 and 15:51 PDT. I installed the unit-8 pr-monitor from the starter (`~/.claude/pr-monitor/monitor.py`, INSTALL.md three-command copy, no hook), filled `playbook.md` with my own rules (7-day first-response and 14-day stalled-review thresholds, one nudge maximum, never nudge merged or closed, no automatic close), ran the free `--state` canary at 15:39, then one full run at 15:51 from `~/maui-issue-879` on `test/879-initialization-codefix`. The monitor read: state MERGED, review decision APPROVED, opened 11 days ago, last activity 2026-10-12 (a lock event by github-actions[bot]), thread 2 reviews, checks "1 pending, 6 passing, 4 skipped" and mergeability UNKNOWN, which INSTALL.md says are leftovers on a merged PR. It chose the merged follow-up form and wrote `drafted-move.md`: a thank-you to TheCodeTraveler, a conditional line about closing #879, and one possible follow-up (the provider may add a duplicate `using CommunityToolkit.Maui;`, seen in code, not tested). It applied my "never nudge merged" and "merged needs no walk-away" rules and asked no question. Copies: `evidence-879/20261021-monitor/run-report.md`, `drafted-move.md`, `playbook-snapshot.md`; log block in `~/.claude/pr-monitor/monitor-log.md`. Limitations: the monitor could not see that #879 is already closed (closed 2026-10-10 16:42 UTC, completed), could not see CLA state, and did not notice the PR is locked, which makes any comment impossible. What I changed: nothing in the monitor or forms; the playbook is mine. Decision, 2026-10-21: I declined the draft. The PR is merged and locked and the issue is closed, so the note adds no necessary follow-up. Nothing was posted. Claude Code ran the install, the two runs, and the evidence copies; the drafting call was the monitor's own Sonnet call.

## Why I Chose This Issue

Issue #879 asks for unit tests for `UseCommunityToolkitInitializationAnalyzer`. It is labeled `enhancement` and `help wanted`. In January 2023 the maintainer (TheCodeTraveler) had replied on the issue inviting a PR with tests. The issue was still open and unclaimed when I looked.

Reasons that the evidence supports:

- **Bounded surface.** One analyzer, one code-fix provider, one xUnit test class. The repository's CI runs that test project as its own job, so I could mirror one job locally.
- **Active maintainer.** TheCodeTraveler replied to my investigation comment the same day and later reviewed the PR.
- **Clear contribution rules.** CONTRIBUTING.md documents the formatting command and the diagnostics to exclude. It states no AI-use ban and no disclosure requirement. I disclosed AI assistance anyway.
- **A real gap under the stale request.** The issue said the analyzer was untested, but the current checkout already had analyzer tests. What was missing was any test of the code fix's output. That narrower gap turned out to hide a defect, which made the issue more valuable than it first looked. I describe that in the next section.

My investigation and claim comment: https://github.com/CommunityToolkit/Maui/issues/879#issuecomment-6098129467 (2026-10-10 13:45 UTC). The maintainer replied at 15:23 UTC: "Thanks @alexh30486-ui! Sounds good. Go for it."

I chose it because the maintainer invited contributions, the test work looked bounded, and I wanted to try applying what I'd learned in Python to a C# project.

**Toolkit**
- Tool: none recorded for selection. No scout or issue-select run existed for #879 when it was chosen on 2026-10-10. A retrospective issue-scout scan and direct grading were completed on 2026-10-17 (see Unit 5 above); they did not grade #879 and did not inform this selection.
- What it produced: nothing for this selection. The selection reasons above come from manual reading of the issue thread, CONTRIBUTING.md, and the test project. The 2026-10-17 run produced `scan-output.md` and `scan-notes.md` for other candidates only.
- Difficulties: the issue text was stale relative to the code, which a tool run against the issue alone would not have caught either.
- What changed: the rubric gained scope branch (g) on 2026-10-17 as a result of the retrospective run. The earlier evidence gap is recorded rather than filled.

## Understanding the Issue

**Problem Description**

The toolkit ships a Roslyn analyzer and a code fix for diagnostic MCT001. The analyzer detects a `MauiAppBuilder` chain that never calls `UseMauiCommunityToolkit()`. The code fix edits the source to add that call. Those are two different things, and they were tested differently.

On `main` at `34bce1ad` the analyzer test project had 16 passing tests: six in `UseCommunityToolkitInitializationAnalyzerTests`, five in the Camera analyzer class, and five in the MediaElement analyzer class. All six tests in this issue's class checked whether the diagnostic fired or stayed silent. None of them applied the code fix and compared the edited source to an expected result. So the question "does the fix produce correct code?" had no answer in the suite.

My new test, `VerifyCodeFixInitializesToolkitBeforeBuild`, checked the code fix itself. It found that the fix put `.UseMauiCommunityToolkit()` after `.Build()`. The test caught this as a mismatch between the generated code and the expected code.

Counts: 16 baseline tests across the project, six in the target class. After my new test, 17 across the project and seven in that class.

The published PR description says the generated code "does not compile." That is a source-based conclusion, not a compiled one. `src/CommunityToolkit.Maui/AppBuilderExtensions.shared.cs` line 26 declares `UseMauiCommunityToolkit(this MauiAppBuilder builder, ...)`, and no overload takes a `MauiApp` receiver. `Build()` returns `MauiApp`, so `.Build().UseMauiCommunityToolkit()` has no matching extension method. I did not separately compile that generated snippet.

**Expected Behavior**

For the common fluent chain

```csharp
MauiApp.CreateBuilder()
    .UseMauiApp<Microsoft.Maui.Controls.Application>()
    .Build()
```

the fix should insert the toolkit call on the builder, before `Build()`:

```csharp
MauiApp.CreateBuilder().UseMauiApp<Microsoft.Maui.Controls.Application>().UseMauiCommunityToolkit().Build();
```

`Build()` turns the `MauiAppBuilder` into a `MauiApp`. `UseMauiCommunityToolkit()` is an extension on the builder, so it has to come first.

**Current Behavior**

Before the fix, the provider generated

```csharp
MauiApp.CreateBuilder().UseMauiApp<Microsoft.Maui.Controls.Application>().Build().UseMauiCommunityToolkit();
```

The regression verifier reported a generated-source mismatch against the expected text. I did not separately compile or run that output, and I did not reproduce it in an IDE; the evidence is the test harness diff shown under Reproduction Process.

**Affected Components**

- `src/CommunityToolkit.Maui.Analyzers/UseCommunityToolkitInitializationAnalyzer.cs`: emits MCT001. Not changed.
- `src/CommunityToolkit.Maui.Analyzers.CodeFixes/UseCommunityToolkitInitializationAnalyzerCodeFixProvider.cs`: selects the invocation to edit. Changed, one line.
- `src/CommunityToolkit.Maui.Analyzers.UnitTests/UseCommunityToolkitInitializationAnalyzerTests.cs`: six analyzer tests, now plus one code-fix test.

**Toolkit**
- Tool: ChatGPT, for reading the provider and explaining what `AncestorsAndSelf().OfType<InvocationExpressionSyntax>().Last()` selects.
- What it produced: the explanation that `.Last()` returns the outermost invocation, and a first proposed correction (swap to `.First()`).
- Difficulties: that first proposal did not fix the test (see Solution Approach).
- What changed: I stopped reasoning about position in the ancestor list and looked at what the diagnostic itself reports.

## Reproduction Process

**Environment Setup**

macOS, .NET SDK 10.0.401, test target net10.0, x64 test host. The saved environment record (`evidence-879/environment.txt`, 2026-10-10 08:11 PDT) shows `ProductVersion: 26.6` and the baseline commit `34bce1ad`. I do not claim a CPU architecture; the x64 SDK path says nothing about the physical chip.

Setup barriers and corrections, from my terminal session (no separate install log was saved):

1. `dotnet` was not on PATH. I located the SDK at `/usr/local/share/dotnet/x64/dotnet` and used that full path in every command.
2. `dotnet --version` reported 10.0.401.
3. The first build failed with NETSDK1147 because the Android workloads required by the solution were missing.
4. Installing the `maui` and `android` workloads resolved that error.
5. The existing analyzer test project then built and ran: 16 passed.

CONTRIBUTING.md lists the .NET SDK and the MAUI workloads as prerequisites, so steps 3 and 4 match the documented setup. I just had not done it yet.

**Steps to Reproduce**

1. Baseline: clone `CommunityToolkit/Maui`, check out `main` at `34bce1ad`, and run the analyzer test project. Result: 16 passed.
2. Add `VerifyCodeFixInitializesToolkitBeforeBuild` to `UseCommunityToolkitInitializationAnalyzerTests.cs`. It marks the `CreateBuilder().UseMauiApp<...>()` span as the diagnostic location and expects `.UseMauiCommunityToolkit().Build()` in the fixed source.
3. Run the filtered test with the original provider (exact saved invocation):

   ```
   /usr/local/share/dotnet/x64/dotnet test --project src/CommunityToolkit.Maui.Analyzers.UnitTests/CommunityToolkit.Maui.Analyzers.UnitTests.csproj -- --filter "FullyQualifiedName~VerifyCodeFixInitializesToolkitBeforeBuild"
   ```

   Observed failure, exit code 2:

   ```
   failed CommunityToolkit.Maui.Analyzers.UnitTests.UseCommunityToolkitInitializationAnalyzerTests.VerifyCodeFixInitializesToolkitBeforeBuild
     Xunit.MicrosoftTestingPlatform.XunitException: System.InvalidOperationException : Context: Iterative code fix application
     content of '/0/Test0.cs' did not match. Diff shown with expected as baseline:
     -            return MauiApp.CreateBuilder().UseMauiApp<Microsoft.Maui.Controls.Application>().UseMauiCommunityToolkit().Build();
     +            return MauiApp.CreateBuilder().UseMauiApp<Microsoft.Maui.Controls.Application>().Build().UseMauiCommunityToolkit();
   Test run summary: Failed!
     total: 1
     failed: 1
   ```

4. After comparison: with the corrected provider, the same command exits 0 with `total: 1, failed: 0, succeeded: 1`.

**Reproduction Evidence**
- **Commit showing reproduction:** the test in commit `91583887`, run against the provider file checked out from `main` (`git checkout main -- <provider file>`), then restored with `git checkout HEAD -- <provider file>`. Working tree was clean afterwards.
- **Screenshots/logs:** `beat-2-contribution/evidence-879/20261010-082958-regression/before-run-debug-filtered-91583887.txt` (the failure above) and `after-run-debug-filtered-91583887.txt` (the pass). The earlier pair captured against `9a93b284` is kept beside them with identical results. The full before-run log was captured after my investigation plan was first written, so the plan's note that it was "not yet saved separately" is out of date.
- **My findings:** the new test reproduced the defect on the first run. The failure is a pure source-text mismatch from the Roslyn test harness, driven by the real analyzer and real code fix with no mocks.

**Toolkit**
- Tool: Claude Code, running the before and after commands and saving the transcripts.
- What it produced: the two filtered-run logs and a full-suite Debug log, each named with the commit they were run against.
- Difficulties: the first capture was against `9a93b284`; after the amend the ship gate rejected it as not tied to the committed tree.
- What changed: I recaptured against `91583887` and put the commit sha in the file names so provenance is visible.

## Solution Approach

**Analysis**

The provider found its target like this:

```csharp
root?.FindToken(diagnosticSpan.Start).Parent?.AncestorsAndSelf()
    .OfType<InvocationExpressionSyntax>().Last()
```

`AncestorsAndSelf()` walks outward from the diagnosed token toward the root, so `.Last()` is the outermost invocation. In `CreateBuilder().UseMauiApp<App>().Build()` that is `Build()`. The analyzer had reported MCT001 on the inner `CreateBuilder().UseMauiApp<App>()` span, but the provider ignored the span and guessed from the chain shape.

**Proposed Solution**

Select the node at the diagnostic's own span:

```csharp
root?.FindNode(diagnosticSpan, getInnermostNodeForTie: true) as InvocationExpressionSyntax
```

The fixer then edits exactly the invocation the analyzer reported. Scope stays at that one line plus one test. Analyzer detection, the Camera and MediaElement providers, samples, docs, and solution-wide formatting are out of scope.

**Implementation Plan**

1. Add `VerifyCodeFixInitializesToolkitBeforeBuild` for the `.Build()` chain.
2. Replace the ancestor-list selection with span-based selection in the provider.
3. Observable checks: filtered test before and after; full analyzer project in Debug and Release.
4. Readiness checks: changed-file `dotnet format --verify-no-changes`, Release build of the CodeFixes project, voice guard on outgoing text, ship gate on the full PR package.

Scope change: the issue asked for analyzer tests; the checkout already had them. I posted the narrowing on the issue and the maintainer replied "Go for it." The plan is saved at `beat-2-contribution/drafts-879/plan.md`.

Unsuccessful attempt: ChatGPT's first suggestion was to replace `.Last()` with `.First()`. I tried it. The filtered test still failed. The problem was never which end of the ancestor list to take; the ancestor list is the wrong source of truth. Span-based selection fixed it.

**Toolkit**
- Tool: ChatGPT for the analysis and the two candidate corrections; plan-check rubric from unit 3 as the structure for `plan.md`.
- What it produced: the `.First()` suggestion (failed) and the `FindNode` suggestion (worked).
- Difficulties: the first suggestion was confidently wrong, and I only caught it because the test was already in place.
- What changed: I now require a failing test before accepting any proposed one-line fix.

## Testing Strategy

Before and after, same test, exit codes recorded:

| Run | Provider | Result | Log |
| --- | --- | --- | --- |
| Filtered regression, Debug | from `main` | exit 2, 1 failed | `evidence-879/20261010-082958-regression/before-run-debug-filtered-91583887.txt` |
| Filtered regression, Debug | commit `91583887` | exit 0, 1 passed | `.../after-run-debug-filtered-91583887.txt` |
| Full analyzer project, Debug | commit `91583887` | 17 passed, 0 failed | `.../full-suite-debug-91583887.txt` |
| Full analyzer project, Release | commit `91583887` | 17 passed, 0 failed, 0 skipped | `evidence-879/20261010-082206/check-4.txt`, rerun by the gate at 08:38 and 08:40 |

Full project command:

```
/usr/local/share/dotnet/x64/dotnet test --project \
  src/CommunityToolkit.Maui.Analyzers.UnitTests/CommunityToolkit.Maui.Analyzers.UnitTests.csproj
```

Release output:

```
Test run summary: Passed!
  total: 17
  failed: 0
  succeeded: 17
  skipped: 0
```

The 17 is the 16 pre-existing tests plus the new one. The target class went from six tests to seven.

Repository checks, from the ship manifest (`~/maui-issue-879/ship-manifest.md`). Commands were sourced from CONTRIBUTING.md (formatting) and `.github/workflows/dotnet-build.yml` (build and test); I added none of my own.

| Check | Command | Result |
| --- | --- | --- |
| Provider formatting | `dotnet format <CodeFixes csproj> --verify-no-changes --include <provider file> --exclude-diagnostics CS0612 CS0618 CS0672 CS1062 CS1064` | exit 0, no output |
| Test-file formatting | same, `--include <test file>` | exit 0, printed "Warnings were encountered while loading the workspace." |
| Release CodeFixes build | `dotnet build src/CommunityToolkit.Maui.Analyzers.CodeFixes/CommunityToolkit.Maui.Analyzers.CodeFixes.csproj -c Release` | 0 warnings, 0 errors |
| Analyzer tests | Debug and Release, above | 17 passed |
| `git diff --check` | on the branch | passed (recorded in `investigation-plan-879.md`) |

Warnings that appeared and are not failures: the workspace-load warning during test-file formatting, and two pre-existing warnings from `src/CommunityToolkit.Maui.Camera/CameraManager.shared.cs` (CS9113, CS0649) during every test build, before and after the change. Neither file is touched by this PR.

Exclusions, all disclosed in the PR:

- No interactive IDE verification of the code fix.
- No complete local platform matrix.
- No other component suites or benchmarks locally.
- Full-solution `dotnet format` excluded because the documented command rewrites tracked files across the solution; changed-file verification gated this change instead.

**Toolkit**
- Tool: ship manifest (unit 7) listing must-pass and excluded checks with dated reasons; Claude Code ran the checks and wrote `test_evidence.md` from the output.
- What it produced: `evidence-879/20261010-082206/check-1..4.txt` and `results.txt`, each with exit code and source.
- Difficulties: the test-file format check printed a workspace warning that looked like a failure until I read the exit code.
- What changed: `results.txt` records the exit code next to each command so warnings and failures cannot be confused.

## Implementation Notes

**2026-10-10, morning (investigation and implementation)**
Set up the SDK and workloads (NETSDK1147 on first build, fixed by installing `maui` and `android` workloads). Baseline: 16 passed. Wrote `VerifyCodeFixInitializesToolkitBeforeBuild`; it failed with `.Build().UseMauiCommunityToolkit()`. Tried ChatGPT's `.First()` swap; still failed. Switched to `FindNode(diagnosticSpan, getInnermostNodeForTie: true)`; filtered test passed, full project 17 passed. Posted the investigation comment on #879 at 13:45 UTC (voice guard passed at 08:31 PDT after two evidence-ordering stops). Maintainer replied "Go for it" at 15:23 UTC.

**2026-10-10, 08:11 to 08:44 PDT (checking, correction, shipping)**
08:11 saved `environment.txt`. 08:22 to 08:23 ran the four manifest checks, all exit 0. 08:29 amended `9a93b284` to `91583887` (one blank line removed from the test file; provider byte-identical). 08:30 to 08:33 voice guard passed on the PR draft. 08:33 gate PASS on the old sha; 08:36 gate BLOCK for stale evidence; recaptured before/after against `91583887`; 08:38 and 08:40 gate PASS with 4/4 manifest checks ok and 7/7 pr-precheck checks pass. 08:44 hook blocked the literal `~` body-file path; retried with the absolute path; PR #3343 opened.

Implementation diff (authoritative source: `git show 91583887` in `~/maui-issue-879`; the saved `evidence-879/change.patch` predates the amend by one blank line):

```diff
-		var declaration = root?.FindToken(diagnosticSpan.Start).Parent?.AncestorsAndSelf().OfType<InvocationExpressionSyntax>().Last() ?? throw new InvalidOperationException();
+		var declaration = root?.FindNode(diagnosticSpan, getInnermostNodeForTie: true) as InvocationExpressionSyntax ?? throw new InvalidOperationException();
```

plus 51 added lines in the test file for the new test. Two files, 52 insertions, 1 deletion, one commit.

**Toolkit**
- Tool: Claude Code as the command runner and transcript writer; git for the amend.
- What it produced: the dated evidence folders and the amended commit.
- Difficulties: amending after evidence capture invalidated the evidence's provenance. The gate caught it; I had not.
- What changed: capture evidence last, after the final commit, and name files by sha.

## Pull Request

**PR Link:** https://github.com/CommunityToolkit/Maui/pull/3343

**PR Description:** Title: `Fix UseCommunityToolkitInitializationAnalyzer code fix inserting UseMauiCommunityToolkit() after Build()`. The body follows the repository template: description of change with the before and after output, `Fixes #879`, checklist, and additional information. Checklist as submitted: tests checked, rebased-on-main checked, coding-standard checked. Left unchecked with a written reason: the `approved`/`Championed` box (the issue is labeled `enhancement` and `help wanted`; the maintainer's "Go for it" is a comment, not a label, so I left that judgment to the core team), samples (no sample-app surface), and documentation (no public API change). AI assistance disclosed in the body: ChatGPT for investigation and drafting, Claude Code for running the checks and drafting the description from their output. Full text at `beat-2-contribution/drafts-879/pr_draft.md`.

**Maintainer Feedback:**
- 2023-01-07, on the issue: TheCodeTraveler invited a PR with unit tests. This is the original invitation, before my involvement.
- 2026-10-10 15:23 UTC, on the issue: "Thanks @alexh30486-ui! Sounds good. Go for it." This approved the narrowed scope (code-fix coverage plus the ordering fix). No label was applied.
- 2026-10-10, on the PR: TheCodeTraveler review, state APPROVED: "Thanks @alexh30486-ui! Approved. Could you please respond with the comment `@dotnet-policy-service agree`? Once you do we will be able to merge this PR."
- 2026-10-10, on the PR: Copilot pull-request reviewer, state COMMENTED: "Approval recommended", 0 open findings.
- My response: I recall submitting the agreement reply on October 10, 2026, but the API records inspected on October 21 contain no comment I can cite. I cannot verify that the reply posted successfully or that the CLA check completed. The 15:11 PDT snapshot on 2026-10-10 and the 15:51 PDT record on 2026-10-21 both show zero PR comments from me and `license/cla` still QUEUED. The merge is not treated here as proof that the CLA check completed.

**Status, in order:**

1. 2026-10-10 08:44 PDT, at opening: the `gh pr create` output showed PR #3343 open with checks pending. That output appears in the terminal transcript I supplied; no separate saved log path is identified.
2. 2026-10-10 15:11 PDT, one `gh pr view` fetch, superseded by record 3 below. It reported the PR merged and showed the CI and review state current at that moment:

| Item | State at 15:11 PDT |
| --- | --- |
| PR state | MERGED by TheCodeTraveler at 16:42 UTC, merge commit `f7f9f4488b168debb8db194895d40ddd7e345fd2` |
| Review decision | APPROVED |
| Build Library (windows-latest, macos-26) | SUCCESS |
| Build Sample App (windows-latest, xcode-27) | SUCCESS |
| Run Benchmarks | SUCCESS |
| WIP | SUCCESS |
| `license/cla` | QUEUED, no conclusion recorded |
| dependabot, sign, release-main, release-nuget | SKIPPED |

3. 2026-10-21 15:51 PDT, pr-monitor full run plus one `gh api` read, saved under `evidence-879/20261021-monitor/`:

| Item | State at 15:51 PDT |
| --- | --- |
| PR state | MERGED, merge commit `f7f9f448`, mergedAt 2026-10-10 16:42:48 UTC |
| Issue #879 | closed 2026-10-10 16:42:50 UTC, state_reason completed |
| Review decision | APPROVED (TheCodeTraveler 16:36 UTC; Copilot reviewer COMMENTED 16:14 UTC) |
| PR conversation | locked by github-actions[bot] 2026-10-12 09:20 UTC; zero issue-style comments on the PR in the API |
| `license/cla` | still QUEUED, no conclusion recorded |
| Checks, mergeability | "1 pending, 6 passing, 4 skipped", UNKNOWN; leftovers on a merged PR per INSTALL.md |

The API shows no PR comment from me; see My response under Maintainer Feedback.

**Toolkit**
- Tool: ship gate hook on `gh pr create` (unit 7); one `gh pr view` fetch for the 2026-10-10 snapshot (not a monitor run); pr-monitor (unit 8) for the 2026-10-21 record, run retrospectively.
- What it produced: the hook block on the `~` path, then a pass honoring the 08:40 manual gate; the dated status table above.
- Difficulties: the `~` block, and the `PR Title: ` prefix in the title file.
- What changed: absolute paths in hook-inspected arguments; title file stripped before use.

## Learnings and Reflections

**Technical Skills Gained**
- Analyzer coverage and code-fix coverage are different questions. Six tests proved the diagnostic fired; none proved the edit was right. The first code-fix test found a defect.
- Selecting a syntax node by the diagnostic's span is more precise than picking an endpoint of the ancestor list. `.Last()` and `.First()` are both guesses about chain shape; `FindNode(diagnosticSpan, ...)` uses what the analyzer already reported.
- Roslyn's `Microsoft.CodeAnalysis.Testing` harness runs the real analyzer and fix end to end and diffs the generated source, which makes the before/after evidence trivial to read.
- .NET MAUI repositories need the MAUI and Android workloads installed before any project in the solution builds, even an analyzer project with no platform code.

**Challenges Overcome**
- `dotnet` missing from PATH and NETSDK1147 from missing workloads: resolved by using the full SDK path and installing the workloads.
- A confidently suggested `.First()` fix that did not work: caught by the already-failing test.
- Voice guard stops for claims placed before evidence: fixed by reordering the comment.
- Ship gate block for evidence tied to a superseded commit: fixed by recapturing after the amend.
- Hook block on a literal `~` path: fixed with an absolute path.

**What I'd Do Differently Next Time**
I would inspect the existing tests before relying on an issue's old description and save baseline and before-and-after output as I go.

## Resources Used

- Issue #879 thread and CONTRIBUTING.md in `CommunityToolkit/Maui`: scope, formatting command, excluded diagnostics, prerequisites.
- `.github/workflows/dotnet-build.yml`: source of the Release build and test commands in the ship manifest.
- `Microsoft.CodeAnalysis.Testing` (already referenced by the test project): drives the analyzer and code fix in the regression test.
- ChatGPT: code reading, the `.First()` suggestion that failed, the `FindNode` suggestion that worked, and draft text for the change, test, and issue comment.
- Claude Code: ran the formatting, build, and test commands; saved transcripts; drafted the PR description and this story from the saved records.
- Scoped orientation (unit 6 repo memory), retrospective run 2026-10-17: `evidence-879/20261017-orientation.md`, distilled into `~/maui-issue-879/CLAUDE.local.md`.
- Issue scout (unit 5), retrospective run 2026-10-17: `~/.claude/skills/issue-scout/scan-output.md` and `scan-notes.md`. ChatGPT helped draft the rubric and strategy wording; Claude Code ran the search, grading, and rubric edit.
- Voice guard (unit 6) and ship gate (unit 7): hooks on `gh issue comment` and `gh pr create`; logs at `~/.claude/voice-guard/guard-log.md` and `~/.claude/ship-gate/gate-log.md`.
- `gh` CLI: opened the PR and took the one status snapshot.
- pr-monitor (unit 8), installed and run 2026-10-21: `~/.claude/pr-monitor/` (runner, move forms, my `playbook.md`); run copies in `evidence-879/20261021-monitor/`.
