# Unit 2: Reproduction Check

## Run history

I evaluated the installed `repro-check` rubric and evidence guide on all 20 scored packages. The completed run agreed with the gold verdicts on **18/20**, meeting the **18/20 PASS** bar. I saved that full run as `beat-1-sandbox/unit-2/eval-run.txt` and committed it with the skill files in commit `6928087`. Two packages disagreed: `pkg-03` failed my `conventions` check and `pkg-10` failed my `steps-followable` check, although both gold labels were `accept`.

I later tried revised wording, but Claude exited with errors on 15 packages. That attempt was a partial run, not a second full score; it did not overwrite the saved `eval-run.txt`. I restored the original rubric and evidence guide before copying the skill files into the coursework repository. The **18/20** run is the evaluation evidence for the committed version.

## Package analysis — `pkg-10`

`pkg-10` concerns Starship issue #7648, where the `directory` module reportedly disappears when a symlink points to a subdirectory inside a Git repository and `repo_root_style` is enabled. The candidate report does **not** claim to reproduce that failure. It describes Starship 1.26.0 on Ubuntu 24.04 with zsh 5.9, creates the Git repository and symlink layout, shows the `[directory]` configuration, and records a prompt in which the directory module remains visible. It also says that the original report used macOS and fish 4.7.1 and that those environment differences may matter. The claim comment promises further investigation on a matching environment rather than a fix or date.

The gold verdict is `accept`; my rubric returned `reject` for `steps-followable`. The report supplies enough information to repeat **the attempt it actually made** and is explicit that it did not reproduce the macOS/fish symptom. The evaluator appears to have treated a difference from the issue's original environment as a failure to follow the steps. That is stricter than the gold label's treatment of an honest cannot-reproduce report. The displayed `starship.toml` content is a reproducible input even though the transcript shows `cat` rather than the command that created the file. I would still reject a report that hid a required input, omitted the essential symlink/configuration trigger without saying so, or claimed to reproduce the bug using a different trigger.

## Check rationale

My `outcome-honest` check says: “A cannot-reproduce passes when it says so plainly, shows what it got, and names what differed from the issue (platform, version, data shape) or what a triggering setup likely needs.” `pkg-10` does those things: it says “cannot reproduce,” gives the visible prompt and `starship explain` result, and identifies the OS and shell differences.

My `steps-followable` check says: “A stranger with only public access could re-run every step from the stated starting state to the trigger: inputs, commands, and config are shown or publicly fetchable,” and also requires “the trigger used [to be] the same one the issue describes.” The report shows the symlink, Git repository, and configuration. The tension is that the check does not explicitly say whether, for a **cannot-reproduce** report, the stranger must recreate the original reporter's platform or the candidate's disclosed attempt. I intended the latter while requiring an exact trigger for a claim of successful reproduction. That ambiguity explains the false rejection.

## Trade-offs and next step

I could clarify `steps-followable` so a disclosed, nonmatching environment can pass when the candidate honestly reports what happened and supplies repeatable steps for that attempt. I would keep the requirements for public inputs, the issue's essential trigger, and evidence matching any claim of successful reproduction. This preserves protection against plausible reports that actually test a different command or private setup.

The saved rubric already passed at 18/20. I did **not** replace it with wording that lacks a completed full evaluation: the later partial run cannot establish whether a change improves `pkg-10` without regressing other packages. A future revision would need a successful complete run, including checks on cases from the categories it might affect. The Starship report here is an evaluation package, not an observation I personally made or a comment to post upstream.
