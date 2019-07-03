# Lessons Learned on Using Shell in Windows

Tooling in use: Windows 10, `cmder`, git-for-windows bash.

### Integration Gotchas

- `poetry shell` should not be used in bash for Windows, only in cmd/cmder, or else it falls through to wsl shell with no tools and wrong interpreter.

### Git shortcuts

`git log --all --grep='png'` - Search for matches in Git commit messages.
