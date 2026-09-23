# Test Design Standard

## Rule

Test design must be driven by relevant behavior, risk, and expected outcomes rather than by indiscriminate scenario volume.

This standard applies to manual and automated testing. A well-designed scenario does not, by itself, imply that it should be automated.

## Rationale

Each test should exist for an identifiable reason. More tests do not necessarily provide more confidence, and redundant tests can increase cost without adding meaningful coverage. Test design should produce useful information about relevant behavior, risk, uncertainty, and expected outcomes. Coverage depth and priority should therefore follow the risks and behaviors that need to be understood or protected.

```text
risk
   ↓
influences
   ↓
test design depth and priority
```

## Requirements

**Identifiable purpose.** Every test must protect or investigate an identifiable behavior, business rule, risk, expected outcome, or relevant uncertainty. Tests must not be added only to increase scenario volume.

**Explicit expected outcome.** Every test must have a clear and observable expected outcome. Statements such as `Works correctly`, `Behaves as expected`, or `No errors occur` are not sufficient when a more specific outcome can be defined.

**Relevant preconditions.** Preconditions that materially affect behavior must be explicit. Test design should not require documentation of preconditions that are irrelevant to the behavior being evaluated.

**Independence.** A test scenario must not require another independent test scenario to run successfully before it. When a sequence is part of the behavior being validated, it may be modeled as one coherent flow or as an explicit state transition.

**Relevant positive and negative behavior.** When relevant to risk, test design must consider successful behavior, rejected behavior, invalid input, failure handling, and unexpected or invalid states. A negative scenario must not be created artificially for every positive scenario.

**Boundary behavior.** When relevant boundaries exist, test design must consider behavior below, at, and above the boundary. Boundary analysis must not be applied artificially where no meaningful boundary exists.

**State transitions.** When states are part of the behavior, test design must consider valid transitions, invalid transitions, resulting state, and state persistence when relevant.

**Business rules.** Business rules within scope must have explicit test coverage. Important rules must not be obscured by combining them into a single generic scenario when separate coverage is needed to understand the outcome of each rule.

**Failure behavior.** When predictable failures represent relevant risk, test design should consider validation feedback, recovery, safe failure, retry behavior, and state preservation when applicable. These considerations do not make every item required for every system or scenario.

**Redundancy control.** Test design must avoid multiple tests that exercise effectively the same behavior without adding meaningful coverage. When several inputs belong to the same behavioral class, appropriate reduction techniques should be considered. This standard does not prescribe a specific reduction technique.

**Traceability.** It must be possible to understand which requirement, behavior, business rule, risk, or expectation a test relates to. Traceability may be semantic and does not require formal identifiers in every project.

**Clarity.** Test intent must be understandable without requiring knowledge of unnecessary implementation details. The language used should be appropriate to the layer being tested.

**Focused scope.** Tests should be focused enough that failures provide useful diagnostic information. Test design should avoid combining many unrelated behaviors into a single scenario without clear justification.

**Context awareness.** Test design must account for project context. The depth, prioritization, specific techniques, risk model, and amount of coverage must be adapted to the context of the project. This standard does not establish a universal risk formula, score, scenario count, or coverage threshold.

## Allowed exceptions

Exceptions may be appropriate when legacy systems limit observability, a behavior can only be meaningfully validated through a larger flow, requirements are incomplete, environment constraints exist, external dependencies impose limitations, or decomposition would remove the real behavior being validated.

Relevant exceptions should be documented in the project context, normally through project decisions when needed. A project exception must not alter this global standard.

## Verification

Review adherence to this standard with questions such as:

```text
Does this test have an identifiable purpose?

Is the expected outcome explicit and observable?

Are relevant preconditions understood?

Does the scenario depend on another independent test?

Are important business rules represented?

Are relevant boundaries considered when applicable?

Are relevant state transitions considered when applicable?

Is meaningful failure behavior considered where risk justifies it?

Does this test add meaningful coverage or duplicate existing behavior?

Is the scenario focused enough to diagnose a failure?

Can we explain why this test exists?
```

These questions support review of the standard; they do not create a separate quality gate.

## Related

- [[Quality Philosophy]]
- [[Risk-Oriented Quality]]
- [[Automation Philosophy]]
- [[Standards]]
- [[Quality Gates]]
