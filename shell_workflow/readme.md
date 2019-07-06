# Lessons Learned on Using Shell in Windows

Tooling in use: Windows 10, `cmder`, git-for-windows bash.

### Integration Gotchas

- `poetry shell` should not be used in bash for Windows, only in cmd/cmder, or else it falls through to wsl shell with no tools and wrong interpreter.

### Git shortcuts

- `git log --all --grep='png'` - Search for matches in Git commit messages.

### Docker shortcuts

- `docker volume ls -q | grep "01" | xargs docker inspect` -- inspect all volumes matching pattern
- `docker volume ls -q | grep "01" | xargs docker volume rm` -- remove all volumes matching pattern

[Other pattern operations over `docker` command](https://www.digitalocean.com/community/tutorials/how-to-remove-docker-images-containers-and-volumes)
