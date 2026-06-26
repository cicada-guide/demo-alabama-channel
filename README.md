# The Alabama Channel — Newsroom Demo

A hosted, pre-launch demonstration of **The Alabama Channel**: a public tool to search,
read, and cite Alabama civic and legislative meetings. Built for newsroom partners by the
**League of Women Voters of Alabama Education Fund** in partnership with **cicada.guide**.

**Live:** https://cicada-guide.github.io/demo-alabama-channel/

> **This is a non-functional demo.** Every speaker name is a placeholder, every quote and
> score is synthetic, and the search / AI / analytics shown are illustrative mockups of a
> future product — nothing here queries real data. The page opens behind a "Newsroom
> preview" notice and carries a persistent `DEMO` banner. See [Demo honesty](#demo-honesty).

## What it shows

A single screen with a fixed navy rail and three switchable views:

| View | What it demonstrates |
|------|----------------------|
| **Ask the corpus** | Plain-English search over meetings → an AI summary plus speaker-attributed, timestamped result clips with confidence scores and bill chips. |
| **Read a meeting** | A transcript reader: speaker-identification chips (enrolled / matched / needs-name / fallback), timestamps, and bill auto-extraction. |
| **Member tracking** | A member profile with appearance stats and a floor-vs-committee consistency breakdown by topic. |

The rail also shows Browse entries (Bills & resolutions, Bodies & sessions, Elected
officials) as part of the vision. The header references the target corpus: "1,230+ meetings
indexed, ~600 fully processed."

## How it's built

- **One file.** Everything is in [`index.html`](index.html) — inline CSS, a small vanilla-JS
  view switcher, no build step, no dependencies, no backend.
- **Fonts via CDN.** General Sans (Fontshare) + Plus Jakarta Sans + IBM Plex Mono (Google Fonts).
- **Design system.** All visual decisions follow [`DESIGN.md`](DESIGN.md) (Direction: Modern
  Civic Tech — Civic Blue `#1D63D1`, Verify Teal `#0E8C8C`, mono reserved for evidence).

## How it's deployed

GitHub Pages serves the repo root from the `main` branch. **Pushing to `main` deploys the
live site** (allow a minute for the Pages build). There is no staging environment.

## How to update the demo

1. Read [`DESIGN.md`](DESIGN.md) first — it is the source of truth for fonts, colors,
   spacing, and the named rules. Don't deviate without updating DESIGN.md.
2. Edit [`index.html`](index.html). Views are toggled by `data-view` / `switchTo()`; the
   click-gate and `DEMO` banner are defined near the top of `<body>`.
3. Preview locally by opening `index.html` in a browser.
4. Commit and push to `main`; confirm the live URL reflects the change.

## Demo honesty

Because the product's whole premise is verifiable trust ("every claim traces back to the
tape"), the demo never lets synthetic content read as real:

- A click-through gate explains that names are placeholders and quotes are illustrative.
- A persistent amber `DEMO` banner and a footer reminder repeat it.
- Copy near every quote states that production quotes must be **verified against the source
  video before publication**.

If you wire in real data later, that honesty scaffolding (gate, banner, placeholder framing)
must come down deliberately — see the notes in [`CLAUDE.md`](CLAUDE.md).

## Project files

| File | Purpose |
|------|---------|
| [`index.html`](index.html) | The entire demo (markup, styles, view-switch script). |
| [`DESIGN.md`](DESIGN.md) | Design system — read before any visual change. |
| [`CLAUDE.md`](CLAUDE.md) | Project guidance and roadmap notes. |
| `Alabama Channel One-Pager.pdf` | Partner-facing one-pager. |

## Partners

League of Women Voters of Alabama Education Fund × [cicada.guide](https://cicada.guide)
