# daily-auto-commit

> A self-running repo. A scheduled GitHub Actions workflow makes **5 additive
> commits per day** — automatically, with zero servers and zero maintenance.

[![Daily Additive Commits](https://img.shields.io/badge/cron-5%20commits%2Fday-2ea44f)](.github/workflows/daily-commit.yml)
[![License: MIT](https://img.shields.io/badge/license-MIT-blue)](LICENSE)
[![Made with GitHub Actions](https://img.shields.io/badge/made%20with-GitHub%20Actions-2088ff?logo=githubactions&logoColor=white)](https://docs.github.com/actions)

Fork it (or use it as a template), enable Actions, and walk away. Commits are
attributed to **you** automatically, so they count toward your contribution
graph — no configuration required.

---

## Quick start

1. **Get your own copy** — click **[Use this template](../../generate)** (or
   just **Fork**).
2. **Enable Actions** — open the **Actions** tab in your new repo and click
   **"I understand my workflows, go ahead and enable them"** (GitHub disables
   workflows on forks/templates by default).
3. **Done.** The workflow now runs 5×/day on the [schedule below](#schedule-utc).

Want to see it work immediately, without waiting for the cron?

```bash
gh workflow run "Daily Additive Commits"   # triggers a run now
```

## How it works

[`.github/workflows/daily-commit.yml`](.github/workflows/daily-commit.yml) is
triggered by **5 cron schedules**. Each run:

1. Checks out the repo.
2. Appends one timestamped line to [`activity.log`](activity.log).
3. Commits and pushes that change back to the default branch.

One commit per trigger × 5 triggers = **5 commits/day**.

## Schedule (UTC)

| Trigger | Cron          |
|---------|---------------|
| ~02:17  | `17 2 * * *`  |
| ~07:23  | `23 7 * * *`  |
| ~12:31  | `31 12 * * *` |
| ~17:19  | `19 17 * * *` |
| ~22:43  | `43 22 * * *` |

Times are off-the-hour on purpose: GitHub's scheduler is busiest at `:00` and
most likely to delay or drop runs then.

## Configuration

Everything works out of the box. To override the commit identity, add
**repository variables** under *Settings → Secrets and variables → Actions →
Variables*:

| Variable         | Default                                              | Purpose                       |
|------------------|------------------------------------------------------|-------------------------------|
| `GIT_USER_NAME`  | repo owner's login                                   | name on each commit           |
| `GIT_USER_EMAIL` | `<id>+<owner>@users.noreply.github.com` (auto-derived) | email on each commit          |

To change **how often** it commits, edit the `cron:` lines in the workflow —
each line is one commit per day. Add lines for more, remove lines for fewer.

## FAQ

**Do these commits count toward my contribution graph?**
Yes. They're authored with your GitHub no-reply email on the default branch of a
repo you own — that's exactly what GitHub counts.

**Will GitHub turn the schedule off?**
Only after **60 days of no activity**. Since this commits daily, it keeps itself
alive.

**How do I make it private?**
`gh repo edit --visibility private`. Private-repo contributions still show if
"Private contributions" is enabled on your profile.

**How do I stop it?**
Disable it in the Actions tab, or run
`gh workflow disable "Daily Additive Commits"`.

## Contributing

Contributions are welcome — see [CONTRIBUTING.md](CONTRIBUTING.md) and the
[Code of Conduct](CODE_OF_CONDUCT.md).

## License

[MIT](LICENSE) © Ismayil Mammadli and contributors.
