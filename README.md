# QAOS

QAOS is a Quality Engineering Operating System for reusing consulting methodology, knowledge, and practices across different projects.

## Purpose

QAOS exists to:

- preserve consulting knowledge;
- standardize principles and practices;
- enable consistent execution with agent assistance;
- adapt the method to different stacks without coupling its core to specific technologies;
- learn from real projects without mixing information between clients.

## Core concepts

The operating system is organized into principles, standards, policies, quality gates, patterns, anti-patterns, skills, agents, playbooks, adapters, templates, metrics, references, knowledge, learnings, and decisions.

## Architecture

```text
QAOS
= consulting methodology

Client workspace
= isolated environment for an engagement

Project
= source of truth for client software

Work
= client-specific artifacts and knowledge

Learnings
= potentially reusable learnings
```

Only `project/` belongs to the client's Git repository. QAOS must not be versioned inside a client project.

## Tooling

QAOS is designed to work with:

- Git
- Codex
- Obsidian
- Markdown-compatible editors

> Markdown is the source of truth. QAOS must not depend on Obsidian to function.

## Status

Current version: `0.1.0-dev`.

The project is under construction.
