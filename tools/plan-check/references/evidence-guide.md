# Evidence guide: where evidence lives in a plan package

Eval mode uses only the frozen bundle. Its source identifier is not permission to fetch the current issue. Live mode uses the scoped issue, the student's posted reproduction, relevant repository documentation, and the submitted plan and comment. Do not rescue a draft with unquoted evidence from unrelated local files.

## Diagnosis and grounding

- Eval: read the issue context, repro-evidence inputs, environment, controls, output, and the candidate plan's diagnosis and intervention. Live: read the issue body and the student's posted repro comment, then the draft diagnosis and approach.
- Record the trigger, actual behavior, expected behavior, strongest failure artifact, proposed mechanism, and intervention. Use these for diagnosis-grounded and cause-targeted. Good evidence links the intervention to the observed mechanism; it does not equate any error with the reported bug. A labeled hypothesis needs a concrete check before dependent edits.

## Scope

- Eval: compare the candidate plan's actions and exclusions with the issue request and thread constraints. Live: use the same parts of the draft against the live issue and relevant maintainer decisions.
- For scope-bounded, list each proposed change and what issue outcome or regression test it serves. One necessary fix can span several files. Unrelated improvements remain scope creep even if easy. A missing out-of-scope heading is not an absent boundary when the actions already define it.

## Executability

- Eval: inspect named files, functions, components, implementation actions, dependencies, and ordering in the candidate plan. Live: inspect those details in the submitted plan and quoted evidence; use repository docs for stated build conventions, not to invent missing plan steps.
- For executable, record the first action and the steps that depend on it. A reader needs an actionable entry point and approach, not finished code. An unknown implementation choice is acceptable when a specific investigation and decision precedes it.

## Test plan

- Eval: compare candidate validation with repro-evidence steps, inputs, output, and expected behavior. Live: compare the draft tests with the student's posted reproduction and applicable documented test commands.
- For test-decisive, record the trigger, code path exercised, observable assertion, and expected before/after difference. A targeted regression test may replace a costly manual repro if it preserves the relevant mechanism. Mocking an unrelated service can isolate a test; mocking away the defective behavior cannot prove the fix. Separate independent failures so an overall error does not mask the target component's improvement.

## Honesty

- Eval: compare claims in the diagnosis and comment with the repro block; inspect risks, unknowns, and deviations if supplied. Live: compare draft claims with posted evidence and explicit deviation notes.
- For uncertainty-honest, mark each material claim as observed, inferred, or planned. Concrete verification can make uncertainty manageable. A deviation must say what changed and why; do not invent a deviation or require one in a package that presents an initial plan. Proposed validation is not a completed test result.

## Comms

- Eval: read thread highlights and the repo-facts template and policy statements, then compare the candidate comment and plan. Live: read the issue body and all available comments, follow relevant maintainer links to contributing guidelines and templates, and read the installed voice guide. Record an access failure explicitly.
- For thread-aware, record each relevant maintainer request and where the comment addresses it. A classmate's classroom plan is not exclusive ownership. For conventions, record the actual applicable rule and the evidence of compliance or violation; do not invent a disclosure rule. Apply requirements to the artifact they govern: a bug-report template is not automatically a plan-comment template.
- Live voice-guide notes quote the rule and offending text. They do not independently change the rubric verdict. Do not infer authorship from writing style.
