# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is
A hosted proof-of-concept newsroom interface for **The Alabama Channel** — a public
tool to search, read, and cite Alabama civic/legislative meetings. Single self-contained
`index.html` (inline CSS, fonts via CDN), deployed via GitHub Pages at
`https://cicada-guide.github.io/demo-alabama-channel/`. Partners: LWV of Alabama
Education Fund × cicada.guide.

## Design System
Always read `DESIGN.md` before making any visual or UI decision. All font choices,
colors, spacing, and aesthetic direction are defined there (Direction: Modern Civic
Tech — General Sans + Plus Jakarta Sans, Civic Blue `#1D63D1` + Verify Teal `#0E8C8C`,
IBM Plex Mono for evidence only). Do not deviate without explicit user approval.
In QA mode, flag any code that doesn't match `DESIGN.md`.

`index.html` implements the Modern Civic Tech system (General Sans via Fontshare +
Plus Jakarta Sans + IBM Plex Mono via Google Fonts, Civic Blue `#1D63D1`, Verify Teal
`#0E8C8C`). The original POC brand (Montserrat + `#2e97f2`) has been retired.

Roadmap and review notes live in `PLAN.md` (approved /autoplan review: retrieval-first
"Search the corpus" before AI synthesis) and `TODOS.md` (deferred scope). The "Ask the
corpus" → "Search the corpus" rename and retiring the AI summary panel are part of the
retrieval build (Increment 1–2), not the visual rebrand — the current page intentionally
still showcases the AI panel as the "Coming, Phase 2" vision behind the demo gate.
