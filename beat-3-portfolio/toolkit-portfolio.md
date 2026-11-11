# Toolkit Portfolio

**Student:** Alex Hernandez

**Working draft prepared:** November 11, 2026

**Public-record snapshot used:** October 21, 2026; not refreshed for this draft


## Featured Tools



I chose these four because together they cover the work I did this term: finding a contribution, communicating about it, checking it before submission, and deciding whether to follow up. The issue scout helped me decide which issues deserved a closer look; a high search ranking alone did not make an issue a good fit. The voice guard checked drafts for claims that needed nearby evidence. The ship gate made me choose which checks mattered for my change. PR-monitor helped me decide whether a follow-up was appropriate after the PR was already open. The scout and orientation work on October 17 and the monitor run on October 21 happened after the Maui PR, so they did not guide that contribution.

### How to read the tool records

| Log label | Simple meaning |
| --- | --- |
| `manual` | I explicitly ran a check. |
| `hook` | An automatic check ran when a command was attempted. |
| `stop` | The check found a problem or could not complete a required check. |
| `pass` | The draft or command passed that particular check. |
| `target` | The file or command being checked. |

A pass applies only to the check and target named in that entry. It does not automatically mean the code works, a message was posted, or the whole contribution is ready.

### The Maui contribution and the toolkit

The Maui contribution was the software change I submitted. The toolkit helped me evaluate work, check communication, review evidence before opening a PR, and consider follow-ups afterward.

In CommunityToolkit/Maui, an analyzer reports a missing initialization call. A separate code-fix provider offers to insert that call. The defect I tested was in the offered edit: it placed `.UseMauiCommunityToolkit()` after `.Build()` instead of before it. I added a test comparing generated code with expected code, then changed how the provider selected the invocation to edit.

| Part of the work | What changed | What that change means |
| --- | --- | --- |
| Maui contribution | Code-fix provider and regression test | Changed project behavior and added a check for the defect. |
| Issue scout | Acceptance rubric, including branch (g) | Changed which issue descriptions the scout should accept. |
| Voice guard | Communication guide | Changed the written rules used to check drafts; the saved comparison does not establish who authored each line. |
| Ship gate | Initial repository-specific manifest | Configured which repository checks to run and recorded exclusions. |
| PR-monitor | Initial playbook configuration | Set waiting periods, nudge limits, and rules for considering follow-ups. |

Configuring a tool is not the same as rewriting its implementation. I filled in the ship manifest, but it stayed unchanged during the later gate retries; recovery involved correcting the evidence package. Declining the monitor's draft did not change the monitor's code. The scout and orientation work on October 17 and monitor run on October 21 were part of my term's toolkit work, but happened after October 10 and did not guide the Maui selection or fix.

**Issue scout**

**What it is, and the judgment hole I wrote:**

The staff runner searches using the fit profile and queries, ranks results, and grades the top five. My part was configuring the acceptance rubric that decides whether an issue is worth considering. The October 17 scan showed why that judgment matters: an issue can look suitable because of its author or label while asking for no concrete deliverable.

**How it evolved, dated:**

On October 17 I ran a retrospective scan. One of the five candidates that came back was cyber-security-basics #869, “Review security concepts.” It passed the old owner/starter-label exemption even though the issue asked for no actual change. That false pass showed the exemption was too soft, so I added branch (g): if the title, body, and thread name no behavior, file, symptom, or concrete deliverable, author identity and starter labels no longer override. I later used the patched rubric for direct grading of WrenAI #1202 and agentic-operator-core #132; this was not a repeat scan or a regression evaluation. The claim-staleness cutoff, minimum-age/star ranking, and non-Python ordering were only proposed; they never went in. This whole scan and patch happened after the Maui work.

**Evidence:**

The October 17 scan report lists 100 query results and five graded candidates. #869 (“Review security concepts”) only passed because it was owner-filed with a starter label, even though it asked for no concrete change.

