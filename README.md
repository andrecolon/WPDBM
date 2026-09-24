# WPDBM — Dream Book Marketing, One-Page Site

Build target: a single-page WordPress + Elementor site for Dream Book Marketing (DBM),
implemented from the reference design in `docs/assets/reference-full-page.webp`.

## What's in this repo

- `docs/page-spec.md` — section-by-section build spec (copy, layout, colors, fonts, spacing)
  pulled from the reference design. This is the source of truth for building the page in Elementor.
- `docs/SETUP.md` — how to get from "empty GoDaddy WordPress site" to "Elementor editor
  ready, with an MCP connection wired up." These are host/account actions only you can do.
- `docs/assets/` — reference design screenshot(s).
- `elementor-templates/` — exported Elementor Template Kit JSON goes here once the page is
  built, so the layout is versioned and re-importable (not just living in the site's database).

## Why a repo for an Elementor site at all

Elementor stores a page's layout as serialized JSON in the WordPress database — there's no
source file to normally check into git. This repo exists so that JSON (exported as an
Elementor Template Kit / template file) and the design decisions behind it are versioned,
diffable, and portable to a new host if you ever leave GoDaddy.

## Status

Environment: WordPress hosted on GoDaddy (Managed WordPress or similar, no cPanel).
See `docs/SETUP.md` for the exact steps and open questions before real build work can start
against the live/staging site.
