# Zedex Landing Page

Single-page marketing site for **Zedex** — Petar's freelance offer selling automated wholesale lead-gen + outreach systems for physical product brands.

## Stack

- **Single file**: `index.html` (inline CSS in `<style>`, inline JS in `<script>` at end of body). No framework, no build step, no package.json.
- **Assets**: `assets/` — logos (SVG with `onerror` fallback to text), founder photo `miroslav_cupffee.jpg`.
- **External deps** (all CDN): Google Fonts (Playfair Display + Inter), Calendly inline-widget script.
- **Deploys anywhere** that serves static HTML.

## Folder history

- Folder was renamed `mise` → `zedex` on 2026-04-24 via robocopy /MOVE (standard `mv` / `Rename-Item` failed with Windows file locks from VS Code).
- `zedex/` is its own git repo (has `.git`). Parent `WEBSITE-BUILDER/` is not a repo.

## Brand tokens (`:root` CSS vars)

| var | hex | role |
|---|---|---|
| `--bg` | `#F4EFE6` | cream page background |
| `--gold` | `#B5693A` | primary CTA, brand accent, italic headline color |
| `--gold-soft` | `#C88254` | hover state for gold |
| `--green` | `#2A4158` | deep navy-green accent (checkmarks, meta) |
| `--text` | `#0F1824` | near-black body text |
| `--text-dim` | ~rgba(15,24,36,.62) | secondary text |

**Typography**: Inter for everything. Headlines at weight 700–800 with tight negative tracking (`-0.025em`). Italic `<em>` accents in gold for emphasis (Inter italic, not serif — switched from Playfair 2026-04-24 for readability).

## Section order (top → bottom)

1. Header (scroll-aware, blurs bg after 20px scroll)
2. **Hero** — 2-col grid (text left, Calendly inline widget right). Stacks on ≤1024px.
3. **Trust bar** — Marquee of brand logos (Cupffee real with local SVG `assets/logos/cupffee.svg`; rest are placeholder brand names with logo-fallback text styling).
4. **Reviews** — Trustpilot-style widget + 3 review cards.
5. **Case Studies** — 3 brand cards (Cupffee real; Northway + Still & Spark placeholder).
6. **Founder** — "Behind Zedex" — round portrait + 3-paragraph intro from Petar. **Moved here 2026-05-03** from position 10 (was right before Final CTA). Reasoning: "I work alone" is the #1 differentiator vs agencies; establishing it early reframes everything that follows through the founder lens. Photo: `assets/founder.jpg`.
7. ~~VSL / Loom~~ — **ARCHIVED 2026-04-24** (commented out in HTML). Will return once Petar records the 2-minute founder intro. See "Archived sections" below for restore instructions.
8. **Outcomes** — 6 stat cards. **Swapped with How It Works 2026-05-03** — founders care about results before process.
9. **How It Works** — 4 steps.
10. **Integrations** — 15-logo grid (HubSpot, Salesforce, Pipedrive, Monday, Airtable, Google Workspace, Microsoft 365, Shopify, WooCommerce, Apollo, Zoho, Close, Attio, ActiveCampaign, Clay). **Restored 2026-05-03** as a dedicated section between Outcomes and Engagement Models. Logos via Clearbit with text fallback. Section copy in ICP-native language.
11. **Engagement models** — 2 tier cards (Done-For-You + White-Label). No prices shown; both CTAs go to Calendly.
12. FAQ — accordion (includes pricing-without-price answer, white-label question; CRM tools list still in FAQ as supplemental coverage to the Integrations section).
13. Final CTA
14. Footer

**Mobile-only**: sticky bottom-of-screen CTA bar (`.mobile-sticky-cta`) added 2026-05-03. Visible only at ≤820px. Body padding-bottom: 80px to prevent overlap.

**Narrative arc** (updated 2026-05-03): Hero promise → trust (logos) → proof at scale (reviews) → proof in depth (cases) → **personal trust (Founder)** → outcomes (what you get) → process (how) → fit (integrations) → engagement (DFY/white-label) → objections (FAQ) → close (Final CTA). The founder reframe at position 6 sets context for the rest of the page.

## Removed sections (kept their CSS)

- **Pains** (`<!-- Pains -->` previously at line ~598) was removed in 2026-04-24 minimalism pass. CSS still in `<style>` block under `/* Pains */` comments, restorable.
- **Integrations** was originally removed 2026-04-24 then **restored 2026-05-03** as a dedicated section. CSS was already preserved.

## Removed sections that may be re-added

- **Pains** (`<!-- Pains -->` previously at line ~598) was removed in 2026-04-24 minimalism pass. CSS still in `<style>` block under `/* Pains */` comments, restorable.

## Archived sections

### VSL / Loom section (commented out 2026-04-24)

Lives between **Pains** and **How It Works** in `index.html`. Wrapped in an outer HTML comment block so the markup is preserved but the section doesn't render. CSS for `.vsl`, `.vsl-head`, `.vsl-frame`, `.vsl-embed`, `.vsl-placeholder`, `.vsl-play`, `.vsl-placeholder-text`, `.vsl-placeholder-sub` is still in the `<style>` block — do **not** delete that CSS; the section will reuse it on restore.

**To restore:** find the comment marker `<!-- VSL / Loom — ARCHIVED ...` in `index.html`, remove the outer `<!--` and `-->` markers that wrap the `<section id="vsl">...</section>` block. Then populate with the real Loom embed:

