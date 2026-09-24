# Setup: GoDaddy WordPress + Elementor + MCP

Your environment: **WordPress hosted on GoDaddy, not on a dedicated/managed WP plan with cPanel.**
That most likely means GoDaddy's own "Managed WordPress" product, which uses GoDaddy's own
hosting dashboard instead of cPanel. Everything below is written for that case — flag it if
you're actually on GoDaddy shared/cPanel hosting with WP installed manually, since a couple of
steps differ (mainly: no built-in staging, and you'd use cPanel's own tools instead of GoDaddy's
hosting dashboard).

None of these steps can be done from this session — they require your GoDaddy login and your
WordPress admin login, neither of which I have. This is the checklist to work through on your
end; ping me with the results (or if a step doesn't look like what's described) and I'll adjust.

## 1. Confirm the WordPress site and plan tier

- [ ] Log into GoDaddy → confirm the exact product (Managed WordPress Basic / Deluxe / Ultimate /
      Business, or "Web Hosting Plus" with WP installed manually).
- [ ] Note the site's admin URL (`https://yourdomain.com/wp-admin`) and confirm you can log in.
- [ ] Check whether a **staging site** is available (GoDaddy's Managed WordPress dashboard has a
      "Staging" tab on mid/upper tiers — one click to create a staging copy). If available, **build
      there first**, not on the live site — then push staging → production when the page is done.
      If your tier doesn't include staging, say so and we'll plan around building directly on
      production during low-traffic hours, or spinning up a temporary throwaway WP site to build
      against instead.

## 2. Install and activate Elementor

- [ ] In `wp-admin → Plugins → Add New`, search "Elementor," install and activate.
- [ ] The free version covers everything in this design (sections/columns, no Theme Builder
      widgets are required for a one-pager like this). Skip Elementor Pro unless you already have
      a license.
- [ ] If plugin installation is greyed out or blocked, your GoDaddy plan may restrict it — that
      usually means either upgrading the plan or asking GoDaddy support to unlock it.

## 3. Set global design tokens in Elementor (once installed)

Under `Elementor → Site Settings → Global Colors` and `Global Fonts`, set up the palette and
type scale documented in `docs/page-spec.md` so every section pulls from the same source instead
of one-off hex values per widget. Details are in that file — do this before building sections.

## 4. Enable an API credential for MCP access

WordPress's built-in **Application Passwords** feature (core since WP 5.6, no plugin needed)
is the standard way to let an external tool authenticate to the REST API. It works on GoDaddy
Managed WordPress as long as the site is HTTPS (it will be, by default).

- [ ] Recommended: create a dedicated WP user (e.g. `mcp-agent`) with the **Editor** role rather
      than using your main admin account — least-privilege, and easy to revoke later.
- [ ] Log in as that user → `Users → Profile → Application Passwords` → generate one, name it
      something like "Claude MCP". Copy the generated password immediately (shown once).
- [ ] **Do not commit this anywhere in this repo or paste it into chat.** It's a credential for
      whatever MCP connector setup you do outside this session.
- [ ] Sanity check the REST API is actually reachable and not blocked by a GoDaddy firewall/
      security plugin: visit `https://yourdomain.com/wp-json/` in a browser — you should get a
      JSON response, not a 403 or a GoDaddy block page. If it's blocked, that's a GoDaddy
      support ticket ("please allow REST API / wp-json access") before an MCP connector can work.

## 5. Connect a WordPress MCP server

This Claude Code session currently has **no WordPress or Elementor MCP server connected** — I
checked the connector registry and only found a "WordPress.com" connector (for WordPress.com-
hosted sites specifically, not applicable to a self-hosted GoDaddy install), and it isn't
installed either.

For a self-hosted site like yours, the path is a WordPress REST API MCP server (e.g. a plugin
exposing an endpoint like `/wp-json/<namespace>/mcp/`) authenticated with the Application
Password from step 4, added as a **custom connector**:

- [ ] Go to **https://claude.ai/customize/connectors** and add a custom connector — name it,
      point it at the site's MCP endpoint URL, and set the auth header (`Authorization: Basic
      <base64 of username:password>`, from the Application Password generated in step 4).
- [ ] **Use HTTPS, not HTTP**, for the endpoint URL. Basic Auth only base64-encodes the
      credentials (trivially reversible) — over plain HTTP the Application Password travels in
      cleartext to anything on the network path. If the site/endpoint is only reachable over
      `http://` right now, fix that before connecting it (GoDaddy sites get HTTPS by default;
      a temp/staging subdomain may need its own cert or may not support HTTPS yet — check).
- [ ] Connectors are only read when a **session starts** — after adding it, start a **new**
      Claude Code session rather than expecting an existing one to pick it up mid-conversation.
- [ ] This is an account-level action — I can't add the connector or edit its config myself
      from inside a sandboxed session (editing a local config file like `~/.claude.json` inside
      this container doesn't do it; that's not how connectors are wired up for cloud sessions).
- [ ] Treat any Application Password that's ever been pasted into a chat, doc, or ticket as
      burned — revoke it (`Users → Profile → Application Passwords`) and generate a fresh one
      once the endpoint is on HTTPS.

Important scope limit to set expectations correctly: a WordPress REST API MCP server can manage
**posts/pages, media, custom fields, and site settings** — it does **not** give clean control
over Elementor's internal layout (Elementor stores a page's section/column/widget tree as one
large JSON blob in post meta; editing that safely from outside the Elementor editor is fragile).
So the realistic workflow is:

- MCP handles: creating the page, uploading media (logo, headshot, icons), setting the page's
  slug/menu placement, and any custom CSS if needed.
- The actual Elementor section layout gets built by hand in the visual editor, using
  `docs/page-spec.md` as the exact blueprint — or by importing an Elementor Template Kit export
  once one exists (see `elementor-templates/`).

## 6. Assets still needed

The only source material so far is the full-page reference screenshot
(`docs/assets/reference-full-page.webp`). For a pixel-accurate build, these should come from you
rather than being cropped/guessed from the screenshot:

- [ ] DBM logo (vector/SVG or high-res PNG, not a screenshot crop)
- [ ] Darcy Hughes headshot (original file)
- [ ] Exact brand hex codes and font files/licenses, if a brand guide exists — otherwise
      `docs/page-spec.md` uses close estimates pulled from the screenshot, flagged as such
- [ ] The exact domain/URL this page will live on (root `/` as a new one-pager, or a specific
      slug on an existing site?)

## Once the above is done

Tell me: the staging/site URL, whether Application Passwords + REST API are working, and
whether a WordPress MCP connector is connected on your end. At that point I can either work
directly against the site through that connector, or hand you a step-by-step Elementor build
sequence section-by-section from `docs/page-spec.md` for you to execute in the editor.
