# Voice guide: how I talk upstream

## Who I am in threads

I am a student contributor making my first contributions to Path Review. I have not maintained this codebase and I say so. What readers get from me: a specific reproduction from my own machine, the exact commands and output, and an honest statement of what I did and did not see. I promise investigation, never fixes or dates.

## Rules I write by

### Rule: Name the specific thing

Every comment names the issue's concrete symptom, component, or trigger. If my comment would read the same on another issue, rewrite it.

- Wrong: "I'd love to work on this issue, it looks interesting!"
- Right: "I'd like to look into the score column showing 0 when the review has no ratings yet (#42). I'll reproduce on the current main and post steps and output here."

### Rule: Promise only what I control

I promise to investigate, reproduce, and report. I never promise a fix, a PR, or a date.

- Wrong: "I can fix this by Friday, please assign it to me."
- Right: "Next step for me is reproducing this locally and posting what I find. If I get a fix working I'll open a PR referencing this issue."

### Rule: Show, then state

Any claim of "reproduced" or "confirmed" comes after the pasted command and output that shows it. No conclusion without its artifact in the same comment.

- Wrong: "Confirmed, this crashes for me too."
- Right: "Ran `python -m pathreview score 7` on main at 3f2a1c; output: `ZeroDivisionError: division by zero` at scoring.py:88. Same traceback as the issue."

### Rule: Say what differed

If my environment or result differs from the issue, I say exactly what differed, in the same sentence as the result.

- Wrong: "Could not reproduce."
- Right: "Could not reproduce on macOS 15 / Python 3.12; the issue is on Ubuntu with Python 3.10. Output was `score: 4.0` (expected per the issue: a crash). The difference may be the dict-ordering change; I have not confirmed that."

### Rule: Disclose AI help when I used it

If I used an AI assistant to draft or check a comment, and the repo's policy asks for disclosure, I say which tool and how much, in one sentence.

- Wrong: (no mention)
- Right: "I used Claude Code to help draft this report and check it against my notes; I ran every step and read every output myself."

## Things I never post

- "Please assign me", "keep this reserved for me", or any ask that blocks classmates.
- "Same as above", "+1", "can confirm" with no artifact of my own.
- A fix date, a guarantee, or "easy fix".
- "Great project!", "Hello sir", or flattery aimed at maintainers.
- A root cause stated as fact when I have only a hunch. I write "I suspect" and say why.
- A conclusion about a platform or version I did not run.
