# Resume

Source for Rabin Shrestha's resume.

`ai.html` is the source of truth and the document published as the live
`resume.pdf`. It positions **fintech first, then AI/LLM** — seven years as
founding engineer on a financial platform is the deeper domain, while the
current LLM work is the forward-looking half. The two are stated separately on
purpose: the fintech experience (ZenLedger, 2018-2025) and the AI work (Marpha
Labs, 2025-) do not overlap, so the resume never implies shipped "AI for
fintech" experience.

`layouts/classic.html` renders the same content in a serif, no-colour,
traditional style for conservative employers. See `layouts/README.md`.

A backend / full-stack variant (`backend.html`) existed until August 2026, as
did `compact` and `sidebar` layouts. All were dropped to keep the set small;
recover them from git history if needed.

## Structure

```
resume/
├── README.md          this file
├── assets/
│   └── resume.css     shared styles (screen + print)
├── ai.html            the resume — edit content HERE
├── layouts/           alternative stylesheets (classic) + generated HTML
└── dist/              exported PDFs (git-ignored by default)
```

## Preview

```bash
open resume/ai.html
```

No build step and no dependencies — the stylesheet is linked relatively, so
opening the file directly works.

## Export to PDF

1. Open `ai.html` in **Chrome**.
2. **File → Print** (`⌘P`).
3. Destination **Save as PDF**, paper **Letter**, margins **Default**,
   **Background graphics ON** (the section rules and status chips need it).
4. Save into `dist/` as `rabin-shrestha-ai.pdf`.

The page CSS already sets `@page { size: Letter; margin: 0.45in }`, so Chrome's
own margin setting should stay on Default — overriding it will double the
margins.

## Publishing

The live resume is served from the repo root as `resume.pdf`
(<https://rabinshrestha.github.io/resume.pdf>). To publish a new version, copy
the exported PDF over that file:

```bash
cp resume/dist/rabin-shrestha-ai.pdf resume.pdf
```

Keep the filename `resume.pdf` — it is the URL people already have.

## Editing notes

- Dates are deliberately **year-granularity** (`2018 – 2025`, `2025 – Present`).
  Keep it that way; mixing month and year granularity draws the eye to gaps.
- Every metric on the page is a real number.
- Target length is **2 pages**. If it spills onto a third, cut bullets from
  EB Pearls first, then trim the oldest ZenLedger bullets.
- Keep prose lean. A revision in August 2026 cut body copy 29% (561 -> 397
  words) by removing framework version numbers, implementation tails, and
  clauses that explained why an achievement mattered. Resist adding them back:
  nobody is hired for the minor version, and version numbers date the document.
- Never frame learning a new language or shipping end-to-end as an achievement.
  Both are assumed at senior level and reading them as accomplishments signals
  the opposite.
- After editing, regenerate `layouts/classic.html` and re-export both PDFs.
- Page margin is **0.5in**. At 0.4in nothing clipped, but the right-aligned
  column (contact, dates, stacks) sat flush against the edge and read as
  trimmed. 0.45-0.55in all still fit two pages, so there is headroom.
- Projects nest inside a `.projects` wrapper that carries **one continuous 1px
  hairline**. Do not move that border onto `.project` — it can only draw one
  segment per project, giving a line that repeatedly starts and stops.
- **Never mark a project with an absolutely-positioned `::before`.** It makes
  `.project` a positioned box, Chrome paints it in a later layer, and the PDF
  text layer comes out scrambled — measured: the ZenLedger heading emitted
  before the Marpha projects, and the whole ZenLedger Platform block after
  EDUCATION. The page looked perfect throughout. Use a border, and re-run the
  extraction-order check after any change here.
- Contact sits **top-right** with inline SVG icons. The icons are decorative
  (`aria-hidden`), vector not raster, and every contact value stays real text —
  verify with an extraction check after touching the header, since a two-column
  header is the same construction that scrambled the dropped sidebar layout.
  `classic.css` suppresses the icons and reflows the items inline; it is a
  traditional centred header on purpose.
- `marphalabs.com` is linked on the Marpha Labs role header only. It used to
  appear in the contact block too — one URL, two links on one page.
- The **BATS / IRS** claim is safe to state publicly. ZenLedger's contract with
  the IRS Civil and Criminal Investigation units was announced by the company
  and covered by trade press (PR Newswire, Accounting Today, ExecutiveBiz), and
  <https://bats.ai> markets the product to "federal and state investigators".
  Nothing on the page is drawn from anything non-public.
- Marpha Labs projects lead with **SwiftScout** — the only shipped, paying
  product — so the section opens on released work rather than a status chip.
- Keep bullet lists in **past tense** throughout; the status chips
  (`Pre-launch`, `In development`) carry the "not yet released" signal.
