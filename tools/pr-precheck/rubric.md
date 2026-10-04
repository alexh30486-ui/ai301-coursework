# Rubric: is this pull request ready to submit?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| plan-fidelity | Complete diff paired with plan scope and deviation notes. | Pass when delivered behavior fits the plan or recorded deviations. A disclosed partial delivery may pass when the remaining boundary and verified fix are clear. Fail for silent additions or omissions. | required |
| description-faithful | Title and description paired with diff and test output. | Pass when claims match delivered changes and observed outcomes, including material limitations. Fail for contradicted or unsupported success claims. | required |
| regression-evidence | Before/after commands and output against repro and plan expectations. | Pass when concrete executed steps show the relevant before failure and after behavior through the affected code path. Mocks may supplement proof with their limits stated. Fail for generic assertions, unrelated behavior or bypassing the fix. | required |
| repository-checks | Required repository commands paired with execution outcomes. | Pass when applicable checks were attempted and outcomes are shown. Explained pre-existing failures or environment blocks may pass when the fix is verified and no explicit must-pass rule is violated. Fail for checks never attempted, absent outcomes or unresolved change-induced required failures. | required |
| diff-reviewable | Every diff hunk and committed file. | Pass when the fix and necessary support are visible without unrelated debris. Fail for debug leftovers, dead experiments or unrelated churn obscuring the change. Necessary support changes and multiple commits do not fail by themselves. | required |
| template-and-disclosure | Explicit template and contribution policies against outgoing text. | Pass when applicable requirements are substantively fulfilled, including required disclosure. Fail for omitted required sections, boilerplate or missing required disclosure. Apply stated assistance assumptions; never infer authorship from prose. Silent policy alone creates no disclosure rule. Live Path Review work uses the mandatory template and discloses actual AI assistance. | required |
| thread-engagement | Relevant maintainer requests paired with changes and description. | Pass when direction is followed or a reasoned departure is addressed consistently with repository rules. Fail for silently ignored blocking requests. Empty threads and classmates' parallel classroom work do not fail. | required |

## Verdict rule

Accept only when all required checks pass. Required fail or unclear means reject. Grade every check. Preferred checks never affect the verdict. Demonstrated omissions fail; unavailable evidence is unclear. Apply disclosed-limitations rules rather than demanding perfection.
