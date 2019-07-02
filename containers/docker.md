# How Do I... in Docker

Tech Stack: Windows 10, Python 3.7+, Poetry package manager, Visual Studio Code for debug and edit.

### Q: How do I debug a Python app with Docker?

A: Set up `Dockerfile` for your Python service, a `docker-compose` config, mount volumes with your code into the container, and run a change watcher on Windows to be able to detect code changes. Then connect the VS Code debugger.

On Windows, use `docker-windows-volume-watcher`.
