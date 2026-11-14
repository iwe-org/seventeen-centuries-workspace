# Seventeen Centuries

[![GitHub](https://img.shields.io/badge/GitHub-iwe--org%2Fseventeen--centuries--workspace-blue)](https://github.com/iwe-org/seventeen-centuries-workspace)

A knowledge graph of three books seventeen centuries apart: Marcus Aurelius's *Meditations* (around 170 AD), Machiavelli's *The Prince* (1513) and Nietzsche's *Beyond Good and Evil* (1886). It is an [iWe](https://iwe.md) workspace template: the iWe app installs it into an empty folder, and the reader's agent works from `AGENTS.md` and the skills in `.claude/skills/`.

## What is in it

1,221 documents under `graph/`:

| Kind | Folder | Count |
| --- | --- | --- |
| Passages | `graph/passages/` | 843 |
| Concepts | `graph/concepts/` | 331 |
| Category hubs | `graph/categories/` | 19 |
| Book hubs | `graph/books/` | 24 |
| Articles | `graph/articles/` | 1 |
| Start page, Categories, Notes | `graph/` | 3 |

A passage holds the translator's text and nothing else. A concept has a summary of how each author uses it and a *Mentioned In* list of passages grouped by book. 42 concepts link passages from all three books, 13 link two, and 276 belong to one book, most of them to *Beyond Good and Evil*.

The graph is a polyhierarchy: a passage is a child of its book and of every concept that lists it, and a concept is a child of its categories and of the hub of each book it links.

## Source texts

All three are public-domain editions from [Standard Ebooks](https://standardebooks.org/):

| Book | Hub | Author, translator | Passages |
| --- | --- | --- | --- |
| [Meditations](https://standardebooks.org/ebooks/marcus-aurelius/meditations/george-long) | [books/meditations.md](graph/books/meditations.md) | Marcus Aurelius, tr. George Long | 515 paragraphs in 12 books |
| [The Prince](https://standardebooks.org/ebooks/niccolo-machiavelli/the-prince/w-k-marriott) | [books/prince.md](graph/books/prince.md) | Niccolò Machiavelli, tr. W. K. Marriott | 27: the dedication and 26 chapters |
| [Beyond Good and Evil](https://standardebooks.org/ebooks/friedrich-nietzsche/beyond-good-and-evil/helen-zimmern) | [books/bge.md](graph/books/bge.md) | Friedrich Nietzsche, tr. Helen Zimmern | 301: the Preface, 299 aphorisms (296 numbers plus 65a, 73a and 237a) and the poem "From the Heights" |

The Standard Ebooks *Meditations* prints no section numbers, so its passages are numbered by paragraph: `meditations-004-051` is the 51st paragraph of Book IV, which other editions number IV.49.

## Document formats

A passage (`graph/passages/bge-146.md`):

``` markdown
---
type: passage
work: bge
ref: '146'
---

# BGE 146

He who fights with monsters should be careful lest he thereby become a monster. And if thou gaze long into an abyss, the abyss will also gaze into thee.
```

Keys are `passages/meditations-BBB-NNN` (titled "Meditations IV.3"), `passages/prince-NN` (titled with the chapter number and heading) and `passages/bge-NNN` (titled "BGE 146").

A concept (`graph/concepts/fortune.md`):

``` markdown
---
type: concept
works:
- meditations
- prince
- bge
---

# Fortune

## Summary

Machiavelli makes fortune a named adversary of political skill …

## Mentioned In

### Meditations

- [Meditations II.3](../passages/meditations-002-003.md)

### The Prince

- [XXV. What Fortune Can Effect in Human Affairs and How to Withstand Her](../passages/prince-25.md)

### Beyond Good and Evil

- [BGE 203](../passages/bge-203.md)
```

The five kinds (passage, concept, hub, article, note) each have a schema in `.iwe/schemas/` and a UI sidecar that tells the iWe app which fields to show beside a link to the document.

## Categories

[Categories](graph/categories.md) links 19 groups, and every concept is in at least one:

- [Aesthetics](graph/categories/aesthetics.md)
- [Epistemology](graph/categories/epistemology.md)
- [Gender Relationships](graph/categories/gender-relationships.md)
- [Metaphysics](graph/categories/metaphysics.md)
- [Moral Systems](graph/categories/moral-systems.md)
- [Nietzschean Concepts](graph/categories/nietzschean-concepts.md)
- [Paradoxes](graph/categories/paradoxes.md)
- [People](graph/categories/people.md)
- [Peoples and Cultures](graph/categories/peoples-and-cultures.md)
- [Philosophers](graph/categories/philosophers.md)
- [Philosophical Schools](graph/categories/philosophical-schools.md)
- [Politics](graph/categories/politics.md)
- [Power Dynamics](graph/categories/power-dynamics.md)
- [Psychology and Instinct](graph/categories/psychology.md)
- [Religion](graph/categories/religion.md)
- [Self Development](graph/categories/self-development.md)
- [States of Being](graph/categories/states-of-being.md)
- [Virtues](graph/categories/virtues.md)
- [Will Concepts](graph/categories/will-concepts.md)

## Articles

- [Virtue across seventeen centuries](graph/articles/virtue-across-centuries.md): how the meaning of virtue changes from Marcus Aurelius through Machiavelli to Nietzsche.

## How the graph was built

1. **Passages.** Each book was converted from the Standard Ebooks XHTML into one markdown document per paragraph (*Meditations*), chapter (*The Prince*) or aphorism (*Beyond Good and Evil*). Endnote references are dropped, emphasis becomes `*text*`, quoted verse becomes a blockquote with its line breaks kept.
2. **Concepts.** Ideas, people and schools were extracted from the passages, one document each, and the word in the passage was linked to its concept.
3. **Categories.** Concepts were grouped into thematic hubs; a concept can sit in several.
4. **Summaries.** Each concept got a summary written from the passages it lists.
5. **Version 2.0.0.** The documents were sorted into folders and given frontmatter and schemas, near-duplicate concepts were merged, and 50 general concepts were traced through each of the three books by full-text search and reading. See [CHANGELOG.md](CHANGELOG.md).

## Checks

From the template folder:

``` bash
iwe-template check .
iwe schema validate
iwe normalize && git diff --exit-code
```

## License

The graph is licensed under CC BY 4.0; the source texts are in the public domain. See [LICENSE.md](LICENSE.md).

## Related projects

- [IWE](https://iwe.md): the CLI and documentation
- [Standard Ebooks](https://standardebooks.org/): the source texts
