---
name: trace-concept
description: Trace one concept through the three books — read its concept document, full-text search each book for the term and its synonyms, read the passages, quote them with citations, and say where an author has nothing. Use when the user asks "what does Marcus/Machiavelli/Nietzsche say about X", "where does X come up", or "trace X".
---

# Trace a concept

A concept document is a starting point, not the whole answer: its list holds
the passages someone already judged relevant. Search the text as well, every
time.

## Steps

1. **Read the concept document**, if there is one. Its `works` field names the
   books it links; `## Mentioned In` lists the passages by book.

   ``` bash
   iwe find --fuzzy fortune -f keys
   iwe retrieve -k concepts/fortune
   ```

2. **Search each book** for the term and its synonyms in the translator's
   vocabulary (Long: "ruling faculty", "universal nature"; Marriott: "valour",
   "ability"; Zimmern: "sympathy" for pity, "gregarious" for herd). Run one
   search per book:

   ``` bash
   iwe find --lexical "fortune chance" --filter 'work: meditations' -f keys
   iwe find --lexical "fortune chance" --filter 'work: prince' -f keys
   iwe find --lexical "fortune chance" --filter 'work: bge' -f keys
   grep -ilE 'fortune|chance' graph/passages/meditations-*.md
   ```

3. **Read the passages** before stating what an author says. A word match is
   not a treatment: "by nature" in passing is not a passage on nature.

   ``` bash
   iwe retrieve -k passages/prince-25
   ```

4. **Answer by author.** Quote the translator's words exactly, and link every
   quotation to its passage with the citation as the link text:

   - `[*Meditations* IV.3, tr. Long](graph/passages/meditations-004-003.md)`
   - `[*The Prince* XXV, tr. Marriott](graph/passages/prince-25.md)`
   - `[*Beyond Good and Evil* 146, tr. Zimmern](graph/passages/bge-146.md)`

   Inside a document in `graph/`, write the link relative to that document.

5. **State the gaps.** When a book has no passage on the concept, say so, and
   say which terms you searched.

Never edit a passage. When the search finds passages the concept document
lacks, offer to add them: a list item under the book's `###` heading in
`## Mentioned In`, the book in `works` if it is new there, and the same
passage linked back from the word in its text only if the user asks for it.
