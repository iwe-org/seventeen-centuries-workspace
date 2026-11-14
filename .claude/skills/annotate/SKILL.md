---
name: annotate
description: Save the user's own note on a passage — a new document in graph/notes/ that links the passage and is listed in the Notes hub. Use when the user says "note that ...", "add a note on IV.3", "annotate this passage", or wants to keep a thought about something they read.
---

# Annotate a passage

The user's notes live beside the books, never inside them. A passage holds
the translator's text and nothing else.

## Steps

1. **Find the passage** the note is about and read it.

   ``` bash
   iwe find --fuzzy "Meditations IV.3" -f keys
   iwe retrieve -k passages/meditations-004-003
   ```

2. **Create the note** as `graph/notes/<slug>.md`, the slug a few lowercase
   words joined by hyphens. Use the user's words; do not expand them.

   ``` markdown
   ---
   type: note
   created: 2026-01-31
   ---

   # Retreat into yourself

   On [*Meditations* IV.3, tr. Long](../passages/meditations-004-003.md): the
   retreat he recommends is a habit of attention, not a place.
   ```

   `created` is today's date. Every passage the note is about is linked inside
   a sentence, with its citation as the link text.

3. **List it in the Notes hub.** Add a line of its own to `graph/notes.md`:

   ``` markdown
   [Retreat into yourself](notes/retreat-into-yourself.md)
   ```

4. **Check.**

   ``` bash
   iwe schema validate
   iwe normalize
   ```

Never write the note, a highlight or a comment into the passage document.
