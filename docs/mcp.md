# MCP

Run the stdio server:

    maintainer-intake mcp

Tools:

- analyze_pr_intake
- analyze_issue_intake
- render_maintainer_packet
- generate_policy_files
- explain_intake_config

Fixture example:

    {
      "fixturePath": "fixtures/github/pr-ready.json",
      "format": "json"
    }

Live GitHub references use OWNER/REPO#NUMBER and require GITHUB_TOKEN or GH_TOKEN. MCP diagnostics go to stderr; stdout is reserved for protocol messages.
