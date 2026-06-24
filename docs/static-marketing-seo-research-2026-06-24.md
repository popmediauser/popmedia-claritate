# Static Marketing / SEO Research Notes

Date: 2026-06-24
Scope: Pop Media static homepage, Vercel-friendly, no backend.

## Operating Decision

Keep the public demo static for now. Use the static site for presentation, sponsor clarity, contact intent, and SEO basics. Keep Laravel as the future application path for accounts, dashboards, saved forms, payments, or admin workflows.

## Source Grading

- Tier 1 / official: Google Search Central, Vercel docs, Schema.org, W3C/WCAG, EDPB.
- Tier 1 / public data: Statbel, Statistics Flanders.
- Tier 2/3 context: Nielsen Norman Group, Reuters Institute, DataReportal, Radiocentre.
- Rule: do not use unverified audience numbers, sponsor logos, or business claims.

## Marketing Findings

1. First screen should speak to two audiences:
   - community/listeners;
   - local sponsors/businesses.
   Proposed plain promise: `Radio si comunitate pentru romanii din Belgia. Promovare locala pentru afaceri care vor sa fie cunoscute.`
   Sources: https://www.nngroup.com/articles/homepage-design-principles/, https://www.nngroup.com/articles/how-long-do-users-stay-on-web-pages/

2. Hero CTAs should be split by intent:
   - primary sponsor CTA: `Vreau promovare pentru afacerea mea`;
   - secondary listener CTA: `Asculta Radio Belgia`.
   Avoid vague CTA-only language such as `Colaboreaza`.
   Sources: https://www.w3.org/WAI/WCAG21/Understanding/link-purpose-in-context, https://www.nngroup.com/articles/get-started/

3. Add a small proof/context strip without fake metrics:
   - `Romani in Belgia`;
   - `Radio + podcast + evenimente`;
   - `Contact direct in Belgia`.
   Sources: https://statbel.fgov.be/en/themes/population/population-movement/migration, https://www.vlaanderen.be/en/statistics-flanders/population/population-by-nationality

4. Rename sponsor packages by outcome, not tier labels:
   - `Vizibilitate locala`;
   - `Interviu + continut`;
   - `Partener de comunitate`.
   Source: https://statbel.fgov.be/en/themes/enterprises/vat-registered-businesses/vat-registered-enterprises

5. Show concrete sponsor deliverables:
   - radio mentions;
   - interview/podcast;
   - social clips;
   - event visibility;
   - monthly recap;
   - contact handoff.
   Sources: https://www.nngroup.com/articles/trustworthy-design/, https://www.radiocentre.org/our-research/the-radio-multiplier-study-ad-awareness/

6. Keep static contact explicit:
   - use prefilled mailto links;
   - no fake form that pretends to submit;
   - optional WhatsApp/phone only if confirmed.
   Sources: https://www.edpb.europa.eu/sme-data-protection-guide/data-protection-basics_en, https://www.nngroup.com/articles/contact-us-pages/

7. Add a collaboration process before/near sponsor packages:
   - choose objective;
   - produce message/content;
   - publish/distribute;
   - send recap.
   Source: https://www.nngroup.com/articles/commitment-levels/

8. Use digital/social as support for radio, not a separate unsupported promise.
   Sources: https://datareportal.com/reports/digital-2026-belgium, https://reutersinstitute.politics.ox.ac.uk/digital-news-report/2026/belgium

9. Add sponsor verticals that recognize themselves:
   - restaurante;
   - constructii;
   - transport;
   - contabilitate;
   - juridic;
   - magazine romanesti;
   - evenimente;
   - servicii pentru nou-veniti.

10. Recommended content order:
    - hero promise;
    - proof/context strip;
    - services/community;
    - sponsor offer;
    - content channels;
    - contact.

## SEO Findings

1. Confirm one canonical production URL before final public SEO:
   - same URL in `canonical`, `og:url`, JSON-LD, and `sitemap.xml`.
   Current safe assumption for this static demo: `https://popmedia-homepage.vercel.app/`.
   Sources: https://developers.google.com/search/docs/crawling-indexing/consolidate-duplicate-urls, https://developers.google.com/search/docs/crawling-indexing/sitemaps/build-sitemap

2. Tighten static head metadata:
   - one descriptive title;
   - one human meta description;
   - no `meta keywords`.
   Sources: https://developers.google.com/search/docs/appearance/title-link, https://developers.google.com/search/docs/appearance/snippet, https://developers.google.com/search/docs/crawling-indexing/special-tags

3. Add social preview metadata:
   - `og:title`;
   - `og:description`;
   - `og:type=website`;
   - `og:url`;
   - `og:site_name`;
   - `og:locale`;
   - absolute `og:image`.
   Sources: https://ogp.me/, https://developers.google.com/search/docs/appearance/google-images

4. Add `sitemap.xml` and update `robots.txt`:
   - one-page sitemap is enough for now;
   - include sitemap URL in robots.
   Sources: https://developers.google.com/search/docs/crawling-indexing/sitemaps/build-sitemap, https://developers.google.com/search/docs/crawling-indexing/robots/intro

5. Add minimal JSON-LD now:
   - `WebSite` is safe;
   - `Organization` / `RadioBroadcastService` only with visible, verified details.
   Sources: https://developers.google.com/search/docs/appearance/site-names, https://developers.google.com/search/docs/appearance/structured-data/intro-structured-data, https://schema.org/WebSite, https://schema.org/RadioBroadcastService

6. Language:
   - keep `html lang="ro"`;
   - skip `hreflang` until there are separate translated pages.
   Sources: https://developers.google.com/search/docs/specialty/international/localized-versions, https://www.w3.org/TR/WCAG22/

7. Accessibility and performance:
   - meaningful images need useful text nearby or `alt`;
   - decorative images can stay decorative;
   - keep JS small;
   - protect LCP/CLS/INP;
   - verify mobile.
   Sources: https://developers.google.com/search/docs/appearance/google-images, https://developers.google.com/search/docs/appearance/core-web-vitals, https://web.dev/articles/vitals

## Visual / IA Audit Findings

- Do not insert content inside `.hero-stage`; it controls sticky scroll and wave timing.
- Preserve the loud, rectangular, radio/editorial identity.
- Prefer bands, rails, signal strips, timelines, and process rows over generic rounded cards.
- Avoid duplicate IDs: current `#podcasts` and `#evenimente` are service-card anchors.
- Add mobile rules for every new section.

## First Implementation Slice

Implement locally on branch `codex/static-clarity-foundation-20260624`:

1. Update hero copy and CTAs while preserving layout.
2. Add a context/proof strip after the hero/services boundary without changing hero internals.
3. Reframe sponsor packages by outcome.
4. Add a static `Cum lucram` process strip.
5. Add richer static contact CTAs with prefilled mailto links.
6. Add SEO head metadata, `robots.txt`, and `sitemap.xml`.
7. Verify desktop/mobile locally.

## Avoid

- No fake listener counts, sponsor results, testimonials, logos, or `#1` claims.
- No fake submit form.
- No backend-like UI that suggests accounts, dashboards, or saved requests.
- No deploy or provider setting change without approval.
