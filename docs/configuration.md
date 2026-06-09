# Configuration

Primary path: .github/maintainer-intake.yml

Generate defaults with:

    maintainer-intake init
    maintainer-intake init --write

Validate policy with:

    maintainer-intake policy doctor --config .github/maintainer-intake.yml

Default shape:

    version: 1
    mode: advisory
    pullRequests:
      requireLinkedIssue: true
      requireTestEvidence: true
      requireGeneratedAcknowledgement: false
      largeChangeThreshold: 500
      requiredSections:
        - Summary
        - Linked issue
        - Tests
        - Scope
      riskyPaths:
        - pattern: ".github/workflows/**"
          require:
            - security-impact
    issues:
      bug:
        require:
          - reproduction
          - expected-behavior
          - actual-behavior
      feature:
        require:
          - use-case
          - non-goals
      security:
        require:
          - affected-version
          - component
          - impact
          - reproduction
      duplicateSearch: false
    labels:
      ready: intake:ready
      needsEvidence: intake:needs-evidence
      maintainerDecision: intake:maintainer-decision

Unknown keys fail validation. The error includes the path so the policy can be repaired.
