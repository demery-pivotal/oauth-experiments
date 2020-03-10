# Dale's OAuth Experiments Repository

In this repo:

- `.bin`:
  Scripts to start, stop, and clean up
  a cluster with one server and one locator.
- `.envrc`
  A `direnv` configuration file that configures
  some handy environment variables and paths.
  See the file's comments for details.
  For this to do anything, you will need `direnv` installed.
- `cf-config/uaa.yml`:
  A UAA configuration that configures:
  - A set of Geode permissions.
  - A set of users with various Geode permissions.
  - A simple Pulse client that can request Geode permissions.
- `notes/docs.md`:
  Links to UAA documentation,
  plus some notes from Dale.
- `notes/how-to.md`:
  - How to build, configure, and run the UAA server.
  - How to install `uaac` (a CLI for interacting with UAA).
  - How to do various tasks using `uaac`.
- `uaa`:
  The UAA source code (as a git submodule).
