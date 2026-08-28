---
name: Weekly Report Status
engine: copilot
on:
  schedule:
    - cron: "0 9 * * 1"
  workflow_dispatch:
permissions:
  contents: read
  issues: read
  pull-requests: read
  copilot-requests: write
tools:
  github:
    mode: gh-proxy
safe-outputs:
  create-issue:
    title-prefix: "[weekly-report] "
    max: 1
---

Create one concise weekly activity report for this repository and publish it as a new GitHub issue using the configured `create-issue` safe output.

Use the previous seven full days ending at workflow start in UTC as the reporting window. Review GitHub activity in that window, covering:

- Commits, including the total and a brief summary of notable changes.
- Issues opened or updated, including titles and links where useful.
- Pull requests opened, updated, or merged, including titles and links where useful.

Keep the report concise and organize it with `###` headings for Overview, Commits, Issues, and Pull Requests. Clearly state the UTC reporting window. If there was no activity of any kind, explicitly state: "No activity occurred during this reporting window." Still publish the issue. Do not make any changes other than creating this report issue.
