# Naming Standard

## Rule

Names must communicate intent and responsibility clearly enough to be understood without unnecessary inspection of implementation details.

## Rationale

Clear naming reduces ambiguity, supports maintenance and review, improves diagnosis, makes tests more understandable, and preserves context over time. Names should communicate meaning rather than satisfy an aesthetic convention alone.

```text
test-design.md
= defines the behavior and purpose of the test

naming.md
= ensures that purpose is communicated clearly through names

automation-code.md
= defines maintainable automated implementation

naming.md
= supports readability and responsibility clarity within that implementation
```

## Requirements

**Intent over mechanics.** Names must describe purpose or behavior rather than merely the mechanics used to implement it. For example, `clickButtonTest` communicates little about intended behavior, while `rejects_submission_when_required_data_is_missing` communicates a relevant outcome. These examples are illustrative only and do not establish a universal naming style.

**Behavior-oriented test names.** Test names should communicate the condition or context when relevant, the action or behavior, and the expected outcome. This standard does not require a rigid test-name format.

**Domain language.** When describing business behavior, names should prefer terminology used by the product or domain. Tests should avoid replacing clear business concepts with unnecessary technical terms.

**Avoid generic names.** Names such as `test1`, `test2`, `scenarioA`, `validationTest`, `basicTest`, `happyPath`, `helper`, `utils2`, and `temp` must not be used when a meaningful name can reasonably be provided. Terms such as `helper` or `utils` are not universally prohibited; the concern is a missing or unclear responsibility.

**Stable meaning.** Names should represent concepts expected to remain meaningful when implementation details change. They should avoid embedding volatile details unless those details are relevant to the contract being tested.

**Responsibility clarity.** Functions, helpers, fixtures, modules, and reusable components should have names that communicate their primary responsibility. Names should avoid accumulating unrelated responsibilities under broad concepts.

**Consistency within context.** Naming should remain consistent within the same project or component. When an established project convention exists and does not conflict with QAOS standards, it should be followed rather than introducing unnecessary variation.

**Abbreviations.** Names should avoid ambiguous or undocumented abbreviations. Widely understood abbreviations within the relevant technical or business context may be used. This standard does not create a universal abbreviation blacklist.

**Boolean meaning.** Names for boolean concepts should make their true and false meanings understandable. They should avoid ambiguous concepts where a reader cannot readily determine what `true` represents. This standard does not prescribe language-specific prefixes.

**Negative naming.** Names should avoid unnecessarily complex negative or double-negative wording. Expected meaning should remain straightforward.

**Test data naming.** When named test data is used, its name should communicate the role of the data in the scenario. Semantic concepts should be preferred over arbitrary identifiers when they improve comprehension.

**Artifact naming.** Documents, reports, decisions, learnings, and other QAOS artifacts should use names that communicate their subject. Within the QAOS repository, filenames must use the repository convention:

```text
lowercase-kebab-case
```

Examples include `automation-code.md`, `risk-oriented-quality.md`, and `client-data-handling.md`. This convention applies to QAOS files and directories only; it must not automatically be imposed on client source repositories.

**No unnecessary metadata in names.** Names should avoid information that belongs more appropriately in metadata, version control, properties, or project context. This may include authorship, temporary status, or dates unless they are intentionally part of an artifact convention.

Technology-specific conventions and required identifiers belong in the relevant project context or `adapters/`. This includes language conventions, framework naming requirements, and other stack-dependent practices.

## Allowed exceptions

Exceptions may be appropriate when a language has established conventions, a framework requires a specific name, a protocol or specification defines terminology, compatibility requires preserving existing names, a legacy project has an established convention, or external systems impose identifiers.

Existing technical conventions should normally be respected when they do not create material ambiguity or conflict with QAOS principles. Teams should not force broad renames solely for aesthetic consistency.

## Verification

Review adherence to this standard with questions such as:

```text
Can the purpose be understood from the name?

Does the name describe behavior or responsibility rather than implementation mechanics?

Does it use domain terminology where appropriate?

Would the name remain meaningful after a reasonable implementation refactor?

Is the name unnecessarily generic?

Does it contain an ambiguous abbreviation?

Is there unnecessary negative or double-negative wording?

Does it conflict with established project conventions without a good reason?

Would another engineer understand why this test or component exists from its name?
```

These questions support review of the standard; they do not create a separate quality gate.

## Related

- [[Quality Philosophy]]
- [[Automation Philosophy]]
- [[Test Design Standard]]
- [[Automation Code Standard]]
- [[Assertions Standard]]
- [[Standards]]
- [[Adapters]]
