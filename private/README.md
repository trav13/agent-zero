# Private workspace for your organization

Use this folder to keep organization-specific assets when you need to customize or deploy Agent Zero from a private repository without touching the core application files.

- Keep environment files, provider overrides, and secrets here instead of in the app tree.
- Recommended layout:
  - `config/` — copies of config files you want to adjust (for example, a private `model_providers.yaml`).
  - `docs/` — internal runbooks and notes that should not live in the public repo.
  - `assets/` — any private resources that the app should not bundle.
- Everything in `private/` is ignored by git (except this README and `.gitkeep` files), so your sensitive data stays out of commits.

When preparing a private fork, drop your customized files into this directory. Wire them up in your deployment pipeline (for example, copy or mount the private `config` contents over the default `conf/` files during deployment). This keeps upstream source untouched while enabling private overrides.
