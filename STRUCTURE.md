# AI Works Portfolio — Structure & Design Proposal

> **Deliverable location note:** This file was authored by the `researcher` agent. The
> sandbox blocked all read/write access outside the `claudecode` working directory, so it
> could not be written directly to `C:\Users\user\OneDrive\Desktop\ai-works-portfolio\STRUCTURE.md`.
> Please move/copy it there. For the same reason the proposal below is grounded in the
> design brief and web research rather than a direct re-read of `abstract_design_prompt.yaml`
> and the current `index.html` — reconcile against those two files before building.

---

## 1. Theme recap (from the design brief)

"EY-style" professional-services aesthetic:

- **Base:** white `#FFFFFF`, light gray `#F5F5F5`, near-black `#1A1A1A`.
- **Accent:** minimal yellow `#FFD500` (used sparingly), dark gray `#4A4A4A` for secondary text.
- **Type:** Inter sans-serif.
- **Form:** sharp edges (0 border-radius), generous whitespace.
- **Tone:** formal, professional, global, transparent.
- **Motion:** subtle fade / slide on scroll.

The product is a **catalog of screenshots of AI-development outputs** (apps, skills,
subagents) — closer to a consultancy "Our Work" / case-study index than a flashy creative
portfolio. The references below were chosen to match that catalog-of-work intent.

---

## 2. Reference sites (what to borrow)

1. **EY (ey.com)** — the anchor for the palette and restraint.
   - Borrow: single bright accent against an otherwise neutral white/gray/near-black system
     (`#FFE600`-family yellow, `#333`, `#999`, `#ccc`, white). The accent appears on *one*
     thing per view (a rule, a hover, a key CTA) — never as a fill across large areas. This
     is the discipline that makes the yellow read as "premium" rather than "loud."

2. **McKinsey / professional-services "Our Work" indexes** — case-study catalog model.
   - Borrow: each work item is a *card with a one-line outcome*, not just a title. High
     contrast, transparent case-study framing (problem → what was built → result). Maps
     directly onto our app/skill/subagent entries.

3. **Stripe Docs (stripe.com/docs)** — structured, scannable, developer-credible.
   - Borrow: deliberate column structure and a persistent, quiet navigation that treats
     categories as first-class. For us: a sticky top nav + a category filter row that lets a
     visitor jump between Apps / Skills / Subagents without losing place. Calm, copy-paste-
     clean information density.

4. **Awwwards "Minimalistic Portfolio" / Leonid Kostetskyi case study** — typographic air.
   - Borrow: very large headings, lots of "air" (free space), font does the work, minimal
     graphic chrome. Validates an oversized hero wordmark and a roomy spacing rhythm.

5. **Awwwards "Black & White" collection / Black Madre case study** — monochrome rigor.
   - Borrow: objective compositions, short paragraphs, large images, light galleries. Confirms
     letting the **screenshots themselves** be the color/visual interest while the chrome stays
     monochrome — the single most important call for this site, since our content *is* colorful
     app screenshots.

---

## 3. Proposed information architecture (sections, in order)

The existing site already has hero / works-gallery / about / footer with a category filter.
This keeps that spine and tightens it. Recommended section order:

1. **Sticky top nav (header)**
   - Left: wordmark "AI Works" (or owner name) in Inter, tight tracking.
   - Right: anchor links — Work · About · Contact.
   - White background, 1px bottom hairline in `#E5E5E5`; shrinks/condenses on scroll. Yellow
     used only as the active-link underline.

2. **Hero**
   - Oversized headline (e.g. "AI Works" / "A catalog of what I've built with AI").
   - One-sentence subhead in `#4A4A4A` describing the catalog (apps, skills, subagents).
   - A single yellow element: an underline rule, a small triangle mark (EY nod), or the CTA.
   - One primary CTA → scrolls to Work. Big top/bottom padding (the "air").

