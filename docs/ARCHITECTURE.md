# ARCHITECTURE (intended design, not yet built)

Status: sketch agreed in conversation on 2026-10-01. Nothing below is implemented. Change it freely as the build teaches you things.

## Principle

The notebook is the **library**. The product is the **layer on top**: structured syllabus, question bank, marking, spaced repetition and weak-spot tracking. Retrieval alone gives grounded answers; it does not teach, test or make someone remember.

## Layers

1. **Library (source of truth)**
   Open Notebook (https://github.com/lfnovo/open-notebook, MIT licence) holding only approved sources from `SOURCES.md`. Hosted on one of Tony's VPS servers. Every document carries the ingest header from `SOURCES.md`.

2. **Syllabus graph**
   `docs/syllabus_map.md` converted to structured data: one record per topic ID with title, type (knowledge or skill), parent unit, linked sources and prerequisites. Every question, flashcard and explanation tags to one or more topic IDs.

3. **Question bank**
   Item types: recall, apply, scenario, draft (mirrors the specialism's performance-outcome tasks such as explaining a process to a client or drafting a letter for a supervisor). Fields: topic IDs, type, difficulty 1-3, model answer, marking points, primary-source citation.

4. **Coach loop**
   Spaced repetition scheduled per topic ID. Weak topics resurface sooner. Short sessions by default, with a visible "how prepared am I" view by unit. The aim is retention and enjoyment, so include quick wins, streaks and variety, not just drilling.

5. **Tester**
   Timed, exam-style sets and scenario practice. Marks against the marking points, explains what was missed, and links back to the source text.

6. **Oracle (ask anything)**
   Free-form questions answered from the library only, with citations. If the library has no source, it says so and suggests where to look.

7. **Web app**
   Mobile-first (learners are teenagers). Simple login. Progress, streaks and topic heatmap on the home screen.

## Data handling

- Store the minimum about learners: a pseudonymous ID, progress and answers. No real names in logs or in this repo.
- Keep learner data separate from the source library so the library can be rebuilt or shared without it.

## Guardrails

- Answers cite a primary source or a syllabus topic ID.
- The tool is a study aid. It does not give legal advice about real situations.
- Law changes: every statute file records its point-in-time version.

## Phasing

1. One unit end to end (library, tags, 30-50 questions, basic spaced repetition), tested by the first tester for a couple of weeks.
2. Full specialism plus core.
3. Invite other learners.

## Open design questions

- How Open Notebook exposes retrieval (API, MCP, or direct vector store) and its hosting requirements. Not yet evaluated.
- Marking approach for free-text and drafting answers (rubric-based model marking with human spot checks).
- Whether the Business, Finance and Employment specialism is in scope.
