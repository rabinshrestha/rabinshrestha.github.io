# Resume

Source for Rabin Shrestha's resume.

`ai.html` is the only variant. It targets AI application engineering, LLM
product teams, and AI-forward startups, and is the document published as the
live `resume.pdf`.

A backend / full-stack variant (`backend.html`) existed alongside it until
August 2026. It was dropped to keep a single source of truth; recover it from
git history if a backend-heavy or platform role needs it.

## Structure

```
resume/
├── README.md          this file
├── assets/
│   └── resume.css     shared styles (screen + print)
├── ai.html            the resume
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
- Marpha Labs projects lead with **SwiftScout** — the only shipped, paying
  product — so the section opens on released work rather than a status chip.
- Keep bullet lists in **past tense** throughout; the status chips
  (`Pre-launch`, `In development`) carry the "not yet released" signal.