3. **Work gallery (the core)** — the reason the site exists.
   - **Category filter row** directly above the grid: All · Apps · Skills · Subagents
     (reuse existing filter). Active filter = near-black pill / underline; inactive = `#4A4A4A`.
   - **Responsive card grid** of screenshot entries. Each card:
     - Screenshot thumbnail (sharp corners, thin `#E5E5E5` frame, fills the card).
     - Title.
     - One-line outcome / description (`#4A4A4A`).
     - Small category tag.
   - Hover: subtle lift / image zoom + yellow accent line — restrained.
   - Optional: clicking a card opens a lightbox or detail panel with the full screenshot and a
     short problem→build→result blurb (the McKinsey case-study borrow). If time-boxed, ship the
     grid + lightbox first, detail copy later.

4. **About**
   - Short, transparent statement: who built these, the approach to building with AI, tools used.
   - Two-column on desktop (heading left, prose right) for an editorial feel; single column on
     mobile. Keep to a few short paragraphs (Black Madre borrow).

5. **Contact / CTA strip**
   - One line + email/links (GitHub, etc.). This can be a slim near-black band with a single
     yellow accent — the one place a stronger accent is justified.

6. **Footer**
   - Wordmark, copyright, minimal links. Light gray `#F5F5F5` background, near-black text.

**Why this order:** nav → hero establishes credibility and palette; work-first respects that
the catalog is the product (McKinsey/Stripe lead with substance); about/contact provide the
"transparent, global, professional" trust layer the brief asks for; footer closes quietly.

---

## 4. Concrete build guidance

**Type scale (Inter, rem):**
| Token | Size / line-height | Weight | Use |
|---|---|---|---|
| Display | 4.5rem / 1.05 | 700 | Hero headline (clamp down to ~2.5rem on mobile) |
| H2 | 2.25rem / 1.15 | 600 | Section headings |
| H3 | 1.25rem / 1.3 | 600 | Card titles |
| Body | 1rem / 1.6 | 400 | Prose |
| Small/Tag | 0.8125rem / 1.4 | 500, letter-spacing 0.04em, uppercase | Category tags, eyebrows |

Use `clamp()` for the hero so it scales fluidly without breakpoints.

**Spacing rhythm:** base unit 8px. Section vertical padding `96px–128px` desktop / `56px–64px`
mobile. Card gap `24px`. Max content width `1200px`, centered, with `24px` side gutters. Lead
with whitespace — when unsure, add space.

**Grid:** work gallery = `repeat(auto-fill, minmax(300px, 1fr))` → 3 cols ≥1024px, 2 cols
≥640px, 1 col below. About = 2-col (`5fr 7fr`) ≥768px, else 1 col.

**Accent usage (the discipline):** yellow `#FFD500` on at most one element per viewport —
hero rule/CTA, active nav underline, card hover line, contact band. Everything else lives in
white / `#F5F5F5` / `#1A1A1A` / `#4A4A4A`. Never a large yellow fill.

**Edges:** `border-radius: 0` everywhere. Borders are 1px hairlines `#E5E5E5`. Shadows minimal
or none; prefer borders + spacing to separate elements.

**Motion (subtle fade/slide):** on-scroll reveal via IntersectionObserver — `opacity 0→1` +
`translateY(16px→0)`, `~400ms ease-out`, staggered ~60ms across grid cards. Respect
`prefers-reduced-motion: reduce` (disable transforms). Nav condense on scroll. Keep it quiet.

**Imagery:** screenshots are the only color. Frame them in thin hairlines, consistent aspect
ratio (object-fit: cover), lazy-load (`loading="lazy"`), and provide alt text per item.

**Zero-build constraints:** single static `index.html`, Inter via Google Fonts (or system
fallback `-apple-system, Segoe UI, Roboto, sans-serif`), vanilla CSS (custom properties for the
palette) + a few lines of vanilla JS for the filter, IntersectionObserver reveals, and the
optional lightbox. No framework, no bundler. Keep `.nojekyll` and `404.html` as-is for GitHub
Pages.

**Accessibility:** maintain near-black-on-white contrast; the yellow is decorative only — never
put essential text on yellow without a dark color (and never light text on yellow). Semantic
landmarks (`header`/`main`/`section`/`footer`), focus-visible states, keyboard-operable filter
and lightbox.
