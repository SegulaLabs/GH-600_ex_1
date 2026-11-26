---
name: update-github-info

on:
  schedule: daily
  workflow_dispatch:

permissions:
  contents: read
  copilot-requests: write

engine:
  id: copilot
  copilot-sdk: true

tools:
  edit:
  web-fetch:

network:
  allowed:
    - defaults
    - copilot
    - awesome-copilot.github.com
    - github.blog
    - github.com

safe-outputs:
  create-pull-request:
    reviewers: [mona]
    draft: false
    if-no-changes: ignore
---

# Update GitHub information

Read `notes/mona-notes.md` and the current `site/content/github-info.md`.
Use the `web_fetch` tool to review:

- https://github.blog/latest/
- https://github.blog/changelog/
- https://awesome-copilot.github.com/workflows/

Choose recent, relevant updates that help developers learn GitHub faster. Update
`site/content/github-info.md` with short, practical summaries, citing the
original GitHub Blog or Changelog source for each update. Follow Mona's notes
and avoid duplicating information already covered in the file.

If there is no useful new information, make no changes. Otherwise, propose only
the update to `site/content/github-info.md` in a pull request and request review
from Mona. Do not write directly to the default branch.
