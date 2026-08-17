# Resume

Source for Rabin Shrestha's resume. Two variants share one stylesheet.

| File | Variant | Target roles |
| --- | --- | --- |
| `ai.html` | **AI / LLM — primary** | AI application engineering, LLM product teams, AI-forward startups |
| `backend.html` | Backend / full-stack | Senior & staff engineering, backend, distributed systems, platform |

`ai.html` is the **primary** variant and the one published as the live
`resume.pdf`. `backend.html` is kept current alongside it — it is the stronger
document for backend-heavy and platform roles.

Both cover the same history. They differ in the summary, the order of the Marpha
Labs projects, the ordering of the skills block, and which bullets lead.

## Structure

```
resume/
├── README.md          this file
├── assets/
│   └── resume.css     shared styles (screen + print)
├── backend.html       backend / full-stack variant
├── ai.html            AI / LLM variant
└── dist/              exported PDFs (git-ignored by default)
```

## Preview

```bash
open resume/backend.html      # or: open resume/ai.html
```

No build step and no dependencies — the stylesheet is linked relatively, so
opening the file directly works.

## Export to PDF

1. Open the variant in **Chrome**.
2. **File → Print** (`⌘P`).
3. Destination **Save as PDF**, paper **Letter**, margins **Default**,
   **Background graphics ON** (the section rules and status chips need it).
4. Save into `dist/` as `rabin-shrestha-backend.pdf` or
   `rabin-shrestha-ai.pdf`.

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
- Every metric on the page is a real number. If one changes, change it in both
  variants — they are independent files and will not stay in sync on their own.
- Target length is **2 pages**. If a variant spills onto a third, cut bullets
  from EB Pearls first, then trim the oldest ZenLedger bullets.
