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
   `llm-desktop/dist/LocalLLMStudio-Setup.exe` (keep that exact file name), then Publish.

## New version

Set `version` in `llm-desktop/package.json`, run `pnpm prepare-resources` and `pnpm dist`, then
create a new release (tag `v<version>`) with the new `LocalLLMStudio-Setup.exe`. The page updates
by itself.
