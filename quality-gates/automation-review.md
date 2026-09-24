# Automation Review Gate

## Purpose

This gate defines the minimum criteria for considering an automated test implementation adequate under QAOS. It must be applied before the implementation is considered complete.

The gate verifies adherence to existing standards. It does not replace contextual judgment or require a specific framework or architecture. Conditional criteria are mandatory only when applicable.

```text
test-case-review.md
= verifies the quality of the test design

automation-review.md
= verifies the quality of the automated implementation
```

A well-designed test may have a poor automated implementation. Technically well-written code does not compensate for a test without purpose or meaningful validation.

## Gate

- [ ] The automated test preserves an identifiable test purpose.
- [ ] The implementation validates the behavior or outcome that gives the test its purpose.
- [ ] Assertions or validations provide sufficient evidence for the intended outcome.
- [ ] Successful execution is not being used as a substitute for meaningful validation.
- [ ] Failure output provides enough information to understand the relevant expectation and observed outcome.
- [ ] The test does not depend on another independent test being executed first.
- [ ] Required state is established or controlled appropriately for the scenario.
- [ ] Relevant test data state is known and appropriate to the test purpose.
- [ ] Unnecessary production, sensitive, or client-confidential data is not used.
- [ ] Shared mutable data does not create uncontrolled dependencies.
- [ ] Parallel execution collisions are considered when relevant.
- [ ] Created or mutated data has an understood lifecycle.
- [ ] Sources of nondeterministic behavior are controlled or explicitly understood when reasonably possible.
- [ ] Arbitrary timing assumptions are not used when a reliable synchronization mechanism is available.
- [ ] Failures provide enough context to support diagnosis.
- [ ] Relevant evidence is preserved when useful and safe.
- [ ] Test intent is understandable, and naming communicates responsibility.
- [ ] Unnecessary duplication is avoided without introducing premature abstraction.
- [ ] Abstraction is proportional to the responsibility it serves.
- [ ] The test is not unnecessarily coupled to volatile or irrelevant implementation details.
- [ ] Irrelevant implementation changes should not routinely break the test.
- [ ] The test and its supporting components have responsibilities that are reasonably clear and focused.
- [ ] Relevant environment assumptions are understood or controlled.
- [ ] Destructive behavior is controlled, and tests affecting shared or production-like environments do so intentionally and safely.
- [ ] Credentials and secrets are not hardcoded or unnecessarily exposed.
- [ ] Logs, reports, and evidence do not unnecessarily expose sensitive or client-confidential information.
- [ ] Relevant side effects are considered and validated when they are part of the expected behavior.
- [ ] Cleanup is performed when necessary to prevent contamination, collisions, unreliable future execution, or harmful persistent state.

Conditional criteria are mandatory only when the corresponding behavior, dependency, environment characteristic, or risk exists. This applies especially to cleanup, parallel execution, side effects, shared environments, persistent state, external dependencies, and production-like environments. `Not applicable` must not be used to disregard an existing risk.

```text
automation-code.md
= defines engineering rules for automated tests

test-data.md
= defines rules for data and state

assertions.md
= defines validation quality

naming.md
= defines naming quality

automation-review.md
= verifies whether the applicable implementation rules are satisfied
```

Technology-specific implementation details belong in `adapters/`. This gate verifies the required property, not a framework-specific mechanism for achieving it.

## Result

```text
PASS
= all applicable mandatory criteria are satisfied or have an explicitly justified project-specific exception

FAIL
= one or more applicable mandatory criteria remain unsatisfied without an accepted justification
```

## Failure handling

If an applicable mandatory criterion fails:

1. The implementation must be corrected; or
2. A justified project-specific exception must be documented when correction is not appropriate.

Correction is the preferred outcome. An exception must include an understandable justification and, when materially relevant, must be recorded in the project context, normally in `work/decisions/`.

A project-specific exception does not modify or weaken the global QAOS gate. This gate must not be ignored.

## Related

- [[Automation Philosophy]]
- [[Automation Code Standard]]
- [[Test Data Standard]]
- [[Assertions Standard]]
- [[Naming Standard]]
- [[Documentation Standard]]
- [[Test Case Review Gate]]
- [[Client Data Handling Policy]]
- [[Credentials and Secrets Policy]]
- [[Quality Gates]]
- [[Adapters]]
- [[Decisions]]
