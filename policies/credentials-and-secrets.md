# Credentials and Secrets Policy

## Purpose

This policy prevents information capable of granting access to systems, environments, or data from being stored, shared, or exposed inappropriately. Credentials and secrets require more restrictive handling than ordinary client data.

## Policy

Secrets must never be stored directly in QAOS documentation, reusable knowledge, or source-controlled files.

Credentials must be accessed only when required for the current task and through an approved mechanism whenever one is available.

Secrets must never become reusable QAOS knowledge.

Access to a credential does not authorize copying, documenting, or redistributing it.

## Scope

This policy applies to local development, test, staging, and production environments; CI/CD; API authentication; databases; cloud services; mobile signing; certificates; package registries; repositories; third-party integrations; test accounts; service accounts; environment variables; generated artifacts; scripts; and automation frameworks.

## What is considered a secret

Secrets include passwords, API keys, access tokens, refresh tokens, session tokens, private keys, SSH keys, certificates containing private material, database credentials, connection strings containing credentials, client secrets, signing keys, service account credentials, webhook secrets, authentication cookies, recovery codes, and encryption keys.

This list is not exhaustive. Any information capable of granting or facilitating unauthorized access must be treated as a secret.

## Requirements

**Minimum access.** Use only credentials necessary for the current task. Avoid privileged access when a lower-privilege credential is sufficient.

**Environment separation.** Credentials for separate environments must remain separate:

```text
development
testing
staging
production
```

Production credentials must not be reused in test automation when an appropriate alternative exists.

**Temporary exposure.** When a secret must be viewed for diagnosis or configuration, minimize exposure, do not copy it unnecessarily, avoid leaving it in screenshots or recordings, remove temporary copies after use, and do not include it in reports.

## Storage

Secrets should be stored through appropriate mechanisms, such as environment variables, approved secret managers, CI/CD secret storage, operating-system credential stores, or client-approved secure storage. No specific provider is required.

Files such as `.env`, `.env.local`, and `.env.test` may be used when appropriate to the project, but they must remain outside version control, must not be used as a knowledge base, and must not be copied to the main QAOS.

## Source code and automation

Automated tests and support scripts must not hardcode credentials or secrets.

When automation requires authentication, obtain values through an external mechanism, keep code and secrets separate, avoid secrets in versioned fixtures, and avoid real credentials when controlled test accounts are sufficient.

Configuration may reference variable names such as `API_TOKEN`, `DATABASE_PASSWORD`, or `TEST_USER_PASSWORD`, but must not contain their real values.

## Logs, evidence and documentation

Secrets may appear accidentally in logs, stack traces, screenshots, videos, HTTP dumps, request and response captures, console output, CI output, and bug reports.

Before preserving or sharing these materials, inspect for secrets, redact sensitive values, remove unnecessary authentication headers, and avoid preserving complete tokens.

```text
Authorization: Bearer [REDACTED]
password=[REDACTED]
```

## Tool and agent behavior

Codex and other agents must avoid printing secrets unnecessarily, copying them into Markdown, moving them from `project/` into `work/`, including them in learnings or generated examples, and must use placeholders when documenting configuration. They must flag suspected secrets discovered in version-controlled files.

When an agent identifies a possible versioned secret, it must:

1. Avoid reproducing the secret in full.
2. Identify the affected location safely.
3. Report the risk.
4. Recommend removal from source control.
5. Recommend credential rotation when exposure may have occurred.

Agents must not rotate or otherwise modify credentials automatically.

## Rotation and exposure

When exposure is suspected, the secret should be considered potentially compromised, its owner or responsible party should be informed, rotation should be considered, copies should be removed where appropriate, and repository history may require review if the secret was committed.

Credential rotation and any history remediation remain under human or client control and must not be automated by agents.

## Prohibited actions

- Hardcoding secrets in source code.
- Storing secrets in QAOS Markdown, `learnings/`, `knowledge/`, or `templates/`.
- Including real credentials in examples.
- Committing `.env` files containing secrets.
- Copying credentials between clients.
- Reusing one client's accounts in another engagement.
- Publishing credentials in screenshots or reports.
- Exposing complete tokens in logs when redaction is possible.
- Converting credentials into reusable documentation.
- Asking agents to preserve credentials for future reference.

## Exceptions

Exceptions must be extremely restricted. They may exist only when technically necessary, explicitly authorized, scoped to the minimum required access, compliant with client-specific requirements, and temporary where possible.

Even under an exception, secrets must not enter the main QAOS, become learnings, or be reused across clients.

## Related

- [[Client Isolation Policy]]
- [[Client Data Handling Policy]]
- [[Policies]]
- [[Decisions]]
