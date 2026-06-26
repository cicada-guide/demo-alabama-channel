# Design System — The Alabama Channel (Newsroom)

> Source of truth for the public newsroom interface. Read this before any visual or
> UI change. Direction: **Modern Civic Tech** (chosen 2026-06-24 from a 3-way redesign).
> This is the public reading/search layer — distinct from the operator-facing
> "Evidence Console" system in `../alabama-channel/DESIGN.md`.

## Product Context
- **What this is:** A free public tool for searching, reading, and citing Alabama
  civic & legislative meetings (1,230+ indexed). Browse, Ask the corpus (AI search,
  Phase 2), Read a meeting, Member tracking.
- **Who it's for:** Newsroom partners and journalists first; the general public second
  (League of Women Voters voter-education audience). Many users are non-technical.
- **Space/industry:** Civic tech / public-records journalism. Peers: Documenters,
  CourtListener, Digital Democracy, news-org transcript tools.
- **Project type:** Public web app (reading + search), currently a hosted POC.
- **Partners:** LWV of Alabama Education Fund × cicada.guide.

## Memorable Thing (north star)
**"A public record you can trust — every claim traces back to the tape."**
Every design decision serves verifiable trust. AI summaries always expose their
sources; confidence is shown, not hidden; quotes carry timestamps and bodies.
If a choice makes the product feel slicker but less traceable, it loses.

## Aesthetic Direction
- **Direction:** Modern Civic Tech — confident, accessible, optimistic, public-good.
- **Decoration level:** intentional — clean surfaces, soft elevation, one gradient
  rail; restraint everywhere else.
- **Mood:** Trustworthy and current. Feels like a well-funded public institution
  that hired good designers, not a startup and not a government PDF.
- **What it rejects:** generic SaaS slop (purple gradients, 3-column icon grids,
  centered-everything), gov-portal drabness, and any styling that buries the source.

## Typography
- **Display/Hero:** General Sans (500/600/700) — geometric-humanist sans with
  character; headlines, panel titles, speaker names. Loaded via Bunny Fonts.
- **Body/UI:** Plus Jakarta Sans (400/500/600/700) — friendly, legible at small
  sizes, strong for non-technical readers.
- **Evidence/Mono:** IBM Plex Mono (500/600) — timestamps, confidence scores, bill
  IDs, counts, source paths, kickers/labels. **Evidence type only — never prose.**
- **Loading:** `https://fonts.bunny.net/css?family=general-sans:500,600,700|plus-jakarta-sans:400,500,600,700`
  + IBM Plex Mono via Google Fonts. (General Sans is not on Google Fonts; Bunny/Fontshare host it.)
- **Scale (px):** h1 32 / title 19 / lead 16 / body 14 / small 13 / meta 12 /
  mono-label 10–11. Display weight 600, letter-spacing −0.02em on h1, −0.01em on titles.
- **Line-height:** 1.1 display, 1.5 UI, 1.6 reading (summaries, excerpts).

## Color
- **Approach:** balanced — one civic blue for action/state, a verify-teal reserved
  for trust affordances, semantic green/amber/red, cool neutrals.
- **Primary — Civic Blue** `#1D63D1` (dark `#154FAC`, soft `#E5EEFC`): primary actions,
  active nav/tab, links, focus ring, selected state. **Accent scarcity: blue is for
  action and current state, not decoration.**
- **Trust — Verify Teal** `#0E8C8C` (soft `#DCF1F1`): citation/verification affordances
  only — "AI summary" label, "View all sources," verify-against-video cues. Reserved.
- **Neutrals:** canvas `#F6F8FC` · surface `#FFFFFF` · field `#EEF2F9` · border `#E2E8F2`
  · text `#14223A` · muted text `#5A6B85`.
- **Rail:** navy gradient `#102A4C → #0B1F3A`, inverse text `#FFFFFF`, active dot teal `#5BC8C8`.
- **Semantic:** success `#1F8A4C` / soft `#E3F4EA` · warning/demo `#B27A07` / soft `#FBEFD6`
  · danger `#C0322B` / soft `#FAE5E3` · info = primary blue.
- **Confidence scores** render in success green when ≥0.85, amber 0.70–0.84, danger <0.70.
- **Dark mode:** not in scope for the POC. When added: redesign rail/surfaces (don't
  invert), reduce saturation 10–20%, keep contrast ≥ WCAG AA.

