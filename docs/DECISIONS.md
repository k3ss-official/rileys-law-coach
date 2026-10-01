# DECISIONS

Dated decision log. **Newer entries override older statements anywhere else in this repo**, including `HANDOFF.md` and `ARCHITECTURE.md`, until those files are rewritten to match.

## D1. Repo name (2026-10-01, Tony)

The repo is `rileys-law-coach`, created by Tony under `k3ss-official`. It was public at creation and should be made private (see `HANDOFF.md`, step 1).

## D2. Notebook tool: Open Notebook (2026-10-01, Tony) - SUPERSEDED by D3

Open Notebook (lfnovo/open-notebook, MIT) was chosen as the most-starred open-source NotebookLM alternative. It was never deployed. References to it in `HANDOFF.md`, `ARCHITECTURE.md` and `SOURCES.md` are historical.

## D3. Notebook tool: Google NotebookLM is the library and study surface (2026-10-01, Tony)

**Decision:** Use Google's NotebookLM instead of Open Notebook. Tony's reason: its learning features are better for studying than the open-source alternative. Tony owns the source-of-truth notebooks under his own Google account and shares them with the first tester. Nothing is hosted on a VPS for the notebook layer.

**Naming:** One secondary source (the notebooklm-py docs) says Google rebranded NotebookLM to "Gemini Notebook" in July 2026. Unverified on Google's own pages. Treat both names as the same product.

**Programmatic access (checked 2026-10-01):**

- There is no official API for consumer accounts that this session could find. Access is through unofficial, reverse-engineered tools that drive a logged-in Google session:
  - `teng-lin/notebooklm-py`: Python API, CLI and agent skill. Reported to cover quiz and flashcard generation, source full-text retrieval, sharing and multi-account profiles. `notebooklm skill install` puts a skill into `~/.claude/skills/notebooklm`.
  - `jacob-bd/notebooklm-mcp-cli`: CLI (`nlm`) plus an MCP server; personal accounts are tested regularly by its author, Enterprise support is experimental. Multiple Google accounts via named profiles.
- Google's Enterprise edition has an official Discovery Engine REST API, but it is narrower (notebooks, sources, audio; no chat or query in the REST API per the third-party docs) and needs Google Cloud auth. Not applicable to a personal or family account.
- Both unofficial tools describe themselves as suited to prototypes and personal projects. They can break when Google changes its internals.

**Architecture consequence:**

- NotebookLM is the **library and study surface**. It holds the approved sources and gives Tony and the tester Google's study features.
- Our own app owns the **question bank, marking, spaced repetition and progress tracking**. It must not depend on NotebookLM being scriptable, because that access is unofficial.
- Data moves by export and import: approved sources are loaded into the notebooks (by hand or with the CLI), and generated quizzes, flashcards and source text are exported into our question bank, tagged with syllabus topic IDs.
- **Before inviting other testers:** other learners would need their own access to the notebooks, or we need a supported path. Decide this at the start of phase 3 of `ARCHITECTURE.md`. Do not build a multi-user product on cookie-based automation.

**Unchanged:** only public-domain or permissively licensed sources go into the notebooks. Every source is tagged in `SOURCES.md` first.

## D4. Working setup (2026-10-01, Tony)

- Repo cloned on Tony's M4 at `~/k3ss-official/rileys-law-coach`.
- A Claude Code session is started from that directory with `claude rc`, so work done there starts from `README.md` then `docs/HANDOFF.md` then this file.
- The claude.ai chat that created this repo pushes through the GitHub connector (existing repos only; it cannot create repos or change visibility).

## Open follow-ups from D3

1. Confirm the NotebookLM / Gemini Notebook naming on Google's own pages.
2. Try `notebooklm-py` and `nlm` against Tony's account with one small notebook and record what works: login, adding a source, generating a quiz, exporting it.
3. Update `ARCHITECTURE.md` layer 1 and `HANDOFF.md` sections 5 and 7 to match D3, then remove the "superseded" note above.
