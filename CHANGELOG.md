# Changelog

All notable changes to this template are documented here. The format is based on
[Keep a Changelog](https://keepachangelog.com/en/1.0.0/).

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
