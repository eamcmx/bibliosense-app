# bibliosense — User Guide

**Version 0.7.1 · Windows 10/11 (64‑bit)**

This guide takes you from a fresh install to your first complete analysis, your
first PRISMA‑screened core corpus, and your first Chronicle video. Every section is
a short checklist of what to click and what to expect.

---

## 1. Install

Pick one (both are the same app):

- **`bibliosense_0.7.1_x64-setup.exe`** — standard installer; adds a Start‑menu
  shortcut. Best for most users.
- **`bibliosense_0.7.1_x64_en-US.msi`** — for IT‑managed machines.

> **First launch may show a Windows SmartScreen notice** (the app isn’t
> code‑signed yet). Click **More info → Run anyway**.

Your saved analyses live in your user profile and your keys in Windows
Credential Manager — nothing is written elsewhere.

---

## 2. First launch

On first run you’ll see the **mode picker** with three ways to work:

| Mode | Use it when… |
|---|---|
| **Bibliometric** | You have (or will fetch) a set of records and want dashboards + a written report. |
| **Literature Review** | You’re curating a PRISMA‑screened core corpus — identification, screening, themes, and a flow diagram. |
| **Research Pilot** | You want the app to help you *design and run the search itself* across databases. |

You also get a **free 30‑day evaluation** — full functionality, no feature
gates. After that, a license key unlocks continued use (see §9).

### (Optional) Turn on AI
AI features — narrative report writing, relevance triage, screening
assistance, the in‑app assistant — are optional and use **your own** provider
key.

1. Open **Settings** (the gear, top‑right) or the **AI Enhancement** panel.
2. Choose a provider (OpenAI, Anthropic, or **Mistral** — Mistral has a capable
   free tier), paste your API key, and **Test**. The model list is fetched live
   from each vendor, so new models show up as soon as they ship.
3. Toggle AI on. You can switch provider/model anytime from the header.

Without a key, all the core analysis still works — AI just adds the written
narrative and assistance on top.

---

## 3. Research Pilot — let the app build your corpus

1. Choose **Research Pilot** and type your research question (or a rough topic —
   it can suggest sharper candidate questions; the one you pick, alongside every
   candidate it proposed, is recorded in the eventual report so the search
   strategy is fully documented from idea to final question).
2. **PubMed** runs live and credential‑free. For **Scopus**, add your Scopus API
   key once via the **Settings gear → Search‑database API keys** (also IEEE if
   you have it); Scopus then runs live too — or switch it to **browser‑assisted**
   mode if you’re off‑campus or would rather export manually from your
   institution, without removing the key.
3. For each database, the app drafts a query and **tunes it against the live hit
   count** until it’s a sensible size — you watch the count move and accept when
   happy. Other databases give you a ready‑to‑paste query for your institutional
   browser, then you upload the export.
4. Click **Consolidate** — every database’s results are merged and de‑duplicated
   into one corpus, with every search recorded for your PRISMA appendix.
5. Continue straight into **Bibliometric analysis** or a **Literature Review**.

---

## 4. Bibliometric analysis

1. In **Bibliometric** mode, drop in your records (a Scopus / Web of Science /
   Lens / OpenAlex export, or the corpus Research Pilot built).
2. Review the **Corpus ready** summary (record count, year range, whether cited
   references are included), adjust analysis settings if needed, and click
   **Run analysis**. A running analysis can be **cancelled** at any point.
3. Explore the interactive dashboards: keyword co‑occurrence, author /
   institution / country collaboration, citation impact, thematic map, research
   fronts, source productivity, and more.
4. Open the **Report** tab for the written narrative (with AI on, every claim is
   grounded in your actual records).

### AI relevance triage (optional, two‑pass analysis)
Turn on **relevance screening** and, before any dashboard is built, the AI
checks every record against your research question and excludes what it judges
off‑topic — so the networks, trends, and counts you explore are computed on the
cleaned corpus, not diluted by papers that slipped through the search. Every
verdict (kept and excluded) stays visible: the **Overview tab’s “AI relevance
screening” card** shows the split, the reasoning behind each exclusion, and an
**Export‑CSV** button for the complete screening; the report opens with the same
identified → excluded → analysed counts. Screening a large corpus (many hundreds
of records) takes a few minutes, with the progress count moving throughout.

