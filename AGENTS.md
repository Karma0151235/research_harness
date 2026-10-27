# AGENTS.md — research_harness

Operating manual for any agent doing research, analysis or writing in this repository.
It holds the **bootstrap protocol**, **general rules**, **quality gates**, and a **Knowledge Base**
distilled from a Masters research methodology course (§5.1–5.16), extended to
doctoral / journal standard (§5.17 onward). **All work is held to doctoral standard** (§0.6).

Direction of travel: the harness keeps growing (§7) toward a research assistant that produces
the work end-to-end, so that the researcher's job is to brainstorm and decide the direction.
How much the agent produces in any one project is set by its **agent mode** (§0.5).

The harness is **plug-and-play**: this file, `CLAUDE.md`, `README.md` and `templates/` are tracked.
Everything personal or project-specific (`PROFILE.md`, root `PROGRESS.md`, project folders, course
materials) is local and git-ignored.

> Precedence: user instruction in the current session > project `AGENTS.md` > `PROFILE.md` > this file.
> If two rules conflict and precedence does not settle it, stop and ask the user.

---

## 0. Bootstrap protocol (MANDATORY — before doing anything else)

Every task, every session, no exceptions:

1. **Read this file** (`/AGENTS.md`) in full.
2. **Read `/PROFILE.md`** (researcher, institution, defaults, AI-use policy). If it does not exist,
   copy `templates/PROFILE.md`, ask the user to fill the blanks, and do not guess any field.
3. **Read root `/PROGRESS.md`** (portfolio of projects, deadlines, harness work). If missing, copy
   `templates/ROOT_PROGRESS.md`.
4. **Identify the project** the task belongs to.
5. **Read the project's `AGENTS.md` and `PROGRESS.md`.**
   - If the project folder or either file does not exist → **create them first** (§0.1) and
     show the plan to the user before doing substantive work.
   - If the task belongs to no project (e.g. harness maintenance) → use the root `PROGRESS.md`.
6. **Re-state the current step** from `PROGRESS.md` in one line before acting
   ("Working on G1 / Step 3.2 — critique of Article 1 framework").
7. **Do the work for that step only.** If the user's request does not match the next unchecked step,
   say so and either (a) add it to `PROGRESS.md` as a new step, or (b) ask which takes priority.
8. **Update `PROGRESS.md` at the end of every step** (tick the box, add date, evidence, and any
   decisions). Never tick a box without evidence (file path, command output, or check result).
9. **Before ending the session**, write a short `Handoff` entry in the project and root
   `PROGRESS.md`: what was done, what is next, open questions. Append to `admin/AI_USE_LOG.md`.

### 0.1 Creating a new project

```
<PROJECT>/
├── AGENTS.md          # project-specific requirements, parsed from the brief (§0.2)
├── PROGRESS.md        # step-by-step plan with checkboxes (§0.3)
├── admin/
│   ├── AI_USE_LOG.md         # running log of AI assistance: the "work trace" (§2.4)
│   ├── AI_Declaration.*      # filled from the log once the institution's form is available
│   └── PAP.md                # pre-analysis plan (all empirical work; §2.6)
├── brief/             # notes on the brief (never commit copyrighted originals)
├── sources/
│   ├── references.md  # every source: APA entry + DOI + verification + index status + read status
│   └── review_matrix.md     # Author/Year | Purpose | Method & Data | Key Findings | Relevance [L3]
├── analysis/          # code (§3); data/README.md from templates/DATA_README.md
├── drafts/            # outlines, user drafts, pushback memos, versioned vNN
└── output/            # final deliverable (PDF/DOCX) + submission checklist
```
Project folders are git-ignored by the harness. To version a project, `git init` a **private**
repository inside its folder; never push course materials or copyrighted PDFs.

### 0.2 Project `AGENTS.md` must contain

1. Header: course/context, assessment name, weight, group size, deadline (date + time + mode of
   submission), **agent mode** (§0.5).
2. The questions/tasks **verbatim**, each with its marks.
3. A **requirements matrix**: every explicit requirement → where it is satisfied → how it is checked.
   Include implicit requirements ("critical engagement", "cite other studies", "minimum 2 WoS articles").
4. Format requirements (title page fields, font, referencing, file format, hard copy).
5. Permitted AI level for this assessment (from `PROFILE.md` §3) and what that means for the workflow.
6. Which Knowledge Base sections (§5) and playbooks (§6) apply, by number.
7. Mark allocation → word/effort budget (effort proportional to marks).
8. Open questions for the user (missing names, IDs, programme, choices).

### 0.3 `PROGRESS.md` format

```markdown
# PROGRESS — <project>
Status: <Not started | In progress | Blocked | Review | Done>   Last updated: YYYY-MM-DD
Deadline: YYYY-MM-DD HH:MM   Days left: N   Mode: <Assist/Produce>   Next gate: <G0–G5>

## Plan
- [ ] 1. <Phase>
  - [ ] 1.1 <Step> — Done when: <objective check> — Evidence: <path/output>
...
## Drift check (run at every step)
- Does this step trace to a question/requirement in AGENTS.md? (cite it)
- Is anything being produced that no requirement asks for? (cut it)
- Are marks and effort still proportional?
## Decisions log   (date — decision — reason)
## Open questions  (date — question — owner)
## Handoff         (date — done / next / blockers)
```

Rules for plans: steps are small (one sitting), each has a **"Done when"** criterion that someone
else could verify, gates (§0.7) appear as explicit steps, and the last phase is always
**QA against the requirements matrix** (§6.3).

Templates for all of the above live in `templates/`. Copy them; do not improvise a new format.

### 0.4 Open-ended projects (topic not fixed by the brief)
Examples: an applied-methods assignment on "a research problem of your choice", a research proposal,
a dissertation or thesis chapter. Before any research on content:
1. Read the prompt **and the rubric** (marking scheme) in full; put both into the project `AGENTS.md`.
   If the rubric is not available, say so and ask for it. Do not guess the marking criteria.
2. Propose **2–3 candidate topics** per open-ended part, each with: research problem (general →
   specific), why it fits the method asked for, data source and its availability, 2+ anchor studies
   (indexed where required, marked `[verify]` until checked), the contribution type (§5.19), and
   risks. Give a recommendation.
3. **Stop and let the user choose.** Record the choice in the Decisions log. Only then plan the content phases.

### 0.5 Division of labour: agent modes
The researcher always owns the **direction** (questions, topic, contribution, key design choices)
and is accountable for the result. How much the agent produces depends on the project's mode,
declared in the project `AGENTS.md`. The mode is **capped by the AI-use policy** that applies to
the work (`PROFILE.md` §3, or the target journal's/institution's policy). If the policy is
unclear, use Assist and ask.

**Produce mode** (default where policy allows: own research, papers, non-assessed work):
- Brainstorm with the researcher first: candidate directions, contributions, risks (§0.4, §5.19).
  Record the researcher's decisions in the Decisions log; do not decide direction alone.
- Then produce the work end-to-end: literature, data, analysis, full drafts, tables, figures,
  replication package, passing every gate (§0.7).
- At each gate, give the researcher a short decision brief (what was done, what was found, the
  choices made and the alternatives) so they can steer and can defend every part (§6.8).
- Disclose AI use as the venue requires; AI is never listed as an author.

**Assist mode** (when policy limits AI, e.g. assessed coursework at a restricted level):
- **Research**: literature search, reading, verified reference lists, evidence banks, data scouting.
- **Outlines**: argument structure in bullet form, linked to the requirements matrix and to sources.
  Each bullet is a claim plus its evidence, not finished sentences for submission.
