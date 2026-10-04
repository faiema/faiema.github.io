# Faië 魔法

Source for [faiema.github.io](https://faiema.github.io/), Faië's public website: art, social links, and workflow documentation.

The site is hand-authored HTML and CSS. There is no JavaScript application, package manager, framework, or build step.

## Files

| Path | Purpose |
| --- | --- |
| [index.html](index.html) | Homepage, social links, documentation link, and visitor counter |
| [styles.css](styles.css) | Homepage styles and responsive layout |
| [workflows.html](workflows.html) | Canon workflow documentation, with its own inline styles |
| [assets/](assets/) | Original artwork and card backgrounds |
| [scripts/import-pending-assets](scripts/import-pending-assets) | Verified batch import of staged assets |
| [.github/asset-import/](.github/asset-import/) | Pending asset manifest and import notes |
| [AGENTS.md](AGENTS.md) | Site maintenance instructions |

## Local preview

From the repository root, serve the files with Python 3:

```sh
python3 -m http.server 8000 --bind 127.0.0.1
```

Open <http://127.0.0.1:8000/> or <http://127.0.0.1:8000/workflows.html>. Use an HTTP server rather than opening the HTML files directly so root-relative asset and page links resolve correctly. Stop the server with Ctrl+C.

The homepage's visitor counter is an external image served by `hitscounter.dev`; the site itself needs no backend.

## Editing and publishing

Edit the HTML and CSS directly. Keep changes small and preserve the dark palette, spectral accents, translucent cards, and generous spacing. The homepage order is introduction, Social Links, Documentation, then the footer.

The Faië figure is a persistent feature on both pages: fixed beside the content on desktop and in normal flow immediately before the footer on mobile. Carry this treatment forward when adding a page.

Before publishing, preview affected pages at desktop and mobile widths, check links and keyboard focus, and preserve reduced-motion support. Run `git diff --check` to catch whitespace errors.

Routine changes are committed directly to `main` and pushed to GitHub. Treat `main` as the live GitHub Pages source; publication may take a few minutes after a successful push. See [AGENTS.md](AGENTS.md) for the full editing policy.

## Importing staged assets

Approved originals are staged in Google Drive and recorded in [.github/asset-import/pending.json](.github/asset-import/pending.json). From a clean checkout, run:

```sh
bash scripts/import-pending-assets
```

The importer requires Bash with `mapfile` support, Git with push access, Python 3, curl, and `sha256sum`, along with standard shell utilities. It pulls the latest changes, downloads and verifies the entire batch by byte size and SHA-256, installs the original files, clears the manifest, commits, and pushes.

Assets are not resized, recompressed, converted, or regenerated. If an import fails, stop and inspect the exact error. Manifest fields and handling rules are documented in [AGENTS.md](AGENTS.md#binary-site-asset-courier); see also the [asset import notes](.github/asset-import/README.md).

## Canon and licensing

The private `faiema/faie-canon` repository owns authoritative Faië canon. This website presents public material and documents workflows; changes here do not establish or revise canon.

Original material published here is released under CC0 1.0 Universal. See [LICENSE](LICENSE).
