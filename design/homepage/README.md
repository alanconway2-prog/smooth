# Handoff: The Smooth Company — Homepage Redesign (Tailor theme)
## For a developer using Claude Code

## Overview
Full mobile-first homepage redesign for The Smooth Company: calm, premium, editorial (Refy-lean) but built to convert. Covers two breakpoints — mobile (390px, primary) and desktop (1440px). The design is direction "10A", refined over many rounds.

## About the design files
`Smooth Homepage.dc.html` is a **design reference authored in HTML** — a prototype of look, layout, spacing and behavior. It is **not production code**. Recreate this as native Liquid sections in the existing **Tailor theme (Shopify OS 2.0)**, reusing the theme's sections, snippets, settings and CSS. Do **not** add a page builder (PageFly/Zellor/etc.) — moving the homepage to native sections is an explicit goal.

The reference renders both breakpoints side by side (two frames labelled Mobile / Desktop) driven by one component. Ignore the `<x-dc>` / `support.js` wrapper and the `data-props`/Tweaks scaffolding — those are prototyping runtime, not deliverables (but DO read the Tweaks as the list of merchant-configurable settings — see "Section settings").

## ⚠️ Header & announcement — replace, don't append (previous build missed this)
On the last attempt the theme kept its OWN header and announcement bar and the new ones were added alongside. This time: **modify the theme's existing `sections/header.liquid` and its announcement block (in `header-group.json`) in place** — restyle them to the spec below. Do not create parallel header/announcement sections. Verify on the live preview that only ONE header and ONE announcement bar render.

## Fidelity
High-fidelity, both breakpoints. Colors, type, spacing, grids and interactions are final. The **Reviews block is provisional** — build a strong generic version until the reviews-platform audit (Loox / Klaviyo Reviews / Firework UGC are all installed); keep markup swappable.

## Scroll order → Tailor section mapping
Rebuild `templates/index.json` to this order:

1. **Announcement bar** — ink `#1d1d1b`, off-white uppercase tracked text: "Free delivery on all orders £30+".
2. **Header** (sticky, white, 1px bottom border `#eeeeec`):
   - Mobile: hamburger + search left · centered black wordmark · account + bag right.
   - Desktop: text nav (Shop / Bestsellers / New / Smooth School) left · **centered** black wordmark · right group = an **offer highlight link** ("20% off gift sets" with a small mint dot) + search + bag. Logo must be centered — give the left nav and right group equal flex so it stays centered.
3. **Hero** — `sections/video.liquid`. Full-bleed muted autoplay loop, poster for first paint, `playsinline`. **Two configurable text placements** (see settings): (a) below the video, centered on white — headline + subline + solid square CTA; (b) on the video, with a position control (bottom-left default, also bottom-center/right, center, top-left/right) and an auto-adjusting scrim. Aggregate rating is NOT in the hero anymore.
4. **Best sellers** — `sections/featured-collection.liquid`. Tabs (Best sellers / New in / Gifting / Travel), each a collection, no reload. Large left-aligned title + "View all" link. Mobile: scroll-snap rail, one large card + ~12% peek of next, no arrows. Desktop: row that fills width (4 or 6 per row — a setting) with prev/next arrows. Card spec below.
5. **Editorial banner** — a single full-bleed image (16:7 desktop / 4:5 mobile) with one small label + outline (white) button, **bottom-left**. (Hideable — see settings.)
6. **Press** — `sections/logo-list.liquid`. "As seen in" (black) + press names in Gotham Bold. **Press logos must be uploadable image fields** (not text) — merchant uploads Vogue/GMA/etc. logos.
7. **Statement break** — a soft paper-toned (`#f6f5f1`) band, centered large Gotham statement with B Corp / cruelty-free / vegan / 1%-giveback woven into the sentence, and two links (Our story · Smooth School). No image, no rules, no eyebrow.
8. **Shop by category** — `sections/collection-list.liquid`. Large left title + "View all". 3 categories, full-bleed, 2px gaps. Mobile rail / desktop 3-up. Big bold category name bottom-left over a bottom gradient.
9. **Shoppable reels** — **CUSTOM** (or the installed video-reels app). 9:16 tiles. Desktop: **edge-to-edge**, 5 across, 2px gap; center tile **autoplays** (only that one), auto-rotates every ~4.5s; **click any tile to move it to center and play**; left/right arrow controls sit **on** the video; no play-button glyphs. Mobile: one centered tile + two peeks, no controls, no autoplay beyond center. Under each video: a bordered product card — small thumb + uppercase name + price + filled-black plus-circle add-to-cart. Only the centered video autoplays (performance).
10. **Reviews** — **CUSTOM / PROVISIONAL.** Big statement "460+ five-star reviews.", grid/rail of review cards on **mint `#b5e3d9`** with black text (stars, quote, verified name). Desktop 4-up, mobile rail.
11. **Newsletter + Footer** — ink background. Desktop: white wordmark + "1% to charity" line, newsletter (email + solid square Subscribe), then 4 open columns (Shop / Learn / Help / Follow). Mobile: **centered** brand + newsletter block up top; menu columns become **collapsible accordions** (rotating chevron, all closed by default); **social icons** (Instagram / TikTok / YouTube glyphs) centered below; then policies row (Terms · Privacy · Accessibility) + © / B Corp line, centered. Smooth School lives in nav + footer (Learn) only — never a homepage section.

