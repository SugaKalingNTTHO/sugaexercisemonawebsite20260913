---
name: update-github-info
description: Keep the site's GitHub information page current from GitHub's public news.
on:
  schedule: daily
  workflow_dispatch:
engine: copilot
permissions:
  contents: read
tools:
  edit:
  web-fetch:
  github:
    toolsets: [repos]
network:
  allowed:
    - github.blog
    - github.com
    - awesome-copilot.github.com
safe-outputs:
  create-pull-request:
    max: 1
---

# Update GitHub information

Read `notes/mona-notes.md` to understand Mona's content and repository conventions.

Use the web-fetch tool to read both of these public sources:

- https://github.blog/latest/
- https://github.blog/changelog/
- https://awesome-copilot.github.com/workflows/

Also use the web-fetch tool to read the Awesome Copilot workflows source at https://awesome-copilot.github.com/workflows/.

Use GitHub repository API tools to read repository guidance or reference files when needed. Do not use terminal, CLI, or sandboxed commands for those repository reads.

Update `site/content/github-info.md` with accurate, concise information based on the sources. Preserve the existing format and make only relevant content changes. Review the resulting file for clarity and consistency.

When the update is complete, use the `create-pull-request` safe output to open a pull request for Mona to review. Summarize the sources and the changes in the pull request title and body. Do not write directly to `main`.