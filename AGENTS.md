# AGENTS.md

A composite GitHub Action that installs the [Mops](https://mops.one) package manager (with caching of packages and toolchain) into a workflow.

## Layout

- `action.yml` — the action definition (composite `runs.steps`); this is the entire implementation.
- `.github/workflows/test-self.yml` — CI that self-tests the action.

There is no application source code, build system, or test runner in this repository.

## Testing

The action has no unit tests. It is validated by the `test-self.yml` workflow, which runs the action against a matrix of `mops-version`, `wasmtime-version`, and `pocket-ic-version` values on `ubuntu-latest` and `macos-latest`, then checks the installed tool versions. This runs on push to `main` and on pull requests. There is no local test command; changes to `action.yml` are verified through CI.

## Conventions

- GitHub Actions `uses:` references are pinned to full commit SHAs with the version in a trailing comment (e.g. `actions/cache@0057852... # v4.3.0`). Keep this style when adding or updating actions.
- All composite steps declare `shell:` explicitly (`sh`), as required for composite actions.
- The `identity-pem` input is a secret; never hard-code it — pass it via GitHub Secrets.
