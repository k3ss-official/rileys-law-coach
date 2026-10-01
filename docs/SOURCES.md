# SOURCES

Register of every source considered. **Rule: only public-domain or permissively licensed material may be ingested into the notebooks or the repo.** Update the status as you go. "Fetched" means stored with header metadata (URL, retrieval date, licence).

Status key: `IN` = approved for ingest, `VERIFY` = believed usable, licence must be confirmed on the source page first, `OUT` = do not ingest.

## A. Already used

| ID | Source | URL | Used for | Licence status | Fetched |
|---|---|---|---|---|---|
| S-01 | Skills England (formerly IfATE), Legal Services T Level outline content, Oct 2020 | https://skillsengland.education.gov.uk/media/4616/final_legal_services_tlevel_outlinecontent_oct2020_itt.pdf | Basis of `docs/syllabus_map.md` (reworded and restructured, not copied) | VERIFY (government publication; confirm licence on page) | Read 2026-10-01 |
| S-02 | Wigan & Leigh College, T Levels page | https://www.wigan-leigh.ac.uk/subject/t-level/ | Confirming course, campus, level, UCAS points | Facts only, no text stored | Read 2026-10-01 |
| S-03 | Pearson, T Level in Legal Services page | https://qualifications.pearson.com/en/qualifications/t-levels/legal-services.html | Confirming awarding body and structure | Facts only, no text stored | Read 2026-10-01 |

## B. Tooling (not knowledge sources)

| Tool | URL | Licence | Status |
|---|---|---|---|
| notebooklm-py (unofficial NotebookLM Python API and CLI) | https://github.com/teng-lin/notebooklm-py | Check repo before use | Not yet tried |
| notebooklm-mcp-cli (`nlm`, unofficial CLI and MCP server) | https://github.com/jacob-bd/notebooklm-mcp-cli | Check repo before use | Not yet tried |
| Open Notebook (considered in D2, dropped in D3) | https://github.com/lfnovo/open-notebook | MIT (verified 2026-10-01) | Not used |

## C. Explicitly out

| ID | Source | Why |
|---|---|---|
| X-01 | Pearson T Level Legal Services specification and sample assessment materials (all versions) | Pearson copyright |
| X-02 | Publisher textbooks and revision guides | Copyright |
| X-03 | College handouts, slides and VLE content | College or author copyright |
| X-04 | Practitioner texts named in the outline (Archbold, Blackstone's Criminal Practice, Stone's Justices' Manual, Banks on Sentence and so on) | Commercial publications |
| X-05 | Paid databases (Westlaw, LexisNexis, CrimeLine) | Licensed content |

## D. Planned, not yet fetched

Primary law from legislation.gov.uk (licence: VERIFY, believed Open Government Licence), and case law from the National Archives Find Case Law service (licence: VERIFY).

Criminal specialism, first priority:

| Item | Maps to topics |
|---|---|
| Police and Criminal Evidence Act 1984 | S1.01, S1.06 |
| Criminal Procedure and Investigations Act 1996 (disclosure) | S3.02 |
| Criminal Justice Act 1967, s9 (witness statements) | S3.02 |
| Proceeds of Crime Act 2002 (incl. s18) | S1.04, PO3 skills |
| Criminal Procedure Rules (current) | S1.04, S3.01 |
| Parole Board Rules 2016 | S1.07, S3.01 |
| Criminal Finances Act 2017 | L07 |
| Anti-social Behaviour, Crime and Policing Act 2014 | S1.12 |
| Case: Osborn, Booth and Reilly (2013), Parole Board oral hearings | S3.01 |

Social welfare, second priority:

| Item | Maps to topics |
|---|---|
| Housing Acts 1985, 1988, 1996; Landlord and Tenant Act 1985 | S1.12, S2.05, S3.04 |
| Equality Act 2010; Human Rights Act 1998 | C08, S1.12 |
| Insolvency Act 1986; Limitation Act 1980 | S1.14, S2.05, S3.05 |
| Consumer Rights Act 2015 | C10, S1.14 |

Core, third priority:

| Item | Maps to topics |
|---|---|
| Companies Act 2006 (relevant parts) | C02 |
| Data protection legislation (UK GDPR, Data Protection Act 2018) | C05, C07 |

## E. Ingest header (put this on every stored source file, and in the notebook source title or notes)

```
source_id:      e.g. L-PACE-1984
title:
url:
retrieved:      YYYY-MM-DD
licence:        exact licence name and URL, as found on the source page
version_note:   point-in-time or "as amended to <date>"
topic_ids:      e.g. S1.01, S1.06
```

Statutes change. Record the point-in-time version and re-check anything the tester is examined on close to the exam date.