- **Pushback**: a critical memo on each user draft (`templates/pushback.md`, §6.5): weak arguments,
  missing evidence, mark-scheme gaps, APA errors, logic problems (§5.2 reliability tests). Be
  direct; flag severity.
- **Feedback loops**: iterate draft → pushback → revision until the QA gate (§6.3) passes.
- **Analysis code** (empirical projects): written to §3 standards; the user must be able to explain
  every modelling choice.
- The user writes the **final prose**. Agents do not write submission-ready paragraphs unless the
  user explicitly asks for one in the current session; log each such request in `admin/AI_USE_LOG.md`.

In both modes every AI contribution is logged (§2.4) and the declaration describes actual use.
Files: outlines go in `drafts/outline_<part>_vNN.md`, pushback in `drafts/pushback_<part>_vNN.md`,
drafts in `drafts/<part>_vNN.md` (or a .docx the user points to).

### 0.6 Rigour standard: always doctoral
Every project, whatever its weight or audience, is done to the standard of a strong doctoral
thesis chapter or journal paper. Rigour is never scaled down; only **presentation** adapts to
the audience and the brief (length, format, depth of notation). Rigorous work, well presented, is
digestible for any reader. Concretely, every project gets:
- A structured, logged literature search (§6.4), positioned against the frontier (last 3–5 years
  of top field journals) as well as the classics; systematic review with a PRISMA flow when the
  question calls for one (§5.18).
- An explicit contribution statement (§4.5, §5.19) and a conceptual framework that generates the
  hypotheses (§5.5).
- Identification defended against the strongest alternative explanation, with the estimand
  stated (§5.17); a threats-to-validity table (§5.7).
- For empirical work: a frozen pre-analysis plan, pre-specified robustness, multiple-testing
  control, power / minimum detectable effect (§2.6), and a replication package that runs on a
  clean environment (§3.15).
- An independent referee-style review before submission (§6.5) and viva-style preparation (§6.8).
When a brief's length limit forces cuts, cut breadth, not rigour: fewer points, each fully
argued and evidenced. Keep extra rigour in appendices or the work trace if the format allows.

### 0.7 Quality gates
A gate is a stop: record pass/fail with evidence in the Decisions log before moving on. A failed
gate means revising the earlier step, not pushing ahead.

| Gate | Before | Pass when |
|---|---|---|
| **G0 Problem** | Literature work | General → specific problem written; gap stated with **why it matters**; RQ ↔ RO table 1:1 (§5.3); feasible with available data/time |
| **G1 Design** | Data/analysis | Method follows from the RQ, not the reverse (§2.3); identification assumptions listed with how each is assessed; empirical work: PAP frozen |
| **G2 Evidence** | Outlining/writing | Every source to be cited is verified and read at least to the claim it supports (§2.1); review matrix complete; contrary evidence included |
| **G3 Analysis** | Interpreting results | Code runs end-to-end from raw (§3); diagnostics reported; robustness list executed; deviations from PAP logged |
| **G4 Draft** | Final QA | Pushback has no open "major" items; argument passes the reliability tests (§5.2); every claim cited or evidenced |
| **G5 Submission** | Hand-in | §6.3 QA passed; AI_USE_LOG and declaration complete; exported file opened and checked |

---

## 1. Repository map

Tracked (the harness):

| Path | What it is | Rules |
|---|---|---|
| `AGENTS.md` | This manual | Change with user approval; record the change in `CHANGELOG.md` |
| `CLAUDE.md` | Imports AGENTS.md for Claude Code | Pointer only; all rules live here |
| `README.md` | Quick start for a fresh clone | Keep in sync with §0 and §1 |
| `CHANGELOG.md` | Harness change history | One entry per change, dated |
| `templates/` | PROFILE, ROOT_PROGRESS, PROJECT_AGENTS, PROJECT_PROGRESS, references, review_matrix, AI_USE_LOG, pushback, PAP, DATA_README | Copy when creating files (§0.1); do not improvise formats |

Local only (git-ignored):

| Path | What it is | Rules |
|---|---|---|
| `PROFILE.md` | Researcher, institution, defaults, AI-use policy | Fill only from the user |
| `PROGRESS.md` | Workspace portfolio and harness work log | Updated every session |
| `<PROJECT>/` | One folder per assessment / research project | Structure per §0.1 |
| `Course/` (or as named in PROFILE §4) | Course materials behind the [L*] tags in §5 | Read-only. Never commit, never upload to public platforms, never copy large verbatim chunks into tracked files |
| Any other files the user adds (spreadsheets, PDFs) | Inputs | Treat as local and confidential unless the user says otherwise |

Text extracts of local course files can be regenerated with `python-pptx`, `python-docx`, `pypdf`
into a scratch directory (never commit them).

---

## 2. General rules

### 2.1 Academic integrity (non-negotiable)
- **Never fabricate** a source, quotation, page number, statistic, DOI, dataset, or result. If you
  cannot verify it, write `[UNVERIFIED]` and tell the user.
- **Never cite from memory.** A reference recalled by the model is a lead, not a source, until it
  is verified (next rule) and read.
- **Verify every reference** before it enters a draft: resolve the DOI (doi.org / Crossref) or find
  the publisher page; confirm authors, year, title, journal, volume, issue, pages. Prefer the
  version of record over working papers; note when a working paper has since been published.
  Record status in `sources/references.md` as `verified (DOI resolved, YYYY-MM-DD)`.
- **Check for retractions and corrections** (Crossref update metadata / Retraction Watch) for any
  source a key argument rests on. Avoid predatory or hijacked journals; when unsure, check the
  journal against Clarivate MJL, Scopus or DOAJ.
- **"Do not reference a source without having actually read it"** [L3]. Minimum: abstract +
  the section supporting the claim. If you only read a secondary account, use secondary citation
  format (§4.4).
- **Index requirements** (e.g. "Web of Science articles"): verify indexing (Clarivate Master
  Journal List — SCIE/SSCI/AHCI/ESCI) and record the index + check date. If it cannot be verified
  directly, record the secondary evidence and say so.
- **Report all results, admit all limitations** [L7]. No trimming, cooking or forging data [L7].
- Avoid the **Seven Deadly Sins** [L7]: carelessness (citation bias, understatement), redundant
  publication, unfair authorship, undeclared conflict of interest, ethics-approval violations,
  plagiarism, other fraud (fabrication/falsification, misappropriating ideas).
- Paraphrase genuinely; quote sparingly with page numbers. Run a self-check for close paraphrase
  of any source you read.

### 2.2 Confidentiality and copyright
- Uploading confidential or copyrighted material to public platforms is **prohibited**.
  Course slides, articles, briefs and personal data stay local.
- Do not paste whole articles or slide decks into tracked files; summarise and cite.
- Before any `git push`, check that only whitelisted harness files are staged (`git status`).
- Participant data (if any primary research): anonymise, store outside git, follow §5.16.

### 2.3 How to work
- **Problem and objectives drive methods — never the reverse** [L5, AA08803]. "Models are the
  means rather than the ends."
- Effort is proportional to marks. Spend the most care on the highest-mark parts.
- Prefer one clear, defensible argument over a list of everything that could be said.
- **Steelman before you critique**: state the strongest version of an author's design or claim,
  then show precisely where it fails and how much it matters (major / moderate / minor).
- Ask the user when a choice is genuinely theirs (topic selection, member details, tone).
  Otherwise pick the conventional default, state it in the Decisions log, and proceed.
