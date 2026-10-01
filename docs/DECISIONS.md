# DECISIONS

Dated decision log. **Newer entries override older statements anywhere else in this repo.**

## D1. Repo name (2026-10-01, Tony)

The repo is `rileys-law-coach`, created by Tony under `k3ss-official`. It was public at creation and must be made private (`HANDOFF.md`, step 1).

## D2. Notebook tool: Open Notebook (2026-10-01, Tony) - SUPERSEDED by D3

Open Notebook (lfnovo/open-notebook, MIT) was chosen first as the most-starred open-source NotebookLM alternative. It was never deployed. Mentioned only as history.

## D3. Notebook tool: Google NotebookLM is the library and study surface (2026-10-01, Tony)

**Decision:** Use Google's NotebookLM instead of Open Notebook. Tony's reason: its learning features are better for studying than the open-source alternative. Tony owns the source-of-truth notebooks under his own Google account and shares them with the first tester. Nothing is hosted on a VPS for the notebook layer.

**Naming:** One secondary source (the notebooklm-py docs) says Google rebranded NotebookLM to "Gemini Notebook" in July 2026. Unverified on Google's own pages. Treat both names as the same product.

**Programmatic access (checked 2026-10-01):**

- There is no official API for consumer accounts that was found. Access is through unofficial, reverse-engineered tools that drive a logged-in Google session:
  - `teng-lin/notebooklm-py`: Python API, CLI and agent skill. Reported to cover quiz and flashcard generation, source full-text retrieval, sharing and multi-account profiles. `notebooklm skill install` puts a skill into `~/.claude/skills/notebooklm`.
  - `jacob-bd/notebooklm-mcp-cli`: CLI (`nlm`) plus an MCP server; personal accounts are tested regularly by its author, Enterprise support is experimental. Multiple Google accounts via named profiles.
- Google's Enterprise edition has an official Discovery Engine REST API, but it is narrower (notebooks, sources, audio; no chat or query in the REST API per third-party docs) and needs Google Cloud auth. Not applicable to a personal or family account.
- Both unofficial tools describe themselves as suited to prototypes and personal projects. They can break when Google changes its internals.

**Architecture consequence:**

- NotebookLM is the **library and study surface**. It holds the approved sources and gives Tony and the tester Google's study features.
- Our own app owns the **question bank, marking, spaced repetition and progress tracking**. It must not depend on NotebookLM being scriptable.
- Data moves by export and import: approved sources go into the notebooks (by hand or with the CLI), and generated quizzes, flashcards and source text are exported into our question bank, tagged with syllabus topic IDs.
- **Before inviting other testers:** other learners would need their own access to the notebooks, or we need a supported path. Decide at the start of phase 3 of `ARCHITECTURE.md`.

**Unchanged:** only public-domain or permissively licensed sources go into the notebooks. Every source is tagged in `SOURCES.md` first.

## D4. Working setup (2026-10-01, Tony)

- Repo cloned on Tony's M4 at `~/k3ss-official/rileys-law-coach`.
- Work continues in Claude Code or the Claude desktop app on the M4, started from that directory. The claude.ai chat that created the repo cannot see those sessions. Sessions share context through the repo only: `README.md`, `docs/HANDOFF.md`, `docs/DECISIONS.md`, `docs/STATUS.md`.
- The claude.ai chat pushes through the GitHub connector (existing repos only; no repo creation or visibility changes).

## D5. Documentation hygiene (2026-10-01)

`HANDOFF.md`, `ARCHITECTURE.md` and `SOURCES.md` were rewritten to match D3. `STATUS.md` is the append-only work log. Anyone changing direction adds a numbered decision here.

## Open follow-ups from D3

1. Confirm the NotebookLM / Gemini Notebook naming on Google's own pages.
2. Try `notebooklm-py` and `nlm` against Tony's account with one small notebook and record what works (login, add a source, generate a quiz, export it). This is HANDOFF step 3.