> Quoted exact excerpt from the 2026-10-17 scan output: “3. https://github.com/almadhlom/cyber-security-basics/issues/869 — "Review security concepts". Passes the rubric only because it is owner-filed with a starter label. It is a daily auto-generated issue with no concrete change requested, in a notes repo whose owner never comments. Rubric tension logged in scan-notes.md; skip in practice.”

That last phrase is the scan report's historical wording. The recorded responsiveness evidence was zero owner comments across the five sampled issues 868, 867, 864, 863, and 862; it does not establish a universal claim about the owner.

> Quoted from the installed rubric after the edit: “(g) the title, body, and thread together name no behavior, file, symptom, or concrete deliverable at all. Author identity and starter labels never override (g).”

> Quoted from the dated change notes, before: “Status: finding recorded, rubric change PROPOSED only. rubric.md not edited.” After: “Status: COMPLETED. rubric.md edited.”

This shows the scope rule was tightened after a real false accept, and that two other candidates were already claimed by open PRs. I also used the patched rubric for direct grading of WrenAI #1202 and agentic-operator-core #132. I did not repeat the scan, regrade the original five, or run a regression evaluation of the patched rubric; I did not grade Maui #879 with the scout. The 60-day claim-staleness idea remains unapplied.

The scan and its notes show why the owner/starter-label exemption needed a limit. Proposed validation: apply both the original and patched rubric to the same saved cases, including #869 and genuinely bounded short issues, then use new candidates to check broader behavior. This comparison has not been run and is not a regression evaluation that already happened.

**Voice guard**

**What it is, and the judgment hole I wrote:**

Voice guard checks local drafts against a communication guide covering claims, questions, pings, evidence order, and AI disclosure. I adopted the evidence-order rule (“No conclusion without its artifact in the same comment”) and AI-disclosure guidance in my guide, alongside other Unit 6/course communication rules. The saved comparison shows the guide changed, but does not establish who wrote each individual rule. I cannot verify whether the original public Maui comment was checked by the guard or matched a guarded draft.

**How it evolved, dated:**

A backup from 2026-10-03 15:35:16 was compared with the current `voice-guide.md` timestamped 2026-10-10 08:19:37. The diff changes the intro from “my first contributions to Path Review” to “open-source contributions” and adds an “Upstream communication” section with claims, questions, pings, and AI disclosure. On October 10 the guard logged a stop at 08:30 against `issue-comment-draft.md` for the evidence-order rule, then a pass at 08:31 on the same file. `pr_draft.md` also got passes. The retained comparison establishes this guide change; the records cited here do not establish later guide edits. Draft revisions are separate from guide changes.

**Evidence:**

The backup is timestamped 2026-10-03 15:35:16 and the current guide is 2026-10-10 08:19:37. The diff changes the introduction and adds the Upstream communication section. That shows the guide text actually changed; it does not prove who wrote each line.

> Quoted exact excerpt from the guard log, 2026-10-10: “2026-10-10 08:30 [manual] stop: rule broken: "No conclusion without its artifact in the same comment."”

> Quoted exact excerpt from the guard log, 2026-10-10: “2026-10-10 08:31 [manual] pass”

**What the stop and pass actually show**

The target matters when reading this log. At 08:30, `pr_draft.md` passed while `issue-comment-draft.md` stopped. Those were different files, so the results do not contradict each other.

At 08:31, the same `issue-comment-draft.md` received a pass. That gives me a clear sequence: the guard stopped that local draft for the evidence rule, then later accepted it. The retained records do not show the exact sentence-level edit between those checks.

The rule was “No conclusion without its artifact in the same comment.” In plain language, that means putting the proof next to the claim. If I say I reproduced a problem, the reader should be able to see the command and output supporting it.

This was a communication check, not a test of the Maui code. The guard could check whether the draft followed its evidence rule, but it could not prove that the code fix worked. That required the separate regression test and its recorded results.

The later 08:44 hook stop was another kind of problem: the guard could not read the body file at the supplied path. A subsequent attempt passed. That was a file-location problem, not another finding about the writing.

