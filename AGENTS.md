# Agent guide

This workspace is a reading graph of three public-domain books: Marcus
Aurelius's *Meditations* (tr. George Long), Machiavelli's *The Prince* (tr.
W. K. Marriott) and Nietzsche's *Beyond Good and Evil* (tr. Helen Zimmern).
You help the user read it, answer questions across the books, and keep their
notes. Documents live in `graph/`; a document's key is its path under `graph/`
without `.md`.

## What is in the graph

| Kind | Key | Frontmatter |
| --- | --- | --- |
| passage | `passages/…` | `type: passage`, `work: meditations \| prince \| bge`, `ref` |
| concept | `concepts/<slug>` | `type: concept`, `works` (the books it links) |
| hub | `index`, `categories`, `notes`, `categories/<slug>`, `books/<key>` | `type: hub` |
| article | `articles/<slug>` | `type: article` |
| note | `notes/<slug>` | `type: note`, `created` (YYYY-MM-DD) |

- **Passages.** 843 documents, each holding the translator's text and nothing
  else. `passages/meditations-BBB-NNN` is book and paragraph, three digits
  each (`meditations-004-003`, titled "Meditations IV.3"). `passages/prince-NN`
  is a chapter, and `prince-00-dedication` the dedication. `passages/bge-NNN`
  is an aphorism (titled "BGE 146"); `bge-065a`, `bge-073a` and `bge-237a` are
  numbered so in the edition, `bge-preface` is the Preface and
  `bge-from-the-heights` the closing poem. `ref` is the citation inside the
  work: `IV.3`, `XXV`, `146`, `Preface`.
- **Meditations numbers are paragraphs of this edition.** The Standard Ebooks
  text prints no section numbers, so `IV.51` is the 51st paragraph of Book IV,
  which other editions number IV.49. A verse Marcus quotes is kept with the
  paragraph before it.
- **What a passage links.** Words in the text link the concepts that list the
  passage. A passage links no other passage, except Long's own
  cross-references in `meditations-012-038`. Passages are never rewritten,
  summarized, modernized or annotated in place.
- **Concepts.** 331 documents, one per idea, person, school or theme.
  `## Summary` says how each author uses it; `## Mentioned In` lists the
  passages under `### Meditations`, `### The Prince` and
  `### Beyond Good and Evil`. `works` names the books that have a group: when
  a concept gains or loses a book, update `works` and the `## Concepts` list
  of that book's hub.
- **Coverage.** 42 concepts link all three books, 13 link two, and 276 belong
  to one book, most of them to Nietzsche. A list holds the passages someone
  judged relevant, about twenty a book at most. Concept lists are a starting
  point: before stating what an author says, also full-text search each book
  for the term and its synonyms, and say so when an author has no passage on
  it.
- **Hubs.** `index` is the only root. It links the books (`books/meditations`,
  `books/prince`, `books/bge`, and under them `books/meditations-book-01` to
  `-12` and `books/bge-part-01` to `-09`), `categories` (19 groups in
  `categories/`; every concept is in at least one), the articles and `notes`.

## Answering a question

1. Read the concept documents the question is about.
2. Search each book: `iwe find --lexical "<terms>" --filter 'work: prince' -f keys`,
   or `grep -ilE '<terms>' graph/passages/prince-*.md`.
3. Read the passages before you state what an author thinks.
4. Quote the translator's words exactly and link each quotation to its passage.

Cite with the translator: *Meditations* IV.3, tr. Long; *The Prince* XXV, tr.
Marriott; *Beyond Good and Evil* 146, tr. Zimmern. A Meditations number is a
paragraph of this edition; say so when the user compares it with another.

The skills `trace-concept`, `compare-authors` and `annotate` hold the steps.

## The user's notes

A note is `graph/notes/<slug>.md` with `type: note` and `created`. It links
the passage or passages it is about inside its sentences, and is listed on a
line of its own in `graph/notes.md`. Never write inside a passage.

## Adding to the graph

- **A concept.** `graph/concepts/<slug>.md` with `type: concept`, `works`,
  `# Title`, `## Summary` and `## Mentioned In` in the shape above. List it in
  a category and in the hub of each book it links.
- **An article.** `graph/articles/<slug>.md` with `type: article`, linked
  under `## Articles` in `graph/index.md`.
- **Links.** Markdown links only, `[Title](../concepts/virtue.md)`, relative
  to the document; never wiki links. A link on a line of its own, or alone in
  a list item, makes the target a child of the document; a link inside a
  sentence is a reference.

Run `iwe schema validate` and `iwe normalize` after a batch of edits.
