# Changelog

All notable changes to this template are documented here. The format is based on
[Keep a Changelog](https://keepachangelog.com/en/1.0.0/).

## [2.0.0]

Document keys change: every document moved into a folder.

### Added

- Frontmatter on every document and a schema with a UI sidecar for each kind
  (`passage`, `concept`, `hub`, `article`, `note`), bound in
  `.iwe/config.toml`. In the iWe app a link to a passage shows its work, and a
  link to a concept the works it spans.
- The Preface and the closing poem "From the Heights" of *Beyond Good and
  Evil*.
- 19 general concepts that had no document (among them fame, necessity, duty,
  freedom, law, war, friendship, anger, wisdom, religion, courage and love).
- `graph/notes.md`, the hub for the reader's own notes in `graph/notes/`, a
  Sources section on the start page, and three skills: `trace-concept`,
  `compare-authors` and `annotate`.

### Changed

- Documents live in `graph/passages/`, `graph/concepts/`,
  `graph/categories/`, `graph/books/` and `graph/articles/`. The category
  `psychology-category` is `categories/psychology`, titled "Psychology and
  Instinct", and `ancient-cultures` is `categories/peoples-and-cultures`.
- A passage's title is its citation: "Meditations IV.3", "BGE 146".
- 50 general concepts (fortune, death, power, justice, nature, truth and
  others) were traced through each book by full-text search and reading.
  42 concepts now link all three books, where one did, and their summaries
  compare the authors from the passages they list. Every concept groups
  *Mentioned In* by book.
- 25 near-duplicate concepts were merged into 20 others, among them the two Cesare
  Borgia documents, `god` and `gods`, `stoicism` and `stoics`, and the three
  on free will. There are 331 concepts.
- Every concept is in at least one category, and concept titles are in title
  case.
- `AGENTS.md` describes the graph as it is, with a citation format that names
  the translator.
- The article uses markdown links instead of wiki links.

### Fixed

- Em dashes are written "—" instead of "---" (1,252 places).
- Linked words in the passages have the translator's wording again: 220 had
  been replaced by the concept's capitalized title.
- Quoted verse keeps its line breaks, and eleven verse quotations the
  passages had lost are back (eight in the *Meditations*, Virgil in *The
  Prince* XVII and Petrarch in XXVI), with the two closing lines of
  *Meditations* I and II.
- Long's cross-references in *Meditations* XII.38 link the paragraphs he
  cites.
- The Philosophers and Religion categories are no longer linked from
  passages as if they were concepts.

### Known

- The *Meditations* are numbered by paragraph of the Standard Ebooks edition,
  which prints no section numbers; a number can differ from other editions.

## [1.1.0]

### Changed

- Every hub's title starts with an emoji, which the iWe sidebar draws as the
  hub's icon: the start page, Categories and each category, the three books,
  the twelve books of the *Meditations* and the nine parts of *Beyond Good and
  Evil*.

## [1.0.1]

### Added

- `preview.png` — the image the iWe template gallery shows for this template.

## [1.0.0]

### Added

- `template.toml` — the manifest that lists this workspace in the iWe template
  gallery.
- `graph/index.md` — the start page the iWe app opens when it creates a
  workspace from this template. It replaces `graph/overview.md`.
- `AGENTS.md` — how the graph is built and how an agent answers questions and
  adds to it. It replaces the `iwe` CLI reference in `CLAUDE.md`.
- `LICENSE.md` — CC BY 4.0 for the graph, with the source texts in the public
  domain.

### Changed

- `.iwe/config.toml` is version 4 and names `graph` as the documents root in
  `[workspace]`.

### Removed

- The actions that ran `claude -p` (Expand, Keywords, Rewrite, Emojify) and the
  `[commands]` table they used.
- `graph/entity_files.txt` and `graph/extract_mentioned_in.sh`, leftovers of the
  build pipeline.