### Reviews rule
Proof as punctuation, exactly three touchpoints, never scattered: (1) aggregate rating (currently woven via press/reviews block), (2) stars on product cards, (3) the dedicated reviews block. No other review call-outs.

## Product card (CUSTOM — extend `snippets/product-card.liquid`)
- Media aspect **configurable: portrait (4:5) or square (1:1)** — see settings. Grey ground `#f4f3f0`.
- Mint badge `#b5e3d9`, black text, flush in the **top-left corner** (no offset), small tracked caps.
- Filled-black plus-circle add-to-cart, bottom-right on the media.
- Below media: uppercase name, then **black** stars + grey `(count)` with the count underlined, then price. **Price shows decimals (£18.00)** and supports sale: sale price ink + struck compare-at `#A8A8A2` (+ optional "Save £x"). Reuse `snippets/price.liquid`.

## Section settings (merchant-configurable — from the reference's Tweaks)
- **Hero text placement**: Below video / On video; and **Hero text position** (bottom-left, bottom-center, bottom-right, center, top-left, top-right) when on video.
- **Product image shape**: Portrait / Square (applies to the product cards).
- **Best sellers per row**: 4 or 6 (desktop grid).
- **Press logos**: repeatable image uploads.
- **Show/hide section toggles**: editorial banner, press bar, statement break, shoppable reels (each a boolean; merchant can hide any of these). Build every homepage section with an enable/disable setting where sensible.
- Standard collection/product pickers for best-sellers tabs, categories, reels, hero video + poster.

## Interactions
- Tabs: swap collection, no reload; active = ink 600 + underline.
- Reels (desktop): auto-rotate center, click-to-center-and-play, arrows on video; (mobile) static center + peeks.
- Footer accordions (mobile only): chevron rotates 0→180°, one open by default.
- Rails: `scroll-snap`, `scroll-padding-left` to inset first card; **do not use scrollIntoView** — use scrollLeft/scrollTo math.
- Hero video: muted, autoplay, loop, playsinline, poster for first paint. Reels: only the centered video autoplays.

## Design tokens (match `config/settings_data.json` — reuse theme settings)
- Ink / text: `#1d1d1b` · Mint accent (sparingly): `#b5e3d9` · deep teal `#0f3d51`
- Hairlines `#efefec`/`#eeeeec`/`#e6e4e0` (light), `#333330` (on ink) · card grey `#f4f3f0` · statement band `#f6f5f1`
- Muted text `#6C6C66`/`#8A8A84`/`#A8A8A2` · stars black · page white; footer ink
- **Type: Gotham only.** Headlines = Gotham **Bold** (700); body/UI = Gotham Medium. Theme already loads `Gotham_Bold.woff2`, `Gotham-Medium.woff2`, `Gotham-Light_1.woff2` on the store's Shopify files CDN. No serif / no Google fonts. Watch for stray inline `font-weight:400` flattening bold headings.
- Section rhythm: 72–110px top / 0 bottom (mobile ~80px, desktop ~110px). Buttons square (0 radius), uppercase, ~0.16em tracking, ink solid or outline.

## Assets (in `assets/`)
- `logo-black.png` (white header), `logo-white.png` (ink footer/announcement), `footer-logo.png` (mint option).
- `mane-master.webp` — the hero product shot used in cards/reels.
- All other product/category/hero/review imagery is a striped grey placeholder — swap for real photography + the muted hero film. Fonts: reuse the theme's Gotham; don't re-upload.

## Suggested build sequence
1. Header + announcement — **replace existing in place** (tokens, logos, sticky white, responsive nav, desktop offer link, centered logo).
2. `snippets/product-card.liquid` (badge, plus-circle, sale price, portrait/square setting).
3. Hero video (both placements + position setting).
4. Best sellers (tabs + rail↔grid, per-row setting).
5. Editorial 50:50, statement break, category.
6. Reels (custom, or wire the installed app).
7. Reviews (generic/provisional, mint).
8. Newsletter + footer (accordion↔columns).
9. Rebuild `templates/index.json`; remove the page-builder homepage sections.
10. QA both breakpoints against the reference (Mobile + Desktop frames).

## Files
- `README.md` — this handoff.
- `Smooth Homepage.dc.html` — the hi-fi reference (open in a browser).
- `assets/` — logo variants + `mane-master.webp`.
