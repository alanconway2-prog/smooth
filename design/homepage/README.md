# Handoff: The Smooth Company — Mobile Homepage Redesign (Tailor theme)

## Overview
A full mobile-first homepage redesign for The Smooth Company, built to feel calm, premium and editorial (Refy-lean) while still converting: full-bleed video hero, tight product rails, category discovery, proof used as punctuation, founder story, shoppable video, reviews and newsletter capture.

Primary canvas is **390px mobile**. Desktop is a scale-up of the same order, not a separate design.

## About the design files
The file in this bundle — `Smooth Homepage.dc.html` — is a **design reference created in HTML**. It is a prototype showing intended look, layout, spacing and behavior. **It is not production code to paste in.** The task is to **recreate this design as native Liquid sections in the existing Tailor theme** (this Shopify OS 2.0 theme), reusing the theme's existing sections, snippets, settings and CSS conventions wherever possible. Do **not** introduce a page builder (PageFly/Zellor/etc.) — the current homepage leans on those and moving to native sections is a goal of this redesign.

## Fidelity
**High-fidelity.** Colors, type, spacing and interactions are final. Recreate pixel-accurately using the theme's existing components. The one deliberately-provisional piece is the **Reviews block** (see notes) — build it as a strong generic block until the reviews-platform (Loox/Klaviyo/etc.) audit is done.

## Target: how this maps onto the Tailor theme
The homepage is `templates/index.json`. Rebuild its `sections`/`order` to the scroll order below. Almost every block has an existing native section — reuse it and set the listed settings. Only two items need custom work (flagged **CUSTOM**).

Scroll order → section mapping:

