# HANDOFF

Last updated: 2026-10-01 by Claude (Sonnet 5.5) in a claude.ai chat with Tony Whelan.
Read order: `README.md`, this file, `docs/DECISIONS.md`, then the latest entry in `docs/STATUS.md`.
This file is written so a person or an agent can resume with no other context.

## 0. Resuming now: the 60-second version

- **State:** planning and source groundwork are done and pushed. There is no application code yet.
- **Notebook layer:** Google NotebookLM (possibly rebranded "Gemini Notebook"), owned by Tony's Google account. Not Open Notebook (that was considered and dropped; see D2 and D3 in `DECISIONS.md`).
- **Do first:** steps 1 to 4 in section 7 (make repo private, verify licences, smoke-test the NotebookLM tooling, confirm the product name).
- **Prompt for a fresh Claude session:**
  > Read README.md, docs/HANDOFF.md, docs/DECISIONS.md and the latest entry in docs/STATUS.md. Then continue from the next unfinished step in HANDOFF section 7. Append what you do to docs/STATUS.md and commit as you go.

## 1. Objective

Build a web app that acts as oracle, companion, coach and tester for one course, so the learner can learn, retain, enjoy and pass.

- Course: Pearson T Level Technical Qualification in Legal Services, Level 3, Crime, Criminal Justice and Social Welfare specialism.
- Delivered at: Wigan & Leigh College, Parsons Walk Campus (listed by the college as "Law & Criminal Justice T Level"). Two years, full time, 16-18.
- First tester: a learner starting the course in September 2026. They test and give feedback. When ready, they invite other learners.
- Knowledge layer: Google NotebookLM notebooks, owned by Tony, holding only approved sources.
- Own app layer: syllabus data, question bank, marking, spaced repetition, progress. This is the real product.
- Commercial intent: meant to grow beyond the first tester. Tony's business priority is products that generate incremental revenue.

## 2. Rules (non-negotiable)

1. **Public-domain or permissively licensed sources only.** No publisher, awarding-body or college-owned materials in the notebooks or the repo. Tony has stated this explicitly. Do not re-raise it or add copyright caveats to chat replies; just comply and record licence status in `docs/SOURCES.md`.
2. **No personal data about the learner in this repo.** No full name, age, school or contact details. Refer to "the first tester". The repo name (first name only) is the one exception, which is why the repo must be private.
3. **No credentials in the repo.** NotebookLM tooling stores Google session or cookie data locally. Never commit it. `.gitignore` covers the usual filenames, but check `git status` before every commit.
4. **Ask Tony before any `sudo` command** and before installing anything system-wide.
5. **Answers must cite a primary source** (a statute section, a case, or a syllabus-map topic ID). If the knowledge base has no source, the tool says so instead of guessing.
6. **Working style:** Tony wants execution, not lectures. State an assumption once and proceed. He is a senior infrastructure and AI practitioner. Keep replies direct.

## 3. Verified facts (checked 2026-10-01)

| Fact | Source |
|---|---|
| Course is offered at Wigan & Leigh College, Parsons Walk Campus, Level 3, 16-18, full time, listed as "Law & Criminal Justice T Level" | https://www.wigan-leigh.ac.uk/subject/t-level/ |
| Awarding organisation is Pearson, with CILEX as sector partner | https://qualifications.pearson.com/en/qualifications/t-levels/legal-services.html and https://iateducation.co.uk/new-legal-services-for-delivery-of-t-levels/ |
| Technical Qualification has a core component (exam plus employer-set project) and an occupational specialism | Skills England outline (SOURCES.md, S-01) |
| Two specialisms exist: Business, Finance and Employment; Crime, Criminal Justice and Social Welfare. The tester is on the second (confirmed by Tony) | Skills England outline; Tony |
| Industry placement is about 45 days (315 hours) | Wigan & Leigh page; T Levels student site |
| Pearson publishes a different specification per start year; the September 2026 intake has its own version | Pearson page above |
| The Pearson spec is Pearson copyright and is NOT in this repo | Pearson spec PDF footer |
| NotebookLM has no official API for consumer accounts that was found; unofficial tools exist (`notebooklm-py`, `notebooklm-mcp-cli`). See D3. | Their GitHub repos and PyPI pages |

## 4. Done so far

- Confirmed the course, college and campus.
- Identified the awarding body, structure and specialisms.
- Converted the Skills England outline (October 2020) into `docs/syllabus_map.md`: core topics C01-C15, legal pathway topics L01-L11, employer-set project skills P1-P5, specialism topics S1.xx, S2.xx, S3.xx, all with stable IDs.
- Created the repo (Tony) and pushed README, handoff, decisions, sources, architecture and the syllabus map (Claude).
- Chose the notebook layer (D3).

## 5. State of each item

