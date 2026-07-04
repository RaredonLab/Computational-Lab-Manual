# CLAUDE.md — Raredon Lab Computational Manual

## Project overview

A computational lab manual for the Raredon Lab (PI: Dr. Micha Sam Brickman Raredon, Yale School of Medicine, Dept. of Anesthesiology). The lab works in lung regeneration, pulmonary fibrosis, spatial transcriptomics, ex vivo bioengineering, and computational biology.

The deliverable is a linked set of standalone HTML files — readable in a browser, hostable on a website, sharable with new lab members. Each document covers one major topic; all share a sidebar navigation linking the full set. Hosted on GitHub Pages.

This is one of three sibling lab manuals. See **Sister manuals** below for cross-linking context.

---

## Document status — all complete

| File | Title | Status |
|------|-------|--------|
| `index.html` | Overview & index | **Complete** |
| `01-onboarding.html` | Onboarding | **Complete** |
| `02-computing-environment.html` | Computing environment | **Complete** |
| `03-git-workflow.html` | Git & GitHub workflow | **Complete** |
| `04-coding-standards.html` | Coding standards | **Complete** |
| `05-data-management.html` | Data management | **Complete** |
| `06-ai-tools.html` | AI tools & Claude | **Complete** |
| `07-ethics-teamwork.html` | Ethics & teamwork | **Complete** |
| `08-publication.html` | Publication & archiving | **Complete** |
| `appendix-a-exit-protocol.html` | Appendix A: Lab exit protocol | **Complete** |

---

## Design system

All documents share identical CSS. Copy the variables block exactly into every new file.

**Fonts (Google Fonts):** IBM Plex Serif (headings), IBM Plex Sans (body), IBM Plex Mono (code/labels)

**CSS variables:**
```css
:root {
  --sidebar-w: 256px; --header-h: 54px;
  --bg: #FFFFFF; --sidebar-bg: #F6F5F1; --border: #E3E1DC;
  --text-p: #1A1917; --text-s: #5C5A56; --text-t: #9C9A96;
  --accent: #1D4ED8; --accent-lt: #EFF6FF; --accent-bd: #BFDBFE;
  --code-bg: #F6F5F1; --code-bd: #D8D6D0;
  --note-bg: #F0FDF4; --note-bd: #16A34A;
  --warn-bg: #FFFBEB; --warn-bd: #D97706;
  --rule-bg: #FFF1F2; --rule-bd: #E11D48;
  --font: 'IBM Plex Sans', sans-serif;
  --font-serif: 'IBM Plex Serif', serif;
  --font-mono: 'IBM Plex Mono', monospace;
}
```

**Layout:** Fixed dark header (`#141210`, 54px). Fixed left sidebar (256px, `--sidebar-bg`). Content: `margin-left: 256px`, `max-width: calc(256px + 800px)`, `padding: 52px 60px 100px`. Sections use `scroll-margin-top: calc(var(--header-h) + 20px)`.

**Component classes:**
- `.call.note` — green callout (tips)
- `.call.warn` — amber callout (cautions)
- `.call.rule` — red callout (hard requirements)
- `.call.info` — blue callout (context/PI notes)
- `.cb-wrap` + `.cb-label` + `<pre>` — labeled code blocks
- `.steps` + `.snum` — numbered steps with blue circles
- `.dodont` — two-column do/don't grid
- `.diagram-wrap` — SVG diagram container
- `h2` with `.sn` span — section headers with `§N` badge

Sidebar nav: active doc gets `class="active" aria-current="page"`. Scrollspy uses `.here` on `.toc-link` elements. Sidebar includes an **Appendices** section below the main documents list, with its own `<hr class="sb-div">` separator.

---

## Writing principles

Apply to every sentence of prose in every document.

1. **Limit em-dashes.** Only where a comma or colon would genuinely be weaker. One or fewer per paragraph. Never use them as stylistic parentheticals. When in doubt, use a colon or restructure the sentence. Always grep for `—` before finalizing a document.

2. **No self-negation / auto-negation.** Cut any "not X, it's Y" construction. Speak directly to what is true; do not set up what it is not first.

3. **No rhetorical triplets.** Avoid three-part parallel constructions unless each element is informationally distinct.

4. **Never use "genuine" or "genuinely."** Find a more specific word or restructure.

5. **Frame as guidance, not group mandate.** Use second person ("you") in instructional prose. When a hard requirement exists, state it and give the reason. Do not appeal to lab identity to justify rules.

6. **Nurturing tone.** Readers are learners. Frame standards in terms of their payoff. Do not make readers feel bad for exploratory work.

7. **Assume an intelligent reader.** Do not over-explain. Write as a thoughtful senior scientist would write for peers new to specific conventions.

---

## Hard rules on content

