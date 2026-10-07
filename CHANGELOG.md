# What’s new in bibliosense

All notable user-facing changes. Dates are release dates.

## 0.7.9 (2026-10)

A small release. One file is no longer written unless you ask for it, two things that
could go wrong when you click a link or open a file that came with someone else's review
are closed, and cited works found through Crossref are printed as their publishers print
them.

### Changed
- **No standalone dashboard file unless you ask for it.** Every analysis wrote a
  `dashboard.html` (5 to 9 MB) into a new folder next to the corpus file, beside the Word
  report (for a Research Pilot search, in the search's own folder, which **Show in folder**
  on the consolidated corpus opens). Nothing in the app uses that file: the dashboards you
  explore are drawn by the app itself. It is now written only when you switch on *Also
  write a standalone dashboard.html beside the report* in the analysis settings (Outputs).
  The switch applies to the current session and is off again when the app starts. When
  you do ask for the file, it now carries the AI text and the cited works' details that
  the report beside it carries (since 0.7.6 it was written too early to hold them).

### Fixed
- **A DOI link in the Report tab opens in your browser.** It used to load the page into
  the app's own window, and the app was gone until it was restarted.
- **"Open file" opens documents only, and an imported review cannot point it elsewhere.**
  A review bundle that someone sends you names, for each record, where its full text is.
  That was taken as given, so a bundle made for the purpose could have made *Open file*
  start a program. An imported review now keeps the documents the bundle itself carries
  and drops every other file path, and *Open file* refuses anything that is not a
  document.
- **The standalone dashboard shows your records as text.** That file placed titles,
  venues, keywords, names and AI text into its page as markup. A keyword that arrived
  with a broken piece of markup (a real case from an IEEE export: `<italic xmlns:ali="`)
  hid the keywords after it, and a record written for the purpose could run script when
  the file was opened in a browser. The file now writes everything from your corpus as
  text, and its links go to doi.org only. Keywords that carry the markup of their source,
  such as `co<sub>2</sub>`, are shown as written, as the app shows them. A
  `dashboard.html` dated before you installed 0.7.9 can be deleted. Do not open one that
  was made from records someone else gave you, or one that someone else sent you; to share
  a dashboard, run the analysis again in 0.7.9 with the switch on.
- **Cited works found through Crossref read as published.** Abstracts and journal names
  came back with coded characters and were printed that way
  (`IEEE Communications Surveys &amp; Tutorials`); they now read as the publisher prints
  them, and a short title that held such a character is recognised as the cited work. An
  analysis made with 0.7.8 keeps the entries it saved; run it again to have them corrected.
- **A paper is no longer printed with a preprint's title as its journal.** When a
  preprint cited by its arXiv number shared a reference code with a different paper, the
  preprint's title and arXiv number were printed as that paper's venue, and the preprint's
  DOI and database number were mixed into its entry.
- **Network labels with braces are drawn as written.** A keyword such as
  `high-t_{c} superconductor` was changed by the chart in the network view and in the
  figure exported from it.
- **The Default preset of the analysis settings** resets the analysis parameters only; it
  no longer changes the output switches or clears the research question.

## 0.7.8 (2026-10)

0.7.6 and 0.7.7 were not published separately. This release carries their fixes, listed
below, and prints the cited works a report lists as full bibliographic entries.

### Cited works are printed as works
- **Every reading is a full entry.** A report built from a Research Pilot corpus listed
  the works to read first by internal codes instead of titles. The report now gives, for
  each of them: the full title, the authors, the year, the journal or conference with
  volume and pages, the DOI, how many records of your corpus cite it, and the abstract
  with its source. The seminal references table, the reading lists per emerging theme,
  the Markdown report and the Seminal refs tab show full titles with authors and venue
  in place of codes. A corpus fetched with a version earlier than 0.7.5 may hold only the
  database's number for a cited work; it is shown as such, and running the search again
  records the titles.
- **No identifier in front of a reader.** Where a text named a record or a cited work by
  an identifier or by a list label ("R-7"), it now names the work.
