# Contribution: Fix MCT001 code-fix placement before `Build()` and add regression coverage

**Contribution Number:** 1

**Student:** Alex Hernandez

**GitHub Username:** alexh30486-ui

**Issue:** [CommunityToolkit/Maui #879](https://github.com/CommunityToolkit/Maui/issues/879)

**Pull Request:** [CommunityToolkit/Maui #3343](https://github.com/CommunityToolkit/Maui/pull/3343)

**Project:** .NET MAUI Community Toolkit; C#; Roslyn analyzer and code-fix tooling.

**Fork and branch:** [alexh30486-ui/Maui](https://github.com/alexh30486-ui/Maui), `test/879-initialization-codefix`.

**Final contribution commit:** [`915838870f6bb95cfc3993dbc895a8016ba34b9f`](https://github.com/alexh30486-ui/Maui/commit/915838870f6bb95cfc3993dbc895a8016ba34b9f).

**Baseline parent:** [`34bce1ada154760353011e90699b1621542eb36b`](https://github.com/CommunityToolkit/Maui/commit/34bce1ada154760353011e90699b1621542eb36b).

**Outcome:** merged October 10, 2026; merge commit [`f7f9f4488b168debb8db194895d40ddd7e345fd2`](https://github.com/CommunityToolkit/Maui/commit/f7f9f4488b168debb8db194895d40ddd7e345fd2).

**Latest documentation and public-record review:** October 21, 2026.

The original issue asked for tests for an initialization analyzer. The checkout already contained tests, so my investigation focused on what they actually verified. One new test applied the offered code fix and inspected the resulting source; it exposed that the fix placed `.UseMauiCommunityToolkit()` after `.Build()`. The submitted change corrected the selected syntax node and added that regression test: two files, 52 insertions, one deletion.

This account separates three kinds of evidence. Public source, the final commit, the issue thread, and PR records can be inspected through the links below. Historical local test results and tool verdicts are summarized from the terminal records and saved reports supplied during the work; those local files are not included in the public course repository. Personal recollections that the public record does not establish, particularly my CLA reply, remain qualified. The October 21 documentation review did not rerun the contribution tests or readiness tools.

## Toolkit

**Unit 5: Issue scout built and run on 2026-10-17, after the Maui contribution; one scope rule patched**

On October 17, after the October 10 contribution had merged, I wrote my scout's fit profile, one Python `good first issue` query, and two ranking filters, then ran one 100-result scan that graded five candidates: three accepted, two rejected because an open PR already said `Closes #5`. The scan accepted the vague owner-filed issue "Review security concepts", which exposed a scope loophole: the owner/starter-label exemption let an issue with no deliverable pass. I added fail branch (g) to the bounded-scope rule and graded two course-site candidates directly under the patched rubric; a claim-age cutoff remains proposed, not applied. No scout run graded Maui #879; the selection on October 10 was manual.

**Unit 6: Voice guard checked revised drafts; scoped repository memory was completed retrospectively on 2026-10-17**

The October 10 voice-guard records report stops on local drafts that asserted a result before showing evidence, followed by passes after commands and output were incorporated into revised drafts; bodyless `--help` requests also demonstrated that the hooks fired. The public issue comment was created at 06:45 PDT and edited at 08:38 PDT, so the later guard checks cannot be credited with protecting its original creation, and the current public prose does not establish that a guard-passed local draft was posted verbatim. On October 17, one read-only orientation agent examined the initialization analyzer, provider, verifier helpers, and test class, then distilled the findings into a 25-line, locally excluded `CLAUDE.local.md`. That orientation occurred after the contribution: it clarified the method-wide analyzer check and the code-fix coverage gap, but did not guide the original implementation.

**Unit 7: Ship gate checked the committed branch, rejected stale evidence, and caught a body-file path problem**

On October 10, the ship gate ran four manifest checks derived from repository guidance and CI, then the existing PR precheck on the real branch. A commit amend made the earlier `9a93b284` evidence reference stale; the gate blocked, and Claude recaptured before/after output tied to `91583887` before later passes. The real PR-opening hook then rejected a body-file argument containing a literal `~` path; using an absolute path resolved the lookup, and the PR opened at 08:44 PDT. These local readiness verdicts helped expose problems in the submission package, while the later maintainer review and merge provided separate upstream decisions.

**Unit 8: PR-monitor ran retrospectively on 2026-10-21; I declined its unnecessary follow-up draft**

On October 21, I adopted a playbook with a seven-day first-response threshold, a fourteen-day stalled-review threshold, one nudge maximum, and no nudge for merged or closed PRs, then Claude ran a free state canary at 15:39 PDT and one full monitor run at 15:51 PDT. The monitor read MERGED and APPROVED, selected its merged-follow-up form, and drafted a thank-you, a conditional issue-closing line, and a possible duplicate-`using` follow-up. Additional API inspection showed the issue already closed and the PR locked, while `license/cla` remained queued; those details exposed limits in the monitor's context rather than a reason to reopen completed work. I declined the draft because it added no necessary follow-up, posted nothing, and left the monitor and forms unchanged.

## Why I Chose This Issue

I chose [CommunityToolkit/Maui #879](https://github.com/CommunityToolkit/Maui/issues/879) because the maintainer had invited contributions, the test work looked bounded, and I wanted to try applying what I had learned in Python to a C# project. My earlier fit profile preferred a small Python bug or test/fixture correction with a clear reproduction and a narrow file surface; MAUI was a language and setup stretch, but the requested test work matched the kind of contribution I wanted to practice. I manually read the issue, contributing guidance, analyzer, provider, and existing tests. The issue's description was stale relative to the checkout: six tests already existed in the target class, but none applied the code fix. My [investigation and claim comment, posted as @alexh30486-ui](https://github.com/CommunityToolkit/Maui/issues/879#issuecomment-6098129467) was created October 10 at 13:45:12 UTC and edited at 15:38:55 UTC; TheCodeTraveler's [“Sounds good. Go for it” reply](https://github.com/CommunityToolkit/Maui/issues/879#issuecomment-6099055335) arrived at 15:23:39 UTC and supported proceeding with the narrowed scope. That response is evidence of support during the work, not evidence that I knew in advance how quickly a maintainer would reply.

The course Issue Selection site later showed #879 in my claimed issues alongside the two comparison candidates, confirming it was present on the course site; that listing does not establish when each claim was made. No scout run selected or graded #879 before I implemented it. My October 17 scout work was retrospective practice: [WrenAI #1202](https://github.com/Canner/WrenAI/issues/1202), an environment-variable and launcher toggle across several recommendation flows, received moderate fit, and [agentic-operator-core #132](https://github.com/Clawdlinux/agentic-operator-core/issues/132), a terminal-recording GIF task, received low fit. Their acceptance showed that passing required checks and matching my preferred work are different judgments. The broad search also admitted a vague owner-filed issue with a starter label, which led to the actual branch-(g) correction; the proposed claim-age cutoff was left unresolved because the scan had interpreted “current” without an explicit threshold. I am recording what the tool taught me after the contribution rather than claiming it made a selection decision it never made. The evidence map below was added using the guide supplied for the October 21 documentation review; it does not supply a missing original scout verdict.

| Criterion family | Concrete evidence in this contribution | Limit of the inference |
| --- | --- | --- |
| Maintainer activity and response | TheCodeTraveler's dated issue reply and human APPROVED review, linked above and below | They establish a response to this work; one same-day response is not a repository-wide latency sample |
| Repository use | The existing source/test projects and the public contribution build/sample/benchmark check records | The record does not establish how many downstream users run the merged change, and a release/adoption audit was not documented at selection time |
| Newcomer scope | One named analyzer/provider/test surface, the observed generated-source mismatch, and the final two-file diff | The issue's old age and label do not prove the work was small; actual source inspection narrowed it |
| Availability | The issue was described as unassigned in the supplied selection record, and the maintainer subsequently supported proceeding | No original scout availability audit is preserved; present-day issue state cannot prove what every competing claim looked like earlier |
| Contribution and AI policy | Pinned contributing guidance, PR-template/checklist handling, actual PR AI disclosure, and human review | Silence in a file inspected is not a blanket audit of all linked policies; an `AGENTS.md` file alone would not override an explicit restriction |

**Toolkit**

- Tool: manual issue/source inspection chose #879 on October 10; `issue-scout` was built and run on October 17, afterward. Fit profile (`scope.md`): "a small, testable first contribution in Python, especially a bug fix or test/fixture correction with a clear reproduction and a narrow file surface." Query (`search-strategy.md`): `gh search issues --language python --label "good first issue" --state open --limit 100`. Ranking: drop assignees, prefer `good first issue`/`help wanted`, order by fewest comments then most recent update; grade the top 5. Rubric checks: maintainer activity, repository in use, bounded newcomer scope, available to claim, contribution policy, maintainer responsiveness.
- What it produced: no verdict on #879, which was never fed to it. One scan on October 17: 100 results; all top-5 had zero comments and were updated within two hours. Accepted: agent-access-review #4 (three `catalog.yaml` entries plus one test, best fit; six-day-old repo, zero stars), Foxel #141 (mobile list-mode UI feature, low fit), cyber-security-basics #869 ("Review security concepts", daily auto-generated one-liner, owner never comments). Rejected: llm-redteam-evidence #5 and agent-access-review #5, each had an open PR whose description said `Closes #5.` Direct grading of the two course-site comparison candidates under the patched rubric: WrenAI #1202 accept (moderate fit; feature across launcher, UI, and ai-service; responsiveness fail at 2 of 4 sampled issues) and agentic-operator-core #132 accept (low fit; Go/Kubernetes docs GIF; CI `AI Attribution Guard` requires human-authored commits).
- Difficulties: ranking by fewest comments then newest surfaced minutes-old issues in zero-star repos and auto-generated daily issues; two of five paid grading slots went to issues already taken, which ranking fields cannot see. The scope rule passed #869 because the exemption for thin owner/starter-label writeups applied before the "names the behavior, files, or symptoms" clause was reached. "Available to claim" set no age threshold, so months-old claim-shaped comments on both direct candidates were read as not current without a stated cutoff. The Python-only query still returned a frontend feature, and the profile had no explicit rule ranking non-Python repos lower.
- What changed: same day, I added fail branch (g) to `rubric.md`: "the title, body, and thread together name no behavior, file, symptom, or concrete deliverable at all. Author identity and starter labels never override (g)"; the exemption now reads "provided (g) below does not hold" and the closing clause "When none of (a)-(g) holds, pass." Why: the exemption was meant to excuse a thin writeup of real work, not an issue requesting no change. Historical grades in `scan-output.md` were left as recorded, not regraded. Proposed and not applied: a 60-day staleness rule for claim comments with no PR or follow-up, a minimum star count or issue age in ranking, and a one-line fit ordering for non-Python repos. No rerun or regression eval of the patched rubric was performed. Limitation: all of this postdates the Maui selection and did not inform it.

## Understanding the Issue

**Problem Description**

The toolkit supplies two related pieces of developer tooling. An **analyzer** inspects source and reports diagnostic MCT001 when it recognizes a `UseMauiApp` invocation without a toolkit-initialization call in the enclosing method. A **code-fix provider** offers an edit in response to that diagnostic. Detecting a missing call and inserting the call correctly are separate behaviors, so tests of the first do not automatically cover the second.

The baseline analyzer test project passed 16 tests. The initialization class contained six: **one diagnostic-ID assertion and five analyzer-behavior tests**. The other ten were in the Camera and MediaElement analyzer classes. After my new test, the totals were 17 across the project and seven in the initialization class. Calling all six original tests “diagnostic behavior tests,” or all sixteen “tests for this analyzer,” would be inaccurate.

| Existing initialization-class test | What it checks |
| --- | --- |
| `UseCommunityToolkitInitializationAnalyzerId` | Diagnostic identifier equals `MCT001` |
| `VerifyNoErrorsWhenUseMauiCommunityToolkit` | An initialization call suppresses the diagnostic |
| `VerifyNoErrorsWhenUseMauiCommunityToolkitHasAdditionalWhitespace` | Extra whitespace does not create a false diagnostic |
| `VerifyErrorsWhenMissingUseMauiCommunityToolkit` | Missing initialization reports the expected diagnostic span |
| `VerifyNoErrorsWhenUseMauiCommunityToolkitWrapInPreprocessorDirectives` | The supported conditional-compilation case does not report a diagnostic |
| `VerifyErrorsWhenUseMauiCommunityToolkitIsCommentedOut` | An ordinary commented-out call does not count as initialization |

The class already imported a `CSharpCodeFixVerifier` specialized with the analyzer and provider. However, the existing helper called `VerifyAnalyzerAsync`; merely mentioning a code-fix type in the verifier's generic arguments did not apply the fix in those tests. The added `VerifyCodeFixInitializesToolkitBeforeBuild` explicitly called `VerifyCodeFixAsync`, supplied expected fixed source, and exercised the edit.

The distinction matters because the analyzer's current implementation checks the enclosing method for a matching call name. A wrongly placed `.UseMauiCommunityToolkit()` can therefore make MCT001 disappear without making the edited program correct. The new test examines the resulting source instead of relying only on disappearance of the original diagnostic. This contribution did not change or comprehensively validate the analyzer's method-wide, syntax-based detection.

**Expected Behavior**

A typical MAUI startup method constructs a builder, configures it, and then builds an application:

```csharp
return MauiApp.CreateBuilder()
    .UseMauiApp<Microsoft.Maui.Controls.Application>()
    .Build();
```

When MCT001 offers to add toolkit initialization, the result should configure the builder before producing the application:

```csharp
return MauiApp.CreateBuilder()
    .UseMauiApp<Microsoft.Maui.Controls.Application>()
    .UseMauiCommunityToolkit()
    .Build();
```

The fix also adds `using CommunityToolkit.Maui;` to the compilation unit. The test expects that import and checks the normalized complete fixed source, not just the presence of the method name.

| Point in the chain | Role relevant to this bug |
| --- | --- |
| `MauiApp.CreateBuilder()` | Produces the builder to configure |
| `.UseMauiApp<Application>()` | Configures that builder; this invocation is the diagnostic's selected span |
| `.UseMauiCommunityToolkit()` | Extension method declared with a `MauiAppBuilder` receiver |
| `.Build()` | Produces the `MauiApp`; builder configuration belongs before it |

**Current Behavior**

Before my change, applying the provider to the same input generated:

```csharp
return MauiApp.CreateBuilder()
    .UseMauiApp<Microsoft.Maui.Controls.Application>()
    .Build()
    .UseMauiCommunityToolkit();
```

The regression verifier reported that this generated source differed from the expected fixed source. That mismatch is the directly observed failure. The [extension declaration at the contribution commit](https://github.com/CommunityToolkit/Maui/blob/915838870f6bb95cfc3993dbc895a8016ba34b9f/src/CommunityToolkit.Maui/AppBuilderExtensions.shared.cs) takes `this MauiAppBuilder builder`, whereas `Build()` returns `MauiApp`; the receiver mismatch supports the PR description's compilation conclusion. I did not separately compile or run the generated snippet in a standalone application, and I did not verify the lightbulb action interactively in an IDE. I keep those limits explicit rather than presenting source reasoning as a separate compilation experiment.

“Current Behavior” here describes the pre-fix behavior being addressed. The PR is now merged; it is not a claim that the project's latest code still contains this particular placement defect.

**Affected Components**

| Component at the final contribution commit | Responsibility | Changed? |
| --- | --- | --- |
| [`UseCommunityToolkitInitializationAnalyzer.cs`](https://github.com/CommunityToolkit/Maui/blob/915838870f6bb95cfc3993dbc895a8016ba34b9f/src/CommunityToolkit.Maui.Analyzers/UseCommunityToolkitInitializationAnalyzer.cs) | Recognizes the invocation, checks the enclosing method, and reports the diagnostic location | No |
| [`UseCommunityToolkitInitializationAnalyzerCodeFixProvider.cs`](https://github.com/CommunityToolkit/Maui/blob/915838870f6bb95cfc3993dbc895a8016ba34b9f/src/CommunityToolkit.Maui.Analyzers.CodeFixes/UseCommunityToolkitInitializationAnalyzerCodeFixProvider.cs) | Chooses the invocation and constructs the edited document | One line replaced |
| [`UseCommunityToolkitInitializationAnalyzerTests.cs`](https://github.com/CommunityToolkit/Maui/blob/915838870f6bb95cfc3993dbc895a8016ba34b9f/src/CommunityToolkit.Maui.Analyzers.UnitTests/UseCommunityToolkitInitializationAnalyzerTests.cs) | Existing ID/behavior tests plus the new code-fix regression | 51 lines added |
| Test project's `Verifiers/` helpers | Build the Roslyn test with input, diagnostics, references, and expected fixed code | No |
| `AppBuilderExtensions.shared.cs` | Declares the toolkit initialization extension and its receiver | No |

**Toolkit**

- Tool: ChatGPT-assisted source reading, followed by the actual regression test and later source verification against the final commit.
- What it produced: an explanation of the nested invocation chain and the distinction between detection and editing, plus two proposed target-selection changes.
- Difficulties: the first proposed `.First()` change did not satisfy the test; early wording also blurred ID tests, analyzer tests, and code-fix tests.
- What changed: the implementation uses the diagnostic's complete span, and this account now distinguishes the one ID assertion, five behavior tests, and one added edit test precisely.

## Reproduction Process

**Environment Setup**

| Item | Recorded value or evidence boundary |
| --- | --- |
| Operating system | macOS; the supplied environment record reports version 26.6 |
| .NET SDK | 10.0.401 |
| SDK executable used | `/usr/local/share/dotnet/x64/dotnet` |
| Test target / host | `net10.0` / x64 test host |
| Hardware architecture | Not established by the SDK path; no ARM64 claim |
| Test framework | xUnit v3; the project references `xunit.v3` 4.0.0 |
| Roslyn testing packages | Analyzer/code-fix testing packages 1.1.4 in the project |
| Baseline / corrected commit | `34bce1ad` / `91583887` |
| Required local setup encountered | .NET SDK and referenced-project workloads; `maui` and `android` installation resolved the observed workload error |

I initially could not invoke `dotnet` because it was absent from PATH. I found the installed executable at the path above and checked the SDK version. The first test-project build then stopped with `NETSDK1147`, requesting Android workloads. Installing the MAUI/Android workloads resolved that barrier and allowed the baseline suite to run with 16 passing tests. The terminal transcript records those steps, but I did not preserve a separate installation log. The workload requirement arose while building this project's references; it does not establish that every standalone analyzer or every project in every MAUI repository needs Android workloads.

The [contributing guide pinned to the contribution commit](https://github.com/CommunityToolkit/Maui/blob/915838870f6bb95cfc3993dbc895a8016ba34b9f/CONTRIBUTING.md) lists the .NET SDK and MAUI workloads as prerequisites. The test project references toolkit, Camera, and MediaElement projects, which explains why the test surface involves more than the provider's own source file.

**Steps to Reproduce**

1. Work from the pinned repository revision, not an unspecified latest `main`. The original baseline was `34bce1ad`, and the final test is inspectable in `91583887`.
2. Confirm that the original suite passes: the recorded baseline result was 16 tests passed. A passing baseline does not show that the offered code fix works, because no baseline test applied it.
3. Add the new test while leaving the provider at its baseline implementation. Its input marks the `CreateBuilder().UseMauiApp<...>()` invocation as diagnostic location 0 and leaves `.Build()` outside the marker.
4. Run the regression. The saved filtered command was:

   ```bash
   /usr/local/share/dotnet/x64/dotnet test \
     --project src/CommunityToolkit.Maui.Analyzers.UnitTests/CommunityToolkit.Maui.Analyzers.UnitTests.csproj \
     -- --filter "FullyQualifiedName~VerifyCodeFixInitializesToolkitBeforeBuild"
   ```

5. Inspect the generated-source difference, not just the nonzero exit code. The recorded failure was:

   ```text
   failed ...UseCommunityToolkitInitializationAnalyzerTests.VerifyCodeFixInitializesToolkitBeforeBuild
   Context: Iterative code fix application
   content of '/0/Test0.cs' did not match. Diff shown with expected as baseline:
   - return MauiApp.CreateBuilder().UseMauiApp<Microsoft.Maui.Controls.Application>().UseMauiCommunityToolkit().Build();
   + return MauiApp.CreateBuilder().UseMauiApp<Microsoft.Maui.Controls.Application>().Build().UseMauiCommunityToolkit();

   Test run summary: Failed!
     total: 1
     failed: 1
   Exit code: 2
   ```

6. Restore the corrected provider from `91583887` and rerun the same filtered test. The saved after result was exit 0, one succeeded, zero failed. Run the full project as a separate regression check; the recorded corrected-suite result was 17 passed.

The original complete before-run transcript was saved after the first investigation plan had already said it was missing. The later recapture fills that evidence gap; it does not mean the transcript existed when the plan was first written.

For a reader reconstructing the comparison now, the following is a **newly documented recipe**, not a claim of a newly executed run. Run it from a clone containing the contribution commit after setting up the documented SDK/workloads; it creates a separate worktree with the new test and restores only the old provider into that worktree:

```bash
contribution_sha=915838870f6bb95cfc3993dbc895a8016ba34b9f
provider_path=src/CommunityToolkit.Maui.Analyzers.CodeFixes/UseCommunityToolkitInitializationAnalyzerCodeFixProvider.cs
test_project=src/CommunityToolkit.Maui.Analyzers.UnitTests/CommunityToolkit.Maui.Analyzers.UnitTests.csproj
comparison_root="$(mktemp -d)"

git worktree add --detach "$comparison_root/before" "$contribution_sha"
git show "${contribution_sha}^:${provider_path}" \
  > "$comparison_root/before/$provider_path"

# Before: new regression test with the original provider.
/usr/local/share/dotnet/x64/dotnet test \
  --project "$comparison_root/before/$test_project" \
  -- --filter "FullyQualifiedName~VerifyCodeFixInitializesToolkitBeforeBuild"

# After: restore the submitted provider in the same comparison worktree.
git -C "$comparison_root/before" restore --source="$contribution_sha" -- "$provider_path"
/usr/local/share/dotnet/x64/dotnet test \
  --project "$comparison_root/before/$test_project" \
  -- --filter "FullyQualifiedName~VerifyCodeFixInitializesToolkitBeforeBuild"

git worktree remove --force "$comparison_root/before"
rmdir "$comparison_root"
```

A later reproduction attempt on October 17 stopped before the tests ran: package restore raised `NU1902` and `NU1903` for `System.Security.Cryptography.Pkcs` 9.0.6, treated as errors. That attempt is a dependency/setup failure, not a second observation of the code-fix defect. It neither replaces the October 10 before/after results nor proves that the regression disappeared. I did not change dependencies or suppress those warnings as part of this contribution. A reader encountering that failure should record it separately rather than label any nonzero test command a successful reproduction.

**Reproduction Evidence**

- **Commit showing reproduction:** [the final commit in my fork](https://github.com/alexh30486-ui/Maui/commit/915838870f6bb95cfc3993dbc895a8016ba34b9f), which contains the regression test and correction together. The failing comparison used that test with the baseline provider restored temporarily; the fixed commit alone is not a committed failing state.
- **Screenshots/logs:** no screenshot is needed to understand the source difference because the before excerpt appears above and in the public PR. Historical local files are `before-run-debug-filtered-91583887.txt`, `after-run-debug-filtered-91583887.txt`, and `full-suite-debug-91583887.txt` under `evidence-879/20261010-082958-regression/`. They remain local provenance references, not clickable files promised to a grader.
- **My findings:** the new test applied the actual provider through the existing Roslyn verifier and found the wrong placement. The after run changed the observable result from a fixed-source mismatch to a pass. This establishes the exercised edit behavior, not every possible fluent chain or an interactive IDE integration.

**Toolkit**

- Tool: Claude Code ran the recorded before/after commands and saved transcripts; ChatGPT helped draft the test and interpretation.
- What it produced: the failure difference, passing filtered result, full Debug result, and commit-qualified evidence filenames summarized above.
- Difficulties: an early evidence pair named the superseded commit; the first plan also predated preservation of the complete before log. The later October 17 attempt was blocked during dependency restore. No live `repro-check` run on the claim comment or a repro report is recorded; the October 10 voice-guard passes on the local comment draft and the test commands Claude ran are not a repro-check verdict.
- What changed: evidence was recaptured against the final revision, and this account distinguishes the original diagnostic experiment from a later environment failure.

## Solution Approach

**Analysis**

`RegisterCodeFixesAsync` receives the diagnostic and its `Location.SourceSpan`. The original provider used only the span's start to locate a token, walked outward through its ancestors, filtered for invocation expressions, and chose the last one:

```csharp
root?.FindToken(diagnosticSpan.Start).Parent?.AncestorsAndSelf()
    .OfType<InvocationExpressionSyntax>().Last()
```

In the reproduced expression, the first token is part of `MauiApp.CreateBuilder()`, nested inside `UseMauiApp<...>()`, nested inside `Build()`. The analyzer reports the `UseMauiApp` invocation's span, but the old selection walks beyond that boundary and chooses `Build()`. `AddUseCommunityToolkit` then wraps the chosen invocation with a new `.UseMauiCommunityToolkit()` call, so choosing `Build()` puts initialization after it. The defect is the target selection; the append operation follows the target it was given.

ChatGPT first suggested `.First()` instead of `.Last()`. That proposal still failed the regression. An endpoint of the ancestor sequence is not the same guarantee as selecting the node whose full span the analyzer reported; the failed proposal was discarded rather than accepted because it looked like a small change. The observations here do not imply ancestor traversal is always wrong in Roslyn code; they explain why this provider's selection rule did not match its diagnostic contract.

**Proposed Solution**

Use the full diagnostic span to request the corresponding syntax node, prefer the innermost node if spans tie, and retain the expected invocation type and existing failure behavior:

```diff
- var declaration = root?.FindToken(diagnosticSpan.Start).Parent?.AncestorsAndSelf().OfType<InvocationExpressionSyntax>().Last() ?? throw new InvalidOperationException();
+ var declaration = root?.FindNode(diagnosticSpan, getInnermostNodeForTie: true) as InvocationExpressionSyntax ?? throw new InvalidOperationException();
```

This leaves the code-action registration and document-edit routine unchanged. The selected `UseMauiApp` invocation is replaced by a toolkit-initialized invocation; its enclosing `.Build()` remains outside that replacement. The resulting builder call therefore appears before the terminal application-building call in the exercised expression.

The change deliberately does not redesign analyzer detection, alter other providers, deduplicate imports, change public APIs, or reformat the solution. The later orientation noticed possible duplicate-import behavior and a diagnostic-category inconsistency, but neither was implemented or tested in this PR. They are observations outside this contribution, not additional resolved bugs.

**Implementation Plan**

The implementation target was `UseCommunityToolkitInitializationAnalyzerCodeFixProvider.cs`: in `RegisterCodeFixesAsync`, replace ancestor-based invocation selection with `root.FindNode(diagnosticSpan, getInnermostNodeForTie: true)`. Leave `AddUseCommunityToolkit` unchanged. Add the regression as `VerifyCodeFixInitializesToolkitBeforeBuild` in `UseCommunityToolkitInitializationAnalyzerTests.cs`.

1. Inspect the current tests instead of implementing the issue's old description literally.
2. Add one code-fix regression to the existing initialization test class, with a diagnostic marker and explicit expected fixed source.
3. Obtain a failure with the old provider, then correct its target selection.
4. Compare the same regression before and after, and run the complete analyzer project in Debug and Release.
5. Run the chosen repository-derived format/build checks, review outgoing text with the guard, and pass the branch through the gate before opening the PR.

The test has several purposeful details. Its marker `{|#0:...|}` identifies the complete diagnosed invocation without including `.Build()`. `Diagnostic().WithLocation(0).WithSeverity(DiagnosticSeverity.Error)` checks the diagnostic expected at that marker. `VerifyCodeFixAsync` receives both source versions and references to `typeof(Options)` and `typeof(Core.Options)`, following the project's verifier conventions. The expected source includes the added namespace import. Parsing it and calling `NormalizeWhitespace()` aligns the expected formatting with the provider's existing normalization, so the comparison does not fail merely because the multiline literal and generated document use different whitespace.

The plan changed in three material ways: the requested “untested analyzer” became a code-fix coverage gap; the test demonstrated a behavior defect requiring one provider edit as well as tests; and the `.First()` proposal was replaced after it failed. I described the narrowed work on the issue, received the maintainer's “Go for it,” and kept the final diff to the provider and regression class. The local `drafts-879/plan.md` is a historical planning record, not an additional submitted artifact.

**Toolkit**

- Tool: ChatGPT for proposed explanations and changes; the Unit 3 plan-check rubric as a planning structure; Claude Code for execution and record keeping.
- What it produced: the failing regression, rejected `.First()` candidate, successful span-based candidate, and bounded implementation plan.
- Difficulties: an AI suggestion sounded plausible while failing the actual test; the original issue wording also did not match the current checkout.
- What changed: the test result governed the implementation decision. No separate successful live `plan-check` invocation is established by these records, so using its structure is not reported as a passed tool run.

## Testing Strategy

The central question was observable: **when the real provider handles MCT001 on a chain ending in `Build()`, does the resulting source place initialization on the builder?** Two observable checks answered it:

1. **Code-fix output:** the regression test failed with the baseline provider because it generated `.Build().UseMauiCommunityToolkit()`, then passed with the corrected provider because the generated source matched `.UseMauiCommunityToolkit().Build()`.
2. **Existing-suite regression:** the full analyzer test project passed all 17 tests in Debug and Release, showing that the new code-fix test and existing diagnostic tests passed together.

The before and after runs used the same expected source. Formatting and build checks were additional repository checks, not substitutes for these two behavior checks.

| Check | Recorded outcome | What it supports | What it does not establish |
| --- | --- | --- | --- |
| Baseline analyzer project | 16 passed | Original suite was green before the added regression | Original code-fix output was correct |
| New filtered test, baseline provider | Exit 2; one failed; expected/actual order differs | The added test detects the exercised placement defect | Independent compilation or IDE behavior |
| Same filtered test, corrected provider | Exit 0; one passed | Submitted selection fixes this regression | Every possible invocation shape |
| Full project, Debug | 17 passed | Existing tests plus new regression pass together | Complete repository or platform coverage |
| Full project, Release | 17 passed, zero failed, zero skipped in the saved reports | Release configuration was also exercised | That every cited early log used the final commit |
| Provider formatting verification | Exit 0 | Chosen provider formatting check passed | Full-solution formatting |
| Test formatting verification | Exit 0 with workspace-load warning | Chosen test-file formatting check completed successfully | Absence of workspace warnings |
| Release CodeFixes project build | Zero warnings, zero errors | Changed provider project builds in Release | Interactive lightbulb registration |
| `git diff --check` | Passed in the supplied record | No reported whitespace errors in that diff | Functional correctness |

The full-project Debug command was:

```bash
/usr/local/share/dotnet/x64/dotnet test \
  --project src/CommunityToolkit.Maui.Analyzers.UnitTests/CommunityToolkit.Maui.Analyzers.UnitTests.csproj
```

Release uses the same project with `-c Release`. The summarized Release result was:

```text
Test run summary: Passed!
  total: 17
  failed: 0
  succeeded: 17
  skipped: 0
```

The early Release report in `evidence-879/20261010-082206/check-4.txt` predates the final commit. It supports that earlier run, not final-commit provenance by itself. The supplied gate reports state that the four checks were rerun after the amend and passed at approximately 08:38 and 08:40 PDT; the final-commit filtered and full-Debug files explicitly name `91583887`. I retain those distinctions rather than relabeling the early log as a run against a commit that did not yet exist.

The manifest's check types came from the pinned contributing guide and [CI workflow](https://github.com/CommunityToolkit/Maui/blob/915838870f6bb95cfc3993dbc895a8016ba34b9f/.github/workflows/dotnet-build.yml). I chose a narrower local scope: provider formatting, test-file formatting, Release provider build, and the analyzer test project. The manifest's excluded table listed full-solution formatting, the other component builds and suites, and benchmarks, each with a reason dated 2026-10-10. That was a contributor judgment, not a claim that CI required exactly these four local commands or that the local test command reproduced CI's reporting and coverage flags. The analyzer tests run as a step within the library-build workflow; they are not a separate dedicated CI job as an earlier description implied.

The source-documented formatting command is:

```bash
dotnet format samples/CommunityToolkit.Maui.Sample.slnx \
  --exclude-diagnostics CS0612 CS0618 CS0672 CS1062 CS1064
```

For local changed-file checks, the recorded form adds `--verify-no-changes` and `--include` to the appropriate project invocation. The original story used placeholders for those full formatting commands; the precise historical arguments belong to the local manifest/transcripts, so I do not reconstruct new command strings and call them verbatim old evidence. Excluding the compiler diagnostics follows the guide's stated concern about formatter-applied obsolete attributes. The test-file check emitted a workspace-load warning but exited zero; two Camera-project warnings, CS9113 and CS0649, also appeared in the supplied before/after build records and were outside the changed files.

Limitations and deliberate exclusions:

- I did not test the fix inside Visual Studio or VS Code.
- I did not separately compile a generated sample application.
- I did not run all component suites, benchmarks, or the full platform matrix locally.
- I verified the selected changed files instead of performing the full-solution formatting check locally. `--verify-no-changes` can avoid rewriting files, so rewriting is not an inherent reason that the broader check was impossible; the actual limitation is the narrower check scope I chose.
- I added one chained-`Build()` regression. Expression-bodied startup methods, multiple builders, import deduplication, all batch-fix cases, and every other fluent-chain form are not newly covered by this test.
- The later vulnerability-related restore failure did not reach any test and is not counted as a code-fix verification result.

**Toolkit**

- Tool: repository-derived ship manifest, Claude Code as the command runner, and gate/precheck reports as records of package readiness.
- What it produced: four historical check logs and result summaries, the before/after regression excerpts, and final-commit Debug evidence. The observable outcomes are included here rather than requiring access to local files.
- Difficulties: workspace warnings could be mistaken for failure, and an early passing report could be mistaken for evidence about the final amended commit.
- What changed: exit codes, configuration, source revision, and the boundary of each check are now stated together. Proposed commands, historical commands, public CI results, and newly failed setup attempts are not pooled into one undifferentiated “all checks passed” claim.

## Implementation Notes

These entries preserve the dates of the work. This expanded October 21 edition adds explanations and public-record corrections from the retained records; it is not presented as an untouched contemporaneous transcript.

**2026-10-10 — Setup, baseline, and first regression**

Located the SDK after the PATH failure, resolved the Android-workload error, and obtained the baseline 16-pass result. Inspected the six initialization-class tests and found no call applying the provider. Added the chained-`Build()` regression, observed the fixed-source mismatch, tried ChatGPT's unsuccessful `.First()` suggestion, and moved to span-based selection. The corrected filtered test and full suite passed in the recorded runs.

**2026-10-10 — Public issue discussion, with timestamp correction**

The public investigation comment was created at **13:45:12 UTC / 06:45:12 PDT**, the maintainer replied at **15:23:39 UTC / 08:23:39 PDT**, and my existing comment was edited at **15:38:55 UTC / 08:38:55 PDT**. Later local guard checks cannot be placed before the comment's creation. The current public issue comment summarizes the 16-to-17 result and the placement correction but does not contain the command/output blocks or AI-disclosure line from some local drafts. The PR contains the before/after excerpt and AI disclosure. A local draft pass is therefore not proof that the same draft was published unchanged.

**2026-10-10 — Evidence, amend, gate, and PR opening**

The local record reports an environment capture around 08:11 PDT, an 08:20 hook setup block on a bodyless `gh pr create --help` (no manifest check ran), the four early checks around 08:22–08:23, an initial gate pass at 08:33 on `9a93b284`, the 08:36 stale-evidence block (the precheck's `regression-evidence` check read unclear, so its verdict was reject), recaptured regression output, and later gate passes around 08:38 and 08:40 on `91583887`. The manifest hash was unchanged across every run; no rubric was patched to clear the block. The recorded refusals were setup- or evidence-related; no earlier-unit-debt refusal appears in the gate transcript. The PR was opened only after the corrected evidence passed; the later hook setup failure was resolved with an absolute body-file path, not bypassed. Public commit metadata records the final commit's author timestamp as **15:29:13 UTC / 08:29:13 PDT** and committer timestamp as **15:33:35 UTC / 08:33:35 PDT**; this distinguishes the author date from the later amended commit rather than assigning one exact amend time from a minute-level recap. The public PR creation timestamp is **15:44:40 UTC / 08:44:40 PDT**.

The authoritative [commit diff](https://github.com/CommunityToolkit/Maui/commit/915838870f6bb95cfc3993dbc895a8016ba34b9f) replaces one provider line and adds 51 test lines: **52 insertions and one deletion across two files**. An earlier local patch contained one additional blank line. It is a historical working patch, not the final diff. The contribution commit also records Claude co-authorship; the public PR description discloses ChatGPT and Claude Code assistance.

**2026-10-10 — Review and merge**

The automated review recommended approval at 16:14:41 UTC and reported zero open findings. TheCodeTraveler submitted an APPROVED review at 16:36:51 UTC while asking for a CLA agreement reply. The PR merged at 16:42:48 UTC, and the issue closed as completed at 16:42:50 UTC. I do not infer CLA-check completion from those events.

**2026-10-17 — Retrospective scout, rubric correction, and orientation**

Installed the scout after the contribution was already complete. The first manually tested query was unnecessarily restricted to the old classroom Path Review repository; ChatGPT corrected that direction to the real-project Python/`good first issue` query before the paid scan. The scan graded five candidates, exposed the absent-deliverable loophole, and led to actual branch-(g) changes and dated notes. The course site showed the Maui issue plus two comparison claims, and both comparison candidates were graded under the patched rubric. A separate scoped orientation clarified the analyzer/provider/verifier connections and replaced the earlier handwritten memory with distilled agent findings. Neither tool run is retroactively credited with choosing or implementing #879.

**2026-10-17 — Additional reproduction attempt blocked during restore**

A temporary-worktree attempt to rerun the old-provider comparison stopped on `NU1902` and `NU1903` package advisories treated as errors. It produced no test verdict. That result is retained as an environment limitation, and the original successful before/after experiment remains the evidence for the code-fix change.

**2026-10-21 — Monitor, declined draft, and documentation review**

The official Unit 8 starter was absent locally, then downloaded and installed. Empty playbook sections blocked a full monitor run until the adopted rules were written. The state canary and full run read the already merged PR, and I declined the draft after its limited context became clear. This documentation review then checked the official story template, pinned source, commit metadata, issue-comment timestamps, and PR records. It corrected the original test taxonomy, the initial-post/guard chronology, the early Release-log provenance, and overbroad workload/coverage statements. No new code tests, scout scan, or gate run was performed for the writing expansion.

**Toolkit**

- Tool: Claude Code for historical command execution and local notes; Git/GitHub metadata for the public commit and event sequence; ChatGPT for the final source-backed editorial audit.
- What it produced: the final two-file change, dated local records, and the more precise chronology above.
- Difficulties: author and committer times were conflated, local draft history was conflated with public comment creation, and preserved old reports could be mistaken for final-revision evidence.
- What changed: the final commit and public timestamps now anchor the chronology, while uncertain local ordering remains approximate. Documentation corrections preserve the earlier limitations instead of rewriting history to make the process look seamless.

## Pull Request

**PR Link:** https://github.com/CommunityToolkit/Maui/pull/3343

**PR Description:** The submitted title was `Fix UseCommunityToolkitInitializationAnalyzer code fix inserting UseMauiCommunityToolkit() after Build()`. The description explains the ordering problem, the diagnostic-span selection, the generated-source comparison, full-project test results, exclusions, and AI assistance. It uses `Fixes #879`; GitHub records the PR merged and issue closed as completed.

The checklist marked tests, rebasing on main, and coding-standard checks complete. It left approval/champion status, samples, and separate documentation unchecked with explanations: the issue had `enhancement`/`help wanted` labels and a supporting maintainer comment rather than the checklist's named approval label; the implementation had no sample-app change or public API change. The maintainer's later approval and merge are the public outcome, not a reason to rewrite the checklist as if every box had been checked at submission.

One correction to the public PR wording belongs in this story: its description says the analyzer already had “16 behavior tests.” The accurate count is **16 project tests**, including **one ID assertion and five analyzer-behavior tests in the target class**, plus ten tests in the other analyzer classes. The new code-fix test brought the project to 17 and the target class to seven. The posted PR also states that the generated output does not compile; here I explain that conclusion through the receiver types while limiting the directly executed observation to the harness mismatch. I have not silently edited the public history or represented those wording corrections as new upstream changes.

**Maintainer Feedback:**

| Event | Feedback and recorded response |
| --- | --- |
| January 7, 2023 | TheCodeTraveler invited a PR with unit tests in the original issue thread, before my involvement |
| October 10, 08:23:39 PDT | [TheCodeTraveler supported proceeding](https://github.com/CommunityToolkit/Maui/issues/879#issuecomment-6099055335) after my investigation comment; the final implementation stayed limited to the provider and test |
| October 10, 09:14:41 PDT | [Copilot review](https://github.com/CommunityToolkit/Maui/pull/3343#pullrequestreview-5479813155): approval recommended, zero open findings; this is automated feedback, distinct from human approval |
| October 10, 09:36:51 PDT | [TheCodeTraveler's APPROVED review](https://github.com/CommunityToolkit/Maui/pull/3343#pullrequestreview-5479894783) also requested `@dotnet-policy-service agree` |
| CLA reply recollection | I recall submitting the agreement reply on October 10, but the API records inspected on October 21 contain no PR conversation comment I can cite; I cannot verify that the reply posted successfully or that the CLA check completed |
| October 21 monitor decision | I declined the drafted close-the-loop message because the PR was merged and locked and the issue was already closed; nothing was posted |

The supplied records do not establish a requested code-revision round after review. I do not invent one to make the contribution story longer. The unresolved CLA record is kept visible: a human review request, an author's recollection, the API's comment list, and a queued check are different facts, and merge does not convert them into proof of acceptance or waiver.

**Status:** Merged; issue completed. Status is dated evidence of what happened, not an assignment-grade claim.

| Time | Recorded state | Evidence boundary |
| --- | --- | --- |
| October 10, 08:44:40 PDT | PR opened; checks initially pending | Public creation timestamp plus supplied opening-time terminal transcript; no separate opening log path was identified |
| October 10, 09:42:48 PDT | PR merged as `f7f9f4488b168debb8db194895d40ddd7e345fd2` | Public PR metadata |
| October 10, 09:42:50 PDT | Issue #879 closed as completed | Public issue metadata |
| October 10, 15:11 PDT | Historical fetch reported merged/approved, successful build/sample/benchmark checks, and CLA queued | Historical snapshot, retained as a record of that fetch |
| October 12, 02:20 PDT | PR's later recorded activity was a lock event | Reported by the monitor follow-up inspection; a lock is not a new requested code change |
| October 21, 15:51 PDT | Full monitor read MERGED/APPROVED and produced a draft; supplementary inspection found issue closed and PR locked | Actual retrospective monitor run; draft declined |
| October 21 documentation audit | Public API still showed merged/locked, two reviews, no issue-style PR comments, and `license/cla` queued | Read-only source/status review; not a second monitor run |

Check records on the contribution commit distinguish completed checks from the pending CLA integration:

| Check group | Recorded result |
| --- | --- |
| Library build: Windows and macOS | Success |
| Sample app build: Windows and xcode-27 | Success |
| Benchmarks | Success |
| WIP | Success |
| `license/cla` | Queued; no completion conclusion |
| Dependabot, signing, release jobs | Skipped in the checked records |

A pending check and UNKNOWN mergeability on an already merged PR do not undo the public merged state. The monitor installation guidance explicitly warns against treating those leftover fields as the current workflow decision for a merged PR. Likewise, success of a CI job is not a claim that I locally executed that job's entire matrix or inspected its coverage artifacts.

**Toolkit**

- Tool: the ship gate on PR creation, historical `gh` reads, and the Unit 8 monitor with my adopted playbook.
- What it produced: the successful opening after a path correction, public review and merge records, dated snapshots, and one merged-follow-up draft that I declined.
- Difficulties: local draft wording did not always match public prose; the monitor lacked issue-closure, lock, and CLA context; a queued integration could be mistaken for an open PR blocker after merge.
- What changed: the story now separates the public issue/PR record from local draft passes, records the declined draft, and preserves CLA uncertainty without claiming the agreement was accepted or waived. No follow-up was posted solely to manufacture activity for the assignment.

## Learnings and Reflections

**Technical Skills Gained**

- **Reading the actual test boundary.** An ID assertion checks the diagnostic's name; an analyzer test checks reporting; a code-fix test checks the source edit. Sharing a generic verifier type does not mean each test exercises every capability of that type. Inspecting which verifier method is called identified the missing coverage.
- **Following a diagnostic through the editor pipeline.** The diagnostic supplies a location, the provider chooses a node, and the edit routine transforms that node. Here the edit routine behaved consistently with a wrongly selected target. The useful investigation followed that connection instead of changing every stage.
- **Understanding fluent-call placement.** A call chain can look like a short expression while containing nested invocation nodes. The selected node's receiver and result type matter: configuration that belongs to `MauiAppBuilder` must be placed before `Build()` produces the application.
- **Making the expected edit explicit.** The new test marks the diagnostic location, supplies reference assemblies, and compares normalized fixed source including the import. It makes a concrete edit expectation visible to future contributors.
- **Separating source conclusions from executed observations.** The source supports the receiver-mismatch explanation. The saved failing test directly shows a fixed-source difference. Those are related forms of evidence, but I should not claim a separate compilation experiment that I did not perform.
- **Understanding build dependencies.** This analyzer test project references platform-adjacent toolkit projects, which led to workload setup even though the edited file was a Roslyn provider. That observed dependency should not be generalized to every analyzer project.
- **Using public state carefully.** A merged PR, a queued CLA integration, a locked thread, and a recent bot event can coexist. A monitor's first summary is a starting point for deciding whether a draft makes sense, not automatic authorization to send it.

**Challenges Overcome**

| Challenge | Action and practical result |
| --- | --- |
| SDK unavailable through PATH | Located the installed executable and used its full path |
| `NETSDK1147` workload error | Installed the required MAUI/Android workloads; the historical baseline then ran |
| Plausible AI proposal still failed | Retained the regression expectation and rejected `.First()` when it did not satisfy it |
| Evidence tied to a superseded commit | Recaptured the comparison and named the final revision explicitly |
| Draft asserted results before evidence | Revised local drafts under the voice guide; kept the public posting history distinct from draft approval |
| Hook could not resolve a literal body-file path | Used an absolute path; the PR opened through the gate |
| Old issue wording obscured existing tests | Read the actual test methods and narrowed the contribution with maintainer support |
| Retrospective scout accepted a vague request | Patched the required scope rule and preserved the original grades as historical results |
| Monitor draft lacked important thread context | Checked the supplementary record, declined the draft, and documented the limitation |

Not every difficulty was resolved. The later dependency-audit failure stopped a fresh reproduction before test execution, the original selection still has no contemporaneous scout run, and the CLA reply remains unverifiable in the inspected public comments. Honest documentation makes those boundaries inspectable; it does not turn missing evidence into completed work.

**What I'd Do Differently Next Time**

I would inspect the existing tests before relying on an issue's old description and save baseline and before-and-after output as I go.

The concrete process implications in this record are to preserve a baseline before editing, keep the first failing output, tie later validation to the final revision, check the public posted text against the local draft, and run selection/orientation tools during their intended phases. Those are prospective improvements suggested by the documented gaps, not claims that every one was already part of my original workflow. The correction to the scout also demonstrates a useful constraint: a title, author role, or label is not enough to establish a real deliverable when the request itself remains undefined.

## Resources Used

- [Issue #879](https://github.com/CommunityToolkit/Maui/issues/879): original testing request and maintainer invitation.
- [My investigation/claim comment](https://github.com/CommunityToolkit/Maui/issues/879#issuecomment-6098129467) and [maintainer reply](https://github.com/CommunityToolkit/Maui/issues/879#issuecomment-6099055335): public discussion and support for proceeding.
- [Final contribution commit](https://github.com/alexh30486-ui/Maui/commit/915838870f6bb95cfc3993dbc895a8016ba34b9f): authoritative provider change, regression test, file counts, and AI co-authorship record.
- [Pinned analyzer source](https://github.com/CommunityToolkit/Maui/blob/915838870f6bb95cfc3993dbc895a8016ba34b9f/src/CommunityToolkit.Maui.Analyzers/UseCommunityToolkitInitializationAnalyzer.cs), [provider](https://github.com/CommunityToolkit/Maui/blob/915838870f6bb95cfc3993dbc895a8016ba34b9f/src/CommunityToolkit.Maui.Analyzers.CodeFixes/UseCommunityToolkitInitializationAnalyzerCodeFixProvider.cs), and [test class](https://github.com/CommunityToolkit/Maui/blob/915838870f6bb95cfc3993dbc895a8016ba34b9f/src/CommunityToolkit.Maui.Analyzers.UnitTests/UseCommunityToolkitInitializationAnalyzerTests.cs): detection, selected-node edit, test taxonomy, and regression implementation.
- [Pinned extension declaration](https://github.com/CommunityToolkit/Maui/blob/915838870f6bb95cfc3993dbc895a8016ba34b9f/src/CommunityToolkit.Maui/AppBuilderExtensions.shared.cs): the builder receiver used in the source-based explanation.
- [Pinned CONTRIBUTING.md](https://github.com/CommunityToolkit/Maui/blob/915838870f6bb95cfc3993dbc895a8016ba34b9f/CONTRIBUTING.md) and [build workflow](https://github.com/CommunityToolkit/Maui/blob/915838870f6bb95cfc3993dbc895a8016ba34b9f/.github/workflows/dotnet-build.yml): prerequisites, formatter exclusions, and repository build/test conventions. No AI prohibition was identified in the contributing guide inspected; that is not a statement that every repository policy file was exhaustively checked.
- [PR #3343](https://github.com/CommunityToolkit/Maui/pull/3343), [automated review](https://github.com/CommunityToolkit/Maui/pull/3343#pullrequestreview-5479813155), and [human approval](https://github.com/CommunityToolkit/Maui/pull/3343#pullrequestreview-5479894783): public validation, requested agreement reply, final description, and merge outcome.
- ChatGPT: investigation assistance, the unsuccessful `.First()` proposal, the successful span-selection proposal, test/comment drafting, and the October 21 source-backed documentation expansion. Claude Code: historical local commands, saved reports, scoped orientation, draft revisions, gate invocation, and monitor installation/execution. These tools had distinct roles; their output was not a substitute for the maintainer's decision.
- Unit 5 issue scout: local `~/.claude/skills/issue-scout/scan-output.md` and `scan-notes.md`; the scan, patched rule, and two comparison verdicts are summarized in this story. Candidate issue links: [WrenAI #1202](https://github.com/Canner/WrenAI/issues/1202) and [agentic-operator-core #132](https://github.com/Clawdlinux/agentic-operator-core/issues/132).
- Unit 6 voice guard and scoped memory: local `~/.claude/voice-guard/guard-log.md`, `evidence-879/20261017-orientation.md`, and the excluded `~/maui-issue-879/CLAUDE.local.md`. Guard draft outcomes and orientation timing are stated above.
- Unit 7 gate: local `ship-manifest.md`, `test_evidence.md`, check logs, and `~/.claude/ship-gate/gate-log.md`; the outcomes, warning boundaries, amend problem, and exclusions are reproduced in the relevant sections.
- Unit 8 [official starter](https://github.com/codepath/ai301-unit8-starter): runner, installation guidance, move forms, and playbook template. The adopted playbook and `run-report.md`, `drafted-move.md`, and `playbook-snapshot.md` remain local under `evidence-879/20261021-monitor/`; the actual outcome and decision are recorded here.
- [Official contribution-story template](https://github.com/codepath/ai301-coursework-template/blob/main/beat-2-contribution/contribution-story.md): exact section names, four weekly entries, and seven phase Toolkit blocks used to check the structure of this expanded account.
- The first-issue evidence guide supplied for this October 21 review: a map from rubric families to GitHub and snapshot evidence. It helped expose the limits of badge, label, policy, last-push, and old-claim inferences in the expanded documentation; this is not a claim that a Copilot edit or guide-based audit was recorded before the original contribution.

For selection evidence, snapshot recency belongs to the capture date and live recency to the run date. Historical October 17 scout verdicts were not reevaluated using October 21 activity. Stars, labels, author badges, and repository instructions are signals to investigate, not guarantees of adoption, responsiveness, manageable scope, availability, or permission.

The local paths above identify retained working records. They are not public download links, separate Assignment 5 submissions, or evidence that a grader can open files absent from the repository. The important results, limits, and public resolving links are included directly in this story. Repository preparation and a successful push also do not establish that the course portal's submission button was clicked; that remains a separate submission action.
