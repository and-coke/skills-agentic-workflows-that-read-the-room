---
emoji: 📝
name: Update GitHub Info
description: Update the GitHub info page from the latest GitHub Blog and Changelog posts.
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
strict: true
tools:
  edit: true
  web-fetch: {}
safe-outputs:
  create-pull-request:
    title-prefix: "[github-info] "
    draft: false
    allowed-files:
      - "site/content/github-info.md"
    protected-files: request_review
---

# Update GitHub Info

Read [notes/mona-notes.md](notes/mona-notes.md) before making any changes.

Fetch the latest updates from:

- https://github.blog/latest/
- https://github.blog/changelog/

Then update [site/content/github-info.md](site/content/github-info.md) with a short, practical summary for developers learning GitHub faster.

When you add or revise an item based on the GitHub Blog or GitHub Changelog, mention that source in the entry.

If there are no meaningful updates to publish, do not create a pull request. Emit `noop` instead.

When the file is updated, use the safe-outputs `create-pull-request` mechanism so the changes are proposed in a pull request for Mona to review.