- Commit to git only when the user asks; never commit local-only paths (§1).

### 2.4 AI declaration (every project)
The institution's AI-use policy (permitted level per assessment type, permitted tools, declaration
obligations) is recorded in `PROFILE.md` §3. Common obligations: declare the tool and the role of
AI, state how AI contributions are acknowledged, and be ready to provide logs/drafts/work traces or
answer oral questions.

Procedure for every new project:
1. Create `admin/AI_USE_LOG.md` from `templates/AI_USE_LOG.md` at project start and append to it
   **every session** (date — tool — task — output file — what the user kept/changed). This log,
   together with `PROGRESS.md` and the versioned drafts, is the work trace an assessor may request.
2. **Declaration document**: fill the institution's form (path in `PROFILE.md` §3) from the log.
   If the form is not yet available, the log is the declaration artefact until it is.
3. The declaration must describe the **actual** use recorded in the log: concise, factual and
   professionally worded. Agents do not understate the level or the role of AI. If the user asks for
   that, decline and offer an accurate wording instead. If planned use would exceed the permitted
   level, stop and tell the user before proceeding.
4. Members must be able to explain every part of the submission orally (§6.8). Flag sections the
   user should review closely.

Member/identity fields default to **blank** in every new project. Fill them only from
`PROFILE.md`, the project's `AGENTS.md`, or the user.

### 2.5 Definition of done (any deliverable)
- Every requirement in the project matrix is met and evidenced; all gates passed (§0.7).
- Every in-text citation ↔ reference-list entry, one-to-one [L7]; all references verified.
- APA 7 throughout (§4.4) unless the brief says otherwise; format requirements met.
- Spelling/grammar pass done; numbers, tables and figures referenced in text.
- AI_USE_LOG current; AI declaration filled.
- Final prose is the user's (§0.5); any agent-written passage the user asked for is logged.
- Final file exported in the required format; submission checklist ticked in `output/`.

### 2.6 Transparency and reproducibility (all projects)
- **Pre-analysis plan** (`templates/PAP.md`) frozen before outcome data are examined: hypotheses,
  variables, primary specification, robustness list, inference choices. Deviations are allowed but
  logged with date and reason [EXT – verify: Nosek et al., 2018; Christensen & Miguel, 2018].
- **Researcher degrees of freedom**: flexible choices of sample, controls, transformations and
  outcomes inflate false positives; pre-specify them or show results across them (specification
  curve) [EXT – verify: Simmons et al., 2011; Simonsohn et al., 2020].
- **Multiple hypotheses**: with several outcomes or subgroups, control the family-wise error rate
  (Romano–Wolf stepdown, Holm) or the false discovery rate (Benjamini–Hochberg) and say which
  [EXT – verify: Benjamini & Hochberg, 1995; Romano & Wolf, 2005].
- **Power**: report the minimum detectable effect, MDE ≈ (t₁₋κ + t_α/2) · SE(β̂), and treat
  insignificant results from underpowered designs as uninformative, not as evidence of no effect
  [EXT – verify: Ioannidis et al., 2017].
- **Data management**: data provenance README (`templates/DATA_README.md`); raw data immutable;
  FAIR principles where data are shared [EXT – verify: Wilkinson et al., 2016].
- **Report effect sizes with uncertainty** (confidence intervals), not only stars or p-values.

### 2.7 Agent epistemics
- Label claims by status: **read** (from a source read in this project), **verified-metadata**
  (exists, not read), **recalled** (model memory, unverified), **inferred** (agent reasoning).
  Only **read** sources support claims in user-facing drafts.
- Mark non-course or uncertain methods guidance `[EXT – verify]` until checked against a source.
- When evidence conflicts, report both sides and the most likely reason for the discrepancy
  (measures, samples, periods, identification) rather than picking one [L3, L10].
- Self-review before handing over: re-read the output against the requirement rows and the
  reliability tests (§5.2); fix errors silently found, report errors that change conclusions.
- Say plainly what was not done, what could not be verified, and what needs the user's access
  (library logins, paywalled PDFs, restricted data).

---

## 3. Clean code rules (empirical work)

Applies to any analysis in `<PROJECT>/analysis/` (Python, R, Stata).

1. **Reproducible from raw**: `data/raw/` is immutable; every derived file is produced by a script.
   No hand-edited numbers in tables or text — results are written to `output/tables/` by code.
2. **One entry point**: `run_all` script (or numbered scripts `01_clean`, `02_describe`,
   `03_estimate`, `04_robustness`, `05_tables`) that runs end-to-end.
3. **Pinned environment**: `requirements.txt` (exact versions) / `renv.lock` / Stata version +
   `ssc` packages listed. Record the Python/R version.
4. **Relative paths only**, configured in one place. No absolute paths, no secrets in code.
5. **Seeds** for anything stochastic (bootstrap, simulation, PLS-SEM bootstrapping, ML splits).
6. **Names match the paper**: variable names and model labels mirror the notation in the text
   (e.g. `y_it`, `x_it`, `q_it` threshold variable). Document units, real vs nominal, base year,
   stock vs flow [AA08803].
7. **Small, single-purpose functions**; no copy-pasted model blocks — loop over specifications.
8. **Assert data assumptions** (panel balanced? duplicates? missing values? ranges?) and fail loudly.
9. **Log diagnostics with the estimates** (tests listed in §5.9–5.11, §5.17) — a model without its
   diagnostics is not finished.
10. **Data provenance**: `data/README.md` from `templates/DATA_README.md` — source, URL, access
    date, licence, transformations.
11. Comments explain *why*, not *what*. Match the surrounding code's style.
12. Code is reviewed for correctness before results are used in a draft.
13. **Tests for transformations**: small unit tests (or assertion scripts) for merges, deflators,
    variable construction; check row counts before/after every merge.