These distinctions keep me from treating every stop as a code failure or every pass as proof of publication. I need to read the time, reason, and target together to understand what each entry actually establishes.

**Ship gate**

**What it is, and the judgment hole I wrote:**

The supplied gate runs the manifest's repository checks and also evaluates the PR evidence package, including whether the evidence matches the intended revision. I filled the manifest with four must-pass checks: changed-provider formatting, changed-test formatting, Release CodeFixes build, and Release analyzer tests. I took the commands from `CONTRIBUTING.md` and `.github/workflows/dotnet-build.yml` and scoped them to the changed files or projects. The three dated exclusions (full-solution formatting, other component/platform suites, benchmarks) were there so the gate stayed focused on the changed surface instead of becoming a full CI re-run.

**How it evolved, dated:**

The initial manifest configuration was recorded at 08:22 on October 10. Later that day I amended the contribution commit, making earlier regression evidence (commit 9a93b284, 53 insertions) no longer match the final tree (91583887, 52 insertions). At 08:36 the overall gate returned BLOCK even though all four manifest checks reported ok, because its evidence-package check found stale revision references. I recaptured before/after evidence tied to 91583887; the manifest fingerprint stayed `4e5264970fa1`, so this recovery did not change the manifest. Later the body-file path had to be changed from a tilde to an absolute path; that was only a command-argument fix, not a change to gate logic.

**Evidence:**

The ship manifest from 2026-10-10 08:22 lists the four must-pass checks and the three dated exclusions. Comparing it with the blank template shows the repository-specific rows were filled in. Gate logs show the same fingerprint `4e5264970fa1` at both 08:33 and 08:38, so the manifest itself did not change during the retries.

> Exact manifest fragments: “Code-fix formatting”; “CONTRIBUTING.md, Code Formatting; adapted to verify the changed file without rewriting it”; and “The change targets code-fix invocation selection; benchmark execution is excluded from this focused gate.” The full source rows include the selected command, source, and (for exclusions) date.

> Quoted exact excerpt from the 2026-10-10 08:36 gate log: “- verdict: BLOCK (block)”
>
> Quoted exact excerpt from the same entry: “- Release analyzer tests: `/usr/local/share/dotnet/x64/dotnet test --project src/CommunityToolkit.Maui.Analyzers.UnitTests/CommunityToolkit.Maui.Analyzers.UnitTests.csproj -c Release` -> ok (59s)”
>
> Quoted exact excerpt from the 08:36 precheck: “regression-evidence [unclear]: Before/after evidence cites commit 9a93b284 and '53 insertions', but the branch commit is 91583887 with 52 insertions, so the before failure is not tied to the committed tree.”
>
> Quoted exact excerpts from the 2026-10-10 08:38 gate log: “- verdict: PASS” and “- package: head 915838870f6bb95cfc3993dbc895a8016ba34b9f title 5f60bf45cfeb body 42965d520a7c manifest 4e5264970fa1”

Later entries at 08:38 and 08:40 show PASS on `91583887`. The 08:44 hook passed after the body-file path was corrected to an absolute path. The gate only records short “ok + duration” summaries, not full transcripts. The full Release transcript that still exists is from before the final amend.

This shows the manifest was filled with scoped checks and dated exclusions, that an amend made the earlier evidence stale, that the gate blocked despite every individual check being ok, and that later evidence tied to the final commit was accepted. It does **not** show that the runner code was rewritten, that the manifest changed during recovery, or that the path fix was anything more than a command-argument correction. The 16-test baseline is only a note from the time; there is no retained log for it.

Choosing those four checks and three exclusions was my call about the smallest set that still covered the changed surface. The 08:36 BLOCK showed me that individual ok rows are not enough when the evidence package itself no longer matches the commit under test. The gate already detects stale evidence; a possible future improvement would be to run that freshness check before the repository commands, so it can block early and avoid spending time on checks for a package already known to be stale. That ordering change is proposed, not implemented.

**PR-monitor**

**What it is, and the judgment hole I wrote:**

