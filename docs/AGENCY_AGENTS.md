# Agency Agents

`.claude/agents/` carries a trimmed subset of the [Agency Agents](https://github.com/msitarzewski/agency-agents)
subagent roster (MIT licensed), installed and cut down for **this repo** —
not copied from any other project's trim.

- **Source**: `msitarzewski/agency-agents`, commit `6d29a9b08785a0e49ffc9818bbdd381164c2df5f` (2026-09-08)
- **License**: MIT
- **Trimmed**: 2026-09-09
- **Kept**: 17 of 279 agents the installer produced for this source commit
  (the project's own docs still describe the roster as "273" — it has grown since)

## What this repo actually is

`oxygens-website` is a static marketing site for Oxygen Students Paradise, a
printing/binding/scanning/DTP and student-services shop in Triprayar,
Thrissur (the same business Printosky runs job/billing software for). Confirmed
by reading the code, not assumed:

- **No framework, no backend, no build step.** The whole site is `index.html`
  (plus three superseded iterations, `index_V1.html`–`index_V3.html`, and
  `privacy.html`) — hand-written HTML with inline `<style>`/`<script>`, zero
  external CSS/JS files, zero `<img>` tags (all visuals are CSS/emoji, no
  photography pipeline). No `package.json`, no `.github/workflows`, no CI.
- **Deployed as GitHub Pages** — a bare `CNAME` file pointing at
  `www.oxygens.in` is the entire deployment config.
- **SEO/schema-heavy**: full Open Graph + Twitter Card meta, and two
  `application/ld+json` blocks (`LocalBusiness` + `Service` with an
  `OfferCatalog` of binding/printing services). No `robots.txt`, `sitemap.xml`,
  or `llms.txt` exist yet, despite the JSON-LD foundation already being there.
- **Tracked**: Google Tag Manager (`GTM-KRT6G3X4`) *and* GA4 (`gtag`, ID
  `G-LKC2WHTC15`) both wired in, with `gtag('event', 'click', ...)` firing on
  every WhatsApp/phone CTA. No ad pixels (no Meta Pixel, no Google Ads
  conversion tag) — this is organic + WhatsApp, not a paid-media operation.
- **Social**: linked to a live Facebook page and Instagram
  (`instagram.com/oxygenstudentsparadise`).
- **No forms, no database, no auth, no payment integration on this site** —
  ordering happens by clicking out to `wa.me` (WhatsApp) or `tel:`/`mailto:`
  links. Razorpay/print-job logic lives in Printosky, not here.
- **Zero accessibility attributes** (`grep -c "aria-"` → 0) on a public local-
  business page — a real, concrete gap.
- **Services actually advertised**: thesis/project binding, document
  printing, scanning, DTP, lamination, CV writing, and — notably — passport
  applications, PSC registration, and university registration ("academic
  prep / study-help" services, not just a copy shop).
- **A privacy policy page exists** (`privacy.html`) and needs to stay accurate
  as a real legal artifact, however small.

Given that, the right roster looks nothing like Printosky's 87-agent,
engineering-heavy trim. This is a front-end/marketing-weighted set with
almost no engineering, no security, no product/PM, and no finance — because
none of those disciplines have real work to do against a framework-less,
backend-less static page with no user data pipeline.

## Kept — 17 agents

### Design (6)
The only division with real design-system surface: the page has custom CSS
variables (`--primary`, `--font-display`, `--font-body`), hand-tuned
responsive breakpoints, and three superseded full rewrites (`_V1`–`_V3`),
which means active visual/messaging iteration is the norm here, not a
hypothetical.

- **UI Designer** — the CSS design tokens and component patterns
  (`.service-card`, `.btn`, `.trust-feature`) are exactly its remit.
- **UX Architect** — "developer-friendly foundations, implementation
  guidance" for the actual hand-rolled CSS system (media queries, custom
  properties) this site runs on.
- **Brand Guardian** — three prior full rewrites of the homepage is evidence
  of active brand/positioning churn (headline moved from "Document Printing
  & Binding" to "Fast Printing & Binding" + added government-services
  angle); consistency across iterations is a real, recurring need.
- **Persona Walkthrough Specialist** — this is a single long scrolling page
  designed to convert a visitor into a WhatsApp message; simulating a
  student's reaction at each scroll position is directly useful and there's
  no A/B infrastructure to do it any other way.
- **Image Prompt Engineer** — the meta tags already *reference* `og-image.jpg`,
  `twitter-card.jpg`, and `logo.jpg`, but the repo contains zero image files.
  Those need to exist; this agent is for generating them.
- **UI Finish-Gate Reviewer** — the page follows a very recognizable
  local-business-template shape (hero/CTA/services/testimonials/location/
  footer); this agent's whole job is catching exactly that kind of
  interchangeable-feeling UI before it ships.

Cut: UX Researcher (no user-testing program or infra exists — Persona
Walkthrough covers the realistic need), Visual Storyteller (no photography
or video content on the page to tell a story with), Whimsy Injector (a
pragmatic local-services page for students booking print jobs isn't the
place for micro-interaction delight work), Inclusive Visuals Specialist (no
AI-generated imagery pipeline exists to review).

### Marketing (4)
- **SEO Specialist** — technical SEO is already half-built (meta keywords,
  OG/Twitter tags, dual JSON-LD schema) and needs someone who understands
  that surface to extend it (sitemap, internal linking, content depth).
- **Content Creator** — the on-page copy has been rewritten three times
  already; that's an ongoing job, not a one-off.
- **Social Media Strategist** — the site links a live Facebook page and a
  live Instagram account; cross-platform strategy for those is a real,
  existing asset, not speculative.
- **AEO Foundations Architect** — the site has zero `robots.txt`, `sitemap.xml`,
  or `llms.txt`, despite already having the LocalBusiness/Service JSON-LD
  that makes those worth adding. A concrete, currently-missing piece of
  infrastructure.

Cut: everything China-platform-specific (Xiaohongshu, WeChat, Zhihu, Baidu,
Bilibili, Kuaishou, Douyin, Weibo, cross-border/China e-commerce, Chinese
podcast/livestream agents) — irrelevant to a Kerala local business, full
stop. Also cut: Growth Hacker, Email Marketing Strategist (no email capture
or CRM anywhere on the site), App Store Optimizer (no app), Twitter/X
agents, TikTok Strategist, LinkedIn Content Creator (this is B2C local
services, not B2B thought leadership), PR & Communications Manager (a
one-location print shop doesn't need crisis comms), Book Co-Author, Video
Optimization Specialist (no YouTube presence), Agentic Search Optimizer
(too speculative for a page with no APIs), AI Citation Strategist
(overlaps AEO Foundations Architect without a distinct enough job here).

### Paid Media (1 of 7)
- **Tracking & Measurement Specialist** — GTM and GA4 are *already* live in
  `index.html`, with custom click events on every WhatsApp/phone CTA. That's
  a real, existing tracking implementation that needs a specialist, even
  though nothing else in this division applies.

Cut the rest of the division outright: no ad pixel, no Google Ads
conversion tag, and no evidence of any paid campaign anywhere in the repo —
PPC Strategist, Search Query Analyst, Paid Media Auditor, Ad Creative
Strategist, Programmatic/Display Buyer, and Paid Social Strategist would all
be managing campaigns that don't exist.

### Testing (3 of 9)
- **Accessibility Auditor** — `aria-` attributes: zero, on a live public
  local-business page. That's not hypothetical, it's measured.
- **Performance Benchmarker** — the whole site is one ~53KB inline-everything
  HTML file; Core Web Vitals on that file directly affects local SEO
  ranking, which this business is actively investing in (see the JSON-LD).
- **Evidence Collector** — three rewritten homepage versions already exist;
  screenshot-based before/after evidence is exactly how the next iteration
  should be validated.

Cut the rest: no API (API Tester), no test suite or interactive flows worth
automating (Test Automation Engineer — it's link-outs to `wa.me`/`tel:`, not
an app), and the remaining agents (Reality Checker, Test Results Analyzer,
Tool Evaluator, Workflow Optimizer) are generic process agents with nothing
concrete in this repo to attach to.

### Support (2 of 6)
- **Legal Compliance Checker** — `privacy.html` is a real, shipped legal
  page that needs to stay accurate as the business (and Indian data-privacy
  expectations) change.
- **Analytics Reporter** — turns the GTM/GA4 data already being collected
  into actual dashboards/insights, complementing the Tracking &
  Measurement Specialist's implementation work.

Cut: Support Responder and Finance Tracker are day-to-day operational roles
that belong to Printosky (the actual print-shop app with a live queue and
billing), not a static marketing page. Infrastructure Maintainer has nothing
to maintain (GitHub Pages + a CNAME file is the entire "infra"). Executive
Summary Generator has no operating cadence here to summarize.

### Specialized (1 of 100+)
- **Study Abroad Advisor** — the site's own meta keywords list "passport
  applications," "PSC registration," and "university registration" as
  advertised services. This isn't just a copy shop; it's explicitly an
  academic-prep/study-help business, and this agent maps directly onto that
  stated service line.

Everything else in this large, grab-bag division was cut: it's dominated by
verticals (legal, healthcare, real estate, hospitality, HR, loan
origination, French/Korean market navigation, civil engineering, etc.) with
no footprint in this repo at all.

## Cut entirely (whole divisions)

- **Engineering** — every agent in this division is scoped to a stack that
  isn't here: React/Vue/Angular (Frontend Developer is explicitly framework
  work), a backend, a database, mobile, DevOps/CI (there's no
  `.github/workflows` at all), a CMS, i18n, embedded, blockchain, or a
  federal-508/USWDS government context. This repo is hand-written static
  HTML/CSS/inline-JS with no build step; nothing in Engineering actually
  fits, so nothing was force-fit. General accessibility is covered instead
  by Testing's Accessibility Auditor.
- **Product** — Sprint Prioritizer, Product Manager, Feedback Synthesizer,
  etc. assume a software product with a backlog and a feedback loop. A
  single static marketing page has neither.
- **Project Management** — no Jira, no sprints, no multi-workstream
  coordination; this is effectively a single-file repo.
- **Security** — no backend, no auth, no user input, no secrets, no attack
  surface beyond static hosting. The entire division targets application-
  level or infrastructure-level security work that doesn't exist here.
- **Finance** — no billing, invoicing, or financial modeling in this repo
  (that's Printosky's domain — Razorpay webhooks and daily revenue live
  there, not on the marketing site).
- **Game Development, GIS, Healthcare, Spatial Computing, Academic,
  Research** — no fit whatsoever. Academic in particular is scholarly
  world-building/narrative-fiction tooling (anthropologist, historian,
  narratologist for game/story settings) — not applicable to a real local
  business's real website, despite the name being easy to confuse with
  "academic prep services."
- **Sales** — this is a walk-in/WhatsApp local-services shop, not an
  outbound B2B sales motion; nothing here runs a pipeline, drafts RFP
  responses, or does MEDDPICC deal scoring.

## Re-installing the full roster

To get all 279 agents back (or re-run the trim differently):

```bash
git clone --depth 1 https://github.com/msitarzewski/agency-agents.git /tmp/agency-agents-src
CLAUDE_CONFIG_DIR=$(pwd)/.claude /tmp/agency-agents-src/scripts/install.sh --tool claude-code --no-interactive
```

That overwrites `.claude/agents/` with the full set; re-delete down to the
list above (or a new one) as needed.
