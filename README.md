# The Smooth Company — theme (Tailor base + 10A homepage)

Built on the **Tailor** premium theme (a clean, app-free export — no PageFly / Zellor /
wholesale-lock baggage, which is what previously caused the desktop shift and the "random
gaps" from `spacer` sections). Tailor's premium cart drawer and features are kept; the
Claude Design "10A" homepage is layered on as native sections.

## Layout
| Path | What it is |
|------|-----------|
| `layout/`, `sections/`, `snippets/`, `templates/`, `assets/`, `config/`, `locales/`, `blocks/` | The Tailor theme. |
| `sections/sc-*.liquid` | Our homepage sections (hero, best-sellers, editorial, press, statement, category, shoppable reels, reviews, footer). |
| `snippets/sc-product-card.liquid` | The 10A product card. |
| `assets/custom.css` | Gotham web-fonts + base type (Bold / Medium / Light from the store CDN). |
| `design/homepage/` | Design reference. Shopify ignores it. |

## Homepage
`templates/index.json` = the 10A order: hero → best sellers → editorial → press →
statement → category → shoppable reels → reviews. All editable/hideable in Customize.
Header/announcement/footer are configured in `sections/header-group.json` and
`sections/footer-group.json` (single ink announcement, sticky white header centred logo,
the designed `sc-footer`).

## Deploy
Upload the zip in Shopify (*Online Store → Themes → Add theme → Upload zip*) as a **new
draft**, preview, then publish. Set your logo + menus in Customize. Product/collection/cart
pages use Tailor's premium defaults; we restyle those next.
