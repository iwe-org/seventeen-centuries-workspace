---
name: compare-authors
description: Compare how Marcus Aurelius, Machiavelli and Nietzsche treat one theme — the same search per author, the passages quoted with citations, and an explicit section on where they disagree. Use when the user asks "how do they differ on X", "compare Marcus and Nietzsche on X", or wants an article that sets the authors side by side.
---

# Compare the authors

## Steps

1. **Gather per author.** For each of the three books, do what the
   trace-concept skill does: the concept document first, then a full-text
   search of that book for the term and its synonyms, then the passages
   themselves.

   ``` bash
   iwe retrieve -k concepts/death
   iwe find --lexical "death die dying" --filter 'work: meditations' -f keys
   iwe find --lexical "death die dying" --filter 'work: prince' -f keys
   iwe find --lexical "death die dying" --filter 'work: bge' -f keys
   ```

2. **Write one section per author**, in the order Marcus Aurelius,
   Machiavelli, Nietzsche. Each states the author's position in a sentence or
   two and supports it with exact quotations, each linked to its passage and
   cited as `*Meditations* IV.3, tr. Long`, `*The Prince* XXV, tr. Marriott`
   or `*Beyond Good and Evil* 146, tr. Zimmern`.

3. **Write a "Where they disagree" section.** Name each disagreement as a
   claim one author makes and another denies, with the passage on each side.
   Keep agreement that is only verbal (the same word for different things,
   such as Marriott's "virtue" and Long's) apart from real agreement.

4. **Write a "What is missing" section.** An author with no passage on the
   theme is a finding: say so, list the terms you searched, and do not fill
   the gap from what you know of the author outside these three books.

When the user wants to keep the comparison, save it as an article:
`graph/articles/<slug>.md` with `type: article` in its frontmatter, linked
under `## Articles` in `graph/index.md`.
