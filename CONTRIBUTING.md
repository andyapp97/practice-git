# Contributing

How a change gets into this repo, in plain English.

## How a change gets in

Nobody commits to `main` directly. Every change takes the same path:

1. **Branch off `main`.** Give it a short name that says what it does — `docs/contributing-guide`, `fix/broken-link`.
2. **Make the change.** Keep it to one thing. A branch that does two unrelated things is two branches.
3. **Commit** with a conventional prefix (see below).
4. **Push the branch** to `origin`.
5. **Open a pull request** against `main`, with a description in the required shape (see below).
6. **Wait for CI**, then get it reviewed and merged.

That's it. No step is optional, including for one-line changes.

## Commit messages

Every commit message starts with one of five prefixes:

| Prefix | Use it for | Example |
| --- | --- | --- |
| `feat` | New functionality | `feat: add search to the index page` |
| `fix` | Correcting broken behaviour | `fix: stop the link checker crashing on redirects` |
| `docs` | Documentation only | `docs: explain the release process` |
| `chore` | Maintenance, config, tidying | `chore: bump the checkout action to v4` |
| `test` | Adding or changing tests | `test: cover the empty-input case` |

Pick the one that matches what the commit actually does. If a commit needs two prefixes, it should probably be two commits.

## Writing the PR description

Every pull request description has three sections:

**What was asked** — the original request, in your words. What someone wanted, not what you did about it.

**What was built** — what actually landed in the diff. Files, behaviour, anything a reviewer should look at first.

**Deviation and why** — anything you did differently from what was asked, or anything you left out. Write `None` if there was none. This section is the point of the shape: it's where a reviewer finds the surprises without having to reverse-engineer them from the diff.

## Placeholder markers

This repo bans the placeholder keyword that `.github/workflows/checks.yml` greps for — the four-letter one meaning "come back to this later". If you're about to leave one in a file, open an issue instead and link it from the code or the PR.

The exact string lives in `checks.yml` if you need to see it.

## What CI checks

`.github/workflows/checks.yml` runs on every pull request. Right now it does one thing: scans `README.md` for that placeholder keyword and fails the PR if it finds one.

**Note the gap.** The repo rule bans that keyword in *every* file, but CI currently only enforces it on `README.md`. A green CI run is not proof that you followed the rule — it only proves `README.md` is clean. Check your own files.

## Adding dependencies or tools

Ask first. Open an issue, or raise it in the PR before you add it — not after. This covers packages, GitHub Actions, linters, build tools, anything that adds something new the repo depends on.
