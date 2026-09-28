# Finance Analyst — Document Review Platform (Working manager + concept analytics)

A browser app that pairs a **functional financial-document manager** with a
**concept analytics/AI layer** for monthly financial review.

> **Live demo:** https://finance-analyst-concept.vercel.app
>
> ⚠️ **Honest scope:** the document-management side is **genuinely functional**; the
> analytics/AI side is a **concept** (illustrative figures). See below.

## What actually works today

A real, self-contained client-side document manager:

- **Upload** financial documents (PDF / XLSX / CSV / images) by click or drag-drop.
- **Persist** them in the browser via **IndexedDB** — the actual file bytes are stored
  and survive a refresh.
- **Organize** by period/month, with per-month counts and storage totals.
- **Download** or delete any stored file; clear a month or everything.
- A stats bar (active periods, total files, storage used, last upload) computed from
  the real stored files.

## What is a concept (not yet wired up)

- The **KPIs, charts, "AI-generated findings", and extracted line items** are
  illustrative sample data, not computed from your uploads.
- The **"AI analyst crew"** is a visual workflow demo; there is no LLM call yet, and
  uploaded files are **stored but not yet parsed**.

## What would make the analytics real (roadmap)

- Parse uploads client-side — SheetJS (`xlsx`) for Excel/CSV and pdf.js (+ OCR for
  scans) to extract tables/text.
- A normalization layer mapping parsed rows to accounts/categories.
- Compute the metrics (revenue, expenses, margin, cash flow, variances) from the
  parsed data and drive the KPIs/charts/table from it.
- For genuine AI findings: a backend proxy calling an LLM (e.g. Anthropic Claude) on
  the extracted data, so no key is exposed client-side.
- Real report export (PDF/XLSX) instead of the placeholder action.

## Tech

Single self-contained HTML file. Vanilla JS, Chart.js, IndexedDB. No build step.
Deploys as-is to any static host (Vercel, Netlify, GitHub Pages).

## Privacy

No API keys, no backend, no data leaves your browser — uploaded files live only in
your browser's IndexedDB.

## License

See [LICENSE](LICENSE). Provided for review and evaluation.
