# The Smooth Company — theme (clean rebuild on Dawn)

A clean, blank-canvas rebuild of the storefront on **Shopify Dawn v15.5** — no PageFly /
Zellor / wholesale-lock baggage from the old Tailor theme (which caused the desktop
right-shift and random section gaps). The Claude Design "10A" homepage is built as native
Liquid sections on top.

## Layout
| Path | What it is |
|------|-----------|
| `layout/`, `sections/`, `snippets/`, `templates/`, `assets/`, `config/`, `locales/` | The theme (clean Dawn base). |
| `sections/sc-*.liquid` | Our custom homepage sections (hero, best-sellers, editorial, press, statement, category, shoppable reels, reviews, footer). |
| `snippets/sc-product-card.liquid` | The 10A product card (mint badge, plus-circle add, portrait/square, sale price). |
| `design/homepage/` | Design reference (prototype + brief). Shopify ignores it. |

## Homepage
`templates/index.json` composes the sc- sections in the 10A scroll order:
hero → best sellers → editorial banner → press → statement → category → shoppable reels → reviews.
Every section is editable/hideable in **Customize** (colours, spacing, alignment, images, etc.).

## Type
Gotham (Bold / Medium / Light) is loaded from the store's Shopify CDN in `layout/theme.liquid`
and set as the theme's heading/body fonts.

## Deploy
Upload the zip in Shopify (*Online Store → Themes → Add theme → Upload zip*) as a **new draft**,
preview, then publish when happy. Your live theme is untouched until you publish.
The other pages (product, collection, cart, search) use Dawn's clean defaults for now — we
style those next.
