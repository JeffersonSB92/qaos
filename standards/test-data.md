# Test Data Standard

## Rule

Test data must be intentionally controlled so that tests remain reliable, understandable, and safe without creating unnecessary coupling to shared or uncontrolled state.

## Rationale

Test data affects reliability, can introduce flakiness and dependencies between tests, and can make failures difficult to reproduce. It can also expose sensitive information when handled without appropriate care. Test data should reflect only the context needed to validate the intended behavior.

```text
automation-code.md
= controls how automation behaves as engineering code

test-data.md
= controls the data and state used by tests
```

## Requirements

**Controlled data.** Tests must use data whose relevant state is known or intentionally prepared whenever reasonably possible. Tests should avoid depending on unknown or unnecessarily mutable data.

**Test isolation.** A test should not rely on data created or modified by another independent test. When sharing is necessary, the dependency must be explicit and controlled.

**Purpose-specific data.** Test data should contain only what is necessary to validate the intended behavior. Tests should avoid excessively large or complex datasets when they add no meaningful value.

**Synthetic data preference.** Synthetic, generated, or controlled test data should be preferred when it can provide sufficient confidence. Real data may be used only when necessary and compatible with applicable policies; synthetic data is not mandatory in every context.

**Production data protection.** Real production data must not be copied into test environments or automation artifacts without legitimate need and appropriate authorization. When its use is necessary, teams must minimize the data used, sanitize or anonymize it when feasible, avoid unnecessary duplication, and preserve client-specific restrictions.

**Sensitive data.** Test data must not expose credentials, secrets, personal information, or confidential business data without legitimate need and appropriate protection. Real sensitive values must not be used in reusable QAOS examples.

**Reproducibility.** When a failure depends on specific data conditions, those conditions should be reproducible or describable enough to support investigation. This does not require every dataset to be permanently retained.

**Creation strategy.** Data may be prepared through different mechanisms depending on the project, such as application interfaces, APIs, database setup, fixtures, factories, scripts, or seeded environments. No approach is universally required; the choice belongs to project context and, when technology-specific, to adapters.

**Shared data.** Shared mutable data should be avoided when it can create coupling, race conditions, or nondeterministic behavior. Read-only shared reference data may be acceptable when stable and appropriate.

**Unique data.** Where collisions or parallel execution may occur, test data should support uniqueness when necessary. This standard does not prescribe identifier, timestamp, or other uniqueness formats.

**Cleanup and lifecycle.** Tests must consider what happens to data created or changed during execution. Possible strategies may include cleanup, transaction rollback, disposable environments, isolated namespaces, or controlled persistent records. No single strategy is universally required.

**Parallel execution.** Test data design should account for concurrent execution when the suite or environment supports parallelism. Shared data must not create silent collisions between independent executions.

**Time-sensitive data.** Tests involving dates or time must control relevant temporal assumptions whenever practical. The concrete mechanism belongs to the project context or relevant adapter.

**Data readability.** Test data should make scenario intent understandable. Tests should avoid unnecessarily obscure or meaningless values when domain-relevant data improves clarity.

**Data mutation.** A test that mutates data must consider whether that mutation can affect other tests, later executions, shared environments, or downstream systems.

**Evidence derived from data.** Logs, screenshots, traces, and other evidence derived from test data must be handled in accordance with the Client Data Handling Policy and Credentials and Secrets Policy. They must not unnecessarily expose client data, credentials, or secrets.

Technology-specific details, including concrete fixture mechanisms, data factories, environment seeding, rollback interfaces, and other implementation choices, belong in `adapters/`.

## Allowed exceptions

Exceptions may be appropriate when legacy systems provide only shared environments, external systems own the required data, production-like data is necessary for a specific validation, environment reset is impractical, or full isolation is technically unavailable.

Relevant exceptions must be understood, have known scope, preserve minimum necessary exposure, and be documented in project decisions when materially important. A local exception must not alter this global standard.

## Verification

Review adherence to this standard with questions such as:

```text
Is the relevant test data state known?

Does this test depend on data produced by another independent test?

Is the data more complex than necessary?

Could synthetic or controlled data provide the required confidence?

Does the test expose production or sensitive information unnecessarily?

Can the relevant data conditions be reproduced?

Could shared mutable data create nondeterministic behavior?

Could this test collide with parallel execution?

What happens to created or mutated data after the test?

Are time-dependent assumptions controlled where relevant?

Does the chosen data make the scenario easier to understand?
```

These questions support review of the standard; they do not create a separate quality gate.

## Related

- [[Quality Philosophy]]
- [[Risk-Oriented Quality]]
- [[Automation Philosophy]]
- [[Test Design Standard]]
- [[Automation Code Standard]]
- [[Client Data Handling Policy]]
- [[Credentials and Secrets Policy]]
- [[Standards]]
- [[Adapters]]
