# Test Case Review Gate

## Purpose

This gate defines the minimum criteria for considering a test scenario or test case adequately designed. It applies to manual test cases, automated scenarios before implementation, acceptance-oriented design, and regression design.

The gate verifies adherence to existing standards and must be applied before test design is considered complete. It does not replace contextual judgment, require specific test design techniques, or assess automation-code quality. Conditional criteria are evaluated only when applicable.

```text
standards/test-design.md
= defines how tests should be designed

standards/assertions.md
= defines how expected outcomes should be meaningfully validated

standards/naming.md
= defines how intent should be communicated

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

Conditional criteria are mandatory only when the corresponding behavior, condition, or risk exists. This applies, for example, to boundaries, state transitions, negative behavior, and failure behavior. A scenario must not fail because a conditional criterion does not apply, but `not applicable` must not be used to disregard a relevant behavior, condition, or risk.

## Result

```text
PASS
= all applicable mandatory criteria are satisfied or have an explicitly justified project-specific exception

FAIL
= one or more applicable mandatory criteria remain unsatisfied without an accepted justification
```

## Failure handling

If an applicable mandatory criterion fails:

1. The test design must be corrected; or
2. A justified project-specific exception must be documented when correction is not appropriate.

Correction is the preferred outcome. An exception must include an understandable justification and, when materially relevant, must be recorded in the project context, normally in `work/decisions/`.

A project-specific exception does not modify or weaken the global QAOS gate. This gate must not be ignored.

## Related

- [[Test Design Standard]]
- [[Assertions Standard]]
- [[Naming Standard]]
- [[Documentation Standard]]
- [[Risk-Oriented Quality]]
- [[Quality Gates]]
- [[Decisions]]