14. **Notebooks for exploration only**; anything that feeds a result lives in a script.
15. **Replication package**: README with requirements, run time, data access, and the
    mapping from each table/figure to the script that produces it [EXT – verify: Social Science
    Data Editors' template README]. Test it by running from a fresh clone and clean environment.

---

## 4. Writing standards

### 4.1 Process
- "To write well is to think well." Outline first (headings, sub-headings), then draft, then
  rewrite — several passes [L7].
- Write for the intended audience (lecturer/examiner/journal) [L7].
- Get a critical review of the draft before finalising (a separate review pass by another agent or
  the user) [L7].

### 4.2 Style
- Simple, direct, precise; avoid jargon and clichés; objective, non-judgemental wording [L7].
- **Present tense** by default and consistently [L3] ("Ledezma and López-Villavicencio (2026) argue…").
- Coherence within paragraphs via link words (therefore, however, in contrast, nevertheless);
  between paragraphs via logically sequenced topic sentences [L7].
- Critical thinking = analysis, synthesis, evaluation (upper Bloom levels), not knowledge /
  comprehension recital [L7]. Every paragraph should judge, compare, or explain — not just report.
- Define every term before using it (clarity test) [L2].

### 4.3 Common mistakes to avoid [L1, L7]
- No/weak problem statement; RQs/ROs missing, misaligned, or buried in one paragraph.
- Theoretical review missing; empirical review confined to one country; **reporting instead of synthesis**.
- Framework given as a diagram with no explanation; methods described but not how they are applied.
- Background ≠ introduction — both needed in a proposal.
- Results reported without interpretation; implications not linked to findings;
  conclusions that merely restate findings.
- Failure to cite landmark studies or to present others' contributions accurately.
- Over-generalisation, selective observation (outliers), illogical reasoning.
- Model chosen for empirical convenience rather than theory.
- Too much detail on minor issues; rambling; sloppy writing; wrong length.

### 4.4 Referencing — APA 7th [APA, L3]
- **Reference list** = only works cited (not a bibliography) [L3].
- Journal: `Author, A. A., & Author, B. B. (Year). Title in sentence case. Journal in Title Case, vol(issue), pages. https://doi.org/xxx`
- Authors: 1–20 listed (`&` before last); 21+ → first 19, `. . .`, last author.
- In-text: one/two authors `(Smith & Miller, 2009)` / `Smith and Miller (2009)`; three+ `(Smith et al., 2009)`.
- Same author & year → `2013a`, `2013b`. Page/para for quotes: `(Smith, 2009, p. 12)`, `(Shadid, 2020, paras. 2–3)`.
- Multiple works: `(Batanova & Loukas, 2014; Gambin & Sharp, 2016)`.
- Secondary: in text `Seidenberg and McClelland (1989, as cited in Coltheart et al., 1993)`;
  list only the source you read.
- Organisation as author: full name; acronym introduced on first use `(American Library Association [ALA], 2010)`.
- Malaysian names: omit bin/binti, a/l, a/p, s/o, d/o; omit conferred titles (Tun, Datuk); Chinese
  names surname first (`Chu, C. N.`).
- Unpublished thesis: `[Unpublished master's thesis]. <University>.`
- Lecture slides: `Author. (Year). Title [PowerPoint slides]. Platform. URL`.
- Software: `Author. (Year). Title (Version) [Computer software]. Publisher. URL`.
- Datasets: `Organisation. (Year). Title of dataset (Version) [Data set]. Publisher. URL`.

### 4.5 Contribution and framing
- State the contribution in the introduction in **one to three sentences**, naming its type
  (§5.19) and against which literature it is a contribution.
- Introduction formula: big picture → gap → research problem → what this study does → what it
  finds (papers) or expects (proposals) → contributions → roadmap [L3].
- Every chapter/section opens with what it does for the argument and closes with what follows.
- Answer "so what?" for each main result: magnitude in meaningful units, comparison to the
  literature, and implication for theory or policy.

### 4.6 Tables and figures
- Each table/figure stands alone: informative title, units, sample, data source, notes defining
  every symbol, standard-error type and significance convention.
- Report N, fixed effects, clustering level and key diagnostics under every regression table.
- Every table and figure is referenced and interpreted in the text; never "see Table 3" alone.

---

## 5. Knowledge Base

Source tags §5.1–5.16 refer to the local course materials (not distributed; see `PROFILE.md` §4):
**[L1]–[L14]** lectures (Lecture 9 is one of the unnumbered files); **[L11]** guest – mixed methods;
**[L12]** guest – PLS-SEM; **[L13]** guest – panel FE/RE guide (Torres-Reyna); **[AA08803]** Theories &
Issues in Economics; **[FL]** Final Lecture summary; **[AR1]** O'Brien (1998/2001) action research
overview; **[AR2]** Quayson (2019); **[ARS]** Raman, Ryan & Olfman (2006) action-research sample paper;
**[APA]** university library APA 7 guide. **[EXT – verify]** = standard practice not in the course
material; verify against the literature before relying on it or citing it.

### 5.1 Research, methodology, methods [L1, L2]
- **Methodology** = principles for organising, planning, designing and conducting research (how you
  will answer the RQ). **Methods** = specific techniques/tools. Not interchangeable.
- Research = systematic approach to new, reliable knowledge. Not: accidental discovery, data
  collection, or literature search alone.
- Types: basic vs applied; **disciplinary** (improves the discipline), **subject-matter**
  (economics applied to contemporary issues; main source of policy work), **problem-solving**
  (prescriptive, most holistic, least generalisable). Descriptive ("what is") vs analytical ("why/how").
- Research process / scientific approach (5 steps): problem → objectives → design (methods &
  procedures) → analysis/results → interpretation & conclusions.
- Required skills: critical thinking, synthesis, creativity [L1].

### 5.2 Paradigms and philosophical foundations [L2, L8]
- **Positivism / logical positivism**: observable, measurable, value-free "what is"; drives
  measurement and objectivity; dominant in empirical estimation. Limitation: ignores usefulness.
- **(Objective) normativism**: knowledge of values (good/bad) is valid and needed for prescriptive
  knowledge; strong in subject-matter and problem-solving research.
- **Pragmatism**: knowledge judged by **workability** for the problem at hand; strongest in
  problem-solving research. Mixed methods and action research typically sit here.
- Blends: disciplinary → positivism + normativism; subject-matter → positivist estimation,
  normative prescriptions, pragmatic focus; problem-solving → always pragmatic.
- Knowledge: normativistic (prescriptive; values) vs positivistic; public (demonstrable — reliable)
  vs private. Reliable knowledge = supported by evidence + reproducible way of obtaining it.
- **Deduction** (theory → hypotheses → test) vs **induction** (observations → generalisation;
  grounded theory, field research).
- **Tests for overall reliability**: logical coherence, correspondence (with prior knowledge),
  clarity (no ambiguity, all terms defined), workability (solves the problem). Use these to audit
  any argument or finding.
- **Research onion** (Saunders et al., 2007) [L8]: philosophies (positivism, realism,
  interpretivism, objectivism, subjectivism, pragmatism) → approaches (deductive/inductive) →
  strategies (experiment, survey, case study, action research, grounded theory, ethnography,
  archival) → choices (mono/mixed/multi-method) → time horizons (cross-sectional/longitudinal) →
  techniques and procedures. Use it to state and justify each layer of a design.
- Terms [L2]: observation, fact, law, theory, concept, variable, axiom, proposition, hypothesis.
- **Statistical hypotheses** need: a conceptual (theoretical) basis; enough specificity to be
  rejected; available data and techniques. **Qualitative hypotheses**: maintained (assumed true),
  diagnostic (causes of a problem), remedial (proposed solutions).
- Functions of theory: formulate problem and hypotheses, design procedures, assemble data,
  interpret findings; orientation, classification, conceptualisation, summarisation, precision,
  prediction, identifying knowledge gaps.

### 5.3 Problem statement, RQs, ROs [L4, L7]
- Research problem = discrepancy between what is known and what needs to be known. "A problem
  well-stated is a problem half solved." It is the **justification** for the research.
- Worth researching if it fills a gap/advances knowledge, examines more thoroughly, or informs practice.
- Two parts: **general problem** (problematic situation, context) → **specific, researchable
  problem** (narrow, addressable with data and methods). General-to-specific funnel.
- Flow: **Topic → Issue (a concern) → Justification (literature/observation) → Deficiencies in
  the evidence (what is missing) → Benefits/outcomes (who gains)**.
- Describe in objective terms; suppress private values; develop from intuitive to logical level.
- Use data/descriptive statistics to reveal and substantiate the problem; cite sources for every
  number. "Not done for country X" is not enough — say **why** it matters for X [L3].
- Objectives: **one-sentence general objective** + specific objectives; must flow from the problem
  and **map 1:1 to research questions** (present as a two-column RQ ↔ RO table).
- Journal introduction: **big picture → gap → research problem → contributions** [L3].

### 5.4 Literature review [L3, L7]
- Purposes: avoid duplication; locate the frontier; give ideas on techniques, data, problems;
  inform design; supply conceptual insight and hypotheses; **identify gaps** (and why they matter).
- Sources: journal articles, book chapters, formal publications (government, international
  organisations, working papers). Search with JEL codes, keywords, indexes, recent issues of major
  journals, theses; start with recent studies (they cite the earlier ones) but include classics.
- Keep complete records of everything read; use a **review matrix** (Author/Year | Purpose |
  Method & Data | Key Findings) — extend with "Relevance / limitation" column.
- Write **synthesis, not a series of summaries**: analyse, compare, contrast; offer your own
  comments. Organise chronologically or by themes. Bad example in [L3] = one paragraph per study.
  Good example = claim + several citations grouped, mechanisms explained, contradictions
  explained (e.g. different results traced to different measures of EPU).
- **Theoretical review first** (most important: mechanisms/channels that justify hypotheses),
  then **empirical review** (weight of evidence, comparisons), then **summary & gaps**.
  Thesis outline: Intro → Definitions → Theoretical → Empirical → Summary & Gaps.
- Cite only less-known facts; reference where the idea is used; consistent style throughout.

### 5.5 Frameworks, models, methodology [L5, L6, L7]
- **Theoretical framework**: the lens; derived from tested theory; one theory can suffice.
  **Conceptual framework**: broader roadmap derived from concepts; defines variables and maps
  their (causal) relationships; may include a theoretical framework; leads to hypotheses.
  "A conceptual analysis through the problem to all hypotheses relevant to the problem" (Williams, 1984).
- Building one: grasp the literature → reduce the problem to the simplest set of conditions →
  identify applicable theory → **base model** → extend to other dimensions → assemble testable
  hypotheses. A diagram **must be explained** in text.
- Good hypothesis [L5]: states an expected relationship, testable, consistent with knowledge, concise.
- Method choice criteria: feasibility, appropriateness, validity/reliability/trustworthiness,
  robustness and replicability.
- Methods section must say: how each method relates to the objectives, model development and
  functional form justification, how estimates are tested, **how results will be interpreted**.
  Cite the studies whose method you follow.
- Model types [L5, AA08803]: **econometric** (stochastic, positive, estimated from data),
  **optimisation** (normative), **simulation** (positive, non-stochastic). Not mutually exclusive.
  "Some important things cannot be modelled" — leave room for qualitative reasoning.
- Empirical methods: descriptive/historical (trends, problem definition); statistical/econometric
  (single equation, multivariate, structural). Modern shift: make observational data behave like
  experimental data (quasi-experimental: DiD, IV, RDD) [AA08803]; "third way" — model-guided
  specification with QE-style identification (Green, 2025) [AA08803]. Causal empirical methods
  dominate recent NBER/CEPR papers (Garg & Fetzer, 2025) [AA08803].
- **Assumptions matter**: results that depend on assumptions known to be unlikely should be
  treated with circumspection (Tirole, 2025) [AA08803]. Add a behavioural assumption only if it
  specifies when and in which direction behaviour deviates [AA08803].
- **Data**: locate existing, generate missing, assess reliability/applicability. Secondary data —
  check source reputation, classification/base-year changes, nominal vs real, stock vs flow.
  Primary data — value-free questions, pilot test, minimal burden, ethics clearance first.
  New sources: satellite/GIS; text-as-data via LLMs (needs conceptual justification, transparency
  and validation) [AA08803].
- **Limitations**: state limits to reliability and applicability of results [L7].
- **Robustness** (common tests) [AA08803]: add controls; alternative variable definitions;
  sub-samples (industry/region/period/firm size); alternative estimators; structural stability;
  outliers.

### 5.6 Quantitative and qualitative research [L6]
- Quantitative — use for numeric answers, measuring change, comparisons, explanation/prediction,
  hypothesis testing. Not for hard-to-quantify, depth, hypothesis generation, highly complex
  linkages, meaning.
- Designs: descriptive, correlational, survey (cross-sectional/longitudinal),
  causal-comparative/**quasi-experimental**, experimental (manipulation + control + randomisation).
- Framework: theoretical framework → model → hypotheses → variables → empirical relationships →
  testing → prediction.
- **Variables**: independent/explanatory, dependent, latent, **mediating** (on the causal path
  X→M→Y), **moderating** (changes strength/direction; not caused by X), **confounding** (affects
  both X and Y), extraneous.
- Qualitative — natural settings, meanings, process, inductive/grounded theory. Methods: action
  research, phenomenology, ethnography, case study (Yin: single/multiple cases and units),
  grounded theory, historical research. Uses: stand-alone, interpreting numbers, generating hypotheses.
- Data collection: participant observation, interviews, focus groups, surveys, documents/archives.
  Analysis: open/axial/selective coding, content, discourse, narrative analysis, hermeneutics, semiotics.

### 5.7 Validity, reliability, sampling, questionnaires [L6]
- **Validity** = measures what it intends to. Internal: construct, content, face. External:
  population, ecological, temporal. External validity via replication logic / analytic
  generalisation (relate findings to literature).
- **Construct validity**: define the construct, show operationalisation resembles it, show data
  support theory; multiple sources of evidence, chain of evidence, key informants review drafts.
- **Reliability** = repeatable operations with the same results; document procedures; keep raw
  field notes, expanded notes, running analysis record (coding memos).
- Good measurement needs both (reliable-not-valid = consistently wrong).
- **Probability sampling**: simple random, stratified, systematic, cluster.
  **Non-probability**: purposive, quota, convenience, snowball. Always justify; state the
  population the sample generalises to.
- **Questionnaire development** (Radhakrishna, 2007): background → conceptualisation (map
  objectives to items; identify IV/DV/moderators) → format & analysis plan (scale level must fit
  the planned test) → **validity** (expert panel + field test) → **reliability** (pilot with
  20–30 non-sample subjects; Cronbach's α ≥ .70; drop items only if they substantially raise α;
  delete no more than 20% of items). Measurement levels: nominal, ordinal, interval, ratio.
- [EXT – verify] Threats-to-validity framing (Shadish, Cook & Campbell, 2002): statistical
  conclusion, internal, construct, external validity. Every proposal and empirical paper includes a table:
  threat → why it applies here → how the design addresses it → residual risk.

### 5.8 Mixed methods research [L10, L11, FL]
- Collect, analyse and **integrate** quant + qual in one study, when integration gives a better
  understanding than either alone. **Integration, not side-by-side use** (Caracelli & Greene, 1997).
- Use when: corroborating; one method informing another; elaborating/explaining (e.g. causal
  processes behind a quant result); clarifying unexpected or contradictory results; building then
  testing theory; generalising qual findings.
- Pros: offset weaknesses; fuller understanding; better context-specific instruments; explains
  mechanisms. Cons: complex, time/resource heavy, hard to build one phase on another, discrepancies
  hard to resolve.
- **Designs** (Creswell, 2012; Christensen et al., 2014):
  - **Explanatory sequential** (QUAN → qual): quant first, priority on quant; qual explains,
    interprets, contextualises, or probes unexpected results; integrate at interpretation.
    Strengths: clear stages, easy to describe/report. Weakness: long timeline.
    Example: survey on risk perceptions → interviews with selected respondents (e.g. low-risk
    perceivers) [L10]; Reza (2020) Bangladeshi migrant workers in Malaysia [L11].
  - **Exploratory sequential** (QUAL → quant): explore, then test/generalise or build an instrument.
  - **Concurrent triangulation / convergent parallel**: separate, simultaneous, equal priority;
    compare/relate at interpretation.
  - **Concurrent nested / embedded**: one dominant method embeds the other; mix in analysis.
  - Also: transformative, multiphase [L10 figure].
- Defining issues [L10]: quant/qual distinctions don't line up neatly; **purpose must be explicit
  and theory-driven** (corroboration, expansion, initiation — Rossman & Wilson, 1985);
  triangulation ≠ mixed methods and does not automatically validate (each source on its own
  terms); a few token interviews "cheapen" qual work; don't over-interpret counts from coded
  small purposive samples; when evidence conflicts, **seek reasons for the discrepancy** rather
  than just weighting.
- Integration techniques: convert qual codes into variables for regression; correspondence
  analysis of coded data. Judge methodology by: do methods answer the question? are background
  assumptions coherent? are methods applied credibly? (Howe & Eisenhart, 1990).
- Mixed methods enrich via **confirmation, extension, or initiation** of new thinking; not
  inherently more or less valid — validity comes from appropriate, thorough application.
- **Triangulation** (Denzin, 1970): data (time, space, persons), theory, method, investigator.
- [EXT – verify] Useful additional sources: Creswell & Plano Clark (2018) *Designing and
  Conducting Mixed Methods Research*; Ivankova, Creswell & Stick (2006) on explanatory sequential
  design; Fetters, Curry & Creswell (2013) on integration (connecting, building, merging,
  embedding; joint displays; confirmation/expansion/discordance).

### 5.9 Panel data: static and dynamic [L13, L14, AA08803, FL]
- Panel = entities observed over time; controls for unobserved heterogeneity (time-invariant
  entity traits) and time-varying common shocks; allows multilevel structure. Drawbacks: sampling/
  coverage, non-response (micro), cross-country dependence (macro).
- **Fixed effects (within/LSDV)**: entity intercepts absorb time-invariant traits correlated with
  regressors; cannot estimate time-invariant causes; weak when within-variation is small.
  Interpretation: for a given entity, as X changes by one unit over time, Y changes by β.
  Add **time effects** (test jointly: `testparm i.year`).
- **Random effects**: entity effect assumed uncorrelated with regressors; allows time-invariant
  regressors; coefficients mix within and between variation.
- **Tests**: Hausman (FE vs RE; reject → FE); Breusch–Pagan LM (RE vs pooled OLS);
  cross-sectional dependence (BP LM, Pesaran CD → Driscoll–Kraay SEs, `xtscc`) mainly in long
  macro panels; groupwise heteroskedasticity (modified Wald `xttest3` → robust SEs);
  serial correlation (Wooldridge `xtserial`); panel unit roots (`xtunitroot`: LLC, IPS, Breitung,
  Fisher, Hadri) in long panels.
- **Dynamic panels**: a lagged dependent variable among regressors is a source of endogeneity
  (correlated with the error) → IV/GMM [L14]. **Difference/System GMM** (Arellano & Bond, 1991)
  uses internal instruments; validate with **Hansen J** (over-identification; robust to
  heteroskedasticity — Sargan is not) and **Arellano–Bond AR(2)** test [L14].
  **Many-instrument bias** in over-identified systems [L14].
- **Threshold models**: popular for nonlinear behaviour / asymmetric adjustment (Zapata &
  Gauthier, 2003); example: income inequality as threshold variable changing the growth–emissions
  relation in 56 countries (Wang & Li, 2023) [AA08803].
- [EXT – verify] Dynamic panel threshold specifics: Hansen (1999) static panel threshold
  (fixed effects, bootstrap test for threshold existence, likelihood-ratio confidence interval);
  Kremer, Bick & Nautz (2013) dynamic threshold with FD-GMM-type instruments; Seo & Shin (2016)
  FD-GMM dynamic threshold with endogenous regressors/threshold. **Instrument proliferation**
  (Roodman, 2009): instruments grow with T, overfit endogenous variables, weaken Hansen test →
  collapse instruments, limit lag depth, report instrument count < number of groups.
  Weak instruments in GMM: check first-stage strength / difference-in-Hansen.
- [EXT – verify] **Few clusters**: with few clusters (roughly < 30–50) cluster-robust SEs
  over-reject; use the wild cluster bootstrap (Cameron, Gelbach & Miller, 2008). Cluster at the
  level of treatment assignment.

### 5.10 Instrumental variables [L14]
- Endogeneity sources: measurement error, reverse causality/simultaneity, omitted variables,
  lagged dependent variable.
- Valid instrument Z: **relevant** (correlated with the endogenous X), **exogenous** (uncorrelated
  with the error), **excluded** (not in the Y equation; affects Y only through X). Cannot reuse an
  explanatory variable already in the model.
- Hausman test for endogeneity (OLS vs IV). **Weak instruments**: bias not removed, large SEs.
  Lagged endogenous regressors are generally **not** good instruments.
- Support validity by: economic-theory argument, ruling out instrument–error links, **comparing
  alternative instruments**. IV is biased if an omitted variable correlates with Z or included Xs.
- Test table: **Kleibergen–Paap** (under-identification/relevance; heteroskedasticity-robust),
  **Stock–Yogo** (weak-instrument critical values), **Sargan–Hansen** (over-identifying
  restrictions; only when m > k). Exact identification (m = k) cannot test validity.
- Worked examples in [L14]: robots in similar-output-structure countries (Pavez & Martínez-Zarzoso,
  2023); lagged foreign-worker dependency and Indonesian wages (Athukorala & Devadason, 2012);
  tariffs for prices (Jamil et al., 2025); historical law-school density and GMM robustness
  (Bielen & Marneffe, 2018).
- [EXT – verify] With heterogeneous effects IV estimates a **LATE** for compliers (Imbens &
  Angrist, 1994): say whose effect it is. Shift-share (Bartik) instruments: state whether
  identification comes from the shares or the shocks (Goldsmith-Pinkham, Sorkin & Swift, 2020;
  Borusyak, Hull & Jaravel, 2022). Weak-IV-robust inference: Anderson–Rubin.

### 5.11 Difference-in-differences [AA08803]
- DiD is a core quasi-experimental technique; **newer estimators address staggered adoption,
  where traditional two-way fixed effects (TWFE) can be biased** [AA08803].
- [EXT – verify] Design essentials: define treatment group, control group, pre/post periods,
  outcome; the DiD estimand is the ATT; **parallel trends** in the absence of treatment is the
  identifying assumption — assess with pre-trend plots and **event-study leads**, placebo
  treatment dates/groups, and sensitivity analysis (Rambachan & Roth, 2023). Pre-trend tests have
  low power and conditioning on them distorts inference (Roth, 2022). Threats:
  anticipation, spillovers/SUTVA violations, concurrent policies, compositional change, Ashenfelter
  dip. Robustness: alternative controls (synthetic control/matching), triple differences,
  cluster SEs at treatment level (Bertrand, Duflo & Mullainathan, 2004), heterogeneity-robust
  staggered estimators (Callaway & Sant'Anna, 2021; Sun & Abraham, 2021; de Chaisemartin &
  D'Haultfœuille, 2020; Goodman-Bacon, 2021 decomposition); review in Roth et al. (2023).

### 5.12 PLS-SEM [L12]
- Analytical tool = f(nature of data [cross-section/panel/time series], type of RQ [group
  comparison, cause–effect, factor reduction, prioritisation]). SEM = latent variables (CFA) +
  path analysis + simultaneous equations.
- **CB-SEM** (theory testing, reflective, normality, large n, global fit) vs **PLS-SEM**
  (prediction/theory development, reflective and formative, no normality, small n OK, no global fit).
- Measurement: **reflective** (construct → items; items must correlate; reliability/validity
  required) vs **formative** (items → construct). Higher-order constructs.
- **Measurement model** criteria: Cronbach's α > .70; composite reliability > .70 (.60–.70
  acceptable in exploratory work); outer loadings > .70 (≥ .50 acceptable if AVE > .50);
  convergent validity **AVE > .50**; discriminant validity: Fornell–Larcker (√AVE > inter-construct
  correlations), **HTMT < .85** (conceptually distinct) / **< .90** (similar), cross-loadings
  (item's own loading > cross-loadings).
- **Structural model**: (1) collinearity VIF < 5; (2) path coefficients and significance via
  bootstrapping (p < .05); (3) R² (.25 weak, .50 moderate, .75 substantial); (4) effect size f²;
  (5) predictive relevance Q². Report direct and indirect (mediation) effects.
- Data prep: rename items, recode text scales to numbers, CSV, no missing data.
- [EXT – verify] Common-method bias in single-respondent surveys: procedural remedies first
  (separate sources/timing), then statistical checks (full collinearity VIF); Harman's single
  factor test alone is weak (Podsakoff et al., 2003).

### 5.13 Action research [AR1, AR2, ARS, L6]
- "Learning by doing": dual commitment to solve a practical problem and contribute to social
  science, through researcher–participant collaboration; researcher acknowledges own bias.
- Cycle (Kemmis): **plan → act → observe → reflect**, repeated. Susman (1983): diagnose →
  action planning → action → evaluation → specify learning. Canonical AR [ARS]: entry → diagnosis →
  action plan → intervention → evaluation/reflection → exit with client sign-off.
- Principles (Winter, 1989): reflexive critique, dialectical critique, collaborative resource,
  risk, plural structure, theory–practice–transformation.
- Paradigm of **praxis**; types: traditional, contextural (action learning), radical
  (participatory/feminist), educational. Tools: research journal, documents, observation,
  questionnaires, interviews, case studies, **search conferences**.
- Ethics (Winter, 1996): consult stakeholders first; all can influence; work stays visible;
  permission before observing/using documents; negotiate descriptions; confidentiality;
  collective decisions; explicit about biases; equal access to information.

### 5.14 Behavioural economics [L8, AA08803]
- Aim: increase explanatory power with realistic psychological foundations (Thaler, 2016).
  Key ideas: bounded rationality (Simon, 1955), prospect theory & loss aversion (Kahneman &
  Tversky, 1979), heuristics/biases, bounded willpower & self-interest, mental accounting,
  sunk cost, choice architecture/nudges, herding.
- Chetty (2015): adopt BE **pragmatically** — include behavioural factors when they improve
  predictions and welfare analysis, like any modelling decision; BE as part of the toolkit.
- Limits of standard assumptions (ceteris paribus, rationality, equilibrium, market efficiency) —
  use when critiquing a theoretical framework's realism.

### 5.15 Research proposal and report structure [L3, L4, L5, L7]
Title (descriptive, no unnecessary words) → Introduction/Background (context, motivation,
general-to-specific) → Problem Statement (general → specific) → RQs & ROs (aligned) →
Literature Review (theoretical → empirical → summary & gaps) → Methodology (conceptual/theoretical
framework; data description & sources; empirical strategy/model specification; limitations) →
Significance (how the gap is bridged) → Organisation of the study → (Output, Gantt, Budget if
required) → References (1:1 with citations).
The proposal is a plan, not a straitjacket; major changes may need approval [L7].
Always include: contribution statement (§4.5), threats-to-validity table (§5.7), PAP summary
(§2.6), data-availability evidence (what was actually checked, when), risk register with fallbacks.

### 5.16 Ethics [L7]
- Voluntary participation, no harm, **informed consent**; Belmont principles (respect for
  persons, beneficence, justice); anonymity vs confidentiality; justified deception + debriefing.
- Human-subjects research needs the institution's research ethics committee approval before data
  collection (see `PROFILE.md`).
- Publication ethics: plagiarism, self-plagiarism/salami-slicing, conflicts of interest,
  duplicate submission, unfair authorship, data falsification.
- [EXT – verify] Secondary data are not automatically exempt: check licence terms, re-identification
  risk in microdata, and whether the committee requires an exemption form.

### 5.17 Causal inference toolkit [EXT – verify]
Beyond the course; verify each source before citing.
- **Start from the estimand**: write the causal quantity (ATE, ATT, LATE, dose-response) in
  potential-outcomes notation, then the identifying assumption, then the estimator. Critiques and
  designs that skip the estimand usually confuse "what is estimated" with "how".
- **DAGs** for control selection: adjust for confounders; never for mediators or colliders
  ("bad controls"); post-treatment variables are bad controls (Pearl, 2009; Cinelli, Forney &
  Pearl, 2024; Angrist & Pischke, 2009).
- **Selection on observables** (regression, matching, weighting): credible only with a rich,
  theory-justified covariate set; report balance and overlap; bound the role of unobservables
  (Oster, 2019 coefficient stability; Rosenbaum sensitivity; Cinelli & Hazlett, 2020).
- **Regression discontinuity**: continuity at the cutoff; test manipulation (density test) and
  covariate balance at the cutoff; local-polynomial estimation with robust bias-corrected
  inference; bandwidth sensitivity (Imbens & Lemieux, 2008; Cattaneo, Idrobo & Titiunik, 2020).
- **Synthetic control**: few treated units, long pre-period; report pre-period fit, donor
  weights, placebo-in-space/time inference (Abadie, Diamond & Hainmueller, 2010; Abadie, 2021).
- **Event studies**: plot leads and lags with a stated reference period; with staggered timing use
  heterogeneity-robust estimators (§5.11).
- **Partial identification / bounds** when point identification is not credible (Manski; Lee
  bounds for attrition).
- **Mechanisms**: mediation claims need their own identification; "consistent with" ≠ "shows".
- **Heterogeneity and external validity**: pre-specify subgroups; distinguish effect
  heterogeneity from noise; argue transportability explicitly (population, setting, period).
- **Credibility checklist** for any causal claim: estimand stated → assumption stated →
  assumption probed (falsification/placebo) → inference appropriate (clustering, few clusters,
  multiple testing) → magnitude interpreted → strongest alternative explanation addressed.

### 5.18 Systematic reviews and meta-analysis [EXT – verify]
- **Protocol first**: question (PICO/PECO or equivalent), databases (Scopus, Web of Science, EconLit,
  RePEc/IDEAS, Google Scholar for grey literature), search strings, inclusion/exclusion criteria,
  screening procedure, data-extraction form. Log every search (database, string, date, hits).
- Report with a **PRISMA 2020** flow diagram: identified → screened → eligible → included, with
  reasons for exclusion (Page et al., 2021).
- Assess study quality / risk of bias with a stated tool; do not weight all studies equally by default.
- **Meta-analysis**: common effect size metric (e.g. partial correlations, elasticities);
  random-effects when heterogeneity is expected; report τ² and I² (Higgins & Thompson, 2002);
  meta-regression for moderators.
- **Publication bias**: funnel plots, FAT-PET-PEESE (Stanley & Doucouliagos, 2014), selection
  models (Andrews & Kasy, 2019). Economics evidence is often underpowered and inflated
  (Ioannidis et al., 2017).
- Systematic-lite (when a full review is out of scope): documented search + inclusion criteria + review matrix, without full
  risk-of-bias scoring.

### 5.19 Contribution and positioning [EXT – verify]
- Contribution types: **new question**; **new evidence for a contested question**; **better
  identification** of a known relationship; **new data or measurement**; **new mechanism**
  (theory or test of channel); **new method**; **new context, with a reason the context changes
  the answer** (institutions, development level, policy design). "Not yet studied in country X"
  alone is not a contribution [L3].
- Gap-spotting (filling holes in the literature) vs **problematisation** (challenging the
  assumptions behind it); the latter produces more interesting questions (Alvesson & Sandberg, 2011).
- A theoretical contribution says what, how, why, and for whom/when/where (Whetten, 1989).
- Positioning test: name the 3–5 closest papers and state in one line each what this study does
  that they do not. If the answer is weak, revise the question before investing in data.
- Pitch (one paragraph): question → why it matters → what is known → what is missing → what this
  study does → what it will deliver.

### 5.20 Doctoral standard and the thesis [EXT – verify against the institution's regulations]
- Typical doctoral criteria: an **original contribution to knowledge** of publishable quality;
  systematic command of the field's frontier; ability to conceive, design and carry out a project;
  independent critical judgement; ability to defend the work orally.
- Formats: **monograph** (intro → literature → framework → method → results chapters →
  conclusion) or **three-paper / by publication** (introduction tying the papers together, three
  self-contained papers, conclusion on the joint contribution). Check which the institution allows.
- Each empirical chapter/paper should be able to stand alone: question, contribution, design,
  results, robustness, limitations.
- Working with supervisors: agenda sent before meetings; decisions and actions minuted in
  `PROGRESS.md`; drafts sent with a cover note stating what feedback is wanted (§6.7).
- Research diary / lab notebook: dated entries on decisions, dead ends and why (it is also the
  work trace).

### 5.21 Prediction, machine learning and causal ML [EXT – verify]
- Separate **prediction** problems (ŷ) from **estimation** problems (β̂); ML excels at the first and
  needs extra structure for the second (Mullainathan & Spiess, 2017; Athey & Imbens, 2019).
- Prediction work: hold-out / time-respecting cross-validation (no look-ahead in time series or
  panels), a simple benchmark model, out-of-sample metrics, leakage checks.
- Causal ML: double/debiased ML with cross-fitting for high-dimensional controls (Chernozhukov
  et al., 2018); causal forests for heterogeneous effects (Wager & Athey, 2018). Identification
  assumptions are unchanged; ML only handles the nuisance functions.
- Text-as-data with LLMs: validate against human-coded samples, report agreement, fix the model
  version and prompt, and treat LLM outputs as measured with error [AA08803].

---

## 6. Playbooks

### 6.1 Critical evaluation of an empirical article
Answer for each article, then **compare across articles** (critical engagement = judging, not describing):
1. **Problem & importance** [§5.3]: general vs specific problem; why it matters (policy, gap,
   magnitude); explicit vs inferred RQs; does the intro follow big picture → gap → problem → contribution?
2. **Framework** [§5.2, 5.5]: explicit theoretical/conceptual framework? If not, reconstruct it
   from the literature review, hypotheses and model. Evaluate: mechanisms stated? assumptions
   realistic? does it generate the hypotheses tested? apply reliability tests (coherence,
   correspondence, clarity, workability).
3. **Parameters/hypotheses & estimation** [§5.6, 5.9–5.11, 5.17]: write the estimand and the
   estimating equation; name the parameter(s) of interest and the null/alternative; map each to
   the framework. Judge the estimator against the RQ and data: identification strategy,
   endogeneity handling, fixed effects, SEs/clustering, diagnostics reported? Cite methodological
   and applied literature.
4. **Findings & conclusions** [§5.5, 5.7]: do results support the claims (magnitude, significance,
   power, robustness, heterogeneity)? Limitations: data, measurement, external validity,
   alternative explanations, omitted mechanisms, causal language vs design. Cite studies with
   contrasting evidence.
5. Use literature **beyond the assigned readings**; every evaluative claim is supported by a
   citation or by evidence from the article (table/section reference).
6. Rate each issue **major / moderate / minor** and credit genuine strengths; a balanced critique
   is more convincing than a list of faults.

### 6.2 Designing an applied method answer (no data required)
State the research problem → the estimand → why this method fits (data structure, RQ type) →
specification with notation and variable definitions → identification/estimation challenges →
diagnostics and fixes → interpretation of estimates → robustness → limitations → empirical
examples (with verified, indexed citations where required).

### 6.3 Final QA (always the last phase)
Walk the requirements matrix line by line; check marks ↔ length balance; citations ↔ references;
APA spot-check of every entry; terminology consistent; every figure/equation explained; title page
fields; AI declaration; export and open the final file to confirm it renders.

### 6.4 Literature search protocol (every project)
1. Define the question and 3–6 concept blocks; list synonyms per block; combine with AND/OR.
2. Search at least two databases plus one grey-literature source; log each search in
   `sources/search_log.md` (database, string, filters, date, hits, kept).
3. Snowball: backward (references of key papers) and forward (citing papers) from 3–5 anchors.
4. Screen titles/abstracts against written inclusion criteria; record exclusions with a reason.
5. Verify every kept source (§2.1) before it enters `references.md`; fill the review matrix.
6. Stop rule: new searches return mostly known papers (saturation); record when it was reached.

### 6.5 Pushback / referee report
Use `templates/pushback.md`. Structure: one-line verdict → requirement coverage → major issues
(each: problem → why it matters → direction of fix → evidence) → moderate → minor → what works →
questions only the author can answer → gate status. Also write it as a journal referee
would: summary of the paper's claim, assessment of contribution, identification, and whether the
conclusions follow; recommendation with the conditions that would change it.

### 6.6 Empirical project pipeline
Question and contribution (G0) → data scouting with a coverage table (units × years × variables,
access tested) → PAP frozen (G1) → `01_clean` with assertions → descriptive statistics and plots
→ primary estimation with diagnostics → pre-specified robustness and heterogeneity → deviations
logged (G3) → tables/figures by code → interpretation memo (magnitudes, comparison to literature)
→ user drafts → pushback loop (G4) → replication run from a fresh clone (G5).

### 6.7 Supervisor / stakeholder pitch
One page: title; the pitch paragraph (§5.19); RQs; data with evidence it exists (source, years,
link, access date); method in two sentences; why this supervisor (link to their research areas);
risks and fallbacks; what you are asking for (supervision, feedback, data access).

### 6.8 Oral defence / viva preparation
From the final draft, generate the 15–20 hardest questions an examiner could ask (contribution,
identification, alternative explanations, data choices, limitations, AI use). The user answers in
their own words; the agent pushes back on weak answers. Every number and citation in the
deliverable must be explainable without notes.

---

## 7. Growing the harness

The harness improves with every project. Goal: an assistant that can take a research direction
from the researcher and deliver doctoral-standard work with minimal hand-holding.
1. **Retrospective at project end**: add a `Lessons` section to the project `PROGRESS.md`
   (what slowed the work, what the assessor/supervisor criticised, what an agent got wrong).
2. **Promote lessons**: turn recurring lessons into rules, Knowledge Base entries, playbooks or
   templates here. Propose the change to the user first; record approved changes in `CHANGELOG.md`.
3. **New methods**: when a project uses a method not in §5, add a section with its assumptions,
   diagnostics, pitfalls and verified key references (tag `[EXT – verify]` until checked).
4. **Automate repeated work** (reference verification, search logging, table generation) as small
   scripts under `tools/` with the same standards as §3; document each in `README.md`.
5. **Keep it general**: no personal, institutional or project-specific content in tracked files;
   that belongs in `PROFILE.md` or the project folder.