1. **Announcement bar** (free-shipping threshold) — theme header/announcement settings (`sections/header.liquid` + `header-group.json`). Ink background `#1d1d1b`, off-white text, uppercase, tracked. Single message: "Free delivery on all orders £30+".
2. **Header** — `sections/header.liquid`. White, sticky, `border-bottom:1px #eeeeec`. Left: hamburger + search. Center: **black** wordmark (`assets/WhiteSmoothCoHorizontalLogo.png` recolored, or the theme's dark logo setting). Right: account + bag. Icons ink `#1d1d1b`, 1.3px stroke.
3. **Hero** — `sections/video.liquid` (or `image-banner` for a still). Full-bleed muted autoplay loop, **poster image for first paint**, `playsinline`. **Copy sits BELOW the video, centered on white** (not overlaid): a compact rating line `★★★★★ 4.7 · 460+ reviews`, then the H2 on **one tidy near-full-width line**, a one-line subcopy, and a solid square CTA "Shop the range". This is Touchpoint 1 of the reviews rule.
4. **Best sellers** — `sections/featured-collection.liquid`, horizontal rail. **CUSTOM:** (a) a 3-way tab switcher above the rail (Best sellers / New in / Bundles) each pointing at a collection; (b) the card treatment — see Product card below. Row is inset ~10px from the screen edge with a tight 2px gap between cards; ends with a centered solid square "Shop all".
5. **Shop by category** — `sections/collection-list.liquid`, full-bleed edge-to-edge rail, 2px gaps, labels bottom-left in tracked caps over a soft bottom gradient. (Sticks / Creams / Tools / Travel / Gifting — the discovery spine.)
6. **Press / social proof** — `sections/logo-list.liquid` or `rich-text.liquid`. One airy band on white: press names in Gotham Bold + a single caption line "As seen in · Winner, Beauty Awards 2025 · Loved by 50,000+". One clean band only — do not repeat proof elsewhere.
7. **Founder story** — `sections/image-with-text.liquid`. Full-bleed portrait, then centered quote + solid square "Read more" linking to the story page.
8. **Watch & shop** — `sections/shop-the-look.liquid` or `video.liquid`, full-bleed 9:16 tiles, 2px gaps, play glyph, title + "Shop £xx" chip. Every tile routes to a PDP.
9. **Reviews** — **CUSTOM / PROVISIONAL.** Big `4.7`, full stars, "460+ verified reviews", a rail of photo review cards (image + stars + quote + verified buyer + product), and an outline square "Read all 460 reviews". Touchpoint 3. Wire to the real reviews app once the platform is chosen; keep markup swappable.
10. **Newsletter** — `sections/newsletter.liquid`, merged into the footer top (First/Email + solid square "Subscribe").
11. **Footer** — `sections/footer.liquid` + `footer-group.json`. Ink background, white wordmark, tagline, newsletter, then **accordion menus on mobile** (Shop / Learn / Help) with rotating chevrons, socials + copyright row. **Smooth School links live in nav + footer only — keep education off the homepage.**

### Reviews rule (important)
Proof as punctuation, exactly **three** touchpoints, do not scatter: (1) aggregate rating under the hero, (2) star ratings on product cards, (3) the one dedicated reviews block low down. No other review call-outs.

## Product card (CUSTOM — extend `snippets/product-card.liquid`)
Refy-style bordered card:
- Outer `border:1px solid #e6e4e0`.
- Media 4:5, badge top-left in tracked caps (theme badge system already set: outlined label style, badge colors configured).
- **Action bar sits at the bottom of the media, inside the border:** full-width, `background:#f4f4f2`, `border-top:1px solid #e6e4e0`, label "Add to cart" left + "+" right, tracked uppercase 10.5px. Hover → fills solid ink `#1d1d1b`, white text. (This is treatment "4A/action-bar"; it was chosen over an on-image bar and over price-in-button because it survives long titles and sale prices.)
- Below the frame (padding-left ~2px): product title (uppercase, 600), cutline (muted), stars + `(count)` with the count underlined, then price row.
- **Price row supports sale:** `£18` ink + `£22` struck `#A8A8A2` + optional "Save £4" mint-teal tag. Use the theme's `snippets/price.liquid` (compare-at already handled) — just restyle to match.

## Interactions & behavior
- **Tabs** (best sellers): click swaps the rail's collection; active tab is ink 600 with a 1.5px underline, others muted 500. No page reload.
- **Add to cart**: outline→solid fill on hover/press (0.18s all).
- **Footer accordions** (mobile): tap toggles a column; chevron rotates 0°→180° (0.2s). One open by default (Shop).
- **Rails**: horizontal scroll-snap (`scroll-snap-type:x mandatory`, `scroll-snap-align:start`). First card inset via `scroll-padding-left` so it clears the edge at rest.
- **Hero video**: muted, autoplay, loop, `playsinline`, poster for first paint; keep text legible if you ever overlay (default is text-below).
- **Vertical rhythm**: one rule — every section owns **72px top, 0 bottom**. Do not add ad-hoc bottom margins; the next section's top padding is the whole gap.

## Design tokens
These already match `config/settings_data.json` — reuse the theme settings rather than hard-coding:
- Ink / heading / body text: `#1d1d1b`
- Mint accent (signature, used sparingly): `#b5e3d9`  · deep teal: `#0f3d51` / `#102833`
- Lines / hairlines: `#e6e4e0` (light), `#eeeeec` (header), `#333330` (on ink)
- Card action-bar grey: `#f4f4f2`  · muted text: `#6C6C66` / `#8A8A84` / `#9A9A94` / `#A8A8A2`
- Star ratings: black `#000` (theme `color_star_ratings`)
- Site bg white `#ffffff`; secondary/footer bg mint `#b5e3d9` (theme default — our footer uses ink instead; confirm with brand)
- **Type: Gotham only.** Headlines = **Gotham Bold** (700), body/UI = Gotham Medium (400/500). The theme already ships these:
  - Gotham Bold: `Gotham_Bold.woff2`  · Gotham Medium: `Gotham-Medium.woff2`  · Gotham Light: `Gotham-Light_1.woff2` (all on the store's Shopify files CDN, referenced in the theme's font snippets). No serif / no Google fonts.
- Spacing scale: section gap **72px**; hero side padding 20px; rail card gap 2px; rail edge inset 10px.
- Buttons: **square (0 radius)**, uppercase, letter-spacing ~0.16em, ink solid or ink outline.

## Assets (in `assets/`)
- `logo-white.png` — white horizontal wordmark (from theme `WhiteSmoothCoHorizontalLogo.png`), for the ink footer/announcement.
- `logo-black.png` — black wordmark (recolored from white), for the white header.
- `footer-logo.png` — mint wordmark (theme original), if a mint treatment is wanted.
- All product/category/hero/review/founder imagery in the prototype is a **striped grey placeholder** — swap for real brand photography and the muted hero film. Placeholders are labeled in the file.
- Fonts: use the theme's existing Gotham font-face declarations; do not re-upload.

## Files
- `Smooth Homepage.dc.html` — the hi-fi design reference (single file; open in a browser to inspect exact spacing/markup). Ignore the `<x-dc>` / `support.js` wrapper — that's the prototyping runtime, not part of the deliverable. The homepage lives in the `#2b` phone frame; the `#3*`/`#4*` blocks at the top are the add-to-cart exploration board (reference only — final choice is the action-bar "4A" card documented above).

## Notes / open items
- **Reviews component is provisional** pending the reviews-platform audit (Loox / Klaviyo Reviews / Firework UGC are all present in the current theme). Build generic, keep swappable.
- Hero treatment (static vs muted loop vs rotating) and the bestsellers-vs-category order were explored; the shipped direction is **muted loop, text-below, category then bestsellers is NOT used — order is bestsellers then category** as listed above.
- A dae-style "Get the look" (style left / products right) section was discussed for later — not in this scope.
