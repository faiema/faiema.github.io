# AGENTS.md

## Purpose

This repository is the source for **faiema.github.io**.

Treat it as a small, hand-authored static website. Its job is to present Faië's public web presence and documentation cleanly, not to become an application framework or a second canon repository.

## Role

When working in this repository, act as the site's web administrator.

The user is the final authority on content, organization, taste, and publishing decisions. Implement requested site changes directly and preserve established intent unless the user asks for a redesign.

## Architecture

The site is intentionally simple.

Current primary files:

- `index.html` — homepage
- `workflows.html` — workflow/documentation page
- `LICENSE` — repository license

There is currently no framework, package manager, build pipeline, templating system, or JavaScript application architecture.

Do not introduce React, Vue, Jekyll, npm, Tailwind, a CSS framework, or another dependency merely to make ordinary HTML/CSS changes.

Prefer the smallest durable implementation that fits the existing site.

## Homepage information architecture

The homepage should read in this broad order:

1. identity / introduction
2. **Social Links**
3. **Documentation**
4. footer / licensing / visitor counter

External social/profile destinations belong under **Social Links**.

Internal explanatory, workflow, reference, or site-documentation pages belong under **Documentation**.

Do not place documentation links above the social links unless the user explicitly changes this organization.

Section headings should be visible when they help make the information architecture clear.

## Visual continuity

Preserve the existing visual language unless the user asks for a redesign:

- dark background
- restrained cyan / violet / pink spectral accents
- translucent panel treatment
- generous spacing
- simple typography
- responsive card layout
- minimal motion
- clean, uncluttered presentation

New UI should look native to the existing page rather than pasted in from a different design system.

Avoid gratuitous ornament and avoid turning the site into generic fantasy styling.

## Persistent Faië footer figure

The full-body Faië artwork at `/assets/faie-homepage.png` is a persistent site feature, not a homepage-only decoration.

Every ordinary public site page should include the Faië footer figure immediately before its footer/license area. Preserve the established responsive behavior:

- on desktop, the figure may remain fixed alongside the main content;
- on mobile, it moves into normal document flow at the end of the page content;
- do not place ordinary navigation, cards, or article content between the figure and the footer;
- reuse the established homepage asset rather than inventing a page-specific substitute unless the user explicitly asks for one.

When adding a new public page, carrying this figure/footer treatment forward is part of the page implementation.

## Accessibility and responsive behavior

Preserve or improve:

- semantic HTML
- useful navigation and section labels
- keyboard focus behavior
- readable contrast
- responsive behavior on narrow screens
- `prefers-reduced-motion` handling
- meaningful alt text where images convey content

Do not sacrifice accessibility for visual effects.

## Editing policy

For small, clearly requested site changes:

1. inspect the relevant current file;
2. make the narrowest coherent edit;
3. preserve unrelated content and styling;
4. commit the change directly to the repository's default branch.

Do not create a branch or pull request for routine edits unless the user asks for one or the change is sufficiently large/risky that review would materially help.

For larger redesigns or structural changes, inspect all affected pages first and keep shared visual behavior consistent.

Do not rewrite an entire page merely because a local edit would be slightly less elegant.

## Publishing assumptions

The repository's default branch is the live GitHub Pages source unless repository configuration demonstrates otherwise.

Treat commits to the publishing branch as production changes.

Do not claim a deployed change is visible until the repository update has succeeded. Allow for normal GitHub Pages propagation delay.

## Relationship to faie-canon

The private `faiema/faie-canon` repository is the durable authority for Faië canon and its ownership rules.

This website may present, summarize, document, or link to material related to that project, but **faiema.github.io is not a competing canon authority**.

Do not silently establish or revise Faië canon by changing prose on this website.

If a website task requires authoritative canon content, consult the current owning material in `faiema/faie-canon` when available.

Conversely, ordinary website layout, navigation, copy presentation, and styling decisions belong here and do not require changes to the canon repository.

## Content and links

Preserve canonical spelling where identity matters, including **Faië** with the diaeresis.

When adding external links:

- use the intended canonical/profile URL;
- preserve sensible `rel` attributes where applicable;
- distinguish external navigation from internal site navigation visually or semantically when useful.

When adding internal pages, link them with stable site-relative paths.

## Scope discipline

Do not overengineer.

A static page should remain static when static HTML and CSS solve the problem.

Do not add infrastructure in anticipation of hypothetical future needs.

Do not reorganize unrelated content while performing a focused request.

Do not remove idiosyncratic site features merely because they are unconventional. If something looks intentional, preserve it unless the user says otherwise.

## Working rule

The practical rule is:

**Make the site do what the user asked, with the least machinery necessary, while leaving it cleaner and no more fragile than you found it.**

## Binary site asset courier

When asked to **import pending site assets**, run:

```bash
bash scripts/import-pending-assets
```

The importer reads `.github/asset-import/pending.json`, downloads the exact staged originals, verifies byte size and SHA-256, writes the full pending batch to its declared site paths, clears the manifest, commits, and pushes.

Do not reinterpret, resize, recompress, convert, regenerate, or manually substitute staged assets. If the importer fails, report the exact error and stop.
