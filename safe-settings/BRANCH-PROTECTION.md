# Branch protection policy

GitHub Free organizations cannot access the branch-protection API for private repositories. Safe Settings full-sync fails with HTTP 403 when the global `settings.yml` includes `branches` and attempts to apply it to `sharedale/sharedale`.

Therefore `safe-settings/settings.yml` intentionally omits `branches`. Other repository settings and labels remain organization-wide. For repositories on plans that support branch protection, place the intended `branches` configuration in `safe-settings/repos/<repository>.yml` (or use a supported higher-level policy), rather than applying it indiscriminately.

Native auto-merge is disabled in `settings.yml`. GitHub documents auto-merge as merging after
**required** reviews and status checks; those requirements cannot be enforced for this private
repository on GitHub Free. Do not add a workflow or bot that replaces that enforcement. Dependabot
may still open grouped patch/minor and major update PRs, but all merging remains manual until the
protection policy exists.

When private branch protection is available for `sharedale/sharedale`, restore the intended `main`
protections: PR-only changes, linear history, and required CI status checks once CI is established.
See https://github.com/sharedale/sharedale/issues/68. After the stable checks have run successfully,
re-enable native auto-merge only for the approved Dependabot patch/minor policy; major updates
remain manual.

This is a **plan-based limitation**, not a GitHub App authorization issue. Do not make the application repository public to work around it.
