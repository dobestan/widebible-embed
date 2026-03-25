# widebible-embed

[![npm](https://img.shields.io/npm/v/widebible-embed)](https://www.npmjs.com/package/widebible-embed)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Zero Dependencies](https://img.shields.io/badge/dependencies-0-brightgreen)](https://www.npmjs.com/package/widebible-embed)
[![Size](https://img.shields.io/badge/size-~5KB-green)](https://bundlephobia.com/package/widebible-embed)

Embed WideBible scripture widgets on any website. **Zero dependencies**, Shadow DOM style isolation, 3 built-in themes (light, dark, sepia), and automatic daily verse updates. Each widget includes a "Powered by WideBible" backlink.

> **Try the interactive widget builder at [widget.widebible.com](https://widget.widebible.com)**

## Quick Start

```html
<!-- Place widget div where you want it to appear -->
<div data-widebible="verse" data-ref="John 3:16" data-theme="light"></div>

<!-- Load the embed script once, anywhere on the page -->
<script src="https://cdn.jsdelivr.net/npm/widebible-embed@1/dist/embed.min.js"></script>
```

That's it. The widget will load, fetch the verse from the WideBible API, and render it with full style isolation.

## Widget Types

| Type | Usage |
|------|-------|
| Verse Card | `<div data-widebible="verse" data-ref="..." data-theme="light"></div>` |
| Chapter Card | `<div data-widebible="chapter" data-ref="..."></div>` |
| Person Card | `<div data-widebible="person" data-slug="moses"></div>` |
| Comparison Card | `<div data-widebible="compare" data-a="..." data-b="..."></div>` |
| Verse of the Day | `<div data-widebible="votd" data-theme="light"></div>` |
| Search Box | `<div data-widebible="search" data-placeholder="..."></div>` |

## Widget Options

| Attribute | Values | Default | Description |
|-----------|--------|---------|-------------|
| `data-widebible` | verse, chapter, person, compare, votd, search | required | Widget type |
| `data-ref` | "John 3:16" | — | Verse/chapter reference |
| `data-slug` | "moses", "paul" | — | Person slug (person widget only) |
| `data-a` | verse ref | — | First verse for comparison |
| `data-b` | verse ref | — | Second verse for comparison |
| `data-theme` | light, dark, sepia | light | Visual theme |
| `data-size` | default, compact | default | Widget size |
| `data-translation` | kjv, etc. | kjv | Translation code |
| `data-show-original` | true, false | false | Show original language text |
| `data-placeholder` | any string | "Search Bible…" | Search box placeholder |

## Themes

```html
<!-- Light (default) -->
<div data-widebible="votd" data-theme="light"></div>

<!-- Dark -->
<div data-widebible="votd" data-theme="dark"></div>

<!-- Sepia (warm, book-like) -->
<div data-widebible="votd" data-theme="sepia"></div>
```

## CDN Options

### jsDelivr (recommended — global CDN, auto-updates with npm)

```html
<script src="https://cdn.jsdelivr.net/npm/widebible-embed@1/dist/embed.min.js"></script>
```

### R2 CDN (widebible.com hosted)

```html
<script src="https://cdn.widebible.com/embed.min.js"></script>
```

### npm (for bundlers)

```bash
npm install widebible-embed
```

```javascript
import 'widebible-embed';
```

## Examples

### Verse of the Day

```html
<div data-widebible="votd" data-theme="light"></div>
<script src="https://cdn.jsdelivr.net/npm/widebible-embed@1/dist/embed.min.js"></script>
```

### Verse with Original Language

```html
<div data-widebible="verse"
  data-ref="John 3:16"
  data-show-original="true"
  data-theme="sepia">
</div>
<script src="https://cdn.jsdelivr.net/npm/widebible-embed@1/dist/embed.min.js"></script>
```

### Compact Verse of the Day (sidebar use)

```html
<div data-widebible="votd" data-theme="light" data-size="compact"></div>
<script src="https://cdn.jsdelivr.net/npm/widebible-embed@1/dist/embed.min.js"></script>
```

### Search Box

```html
<div data-widebible="search" data-placeholder="Search Bible…"></div>
<script src="https://cdn.jsdelivr.net/npm/widebible-embed@1/dist/embed.min.js"></script>
```

## Technical Details

- **Shadow DOM**: Complete style isolation — no CSS conflicts with your site
- **Zero dependencies**: No jQuery, React, or any external library
- **System fonts**: No Google Fonts request — loads instantly
- **CORS**: WideBible API has CORS enabled for all origins
- **Caching**: Verse of the Day cached in localStorage (refreshes daily)
- **MutationObserver**: Works with dynamically added elements (SPAs)
- **Bundle size**: ~5KB gzipped

## Learn More About Bible

Visit [widebible.com](https://widebible.com) — WideBible is a comprehensive Bible reference with full text, translations, and study tools.

- **API docs**: [widebible.com/developers/](https://widebible.com/developers/)
- **Widget builder**: [widget.widebible.com](https://widget.widebible.com)
- **npm package**: [npmjs.com/package/widebible-embed](https://www.npmjs.com/package/widebible-embed)

## WideHoly Scripture Family

Part of [WideHoly](https://wideholy.com) — Scripture for everyone.

| Site | Domain | Scripture |
|------|--------|-----------|
| **WideBible** | [widebible.com](https://widebible.com) | Bible verses, chapters, people |
| **WideQuran** | [widequran.com](https://widequran.com) | Quran verses, surahs |
| **WideTorah** | [widetorah.com](https://widetorah.com) | Torah verses, portions |
| **WideGita** | [widegita.com](https://widegita.com) | Bhagavad Gita verses |
| **WideSutra** | [widesutra.com](https://widesutra.com) | Buddhist sutras, teachings |
| **WideHoly** | [wideholy.com](https://wideholy.com) | Multi-religion scripture hub |

## License

MIT — see [LICENSE](./LICENSE).

Built with ❤️ by [WideHoly](https://wideholy.com).
