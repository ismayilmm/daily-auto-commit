# Contributing

Thanks for your interest in improving **daily-auto-commit**! This is a small
project, so the process is light.

## Ways to contribute

- **Report a bug or request a feature** — open an
  [issue](../../issues). Include what you expected, what happened, and a link to
  a failing Actions run if relevant.
- **Improve the docs** — typos, clearer wording, and better examples are all
  welcome.
- **Send a fix or enhancement** — open a pull request (see below).

## Pull requests

1. Fork the repo and create a branch: `git checkout -b my-change`.
2. Make your change. Keep it focused and small.
3. If you edited [`.github/workflows/daily-commit.yml`](.github/workflows/daily-commit.yml),
   validate the YAML and, ideally, test it on your own fork with
   `gh workflow run "Daily Additive Commits"` before opening the PR.
4. Use clear commit messages. [Conventional Commits](https://www.conventionalcommits.org/)
   (`feat:`, `fix:`, `chore:`, `docs:`) are appreciated but not required.
5. Open the PR and describe **what** changed and **why**.

## Scope

The goal is to stay tiny and dependency-free: a single workflow that makes
additive commits on a schedule. Please keep changes aligned with that — new
features should be optional and not add runtime dependencies.

## Code of Conduct

By participating, you agree to uphold our
[Code of Conduct](CODE_OF_CONDUCT.md).
