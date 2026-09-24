# Elementor templates

Empty until the page is built. Once the one-pager is assembled in the Elementor editor:

1. `Elementor → Templates → Saved Templates → Export` the page (or use "Save as Template" on
   the page first, then export that template) — this produces a `.json` file.
2. Drop the exported `.json` here, named for the section or page it represents
   (e.g. `dbm-onepager-full.json`).
3. Commit it. This gives us a portable, diffable copy of the layout independent of the
   WordPress database — re-importable into any Elementor site via
   `Templates → Saved Templates → Import Templates`.

If the build ends up needing custom CSS beyond what Elementor's UI panels cover, put it in a
sibling `custom.css` here (referencing which section it applies to) rather than pasting into
Elementor's global custom CSS field with no record of it.