## Spacing
- **Base unit:** 4px.
- **Density:** comfortable — roomy enough for the public, tight enough to scan results.
- **Scale:** 2xs(4) xs(8) sm(12) md(16) lg(24) xl(32) 2xl(48). Page gutter 36px,
  content max-width 1060px.

## Layout
- **Approach:** hybrid — fixed 256px navy rail + tabbed content area; card-based panels.
- **Grid:** single content column (max 1060px) with full-width cards; rail is persistent.
- **Border radius:** chips/pills 999px · inputs 12px · cards 16px · buttons 12px ·
  small controls 10px · avatars 50%.
- **Elevation:** soft only — `0 1px 2px rgba(20,34,58,.04)` resting, `0 4px 16px
  rgba(20,34,58,.08)` on result hover. No heavy shadows, no glassmorphism.

## Motion
- **Approach:** minimal-functional with light intent. Result cards lift on hover
  (150ms), inputs show a blue focus border, tabs/chips transition color.
- **Easing:** enter `ease-out`, exit `ease-in`, move `ease-in-out`.
- **Duration:** micro 50–100ms · short 150–250ms · medium 250–400ms.
- **Reduced motion:** honor `prefers-reduced-motion` — drop hover lifts, keep color/focus.

## Components
- **Buttons:** primary = Civic Blue fill, white text, 12px radius, Jakarta 700;
  secondary = white + 1.5px border, 600. Hover deepens to `#154FAC`.
- **Search input:** field bg, transparent border, focus → white bg + blue border, 15px.
- **Chips/filters:** pill (999px), 600 weight; active = blue-soft bg + blue-dark text
  + blue border. Active bill filter is a removable chip.
- **AI summary panel:** white→`#FAFCFF` gradient card, 4px blue→teal left edge, teal
  "AI summary · synthesized" pill, mono confidence pill, and a required
  **"View all sources →"** link. Never present a synthesized claim without its sources.
- **Result card:** title (General Sans 600), mono source line (body · date · duration ·
  `@ timestamp`), quoted excerpt in a tinted field block with `<mark>` highlight,
  footer with speaker avatar+name, bill chip, mono confidence. Actions top-right.
- **Demo banner:** amber-soft bar, amber `DEMO` pill — present whenever data is
  placeholder/illustrative (see Demo Honesty Rule).

## Named Rules
- **The Citation Rule.** Every AI-synthesized statement exposes its sources: a visible
  segment count, average confidence (mono), and a "View all sources" path. No claim
  stands without traceable evidence.
- **The Evidence Type Rule.** IBM Plex Mono is reserved for evidence — timestamps,
  confidence, bill/section IDs, counts, paths, kickers. Never for prose or headlines.
- **The Verify-Teal Rule.** Teal `#0E8C8C` marks trust/verification only. Don't spend
  it on decoration; if it's teal, it's about provenance.
- **Accent Scarcity Rule.** Civic Blue means action or current state. Overusing it as
  filler erases the signal.
- **The Demo Honesty Rule.** Placeholder names and illustrative quotes must stay
  visibly flagged (amber demo banner + gate notice). Trust depends on never letting a
  synthetic figure read as real.
- **Source-Safety of Quotes.** Copy near any quote/citation reinforces that production
  quotes must be verified against the source video before publication.

## Accessibility
WCAG AA baseline: contrast ≥ 4.5:1 for text, visible focus rings, keyboard-navigable
search/results/tabs, status never by color alone (confidence shows the number, labels
accompany semantic colors), and `prefers-reduced-motion` respected.

## Decisions Log
| Date | Decision | Rationale |
|------|----------|-----------|
| 2026-06-24 | Adopted **Modern Civic Tech** direction (General Sans + Plus Jakarta Sans, Civic Blue + Verify Teal) | Chosen from a 3-way redesign (vs. Civic Records/Archival and Newsroom Wire). Audience includes the non-technical public; accessible + current beat formal or techy, while keeping mono evidence rigor. |
| 2026-06-24 | Moved off Montserrat / `#2e97f2` from the original POC | Montserrat is overused; the redesign gives the newsroom its own face distinct from the operator console. Live `index.html` to be updated to match. |
| 2026-06-24 | Reserved IBM Plex Mono as evidence-only type | Borrowed the proven discipline from the sibling Evidence Console so AI output reads as sourced journalism. |
