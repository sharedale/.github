# Branch protection policy

GitHub Free organizations cannot access the branch-protection API for private repositories. Safe Settings full-sync fails with HTTP 403 when the global `settings.yml` includes `branches` and attempts to apply it to `sharedale/sharedale`.

Therefore `safe-settings/settings.yml` intentionally omits `branches`. Other repository settings and labels remain organization-wide. For repositories on plans that support branch protection, place the intended `branches` configuration in `safe-settings/repos/<repository>.yml` (or use a supported higher-level policy), rather than applying it indiscriminately.

When private branch protection is available for `sharedale/sharedale`, restore the intended `main` protections: PR-only changes, linear history, and required CI status checks once CI is established. See https://github.com/sharedale/sharedale/issues/68.

This is a **plan-based limitation**, not a GitHub App authorization issue. Do not make the application repository public to work around it.