- **No specific lab member names** anywhere. Use role descriptions or generic initials (AB, CD) in examples.
- **No specific R package names** except NICHES. Use generic descriptions.
- **No "we" framing** in instructional prose except in the lab mission/identity context (Document 01 §1).
- **No visualization drafts as an AI task.** Drawing and visualization design are human thinking activities.
- **Reading and writing scientific papers** (methods, results, discussion, figure captions) is reserved for human authors. AI may assist with grant text only.

---

## Process for drafting new or revised documents

1. Elicit content from the PI first. Do not invent conventions.
2. Draft as a complete, browser-ready HTML file using the design system above.
3. Present with `present_files`.
4. Iterate using `str_replace` for targeted edits.
5. Before finalizing: grep for `—` (em-dashes), scan for self-negation and "genuine/genuinely."

---

## Content decisions by document

### index.html
- Dark hero section with lab name, manual title, subtitle, PI/department metadata.
- 2-column document card grid (8 cards). Cards for incomplete documents show a "Coming soon" pill and are non-clickable.
- Appendices section below grid as a list of cards.
- "How to use this manual" callout at the bottom.
- No sidebar; full-width layout.

### Document 01 — Onboarding
- **§1:** Single tight paragraph — "Overview of the computational wing of the Raredon Lab." Cell-to-cell signaling, generalizability, visualization as intellectual lens, graph-structured data, serving the larger team.
- **§2:** Why the manual exists.
- **§3:** First-week checklist (7 numbered steps). Three storage locations: lab HPCs, Raredon Lab server (`smb://storage.yale.edu/home/RaredonLab-CC1126-MEDANE`), RaredonLab SharePoint.
- **§4–§7:** Who to ask, tools/resources, what a good week looks like, being a good colleague.
- **§8:** The four steps of data science — visual card flow: Acquisition → Exploration → Analysis → Communication.
- **§9:** "Things worth remembering" — five maxims with brief explanatory paragraphs (quote-left + body-right layout).

### Document 02 — Computing environment
- Hardware: 16 GB RAM min, 100 GB free storage, Mac SSD swap note, lab workstations first-come-first-served.
- HPC: McCleary (YCRC). SSH or Open OnDemand. SLURM examples included.
- Three storage locations with paths/URLs and retention guidance.
- Software list (16 items in install order): R, Python, RStudio/Positron, Git, GitHub Desktop, Claude, Adobe Illustrator, EndNote/Zotero, Microsoft Office, Slack, XeniumExplorer, Docker, QuPath, FIJI, Cisco AnyConnect, OneDrive Desktop.
- R large-memory config: `.Rprofile` settings, `lobstr`, BPCells, SLURM memory examples.
- NICHESv2: private repo, requires collaborator access, `devtools::install_local()`.
- renv guidance included.
- §6: Interactive HTML checklist (27 items, 4 groups) with live progress bar. JS toggle only, no localStorage.

### Document 03 — Git & GitHub Workflow
- Fork model: RaredonLab origin (`main` + `dev`) → personal fork (`username/repo-initials`) → local clone.
- `dev` default; `main` protected (PI only). Self-approval allowed if no conflicts and no shared infrastructure changes.
- `functions/` for helpers (not `R/`). File naming: `NN_YYYYMMDD_AB_descriptive-name.ext`.
- Standard R `.gitignore` template included. End-of-day push mandatory.
- `CLAUDE.md` in every repo root. Claude can write commit messages.
- Fork model SVG diagram: PI-only arrow points dev → main; PR arrow on right side.

### Document 04 — Coding Standards
- Three categories: Scripts (.R), Rmarkdown (.Rmd → .html), R Packages (CRAN).
- Scripts: header block required (title, author, date, purpose, inputs, outputs, libraries, paths — in that order). One operation per script. Exploratory OK; clean up before sharing.
- Rmarkdown: teaching/polishing tool, script first. YAML header standard. Global chunk options suppress noise. Named chunks. HTML to `docs/`.
- Helper functions: >~25 lines → `functions/`. Roxygen preferred. No hardcoded values.
- R packages: build with Claude Code or similar AI. Standard tools (testing, documentation, pkgdown). Vignettes and demo scripts required.
- Publication-ready code: linear execution, load from disk/operate/save to disk, date stamps.

### Document 05 — Data Management
- Core principles: raw data inviolable, scratch vs. permanent record, linear workflows.
- Three storage locations: HPCs (active/temporary), lab server (long-term archive, backed up), SharePoint (active collaboration, no VPN needed).
- Raw data: sequencing/Xenium → lead bioinformatician → lab data library; imaging → personal server folders; external → lead bioinformatician.
- Processed outputs: elegant save points (no redundant intermediates). Critical tip: save metadata changes as CSV, not as a re-saved whole object.
- Computational lab notebook: daily notes (date, filepaths, script names, reasoning, problems, open questions).
- External sharing: SharePoint/OneDrive preferred.
- Common mistakes: too many intermediates, re-saving whole objects for metadata changes, poor imaging file labeling, excessive microscopy accumulation, non-linear workflows (code example included).
- Appendix A referenced for exit protocol (separate document).

