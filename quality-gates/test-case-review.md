# Test Case Review Gate

## Purpose

This gate defines the minimum criteria for approving a test scenario or test case as adequately designed under the current QAOS version. It applies to manual test cases, automated scenarios before implementation, acceptance-oriented design, and regression design.

The gate verifies minimum adherence to the method before test design is considered complete. It does not replace contextual judgment or require specific test techniques, and it does not assess automation-code quality.

```text
standards/test-design.md
= defines the rules

quality-gates/test-case-review.md
= verifies whether those rules are satisfied
```

## Gate

- [ ] The test has an identifiable purpose.
- [ ] The behavior, business rule, risk, expected outcome, or relevant uncertainty being validated is clear.
- [ ] The expected outcome is explicit and observable.
- [ ] Relevant preconditions are identified when they materially affect behavior.
- [ ] The scenario does not depend on another independent test being executed first.
- [ ] The scenario is focused enough to make failures reasonably diagnosable.
- [ ] Important business rules within scope are represented.
- [ ] Relevant positive, negative, or failure behavior has been considered when justified by risk.
- [ ] Relevant boundaries have been considered when applicable.
- [ ] Relevant state transitions have been considered when applicable.
- [ ] The scenario adds meaningful coverage and is not an unnecessary duplicate.
- [ ] The test intent is understandable from its name or description.
- [ ] Terminology is consistent with the domain or project context.
- [ ] The scenario avoids unnecessary implementation detail.
- [ ] Traceability to the relevant requirement, behavior, rule, risk, or expectation is possible.
- [ ] Assertions or expected validations are sufficient to prove the intended outcome.
- [ ] No sensitive or client-confidential information is included unnecessarily.

Conditional criteria are mandatory only when the corresponding behavior or risk exists. This applies, for example, to boundaries, state transitions, negative behavior, and failure behavior.

```text
PASS
= all applicable mandatory criteria are satisfied or explicitly justified

FAIL
= one or more applicable mandatory criteria remain unsatisfied without justification
```

## Failure handling

If an applicable mandatory criterion fails, the test design must be corrected or a justified project-specific exception must be documented when correction is not appropriate.

Relevant exceptions must be recorded in the project context, normally in `work/decisions/`. A project exception does not modify the QAOS gate. This gate must not be ignored.

## Related

- [[Test Design Standard]]
- [[Assertions Standard]]
- [[Naming Standard]]
- [[Documentation Standard]]
- [[Risk-Oriented Quality]]
- [[Quality Gates]]
- [[Decisions]]
