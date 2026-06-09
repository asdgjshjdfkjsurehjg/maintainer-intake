# Security Model

Maintainer Intake is a metadata and policy checker. It does not execute contributor code.

Boundaries:

- No checkout of contributor branches is required.
- pull_request_target handling is metadata/API-only.
- No shell commands are built from issue or pull request text.
- Fixture mode requires no token.
- GitHub writes are constrained to comments, configured labels, and check runs from explicit write plans.
- Security-sensitive issue body content is not echoed into public artifacts.
- Tokens and authorization headers must not be logged.

The security verification lane scans workflows and Action source for privileged checkout or contributor-code execution patterns.
