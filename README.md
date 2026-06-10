# Maintainer Intake

Deterministic contribution-intake checks for open-source maintainers.

Maintainer Intake validates whether an issue or pull request contains the evidence a maintainer needs before review time is spent. It checks repository policy, templates, scope, tests, risky paths, and security-sensitive reports, then produces a concise packet for comments, checks, labels, gates, CLI use, or MCP clients.

It does not detect authorship. It evaluates evidence and accountability.

## Install

Run without installing globally:

    npx --yes maintainer-intake@0.1.1 --version
    npx --yes maintainer-intake@0.1.1 init

Or install the CLI globally:

    npm install --global maintainer-intake@0.1.1

## 60-second fixture demo

    npm ci
    npm run build
    node dist/cli/index.js analyze-pr --fixture fixtures/github/pr-ready.json --format markdown
    node dist/cli/index.js analyze-pr --fixture fixtures/github/pr-unready.json --format json

## CLI

    maintainer-intake init
    maintainer-intake init --write
    maintainer-intake policy doctor --config .github/maintainer-intake.yml
    maintainer-intake analyze-pr --fixture fixtures/github/pr-ready.json --format json
    maintainer-intake analyze-issue --fixture fixtures/github/issue-bug-ready.json --format markdown

Live GitHub reads use OWNER/REPO#NUMBER and require GITHUB_TOKEN or GH_TOKEN.

## GitHub Action

Use the Action in advisory mode first:

    - uses: asdgjshjdfkjsurehjg/maintainer-intake@v0
      with:
        mode: advisory

See docs/github-action.md for the complete workflow, permissions, modes, outputs, rollback, and safe event guidance.

## MCP

Run the stdio MCP server with:

    maintainer-intake mcp

The MCP server exposes analyze_pr_intake, analyze_issue_intake, render_maintainer_packet, generate_policy_files, and explain_intake_config.

See docs/mcp.md for an `npx`-based MCP client configuration.

## Statuses And Modes

Statuses:

- ready_for_review
- needs_author_evidence
- needs_maintainer_decision
- reject_recommended

Modes:

- advisory: never fails because evidence is missing.
- check: emits check-run intent.
- label: emits configured label intent.
- gate: fails only when required evidence is missing.

## Verification

The full local lane is:

    npm run verify

The package and Action release gates include bundle rebuild, tarball audit, packed install, security scan, and fixture E2E.

## License

MIT