| Item | State |
|---|---|
| GitHub repo | https://github.com/k3ss-official/rileys-law-coach. **Public at last check (2026-10-01). Make it private.** Claude's GitHub connector in claude.ai can push to it but cannot create repos or change visibility. Local clone intended at `~/k3ss-official/rileys-law-coach` on Tony's M4. |
| Notebook layer | Google NotebookLM, owned by Tony's Google account, shared with the tester. Access for tooling is unofficial (D3). Not yet tested. |
| Hosting | Nothing to host for the notebook layer. Our own app will need a home later (Tony's VPS is the likely candidate). Undecided. |
| Statutes and case law | Not fetched yet. Planned list is in `docs/SOURCES.md`. |
| Pearson Sept 2026 spec | Deliberately not obtained (copyright). The 2020 Skills England outline is the topic backbone. It is older than the current spec, so topics need reconciling against the college's scheme of work if the tester can share it. |
| Licence confirmation | Skills England outline, legislation.gov.uk and National Archives case law are believed to be under open licences. **Not verified on the source pages.** Verify before ingesting. |
| Product name | Possibly "Gemini Notebook" since July 2026 per a secondary source. Unverified. |
| Code | None written. |

## 6. Environment notes

- **claude.ai chat (where this was written):** web search and fetch; GitHub connector authenticated as `k3ss-official` (read and write on existing repos, no repo creation); sandbox with open network; no `gh` CLI, no Scrapling MCP, no `last30days` skill. Claude Code sessions are not visible to the chat, and the chat is not visible to them. The repo is the only shared memory.
- **Tony's M4 (Claude Code or desktop app):** has `gh`. Earlier sessions there reportedly had local MCP tools such as Scrapling and osascript. Verify what is installed before relying on it.
- **Passing context between sessions:** commit to the repo. Append to `docs/STATUS.md` after each chunk of work and push, so any other session can read it.

## 7. Next steps, in order

1. **Make the repo private** (Tony). Acceptance: GitHub shows the repo as Private.
2. **Verify licences** for the Skills England outline, legislation.gov.uk and the National Archives case-law service on their own pages. Record exact licence names and URLs in `docs/SOURCES.md`. Acceptance: each source's status moves from VERIFY to IN or OUT.
3. **Smoke-test the NotebookLM tooling with one small notebook.** Install `notebooklm-py` or `notebooklm-mcp-cli` (`nlm`), log in with Tony's Google account through the tool's own browser flow, create one test notebook, add one approved source (for example a statute page from legislation.gov.uk), generate a quiz, export it. Do not commit any auth files. Acceptance: `docs/STATUS.md` records what worked and what failed, with command lines.
4. **Confirm the product name** (NotebookLM vs Gemini Notebook) on Google's pages and update `DECISIONS.md`.
5. **Fetch the criminal-procedure set first** (the largest part of the specialism): PACE 1984, Criminal Procedure and Investigations Act 1996, Criminal Justice Act 1967 s9, Proceeds of Crime Act 2002 (s18 and lifestyle provisions), Criminal Procedure Rules, Parole Board Rules 2016. Store each as clean text with the ingest header from `SOURCES.md`. Acceptance: every file has a header and topic IDs.
6. **Fetch landmark cases** from the National Archives case-law service (for example Osborn, Booth and Reilly, named in the outline). Acceptance: neutral citation, URL and topic IDs recorded.
7. **Convert the syllabus map to structured data** (`data/syllabus.json` or YAML), one record per topic ID. Acceptance: a script confirms every ID in `docs/syllabus_map.md` is present exactly once.
8. **Question bank schema and a first set** of 30-50 questions for one unit (suggest S1.01, police procedure and interviews), each with topic IDs, type, difficulty, marking points and a primary-source citation. Acceptance: schema validated, every question cites a source.
9. **App skeleton with spaced repetition per topic ID.** Pick the stack and hosting (open question below). Acceptance: runs locally, can serve and mark one question set.
10. **Trial with the first tester for about two weeks**, collect feedback in `docs/STATUS.md`.
11. **Before inviting others:** decide the multi-user path (D3). Do not build a multi-user product on cookie-based automation.

## 8. Open questions for Tony

- Can the tester share the college's scheme of work or term plan (for the project's use, not redistribution)? It would settle topic order and any drift from the 2020 outline.
- Should the eventual product also cover the Business, Finance and Employment specialism, or stay Crime-only?
- Stack and hosting for our own app (his VPS, or elsewhere)?

## 9. Conventions

- Append, don't rewrite, in `docs/STATUS.md`. Newest entry at the bottom, dated, with: what was done, what was found, what is next.
- Record decisions in `docs/DECISIONS.md` with a number and date. Newer decisions override older statements.
- Keep topic IDs stable. If the syllabus map changes, add IDs; do not renumber.
- Dates are absolute (YYYY-MM-DD).
