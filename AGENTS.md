# AGENTS.md

This repository is a **GitHub Composite Action** that builds a [Zola](https://www.getzola.org/) static site using Docker and uploads the result as a GitHub Pages artifact.

## Architecture

- **`action.yml`** — The action definition. Pulls `ghcr.io/getzola/zola:<version>`, runs `zola build` (and optionally `zola check`) via Docker, then uploads the output with `actions/upload-pages-artifact`.
- **`.github/workflows/release-please.yml`** — Automated release workflow. On every push to `master`, release-please creates/updates a release PR. When merged, it creates a GitHub Release and moves the major version tag (e.g. `v0`) to the new commit.
- **`release-please-config.json`** — Configured as `release-type: simple` with `bump-minor-pre-major` enabled (pre-1.0 semver).

## Release process

Releases are fully automated via release-please:
1. Merge commits with conventional commit messages (`feat:`, `fix:`, `chore:`, `deps:`) to `master`
2. release-please opens/updates a release PR with CHANGELOG entries
3. Merging the release PR creates a GitHub Release and moves the major version tag (`v0`, `v1`, etc.)

There are no build steps, test commands, or local tooling — the action runs entirely in GitHub Actions via Docker.
