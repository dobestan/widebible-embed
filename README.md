# widebible-embed

[![npm](https://img.shields.io/npm/v/widebible-embed)](https://www.npmjs.com/package/widebible-embed)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Zero Dependencies](https://img.shields.io/badge/dependencies-0-brightgreen)](https://www.npmjs.com/package/widebible-embed)
[![Size](https://img.shields.io/badge/size-~5KB-green)](https://bundlephobia.com/package/widebible-embed)

Embed WideBible scripture widgets on any website. **Zero dependencies**, Shadow DOM style isolation, 3 built-in themes (light, dark, sepia), and automatic daily verse updates. Each widget includes a "Powered by WideBible" backlink.

WideBible covers **66 books** (39 Old Testament, 27 New Testament), **31,102 verses**, 4 English translations (KJV, ASV, BBE, YLT), **1,833 biblical people**, **942 biblical places**, and **432,000+ cross-references** — all accessible via free public API with CORS enabled for any origin.

> **Try the interactive widget builder at [widget.widebible.com](https://widget.widebible.com)**

<p align="center">
  <img src="demo.gif" alt="widebible-embed demo — Bible verse widget with KJV, ASV, BBE translations and light/dark/sepia themes" width="800">
</p>

## Table of Contents

- [Quick Start](#quick-start)
- [What You Can Do](#what-you-can-do)
  - [Verse Card — Single Bible Verse Display](#verse-card--single-bible-verse-display)
  - [Chapter Card — Full Chapter with Navigation](#chapter-card--full-chapter-with-navigation)
  - [Person Card — Biblical Figure Profile](#person-card--biblical-figure-profile)
  - [Comparison Card — Side-by-Side Verse Comparison](#comparison-card--side-by-side-verse-comparison)
  - [Verse of the Day — Auto-Updating Daily Widget](#verse-of-the-day--auto-updating-daily-widget)
  - [Search Box — Full-Text Bible Search](#search-box--full-text-bible-search)
- [Widget Options](#widget-options)
- [Themes](#themes)
- [CDN Options](#cdn-options)
- [Technical Details](#technical-details)
- [Learn More About the Bible](#learn-more-about-the-bible)
- [WideHoly Scripture Family](#wideholy-scripture-family)
- [License](#license)

## Quick Start

```html
<!-- Place widget div where you want it to appear -->
<div data-widebible="verse" data-ref="John 3:16" data-theme="light"></div>

<!-- Load the embed script once, anywhere on the page -->
<script src="https://cdn.jsdelivr.net/npm/widebible-embed@1/dist/embed.min.js"></script>
```

That's it. The widget loads, fetches the verse from the WideBible API, and renders it with full style isolation. No configuration files, no build step.

## What You Can Do

The Bible contains 66 canonical books written across roughly 1,500 years in three languages — Hebrew, Aramaic, and Greek. WideBible makes every verse, chapter, person, and place queryable through a structured API, enabling developers to embed rich scripture content with a single HTML attribute.

### Verse Card — Single Bible Verse Display

A Verse Card renders a single verse reference with translation name, book context, and optional original-language text. The default translation is KJV (King James Version, 1611), the most widely cited English Bible. Other supported translations: ASV (American Standard Version, 1901), BBE (Bible in Basic English, 1949), YLT (Young's Literal Translation, 1862).

| Translation | Code | Style | Year |
|-------------|------|-------|------|
| King James Version | `kjv` | Traditional, formal | 1611 |
| American Standard Version | `asv` | Literal, scholarly | 1901 |
| Bible in Basic English | `bbe` | Simplified vocabulary | 1949 |
| Young's Literal Translation | `ylt` | Woodenly literal | 1862 |

```html
<!-- John 3:16 in KJV (default) -->
<div data-widebible="verse"
  data-ref="John 3:16"
  data-theme="light">
</div>

<!-- Psalm 23:1 with Hebrew original text -->
<div data-widebible="verse"
  data-ref="Psalm 23:1"
  data-translation="kjv"
  data-show-original="true"
  data-theme="sepia">
</div>

<!-- Romans 8:28 in BBE, compact size for sidebar -->
<div data-widebible="verse"
  data-ref="Romans 8:28"
  data-translation="bbe"
  data-size="compact"
  data-theme="dark">
</div>

<script src="https://cdn.jsdelivr.net/npm/widebible-embed@1/dist/embed.min.js"></script>
```

**Available options for Verse Card:**

| Attribute | Values | Default |
|-----------|--------|---------|
| `data-ref` | "Book Chapter:Verse" e.g. `John 3:16` | required |
| `data-translation` | `kjv`, `asv`, `bbe`, `ylt` | `kjv` |
| `data-show-original` | `true`, `false` | `false` |
| `data-theme` | `light`, `dark`, `sepia` | `light` |
| `data-size` | `default`, `compact` | `default` |

Learn more: [Bible Verse Lookup — widebible.com](https://widebible.com) · [KJV Translation Guide](https://widebible.com/translations/kjv/) · [Bible Books Reference](https://widebible.com/books/)

### Chapter Card — Full Chapter with Navigation

A Chapter Card renders all verses in a chapter with previous/next navigation. Ideal for study pages, devotional sites, or any context where readers want to read extended passages.

The Bible's 1,189 chapters range from a single verse (Psalm 117) to 176 verses (Psalm 119). Chapter Cards adapt their layout automatically — compact books like Obadiah (21 verses) display inline, while longer chapters like Numbers 7 (89 verses) render in a scrollable container.

```html
<!-- Genesis Chapter 1 — The Creation account -->
<div data-widebible="chapter"
  data-ref="Genesis 1"
  data-theme="light">
</div>

<!-- Psalm 23 — The Lord is my shepherd (6 verses) -->
<div data-widebible="chapter"
  data-ref="Psalm 23"
  data-translation="kjv"
  data-theme="sepia">
</div>

<!-- John Chapter 3 — Nicodemus and the new birth (36 verses) -->
<div data-widebible="chapter"
  data-ref="John 3"
  data-show-original="true"
  data-theme="dark">
</div>

<script src="https://cdn.jsdelivr.net/npm/widebible-embed@1/dist/embed.min.js"></script>
```

Learn more: [Browse Bible Chapters — widebible.com/chapters/](https://widebible.com) · [Old Testament Books](https://widebible.com/books/) · [New Testament Books](https://widebible.com/books/)

### Person Card — Biblical Figure Profile

WideBible indexes **1,833 biblical people** — from major figures like Moses, David, and Paul to minor characters who appear in a single genealogy. Each person profile includes first mention, total verse appearances, associated places, and related figures.

```html
<!-- Moses — The Lawgiver (appeared in ~848 verses) -->
<div data-widebible="person"
  data-slug="moses"
  data-theme="light">
</div>

<!-- King David — Shepherd, warrior, psalmist (appeared in ~1,118 verses) -->
<div data-widebible="person"
  data-slug="david"
  data-theme="sepia">
</div>

<!-- Apostle Paul — Author of 13 epistles -->
<div data-widebible="person"
  data-slug="paul"
  data-theme="dark">
</div>

<script src="https://cdn.jsdelivr.net/npm/widebible-embed@1/dist/embed.min.js"></script>
```

**Available options for Person Card:**

| Attribute | Values | Notes |
|-----------|--------|-------|
| `data-slug` | lowercase person name | e.g. `moses`, `david`, `paul`, `mary` |
| `data-theme` | `light`, `dark`, `sepia` | `light` |

Learn more: [Biblical People Directory — widebible.com/people/](https://widebible.com/people/) · [Patriarchs and Prophets](https://widebible.com/people/) · [Apostles of Jesus](https://widebible.com/people/)

### Comparison Card — Side-by-Side Verse Comparison

Compare any two Bible verses side by side — useful for parallel Gospel comparisons, Old Testament prophecy vs. New Testament fulfillment, or showing how different translations render the same passage.

With 31,102 verses, there are over 482 million possible verse pairs. Popular comparisons include Synoptic Gospel parallels (Matthew/Mark/Luke covering the same events), Messianic prophecy fulfillments, and wisdom literature parallels between Proverbs and Ecclesiastes.

```html
<!-- Compare two creation accounts: Genesis 1:1 vs John 1:1 -->
<div data-widebible="compare"
  data-a="Genesis 1:1"
  data-b="John 1:1"
  data-theme="light">
</div>

<!-- Messianic prophecy: Isaiah 7:14 foretold vs Matthew 1:23 fulfilled -->
<div data-widebible="compare"
  data-a="Isaiah 7:14"
  data-b="Matthew 1:23"
  data-translation="kjv"
  data-theme="sepia">
</div>

<!-- Synoptic parallel: Matthew 5:3 vs Luke 6:20 (Beatitudes) -->
<div data-widebible="compare"
  data-a="Matthew 5:3"
  data-b="Luke 6:20"
  data-show-original="true"
  data-theme="dark">
</div>

<script src="https://cdn.jsdelivr.net/npm/widebible-embed@1/dist/embed.min.js"></script>
```

Learn more: [Synoptic Gospel Parallels — widebible.com](https://widebible.com) · [Messianic Prophecies](https://widebible.com) · [Cross-Reference Explorer](https://widebible.com)

### Verse of the Day — Auto-Updating Daily Widget

The Verse of the Day widget displays a curated verse that changes automatically each day. Results are cached in localStorage and refresh at midnight UTC — no server calls on repeat visits within the same day. This makes it ideal for homepages, blog sidebars, and any page where you want fresh scripture without manual updates.

The daily verse selection cycles through 365 curated passages covering wisdom, promises, encouragement, and the Gospels — suitable for general Christian audiences.

```html
<!-- Verse of the Day — full size, light theme -->
<div data-widebible="votd" data-theme="light"></div>

<!-- Verse of the Day — dark theme for dark websites -->
<div data-widebible="votd" data-theme="dark"></div>

<!-- Verse of the Day — sepia, warm book-like tone -->
<div data-widebible="votd" data-theme="sepia"></div>

<!-- Compact for narrow sidebars (shows verse + reference only) -->
<div data-widebible="votd" data-theme="light" data-size="compact"></div>

<script src="https://cdn.jsdelivr.net/npm/widebible-embed@1/dist/embed.min.js"></script>
```

Learn more: [Daily Bible Verse — widebible.com](https://widebible.com) · [Bible Reading Plans](https://widebible.com) · [Verse Collections](https://widebible.com)

### Search Box — Full-Text Bible Search

Embed a full-text search box that queries all 31,102 verses in real time. Results appear in a dropdown as the user types, with verse reference, book, and a highlighted snippet. Clicking a result opens the full verse on widebible.com.

The search index covers all 4 translations simultaneously. Searching "love one another" returns verses from John, Romans, 1 John, and more — across all supported translations.

```html
<!-- Default search box -->
<div data-widebible="search"
  data-placeholder="Search Bible verses…"
  data-theme="light">
</div>

<!-- Thematic search — pre-scoped to a topic -->
<div data-widebible="search"
  data-placeholder="Search Psalms…"
  data-theme="sepia">
</div>

<!-- Dark theme search for dark-mode websites -->
<div data-widebible="search"
  data-placeholder="Find a Bible verse…"
  data-theme="dark">
</div>

<script src="https://cdn.jsdelivr.net/npm/widebible-embed@1/dist/embed.min.js"></script>
```

Learn more: [Bible Verse Search — widebible.com](https://widebible.com) · [Concordance Search](https://widebible.com) · [API Search Endpoint](https://widebible.com/developers/)

## Widget Options

All widget types share these common attributes:

| Attribute | Values | Default | Description |
|-----------|--------|---------|-------------|
| `data-widebible` | `verse`, `chapter`, `person`, `compare`, `votd`, `search` | required | Widget type |
| `data-ref` | `"Book Chapter:Verse"` | — | Verse or chapter reference (verse/chapter widgets) |
| `data-slug` | `"moses"`, `"paul"` | — | Person identifier (person widget only) |
| `data-a` | verse reference | — | First verse for comparison |
| `data-b` | verse reference | — | Second verse for comparison |
| `data-theme` | `light`, `dark`, `sepia` | `light` | Visual theme — light for white backgrounds, dark for dark UIs, sepia for warm book-like feel |
| `data-size` | `default`, `compact` | `default` | Compact omits metadata, suitable for sidebars under 300px |
| `data-translation` | `kjv`, `asv`, `bbe`, `ylt` | `kjv` | Bible translation |
| `data-show-original` | `true`, `false` | `false` | Show Hebrew (OT) or Greek (NT) source text below translation |
| `data-placeholder` | any string | `"Search Bible…"` | Placeholder text for search widget |

## Themes

WideBible widgets support 3 themes that respect your site's visual design:

```html
<!-- Light — white background, dark text, blue accent -->
<div data-widebible="votd" data-theme="light"></div>

<!-- Dark — dark background, light text, blue accent -->
<div data-widebible="votd" data-theme="dark"></div>

<!-- Sepia — warm parchment background, brown text — evokes printed Bible -->
<div data-widebible="votd" data-theme="sepia"></div>
```

All themes are self-contained inside Shadow DOM — they never affect or inherit from your site's CSS. You can place widgets on pages with any existing stylesheet without conflicts.

## CDN Options

### jsDelivr (recommended — global CDN, auto-updates with npm)

```html
<script src="https://cdn.jsdelivr.net/npm/widebible-embed@1/dist/embed.min.js"></script>
```

Pin to a specific version for production stability:

```html
<script src="https://cdn.jsdelivr.net/npm/widebible-embed@1.0.1/dist/embed.min.js"></script>
```

### R2 CDN (widebible.com hosted)

```html
<script src="https://cdn.widebible.com/embed.min.js"></script>
```

### npm (for bundlers — Webpack, Vite, Rollup)

```bash
npm install widebible-embed
```

```javascript
// Import the embed script — registers the custom behavior on data-widebible elements
import 'widebible-embed';
```

## Technical Details

- **Shadow DOM**: Complete style isolation — no CSS conflicts with your site. Widgets are fully encapsulated.
- **Zero dependencies**: No jQuery, React, Vue, or any external library. Pure browser APIs only.
- **System fonts**: No Google Fonts request — widgets use the system font stack and load instantly.
- **CORS**: WideBible API has CORS enabled for all origins — no proxy needed.
- **Caching**: Verse of the Day is cached in localStorage and refreshes daily at midnight UTC.
- **MutationObserver**: Works with dynamically added elements (React, Vue, Angular SPAs) — widgets initialize when their container is added to the DOM.
- **Bundle size**: ~5KB gzipped.
- **Accent color**: Blue (`#3B82F6`) — matches the WideBible brand.
- **API base**: `https://widebible.com/api/v1/` — free, no authentication required.

## Learn More About the Bible

- **Browse**: [All 66 Bible Books](https://widebible.com/books/) · [Old Testament](https://widebible.com/books/) · [New Testament](https://widebible.com/books/) · [Psalms — 150 Chapters](https://widebible.com/books/)
- **People**: [1,833 Biblical People](https://widebible.com/people/) · [Prophets and Patriarchs](https://widebible.com/people/) · [Apostles and Disciples](https://widebible.com/people/)
- **Places**: [942 Biblical Places](https://widebible.com/places/) · [Jerusalem](https://widebible.com/places/) · [Ancient Israel Geography](https://widebible.com/places/)
- **Tools**: [Bible Verse Lookup](https://widebible.com) · [Cross-Reference Explorer — 432K+ links](https://widebible.com) · [Widget Builder](https://widget.widebible.com)
- **API**: [REST API Docs](https://widebible.com/developers/) · [OpenAPI Spec](https://widebible.com/api/openapi.json)

## WideHoly Scripture Family

Part of [WideHoly](https://wideholy.com) — Scripture for everyone.

| Site | Domain | Scripture |
|------|--------|-----------|
| **WideBible** | [widebible.com](https://widebible.com) | **66 books, 31,102 verses, KJV/ASV/BBE/YLT, 1,833 people, 942 places** |
| WideQuran | [widequran.com](https://widequran.com) | 114 surahs, 6,236 ayahs, Arabic Uthmani + 5 translations |
| WideTorah | [widetorah.com](https://widetorah.com) | 24 books, 23,145 verses, Hebrew Masoretic + English, 54 parashot |
| WideGita | [widegita.com](https://widegita.com) | 18 chapters, 700 verses, Sanskrit Devanagari + 9 commentators |
| WideSutra | [widesutra.com](https://widesutra.com) | 5 collections, 5,326 texts, Pali + English |
| WideHoly | [wideholy.com](https://wideholy.com) | 5 religions, 236,000+ scripture records, cross-religion comparison |

## License

MIT — see [LICENSE](./LICENSE).

Built with care by [WideHoly](https://wideholy.com).