### Export
From the report/output area you can save:
- **Word (.docx)** and **Markdown** reports,
- figures as images,
- and (see §6) a **Chronicle video**.

---

## 5. Literature Review mode — build the core corpus (PRISMA 2020)

This mode takes you **up to the curated, PRISMA‑screened core corpus** — the
rigorous foundation your literature review is built on. The reading, synthesis,
and write‑up stay yours.

1. Choose **Literature Review** and set your research question(s).
2. **Identification** — bring in your search results (or carry them over from a
   bibliometric analysis / Research Pilot consolidation). If a prior bibliometric
   run already screened the corpus for relevance, those verdicts arrive here as
   a starting point for screening.
3. **Screening** — define inclusion/exclusion criteria; AI can assist
   title/abstract screening, and you make the final call on each record.
4. **Retrieval** — fetch full texts automatically: open‑access sources, plus
   direct publisher download (ScienceDirect) for Elsevier papers when your
   network is entitled.
5. **Themes** — get suggested themes, organise included studies, and use
   **Pre‑qualify with AI** to flag studies that no longer fit a theme.
6. **Export** — a publishable **PRISMA flow diagram** (SVG + PDF + DOCX), a
   records table, and a **“Curated corpus (Zotero)”** export: your screened,
   theme‑tagged corpus as CSL‑JSON with stable citation keys plus a matching
   RIS that attaches any PDFs you downloaded — import into Zotero and
   everything lands with abstracts, tags, and keys intact.

---

## 6. Chronicle video — the story of your field

1. From a completed bibliometric analysis, open **Chronicle** (Output tab) or
   “Export evolution video”.
2. Choose which **scenes** to include (timeline, keyword/author/institution/
   country/source races, co‑occurrence network, thematic drift, outro), set the
   **title**, and pick **captions** or a **neural voice‑over**.
3. Render and **Save** the MP4.

It’s the fastest way to make a review land with an audience that won’t read the
full report.

---

## 7. The Library

Every analysis you run is saved to the **Library** (the books icon, top‑right) —
reopen, compare, rename, or delete past analyses and reviews at any time.

---

## 8. The in‑app assistant

With AI enabled, chat with the assistant about **your specific dataset** — ask
what the busiest research fronts are, which authors bridge clusters, or to
explain a figure. It answers from your loaded corpus.

---

## 9. Trial & licensing

- **Free 30‑day evaluation** begins on first launch — full features.
- For continued use, activate a **license key**: open the **About** dialog (or
  the trial screen) and paste your key into **Activate license**.
- **Need a license** (individual, lab, or institutional)? Reach out on
  **[LinkedIn](https://www.linkedin.com/in/emmanuel-merch%C3%A1n-444381105/)**.

---

## 10. Privacy

- Your **library, analyses, and data stay on your machine.**
- **AI features and online full‑text retrieval** reach the internet **only when
  you enable them**, using credentials you supply.
- API keys are stored in **Windows Credential Manager**, never in plain text.

---

## 11. Troubleshooting

| Symptom | Fix |
|---|---|
| **SmartScreen blocks first launch** | *More info → Run anyway* (the app isn’t code‑signed yet). |
| **A database lane won’t run live** | PubMed needs no key; **Scopus needs your Scopus API key** (Settings gear). Some keys only return full records on a subscribing campus network — switch that lane to browser‑assisted instead. |
| **AI features greyed out** | Add and **Test** a provider key, then toggle AI on. |
| **Large corpus feels slow** | 8 GB RAM is recommended for >1000 records; analysis is heaviest on first run. With relevance screening on, a several‑hundred‑record corpus takes a few minutes for the triage pass alone — the progress count keeps moving throughout. |

---

*Questions or feedback? Connect on **[LinkedIn](https://www.linkedin.com/in/emmanuel-merch%C3%A1n-444381105/)** · © 2026 Emmanuel A. Merchán‑Cruz. All rights reserved.*
