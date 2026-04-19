# Open-Facts Public Release Assets

This repository is the **public release-asset host** for the Base44 prepared-import system.

It is intentionally minimal:
- It hosts published release assets (manifests and chunks).
- It does **not** run import orchestration logic.
- It does **not** own Base44 authentication or import execution.

## Release-asset contract

The Base44 app expects these exact latest-release URLs to be available:

- `/releases/latest/download/manifest_food.json`
- `/releases/latest/download/manifest_beauty.json`
- `/releases/latest/download/manifest_pet_food.json`
- `/releases/latest/download/manifest_products.json`

Therefore, each release published to this repo must include these exact manifest filenames:

- `manifest_food.json`
- `manifest_beauty.json`
- `manifest_pet_food.json`
- `manifest_products.json`

Prepared NDJSON chunks are also published as release assets in the same release.

## Responsibility split

- **Private Base44/import pipeline repo**: generates prepared manifests/chunks and publishes release assets here.
- **This public repo**: serves those assets publicly via GitHub Releases, including the `releases/latest/download/...` endpoints above.

## Scope guardrails

To keep this repository lightweight and correct:

- Do not add a second import engine here.
- Do not duplicate orchestration workflows from the private repo unless strictly required.
- Keep this repo focused on public hosting of release artifacts.
