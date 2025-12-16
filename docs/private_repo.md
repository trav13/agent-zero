# Private repository layout

This guide explains how to keep organization-only assets in a **separate private space** without modifying the Agent Zero application code.

## Why a private directory?
- Keep secrets and organization-specific assets out of the public app tree.
- Avoid diverging from upstream while still allowing private overrides and runbooks.

## Directory structure
Create a `private/` folder at the repository root:

- `private/README.md` – usage notes (tracked)
- `private/config/` – copies of config you need to override (e.g., `model_providers.yaml`, `.env` files)
- `private/docs/` – internal documentation and runbooks
- `private/assets/` – any private binaries or resources

All contents under `private/` are ignored by git (except this README and `.gitkeep` files), so your sensitive material stays out of commits.

## Workflow for private builds
1. Place your private configs inside `private/config/`. For example, keep your organization-specific `model_providers.yaml` there with private API bases or keys.
2. In your CI/CD or deployment scripts, copy or mount the private config files over the defaults in `conf/` before starting the app. This avoids editing application files directly.
3. Keep any internal documentation in `private/docs/` so it travels with your private fork but remains separated from the public documentation set.

By isolating private assets here, you can build out your own private repository or fork without "messing with the app" while still having a predictable place to store overrides and notes.
