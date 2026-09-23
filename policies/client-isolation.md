# Client Isolation Policy

## Purpose

This policy ensures logical and operational isolation between consultancy clients. QAOS must support reusable methodology without enabling inappropriate reuse of client-specific information.

## Policy

Each client engagement must operate within its own isolated workspace.

Client-specific information must never be intentionally transferred from one client workspace to another.

Reusable consultancy knowledge must pass through sanitization and generalization before being incorporated into the main QAOS.

## Scope

This policy applies to Codex sessions, IDE workspaces, terminal sessions, QAOS agents, skills, generated documentation, analysis artifacts, client source code, learnings, and local project files.

## Requirements

**Workspace boundary.** An agent or operator must work from the root of one client workspace, for example `clients/company-a/`. They must not normally operate from a root containing multiple clients, such as `clients/`, where `company-a/`, `company-b/`, and `company-c/` are simultaneously available. This prevents a session from accessing multiple client contexts without operational need.

**Codex execution.** When Codex is used for a client, the session must start at that client's workspace root and use that workspace's `os/`, `project/`, `work/`, and `learnings/`. It must not deliberately navigate to other client directories or use another client's data as context.

**Client repository isolation.** The following structure must remain outside the client's Git repository:

```text
client-workspace/
├── os/
├── project/
├── work/
└── learnings/
```

Only content under `project/` that belongs to the client repository may be versioned in that repository. The QAOS copy must never be committed to the client's repository. The same applies to `work/` and `learnings/`, unless an explicit decision makes a specific artifact an official client deliverable.

**QAOS isolation.** The main QAOS must not contain client names, private internal system names, private endpoints, credentials, secrets, tokens, real data, confidential business rules, proprietary client code, identifiable proprietary architecture, contractual information, or other internal information that can identify a client.

**Learnings.** Learnings discovered in a project must initially remain in that client's workspace. Before incorporation into the main QAOS, they must be reviewed, sanitized, generalized, checked for client-specific information, and intentionally promoted. No process may promote learnings automatically to the main QAOS.

**Work artifacts.** Files in `work/` are client-specific by default and must not be used as a knowledge source for another client. A reusable conclusion must first be extracted as a learning and follow the required promotion process.

**Agent behavior.** Agents must interpret workspace contents as follows:

```text
os/
= reusable consultancy methodology

project/
= client source of truth

work/
= client-specific working knowledge

learnings/
= candidate reusable knowledge still associated with this engagement
```

Agents must not infer that information in `work/` or `project/` is reusable for other clients.

## Prohibited actions

- Deliberately opening multiple client workspaces in the same working session when not necessary.
- Copying data from one client to another.
- Using one client's proprietary code as an example for another client.
- Moving artifacts from `work/` directly to the main QAOS.
- Moving learnings directly to principles, standards, patterns, or playbooks without review.
- Versioning the QAOS copy inside a client's repository.
- Storing credentials or secrets in QAOS.
- Assuming that client-specific knowledge is general consultancy knowledge.

## Exceptions

Exceptions must be rare and explicit. An exception may exist only when there is a legitimate operational need, it does not violate a contract, NDA, or confidentiality obligation, its scope is clearly defined, the decision is documented, and access is limited to the minimum necessary.

For example, a specific artifact in `work/` may be deliberately delivered to the client through `project/` or another official delivery channel. This does not make all of `work/` part of the project.

No exception may permit information sharing between clients.

[[Policies]] · [[Learnings]] · [[Decisions]]