```html
<div class="vsl-embed">
  <iframe src="https://www.loom.com/embed/YOUR_LOOM_ID"
          frameborder="0" allowfullscreen
          style="width:100%;height:100%;border:0"></iframe>
</div>
```

Replaces the current `<div class="vsl-placeholder">...</div>` block. Section will slot back in between Pains and How It Works.

**Why archived:** Petar plans to record a 2-minute founder intro to populate it. Kept the CSS + markup intact so the section is a 30-second restore when the Loom URL is ready.

## Secondary pages

- **`case-studies.html`** — 15 case studies on a single page (Cupffee real + 14 fictional composites). Sticky side nav, deep-linkable via `#brand-slug`. Trust bar marquee logos link here. Added 2026-04-24 with a prominent disclaimer labeling composite/illustrative cases vs real client work.

## Voice & tone

**Zedex speaks as "I"** (Petar, the founder) — not "we." Established 2026-04-24 to keep the voice consistent with the "I work alone" founder section.

- Use **"I"** anywhere Zedex is the actor: hero subtitle, How It Works step descriptions, FAQ answers, engagement card taglines, Outcomes/Cases section subs.
- **Keep "we"** in three contexts:
  1. Client testimonials & case-study quotes — "we" = the client's company speaking
  2. Joint "we" — when the sentence means *you + me on the call together* (e.g., "We'll figure that out on the call", "We get on a call together")
  3. Prospect-side "our" — when "our" refers to the *prospect's* things (e.g., FAQ "Can you build this for our distributors?")
- The founder section uses **"I work alone — on purpose."** Don't soften this; it's the brand differentiator.
- Tone: confident but not boastful, concrete not buzzwordy, professional but warm. Avoid "scope creep," "kickoff," "leveraged," "drive results," "scaled" as verbs, marketing parallelisms ("X, Y, and Z"), and "no X, no Y — just Z" patterns.

## Brand assets

- **`assets/brand/`** — wordmark.svg, z-mark.svg, favicon.svg (favicon already wired into both pages).
- **`assets/brand/linkedin-banner.html`** — 3 variants of 1584×396 LinkedIn banner with content in right half to avoid profile-photo overlay. Export to PNG via Chrome DevTools → Capture node screenshot.
- **`assets/brand/README.md`** — export instructions for all brand assets.
- Brand was originally designed in Playfair Display via Claude Design (Apr 2026), then site switched to Inter for readability. The brand SVGs retain Playfair (standalone logo use); the site body uses Inter.

## Calendly integration

- Booking URL: `https://calendly.com/krastev/meeting`
- **Hero** uses the inline embed (`calendly-inline-widget` div + widget.js script loaded at end of body) with `primary_color=B5693A` and `hide_gdpr_banner=1`.
- All other CTAs (header nav, final CTA section, footer, mobile panel) link to the same URL in a new tab.

## Design conventions

- **Italic accents in headlines**: wrap in `<em>` → renders as Inter italic in gold.
- **CTA button**: `.btn-primary` — gold pill, white text, 16×32 padding, animated `→` arrow on hover, lifts 2px + drops gold shadow. Used in header nav, hero (href `#hero-calendly` — scrolls to the embed on mobile, visually anchors the left column on desktop), and final CTA section.
- **Hero-bullets pattern**: three italic Playfair benefit lines with gold icon chips, mirroring the split-hero pattern from direct-response agency sites (but in the warm editorial palette).
- **Cards**: white bg, 1px border (`--border`), 18–28px radius, lift 4px on hover with deeper shadow.
- **Reveal animations**: `.reveal` class + IntersectionObserver adds `.is-visible` at 12% threshold. Delay modifiers: `.delay-1`/`.delay-2`/`.delay-3`.
- **Section head pattern**: `<span class="section-tag">` (small uppercase gold label) + `<h2 class="section-title">` (with italic `<em>` accent) + `<p class="section-sub">`.

## Responsive breakpoints

- `≤1024px`: hero stacks to 1-col, text centers
- `≤820px`: nav collapses to hamburger, sections shorten (90px padding), hero-meta wraps
- `≤480px`: tighter container padding, smaller hero title (40px), smaller btn-primary

## Currency / region

- Uses **€** throughout copy. No explicit country targeting — positioning is "physical product brands" generally, leaning EU/global.

## Content caveats (for future sessions)

- **Testimonials are mixed real/placeholder**: Cupffee / Miroslav Zapryanov is a real Bulgarian brand. Northway Goods / Tomás Herrera and Still & Spark / Amara Okafor (renamed from "Rania Okafor" 2026-04-24) are placeholder brands. Trustpilot widget is visual-only.
- **Pricing is NOT shown on the site** (removed 2026-04-24 per positioning decision). All price discussion happens on the strategy call. Do not re-add price tags, tiers, or "starting at €X" references unless Petar explicitly reverses this.
- **Two engagement models**: Done-For-You (for the brand's own pipeline) and White-Label (brand deploys the system to their distributors). Same core infrastructure, different delivery target. Both target *product brand founders* — not agencies.
- **Service stack** behind the scenes: n8n + Claude API + Apollo/Clay + HubSpot/Pipedrive + Shopify/WooCommerce. Listed in FAQ but the site is channel-agnostic to the prospect.

## What the site is NOT

- Not a CMS — no admin panel, copy is edited directly in `index.html`.
- Not connected to analytics yet (no GA/Plausible tags installed).
- Not connected to a form backend — the only conversion path is Calendly.
