# Zettelkasten

This repository version-controls my note-taking workflow for a local
zettelkasten vault. The vault is managed in Obsidian and edited primarily
through Neovim with
[obsidian.nvim](https://github.com/obsidian-nvim/obsidian.nvim).

## Notes Workflow

Notes move through three stages:

1. Create new note
   - Created using `~/dotfiles/stow/local/.local/scripts/on`
   - Stored in temporary directory
   - Front-matter added via template in Neovim

2. Review and decide whether to keep it
   - Review initiated using `~/dotfiles/stow/local/.local/scripts/or`
   - Review performed in Neovim (see `obsidian.lua` file)
     - If not kept -> file deleted
     - If kept -> move to new temporary directory

3. Refile kept notes into long-term directory
   - Refile using `~/dotfiles/stow/local/.local/scripts/og`
   - Notes refiled in sub-directory based on `tag` in note front-matter

The result is a small pipeline:

```text
tmp/ -> keep/ -> tag-specific directory
```

## Repository Structure

```text
zettelkasten/
├── README.md
├── images/         # image files linked in notes
├── tmp/            # default location for new notes
├── keep/           # contains notes kept after review
└── notes/          # notes organized in [tag] sub-directories
     ├── python/
     │   └── ...
     └── books/
         └── ...
```

## Conventions

- File names should be descriptive enough to produce a readable title.
- Tags should describe where a note belongs, not only what it mentions.
- Hub links connect related notes and let hub pages populate from backlinks.
- Temporary notes should be reviewed weekly so `tmp/` stays small.
