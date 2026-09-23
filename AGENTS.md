# QAOS Agent Map

## Identity

This repository contains QAOS, the reusable Quality Engineering methodology of the consultancy.

## Source of truth

Markdown files in this repository are the source of truth.

## Knowledge map

```text
principles/
→ Quality Engineering philosophy

standards/
→ objective technical rules

policies/
→ governance and security

quality-gates/
→ mandatory completion criteria

patterns/
→ proven solutions

anti-patterns/
→ demonstrably problematic approaches

skills/
→ focused procedures for specific tasks

agents/
→ specialized roles that use skills

playbooks/
→ guidance for recurring situations

adapters/
→ translation of the method for specific stacks

templates/
→ reusable artifact structures

metrics/
→ metric definition and interpretation

references/
→ official and authoritative sources

knowledge/
→ research, external sources, and syntheses

learnings/
→ generalized practical knowledge that is still maturing

decisions/
→ relevant decisions about QAOS architecture and method
```

## Operating principles

1. Do not invent normative content without support in QAOS.
2. Clearly distinguish established knowledge from a hypothesis or suggestion.
3. Do not automatically promote a learning to a standard or pattern.
4. Do not treat content in `knowledge/` as a mandatory rule.
5. Do not change principles, standards, policies, or quality gates incidentally during another task.
6. Structural or normative changes must be explicit.
7. Keep client-specific knowledge outside the main QAOS repository.
8. Do not store credentials, secrets, or sensitive client data in QAOS.
9. Prefer reusing existing content before creating duplicate concepts.
10. Preserve the separation between method, execution, and knowledge.

## Scope discipline

Agents and skills must respect their defined scope and must not assume responsibilities outside it without explicit need.

## Changes

Document significant changes to the QAOS model or decisions in `decisions/` when justified.
