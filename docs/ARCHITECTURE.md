# ARCHITECTURE (intended design, not yet built)

Status: sketch agreed in conversation on 2026-10-01 and updated for D3 (Google NotebookLM). Nothing below is implemented. Change it freely as the build teaches you things, and record direction changes in `DECISIONS.md`.

## Principle

The notebook is the **library and study surface**. The product is the **layer on top**: structured syllabus, question bank, marking, spaced repetition and weak-spot tracking. Grounded retrieval gives cited answers; it does not by itself test, schedule revision or track progress.

## Layers

1. **Library and study surface: Google NotebookLM**
   Notebooks owned by Tony's Google account, holding only approved sources from `SOURCES.md`, shared with the first tester. Tony and the tester use Google's own study features there (chat with citations, quizzes, flashcards, audio and so on). Scriptable access is unofficial (`notebooklm-py`, `notebooklm-mcp-cli`; see D3), so nothing in our app may hard-depend on it. Every document carries the ingest header from `SOURCES.md`.

2. **Syllabus graph**
   `docs/syllabus_map.md` converted to structured data: one record per topic ID with title, type (knowledge or skill), parent unit, linked sources and prerequisites. Every question, flashcard and explanation tags to one or more topic IDs.

3. **Question bank**
   Item types: recall, apply, scenario, draft (mirrors the specialism's performance-outcome tasks such as explaining a process to a client or drafting a letter for a supervisor). Fields: topic IDs, type, difficulty 1-3, model answer, marking points, primary-source citation. Items come from three places: written by us, generated in NotebookLM and exported, or contributed by the tester.

4. **Coach loop**
   Spaced repetition scheduled per topic ID. Weak topics resurface sooner. Short sessions by default, with a visible "how prepared am I" view by unit. The aim is retention and enjoyment, so include quick wins, streaks and variety, not just drilling.

5. **Tester**
   Timed, exam-style sets and scenario practice. Marks against the marking points, explains what was missed, and links back to the source text.

6. **Oracle (ask anything)**
   Answers from approved sources only, with citations. In phase 1 this is NotebookLM's own chat. If the library has no source, it says so and suggests where to look.

7. **Web app**
   Mobile-first (learners are teenagers). Simple login. Progress, streaks and topic heatmap on the home screen. Stack and hosting undecided (`HANDOFF.md`, section 8).

## Data flow

```
approved sources --> NotebookLM notebooks --(export: quizzes, flashcards, source text)--> question bank
                                                                                   |
 syllabus graph (topic IDs) ------------------------------------------------------+--> coach loop --> web app --> tester
```

The export step is the fragile part (unofficial tooling). Keep it a small, replaceable script, and keep a manual export path (copy and paste, or file download) that works without it.

## Data handling

- Store the minimum about learners: a pseudonymous ID, progress and answers. No real names in logs or in this repo.
- Keep learner data separate from the source library.
- Never commit Google session or cookie files.

## Guardrails

- Answers cite a primary source or a syllabus topic ID.
- The tool is a study aid. It does not give legal advice about real situations.
- Law changes: every statute file records its point-in-time version.

## Phasing

1. **Phase 1:** one unit end to end (approved sources in a notebook, tagged question set of 30-50, basic spaced repetition), tested by the first tester for about two weeks.
2. **Phase 2:** full specialism plus core.
3. **Phase 3:** invite other learners. Gate: decide the multi-user path first (each learner's own notebook access, or a supported API route). Do not rely on cookie-based automation for other people's access.

## Open design questions

- Whether the unofficial NotebookLM tooling is reliable enough for the export step (`HANDOFF.md`, step 3).
- Marking approach for free-text and drafting answers (rubric-based model marking with human spot checks).
- Whether the Business, Finance and Employment specialism is in scope.
- Stack and hosting for our own app.
