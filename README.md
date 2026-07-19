# The Smooth Company — Shopify theme

This repository holds the **Tailor** Shopify theme for [thesmoothcompany.com](https://www.thesmoothcompany.com)
under version control, so changes can be reviewed before they go live on the store.

## Repository layout

| Path | What it is |
|------|-----------|
| `assets/`, `config/`, `layout/`, `locales/`, `sections/`, `snippets/`, `templates/` | The Shopify theme itself. These are the folders Shopify expects at the repo root. |
| `design/homepage/` | **Reference only.** The homepage redesign handoff (design prototype + notes). Shopify ignores this folder; it is here so the design brief travels with the code. |

## Current work

Rebuilding the homepage (`templates/index.json`) as native Liquid sections per the
brief in [`design/homepage/README.md`](design/homepage/README.md) — moving off the
PageFly/Zellor page-builder sections and onto the theme's own sections.

## How this connects to the live store

Two ways to get changes from here onto the store:

1. **Download a zip** of the theme and upload it in Shopify admin
   (*Online Store → Themes → Add theme → Upload zip file*). Good for a one-off handover.
2. **Shopify GitHub integration** (recommended) — connect this repo to a theme in
   *Online Store → Themes → Add theme → Connect from GitHub*. Shopify then keeps that
   theme in sync with a chosen branch automatically. Work happens on a branch, gets
   reviewed, then merges.

Either way, always add a redesign as a **new/duplicate theme** first and preview it —
never edit the live theme directly.