The supplied monitor reads PR state and applies the rules in the playbook to decide whether to prepare a move. My playbook sets a 7-day quiet period before an initial nudge, 14 days for stalled review, a hard maximum of one nudge, and a rule against nudging a merged or closed PR. A merged-PR close-the-loop follow-up draft is a different move from a nudge; the no-nudge rule did not prevent the monitor from selecting that draft.

**How it evolved, dated:**

This was retrospective work on October 21. The 15:39 state-only canary logged the PR as merged and selected no move; the 15:51 full run, after the playbook was populated, selected the merged-follow-up form and produced a conditional close-the-loop draft. That follow-up was not a nudge, so the no-nudge rule did not stop it. Comparing the template, populated playbook, and run records establishes the configuration/run sequence; timestamps alone do not establish that the run caused any later tool change. Supplementary inspection found issue #879 already closed and the PR locked; the CLA check was still queued. I declined the draft. The monitor and forms were not changed after the run.

**Evidence:**

Comparing the blank staff template with the populated playbook shows the response thresholds, nudge limit, and merged/closed-PR rule were filled in before the full run. The 15:39 canary and 15:51 run log independently record the canary state and the later merged-follow-up move. Together these artifacts show configuration and run behavior; the timestamps alone do not establish a causal change to the monitor itself.

> Quoted exact excerpts from the populated playbook: “- Initial human response: wait 7 days of quiet before a nudge is on the table.” and “- Never nudge a merged or closed PR.”

> Quoted exact excerpt from the monitor log, 2026-10-21 15:39: “- move: none (state-only canary)”
>
> Quoted exact excerpt from the monitor log, 2026-10-21 15:51: “- move: Merged-PR close-the-loop note (thanks, issue status, possible follow-up) (via the merged follow-up form)”

> Quoted exact excerpt from the run report, 2026-10-21 15:51: “- state: MERGED: the PR is merged”
>
> Quoted exact excerpt from the drafted move: “If it did not close on its own, it can be closed now that the fix is in `main`.”

When I checked further, issue #879 was already closed and the PR was locked; the CLA check was still queued. The monitor report itself does not contain those details, and the draft was never posted.

This shows the playbook was actually configured, that the canary and full run ran, and that the monitor selected a merged follow-up draft. It does **not** show that this work guided the October 10 Maui contribution, that declining the draft changed the monitor, or that any message was sent. The unresolved CLA and queued check also do not prove acceptance or waiver.

I chose the waiting and nudge limits so automated messages stay rare and never happen after merge. The run did not change how I see the monitor; it just confirmed that any generated draft still needs human context (issue status, lock, CLA) before I would act on it. I would require that extra context every time.

## Inventory

- **Original issue-select:** Unit 1 used a static rubric on a fixed set of selected issues; the later scout searches live issues and grades candidates against the configured acceptance rubric. It still lives in `tools/issue-select/`. Record: its fixture evaluation dated 2026-09-17 graded 20 packages and matched 20/20. Unit 1's selected classroom issue was Path Review #73.
- **repro-check:** Checks whether a claim/reproduction package has the expected artifacts and structure. Record: its fixture evaluation dated 2026-09-23 scored 18/20 on 20 packages. The live attempt on classroom Path Review #62 was not completed because credits were unavailable. No live Maui #879 verdict is established.
- **plan-check:** Checks a candidate plan and its plan-comment against a structured rubric; fixture scores are not live tool verdicts. Record: its fixture evaluation dated 2026-10-01 scored 20/20 on 20 packages. The live attempt on classroom Path Review #62 was blocked by the individual spend limit. No live Maui #879 verdict is established.
- **pr-precheck:** Reviews a PR package for required pieces; inside the ship gate it is one of the live checks rather than an independent final verdict. Record: the fixture evaluation dated 2026-10-03 scored 19/20 on 20 packages. The October 10 ship-gate logs include its live checks; later gate entries report those checks passing. This is not a `repro-check` or `plan-check` verdict.
- **Scoped orientation and repository memory:** A read-only pass that maps the analyzer/provider/verifier/test surface and writes local notes. Record: one scoped read-only orientation ran retrospectively on 2026-10-17, a week after the Maui PR merged; it examined the analyzer/provider/verifier/test surface and produced a 25-line locally excluded `CLAUDE.local.md`. The file is present in the local Maui clone. It did not guide the October 10 contribution.

