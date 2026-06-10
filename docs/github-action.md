# GitHub Action

The Action runs on Node 24 and uses GitHub APIs for metadata, issue, pull request, comment, label, and check behavior. It does not check out or execute contributor code.

Minimal workflow:

    name: Maintainer Intake
    on:
      pull_request_target:
        types: [opened, edited, reopened, synchronize, ready_for_review]
      issues:
        types: [opened, edited, reopened]
    permissions:
      contents: read
      pull-requests: write
      issues: write
      checks: write
    jobs:
      intake:
        runs-on: ubuntu-latest
        steps:
          - uses: asdgjshjdfkjsurehjg/maintainer-intake@v0
            with:
              mode: advisory
              config: .github/maintainer-intake.yml

Start with advisory mode. Move to check, label, or gate only after the packet matches project policy.

Inputs:

- `config`: config path; defaults to `.github/maintainer-intake.yml`.
- `mode`: optional `advisory`, `check`, `label`, or `gate` override.
- `token`: GitHub token for API reads and enabled writes.
- `comment`: create or update the marked intake comment; defaults to `true`.
- `labels`: apply configured labels; defaults to `false`.
- `check-name`: check-run name; defaults to `Maintainer Intake`.

Outputs:

- `status`: deterministic intake status.
- `score`: score from 0 to 100.
- `result-json`: serialized intake result.
- `packet-summary`: one-line maintainer summary.

Supported events are `pull_request`, `pull_request_target`, and `issues`. Other events return `unsupported_event` with score `0` and do not perform writes.

Rollback:

1. Remove the workflow.
2. Remove tool-owned labels if desired.
3. Delete the marked Maintainer Intake comment if desired.
4. Remove .github/maintainer-intake.yml.
