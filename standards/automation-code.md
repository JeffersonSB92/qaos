# Automation Code Standard

## Rule

Automated test code must be treated as maintainable engineering code and must provide reliable, understandable, and diagnosable feedback.

## Rationale

Automation code has a lifecycle and requires maintenance as systems, environments, and risks evolve. Its design influences whether a suite can be trusted, whether failures can be investigated, and whether change remains sustainable. Poorly designed automation can create noise and unnecessary complexity rather than useful feedback.

```text
test-design.md
= what should be tested and how the scenario is designed

automation-code.md
= how automated implementation should behave as engineering code
```

## Requirements

**Independent execution.** Automated tests must not depend on the successful execution of another independent test. Execution order must not determine a test result. When a sequence is part of the behavior being tested, it may exist within the same coherent flow.

**Controlled state.** Tests must control the state required for their execution as much as reasonably possible. They should avoid depending on residual state left by previous executions.

**Deterministic behavior.** Automation should produce the same result when executed under the same relevant conditions. Known sources of nondeterminism should be controlled or explicitly understood. This does not assume that every system can be made perfectly deterministic.

**Explicit assertions.** Automated tests must contain meaningful validation of the behavior they are intended to protect. Tests must not merely perform actions without checking a relevant outcome. This standard does not define a minimum number of assertions.

**Clear intent.** The purpose of a test must be understandable from its structure and naming without unnecessary investigation into implementation details. Detailed naming conventions are outside the scope of this standard.

**Diagnostic failures.** A failure should provide enough information to investigate the behavior that failed. Automation should avoid masking the actual cause behind generic errors whenever reasonably possible.

**Minimal unnecessary coupling.** Tests should avoid unnecessary coupling to unrelated system behavior, volatile implementation details, other tests, and shared mutable state. Not every technical dependency is inappropriate; some dependencies are inherent to the test level and may be justified by the feedback required.

**No arbitrary waiting.** Automation must not rely on arbitrary fixed delays when a deterministic or observable synchronization mechanism is reasonably available. The concrete synchronization approach belongs to the relevant adapter.

**Resource cleanup.** When tests create resources or state that may affect future executions, cleanup must be considered. The concrete approach may vary according to system architecture, environment, test level, and isolation model. Cleanup is not required when the environment already guarantees appropriate isolation.

**Reuse without premature abstraction.** Reusable logic may be extracted when it reduces meaningful duplication or improves clarity. Automation must avoid unnecessary abstraction that makes tests harder to understand.

**Failure transparency.** Automation must not suppress, ignore, or convert meaningful failures into successful results merely to keep the suite green. Retries may exist when justified, but they should not mask persistent failures or unknown flakiness. This standard does not define a retry policy.

**Maintainability.** Automation code must favor readability, simplicity, clear responsibilities, localized change, and predictable behavior. It should avoid clever abstractions when simpler solutions communicate intent more clearly.

**Observability and evidence.** When useful for diagnosis, automation should expose sufficient evidence about failures, such as logs, request information, screenshots, traces, or relevant state information. No evidence type is universally required. Evidence must respect the Client Data Handling Policy and Credentials and Secrets Policy: it must not unnecessarily expose client data, credentials, or secrets.

**Environment awareness.** Tests must not silently assume environmental conditions that materially affect their behavior. Relevant environment dependencies should be explicit or controlled.

**Production safety.** Automation must not perform destructive or unsafe operations against production systems unless this is explicitly designed, authorized, and controlled by the engagement.

This standard defines global automation-code behavior. Technology-specific details, including fixture interfaces, selector strategies, synchronization mechanisms, framework configuration, test runners, and language idioms, belong in `adapters/`.

```text
Automation Philosophy
        ↓
Automation Code Standard
        ↓
Technology Adapter
        ↓
Project implementation
```

## Allowed exceptions

Exceptions may be appropriate when legacy systems prevent ideal isolation, external systems introduce unavoidable nondeterminism, third-party components expose limited observability, larger end-to-end flows are required, or temporary technical constraints exist.

Exceptions must have a justification and known scope. They must not silently become the default practice and should be documented in project decisions when materially relevant. A project exception must not alter this global standard.

## Verification

Review adherence to this standard with questions such as:

```text
Can this test run independently?

Does execution order affect its result?

Is required state controlled?

Does the test contain meaningful validation?

Can we understand what behavior the test protects?

Would a failure provide useful diagnostic information?

Does the test rely on arbitrary waiting?

Is shared mutable state introducing unnecessary risk?

Is unnecessary abstraction making the test harder to understand?

Are failures being hidden, ignored, or masked?

Could created state affect later executions?

Are relevant environment assumptions explicit?

Does the automation expose sensitive information unnecessarily?
```

These questions support review of the standard; they do not create a separate quality gate.

## Related

- [[Automation Philosophy]]
- [[Test Design Standard]]
- [[Standards]]
- [[Quality Gates]]
- [[Adapters]]
- [[Client Data Handling Policy]]
- [[Credentials and Secrets Policy]]
