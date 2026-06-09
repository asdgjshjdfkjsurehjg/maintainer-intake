# Rule Reference

Rules are deterministic and versioned by stable IDs.

## Pull Requests

| ID                   | Behavior                                                                  |
| -------------------- | ------------------------------------------------------------------------- |
| MI-PR-TEMPLATE       | Requires configured PR template sections.                                 |
| MI-PR-LINKED-ISSUE   | Requires linked issue or documented exemption when configured.            |
| MI-PR-SCOPE          | Requires scope, intent, or non-goal language.                             |
| MI-PR-TEST-EVIDENCE  | Requires exact test commands or justified exemption.                      |
| MI-PR-BEHAVIOR-TESTS | Requires behavior-change test evidence when applicable.                   |
| MI-PR-LARGE-CHANGE   | Flags large changes and requires a review plan.                           |
| MI-PR-RISKY-PATH     | Requires configured evidence for risky paths.                             |
| MI-PR-CI-WEAKENING   | Warns on workflow, CI, or test weakening indicators.                      |
| MI-PR-GENERATED-ACK  | Requires accountability acknowledgement when configured.                  |
| MI-PR-CLASSIFICATION | Classifies docs-only, dependency-only, formatting-only, or mixed changes. |

## Issues

| ID                            | Behavior                                                                                                      |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------- |
| MI-ISSUE-CLASSIFICATION       | Classifies bug, feature, security-sensitive, or unknown issues.                                               |
| MI-ISSUE-BUG-EVIDENCE         | Requires reproduction, expected behavior, and actual behavior for bugs.                                       |
| MI-ISSUE-FEATURE-EVIDENCE     | Requires use case and non-goals for features.                                                                 |
| MI-ISSUE-SECURITY-ROUTING     | Redirects security-sensitive reports to private reporting guidance and avoids echoing sensitive body content. |
| MI-ISSUE-DUPLICATE-CANDIDATES | Treats duplicate lookup as advisory when enabled.                                                             |

## Status Precedence

Errors require maintainer decision. Security-sensitive routing may produce reject_recommended. Blocking or high evidence failures produce needs_author_evidence. Warnings produce needs_maintainer_decision. Otherwise the contribution is ready_for_review.
