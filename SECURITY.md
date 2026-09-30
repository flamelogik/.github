# Security Policy

Community tools run inside Flame, on artists' workstations, alongside client work. We take security reports seriously.

## Reporting a vulnerability

**Please don't open a public issue.** Instead, go to the affected repo's **Security** tab and choose **Report a vulnerability**. This opens a private advisory that only the repo's maintainers and the org owners can see.

Examples of what to report:
- code that exposes credentials, tokens or file paths it shouldn't
- scripts that run untrusted input (for example, `eval` on file contents or unchecked shell commands)
- a published release binary that doesn't match its source, or behaves unexpectedly
- dependencies with known vulnerabilities

## What happens next

These are volunteer projects, so response times are best effort, but we aim to:
- acknowledge your report within **7 days**
- work with you on a fix inside the private advisory
- release the fix and publish the advisory, crediting you unless you prefer not to be named

If you think a published binary is **malicious**, say so clearly in the report. Owners will pull the release immediately while they investigate.
