# AI301 Unit 1: Issue Selection

## What I did

For Unit 1, I built and tested an `issue-select` skill for choosing a good first issue in an open-source repository.

The main idea was to avoid picking an issue just because it looked easy. I wanted to check the actual repository and issue state first, then use a consistent rubric to decide whether an issue was active, available, appropriately scoped for a newcomer, and compatible with the project's contribution requirements.

For my live repository, I used:

`codepath/pathreview-ai301-fa26-s1`

I evaluated three candidate issues:

- [Issue #73](https://github.com/codepath/pathreview-ai301-fa26-s1/issues/73) — README and `.env.example` disagree about which LLM API key to set
- [Issue #72](https://github.com/codepath/pathreview-ai301-fa26-s1/issues/72) — `verify_password` raises `UnknownHashError` on malformed stored hashes
- [Issue #69](https://github.com/codepath/pathreview-ai301-fa26-s1/issues/69) — output parser crashes on a top-level JSON array fallback

I selected **issue #73**.

---

## Rubric

The main part of the assignment was completing:

`tools/issue-select/rubric.md`

The rubric gives me a consistent way to evaluate an issue instead of making the decision based only on personal judgment.

The checks I used were:

1. **Repository activity**
2. **Repository availability**
3. **Bounded newcomer scope**
4. **Whether the issue is already claimed**
5. **Contribution-policy compatibility**

The rubric uses required checks to determine the final verdict. An issue needs to meet the required conditions to be accepted.

I also refined the newcomer-scope check during the assignment. The goal was to distinguish a genuinely bounded issue from an umbrella or overly broad issue without rejecting an issue simply because completing it involves more than one related step or file.

The completed rubric is located at:

`tools/issue-select/rubric.md`

---

## Issue-Selection Skill

I installed the completed skill in Claude Code at:

`~/.claude/skills/issue-select/`

The repository version is included in:

`tools/issue-select/`

The required skill files are:

```text
tools/issue-select/
├── rubric.md
├── SKILL.md
├── scope.md
└── references/
    └── evidence-guide.md
