# Sharedale organization configuration

This repository provides organization-level issue templates and Safe Settings Sync configuration.

## Safe Settings Sync

The workflow is based on [LayeredCraft/.github](https://github.com/LayeredCraft/.github) and runs every four hours or manually.

Configure a GitHub App for `github/safe-settings` with the necessary organization/repository permissions, and install it for the intended repositories. Set these **repository** values in `sharedale/.github`:

- Variable `SAFE_SETTINGS_GH_ORG`: `sharedale`
- Variable `SAFE_SETTINGS_APP_ID`: the Safe Settings GitHub App ID
- Secret `SAFE_SETTINGS_PRIVATE_KEY`: the GitHub App private key

Review the policies before the first manual workflow run. The organization configuration repository is excluded from managed targets. Do not add required CI checks until the bootstrap check exists (#67), then configure them in #68.

**Merging this PR does not install a GitHub App or create credentials.** Once the App is configured, run the workflow manually and inspect the result.

## Issue templates

The four issue forms are copied unchanged from `ncipollina/sharedale`. GitHub uses organization-level issue templates when the target repository does not have local templates. Merge this repository's PR before merging the companion PR removing the application's duplicate forms.