## The Arc

**Beat 1**

Date: October 10, 2026<br>
Friction: A local draft put a claim before its supporting command/output. The guard stopped it for missing evidence.<br>
Change: The guard log records a stop and later pass on the same draft, but the retained records do not specify the sentence-level edit between them.<br>
Result: A later local pass was recorded on the same target. That pass does not mean the original public comment was created under the guard or posted from a passed draft.

**Beat 2**

Date: October 10, 2026<br>
Friction: Amending the contribution commit made the earlier regression evidence (9a93b284 / 53 insertions) stale relative to the final tree (91583887 / 52 insertions). At 08:36 the gate blocked even though every manifest check reported ok.<br>
Change: I recaptured before/after evidence tied to 91583887. The manifest fingerprint stayed the same.<br>
Result: The 08:38 and 08:40 gate entries recorded PASS, backed by the gate-log/precheck package that referenced the final commit.

**Beat 3**

Date: October 10, 2026<br>
Friction: The hook failed looking up the body file with a literal tilde.<br>
Change: I switched to an absolute body-file path. The gate implementation itself did not change.<br>
Result: The corrected command passed the hook at 08:44, and `gh pr create` opened the PR. That does not establish that the manifest checks were rerun at that moment.

**Beat 4**

Date: October 17, 2026<br>
Friction: The vague owner-filed “Review security concepts” issue passed under the original thin-writeup / starter-label exemption.<br>
Change: Branch (g) was added so the total absence of any named behavior, file, symptom, or deliverable overrides author identity and starter labels.<br>
Result: WrenAI #1202 and agentic-operator-core #132 were graded directly under the patched rubric. I am not claiming #879 was regraded or that a regression suite passed.

**Beat 5**

Date: October 21, 2026<br>
Friction: The monitor report left out issue-closure and lock context, and the conditional draft assumed a close-the-loop note was still useful.<br>
Change: Supplementary inspection filled in the missing context and I declined the generated move.<br>
Result: The draft was not posted. Nothing was sent, and the monitor and forms were left unchanged.

## Limitations and What's Next

A few boundaries still matter. The 16-test baseline is only a contemporaneous note, not a retained log. Classroom #62 and Maui #879 are separate. Fixture scores are not live verdicts. Issue closure, PR lock, and the queued CLA check are separate facts from what the monitor itself reported. The public-state snapshot is from October 21; this portfolio is being written later.

**Tool limits.**

issue-scout: The patched rubric was used for two direct candidate grades, but the scan was not repeated and the rubric was not regression-evaluated. The proposed 60-day claim-staleness threshold, minimum-age/star ranking, and non-Python fit ordering are still unapplied.

voice-guard: It only checks the rules written in its guide. Commands outside its parsing path and any technical-correctness questions are invisible to it. A local pass does not prove the published text matched the guarded draft.

ship-gate: It depends on a correctly scoped manifest and on evidence fingerprints that still point at the intended revision. Gate summaries are not full command-output transcripts.

pr-monitor: The run report did not include issue-closure or lock context, so a human had to check that before acting on the merged-follow-up draft. A nudge and a merged-PR follow-up are different moves. The October 21 run was retrospective and left the monitor and forms unchanged.

What I would do next, in order: compare the original and patched scout rubric on the same saved cases, including #869 and genuinely bounded short issues, then use new candidates to check broader behavior; consider moving the ship gate's existing evidence-freshness check ahead of repository commands, so stale packages stop earlier; and extend the monitor's state canary to surface issue status and lock state before offering a merged-PR follow-up. These are proposed next steps, not completed changes. The scout comparison is my first priority because it would check the scope-rule change beyond the two direct grades; no regression evaluation has been run.
