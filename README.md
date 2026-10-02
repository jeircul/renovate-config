# renovate-config

Shared Renovate preset for the `jeircul` repositories.

## Use

Add the preset to `.github/renovate.json5`:

```json5
{
  extends: ['github>jeircul/renovate-config'],
}
```

Renovate reads `default.json` from this repository.

## Rules

`default.json` sets these rules:

- Extends `config:recommended`.
- Uses semantic commit messages (`:semanticCommits`).
- Pins GitHub Actions to a commit digest (`helpers:pinGitHubActionDigests`).
- Puts all minor and patch updates into one PR (`group:allNonMajor`).
- Automerges minor and digest updates (`:automergeMinor`, `:automergeDigest`).
- Refreshes lock files once a month (`:maintainLockFilesMonthly`).
- Runs before 06:00 on Monday, `Europe/Oslo` time.
- Waits 3 days after a release before it proposes the update.
- Opens a maximum of 5 PRs at the same time.
- Rebases a PR only when it has a conflict.
- Labels all PRs `dependencies`. Major updates also get `major`.
- Enables OSV vulnerability alerts. Security PRs get the label `security`.
- Does not update `jeircul/**` actions. Callers track `@main` of their own actions on purpose.

## Changes

A change on `main` applies to every repository that extends the preset. The `validate` workflow runs `renovate-config-validator --strict` on each PR and on each push to `main`.

## License

MIT. See `LICENSE`.
