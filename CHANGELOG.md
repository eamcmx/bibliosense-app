# What’s new in bibliosense

All notable user-facing changes. Dates are release dates.

## 0.7.1 — 2026-07

Fixes uncovered while testing 0.7.0 on real, large corpora.

### Fixed / improved
- **Large-corpus relevance triage no longer stalls.** It now screens papers in
  batches instead of one call per paper, so a 600-900 record corpus completes
  triage in minutes instead of the better part of an hour, with a progress
  count that keeps moving throughout.
- **Cancel actually cancels** a relevance triage in progress, instead of only
  taking effect once the whole pass finished.
- **A few dialogs (Continue to Literature Review, Start a Literature Review,
  About, confirmations, the AI-error popup, the file picker) could render
  with their top clipped off-screen** on shorter or zoomed windows. All of
  them now stay fully on screen and scroll internally when needed.

## 0.7.0 — 2026-07

Smarter screening, a curated path into Zotero, and much denser analysis maps.
(This release includes the 0.6 "Triage" feature set, which was never published
separately.)

### New
- **AI relevance triage across the whole corpus.** Toggle relevance screening
  and every record gets an on-topic/off-topic verdict with a short reason,
  cross-checked by an independent lexical score so you can see exactly where
  the two disagree. The results live on the Overview tab, with the flagged
  list one click away and a CSV export of the complete screening.
- **Relevance carries into your literature review.** Records flagged in the
  bibliometric pass arrive in title/abstract screening pre-annotated, so your
  review starts from the AI's prior instead of from zero.
- **Curated corpus straight to Zotero.** Export the screened, theme-tagged
  corpus as CSL-JSON with stable citation keys (Better BibTeX compatible:
  Ullah2026, Wang2025a...) plus a matching RIS that attaches your downloaded
  PDFs. Import to Zotero and everything lands with abstracts, tags and keys
  intact.
- **Publisher full-text retrieval.** On an entitled network, Elsevier papers
  download directly from ScienceDirect during full-text retrieval; elsewhere
  bibliosense detects the situation quickly and continues with open access.
- **Reports document how your question was built.** The search-strategy
  section now records the original idea you typed, the candidate research
  questions the assistant proposed (the selected one marked), the final
  research question, and each database's query-refinement trail with live hit
  counts: the full audit from idea to corpus.
- **Model lists are always current.** The AI provider panels fetch the live
  model list from each vendor, so new models appear the day they ship.

### Fixed / improved
- **Keyword maps are far denser.** Scopus live searches now fetch indexed
  keywords as well as author keywords, and spelling variants of one concept
  ("power-law fluid" / "power law fluids" / "porous media" / "porous medium")
  are merged before counting. Co-occurrence networks that collapsed to a
  handful of nodes now show the real thematic structure of the field.
- **Countries and institutions are correct** for Scopus live corpora
  (affiliations previously arrived without their city and country parts).
- **The acronym glossary is genuine**: acronyms are detected across the whole
  corpus with real frequencies and author-provided definitions harvested from
  the abstracts, instead of a sample-limited guess.
- **Off-campus full-text runs no longer stall** at the start of retrieval.
- The research question is shown in the report again (it was silently dropped
  from the search-strategy section).
- Assorted dialog sizing fixes on smaller displays.

## 0.5.1 — 2026‑06

A polish release that makes setup and the search lanes work the way you'd expect.

### Fixed / improved
- **Set up your AI key from anywhere.** The AI‑provider key (Mistral, Claude,
  OpenAI…) is now entered from the **Settings gear** on every screen — expanded
  and ready in one click, no longer buried inside the bibliometric flow.
- **Live Scopus search is richer.** Records now arrive with the **full
  (non‑truncated) abstract and their reference list** (so co‑citation and
  coupling work), enriched in parallel with a live progress count.
- **Work off‑campus.** Switch Scopus between **live API** and **browser‑assisted**
  in the Research Pilot — so when your key isn't entitled off‑campus (or you'd
  rather export manually from your institution), you can, without removing the key.
- **Reliable consolidation.** A live Scopus/PubMed search run inside a Research
  Pilot session is always included when you consolidate.
- **License activation fixed.** Machine‑locked license keys now activate
  correctly on the machine they're bound to.

## 0.5.0 “Chronicles” — 2026‑06

The release that turns a review into a story, and a search into a guided workflow.

### New
- **Chronicle videos.** Export a narrated MP4 that animates how your field evolved
  over time — a scrolling publications/citations timeline, bar “races” of the top
  keywords, authors, institutions, countries and sources, a co‑occurrence network
  that assembles year by year, and a thematic‑drift map. Choose exactly which
  scenes to include, set the title, and pick captions or a neural voice‑over.
- **Research Pilot — live database search.** Describe your question and the app
  drafts a search, tunes it against the **live result count**, and fetches the
  records for you. **PubMed** and **Scopus** run directly in‑app (Scopus needs
  your Scopus API key, added in Settings); other databases are guided
  browser‑assisted lanes. Results from every database are merged and de‑duplicated
  into one PRISMA‑complete corpus.
- **Search‑database API keys.** Add your Scopus / IEEE keys in Settings (stored
  securely in Windows Credential Manager) to search those databases live.
- **Editable Chronicle title** and cleaner co‑occurrence figures in reports.

### Improved
- Richer Scopus records — full (non‑truncated) abstracts and reference lists, so
  co‑citation and coupling analyses work on Scopus corpora.
- Reliability fixes across search consolidation and report figure export.

### Licensing
- Free 30‑day evaluation on first launch; license keys for continued use
  (contact via [LinkedIn](https://www.linkedin.com/in/emmanuel-merch%C3%A1n-444381105/)).

---

## Earlier
- **0.4.x** — AI‑enhanced narrative reports; multi‑database literature‑review
  workflow; saved‑analysis Library; in‑app research assistant.
- **0.2.x** — Bibliometric dashboards and PRISMA 2020 screening + core‑corpus
  curation with AI‑assisted screening and open‑access full‑text retrieval.
