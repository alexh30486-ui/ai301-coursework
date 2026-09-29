# Procedure: how this skill grades a plan package

## Read order

1. Identify eval mode from a supplied frozen bundle, or live mode from the submitted plan, draft comment, and issue URL. If the input mode is ambiguous, request the missing input before grading.
2. In live mode first read scope.md. Confirm the repository matches the configured source and the plan concerns the student's Unit 2 issue or assigned house issue. Stop without a verdict for an unfilled scope or outside-scope issue. Read voice-guide.md next. In eval mode ignore both files and make no network requests.
3. Read rubric.md and references/evidence-guide.md completely. If there are no completed checks or procedure steps, stop without inventing criteria.
4. Read the issue context, thread, and repository rules before the candidate's argument. Record the requested outcome and constraints. Read the reproduction next; record trigger, environment, actual result, expected result, and controls. This establishes the evidence before the plan can bias its interpretation.
5. Read the complete candidate plan, including test strategy, unknowns, and deviations. Read the outgoing comment last and compare it with the plan. In live mode use the student's posted repro; for a house issue use the repro pack quoted in the drafts. Do not silently use other local files to fill omissions.

## Evidence gathering

1. Build a small evidence ledger with source location, short quote or faithful fact, and the checks it supports. Follow the evidence guide's exact locations in the chosen mode.
2. Gather diagnosis and grounding: pair each material causal claim and proposed intervention with the observed repro facts. Feed diagnosis-grounded and cause-targeted.
3. Gather scope: list planned actions and their connection to the requested outcome or regression coverage. Feed scope-bounded.
4. Gather execution: record the entry point, actual actions, needed dependencies, and ordering. Feed executable.
5. Gather tests: record input/trigger, real code path, observable assertion, expected failure before and expected behavior after, plus relevant normal behavior. Feed test-decisive.
6. Gather honesty: record consequential uncertainties, how they will be resolved, completed-work claims, and any explicit deviations. Feed uncertainty-honest.
7. Gather comms: pair applicable maintainer requests with the comment's response; pair explicit contribution requirements with compliance evidence. Feed thread-aware and conventions. In live mode separately record voice-guide notes. If a live source is inaccessible, record the limitation instead of treating it as an empty policy or thread.

## Check execution

1. Execute all eight checks in rubric-table order. For each, read its pass condition, consult the ledger entries, and assign pass, fail, or unclear with one deciding evidence sentence. Do not stop after the first failure.
2. If a deciding fact is missing, re-read the specific source section once. In live mode, attempt the identified relevant source if it has not been read. Do not browse in eval mode. If evidence remains unavailable, grade unclear unless the rubric explicitly makes that omission a fail.
3. Distinguish absent evidence from absent obligation: an empty thread imposes no extra maintainer direction; a silent policy imposes no AI disclosure; a planned test does not need already-executed output. Do not infer requirements from formatting.
4. Prefer the demonstrated artifact over a conflicting unsupported claim. Explain the conflict. Test whether the validation could still pass if the original defect remained; if so, apply test-decisive accordingly.
5. A ledger entry with a source and no unresolved contradiction is enough to grade its check without rereading the entire package. Revisit only the affected sources when new conflicting evidence appears.
6. For an updated plan, treat deviations as part of the current plan and repeat all checks. Determine whether the proposed follow-up comment accurately explains any changed public intent. Never claim the updated plan was previously approved.

## Verdict assembly

1. Apply the rubric's rule mechanically: accept only if every required check passes. Required fail or unclear means reject; preferred checks never change it.
2. Before the JSON, summarize each check briefly, explain decisive failures or missing evidence, and report live voice-guide violations by quoting the rule. Report any procedure gap without inventing a substitute step.
3. End with exactly one fenced json block containing item (issue URL in live mode or package ID in eval mode), checks (objects with name, grade, evidence), and verdict (accept or reject). Use exact rubric check names and only pass, fail, or unclear as grades. Escape strings correctly; do not use placeholders as evidence.
4. Verify every rubric check appears once, the verdict follows the grades, and the JSON is syntactically valid. Write nothing after that final block. The output is a plan judgment, not permission to post or a claim that implementation tests have run.
