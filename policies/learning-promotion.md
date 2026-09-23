# Learning Promotion Policy

## Purpose

This policy enables QAOS to evolve from practical experience without compromising client isolation or turning isolated observations into premature rules.

## Policy

Client learnings must remain client-scoped until they have been intentionally reviewed for reuse.

No client learning may be promoted directly into the main QAOS without sanitization and generalization.

Promotion must be intentional and reviewable.

A learning does not become a standard, pattern, or policy merely because it was observed once.

Practical experience may inform QAOS, but maturity and evidence must determine its destination.

## Scope

This policy applies to learnings derived from automation implementation, test design, project discovery, architecture assessment, tooling, CI/CD, debugging, flaky test investigation, mobile testing, API testing, performance testing, process improvement, documentation, failed and successful approaches, project constraints, and consultancy execution.

## Learning lifecycle

**Client candidate.** A learning begins in `client-workspace/learnings/` and may still contain engagement-specific context. Its conceptual status is `candidate`.

**Reviewed client learning.** The learning has been assessed for value beyond the original project. It may remain too specific and never leave the client workspace.

**Sanitized and generalized.** Identifying or proprietary information has been removed, and the learning has been rewritten independently of the client.

**QAOS learning.** The learning is accepted in `qaos/learnings/` as reusable practical knowledge that is still maturing.

**Matured.** With additional evidence, the learning may later contribute to another QAOS component. A learning is not required to reach this stage.

```text
project experience
      ↓
client learning
      ↓
review
      ↓
sanitization
      ↓
generalization
      ↓
promotion decision
      ↓
qaos/learning
```

## Promotion criteria

A learning is a promotion candidate only when it may apply to more than one project, reveals a recurring risk, identifies a reusable technique, captures a failure mode worth avoiding, improves existing QAOS practice, exposes a gap in guidance, provides evidence for or against a pattern, or may improve a skill, adapter, playbook, or quality gate.

Review the following questions:

```text
Is this useful outside the original engagement?
Is this still meaningful without client-specific context?
Can it be explained without proprietary information?
Does it add something not already captured by the QAOS?
```

If a relevant answer is no, the learning must remain only in the client workspace.

## Sanitization

Before promotion, remove or replace client names, product and employee names, internal system and identifying repository names, private URLs and endpoints, credentials and tokens, screenshots and logs, proprietary source code, real data, confidential business rules, internal identifiers, ticket IDs, identifying environment details, and unique confidential architecture details.

Sanitization must not be superficial. Replacing only a company name with `Client A` is insufficient when the remaining content can still identify the client.

## Generalization

After sanitization, rewrite the learning as reusable knowledge. For example:

```text
In a specific client system, an inspection synchronization endpoint failed when...
```

becomes:

```text
Long-running offline workflows should be tested separately for local persistence, reconnection, synchronization, and conflict handling.
```

A promoted learning must explain what was learned, why it matters, where it may apply, relevant limitations, and its practical basis when appropriate. It must not turn a specific context into a universal rule.

## Promotion targets

The default first destination for generalized practical learning is `qaos/learnings/`. Do not promote directly to a more mature category without sufficient justification.

- **Pattern:** a solution is recurrently successful and validated.
- **Anti-pattern:** an approach recurrently produces problems.
- **Standard:** evidence and method justify an objective, verifiable technical rule; this has a higher bar than a learning or pattern.
- **Skill:** the learning improves execution of a specific task.
- **Playbook:** the learning improves response to a recurring consultancy situation.
- **Adapter:** the learning is specific to a technology, framework, or stack.
- **Quality gate:** the learning reveals a verifiable criterion before activity completion.
- **Knowledge synthesis:** the learning contributes to a broader conclusion with research or other evidence.

No single destination is mandatory.

## Review and approval

No promotion may be automatic. The process must include:

1. Review of the original learning.
2. Sanitization check.
3. Generalization check.
4. Duplication check against existing QAOS knowledge.
5. Destination decision.
6. Explicit approval before modifying the main QAOS.

Agents may identify candidates, propose sanitization and generalization, suggest destinations, detect duplication, and produce promotion proposals. They must not promote automatically, modify principles, standards, policies, or quality gates solely because a learning exists, or assume repeated wording means repeated evidence.

Human approval is required for promotion into normative QAOS components.

## Traceability

Retain enough context to explain acceptance without preserving identifiable client information. When appropriate, a QAOS learning may state:

```text
Origin:
Observed during practical consultancy work.
```

or:

```text
Evidence:
Observed in multiple project contexts.
```

Do not record client names in the main QAOS. Git and `decisions/` may preserve relevant method changes. No complex mandatory ID system is required.

## Prohibited actions

- Copying a client learning directly into the main QAOS without review.
- Preserving client names, proprietary code, screenshots, logs, private endpoints, credentials, or secrets in promoted learnings.
- Using one client's learning directly as guidance for another client before generalization.
- Promoting one observation directly into a global standard without sufficient justification.
- Automatically promoting content through scripts or agents.
- Treating superficial anonymization as sanitization.
- Creating duplicate QAOS knowledge when an existing component should be updated instead.

## Rejection and deferral

Not every learning should be promoted. A learning may be `promoted`, `deferred`, or `rejected`.

**Deferred** applies when the insight seems useful but evidence is weak, more project experience is desirable, or the destination is unclear.

**Rejected** applies when the learning is too client-specific, duplicates existing knowledge without value, lacks sufficient evidence, is not useful beyond the engagement, or loses useful meaning after sanitization.

Rejection does not require deletion of the original client learning; it may remain useful within its workspace.

## Related

- [[Client Isolation Policy]]
- [[Client Data Handling Policy]]
- [[Credentials and Secrets Policy]]
- [[Learnings]]
- [[Knowledge]]
- [[Patterns]]
- [[Anti Patterns]]
- [[Standards]]
- [[Decisions]]
