# Layout variants

Alternative stylesheets for the same resume. Both variants render the
**identical content** from `../ai.html` — only the stylesheet differs.
`classic.html` is a generated copy with the `<link>` swapped, so content edits
belong in `../ai.html` and must be regenerated down (see below).

| Variant | Look | Reading order | Use for |
| --- | --- | --- | --- |
| `../ai.html` | Modern single column, blue accent | OK | Default — safe everywhere |
| `classic.html` | Serif, centred header, no colour | OK | Conservative firms, traditional finance |

Both export to 2 pages, Letter, 9 live links, zero ligature glyphs.

## Variants that were removed

A `compact` (dense single column) and a `sidebar` (tinted left rail) variant
were built and dropped in August 2026. Recover them from git history if needed.

The sidebar one is worth remembering as a negative result. It was built on the
theory that keeping a linear DOM and merely *placing* sections with CSS Grid
would preserve PDF extraction order, dodging the usual ATS objection to sidebar
resumes. **That theory is wrong.** Chrome emits PDF text by geometric band — a
top-to-bottom sweep across the full page width — so DOM order is never
consulted. The measured order was:

```
SUMMARY -> EXPERIENCE -> Co-Founder -> SwiftScout
-> TECHNICAL SKILLS -> EDUCATION      <-- the rail cut in here
-> FillAnyForms -> HabreCare -> ZenLedger -> EB Pearls
```

The rail landed mid-way through the Marpha Labs role. Do not rebuild a
two-column print layout without re-running the extraction check below.

## Regenerate after editing content

```bash
cd resume/layouts
sed 's|href="assets/resume.css"|href="classic.css"|' ../ai.html > classic.html
```

## Export and verify

```bash
"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless \
  --disable-gpu --no-pdf-header-footer \
  --print-to-pdf="../dist/layout-classic.pdf" "file://$PWD/classic.html"
```

Check page count, link count, ligature glyphs (must be zero) and section
extraction order before using any variant for a real application. A layout that
looks right can still be broken in the text layer.
