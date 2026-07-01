# j-code-ext-markup-pack-1

A JCode **language** extension bundling several **markup, config, and data**
formats in one pack — installed through the
[JCode Marketplace](https://github.com/blamspotdev/j-code-marketplace) and shipped
**pre-installed** with the JCode app.

| Language | Extensions |
|---|---|
| HTML | `.html` `.htm` `.xhtml` `.vue` `.svelte` |
| XML | `.xml` `.xsd` `.xsl(t)` `.plist` `.csproj` `.props` `.targets` … |
| SVG | `.svg` |
| YAML | `.yaml` `.yml` |
| JSON | `.json` `.jsonc` `.json5` `.webmanifest` … |
| TOML | `.toml` |
| CSS | `.css` `.pcss` `.postcss` |
| INI / .env | `.ini` `.conf` `.cfg` `.env` `.properties` `.editorconfig` `.gitconfig` |

Each language provides syntax **coloring**, as-you-type **completions + snippet
helpers** (e.g. an HTML5 boilerplate, a `<link>`/`<script>` tag, a CSS flex-center
block, an XML declaration), and the built-in **Format Document** (indent / trim
trailing whitespace / final newline).

## Manifest shape — one extension, many languages

`extension.yaml` uses a `languages:` array; each entry is a self-contained language
pack resolved by file extension:

```yaml
type: language
languages:
  - id: html
    extensions: [".html", ".htm"]
    comment: { blockStart: "<!--", blockEnd: "-->" }
    strings: ["\"", "'"]
    keywords: [div, span, a, img]      # colored as keywords; also offered as completions
    types: [class, id, href]           # colored as types
    formatter: { indent: 2, trimTrailingWhitespace: true, insertFinalNewline: true }
    completions:
      - { label: a, detail: anchor, insert: "<a href=\"$1\">$0</a>" }   # $1/$0 = tab stops
    helpers:
      - { title: HTML5 boilerplate, snippet: "..." }
  - id: css
    # ...
```

The legacy single-`language:` form is still supported for one-language packs.

See the marketplace's
[`CREATING-EXTENSIONS.md`](https://github.com/blamspotdev/j-code-marketplace/blob/main/CREATING-EXTENSIONS.md)
for the full authoring flow.

## License

MIT. © 2026 blamspotdev (Janrick Samorin).
