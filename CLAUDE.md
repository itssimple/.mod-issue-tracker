# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working in this repository.

## What this repository is

This is the public issue tracker for NoLifeKing85's Minecraft mods. It contains **no source code** — its purpose is to collect bug reports and feature requests from mod users via GitHub Issues.

## Repository layout

- `.github/ISSUE_TEMPLATE/bug_report.md` — bug report template (applies labels `bug, triage`; asks for game version and modloader: Forge, NeoForge, Fabric, Quilt)
- `.github/ISSUE_TEMPLATE/feature_request.md` — feature request template (applies labels `enhancement, triage`)
- `.github/workflows/discord-issue-notifications.yml` — sends a Discord embed to a webhook whenever a new issue is opened
- `.github/FUNDING.yml` — sponsor links (GitHub Sponsors, Ko-fi)

## Discord notifications

The `discord-issue-notifications.yml` workflow fires on `issues: opened` and posts a rich embed (title, author, labels, body excerpt, color-coded by label) to Discord.

- The webhook URL comes from the repository secret **`DISCORD_WEBHOOK_URL`**.
- If the secret is not set, the notification step is skipped — the workflow never fails because of a missing webhook.
- Issue titles and bodies are sent via `actions/github-script` (JSON-built payload, `allowed_mentions` disabled), so untrusted issue content cannot inject shell commands or Discord mentions.

## Conventions

- There is no build, test, or lint step — changes here are limited to issue templates, workflows, and documentation.
- Keep issue template labels (`bug`, `enhancement`, `triage`) in sync with the label-based embed colors in the Discord workflow if either changes.
