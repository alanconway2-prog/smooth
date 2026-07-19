# Go-live guide — new homepage

This is written for someone who has **not** used Shopify themes or GitHub much before.
Take it slowly; nothing here touches your live store until the very last step, and
even then only when *you* choose to.

---

## 1. Upload the theme (safe — creates a *new* theme, doesn't change your live one)

1. In the zip I sent you (`smooth-theme-newlayout-v1.zip`), **don't unzip it** — Shopify wants the zip as-is.
2. In Shopify admin go to **Online Store → Themes**.
3. Scroll to the **Theme library** section → **Add theme → Upload zip file** → choose the zip → **Upload file**.
4. It appears in your library as a new, unpublished theme (probably named "newlayout" or similar). Your current live theme is untouched.
5. On the new theme click **… → Preview** to see it, or **Customize** to open the editor.

> If Shopify says the zip isn't valid, make sure you're uploading the file exactly as sent (not a re-zipped folder).

---

## 2. What you'll see straight away

The homepage is fully rebuilt as the new mobile-first design — hero, best-sellers,
categories, press, founder, watch & shop, reviews, and the new ink footer. Out of the
box it shows **grey striped placeholders** where your photos, products and collections
go. That's expected. The next section is how to drop in the real content.

Open `preview.html` (in this folder) in any browser to see the intended look.

---

## 3. Fill in the real content (in **Customize**, no code)

Everything below is done by clicking sections in the theme editor's homepage. Each
section has plain-English settings.

**Header / announcement**
- [ ] The announcement bar already says *"Free delivery on all orders £30+"* on an ink background. Edit it under the **Header** if you want.
- [ ] **Logo:** the header wants the **black** wordmark on white. In **Header → Logo image**, upload `sc-logo-black.png` (it's bundled in the theme's Assets, or use your own black logo). *This is the one thing that needs your click — image settings can't be pre-filled from a file.*

**Hero**
- [ ] Add your **hero video** (muted brand film) and a **poster image** for first paint. No video? Just set a poster image.
- [ ] Edit the rating line, heading, subcopy and button link.

**Best sellers rail**
- [ ] It has 3 tabs (**Best sellers / New in / Bundles**). For each tab, pick the **collection** it should show. (Tab 1 currently points at your "all" collection so you see real products immediately.)
- [ ] Product cards can show three extras via **product metafields** (optional but recommended):
  - `custom.cutline` — the little grey descriptor line (e.g. "Frizz + flyaways, on the go")
  - `custom.review_count` — the number in `(312)`
  - `custom.badge` — the top-left label (e.g. "Bestseller", "New")
  - Sale price + "Save £X" appear automatically when a product has a compare-at price.
  - *(Set metafields under Shopify **Settings → Custom data → Products**. If you skip these, the cards still look right — they just omit those lines.)*

**Shop by category**
- [ ] For each of the 5 tiles pick a **collection** (label + image come from the collection, or override per tile).

**Press band**
- [ ] Edit the press names or swap them for logo images, and edit the caption.

**Founder story**
- [ ] Add the founder **portrait image**, edit the quote, and point the button at your story page.

**Watch & shop**
- [ ] For each tile add a **9:16 video** (and/or a poster image) and link it to the product.

**Reviews** *(provisional)*
- [ ] This is a strong generic block for now. Once you've chosen a reviews app (Loox / Klaviyo / Firework), it can be swapped to pull real reviews. Until then, edit the sample cards or hide the section.

**Footer**
- [ ] The three columns (**Shop / Learn / Help**) are wired to your existing footer menus (`footer-1/3/4`). Re-point them to the right menus under each **Menu column**, and edit the newsletter text. The white wordmark is bundled; upload your own if you prefer.

---

## 4. Go live (when you're happy)

On the new theme in **Online Store → Themes**: **… → Publish**. That makes it your
live theme. You can always re-publish the previous theme to roll back.

---

## Things worth knowing

- **Add to cart** on the product cards adds the item and opens your cart drawer (falls back to the cart page if the drawer isn't enabled). Test it once in preview.
- **The old homepage** used PageFly + Zellor page-builder sections. The new one is 100% native theme sections — easier to edit and faster. The old sections still exist in the theme (unused) if you ever need them.
- **Header, announcement and footer are site-wide** (they show on every page), so those changes affect the whole store, not just the homepage — that's normal.
- If something looks off, it's almost always a section setting in **Customize** — nothing here is hard-coded that you can't change there.

## For later: keeping GitHub in sync (optional)

Right now GitHub just holds a safe copy of the theme. If you want changes to flow
automatically from GitHub into Shopify in future, connect them once:
**Online Store → Themes → Add theme → Connect from GitHub**, and pick this repo +
branch. Then you never need to upload a zip again. Ask me and I'll walk you through it.
