# HANDOFF

Last updated: 2026-10-01 by Claude (Sonnet 5.5) in a claude.ai chat session with Tony Whelan.
Read this first. It is written so a person or an agent can resume with no other context.

## 1. Objective

Build a web app that acts as oracle, companion, coach and tester for one course, so the learner can learn, retain, enjoy and pass.

- Course: Pearson T Level Technical Qualification in Legal Services, Level 3, Crime, Criminal Justice and Social Welfare specialism.
- Delivered at: Wigan & Leigh College, Parsons Walk Campus (course listed by the college as "Law & Criminal Justice T Level"). Two years, full time, 16-18.
- First tester: a learner starting the course in September 2026. They test and give feedback. When ready, they invite other learners.
- Plan for the knowledge base: Open Notebook (lfnovo/open-notebook, MIT) holds the source material as the single source of truth, hosted on one of Tony's VPS servers.
- Commercial intent: this is meant to grow beyond the first tester. Tony's business priority is products that generate incremental revenue.

## 2. Rules (non-negotiable)

1. **Public-domain or permissively licensed sources only.** No publisher, awarding-body or college-owned materials in the knowledge base. Tony has stated this explicitly. Do not re-raise it or add copyright caveats to chat replies; just comply and record licence status in `SOURCES.md`.
2. **No personal data about the learner in this repo.** No full name, age, school or contact details. Refer to "the first tester". The repo name (first name only) is the one exception, which is why the repo should be private.
3. **Answers must cite a primary source** (a statute section, a case, or a syllabus-map topic ID). If the knowledge base has no source, the tool says so instead of guessing.
4. **Working style:** Tony wants execution, not lectures. State an assumption once and proceed. He is a senior infrastructure and AI practitioner.

## 3. Verified facts (checked on 2026-10-01)

| Fact | Source |
|---|---|
| Course is offered at Wigan & Leigh College, Parsons Walk Campus, Level 3, 16-18, full time, listed as "Law & Criminal Justice T Level" | https://www.wigan-leigh.ac.uk/subject/t-level/ |
| Awarding organisation is Pearson, with CILEX as sector partner | https://qualifications.pearson.com/en/qualifications/t-levels/legal-services.html and https://iateducation.co.uk/new-legal-services-for-delivery-of-t-levels/ |
| Technical Qualification has a core component (exam plus employer-set project) and an occupational specialism | Skills England outline (see SOURCES.md, S-01) |
| Two specialisms exist: Business, Finance and Employment; Crime, Criminal Justice and Social Welfare. The tester is on the second (confirmed by Tony) | Skills England outline; Tony |
| Industry placement is about 45 days (315 hours) | Wigan & Leigh page; T Levels student site |
| Pearson publishes a different specification per start year; the September 2026 intake has its own version | https://qualifications.pearson.com/en/qualifications/t-levels/legal-services.html |
| The Pearson spec is Pearson copyright and is NOT in this repo | Pearson spec PDF footer |

## 4. Done so far

- Confirmed the course, college and campus (2026-10-01).
- Identified the awarding body, structure and specialisms.
- Fetched the Skills England outline content (October 2020) and converted it into `docs/syllabus_map.md`: core topics C01-C15, legal pathway topics L01-L11, employer-set project skills P1-P5, specialism topics S1.xx, S2.xx, S3.xx, all with stable IDs.
- Wrote this handoff, the source register and the architecture sketch.

## 5. Not done, and why

| Item | State |
|---|---|
| GitHub repo | Created by Tony on 2026-10-01: https://github.com/k3ss-official/rileys-law-coach. **It was PUBLIC when this was written. Set it to private** (repo Settings, Danger Zone, Change visibility). Claude's GitHub connector cannot create repos or change visibility, but can push to existing ones. Claude's first commit contains docs only. |
| Notebook tool | **Decided (2026-10-01):** Open Notebook, https://github.com/lfnovo/open-notebook (MIT licence, verified on the repo; about 39,600 stars, the most-starred open-source NotebookLM alternative by name on that date). Chosen by Tony's rule "the one with the most attention". Not yet deployed or evaluated. Other candidates seen: SurfSense (MODSetter/SurfSense, about 16,300 stars), podcastfy (podcast-only), notebookllama (run-llama). |
| VPS | Not chosen. |
| Statutes and case law | Not fetched yet. Planned list is in `SOURCES.md`. |
| Pearson Sept 2026 spec | Deliberately not obtained (copyright). The 2020 Skills England outline is the topic backbone instead. It is older than the current spec, so topics need reconciling against the college's scheme of work if the tester can share it. |
| Licence confirmation | The Skills England outline and legislation.gov.uk content are believed to be government publications under open licences. This has not been verified on the source pages. Do that before ingesting. |
| Code | None written. |

## 6. Tooling notes for whoever resumes

Claude sessions on claude.ai had, on 2026-10-01:

- Web search and page fetch: yes.
- GitHub connector (authenticated as `k3ss-official`): read and write on existing repos; cannot create repos.
- `gh` CLI: not installed in the sandbox.
- Scrapling MCP: not available.
- `last30days` skill: not installed.
- Sandbox with open network access, files delivered via download.

If you are running somewhere with `gh`, Scrapling or other tools, use them; nothing here depends on their absence.

## 7. Next steps, in order

1. **Make the repo private** (Tony). Acceptance: repo shows as Private on GitHub.
2. **Verify licences** for the Skills England outline and legislation.gov.uk on their own pages; record the exact licence name and URL in `SOURCES.md`.
3. **Fetch the criminal-procedure set first** (largest part of the specialism): PACE 1984, Criminal Procedure and Investigations Act 1996, Criminal Justice Act 1967 s9, Proceeds of Crime Act 2002 (s18 and lifestyle provisions), Criminal Procedure Rules, Parole Board Rules 2016. Store each as clean text with its URL, retrieval date and licence. Acceptance: each file has a header block and maps to syllabus topic IDs.
4. **Fetch landmark cases** from the National Archives case-law service (for example Osborn, Booth and Reilly, named in the outline). Acceptance: neutral citation, URL and topic IDs recorded.
5. **Evaluate Open Notebook** (lfnovo/open-notebook): read its README for deployment (Docker or otherwise), hardware and model requirements, and how it exposes retrieval (API or otherwise). Pick the VPS. Acceptance: a short note in `ARCHITECTURE.md` on how the coach and tester layer will call it.
6. **Stand up the notebook with one unit loaded**, then put a small question set in front of the tester for a couple of weeks.
7. **Build the coach and tester layer** (question bank, marking against the spec's skills, spaced repetition per topic ID, weak-spot tracking). See `ARCHITECTURE.md`.
8. Only then: invite other testers.

## 8. Open questions for Tony

- Which VPS should host Open Notebook?
- Can the tester share the college's scheme of work or term plan (his own course handbook, not for redistribution)? It would settle topic order and any drift from the 2020 outline.
- Should the eventual product cover the Business, Finance and Employment specialism too, or stay Crime-only?
