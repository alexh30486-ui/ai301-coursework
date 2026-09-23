# Evidence guide: where proof lives in a reproduction package

For every kind of proof a rubric check names, this file says where to find it and what good looks like. Read the issue first, then the claim, then the report; the deciding evidence is almost always the artifact read against the issue's described behavior.

## Environment

- Where it lives: In an eval bundle, the repro report's opening "Environment:" line (or a Setup/Versions block). The target to compare against is the issue's body (reporter's version and platform), the thread highlights (maintainer notes such as "confirmed on main" or "only on the Store build"), and the repo-facts block's latest release. Live: the draft's environment line; the issue body and comments on GitHub; the releases page for the current version; the repo's bug template for what fields it wants.
- What good looks like: The project version and the platform are named, plus any runtime component the issue itself turns on (shell, browser, driver, build profile, install method). The versions named match what the issue targets, or the difference is called out in the report ("issue is on main, I tested 1.3.1 release"). A report that tests an older version than the issue confirms on, without saying so, does not have a sufficient environment record even if it lists versions.

## Steps

- Where it lives: In an eval bundle, the repro report's numbered or narrated steps between the environment line and the artifact. Compare against the issue body's own trigger (the exact command, flag syntax, operator, config snippet, expression) and any thread comment that refines it. Live: the draft's steps; the issue body and its linked playground/repo.
- What good looks like: A stranger can start from an empty directory or a public link and reach the trigger using only what the steps show. Every input file, config, and command is either pasted or publicly fetchable. The trigger is the issue's trigger character for character (offset-from-end vs. prefix range, `=` vs. `:`, bound vs. unbound variable). Steps that live in a private repo, reference an unshared config, or omit the flag the issue says matters (driver, profile) are not followable.

## Behavior shown

- Where it lives: In an eval bundle, the fenced blocks and quoted output inside the repro report (terminal transcript, log excerpt, produced CSS/JSON, exit code, screenshot description). Read each one against the issue body's stated behavior: the exact error message, exit code, panic vs. graceful validation error, wrong value, missing header, blank pane. Live: the same, in the draft.
- What good looks like: The artifact shows the same failure class the issue describes. A capacity-overflow panic (exit 101) is not shown by an argument-validation error (exit 1); an "Invalid path expression" runtime error is not shown by a compile error; a crash is not shown by garbled output with the process still alive; a blank pane is not shown by a version banner. If the report says "reproduced" there must be an artifact that a reader can point at and say "that is the issue's behavior". If the report says "could not reproduce", the artifact should show the correct/non-triggering output that the attempt produced.

## Honesty

- Where it lives: In an eval bundle, the report's Expected/Actual lines and any sentence with "reproduced", "confirmed", "verified", "guaranteed", "root cause", read side by side with the artifacts above and the environment record. Also the claim comment's summary of what was done.
- What good looks like: Every claim is backed by something shown in the same report. "Confirmed on Windows and macOS" requires artifacts from both. A diagnosed root cause requires a transcript or code reference that shows it. An honest cannot-reproduce says "did not reproduce", shows what happened instead, and names the differences from the issue (OS, shell, version, data size) and what it suspects would trigger it; that is a pass. Expected and actual must match the artifact's direction (the artifact shows X, so Actual says X). A polished report whose own artifact contradicts its conclusion fails.

## Comms

- Where it lives: In an eval bundle, the candidate claim comment (read against the issue title/body/thread) and the repo-facts block's "bug reports" template line and "contribution policy" line, including any AI-use policy. Live: the draft comment; the repo's CONTRIBUTING.md, AI_POLICY.md or equivalent, the issue template, and the scope's house rules.
- What good looks like: The claim names the issue's specific symptom or component and one next step the author controls (investigate, test the patch, report back), never a fix date or a guarantee, never "assign me / reserve this". Boilerplate is detectable by the swap test: if the comment would read identically on a different issue, it fails. For AI policy: course packages are AI-assisted, so a policy that says all AI use must be disclosed is met only when a comment says so and how much (tool, extent). A policy that requires comments in the human's own words is met by a specific, first-person, non-templated comment. A permissive policy (responsibility only) or no policy imposes nothing.
