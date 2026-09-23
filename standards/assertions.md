# Assertions Standard

## Rule

Assertions must verify the behavior or outcome that gives a test its purpose and must provide meaningful evidence when that expectation is not met.

## Rationale

Assertions transform test execution into validation. Executing steps is not sufficient, and the absence of an error does not by itself prove that behavior is correct. Weak assertions can create false confidence, while assertions coupled excessively to implementation details can make tests fragile. Meaningful failures support diagnosis and useful feedback.

```text
test-design.md
= defines what behavior and outcome should be tested

assertions.md
= defines how the expected outcome must be meaningfully validated

automation-code.md
= engineering quality of automated implementation

assertions.md
= quality of the validation performed by the test
```

Assertions validate the expected outcome; they must not redefine the scenario designed under the Test Design Standard.

## Requirements

**Purpose-aligned validation.** Assertions must validate the behavior, rule, state, or outcome that justifies the existence of the test. Tests should avoid assertions that validate only secondary details while ignoring the primary objective.

**Observable evidence.** Whenever possible, assertions should validate observable outcomes relevant to the tested behavior. Appropriate observability depends on the test level and context; this standard does not prescribe a universal observation mechanism.

**Absence of error is not enough.** A test must not be considered valid solely because execution completed without an error when an expected outcome can be verified. An exception may be appropriate when the explicit purpose of the test is to verify the absence of failure under a defined condition.

**Relevant assertions.** Assertions must be relevant to the scenario. Tests must not add validations unrelated to the behavior under test merely to increase the number of checks.

**Sufficient confidence.** Assertions should provide enough evidence to support the intended conclusion of the test. This standard does not establish a minimum number of assertions.

**Failure clarity.** When an assertion fails, the failure should make it reasonably clear what was expected, what was observed, and which relevant behavior failed. The specific form of failure information depends on the stack and framework.

**Stable expectations.** Assertions should avoid unnecessary dependence on volatile or irrelevant details, such as presentation details unrelated to the behavior, unstable identifiers, incidental ordering, or transient implementation details. These examples are contextual considerations, not universal prohibitions.

**Exactness proportional to intent.** Assertions must be precise enough to validate the intended behavior without becoming unnecessarily brittle. They must avoid both vague expectations and excessive specificity without relevant purpose.

**Multiple assertions.** Multiple assertions in one test may be valid when they collectively validate one coherent behavior or outcome. Tests should avoid grouping validations of independent behaviors merely to reduce the number of tests.

**Negative assertions.** Negative assertions should be used when absence, rejection, or prevention is part of the expected behavior. They should avoid broad conditions that can pass for reasons unrelated to the behavior being evaluated.

**State validation.** When behavior changes state, assertions should validate the relevant resulting state when that state is part of the expected outcome. Tests are not required to validate every internal state of the system.

**Error validation.** When a scenario expects failure, rejection, or error behavior, assertions must validate the relevant outcome rather than merely provoke the failure. When applicable, this may include the error type, user feedback, status, state preservation, or returned information. No specific format is required.

**Side effects.** When side effects are part of the intended behavior, they should be validated at an appropriate level. Relevant effects may include persistence, message publication, file creation, downstream state, or notification. Tests are not required to validate every possible side effect.

**Avoid implementation-only validation.** Assertions should not validate internal implementation details unless those details are intentionally part of the contract or the chosen test level requires them.

Technology-specific assertion libraries, matcher mechanisms, polling behavior, failure output, and other framework-dependent validation details belong in `adapters/`. No such approach is universally required by this standard.

## Allowed exceptions

Exceptions may be appropriate when observability is limited, legacy systems expose only indirect evidence, third-party dependencies restrict validation, the test intentionally targets internal implementation behavior, or the expected behavior is specifically no failure under a defined condition.

Relevant exceptions must be understood and, when materially important, documented in the project context. A local exception must not alter this global standard.

## Verification

Review adherence to this standard with questions such as:

```text
Does this assertion validate the actual purpose of the test?

Would the test still pass if the intended behavior were broken?

Is execution success being mistaken for behavior validation?

Are the expectations observable and meaningful?

Are assertions validating irrelevant or volatile details?

Is the assertion precise enough without being unnecessarily brittle?

Would a failure provide useful information?

Are multiple assertions validating one coherent behavior?

If failure is expected, is the failure outcome itself validated?

If state or side effects matter, are the relevant ones verified?
```

These questions support review of the standard; they do not create a separate quality gate.

## Related

- [[Quality Philosophy]]
- [[Automation Philosophy]]
- [[Test Design Standard]]
- [[Automation Code Standard]]
- [[Test Data Standard]]
- [[Standards]]
- [[Adapters]]
- [[Quality Gates]]