### Document 06 — AI Tools & Claude
- AI as HMI tool. De-skilling is a personal choice. The thinking comes before the prompt.
- Hard limits: reading/writing scientific papers (methods, results, discussion, captions) is human work. Grant text may be AI-assisted. Visualization design is human.
- Session setup: load `CLAUDE.md` first, provide goals/open questions/current task/style preferences.
- `CLAUDE.md` files: every repo has one. Content: what, how, current state, open questions. Keep focused.
- Skills files: `SKILL.md` in `.claude/skills/`. Committed to Git. Aspirational lab Skills library.
- Prompting: long specific prompts. Describe data structure, never upload raw data. Iterate deliberately. Literature reviews need verifiable PMIDs/DOIs.
- Hallucination: prioritize verifiable tasks. Never publish a fake citation.
- Attribution: AI noted in commit messages, script headers, publications. Humans write all paper text except grant drafts.
- Yale policy: `provost.yale.edu/news/guidelines-use-generative-ai-tools`. No moderate/high-risk data in AI tools.
- Evolving badge displayed; opting out allowed.

### Document 07 — Ethics & Teamwork
- Authorship: CRediT taxonomy. Conversations begin at project start. First authorship = significant responsibility. Gift authorship not acceptable. Disputes to PI in private.
- Credit: 1+n rule — one meaningful conversation → acknowledgments; +n conversations → offer authorship.
- Acknowledgments: all funding, collaborators, resources. Cross-reference to General Lab Manual (in development).
- Data integrity: team interpretation of results, figure craft as multi-month process, negative results are results.
- Errors: self-errors acknowledged honestly and openly ("Perfection can be boring. Failure is often interesting."). Others' errors: schedule a meeting, listen first, then offer help. Misconduct to PI in private.
- Lab culture: respect for focus/quiet, ask about screens sparingly, share code via GitHub.
- Disagreement with PI: Rule of Three (note/table it; write it out/discuss; do the task).
- Communication: 1–2 seminars/week. Slack: few business days. Email: 24 hours. Weekends protected.
- Yale resources table: Research Integrity office, SHARE, Title IX, OIEA, GSAS, Mental Health.
- PI's role: stated explicitly. Ends: "If the PI is failing at any of these things, please say so. We will adjust."

### Document 08 — Publication & Archiving
- Figures: 300 dpi PNG, file linking in Illustrator (required), Arial/Helvetica ≥6 pt, distinguishable colors with legend, all axes labeled, inspect at high zoom.
- Image integrity pipelines: R → disk → Illustrator (computational); machine → raw → crop/adjust → Illustrator (microscopy).
- Code release: GitHub repo per paper. Minimum = organized code dump. Ideal = README + scripts + vignettes + package.
- Data deposition: GEO (sequencing) + Figshare (processed/supplementary). Both raw and processed. Check with PI before any public release.
- Manuscript process: 6 numbered steps. In-person submission meeting with PI (1 hour). PI is corresponding author by default. Every revision round repeats the full process.
- Preprints: case by case with PI.
- Archiving: complete = peer-reviewed and published. Server README + GitHub + GEO/Figshare accessions all in place.

### Appendix A — Lab Exit Protocol
- Standalone HTML document with same design system.
- Sidebar shows main docs + Appendices section (A highlighted as active).
- 5 sections: overview, data/files, GitHub, accounts/access, exit checklist.
- Interactive checklist (14 items, 4 groups) with progress bar. JS toggle only.
- Data/files section includes hard rule: no data left on personal hardware at exit.

---

## Sister manuals

Two sibling lab manuals are in development in separate repositories and new Claude chats:

| Manual | Scope | Status |
|--------|-------|--------|
| **General Lab Manual** | All lab members. Authorship principles, first author responsibilities, mentorship, career development, general lab policies and culture. | In development |
| **Wet Lab Manual** | Wet lab and bioengineering members. Safety, equipment, cell culture, bioengineering protocols, paper lab notebooks, reagent management, microscopy. | In development |

**Cross-linking:** Once all three manuals are live on GitHub Pages, insert absolute URLs for cross-references. Current placeholder cross-references in this manual:
- Document 07 §1 and §2: "General Lab Manual — Authorship Principles and Responsibilities of First Authors"
- Document 08 §5: "General Lab Manual — Responsibilities of First Authors"

Update these to absolute links once the General Lab Manual URL is established.

---

## PI context and sensibility

- Lab's published tool: NICHES (cell-to-cell communication framework). Other packages exist but are not named in the manual.
- Storage: three distinct locations — lab HPCs, Raredon Lab server, RaredonLab SharePoint. All three mentioned wherever storage is discussed.
- HPC: McCleary (Yale Center for Research Computing).
- IDE: Positron preferred; RStudio supported.
- The PI's writing sensibility is rigorous, direct, and academic. The manual should read like it was written by a thoughtful scientist.
- Strong PI opinions: drawing/visualization as human thinking; reading and writing papers as human thinking; AI citation integrity; crediting original authors; data provenance.
