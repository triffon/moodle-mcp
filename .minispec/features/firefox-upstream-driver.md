# Firefox: back to the upstream driver

## Goal

Send the Firefox channel (branch `feat/firefox-channel`) as a pull request, on the upstream `@falkenslab/moodle-driver` instead of the fork.

## Context

- The branch has two commits: `build(deps)` puts the fork `@triffon/moodle-driver@0.10.0-firefox.1` under the driver's name (an npm alias), and `feat(config)` adds the channel itself.
- The fork exists only until falkenslab/moodle-driver#89 is merged and released upstream. Waiting on that; nothing to do before it.

## Changes

- Replace the `build(deps)` commit with one bumping `@falkenslab/moodle-driver` in `package.json` to the release with Firefox (a plain version, no `npm:` alias), then `npm install` for the lock file.
- Remove the fork note from the driver's line in `.minispec/core/stack.md`.
- Rebase the branch on `main` if it moved.
- Run the `verify` skill (typecheck, lint, build, the Docker tests, the `--strict` check).
- Push the branch and open the pull request; delete this card in the same change.

## Acceptance

- `package.json` and `package-lock.json` name no `@triffon/` package.
- `verify` passes: tests `fail 0`, `--strict` with `exit=0 warnings=0`.
- `server_info` shows `openChannel: "firefox"` with `--channel firefox`, in Docker.
