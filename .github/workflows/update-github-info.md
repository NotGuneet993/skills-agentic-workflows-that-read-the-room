---
name: update-github-info
description: Draft a concise GitHub Info update from Mona's notes and the GitHub Blog/Changelog, then propose the change as a reviewed PR.
on:
  workflow_dispatch:
  schedule:
    - cron: '17 9 * * *'
permissions:
  contents: read
tools:
  edit:
  web-fetch:
network:
  allowed:
    - github.com
    - github.blog
safe-outputs:
  create-pull-request:
    title-prefix: "[mona] "
    draft: true
    fallback-as-issue: false
---

# Update Mona's GitHub Info website

Read `notes/mona-notes.md` before drafting updates.

Use the official public guidance and repository references to inform your writing:
- Read external public guidance with `web-fetch`, especially:
  - https://github.blog/latest/
  - https://github.blog/changelog/
- Read repository guidance or reference files with GitHub repository API tools instead of terminal, CLI, or sandboxed commands.
- Check the syntax of this workflow configuration to confirm it is valid before you begin.
- Do not compile the workflow; only prepare the markdown workflow and the reviewable pull request.

Update `site/content/github-info.md` with short, practical improvements that help developers learn GitHub faster. When a fact or insight comes from the GitHub Blog or GitHub Changelog, call out the source clearly.

Open a pull request for Mona to review. Do not write directly to `main`; rely on `safe-outputs` with `create-pull-request` so the change is proposed for review rather than pushed directly.

Keep the change concise and review-friendly, and include a PR title that makes the Mona GitHub Info update easy to review.
