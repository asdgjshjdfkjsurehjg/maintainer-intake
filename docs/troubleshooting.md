# Troubleshooting

## Config Errors

Run:

    maintainer-intake policy doctor --config .github/maintainer-intake.yml

Unknown keys and invalid values return exit code 2.

## Live GitHub Reads

Set GITHUB_TOKEN or GH_TOKEN. Provider or auth failures return exit code 3.

## Gate Mode

Gate mode returns nonzero only when required evidence is missing. Advisory mode reports the same packet without failing.

## Action Permissions

For comments, labels, and checks, grant only the permissions needed by the selected mode. If a permission is missing, preserve the analysis result and inspect the Action log for the write limitation.

## Unsupported Action Events

The Action supports `pull_request`, `pull_request_target`, and `issues`. Other events return status `unsupported_event`, score `0`, and no write actions. Change the workflow trigger rather than treating this as a policy failure.

## Rate Limits

Live duplicate and provider checks are advisory when unavailable. Fixture mode remains available without network credentials.
