# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository purpose

This is `Somendran/Somendran` — a GitHub profile README repository. Its sole content-bearing file is `README.md`, which GitHub renders on the profile page at github.com/Somendran. There is no application code, build system, package manifest, or test suite. The `assets/` directory currently exists but is empty.

## Structure

- `README.md` — the profile page content. All edits to "the site" are edits to this one file.
- `.github/workflows/link-check.yml` — runs `lychee-action` against `README.md` on every push/PR that touches it, weekly on a schedule, and on manual dispatch. Accepts HTTP status ranges `100..=103,200..=299,999` (999 tolerates LinkedIn-style bot-blocked responses) — link edits should stay compatible with these checks.
- `.github/workflows/snake.yml` — runs daily (cron) to regenerate a GitHub contribution "snake" SVG via `Platane/snk` and publishes it to the `output` branch via `crazy-max/ghaction-github-pages`. `README.md` embeds the dark-variant SVG directly from that branch's raw URL. This workflow requires `contents: write` permission and does not need to be touched when editing README content.

## Working in this repo

- Changes are almost always direct edits to `README.md` (badges, project table, tech stack, links).
- After editing links in `README.md`, keep in mind the link-check workflow will validate them — avoid introducing links outside the accepted status code ranges above.
- There is no local build/lint/test command to run; README changes are validated by GitHub Actions (link-check) after push, and by visually reviewing the rendered Markdown/badges.
