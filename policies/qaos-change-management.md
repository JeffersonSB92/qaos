# QAOS Change Management Policy

## Purpose

This policy ensures QAOS evolves deliberately, traceably, and consistently with its knowledge model. Evolution is expected and desirable; the policy prevents accidental, poorly classified, or incoherent changes rather than preventing change.

## Policy

Changes to the QAOS must be intentional, scoped, and consistent with the responsibility of the affected component.

Normative components must not be changed incidentally while performing unrelated work.

New knowledge must be classified before being incorporated into the QAOS.

Existing content should be updated when appropriate instead of creating unnecessary duplication.

Significant architectural or methodological decisions should be recorded when the rationale is important for future understanding.

## Scope

This policy applies to principles, standards, policies, quality gates, patterns, anti-patterns, skills, agents, playbooks, adapters, templates, metrics, references, knowledge, learnings, decisions, repository structure, and root guidance files such as `AGENTS.md`, `README.md`, and `HOME.md`.

## Change classes

### Normative

Changes that alter how QAOS must operate or what it considers mandatory. This includes principles, standards, policies, and quality gates. These changes require greater care.

### Operational

Changes that alter how tasks are executed or supported. This includes skills, agents, playbooks, adapters, templates, and metrics. They may affect practical execution without necessarily changing philosophy or global rules.

### Knowledge

Changes that add or refine non-normative information. This includes references, knowledge, learnings, patterns, and anti-patterns. Patterns and anti-patterns are validated reusable knowledge, but are not automatically mandatory rules.

## General requirements

Before a change:

1. Identify the target component.
2. Confirm that the change belongs to that component.
3. Check for existing related content.
4. Avoid duplication.
5. Identify related files that may become inconsistent.
6. Assess whether the change is normative, operational, or knowledge-oriented.

During a change, preserve terminology consistency and category boundaries, update related links when necessary, and avoid unnecessary scope expansion.

After a change, review affected relationships, ensure no contradictory guidance was introduced, and determine whether a decision record is needed.

## Normative changes

Changes in `principles/`, `standards/`, `policies/`, and `quality-gates/` must be explicit. State the reason, assess the impact on related components, verify whether adapters, skills, agents, or gates depend on the previous rule, and preserve consistency between standards and quality gates.

Record a decision when a change materially alters the method. A project-specific exception must not weaken a global QAOS rule; context-specific exceptions belong to project decisions.

## Structural changes

Changes to repository architecture or category design require care. Before adding a category, ask:

```text
Does an existing category already cover this need?
Will the new category reduce ambiguity or create more overlap?
Is there repeated real usage that justifies it?
```

Do not create directories merely because they may be useful in the future. A significant structural change should normally create a record in `decisions/`.

## Knowledge changes

Content in `references/`, `knowledge/`, `learnings/`, `patterns/`, and `anti-patterns/` may evolve more frequently. Source material must not be confused with QAOS conclusions. Learnings must follow the Learning Promotion Policy; a single source must not automatically create a standard, and a single project observation must not automatically create a pattern. Patterns require practical validation. Consolidate duplicated topics when practical.

## Review and approval

### Low-impact change

Typos, broken links, formatting, metadata corrections, and clarifications without meaning changes may be applied directly after verification.

### Method-impacting change

Changing a standard or policy, adding or removing a quality gate criterion, changing a principle or category boundary, or adding a mandatory requirement requires explicit review before completion. In the current QAOS context, that review is human.

Agents may propose and implement changes after explicit instruction, but must not autonomously decide that a normative change is necessary.

## Decision records

Use `decisions/` when it is important to retain rationale for adding a category, changing category meaning, adopting or rejecting a major method change, changing a principle, materially changing a standard or policy, or changing client isolation.

Do not create decisions for typos, formatting, minor wording, or trivial link corrections. Git remains the primary technical history; `decisions/` preserves why.

## Versioning

QAOS uses explicit versioning through `VERSION`. Version changes should be intentional, meaningful releases should update `VERSION`, and not every commit requires a version change. Development work may occur under a development version. Versioning should communicate meaningful method evolution.

Semantic versioning may be considered in the future but is not mandatory under this policy.

## Backward impact

Before changing existing content, assess whether client workspaces created from earlier versions may behave differently.

Existing client workspaces do not need to be automatically updated when the main QAOS changes. A QAOS copy in a client workspace represents the state used for that engagement until an update is deliberately performed.

## Prohibited actions

- Changing normative content incidentally during unrelated work.
- Automatically promoting learnings into standards.
- Changing principles based on one project.
- Creating duplicate concepts instead of reviewing existing content.
- Creating top-level categories without evaluating existing categories.
- Silently weakening quality gates because of project-specific constraints.
- Automatically updating every client workspace when the main QAOS repository changes.
- Altering `VERSION` for every small change.
- Using agents as autonomous authority for methodological changes.
- Deleting historical decisions merely because the method evolved.

## Exceptions

Urgent changes may be made when needed to correct unsafe guidance, a confidentiality risk, clearly incorrect normative guidance, or a serious inconsistency.

Even in these cases, the change must be reviewed as soon as practical, the rationale should be preserved when significant, and related content should be checked for consistency.

## Related

- [[Learning Promotion Policy]]
- [[Client Isolation Policy]]
- [[Policies]]
- [[Decisions]]
- [[Standards]]
- [[Quality Gates]]
- [[Learnings]]