- **One entry per cited work, built from all the records that cite it.** Each citing
  record renders a cited work a little differently (a lost hyphen, a lower-cased name, a
  wrong page). The entry takes the form most citing records give, never mixes two papers
  into one, and says so when a detail rests on a single record. A corpus that gives its
  references as strings (a database CSV export) is read the same way.
- **Authors and abstracts are looked up** for the works the report lists (up to 45),
  because reference lists do not carry them: Scopus when you have a key, then OpenAlex,
  arXiv, Crossref and Semantic Scholar. A result is used only when its title, first
  author and year agree with what your corpus cites; every entry says what the lookup
  supplied and when, and every abstract names its source. Results are remembered, so a
  later report asks nothing twice. What is sent identifies the cited work and nothing
  else (its DOI, its database number, or its title with the first author's surname),
  never your own records. The lookup is on by default; the user guide (Privacy) lists
  the services and says how to switch it off.
- **Saved analyses** show full entries when you open their Report tab (for an analysis
  with the Legacy badge, press Refresh figures). A copy of the report as first saved is
  kept beside it.

### New
- **OpenAlex API key (optional).** Settings has a new field for a free OpenAlex key.
  Without one, OpenAlex gives everyone on the same network a small shared daily
  allowance, which a campus uses up quickly; with your own key the lookups of cited
  works, and the open-access search of a literature review, draw on your own allowance
  instead. The key is kept in Windows Credential Manager and sent to OpenAlex only.
- **From a corpus to a literature review, nothing asked twice.** Starting a review from
  a saved analysis, the Library or the Research Pilot now carries the databases, their
  queries, dates and hit counts, the duplicates removed and the research question into
  the review, with a preview before you start. Records a database reported but that
  were never exported are counted as removed for other reasons, not as duplicates.
- **Save the corpus where you choose.** The Research Pilot's consolidated corpus can be
  saved to a folder you pick, with the search record that belongs to it; the copy is
  refreshed each time you re-consolidate. Every Library row can also save the corpus
  its analysis was run on.

### Fixed in the bibliometric report
Corrections to the statistics and wording of the bibliometric report, found on real
two-database corpora.

- **Growth and trends compare like with like.** When the databases in a corpus cover
  different years (for example Scopus 2021-2025 and IEEE Xplore 2020-2026), growth, eras,
  emerging themes and period shifts now use only the complete years every database
  covers, and the report names the years left out and why. On one such corpus the
  growth rate changed from +74.5%/yr to +20.7%/yr.
- **Emerging themes.** A theme is called significant only when a proper statistical test
  says so: are more of the keyword's records in that period than the period's size
  predicts, allowing for which database each record came from, with false-discovery
  control. Before, nothing could reach significance with few periods, and the report
  still headlined a theme. Rows that are not significant are labelled as such, in the
  table and in the reading lists.
- **Network sections.** The largest "cluster" in several sections was really the set of
  items left out of the network's backbone. Sections now describe the real communities,
  numbered the same way everywhere, name the most connected items for what they are, and
  no longer read meaning into the density of a backbone.
- **Country shares** are shares of all records, not of the countries listed.
- **AI text** reads the same numbers as the tables beside it: the thematic paragraph no
  longer contradicts the transitions table; every paper is placed in its main cluster
  only; the most-cited paper of each cluster is named correctly; cluster
  names must describe what most of the cluster's records share; figures a paper quotes
  from earlier work are not presented as its findings; "bridge" keywords are computed
  rather than guessed. The section 8 AI paragraph and the AI cover title carry an AI stamp.
- **Wording that claimed too much** (an h-index "indicating a well-established field",
  "explosive" growth, "most of this literature" for a third of it) is replaced by what
  the numbers mean.
- **Same corpus, same result.** Two runs on one corpus could produce different keyword
  clusters; they are now identical.
- **Data.** A preprint and its published version are one cited work; journal-name
  variants such as "Sensors (Basel, Switzerland)" merge; "China and" no longer reads as
  Andorra; city names are not institutions; database indexing terms that the papers
  themselves never mention are left out of the keyword analysis.
- **AI paragraphs withheld by mistake.** The check that keeps AI text honest was too
  strict in places and withheld sound paragraphs, cluster names, report titles, glossary
  entries and query proposals. It now withholds only what the data does not support. A
  cluster whose name is still withheld is named by its top keywords instead of
  "Cluster N".
- **AI cost.** An analysis asked the AI provider for the same text twice, and again each
  time a report was reopened. Each question is now asked once.
- **Document types.** IEEE conference papers, and any record whose source carried no
  type, were counted as journal articles. They are now classified from what each
  database records about the document.
- **Emerging themes.** Terms with no history to spike over are listed as new or
  concentrated terms; a spike must stand clear of its own history; a score at the
  mathematical ceiling is marked as such in the table.
- **Transitions** no longer list a topic as both emerging and persistent.
- **Institutions and countries.** "NA" placeholders are dropped; spelling variants that
  differ only by diacritics are one institution; Lesotho, Eswatini and Georgia resolve.
- **Cited works that Scopus returns without a title** (books, for example) are no longer
  merged with other works of the same author and year.
- **Bibliographic-coupling hubs** are named by title and ranked by citations; the
  network views also draw the smaller groups and say how many nodes and clusters are
  shown of the total.
- **"Refresh figures"** on a report opened from the Library no longer fails.

### Literature review (PRISMA 2020)
- **The flow adds up.** Your decision overrides the AI verdict in every box: a record
  you exclude after an "uncertain" verdict is counted as excluded, and an AI exclusion
  you include moves on to full text. Records removed before screening for reasons other
  than duplication have their own box.
- **Included means judged eligible.** A study is included only when you mark its full
  text eligible; retrieving it, or finding an open-access link, is no longer enough.
  Each full-text exclusion cites the criterion it fails.
- **Screening.** A failed AI call is no longer saved as an "uncertain" verdict; the
  record stays unscreened and is retried. The Claude subscription screens one record at
  a time. You can stop a run and keep every verdict so far. The screener also sees each
  record's document type and database.
- **Nothing is lost silently.** Replacing the library, changing the criteria after
  screening, or importing a review with the same name now asks first and keeps your
  decisions.
- **Methods text written from your review.** The Methods text of the PDF and Word reports describes what was
  actually done in your review: how many records the AI decided alone and how many you
  decided, whether the criteria changed, and where the full texts came from.
- **Validation** samples half of its records from the AI exclusions and estimates how
  many relevant records the AI may have missed, with a 95% interval; you can apply your
  ratings to the review.
- **Themes** are proposed from every record that passed screening, and deleting a theme
  no longer moves records to another one.
- **References.** Scopus searches keep volume, issue and pages, and "Fill locators"
  completes older records from Crossref.
- **Full-text retrieval.** A record is noted as "no open-access copy found" only when
  that is the answer, not when OpenAlex was too busy to answer. The publisher download
  sends your Scopus key and institution token to Elsevier's own address only.

## 0.7.5 (2026-09)

Report integrity. An external review found invented facts in AI paragraphs and
wrong statistics in the tables of a 0.7.4 report; every point was confirmed on
three real corpora. 0.7.5 fixes the causes. **Reports generated with earlier
versions should be regenerated before they are used in a manuscript**; the
release notes list the affected sections.

### Fixed
- **Numbers.** Countries, authors and institutions are counted by records, not
  by affiliation strings or network links; venue and reference totals cover the
  whole corpus, not the listed slice; growth is measured over complete years
  from a real base year; the m-index is anchored on the first year with real
  output; only keyword communities of three or more keywords count as themes.
- **Statistics that could not hold.** Emerging-theme scores that hit the
  mathematical ceiling are no longer presented as bursts; Bradford and Lotka are
  tested before the report says a law holds; every adaptive threshold prints
  what was applied. Statistics that do not hold on a corpus print a caveat or
  "not computable" instead of a number.
- **AI paragraphs.** Every AI call is built from the analysis itself and its
  answer is checked against the data it was given: a paragraph that cites a
  value not in the analysis is regenerated once and otherwise withheld, with a
  visible note and an "AI generation log" at the end of the report. Each AI
  paragraph shows its model, date and prompt version.
- **Relevance screening** now judges records against the research question you
  state (or the Research Pilot question), never against an AI-written title.
- **Saved analyses** open with the date and engine version they were computed
  with; older analyses show a Legacy badge and keep their original report.
- **Literature review.** Records the screening never reached are reported as
  such (not as screened and excluded); the curated export is exactly the PRISMA
  included set, with not-retrieved records listed beside it; citation keys are
  assigned once and never change between exports; the year clause recorded for
  each database query is checked against the records and flagged when they
  disagree.

### New
- Entity canonicalisation before counting: keyword variants and acronyms,
  journal abbreviations across databases, country names, multi-campus
  institutions, author identifiers, and one key per cited work across PubMed,
  Scopus and CSV references (resolved when sources are consolidated).
- A "Research question this corpus was searched for" field in the analysis
  options.
- A canonicalisation log and a generated methodology section in every report;
  document type, volume, issue, pages and ISSN carried through consolidation
  and into the curated export.

## 0.7.4 (2026-09)

AI providers and models: current model lists, requests that work with today's
vendor APIs, and error messages that tell you what to do next. This release
also carries the 0.7.2 and 0.7.3 changes, which were not published separately.

### New
- **Current model choices for every provider.** The model list is fetched from
  the vendor when a key is saved, with the recommended picks first (cheap /
  mid-tier / frontier badges), the default marked, and a Custom entry for
  anything newer. The defaults are now Ministral 8B (Mistral), GPT-5.4 nano
  (OpenAI), Claude Haiku 4.5 (Anthropic API) and Claude Sonnet 5 (Claude Code
  subscription).
- **Validate checks two things:** that the key is accepted, and that the
  selected model actually answers on your account. If the key is fine but the
  model is not included in your plan, the panel says exactly that.
- **Change the model on the spot.** When a model is not available to your
  account, is unknown to the provider, or your installed Claude Code is too old
  for it, the message names the problem and opens the model picker.

### Fixed / improved
- **OpenAI and the newer Anthropic models answer again.** Requests are now
  shaped the way each vendor requires; before this release every OpenAI call
  and the newer Claude models (Sonnet 5, Opus 5, Fable) failed.
- **Mistral free tier.** The models the free plan does not include (Mistral
  Small / Medium / Large) are no longer the default and are no longer retried
  with a "try again in a minute" message; the app tells you the plan has no
  allowance for that model and offers another.
- **The model you pick is saved immediately** and shown in the header pill,
  including for the Claude Code subscription; switching provider no longer
  resets your choice.
- The Claude subscription card and the header token counter display correctly.
- A model that declines to answer is reported as such, with the suggestion to
  switch model, instead of a generic error.

## 0.7.3 (2026-08, not published separately)

Chronicle videos, after a frame-by-frame review of a real video.

### Fixed / improved
- **Countries are countries.** Cities, e-mail addresses and stray affiliation
  text no longer appear in the country race.
- **Continuous narration.** One script is written for the whole video, so the
  scenes stop restating the same names and years; the script is saved next to
  the audio file.
- Thematic-map quadrants use one consistent legend and marker set; periods with
  no emerging topics no longer render empty; duplicate drift labels are gone;
  the keyword network is laid out readably.

## 0.7.2 (2026-07, not published separately)

### Changed
- **Licenses are tied to the computer they are issued for.** Your Machine ID is
  shown in About and on the trial-expired screen, with a copy button, so you can
  send it when requesting a key. Keys issued without a machine binding are no
  longer accepted.

## 0.7.1 (2026-07)

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

## 0.7.0 (2026-07)

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

## 0.5.1 (2026‑06)

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

## 0.5.0 “Chronicles” (2026‑06)

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
