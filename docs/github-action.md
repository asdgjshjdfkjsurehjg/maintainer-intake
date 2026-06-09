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

Rollback:

1. Remove the workflow.
2. Remove tool-owned labels if desired.
3. Delete the marked Maintainer Intake comment if desired.
4. Remove .github/maintainer-intake.yml.
