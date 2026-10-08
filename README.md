# Local LLM Studio: download page

A single static page (`index.html`) with a **Download for Windows** button. It is meant for a
**public** GitHub repo (`Tompmk/local-llm-studio-download`) that holds only this page and the
installer in GitHub Releases. The source code stays in the private repos.

- The button links to `releases/latest/download/LocalLLMStudio-Setup.exe`, which always points
  to the newest release.
- The page asks GitHub's public API for the latest version and file size. It uses no trackers,
  no cookies and no external fonts, and a Content-Security-Policy blocks everything else.
- Light and dark follow the visitor's system. The text is in English, Lao and Thai; a visitor
  whose browser language is Lao or Thai sees that language first.

## Publish (first time)

1. On GitHub, create a **public** repository named `local-llm-studio-download`. Add no README,
   .gitignore or license.
2. Push this folder to it (Claude can do this when asked).
3. Repo **Settings > Pages**: Source "Deploy from a branch", branch `main`, folder `/ (root)`.
   The page will be at `https://tompmk.github.io/local-llm-studio-download/`.
4. Repo **Releases > Draft a new release**: tag `v0.1.0`, title `Local LLM Studio 0.1.0`, attach
   `llm-desktop/dist/LocalLLMStudio-Setup.exe` **and** `llm-desktop/dist/SHA256SUMS` (keep those
   exact file names), then Publish. The app's update check refuses a release without
   `SHA256SUMS`.

## New version

Set `version` in `llm-desktop/package.json` (and `__version__` in `llm-backend/app/__init__.py`),
run `pnpm prepare-resources`, `pnpm dist` and `pnpm checksums`, then create a new release (tag
`v<version>`) with `LocalLLMStudio-Setup.exe` and `SHA256SUMS`. The page updates by itself, and
installed apps with update checks switched on will offer it.
