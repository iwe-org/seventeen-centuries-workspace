# Agent guide

This workspace is a knowledge graph of three public-domain books: Marcus
Aurelius's *Meditations*, Machiavelli's *The Prince* and Nietzsche's *Beyond
Good and Evil*. You help the user read it, answer questions across the books,
and write new documents on top of it. Every document lives in `graph/`, and a
document's key is its file name without `.md`.

## How the graph is built

- **Start page.** `index` links the three books, the categories and the
  articles. It is the only root.
- **Books.** `meditations` links its twelve books (`meditations-book-01` to
  `meditations-book-12`), and each of those links its passages
  (`meditations-BBB-PPP`, titled `III.7`). `bge` links its nine parts
  (`bge-part-01` to `bge-part-09`), and each part links its aphorisms
  (`bge-NNN`, plus `bge-065a` and `bge-073a`). `prince` links its dedication
  (`prince-00-dedication`) and its 26 chapters (`prince-NN`).
- **Fragments.** A passage, aphorism or chapter holds the book's text and
  nothing else, with inline links to the concepts it mentions. The text is the
  source edition's: never rewrite, summarize or modernize it in place.
- **Concepts.** One document per idea, person, school or theme (`virtue`,
  `will-to-power`, `socrates`). It opens with `## Summary`, a comparison of how
  the books use it, followed by `## Mentioned In`, which links every fragment
  that mentions it, grouped by book.
- **Categories.** `categories` links the thematic groups (`philosophers`,
  `virtues`, `politics`, …), and each group links its concepts. A concept may
  sit in several groups.
- **Articles.** Essays written from the graph, such as
  `virtue-across-centuries`, listed under `## Articles` in `index`. They quote
  the fragments and link each quotation to its fragment.

## Answering a question

1. Find the concepts the question is about, and read their summaries.
2. Follow `## Mentioned In` to the fragments, and read the passages themselves
   before you state what an author thinks.
3. Quote the text, and link every quotation to the fragment it comes from.

## Adding to the graph

- **A new concept.** Create `graph/<slug>.md` with `# Title`, `## Summary` and
  `## Mentioned In` in the shape above. Add a link to it in every fragment that
  mentions it, and list it in the category it belongs to.
- **A new article.** Create `graph/<slug>.md` and link it under `## Articles`
  in `index` and under `## Articles` in the concepts it is mainly about.
- **Links.** Use markdown links, `[Title](key.md)`. A link on a line of its
  own makes the target a child of the document; a link inside a sentence is a
  reference.

Run `iwe normalize` after a batch of edits to keep the formatting consistent.
